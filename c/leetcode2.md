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
