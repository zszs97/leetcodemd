# 开始刷题

## 题目简介

 
【Day 2 】2021-09-11 - (821. 字符的最短距离)
-------------------


### 题目思路

+ 从当前下标出发，分别向左、右两个方向去寻找目标字符 C。
+ 只在一个方向找到的话，直接计算字符距离
+ 两个方向都找到的话，取两个距离的最小值
+ 正反两趟遍历，比较与c的距离，取小的值

## 题目代码
### 代码块
``` c++
class Solution {
public:
    vector<int> shortestToChar(string s, char c) {
        vector<int> str(s.length());

        for(int i = 0;i<s.length();i++)
        {
            if(s[i] == c) continue;
            int left = i;
            int right = i;
            int dist = 0;
            while(left >0 || right <= s.length()-1){  //left:往左边的指针 right：往右边的指针
                if(s[left] == c) {
                    dist = i-left;
                    break;
                }
                if(s[right] == c){
                    dist = right -i;
                    break;
                }
                if(left>0) left--;
                if(right<s.length()-1) right++;
            }
            str[i] = dist;
        }
        return str;
        
    }
};
```

## 复杂度
+ 空间复杂度 O(N)
+ 时间复杂度 O(N)，其中 N 为数组的长度