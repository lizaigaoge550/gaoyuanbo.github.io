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
