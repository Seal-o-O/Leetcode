5 Longest Palindromic Substring

Medium

4617417Share

Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s** is 1000.

**Example 1:**

```
Input: "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```

**Example 2:**

```
Input: "cbbd"
Output: "bb"
```

```c++
class Solution {
public:
    string longestPalindrome(string s) {
        if(s.size() < 2) return s; //only 1 or 2 characters
        int start_idx = 0, max_len = 0;
        int i = 0;
        while(i < s.size()){
            int r_ptr = i;
            int l_ptr = i;
            //find the middle of a palindrome
            while(r_ptr < s.size()-1 && s[r_ptr] == s[r_ptr + 1]) r_ptr++;
            i = r_ptr+1;
            //expend from the middle out
            while(r_ptr < s.size()-1 && l_ptr > 0 && s[r_ptr + 1] == s[l_ptr - 1]){
                r_ptr++;
                l_ptr--;
            }
            int new_len = r_ptr - l_ptr + 1;
            if(new_len > max_len){
                start_idx = l_ptr;
                max_len = new_len;
            }
        }
        return s.substr(start_idx, max_len);
        
    }
};
```

