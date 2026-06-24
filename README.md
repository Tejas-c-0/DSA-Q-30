# LeetCode 167 - Two Sum II (Input Array Is Sorted)

## Problem

Given a **1-indexed** array of integers `numbers` that is already sorted in non-decreasing order, find two numbers such that they add up to a specific `target`.

Return the indices of the two numbers **(1-indexed)**.

## Example

```python
numbers = [2,7,11,15]
target = 9
```

Output:

```python
[1,2]
```

Because:

```python
2 + 7 = 9
```

---

## Pattern Used

* **Two Pointers**
* **Sorted Array Optimization**

---

## Intuition

Since the array is sorted, we can use two pointers:

* `left` starts from the beginning
* `right` starts from the end

At each step:

* If the current sum is **greater than** target, move `right` left to reduce the sum.
* If the current sum is **less than** target, move `left` right to increase the sum.
* If the current sum equals the target, return the indices.

This avoids using a hash map and gives an efficient linear-time solution.

---

## Approach

1. Initialize two pointers:

   * `left = 0`
   * `right = len(numbers) - 1`
2. While `left < right`:

   * Compute `current_sum = numbers[left] + numbers[right]`
   * If `current_sum > target`, decrement `right`
   * If `current_sum < target`, increment `left`
   * Otherwise, return `[left + 1, right + 1]` because the problem uses **1-based indexing**

---

## Python Solution

```python
from typing import List

class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        left = 0
        right = len(numbers) - 1

        while left < right:
            current_sum = numbers[left] + numbers[right]

            if current_sum > target:
                right -= 1
            elif current_sum < target:
                left += 1
            else:
                return [left + 1, right + 1]
```

---

## Time Complexity

* **O(n)**
  Because each pointer moves at most once through the array.

## Space Complexity

* **O(1)**
  Only two pointers are used.

---

## What I Learned

* How sorted arrays can be optimized using the **Two Pointers** pattern.
* How pointer movement depends on whether the current sum is greater or smaller than the target.
* Why 1-indexed output matters in this problem.
* How to replace a brute-force `O(n²)` approach with an `O(n)` solution.
