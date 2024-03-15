# Arrays & Hashing
 "Explore a curated collection of 9 array and hashing related problems, ranging from easy to medium difficulty. Enhance your algorithmic skills and understanding of data structures with this comprehensive repository."


# 0️⃣Table of Contents
1. [Contains Duplicate (Easy)](#1️⃣contains-duplicate-easy)
2. [Valid Anagram (Easy)](#2️⃣valid-anagram-easy)
3. [Two Sum (Easy)](#3️⃣two-sum-easy)
4. [Group Anagrams (Medium)](#4️⃣group-anagrams-medium)
5. [Top K Frequent Elements (Medium)](#5️⃣top-k-frequent-elements-medium)
6. [Product of Array Except Self (Medium)](#6️⃣product-of-array-except-self-medium)
7. [Valid Sudoku (Medium)](#7️⃣valid-sudoku-medium)
8. [Longest Consecutive Sequence (Medium)](#8️⃣longest-consecutive-sequence-medium)

# 1️⃣Contains Duplicate (Easy)
[Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)
![Contains Duplicate](images/Contains%20Duplicate.png)

### Intuition
My initial thoughts on solving this problem are to efficiently check for duplicate elements in the given array. The use of a HashSet comes to mind as it allows for constant-time average complexity for both insertion and lookup operations, which is crucial for optimal duplicate detection.

### Approach
1. Start with an empty HashSet to store unique elements.
2. Iterate through the array.
3. Check if the current element is already in the HashSet.
   - If yes, return True indicating the presence of a duplicate.
   - If not, proceed to the next step.
4. Add the current element to the HashSet.
5. If the loop completes without finding duplicates, return False.

### Complexity
- Time complexity:
The time complexity is O(n) , where n is the length of the input array. This is because, in the worst case, we iterate through the entire array once. Checking for membership in a HashSet has an average time complexity of O(1).

- Space complexity:
The space complexity is also O(n) . The HashSet may store all elements in the array in the worst case, leading to linear space usage.

### Code(Python)
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

### Code(C++)
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



# 2️⃣Valid Anagram (Easy)
[Valid Anagram](https://leetcode.com/problems/valid-anagram/description/)
![Valid Anagram](images/Valid%20Anagram.png)
### 🟢Approach 1:Use hash maps to store frequencies, decrementing for one string and checking for another.

### Intuition
My initial thoughts on solving this problem are to compare the frequency of characters in two strings to determine if one is an anagram of the other.

### Approach
1. Use an unordered map to store the frequency of characters in the first string (s).
2. Iterate through the second string (t) and decrement the corresponding frequency in the map.
   - If at any point, the frequency becomes negative, return false as it indicates an extra character in t.
3. Calculate the sum of remaining frequencies in the map after iterating through both strings.
4. If the sum is non-zero, return false; otherwise, return true.
   
### Complexity
- Time complexity:
   - O(n), where n is the length of the input strings. The algorithm iterates through both strings once.
- Space complexity:
   - O(1) in terms of auxiliary space, as the unordered map has a constant size of 26 (assuming only lowercase letters).

### Code(C++)
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

### Code(Python)
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


### 🟢Approach 2:Create dictionaries for both strings and compare them.
### Intuition
My initial thoughts on solving this problem are to efficiently check for anagrams by comparing the frequency of characters in two strings.

### Approach
1. Create two dictionaries, S and T, to store the frequency of characters in strings s and t, respectively.
2. Iterate through string s and update the frequencies in dictionary S.
3. Iterate through string t and update the frequencies in dictionary T.
4. Check if dictionaries S and T are equal.
   - If yes, it indicates that both strings have the same character frequencies and are anagrams.
   - If not, they are not anagrams.

### Complexity
- Time complexity:
   - O(n), where n is the length of the input strings. The algorithm iterates through both strings once.
- Space complexity:
   - O(n), where n is the length of the input strings. The dictionaries may store all distinct characters in both strings in the worst case.

### Code(Python)
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

### Code(C++)
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
### 🟢Approach 3:Sort both strings and check for equality.
### Intuition
My initial thoughts on solving this problem are to compare the sorted versions of the two strings to determine if they are anagrams.

### Approach
The approach involves sorting both strings and checking if their sorted versions are equal. If they are, it indicates that the strings have the same character frequencies and are therefore anagrams.

### Complexity
- Time complexity:
The time complexity is O(n log n), where n is the length of the longer string among s and t. This is due to the sorting operation.

- Space complexity:
The space complexity is O(n), where n is the length of the longer string among s and t. This is required for storing the sorted versions of the strings.

### Code
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # Compare the sorted versions of strings s and t
        return sorted(s) == sorted(t)
```


### 🟢Approach 4:Create Counter objects for both strings and compare them.
### Intuition
My initial thoughts on solving this problem are to efficiently compare the character frequencies in two strings. The use of Python's Counter class comes to mind as it provides a convenient way to count occurrences of elements.

### Approach
The approach involves using the Counter class to create dictionaries of character frequencies for both strings. Then, compare the dictionaries to check if they are equal. If they are, it indicates that the strings have the same character frequencies and are therefore anagrams.

### Complexity
- Time complexity:
The time complexity is O(n), where n is the total number of characters in both strings. This is because the Counter class iterates through both strings once to count the occurrences.

- Space complexity:
The space complexity is O(n), where n is the total number of unique characters in both strings. This is required for storing the character frequencies in the Counter objects.

### Code
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # Compare the character frequencies using Counter objects
        return Counter(s) == Counter(t)
```

# 3️⃣Two Sum (Easy)
[Two Sum](https://leetcode.com/problems/two-sum/description/)
![Two Sum](images/Two%20Sum.png)

### 🟢Approach 1:Efficiently find pair of numbers in array that sums up to target. Use unordered map for quick lookups.

### Intuition
My initial thoughts on solving this problem are to efficiently find a pair of numbers in the given array that sums up to the target value. The use of an unordered map can aid in quick lookups and complement calculation.

### Approach
1. Iterate through the array.
2. For each element, calculate its complement by subtracting it from the target value.
3. Check if the complement is already present in the unordered map.
   - If yes, return the indices of the two elements forming the sum.
   - If not, proceed to the next step.
4. Store the current element and its index in the unordered map for future lookups.
5. If the loop completes without finding a pair, return an empty vector indicating no such pair exists.

### Complexity
- Time complexity:
The time complexity is O(n), where n is the length of the input array. This is because the algorithm iterates through the array once.

- Space complexity:
The space complexity is O(n), where n is the length of the input array. This is required for storing elements and their indices in the unordered map.

### Code(cpp)
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> m;
        int n = nums.size();
        int temp;
        
        for (int i = 0; i < n; i++) {
            // Calculate the complement for the current element
            temp = target - nums[i];
            
            // Check if the complement is already in the unordered map
            if (m.count(temp)) {
                // If yes, return the indices of the two elements forming the sum
                return {i, m[temp]};
            }
            
            // Store the current element and its index in the unordered map for future lookups
            m[nums[i]] = i;
        }
        
        // If the loop completes without finding a pair, return an empty vector
        return {};
    }
};
```

### Code(python)
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        m={}
        n=len(nums)

        for i in range(n):
            # Calculate the complement for the current element
            temp=target-nums[i]
            
            # Check if the complement is already in the dictionary
            if temp in m:
                # If yes, return the indices of the two elements forming the sum
                return [m[temp],i]
            
            # Store the current element and its index in the dictionary for future lookups
            m[nums[i]]=i
        
        # If the loop completes without finding a pair, return an empty list
        return []        
              
```


## 4️⃣Group Anagrams (Medium)
[Group Anagrams](https://leetcode.com/problems/group-anagrams/description/)
![Group Anagrams](images/Group%20Anagrams.png)

### 🟢Approach 1: Efficiently group anagrams by their sorted representation.
4.1 Group Anagrams(MEDIUM)

### Intuition
My initial thoughts on solving this problem are to efficiently group anagrams from the given list of strings. Anagrams share the same characters but may be arranged differently. I would explore a method to identify anagram groups.

### Approach Explanation

#### 1. Utilize a defaultdict to store lists of anagrams based on their sorted representation:
   - **Reason:** We use a defaultdict because it allows us to initialize a list for a key that doesn't exist yet. In this case, each key in the defaultdict represents a unique sorted representation of characters (anagram group). If we used a regular dictionary and tried to append words to a non-existing key, it would raise a `KeyError`. The defaultdict simplifies the process of creating and updating lists associated with each sorted form.

#### 2. Iterate through each word in the input list:
   - **Reason:** We need to process each word in the input list to identify anagrams and group them accordingly. This step ensures that we consider every word in the given list.

#### 3. Sort the characters of each word to obtain a canonical representation:
   - **Reason:** Sorting the characters of each word creates a canonical representation that is unique for each anagram group. Anagrams, by definition, have the same characters but in a different order. By sorting the characters, we ensure that anagrams have the same sorted representation, making it easy to identify and group them together.

#### 4. Append the original word to the list associated with its sorted form in the defaultdict:
   - **Reason:** This step involves updating the defaultdict with the original words associated with their sorted representations. By doing so, we maintain a mapping between the canonical representation of anagrams and the actual words that belong to each group. This is crucial for retrieving the final result.

#### 5. Return the values (anagram groups) of the defaultdict:
   - **Reason:** The final result should be a list of anagram groups. By returning the values of the defaultdict, we obtain a list where each element is a group of words that are anagrams of each other. This step completes the process of identifying and grouping anagrams.

Overall, this approach leverages the defaultdict's ability to handle missing keys, the sorting of characters for canonical representation, and the association of original words with their sorted forms to efficiently group anagrams in the input list.
.

### Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
  - The time complexity is O(n * m * log(m)), where n is the number of words in the list, and m is the maximum length of a word. This is because, for each word, we sort its characters, which takes O(m * log(m)) time.
  
- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
  - The space complexity is O(n * m), where n is the number of words in the list, and m is the maximum length of a word. This is due to storing the anagram groups in a defaultdict.
  
### Code(Python)
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        # Step 1: Utilize a defaultdict to store lists of anagrams based on their sorted representation
        dd = defaultdict(list)
        
        # Step 2: Iterate through each word in the input list
        for word in strs:
            # Step 3: Sort the characters of each word to obtain a canonical representation
            sword = ''.join(sorted(word))
            
            # Step 4: Append the original word to the list associated with its sorted form in the defaultdict
            dd[sword].append(word)

        # Step 5: Return the values (anagram groups) of the defaultdict
        return list(dd.values())
```

### Code(C++)
```c++
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        // Step 1: Use an unordered_map to store lists of anagrams based on their sorted representation
        unordered_map<string, vector<string>> mp;

        // Step 2: Iterate through each word in the input vector
        for(auto word : strs){
            // Step 3: Create a copy of the word and sort its characters to obtain a canonical representation
            string temp = word;
            sort(temp.begin(), temp.end());

            // Step 4: Append the original word to the list associated with its sorted form in the unordered_map
            mp[temp].push_back(word);
        }

        // Step 5: Prepare the final result as a vector of vectors containing anagram groups
        vector<vector<string>> ans;
        for(auto x : mp){
            // Append each group of anagrams to the final result
            ans.push_back(x.second);
        }

        // Step 6: Return the final result
        return ans;
    }
};

```

### 🟢Approach 2:Group anagrams using character count representations.
### Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My initial thoughts are to utilize character count representations to group anagrams efficiently.

### Approach
<!-- Describe your approach to solving the problem. -->
1. **Use a defaultdict to store lists of anagrams based on their character count representation.**
   - *Reason:* defaultdict simplifies the code by allowing direct appending to a list associated with a key without explicitly checking if the key exists. It defaults to an empty list for missing keys.

2. **Iterate through each string in the input list.**
   - *Reason:* To process each string in the given list.

3. **Calculate the count of each character in the string.**
   - *Reason:* Character count representations help identify anagrams by ensuring that anagrams have the same count of each character. Using an array allows constant-time access for updating counts.

4. **Use a tuple of character counts as a key to group anagrams.**
   - *Reason:* Tuples are hashable, making them suitable for use as keys in a defaultdict. They represent the unique character count pattern for each string, enabling grouping of anagrams with the same counts.

5. **Return the values (anagram groups) of the defaultdict.**
   - *Reason:* Values of the defaultdict represent groups of anagrams, providing the desired result.

### Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
The time complexity is O(n * k), where n is the number of strings and k is the maximum length of any string in the input list. This is because we iterate through each string and, for each character in the string, perform constant-time operations.

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
The space complexity is O(n * k) as we use a defaultdict to store anagrams based on their character count representations.

### Code(Python)
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        # Step 1: Use a defaultdict to store lists of anagrams based on their character count representation
        ans = collections.defaultdict(list)

        # Step 2: Iterate through each string in the input list
        for s in strs:
            # Step 3: Calculate the count of each character in the string
            count = [0] * 26
            for c in s:
                count[ord(c) - ord("a")] += 1
            
            # Step 4: Use a tuple of character counts as a key to group anagrams
            ans[tuple(count)].append(s)
        
        # Step 5: Return the values (anagram groups) of the defaultdict
        return ans.values()

```

### Code(C++)
```c++
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        // Step 1: Use an unordered_map to store lists of anagrams based on their character count representation
        unordered_map<string, vector<string>> m;

        // Step 2: Iterate through each string in the input vector
        for (int i = 0; i < strs.size(); i++) {
            // Step 3: Calculate the count of each character in the string
            string key = getKey(strs[i]);
            
            // Step 4: Update the unordered_map with the original string associated with its character count representation
            m[key].push_back(strs[i]);
        }
        
        // Step 5: Prepare the final result as a vector of vectors containing anagram groups
        vector<vector<string>> result;
        for (auto it = m.begin(); it != m.end(); it++) {
            // Append each group of anagrams to the final result
            result.push_back(it->second);
        }

        // Step 6: Return the final result
        return result;
    }

private:
    // Helper function to calculate the character count representation of a string
    string getKey(string str) {
        vector<int> count(26);
        
        // Count the occurrences of each character
        for (int j = 0; j < str.size(); j++) {
            count[str[j] - 'a']++;
        }
        
        // Create a key by concatenating the counts with '#' as a separator
        string key = "";
        for (int i = 0; i < count.size(); i++) {
            key.append(to_string(count[i]) + '#');
        }
        
        return key;
    }
};

```



## 5️⃣Top K Frequent Elements (Medium)
[Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/description/)
![Top K Frequent Elements](images/Top%20K%20Frequent%20Elements.png)

### 🟢Approach 1:Count element frequencies, sort by frequency, and return top k elements.
### Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My initial thoughts are to count the frequency of each element and then select the top k frequent elements.

### Approach
<!-- Describe your approach to solving the problem. -->
1. Use a dictionary (lis) to count the frequency of each element in the input list (nums).
2. Create an empty list (ans) to store the top k frequent elements.
3. Iterate through nums and update the frequency count in the dictionary (lis).
4. Sort the dictionary items based on frequency in descending order.
5. Extract the top k frequent elements and append them to the ans list.
6. Return the ans list.

### Complexity
- Time complexity:
  - The time complexity is O(n log n), where n is the length of the input list. This is due to the sorting step.
- Space complexity:
  - The space complexity is O(n), where n is the number of unique elements in the input list. This is for the lis dictionary.
  
### Code(Python)
```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        # Step 1: Use a dictionary (lis) to count the frequency of each element in nums.
        lis = {} 
        ans = [] 
        for x in nums:
            if x in lis:
                lis[x] += 1
            else:
                lis[x] = 1
        
        # Step 2: Sort the dictionary items based on frequency in descending order.
        slis = sorted(lis.items(), key=lambda item: item[1], reverse=True)
        
        # Step 3: Extract the top k frequent elements and append them to the ans list.
        for i in range(k):
            ans.append(slis[i][0])
        
        return ans

```

### Code(C++)
```c++
class Solution {
    static bool cmp(pair<int, int>& a, pair<int, int>& b) {
        return a.second > b.second;
    }
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        // Step 1: Use an unordered_map (mp) to count the frequency of each element in nums.
        unordered_map<int, int> mp;
        for (auto x : nums) {
            mp[x]++;
        }

        // Step 2: Create a vector of pairs (v) to store the elements and their frequencies.
        vector<pair<int, int>> v;
        for (auto x : mp) {
            v.push_back(pair{x.first, x.second});
        }

        // Step 3: Sort the vector based on frequencies in descending order.
        sort(v.begin(), v.end(), cmp);

        // Step 4: Create a vector (ans) to store the top k frequent elements.
        vector<int> ans;
        for (int i = 0; i < k; i++) {
            auto it = v.begin() + i;
            ans.push_back(it->first);
        }
        return ans;
    }
};
        
```

### 🟢Approach 2:Use buckets to group elements by frequency, then collect top k elements.
### Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My initial thoughts are to efficiently determine the top k frequent elements in the given array. To achieve this, using a bucket sorting approach based on the frequency of elements seems promising.

### Approach
<!-- Describe your approach to solving the problem. -->
1. **Create a dictionary (`mp`) to store the frequency of each element in the array:**
   - This step involves iterating through the given array and counting the occurrences of each element using a dictionary. The keys of the dictionary represent the elements, and the values represent their frequencies.

2. **Create buckets to store elements based on their frequency:**
   - Buckets are used to group elements with the same frequency. In this case, we create a list of buckets, where the index of each bucket represents the frequency, and the bucket contains elements with that frequency.

3. **Iterate through the array to populate the `mp` dictionary:**
   - For each element in the array, update the corresponding frequency in the `mp` dictionary.

4. **Iterate through the items in `mp` and distribute elements into the corresponding buckets based on their frequency:**
   - After counting the frequencies in the `mp` dictionary, iterate through its items and distribute elements into the buckets based on their frequencies. Each element goes into the bucket corresponding to its frequency.

5. **Iterate through the buckets from right to left (highest to lowest frequency) and append elements to the answer list until the desired k elements are collected:**
   - Starting from the highest frequency bucket, iterate through the buckets in descending order. For each bucket, append its elements to the answer list until we collect the top k frequent elements.

6. **Return the answer list:**
   - The final step is to return the answer list containing the top k frequent elements.

### Example
Consider the input array: [1, 1, 1, 2, 2, 3], and k = 2.

- After creating the `mp` dictionary: {1: 3, 2: 2, 3: 1}
- Buckets: [[], [3], [2], [1]]
- Iterate through the buckets (from right to left):
   - Bucket with frequency 3: Append 1 to the answer list (top k = 1).
   - Bucket with frequency 2: Append 2 to the answer list (top k = 2).
   - The answer list is [2, 1], which represents the top k frequent elements.

### Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
   - Calculating the frequency and populating the dictionary: O(n)
   - Distributing elements into buckets: O(n)
   - Building the answer list: O(k) (assuming k is small)
   - Overall time complexity: O(n)
- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
   - Dictionary `mp`: O(n)
   - Buckets: O(n)
   - Answer list: O(k) (assuming k is small)
   - Overall space complexity: O(n)

### Code(Python)
```python
# Python Solution
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        # Step 1: Create a dictionary (`mp`) to store the frequency of each element in the array.
        # Step 2: Create buckets to store elements based on their frequency.
        buckets = [[] for i in range(len(nums) + 1)]

        # Step 3: Iterate through the array to populate the `mp` dictionary.
        for n in nums:
            mp[n] = 1 + mp.get(n, 0)

        # Step 4: Iterate through the items in `mp` and distribute elements into the corresponding buckets based on their frequency.
        for n, c in mp.items():
            buckets[c].append(n)

        # Step 5: Iterate through the buckets from right to left (highest to lowest frequency) and append elements to the answer list until the desired k elements are collected.
        ans = []
        for i in range(len(buckets) - 1, 0, -1):
            for n in buckets[i]:
                ans.append(n)
                if len(ans) == k:
                    return ans
```         

### Code(C++)
```c++
# C++ Solution
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        int n = nums.size();
        
        unordered_map<int, int> mp;
        
        // Step 1: Iterate through the vector to populate the `mp` dictionary.
        for (int i = 0; i < n; i++) {
            mp[nums[i]]++;
        }
        
        vector<vector<int>> containers(n + 1);
        
        // Step 2: Iterate through the `mp` dictionary and distribute elements into the corresponding buckets based on their frequency.
        for (auto it = mp.begin(); it != mp.end(); it++) {
            containers[it->second].push_back(it->first);
        }
        
        vector<int> ans;
        
        // Step 3: Iterate through the buckets from right to left (highest to lowest frequency) and append elements to the answer list until the desired k elements are collected.
        for (int i = n; i >= 0; i--) {
            if (ans.size() >= k) {
                break;
            }
            if (!containers[i].empty()) {
                ans.insert(ans.end(), containers[i].begin(), containers[i].end());
            }
        }
        
        return ans;
    }
};
```      




## 6️⃣Product of Array Except Self (Medium)
[Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/description/)
![Product of Array Except Self](images/Product%20of%20Array%20Except%20Self.png)

### 🟢Approach 1:Calculate left and right products to obtain product of all array elements except self.
### Intuition
My initial thoughts on solving this problem involve calculating the product of all elements to the left and right of each element in the given array.

### Approach
1. Initialize three arrays: `left` to store the product of elements to the left of each element, `right` to store the product of elements to the right of each element, and `ans` to store the final product.
2. Iterate through the array to calculate the product of elements to the left of each element, storing the results in the `left` array.
3. Iterate through the array in reverse to calculate the product of elements to the right of each element, storing the results in the `right` array.
4. Iterate through the array to calculate the final product by multiplying corresponding elements from the `left` and `right` arrays, storing the results in the `ans` array.
5. Return the `ans` array as the final result.

### Complexity
- Time complexity: O(n) where n is the length of the input array. We perform three passes through the array.
- Space complexity: O(n) for the three additional arrays (`left`, `right`, and `ans`), each of size n.

### Code(C++)
```c++
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int n = nums.size();
        // Initialize arrays for left and right products, and the final result.
        vector<int> left(n, 1); 
        vector<int> right(n, 1); 
        vector<int> ans(n, 1);
        
        // Calculate the product of elements to the left of each element.
        int left_product = 1;
        for (int i = 0; i < n; i++) {
            left[i] = left_product;
            left_product *= nums[i];
        }
        
        // Calculate the product of elements to the right of each element.
        int right_product = 1;
        for (int i = n - 1; i >= 0; i--) {
            right[i] = right_product;
            right_product *= nums[i];
        }
        
        // Calculate the final result by multiplying corresponding left and right products.
        for (int i = 0; i < n; i++) {
            ans[i] = left[i] * right[i];
        }
        
        return ans;
    }
};

```

### Code(Python)
```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        pro = 1
        rpro = 1
        ans = []
        left = []
        right = []
        
        # Calculate the product of elements to the left of each element.
        for x in nums:
            left.append(pro)
            pro = pro * x
        
        # Calculate the product of elements to the right of each element.
        for x in reversed(nums):
            right.append(rpro)
            rpro = rpro * x
        
        # Calculate the final result by multiplying corresponding left and right products.
        for i in range(len(nums)):
            ans.append(left[i] * right[len(nums) - 1 - i])
        
        return ans

```

### 🟢Approach 2:Calculate left and right products iteratively to obtain product of all array elements except self.

### Intuition
The initial thought is to calculate the product of all elements to the left and right of each element in the array.

### Approach
1. Initialize an array `ans` with ones to store the final product of elements.
2. Iterate through the array from left to right.
    - Calculate the product of elements to the left of each element and update the `ans` array accordingly.
3. Initialize a variable `rightSum` to store the product of elements to the right.
4. Iterate through the array from right to left.
    - Update the `ans` array by multiplying it with the product of elements to the right of each element.
5. Return the `ans` array as the final result.

### Complexity
- Time complexity:
    - The time complexity is O(n) as we iterate through the array twice.
- Space complexity:
    - The space complexity is O(n) for the result array.

### Code(C++)
```c++
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        // Get the size of the input array.
        int n = nums.size();
        
        // Initialize the result array with ones.
        vector<int> ans(n, 1);
        
        // Initialize a variable to store the product of elements to the left.
        int leftSum = 1;
        
        // Calculate the product of elements to the left of each element.
        for (int i = 0; i < n; i++) {
            ans[i] = leftSum;
            leftSum = leftSum * nums[i];
        }
        
        // Initialize a variable to store the product of elements to the right.
        int rightSum = 1;
        
        // Update the result by multiplying with the product of elements to the right.
        for (int i = n - 1; i >= 0; i--) {
            ans[i] = ans[i] * rightSum;
            rightSum = rightSum * nums[i];
        }
        
        return ans;
    }
};


```

### Code(Python)
```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        # Initialize the result array with ones.
        ans = [1] * (len(nums))

        # Calculate the product of elements to the left of each element.
        for i in range(1, len(nums)):
            ans[i] = ans[i-1] * nums[i-1]

        # Initialize a variable to store the product of elements to the right.
        rightSum = 1

        # Update the result by multiplying with the product of elements to the right.
        for i in range(len(nums) - 1, -1, -1):
            ans[i] *= rightSum
            rightSum *= nums[i]

        return ans
```



## 7️⃣Valid Sudoku (Medium)
[Valid Sudoku](https://leetcode.com/problems/valid-sudoku/description/)
![Valid Sudoku](images/Valid%20Sudoku.png)


### 🟢Approach 1:Utilizes sets to validate rows, columns, and 3x3 subgrids in a Sudoku board efficiently.
### Intuition
The initial thought is to iterate through the Sudoku board and check whether the placement of each number is valid.

### Approach
1. Initialize an empty list `r` to store seen elements in rows, columns, and 3x3 subgrids.
2. Iterate through the Sudoku board using two nested loops.
3. For each element encountered in the board:
   - Check if the element is not '.' (an empty cell).
     - If not empty, perform the following checks:
       - Check for violations in the current row by appending the tuple `(i, ele)` to `r`.
       - Check for violations in the current column by appending the tuple `(ele, j)` to `r`.
       - Check for violations in the current 3x3 subgrid by appending the tuple `(i // 3, j // 3, ele)` to `r`.
4. After iterating through the entire board, check if there are any violations. If the length of the list `r` is not equal to the length of the set created from `r`, return False, indicating a violation.
5. If the entire board is iterated without any violations, return True, indicating a valid Sudoku board.

### Explanation:
- When an element is not empty (i.e., not '.'), it is checked for violations in the current row, column, and subgrid.
- Violations can occur if the same number is found more than once in the same row, column, or subgrid.
- The tuple `(i // 3, j // 3, ele)` is used to represent the subgrid. This helps identify the unique 3x3 subgrid for each element in the board.
- The use of a set in the last step ensures that each tuple in `r` is unique, checking for violations across rows, columns, and subgrids.
- The return statement checks whether the length of `r` is equal to the length of the set. If they are equal, it means there are no violations, and the Sudoku board is valid.

### Complexity
- Time complexity:
    - The time complexity is O(1) since the size of the Sudoku board is fixed (9x9).
- Space complexity:
    - The space complexity is O(1) since the size of the sets used for tracking elements in rows, columns, and subgrids is fixed.

### Code
```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        # Initialize an empty list to store seen elements in rows, columns, and subgrids.
        r = []

        # Iterate through the Sudoku board.
        for i in range(9):
            for j in range(9):
                ele = board[i][j]
                # Check if the element is not '.' (empty cell).
                if ele != '.':
                    # Check for violations in the current row, column, and subgrid.
                    r += [(i, ele), (ele, j), (i // 3, j // 3, ele)]

        # Return True if there are no violations, i.e., the length of the list is equal to the length of the set.
        return len(r) == len(set(r))
```

### 🟢Approach 2: Validates Sudoku rules using boolean arrays to track digits in rows, columns, and subgrids.
### Intuition

The intuition is to check the validity of a Sudoku board by ensuring that each row, each column, and each of the nine 3x3 subgrids contains all the digits from 1 to 9 without repetition.

### Approach

1. Initialize three sets: `cols` for columns, `rows` for rows, and `subGrid` for 3x3 subgrids.
2. Iterate through each cell in the Sudoku board using two nested loops.
3. Check if the current cell contains a digit (not a dot).
   - If yes, proceed to the next step.
   - If no, continue to the next cell.
4. Check if the digit is already present in the corresponding row, column, or subgrid.
   - If yes, return False as it violates the Sudoku rules.
   - If no, add the digit to the sets for the current row, column, and subgrid.
5. Continue the iteration until all cells are processed.
6. If the iteration completes without returning False, the Sudoku board is valid, and the function returns True.

### Complexity
- Time complexity:
The time complexity is O(1) since the size of the Sudoku board is fixed.

- Space complexity:
The space complexity is O(1) as well, considering the fixed-size sets used for each row, column, and subgrid.
  
### Code
```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        # Initialize three sets to keep track of digits in each column, row, and subgrid.
        cols = collections.defaultdict(set)
        rows = collections.defaultdict(set)
        subGrid = collections.defaultdict(set)  # key = (r / 3, c / 3)

        # Iterate through each cell in the Sudoku board.
        for r in range(9):
            for c in range(9):
                # Skip empty cells represented by dots.
                if board[r][c] == ".":
                    continue

                # Check if the digit is already present in the corresponding row, column, or subgrid.
                if (
                    board[r][c] in rows[r]
                    or board[r][c] in cols[c]
                    or board[r][c] in subGrid[(r // 3, c // 3)]
                ):
                    # If yes, return False as it violates the Sudoku rules.
                    return False

                # Update the sets for the current row, column, and subgrid with the current digit.
                cols[c].add(board[r][c])
                rows[r].add(board[r][c])
                subGrid[(r // 3, c // 3)].add(board[r][c])

        # If the iteration completes without returning False, the Sudoku board is valid, and the function returns True.
        return True

```

### 🟢Approach 3:Ensures Sudoku validity by employing boolean arrays to detect duplicates in rows, columns, and subgrids.

### Intuition
My initial thoughts are to maintain sets or arrays to keep track of the digits in each row, column, and 3x3 subgrid to validate the rules of Sudoku.

### Approach
1. Initialize three 2D boolean arrays (`row`, `col`, `subGrid`) to keep track of digits encountered in each row, each column, and each 3x3 subgrid.
   - Example:
     - `row[r][d]` is true if digit `d+1` is already present in the `r`-th row.
     - `col[c][d]` is true if digit `d+1` is already present in the `c`-th column.
     - `subGrid[g][d]` is true if digit `d+1` is already present in the `g`-th 3x3 subgrid.

2. Iterate through each cell in the Sudoku board.
   - Skip empty cells represented by dots ('.').
   - Convert the character digit to a numerical index (`idx`) by subtracting the ASCII value of '0' and subtracting 1.
     - Example: If `board[r][c]` is '5', `idx` will be 4.
   - Determine the subgrid number (`gridNum`) based on the current cell's position.
     - Example: If `r = 4` and `c = 7`, then `gridNum` will be 5.

3. Check if the digit is already present in the corresponding row, column, or subgrid.
   - If `row[r][idx]`, `col[c][idx]`, or `subGrid[gridNum][idx]` is true, return false as it violates the Sudoku rules.

4. Update the boolean arrays for the current row, column, and subgrid with the current digit.
   - Set `row[r][idx]`, `col[c][idx]`, and `subGrid[gridNum][idx]` to true.

5. If the iteration completes without returning false, the Sudoku board is valid, and the function returns true.

### Complexity
- Time complexity:
  - The time complexity is O(1) since the size of the Sudoku board is fixed.
- Space complexity:
  - The space complexity is O(1) as the size of the Sudoku board is constant, and the arrays have fixed dimensions.
  
### Code
```cpp
class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {
        const int num = 9;
        // Initialize boolean arrays to track digits in each row, column, and subgrid
        bool row[num][num] = {false};
        bool col[num][num] = {false};
        bool subGrid[num][num] = {false};
        
        // Iterate through each cell in the Sudoku board
        for(int r = 0; r < num; ++r){
            for(int c = 0; c < num; ++c){
                // Skip empty cells
                if(board[r][c] == '.')
                    continue; // if not a number, proceed to the next cell
                
                // Convert character digit to numerical index
                int idx = board[r][c] - '0' - 1; // char to num idx
                // Determine the subgrid number based on the current cell's position
                int gridNum = (r/3) * 3 + (c/3);
                
                // Check if the number already exists in the corresponding row, column, or subgrid
                if(row[r][idx] || col[c][idx] || subGrid[gridNum][idx]){
                    return false; // if duplicate number found, the Sudoku board is invalid
                }
                
                // Update the boolean arrays for the current row, column, and subgrid with the current digit
                row[r][idx] = true;
                col[c][idx] = true;
                subGrid[gridNum][idx] = true;
            }
        }
        return true; // if no duplicates found, the Sudoku board is valid
    }
};

```


## 8️⃣Longest Consecutive Sequence (Medium)
[Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/description/)
![Longest Consecutive Sequence](images/Longest%20Consecutive%20Sequence.png)

### 🟢Approach 1:Using an unordered map to track consecutive sequences for finding the longest consecutive sequence.
# Intuition
The intuition behind this approach is to use an unordered map to efficiently check the presence of numbers and track consecutive sequences. We mark the potential starting points of consecutive sequences and explore each sequence to find the longest one.

### Approach
1. Create an unordered map `mp` to store whether a number is present in the input vector `nums`.
2. Iterate through the input vector and populate the unordered map with the presence of each number.
3. Iterate through the input vector again:
   - If `nums[i] - 1` is present in `mp`, mark `nums[i]` as not the start of a consecutive sequence by setting its value in the map to false.
   - If `nums[i] - 1` is not present in `mp`, it means `nums[i]` is potentially the start of a consecutive sequence.
4. Find the length of the consecutive sequences starting from the marked points and update the maximum length.
5. Return the length of the longest consecutive sequence.

### Complexity
- Time complexity: O(n), where n is the size of the input vector.
- Space complexity: O(n), due to the usage of the unordered map to store number presence.

### code(Python)
```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        # Step 1: Create a set 'num' to efficiently check the presence of numbers.
        num = set(nums)
        longest = 0

        # Step 2: Iterate through each number in 'nums'.
        for x in nums:
            # If 'x-1' is not in 'num', it means 'x' is potentially the start of a consecutive sequence.
            if x - 1 not in num:
                l = 0
                # Step 3: While (x + l) is in 'num', count the length of the consecutive sequence.
                while (x + l) in num:
                    l += 1
                # Update 'longest' if the current sequence length is greater.
                longest = max(l, longest)

        # Step 4: Return the length of the longest consecutive sequence.
        return longest

```

### code(C++)
```c++
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        // Step 1: Create an unordered map 'mp' to store whether a number is present in the input vector 'nums'.
        unordered_map<int, bool> mp;

        // Step 2: Iterate through the input vector and populate the unordered map with the presence of each number.
        int n = nums.size();
        for(int i = 0; i < n; i++) {
            mp[nums[i]] = true;
        }

        // Step 3: Iterate through the input vector again:
        for(int i = 0; i < n; i++) {
            // If 'nums[i] - 1' is present in 'mp', mark 'nums[i]' as not the start of a consecutive sequence by setting its value in the map to false.
            if(mp.count(nums[i] - 1) > 0) {
                mp[nums[i]] = false;
            }
        }

        // Step 4: Find the length of the consecutive sequences starting from the marked points and update the maximum length.
        int ml = 0;
        for(int i = 0; i < n; i++) {
            if(mp[nums[i]] == true) {
                int j = 0, c = 0;
                // Count the length of the consecutive sequence starting from 'nums[i]'.
                while(mp.count(nums[i] + j) > 0) {
                    j++;
                    c++;
                }
                // Update 'ml' if the length of the current sequence is greater.
                if(c > ml) {
                    ml = c;
                }
            }
        }

        // Step 5: Return the length of the longest consecutive sequence.
        return ml;
    }
};

```

### 🟢Approach 2:Sorting the array simplifies identifying consecutive numbers, finding the longest sequence in O(n log n) time.
### Intuition
The intuition behind this approach is to sort the input array and then iterate through it to find the length of the longest consecutive sequence. Sorting simplifies the process of identifying consecutive numbers.

### Approach
1. Check if the input array is empty. If it is, return 0, as there is no consecutive sequence.
2. Sort the input array in ascending order.
3. Initialize variables `maxLength` and `currentLength` to 1.
4. Iterate through the sorted array, starting from the second element.
5. For each element, check if it is consecutive to the previous one.
   - If yes, increment `currentLength`.
   - If not, reset `currentLength` to 1.
6. Update `maxLength` with the maximum of its current value and `currentLength`.
7. Return `maxLength` as the length of the longest consecutive sequence.

### Complexity
- Time complexity: O(n log n) due to the sorting operation, where n is the size of the input array.
- Space complexity: O(1) as we use a constant amount of extra space for variables.

### Code(Python)
```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        if not nums:
            return 0

        # Step 1: Sort the input list in ascending order.
        nums.sort()

        # Step 2: Initialize variables 'maxLength' and 'currentLength' to 1.
        maxLength = 1
        currentLength = 1

        # Step 3: Iterate through the sorted array, starting from the second element.
        for i in range(1, len(nums)):
            # Step 4: Check if the current number is not equal to the previous one.
            if nums[i] != nums[i - 1]:
                # Step 5: If the current number is one more than the previous one, it is part of the consecutive sequence.
                if nums[i] == nums[i - 1] + 1:
                    currentLength += 1
                else:
                    # If not consecutive, reset the current length.
                    currentLength = 1

                # Step 6: Update the maximum length.
                maxLength = max(maxLength, currentLength)

        # Step 7: Return 'maxLength' as the length of the longest consecutive sequence.
        return maxLength

```

### Code(C++)
```c++
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        // Step 1: Check if the input array is empty. If it is, return 0 as there is no consecutive sequence.
        if (nums.empty()) {
            return 0;
        }

        // Step 2: Sort the input array in ascending order.
        sort(nums.begin(), nums.end());

        // Step 3: Initialize variables 'maxLength' and 'currentLength' to 1.
        int maxLength = 1;
        int currentLength = 1;

        // Step 4: Iterate through the sorted array, starting from the second element.
        for (int i = 1; i < nums.size(); ++i) {
            // Step 5: Check if the current number is not equal to the previous one.
            if (nums[i] != nums[i - 1]) {
                // Step 6: If the current number is one more than the previous one, it is part of the consecutive sequence.
                if (nums[i] == nums[i - 1] + 1) {
                    ++currentLength;
                } else {
                    // If not consecutive, reset the current length.
                    currentLength = 1;
                }

                // Step 7: Update the maximum length.
                maxLength = max(maxLength, currentLength);
            }
        }

        // Step 8: Return 'maxLength' as the length of the longest consecutive sequence.
        return maxLength;
    }
};

```




