# Leetcode 152: Maximum Product Subarray

- [Link to Problem](https://leetcode.com/problems/maximum-product-subarray/)

## Solution
```java
class Solution {
    public int maxProduct(int[] nums) {
        int productMin = 1;
        int productMax = 1;
        int max = Integer.MIN_VALUE;
        for (int i = 0 ; i < nums.length ; i++) {
            int tempMax = productMax * nums[i];
            productMax = Math.max(nums[i], Math.max(productMin*nums[i], tempMax));
            productMin = Math.min(nums[i], Math.min(productMin*nums[i], tempMax));
            max = Math.max(max, productMax);
        }
        return max;
    }
}s
```