# DailyStudy

## Content
<!-- vim-markdown-toc GFM -->
* [1. 两数之和](#TwoSum)
* [2. 整数反转](#ReverseInteger)
* [3.](#3.)
* [4.](#4.)
<!-- vim-markdown-toc -->

## TwoSum
* 本题具有多种解法
  * 简单一点的可以直接暴力遍历求解，时间复杂度为O(N)
  * 通过hash表构建索引，由于hash表索引速度是常数时间，一次遍历。可将时间复杂度优化至O(N)
    * code:
      ```cpp
      class Solution 
      {
      public:
      vector<int> twoSum(vector<int>& nums, int target) 
      {
        int len = nums.size();
        unordered_map<int, int> hashMap;
        for(int i = 0; i < len; ++i)
        {   
            if(hashMap.find(target-nums.at(i))!=hashMap.end())
            {
                auto iter = hashMap.find(target-nums.at(i));
                vector<int> index = {i, iter->second};
                return index;
            }
            hashMap.emplace(make_pair(nums.at(i), i));
        }
        throw "No Solution!";
        }
      };
      ```
      
## ReverseInteger
* 本题主要考察数据溢出
  * 32位环境下，2^31-1=2147483647,-2^31=-2147483648
  * 在数据运算即将溢出时捕获并退出
    * code:
      ```cpp
      class Solution {
      public:
      int reverse(int x) {
      if (x == 0)
      return 0;
      int result = 0;
      while (x != 0)
      {
      int pop = x % 10;
      if (result > INT_MAX / 10) return 0;
      if (result < INT_MIN / 10) return 0;
      result = result * 10 + pop;
      x /= 10;
      }
      return result;
      }
      };
      ```

