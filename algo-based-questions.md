### **1. Reverse a String**
**Problem:** Write a function that reverses a given string.

**Example:**
```javascript
reverseString("hello");  // Output: "olleh"
reverseString("JavaScript");  // Output: "tpircSavaJ"
```

**Hints:**
- You can solve this using a variety of approaches, such as using loops, recursion, or built-in methods like `split()`, `reverse()`, and `join()`.

---

### **2. Find the Missing Number in an Array**
**Problem:** Given an array of integers containing numbers from 1 to N, but one number is missing, find the missing number. The array will have a length of N-1.

**Example:**
```javascript
findMissingNumber([1, 2, 3, 5]);  // Output: 4
findMissingNumber([2, 3, 7, 5, 1]);  // Output: 4
```

**Hints:**
- Think about mathematical properties of the sum of a series. The sum of numbers from 1 to N is `(N * (N + 1)) / 2`. You can subtract the sum of the array from this total to find the missing number.

---

### **3. Find the Longest Substring Without Repeating Characters**
**Problem:** Given a string, find the length of the longest substring without repeating characters.

**Example:**
```javascript
longestSubstring("abcabcbb");  // Output: 3 ("abc")
longestSubstring("bbbbb");  // Output: 1 ("b")
longestSubstring("pwwkew");  // Output: 3 ("wke")
```

**Hints:**
- Use a sliding window approach and a hash map (or set) to keep track of characters you've seen.

---

### **4. Check for Balanced Parentheses**
**Problem:** Write a function to check if a string has balanced parentheses. The string may contain parentheses `()`, square brackets `[]`, and curly braces `{}`. You need to ensure that each opening bracket has a corresponding closing bracket, and they are properly nested.

**Example:**
```javascript
isBalanced("{[()]}");  // Output: true
isBalanced("{[(])}");  // Output: false
isBalanced("{{[[(())]]}}");  // Output: true
```

**Hints:**
- Use a stack data structure to track opening brackets. Whenever a closing bracket is encountered, pop the last opening bracket from the stack and check if they match.

---

### **5. Find the Two Numbers That Add Up to a Target**
**Problem:** Given an array of integers and a target number, find two numbers in the array that add up to the target sum. Return the indices of the two numbers.

**Example:**
```javascript
twoSum([2, 7, 11, 15], 9);  // Output: [0, 1] (2 + 7 = 9)
twoSum([3, 2, 4], 6);  // Output: [1, 2] (2 + 4 = 6)
```

**Hints:**
- A brute force approach would involve using two loops, but this can be optimized by using a hash map to store the numbers you've seen so far.

### **6. FizzBuzz**
**Problem:** Write a program that prints the numbers from 1 to `n`. But for multiples of 3, print `"Fizz"` instead of the number, and for multiples of 5, print `"Buzz"`. For numbers which are multiples of both 3 and 5, print `"FizzBuzz"`.

**Example:**
```javascript
fizzBuzz(15);
/*
Output:
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz
*/
```

**Hints:**
- Use the modulo operator (`%`) to check for divisibility by 3 and 5.

---

### **7. Find All Duplicates in an Array**
**Problem:** Given an array of integers, find all elements that appear more than once. The answer should be returned as an array of duplicate elements.

**Example:**
```javascript
findDuplicates([4, 3, 2, 7, 8, 2, 3, 1]);  // Output: [2, 3]
findDuplicates([1, 1, 2]);  // Output: [1]
```

**Hints:**
- You can solve this using a hash map (or set) to track seen numbers, or you can modify the array to mark seen elements.

---

### **8. Merge Two Sorted Arrays**
**Problem:** Given two sorted arrays, merge them into a single sorted array.

**Example:**
```javascript
mergeSortedArrays([1, 3, 5], [2, 4, 6]);  // Output: [1, 2, 3, 4, 5, 6]
mergeSortedArrays([1, 2, 3], [0, 5, 6]);  // Output: [0, 1, 2, 3, 5, 6]
```

**Hints:**
- Use two pointers to traverse each array and compare their elements, inserting the smaller element into the result array.

---

### **9. Rotate an Array**
**Problem:** Given an array of integers, rotate the array to the right by `k` steps. For example, if `k = 3`, the elements of the array should be moved 3 positions to the right.

**Example:**
```javascript
rotateArray([1, 2, 3, 4, 5, 6, 7], 3);  // Output: [5, 6, 7, 1, 2, 3, 4]
rotateArray([-1, -100, 3, 99], 2);  // Output: [3, 99, -1, -100]
```

**Hints:**
- You can solve this problem by reversing the whole array and then reversing specific parts of the array, or you can use a direct approach with an auxiliary array.

---

### **10. Implement an Anagram Checker**
**Problem:** Given two strings, determine if one is an anagram of the other. An anagram is a word or phrase formed by rearranging the letters of another, using all the original letters exactly once.

**Example:**
```javascript
isAnagram("anagram", "nagaram");  // Output: true
isAnagram("rat", "car");  // Output: false
```

**Hints:**
- Sort both strings and compare if they are equal, or you can use a frequency count approach (hash map) to track the occurrence of each character.