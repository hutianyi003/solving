# 跳跃游戏

## 题目

### 描述

给定一个非负整数数组，假定你的初始位置为数组第一个下标。
数组中的每个元素代表你在那个位置能够跳跃的最大长度。

请确认你是否能够跳跃到数组的最后一个下标。

例如：A = [2,3,1,1,4] 能够跳跃到最后一个下标，输出true；  
A = [3,2,1,0,4] 不能跳跃到最后一个下标，输出false。

## 思路

>关键在于，如果能走到第i个点，则之前的所有点都[可以走到](./prove.md)。所以，每个点尽量往远处走，直到到达第n个点（true）或者无法继续往前（false）。代码中用一个变量保存当前可能的最远点即可。

## 实现

```cpp
//The sample code is only for algorithm testing therefore contains no comments and not suitable for real-world projects.
//Copy is NOT allowed.


#include <iostream>

const int MaxN = 510;
int r[MaxN];

int main()
{
    int n;
    std::cin >> n;
    for (int i = 1; i <= n; i++)
        std::cin >> r[i];
    int nowmaxdis = 1;
    for (int i = 1; i <= n; i++) {
        if (nowmaxdis < i)
            break;
        if (i + r[i] > nowmaxdis)
            nowmaxdis = i + r[i];
    }
    if (nowmaxdis >= n)
        std::cout << "true";
    else
        std::cout << "false";
    return 0;
}
```