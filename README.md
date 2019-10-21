# DailyStudy

## Content
<!-- vim-markdown-toc GFM -->
* [1. 两数之和](#TwoSum)
* [2. 整数反转](#ReverseInteger)
* [3.](#3.)
* [4.](#4.)
<!-- vim-markdown-toc -->

## TwoSum
* 给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素
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
* 给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转
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

