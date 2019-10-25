1 Two Sum 

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have ***exactly\*** one solution, and you may not use the *same* element twice.

 **Example:** 

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

If we use the normal way to find target, it will be  Time Limit Exceeded. Because the time complex is  O(n^2). So we should find an  O(n)  algorithm to solve the problem. Hash Map is a good way to reduce the time, but increase the space complex.

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> m; //remember the initialization of Hash map
        vector<int> res;
        for (int i = 0; i < nums.size(); i++){
            m[nums[i]] = i;
        }
        for (int i = 0; i < nums.size(); i++){
            int t= target - nums[i];
            if (m.count(t) && m[t] != i) {//m.count means if t is in the map, value=1, otherwise 0
                res.push_back(i);
                res.push_back(m[t]);
                break;
            }
        }
        return res;
    }
};
```

 https://blog.csdn.net/qq_26399665/article/details/52295380 