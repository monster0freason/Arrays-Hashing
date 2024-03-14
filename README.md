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



## Valid Anagram (Easy)
[Valid Anagram](https://leetcode.com/problems/valid-anagram/description/)
![Valid Anagram](images/Valid%20Anagram.png)

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

