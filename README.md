# [35. Search Insert Position](https://leetcode.com/problems/search-insert-position/)

## 📝 Description

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with **O(log n)** runtime complexity.

### Examples

| Input | Target | Output | Explanation |
| :--- | :--- | :--- | :--- |
| `[1,3,5,6]` | `5` | `2` | Target found at index 2. |
| `[1,3,5,6]` | `2` | `1` | 2 is not present; would be inserted at index 1. |
| `[1,3,5,6]` | `7` | `4` | 7 is not present; would be inserted at the end. |

---

## 💡 Intuition & Approach

This solution utilizes **Binary Search** to achieve the required $O(\log n)$ time complexity. 

### Logic:
1. **Initialise Pointers:** We start with `start = 0` and `end = n - 1` to define our search range.
2. **Binary Search Loop:** 
   - We calculate the middle index: `mid = (start + end) / 2`.
   - If `nums[mid]` equals the `target`, we've found our index and return it immediately.
   - If the `target` is smaller than `nums[mid]`, we move our `end` pointer to `mid - 1`.
   - If the `target` is larger, we move our `start` pointer to `mid + 1`.
3. **Insertion Point:** If the loop finishes without finding the target, the correct insertion index is represented by `end + 1` (which is equivalent to where the `start` pointer finally lands).

---

## 🚀 Complexity Analysis

- **Time Complexity:** $O(\log n)$ — The search space is halved in every iteration.
- **Space Complexity:** $O(1)$ — Only a few integer variables are used, regardless of input size.

---

## 🛠️ Implementation (Java)

```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int n = nums.length;
        int start = 0;
        int end = n - 1;
        
        while (start <= end) {
            int mid = (start + end) / 2;
            
            if (nums[mid] == target) {
                return mid;
            } else if (target < nums[mid]) {
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        }    
        return end + 1;
    }
}
