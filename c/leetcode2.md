## Palindrome Number
* 题意：决定一个整数是否是回文
* 思路双向指针
* 代码
```python
  bool isPalindrome(int x) {
        if(x == 0) return true;
        if(x < 0) return false;
        string s = to_string(x);
        int left = 0, right = s.size()-1;
        while(left < right){
            if(s[left++] != s[right--]) return false;
        }
        return true;
    }
```

## Regular Expression Matching  
* 题意：实现一个正则表达，实现*和.
* 思路：


## Container With Most Water
* 题意：给一系列的整数，找出两个整数围起来的面积最大
* 思路：前后两个指针，首先算出这两个整数之间的面积，移动较小的那一根(前移或后移)
* 代码
```python
  int maxArea(vector<int>& height) {
        int maxarea = 0;
        int start = 0;
        int area = 0;
        int end = height.size()-1;
        while(start < end){
            if(height[end] < height[start]){
                area = height[end]*(end-start);
                end--;
            }
            else{
                area = height[start]*(end-start);
                start++;
                
            }
            maxarea = max(maxarea,area);
        }
        return maxarea;
    }
```

## Longest Common Prefix  
* 题意：发现最长前缀在string的list中
* 思路：就是一个一个string比较，每次去小的orefix
* 代码
```python
  int helper(string olds, string news){
        for(int i =0;i<min(olds.size(),news.size());i++){
            if (olds[i] != news[i]) return i;
        }
        return min(olds.size(),news.size());
    }

    string longestCommonPrefix(vector<string>& strs) {
        if(strs.size() == 0) return "";
        string rtn = strs[0];
        for(int i = 1;i <strs.size()&&rtn != "";i++){
            rtn = rtn.substr(0,helper(rtn,strs[i])); //c++中截取字符串 substr(start,end)
            }
    return rtn;
        
    }
```

## 3Sum
* 题意：给定一个数组和一个目标值，找出3个加起来等于目标值的数组
* 思路：先排序，然后前后两个指针，当前指针和后指针，这个题最主要的就是每次固定一个点，设置两个指针遍历剩余的点
* 代码
```python
vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> res;
        int len = nums.size();
        if(len < 3){
            return res;
        }
        sort(nums.begin(),nums.end()); //排序
        for(int i=0;i<len;i++){     //每次固定一个初始位置
            if(nums[i]>0) break;
            if(i>0 && nums[i]==nums[i-1]) continue;
            int begin=i+1, end=len-1; //初始化start,end
            while(begin<end){
                int sum=nums[begin]+nums[i]+nums[end];
                if(sum == 0){
                    vector<int> t;
                    t.push_back(nums[i]);
                    t.push_back(nums[begin]);
                    t.push_back(nums[end]);
                    res.push_back(t);
                    begin++,end--;
                    while(begin<end && nums[begin] == nums[begin-1]) begin++;
                    while(begin<end && nums[end] == nums[end+1] ) end--;
                    
                }else if(sum > 0){
                    end--; // 当sum>0 end-- 减小sum
                }else{
                    begin++; // 当sum<0 start++ 增加sum
                }
            }
        }
        return res;
    }
```
