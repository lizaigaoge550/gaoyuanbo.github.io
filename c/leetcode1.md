## ZigZag Conversion
 * 思路：最后一行和第一行的间隔是2*n-2, 中间的是每两个数间隔加起来是2*n-2
 * 代码:
   ```c++
    string convert(string s, int numRows) {
        if(numRows == 1) return s;
        int len = s.size(),k=0, interval = (numRows<<1)-2;
        string res(len,' ');
        for(int j = 0;j < len;j += interval) res[k++] = s[j];
        for(int i = 1;i < numRows-1;i++){
            int inter = (i << 1);
            for(int j = i;j <len;j+=inter){
                res[k++] = s[j];
                inter = interval-inter;
            }
        }
        for(int j = numRows-1;j < len;j += interval) res[k++] = s[j];
        return res;
      }
   ```
