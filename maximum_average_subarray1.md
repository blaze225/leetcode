https://leetcode.com/problems/maximum-average-subarray-i/description

You are given an integer array nums consisting of n elements, and an integer k.

Find a contiguous subarray whose **length is equal to** k that has the maximum average value and return _this value_. Any answer with a calculation error less than 10-5 will be accepted.

Example 1:

Input: nums = [1,12,-5,-6,50,3], k = 4
Output: 12.75000
Explanation: Maximum average is (12 - 5 - 6 + 50) / 4 = 51 / 4 = 12.75

Example 2:

Input: nums = [5], k = 1
Output: 5.00000

Constraints:

n == nums.length

1 <= k <= n <= 105

-104 <= nums[i] <= 104

### Solution

#### 1. Sliding window

``` python
def findMaxAverage(self, nums: List[int], k: int) -> float:
    # Initialize sum and avg variables
    maxAvg = -10000
    maxSum = 0
    for i, num in enumerate(nums):
        maxSum += num
        # When we have a big enough window, start calculating avg
        if i+1 >=k:
            maxAvg = max(maxAvg, maxSum/k)
            # Remove the first element from the window to make room for the next
            maxSum -= nums[i+1-k]
    return maxAvg
```

#### 2. Sliding window optimized

``` python
def findMaxAverage(self, nums: List[int], k: int) -> float:
    # Initialize max and current sum variables
    # Directly assign sum of first k element
    # It is sufficient to just keep track of the max sum
    maxSum = currSum = sum(nums[:k])
    for i in range(k, len(nums)):
        currSum += nums[i] - nums[i-k]
        maxSum = max(maxSum, currSum)
    return maxSum/k
```
