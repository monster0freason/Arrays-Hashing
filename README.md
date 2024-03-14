# Arrays & Hashing
 "Explore a curated collection of 9 array and hashing related problems, ranging from easy to medium difficulty. Enhance your algorithmic skills and understanding of data structures with this comprehensive repository."


## 0️⃣Table of Contents
1. [Contains Duplicate (Easy)](#contains-duplicate-easy)
2. [Valid Anagram (Easy)](#valid-anagram-easy)
3. [Two Sum (Easy)](#two-sum-easy)
4. [Group Anagrams (Medium)](#group-anagrams-medium)
5. [Top K Frequent Elements (Medium)](#top-k-frequent-elements-medium)
6. [Product of Array Except Self (Medium)](#product-of-array-except-self-medium)
7. [Valid Sudoku (Medium)](#valid-sudoku-medium)
8. [Encode and Decode Strings (Medium)](#encode-and-decode-strings-medium)
9. [Longest Consecutive Sequence (Medium)](#longest-consecutive-sequence-medium)

## Contains Duplicate (Easy)
[Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)
![Contains Duplicate](images/Contains%20Duplicate.png)
```
# Intuition
My initial thoughts on solving this problem are to efficiently check for duplicate elements in the given array. The use of a HashSet comes to mind as it allows for constant-time average complexity for both insertion and lookup operations, which is crucial for optimal duplicate detection.

# Approach
1. Start with an empty HashSet to store unique elements.
2. Iterate through the array.
3. Check if the current element is already in the HashSet.
   - If yes, return True indicating the presence of a duplicate.
   - If not, proceed to the next step.
4. Add the current element to the HashSet.
5. If the loop completes without finding duplicates, return False.

# Complexity
- Time complexity:
The time complexity is O(n) , where n is the length of the input array. This is because, in the worst case, we iterate through the entire array once. Checking for membership in a HashSet has an average time complexity of O(1).

- Space complexity:
The space complexity is also O(n) . The HashSet may store all elements in the array in the worst case, leading to linear space usage.

# Code(Python)
 ```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        # Create an empty HashSet to store unique elements
        hashSet = set()
        
        # Iterate through the array
        for n in nums:
            # Check if the element is already in the HashSet
            if n in hashSet:
                # If yes, return True indicating the presence of a duplicate
                return True
            
            # Add the element to the HashSet
            hashSet.add(n)
        
        # If the loop completes without finding duplicates, return False
        return False
```

# Code(C++)
```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        // Create an unordered_set to store unique elements
        unordered_set<int> hashSet;
        
        // Iterate through the vector
        for(int n : nums){
            // Check if the element is already in the unordered_set
            if(hashSet.count(n) > 0){
                // If yes, return true indicating the presence of a duplicate
                return true;
            }
            
            // Add the element to the unordered_set
            hashSet.insert(n);
        }
        
        // If the loop completes without finding duplicates, return false
        return false;
    }
};
```
```


## Valid Anagram (Easy)
[Valid Anagram](https://leetcode.com/problems/valid-anagram/description/)
![Valid Anagram](images/Valid%20Anagram.png)
2.1 Valid Anagram(EASY)

# Intuition
My initial thoughts on solving this problem are to compare the frequency of characters in two strings to determine if one is an anagram of the other.

# Approach
1. Use an unordered map to store the frequency of characters in the first string (s).
2. Iterate through the second string (t) and decrement the corresponding frequency in the map.
   - If at any point, the frequency becomes negative, return false as it indicates an extra character in t.
3. Calculate the sum of remaining frequencies in the map after iterating through both strings.
4. If the sum is non-zero, return false; otherwise, return true.
   
# Complexity
- Time complexity:
   - O(n), where n is the length of the input strings. The algorithm iterates through both strings once.
- Space complexity:
   - O(1) in terms of auxiliary space, as the unordered map has a constant size of 26 (assuming only lowercase letters).

# Code(C++)
```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        unordered_map<char, int> m;
        int sum = 0;
        
        // Populate the map with the frequency of characters in the first string (s)
        for (char n : s) {
            m[n]++;
        }
        
        // Iterate through the second string (t) and decrement the corresponding frequency
        for (char n : t) {
            if (m[n] > 0) {
                m[n]--;
            } else {
                return false;
            }
        }
        
        // Calculate the sum of remaining frequencies in the map
        for (char n : s) {
            sum += m[n];
        }
        
        // If the sum is non-zero, return false; otherwise, return true
        return sum == 0;
    }    
};
```

# Code(Python)
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        m = {}
        sum_val = 0
        
        # Populate the dictionary with the frequency of characters in the first string (s)
        for char in s:
            m[char] = m.get(char, 0) + 1
        
        # Iterate through the second string (t) and decrement the corresponding frequency
        for char in t:
            if m.get(char, 0) > 0:
                m[char] -= 1
            else:
                return False
        
        # Calculate the sum of remaining frequencies in the dictionary
        for char in s:
            sum_val += m[char]
        
        # If the sum is non-zero, return False; otherwise, return True
        return sum_val == 0

```


2.2 Valid Anagram(EASY)
# Intuition
My initial thoughts on solving this problem are to efficiently check for anagrams by comparing the frequency of characters in two strings.

# Approach
1. Create two dictionaries, S and T, to store the frequency of characters in strings s and t, respectively.
2. Iterate through string s and update the frequencies in dictionary S.
3. Iterate through string t and update the frequencies in dictionary T.
4. Check if dictionaries S and T are equal.
   - If yes, it indicates that both strings have the same character frequencies and are anagrams.
   - If not, they are not anagrams.

# Complexity
- Time complexity:
   - O(n), where n is the length of the input strings. The algorithm iterates through both strings once.
- Space complexity:
   - O(n), where n is the length of the input strings. The dictionaries may store all distinct characters in both strings in the worst case.

# Code(Python)
```python
# Python Solution
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # Step 1: Check if the lengths of both strings are equal
        if len(s) != len(t):
            return False

        # Step 2: Create dictionaries S and T to store character frequencies
        S, T = {}, {}

        # Step 3: Iterate through string s and update frequencies in dictionary S
        for i in range(len(s)):
            S[s[i]] = 1 + S.get(s[i], 0)

        # Step 4: Iterate through string t and update frequencies in dictionary T
        for i in range(len(t)):
            T[t[i]] = 1 + T.get(t[i], 0)
        
        # Step 5: Check if dictionaries S and T are equal, indicating anagrams
        return S == T

```

# Code(C++)
```c++
// C++ Solution
class Solution {
public:
    bool isAnagram(string s, string t) {
        // Step 1: Check if the lengths of both strings are equal
        if(s.size() != t.size()) return false;
        
        // Step 2: Create unordered maps sMap and tMap to store character frequencies
        unordered_map<char,int> sMap;
        unordered_map<char,int> tMap;
        
        // Step 3: Iterate through string s and update frequencies in sMap
        for(int i = 0; i < s.size(); i++){
            sMap[s[i]]++;
        }

        // Step 4: Iterate through string t and update frequencies in tMap
        for(int i = 0; i < t.size(); i++){
            tMap[t[i]]++;
        }
        
        // Step 5: Check if character frequencies in sMap and tMap are equal
        for(int i = 0; i < sMap.size(); i++){
            if(sMap[i] != tMap[i]) return false;
        }
        
        return true;
    }
};

```
2.3 Valid Anagram(EASY)
# Intuition
My initial thoughts on solving this problem are to compare the sorted versions of the two strings to determine if they are anagrams.

# Approach
The approach involves sorting both strings and checking if their sorted versions are equal. If they are, it indicates that the strings have the same character frequencies and are therefore anagrams.

# Complexity
- Time complexity:
The time complexity is O(n log n), where n is the length of the longer string among s and t. This is due to the sorting operation.

- Space complexity:
The space complexity is O(n), where n is the length of the longer string among s and t. This is required for storing the sorted versions of the strings.

# Code
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # Compare the sorted versions of strings s and t
        return sorted(s) == sorted(t)
```


2.4 Valid Anagram(EASY)
# Intuition
My initial thoughts on solving this problem are to efficiently compare the character frequencies in two strings. The use of Python's Counter class comes to mind as it provides a convenient way to count occurrences of elements.

# Approach
The approach involves using the Counter class to create dictionaries of character frequencies for both strings. Then, compare the dictionaries to check if they are equal. If they are, it indicates that the strings have the same character frequencies and are therefore anagrams.

# Complexity
- Time complexity:
The time complexity is O(n), where n is the total number of characters in both strings. This is because the Counter class iterates through both strings once to count the occurrences.

- Space complexity:
The space complexity is O(n), where n is the total number of unique characters in both strings. This is required for storing the character frequencies in the Counter objects.

# Code
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # Compare the character frequencies using Counter objects
        return Counter(s) == Counter(t)
```

## Two Sum (Easy)
[Two Sum](https://leetcode.com/problems/two-sum/description/)
![Two Sum](images/Two%20Sum.png)

## Group Anagrams (Medium)
[Group Anagrams](https://leetcode.com/problems/group-anagrams/description/)
![Group Anagrams](images/Group%20Anagrams.png)

## Top K Frequent Elements (Medium)
[Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/description/)
![Top K Frequent Elements](images/Top%20K%20Frequent%20Elements.png)

## Product of Array Except Self (Medium)
[Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/description/)
![Product of Array Except Self](images/Product%20of%20Array%20Except%20Self.png)

## Valid Sudoku (Medium)
[Valid Sudoku](https://leetcode.com/problems/valid-sudoku/description/)
![Valid Sudoku](images/Valid%20Sudoku.png)

## Longest Consecutive Sequence (Medium)
[Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/description/)
![Longest Consecutive Sequence](images/Longest%20Consecutive%20Sequence.png)

