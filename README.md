# NeetCode 150 — Python Optimal Solutions

This README provides concise, optimal Python solutions for the **NeetCode 150** problems, focusing on:

* **Time Complexity** (targeting the best possible)
* **Space Complexity**
* **Clean & interview-ready implementations**
* **Patterns used (Two Pointers, Sliding Window, Hashing, etc.)**

---

## 🧠 Arrays & Hashing

### 217. Contains Duplicate

**Time:** O(n), **Space:** O(n)

```python
class Solution:
    def containsDuplicate(self, nums):
        seen = set()
        for n in nums:
            if n in seen:
                return True
            seen.add(n)
        return False
```

### 242. Valid Anagram

**Time:** O(n), **Space:** O(1)

```python
class Solution:
    def isAnagram(self, s, t):
        if len(s) != len(t): return False
        count = [0] * 26
        for i in range(len(s)):
            count[ord(s[i]) - ord('a')] += 1
            count[ord(t[i]) - ord('a')] -= 1
        return all(x == 0 for x in count)
```

### 1. Two Sum

**Time:** O(n), **Space:** O(n)

```python
class Solution:
    def twoSum(self, nums, target):
        prev = {}
        for i, n in enumerate(nums):
            diff = target - n
            if diff in prev:
                return [prev[diff], i]
            prev[n] = i
```

---

## 🔁 Two Pointers

### 125. Valid Palindrome

**Time:** O(n), **Space:** O(1)

```python
class Solution:
    def isPalindrome(self, s):
        l, r = 0, len(s) - 1
        while l < r:
            while l < r and not s[l].isalnum(): l += 1
            while l < r and not s[r].isalnum(): r -= 1
            if s[l].lower() != s[r].lower(): return False
            l += 1
            r -= 1
        return True
```

### 167. Two Sum II

**Time:** O(n), **Space:** O(1)

```python
class Solution:
    def twoSum(self, numbers, target):
        l, r = 0, len(numbers) - 1
        while l < r:
            s = numbers[l] + numbers[r]
            if s == target:
                return [l + 1, r + 1]
            if s < target:
                l += 1
            else:
                r -= 1
```

### 11. Container With Most Water

**Time:** O(n), **Space:** O(1)

```python
class Solution:
    def maxArea(self, height):
        l, r = 0, len(height) - 1
        res = 0
        while l < r:
            area = (r - l) * min(height[l], height[r])
            res = max(res, area)
            if height[l] < height[r]: l += 1
            else: r -= 1
        return res
```

---

## 📏 Sliding Window

### 3. Longest Substring Without Repeating Characters

**Time:** O(n), **Space:** O(n)

```python
class Solution:
    def lengthOfLongestSubstring(self, s):
        seen = set()
        l = 0
        res = 0
        for r in range(len(s)):
            while s[r] in seen:
                seen.remove(s[l])
                l += 1
            seen.add(s[r])
            res = max(res, r - l + 1)
        return res
```

---

## 📚 More sections will be added (Dynamic Programming, Trees, Graphs, etc.)

This file is meant to grow as you complete NeetCode 150.

Let me know which section you want added next!
