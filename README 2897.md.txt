LeetCode 2897, Apply Operations on Array to Maximize Sum of Squares.

Idea: the operation never changes how many numbers in the array have a given bit set. So for each bit position, count how many numbers have it. Then build k numbers greedily: for each number, set every bit whose count is still above zero, and reduce that count by one. The first number gets the most bits, the second gets the next most, and so on. Because squaring rewards large values, packing the bits into as few numbers as possible gives the maximum sum of squares. Add up the squares modulo 1,000,000,007.

Python:

class Solution:
def maxSum(self, nums, k):
MOD = 10**9 + 7
cnt = [0] * 30
for x in nums:
for b in range(30):
if x >> b & 1:
cnt[b] += 1

    ans = 0
    for _ in range(k):
        cur = 0
        for b in range(30):
            if cnt[b] > 0:
                cur |= 1 << b
                cnt[b] -= 1
        if cur == 0:
            break
        ans = (ans + cur * cur) % MOD
    return ans

Check with nums = [2, 6, 5, 8], k = 2: bit counts are bit 0: 1, bit 1: 2, bit 2: 2, bit 3: 1. The first number is 15, the second is 6, and 225 + 36 = 261, which matches the expected output.

Complexity: O(30n + 30k) time, O(1) extra space.