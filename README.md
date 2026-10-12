Apply Operations on Array to Maximize Sum of Squares (LeetCode 2897)

DESCRIPTION
Greedily redistribute each bit position’s set bits into as few numbers as possible, then sum the squares of the top k resulting values modulo 10^9 + 7.

PROBLEM
Given a 0-indexed integer array nums and a positive integer k, you may repeatedly choose two distinct indices i and j and replace nums[i] with (nums[i] AND nums[j]) and nums[j] with (nums[i] OR nums[j]). After any number of operations, choose k elements from the array and return the maximum possible sum of their squares, modulo 10^9 + 7.

APPROACH

The operation never changes how many numbers have a given bit set. It only moves bits between elements.
Count how many numbers have each bit set (bits 0 to 29).
Build k numbers one at a time. For each, set every bit whose count is still above zero, then reduce that count by one.
The first number is the OR of everything, the second is the next largest, and so on. Squaring rewards large values, so packing bits into as few numbers as possible is optimal.
Add up the squares modulo 10^9 + 7.

EXAMPLE
Input: nums = [2, 6, 5, 8], k = 2
Bit counts: bit 0 = 1, bit 1 = 2, bit 2 = 2, bit 3 = 1
First number: 15. Second number: 6.
Output: 225 + 36 = 261

COMPLEXITY
Time: O(30n + 30k)
Space: O(1)

USAGE
The solution is the class Solution with the method maxSum(nums, k), in Python or C++.

CONSTRAINTS
1 <= k <= nums.length <= 10^5
1 <= nums[i] <= 10^9

SUGGESTED FILE NAME
apply_operations_max_sum_of_squares.py
