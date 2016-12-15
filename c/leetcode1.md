## ZigZag Conversion
 * 思路：最后一行和第一行的间隔是2*n-2, 中间的是每两个数间隔加起来是2*n-2
 * 代码:
   
   ```c++
    string convert(string s, int numRows) {
        if(numRows == 1) return s;
        int len = s.size(),k=0, interval = (numRows<<1)-2;
        string res(len,' ');
        for(int j = 0;j < len;j += interval) res[k++] = s[j]; //第一行间隔是2*n-2
        for(int i = 1;i < numRows-1;i++){
            int inter = (i << 1); //中间第3个位置和第2个位置的距离
            for(int j = i;j <len;j+=inter){
                res[k++] = s[j];
                inter = interval-inter; //中间第1个位置和第2个位置的距离
            }
        }
        for(int j = numRows-1;j < len;j += interval) res[k++] = s[j];
        return res;
      }
   ```
   
 ## Reverse Integer
   * 思路:
   * 代码:
      
   ```c++
   int reverse(int x) {
        if(x == 0) return x;
        if(x == INT_MIN) return 0;
        bool neg = (x < 0);
        long rtn = 0, prev = 0;
        x = neg ? -1 * x : x;
        while(x != 0){
            rtn = rtn * 10 + x % 10; //结果每次乘以10
            x = x / 10;
            if(prev > rtn) return 0;
        }

        if(neg) rtn = rtn * -1;
        if(rtn < INT_MIN || rtn > INT_MAX) return 0;
        return rtn;
    }
   ```
   
 ## String to Integer
 
   * 思路: 先去掉前后的空格，遍历遇到为空的跳过，遇到不是数字的，就结束循环
   
   * c++ string.erase(位置,长度，要擦除的字符) 不指定长度, 擦除当前位置元素, 不指定要擦除的元素，都擦除.
   
   * string.find_first_not_of(ss) 返回第一个string中不在ss中字符的索引
   
   * 代码 
   ```c++
   int myAtoi(string str) {
        if (str == "") return 0;
        str.erase(0,str.find_first_not_of(' ')); //去掉前面的空格
        str.erase(str.find_last_not_of(' ')+1); //去掉最后的空格
        int i = 0, len = str.length(),sign = 1;
        while(i < len && str[i] == ' ') i++; //若是空格，跳过
        if(i == len) return 0;
        if(str[i] == '+'){
            sign = 1;
            i++;
        }else{
            if(str[i] == '-'){
                sign = -1;
                i++;
            }
        }
        long long ret = 0;
        for(;i < len;i++){
            if(str[i] < '0' || str[i] > '9') break; //若不是数字，break
            ret = ret*10 + (str[i]-'0');
            if(ret > INT_MAX) break;
        }
        ret *= sign;
        if(ret > INT_MAX) return INT_MAX;
        if(ret < INT_MIN) return INT_MIN;
        return ret;
        
    }
   ```
 
## Palindrome Number
      * 思路：前后指针，不相等返回false
      * 代码
      
      ```c++
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
