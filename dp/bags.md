## 多重背包问题
* 使用滚动数组, 初始化将数组dp[]全部设置为0, 将dp[0]设为1. 利用双重循环i 从1到n遍历到w[i], 内层循环j 从v[i] 开始往后遍历, 只要dp[j-v[i]]的值为真(表示价值j-v[i]能满足)且dp[j]值为假(表示价值j未能满足)则价值j是有可能达到的.为什么说可能？是因为能否达到价值j也得看v[i]的数量是否达到上限. 所以开辟一个数组num[maxn]记录w[i]的数量. 在第一层循环内将数组num初始化为0, 一旦满足
dp[j-v[i]] && !dp[j] && num[j-v[i]] < w[i] 说明价值j是可以满足的. 则dp[j]的值为真, num[j] = num[j-v[i]]+1

* 模板
```python
for(int i=1;i<=n;i++)  
    {  
        memset(num,0,sizeof(num));  
        for(int j=v[i];j<=maxn;j++)  
        {  
            if(dp[j-v[i]&&!dp[j]&&num[j-v[i]]<w[i])   
            {  
                .......           //具体操作因题而异  
                num[j]=num[j-v[i]]+1;  //求num[j]对应的使用数  
            }  
        }  
    }  
```

* example
* n种价值的硬币，每种都有其数量w[i]，给一个最大价值量m求出不超过最大价值量的情况下能凑出多少种价值
```python
#include <iostream>  
#include <stdio.h>  
#include <string.h>  
using namespace std;  
  
int use[100001];  
int n,m;  
bool dp[100001];  
int v[1001],num[1001];  
int main()   
{  
    while (scanf("%d %d", &n, &m) != EOF)   
    {  
        if (n == 0 && m == 0) break;  
        for (int i = 0; i < n; ++i)  
            scanf("%d", a+i);  
        for (int i = 0; i < n; ++i)   
            scanf("%d", num+i);  
        int res = 0;  
        memset(dp,false,sizeof(dp));  
        dp[0] = true;  
        for (int i = 0; i < n; ++i)   
        {  
            memset(use,0,sizeof(use));  
            for (int j = a[i]; j <= m; ++j)   
            {  
                if (!dp[j] && dp[j-a[i]] && use[j-a[i]]<num[i])  
                {  
                    dp[j] = true;  
                    use[j] = use[j-a[i]] + 1;  
                    ++res;  
                }  
            }  
        }  
        printf("%d\n", res);  
    }  
 return 0;  
}  
```
