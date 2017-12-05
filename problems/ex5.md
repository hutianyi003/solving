# 最长不重复子串

## 题目

### 描述

## 思路

## 实现

```cpp
//The sample code is only for algorithm testing therefore contains no comments and not suitable for real-world projects.
//Copy is NOT allowed.

#include <iostream>
#include <string>

const int alphaSize = 256;
int getMaxLenth(const std::string& s)
{
    if (s.size() == 0)
        return 0;
    int n = s.size(), l = 0;
    int ans = 1;
    bool vis[alphaSize] = { false };

    vis[s[0]] = true;
    for (int r = 1; r < n; r++) {
        while (vis[s[r]]) {
            vis[s[l++]] = false;
        }
        vis[s[r]] = true;
        if (r - l + 1 > ans)
            ans = r - l + 1;
    }
    return ans;
}

int main()
{
    std::string buffer;
    while (std::getline(std::cin, buffer)) {
        std::cout << getMaxLenth(buffer) << std::endl;
    }
    return 0;
}
```