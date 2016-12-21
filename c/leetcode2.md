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
