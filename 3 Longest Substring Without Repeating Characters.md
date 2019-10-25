3 Longest Substring Without Repeating Characters 

Given a string, find the length of the **longest substring** without repeating characters.

**Example 1:**

```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```

**Example 2:**

```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

```c++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        const int N = s.size();
        if (N<=1) return N;
        unordered_set<char> set;
        //using sliding window
        int res = 0;
        int l=0,r=0;
        while(r<N){
            while(set.count(s[r])){
                set.erase(s[l]);
                ++l;
            }
            set.insert(s[r]);
            res = max(res,int(set.size()));
            ++r;
        }
        return res;
    }
};
```

