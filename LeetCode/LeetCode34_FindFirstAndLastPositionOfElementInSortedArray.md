# LeetCode 34: Find First and Last Position of Element in Sorted Array

### Difficulty: Medium

### Description:
Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

Example 1:
```
Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
```
Example 2:
```
Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
```

### Thought:
1. Key point: Sorted array, search problem, runtime O(logN)
2. Binary search O(logN)
3. Time complexity: O(logN + M), M < N
4. Space complexity: O(1)

### Code:
```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int min = 0;
        int max = nums.length-1;
        int tmp;
        int mid = -1;

        // binary search to find target value
        while (min <= max) {
            mid = (min + max) / 2;

            if (nums[mid] == target) {
                break;
            } else if (nums[mid] < target) {
                min = mid+1;
            } else if (nums[mid] > target) {
                max = mid-1;
            }
        }

        // Not found
        if (mid == -1 || nums[mid] != target) {
            return new int[]{-1, -1};
        }

        // loop from mid to find first and last target
        int i = mid;
        int j = mid;
        while (true) {
            if (i >= 0 && nums[i] == target) {
                i--;
            }
            if (j < nums.length && nums[j] == target) {
                j++;
            }
            if ((i < 0 || nums[i] != target) &&
                (j == nums.length || nums[j] != target)) {
                break;
            }
        }
        return new int[]{i+1, j-1};
    }
}
```

### Result:
Runtime: 6 ms, faster than 32.21% of Java online submissions
