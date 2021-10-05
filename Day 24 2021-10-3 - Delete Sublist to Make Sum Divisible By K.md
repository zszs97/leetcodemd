# 开始刷题

## 题目简介

 
【Day 24】2021-10-3 - (Delete Sublist to Make Sum Divisible By K)
-------------------


### 题目思路

+ 晚点看 

## 题目代码
### 代码块
``` c++
int floorMod(const int& a, const int& b)
{
    return (a % b + b) % b;
}
int solve(vector<int>& nums, int k) {
    int allSum = 0;
    for (int& num : nums)
        allSum += num;

    allSum = floorMod(allSum, k);
    unordered_map<int, int> dict;
    dict[0] = -1;

    int preSum = 0;
    int minLen = nums.size();
    for (int i = 0; i < nums.size(); i++) {
        preSum += nums[i];
        int mod = floorMod(preSum, k);
        dict[mod] = i;

        if (dict.count(floorMod(preSum - allSum, k)))
            minLen = min(minLen, i - dict[floorMod(preSum - allSum, k)]);
    }
    return minLen == nums.size() ? -1 : minLen;
}
```

## 复杂度
+ 空间复杂度 O(min(n,k) 
+ 时间复杂度 O(n)
