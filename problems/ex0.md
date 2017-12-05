# 跳跃游戏

## 思路

>关键在于，如果能走到第i个点，则之前的所有点都[可以走到](prove.html)。所以，每个点尽量往远处走，直到到达第n个点（true）或者无法继续往前（false）。代码中用一个变量保存当前可能的最远点即可。

## 实现

```cpp
//The code bellow is only for algorithm testing and contains *no* comments.  Some parts are *not* suitable for projects.
//Copy is *not* allowed.


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