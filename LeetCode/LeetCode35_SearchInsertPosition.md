# LeetCode 35: Search Insert Position
### Difficulty: Easy
### Description:
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

Example 1:
```
Input: [1,3,5,6], 5
Output: 2
```
Example 2:
```
Input: [1,3,5,6], 2
Output: 1
```
Example 3:
```
Input: [1,3,5,6], 7
Output: 4
```
Example 4:
```
Input: [1,3,5,6], 0
Output: 0
```

### Thought:
1. Key point: Sorted array, search problem
2. Solutions:
- Simple O(N) loop solution
- Improved O(N/2) loop solution by two pointers from head and tail at the same time
- Binary search O(logN)
3. Time complexity: O(logN)
4. Space complexity: O(1)

### Code:
```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        if (nums.length == 0 || nums[0] > target) {
            return 0;
        }
        if (nums[nums.length-1] < target) {
            return nums.length;
        }

        int max = nums.length -1;
        int min = 0;
        int i;
        while (min < max) {
            i = (max + min) / 2;
            if (nums[i] == target) {
                return i;
            }
            if (nums[i] < target) {
                min = i+1;
            } else {
                max = i-1;
            }
        }

        if (nums[min] < target) {
            return min + 1;
        } else {
            return min;
        }
    }
}
```

### Result:
Runtime: 2 ms, faster than 100.00% of Java online submissions
