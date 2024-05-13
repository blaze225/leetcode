https://leetcode.com/problems/move-zeroes/description

Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

**Note** that you must do this in-place without making a copy of the array.


Example 1:

Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]

Example 2:

Input: nums = [0]
Output: [0]
 

**Constraints**:

1 <= nums.length <= 104

-231 <= nums[i] <= 231 - 1

### Solution

Two pointer approach: one for the current number being processed and the other for keeping track of the non zeroes

#### 1. Move all non zeroes to the front and write the zeroes at the end

``` python
def moveZeroes(self, nums: List[int]) -> None:
    """
    Do not return anything, modify nums in-place instead.
    """
    # Pointer to maintain index of last non zero number
    lastNonZeroIndex = 0
    for i in range(len(nums)):
        # If number is not zero, write it to the lastNonZeroIndex
        if nums[i] != 0:
            nums[lastNonZeroIndex] = nums[i]
            lastNonZeroIndex += 1
    # All the non zeroes have been moved to the front in order
    # All the numbers after that have to be zero
    for i in range(lastNonZeroIndex, len(nums)):
        nums[i] = 0
```

#### 2. Instead of moving all non zeroes, swap them

``` python
def moveZeroes(self, nums: List[int]) -> None:
    """
    Do not return anything, modify nums in-place instead.
    """
    # Pointer to maintain index of last non zero number
    lastNonZeroIndex = 0
    # 
    for i in range(len(nums)):
        # Swap the non zero number with the current number (zero)
        # This way we still move them to the front but also move the zeroes to the end
        if nums[i] != 0:
            nums[lastNonZeroIndex], nums[i] = nums[i], nums[lastNonZeroIndex]
            lastNonZeroIndex += 1
```
