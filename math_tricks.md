### Divison
- If you have (a/b) and (b/c), to get (a/c) just multiply (a/b) * (b/c).
- If you have (a/b) = 2, then (b/a) is just 1 over the value, which is 1/2.

### Subarrays
- As you add a new number to an array, the number of subarrays **INCREASE** by the length of that subarray. Example:
```
arr = []
count = 0

// after adding 5:
arr = [5]
count += (end - start + 1) // which is 1! So count is 1.
new subarrays are [ (5) ]

// after adding 2:
arr = [5, 2]
count += (end - start + 1) // which is 2! So the count is 3.
new subarrays are [(2), (5, 2)]

// after adding 6:
arr = [5, 2, 6]
count += (end - start + 1) // which is 3! So the count is 6.
new subarrays are [(5, 2, 6), (2, 6) (6)]
```
