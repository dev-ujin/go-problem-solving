# LeetCode 53: Maximum Subarray

- [Link to Problem](https://leetcode.com/problems/maximum-subarray/)

## Solution
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int sum = 0;
        int max = Integer.MIN_VALUE;
        for (int i = 0 ; i < nums.length ; i++) {
            if (sum < 0) {
                sum = nums[i];
            } else {
                sum += nums[i];
            }
            if (sum > max) {
                max = sum;
            }
        }
        return max;
    }
}
```