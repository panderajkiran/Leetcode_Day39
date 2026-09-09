# Leetcode_Day39

# Day 39 — Sqrt(x)

**LeetCode Problem:** 69. Sqrt(x)  
**Difficulty:** Easy  
**Language:** Java  
**Topic:** Binary Search

## 📝 Problem

Given a non-negative integer `x`, return the square root of `x` rounded down to the nearest integer.

The solution should not use any built-in exponent functions or operators.

### Examples

**Example 1:**
- Input: `x = 4`
- Output: `2`

**Example 2:**
- Input: `x = 8`
- Output: `2`

Because √8 = 2.828..., and rounding down gives `2`.

---

## 💡 Approach

I used **Binary Search** to find the integer square root.

1. Set the search range from `1` to `x`.
2. Find the middle value.
3. Check whether `mid` can be the square root.
4. Instead of calculating `mid * mid`, I used `x / mid` to avoid integer overflow.
5. If `mid <= x / mid`, then `mid` can be a possible answer, so I store it and search on the right side.
6. Otherwise, I search on the left side.
7. Finally, return the stored answer.

### Why Binary Search?

The possible answer lies within a sorted range.

Binary Search repeatedly cuts the search space in half, making it much faster than checking every number one by one.

---

## 💻 Java Solution

```java
class Solution {
    public int mySqrt(int x) {
        int low = 1, high = x;
        int ans = 0;

        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (mid <= x / mid) {
                ans = mid;
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }

        return ans;
    }
}
⏱️ Complexity
Time Complexity: O(log x)
Space Complexity: O(1)
📚 What I Learned

Today I learned how Binary Search can be used beyond simply searching for an element in an array.

I also learned an important way to avoid integer overflow by comparing:

mid <= x / mid

instead of directly calculating:

mid * mid

This small change makes the solution safer for large values.

🎯 Takeaway

Sometimes the best solution is not about doing more calculations.

It is about reducing the number of calculations you need to do.

Day 39 complete. One more problem, one more step forward.
