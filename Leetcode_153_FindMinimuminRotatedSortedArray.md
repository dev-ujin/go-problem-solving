# Leetcode 153: Find Minimum in Rotated Sorted Array

- [Link to Problem](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

## Solution
```java
class Solution {
    public int findMin(int[] nums) {
        int startIndex = 0;
        int endIndex = nums.length - 1;
        while(startIndex < endIndex) {
            int midIndex = (startIndex + endIndex) / 2; 
            if ((nums[startIndex] <= nums[midIndex]) && (nums[midIndex] <= nums[endIndex])) {
                return nums[startIndex];
            }
            else if (nums[startIndex] > nums[midIndex]) {
                endIndex = midIndex;
            }
            else if (nums[midIndex] >  nums[endIndex]) {
                startIndex = midIndex + 1;    
            }
        }
        return nums[startIndex];
    }
}
```