# Assignment
Easy 1:
Algorithm:
1. Start by removing any trailing spaces from the input string to ensure accuracy.
2. Initialize a variable `length` to zero, which will hold the length of the last word.
3. Traverse the string from right to left.
4. While traversing, ignore any trailing spaces.
5. When encountering a non-space character, start counting the length of the word until a space or the start of the string is reached.
6. Return the length of the last word found.

Pseudocode:
FUNCTION lengthOfLastWord(s):
    length = 0
    i = length(s) - 1 
    WHILE i >= 0 AND s[i] == ' ':
        i = i - 1
    WHILE i >= 0 AND s[i] != ' ':
        length = length + 1
        i = i - 1

    RETURN length
```

Explanation:
- The algorithm starts by trimming any trailing spaces from the input string to ensure accuracy in calculating the length of the last word.
- It then starts traversing the string from the end (`length(s) - 1`) while skipping any trailing spaces.
- Once a non-space character is encountered, it begins counting the length of the word until a space or the start of the string is found.
- Finally, it returns the length of the last word discovered.

This approach efficiently computes the length of the last word in the given string without the need to split the entire string into separate words.
Medium 2: 
To find all elements in an integer array that appear more than ⌊n/3⌋ times (where ⌊⌋ denotes the floor function), you can use the Boyer-Moore Majority Vote algorithm. The algorithm can be modified for this specific case to find elements that appear more than ⌊n/3⌋ times.

Algorithm:
1. Initialize two candidate variables `candidate1` and `candidate2` and their respective counters `count1` and `count2`.
2. Traverse through the array.
3. If the current element matches either `candidate1` or `candidate2`, increment the respective count.
4. If any counter reaches 0, update the corresponding candidate.
5. Decrease both counters if the current element is different from both candidates.
6. After the first traversal, reset the counters and re-traverse the array to count occurrences of the two candidates.
7. Verify if the counts of the candidates are greater than ⌊n/3⌋.
8. Return the elements that meet the condition.

Here's a Python implementation of the algorithm:

```python
def majorityElement(nums):
    if not nums:
        return []

    candidate1, candidate2 = None, None
    count1, count2 = 0, 0

    for num in nums:
        if candidate1 == num:
            count1 += 1
        elif candidate2 == num:
            count2 += 1
        elif count1 == 0:
            candidate1 = num
            count1 = 1
        elif count2 == 0:
            candidate2 = num
            count2 = 1
        else:
            count1 -= 1
            count2 -= 1

    count1 = count2 = 0
    for num in nums:
        if num == candidate1:
            count1 += 1
        elif num == candidate2:
            count2 += 1

    result = []
    if count1 > len(nums) // 3:
        result.append(candidate1)
    if count2 > len(nums) // 3:
        result.append(candidate2)

    return result

# Example
nums = list(map(int,input())
print("Output:", majorityElement(nums)) 
```
