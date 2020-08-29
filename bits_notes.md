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
