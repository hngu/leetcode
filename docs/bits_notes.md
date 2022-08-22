### Observations:
- Odd numbers in binary have their last bit set to 1.
- Even numbers in binary have their last bit set to 0.
- Numbers that are powers of 2 have their left most bit set to 1. It is the only 1 set.
- If a binary number, N, is a power of 2, the N-1 in binary will have the leftmost bit be zero and the bits to the right of it all 1s.

### Shifting:
- 4 << 1: means to shift binary rep. of 4 (100) by 1 position to the left, so the result will be 8 (1000).
- 4 >> 1: this is the same for right shift (>>) but in the right position so the result will be 2 (10) where the last bit is dropped.
- Observation: when you shift a number by 1 to the left, you are multiplying it by 2. If you are shifting the number by 1 to the right, you are dividing by 2.

### Practice:

1. Fetch the bit at position i from left in the binary representation of a number.
Solution: `If number & (1<<(position-1))!=0: bit is set`

2. Toggle all the bits of a number: XOR the number with all one’s.
Solution: `XOR by bit 1 toggles the original bit.`

3. Check if a given number is a power of 2.
Solution: `Number is power of 2 if Number & (Number-1)==0`

4. Given an array of numbers. Array has only one element which is alone. 
All other elements appear in pair. Find that one element with missing pair in O(1) extra space.
HINT: `XOR of element with itself results value zero.`

5. Find the number of set bits in a binary representation of a number.
Solution: `number of set bits in a number: number = number & (number-1), till number != 0 and increment the counter at each step. Finally return the counter.`

6. One more trick I found useful is, if you want to find the total number of bits in a binary representation of a number, you can simply use this formula:
`number of bits = floor(log(number)/ log(2))+1`

### Example Problems:

```
Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

Follow up: Could you implement a solution using only O(1) extra space complexity and O(n) runtime complexity?


Input: nums = [3,0,1]
Output: 2
Explanation: n = 3 since there are 3 numbers, so all numbers are in the range [0,3]. 2 is the missing number in the range since it does not appear in nums.

Input: nums = [0,1]
Output: 2
Explanation: n = 2 since there are 2 numbers, so all numbers are in the range [0,2]. 2 is the missing number in the range since it does not appear in nums.

Input: nums = [9,6,4,2,3,5,7,0,1]
Output: 8
Explanation: n = 9 since there are 9 numbers, so all numbers are in the range [0,9]. 8 is the missing number in the range since it does not appear in nums.

Input: nums = [0]
Output: 1
Explanation: n = 1 since there is 1 number, so all numbers are in the range [0,1]. 1 is the missing number in the range since it does not appear in nums.

Solution:
Intuition

We can harness the fact that XOR is its own inverse to find the missing element in linear time.

Algorithm

Because we know that nums contains nn numbers and that it is missing exactly one number on the range [0..n-1][0..n−1], we know that nn definitely replaces the missing number in nums. Therefore, if we initialize an integer to nn and XOR it with every index and value, we will be left with the missing number. Consider the following example (the values have been sorted for intuitive convenience, but need not be):

class Solution:
    def missingNumber(self, nums):
        missing = len(nums)
        for i, num in enumerate(nums):
            missing ^= i ^ num
        return missing
```
