# LeetCode 26: Remove Duplicates from Sorted Array

### Difficulty: Easy

### Description:

Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

Example 1:
```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

It doesn't matter what you leave beyond the returned length.
```

Example 2:
```
Given nums = [0,0,1,1,1,2,2,3,3,4],

Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively.

It doesn't matter what values are set beyond the returned length.
```

### Thought:
1. Key point: Sorted array, in-place O(1) memory
2. Two pointers, i indexed the current length, j traversed for next non-duplicated number
3. One variable (tmp) to store last non-duplicated number
3. Time complexity: O(N)
4. Space complexity: O(1)

### Code:
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 0) {
            return 0;
        }
        int i, j, tmp = nums[0];
        for (i = 0, j = i+1 ; j < nums.length ; j++) {
            if (tmp != nums[j]) {
                nums[i+1] = nums[j];
                i = i+1;
                tmp = nums[i];
            }
            return i+1;
        }
    }
}
```

### Result:
Runtime: 5 ms, faster than 100.00% of Java online submissions
