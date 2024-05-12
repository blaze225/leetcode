https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/

You are given an integer array prices where `prices[i]` is the price of a given stock on the ith day.

On each day, you may decide to buy and/or sell the stock. You can only hold at most **one share** of the stock at any time. However, you can buy it then immediately sell it on the **same day**.

*Find and return the **maximum profit** you can achieve*.

 

Example 1:

Input: prices = [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
Total profit is 4 + 3 = 7.

Example 2:

Input: prices = [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
Total profit is 4.

Example 3:
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: There is no way to make a positive profit, so we never buy the stock to achieve the maximum profit of 0.
 

Constraints:

1 <= prices.length <= 3 * 104

0 <= prices[i] <= 104

#### Solution
``` python
def maxProfit(self, prices: List[int]) -> int:
    # Initializations
    profit = 0
    min_price = prices[0]
    max_price = prices[0]
    for i in range(1, len(prices)-1):
        # Finding the best price to buy (local minima)
        # Also we need to reset max_price because we found new stock to buy
        # and we must sell after we buy
        if prices[i] < min_price and prices[i+1] > prices[i]:
            min_price = max_price = prices[i]
        # Finding the best price to sell (local maxima)
        # Calculate new profit and update total profit
        # Also we need to reset min_price because the stock has been sold
        if prices[i] > max_price and prices[i+1] < prices[i]:
            max_price = prices[i]
            # print("new profit", max_price - min_price)
            profit += max_price - min_price
            min_price = prices[i]
    # Edge condition: if the last stock is the local maxima then sell and add to total profit
    if prices[-1] > min_price:
        profit += prices[-1] - min_price
    return profit
```