## Two Sum
 * 思路：建一个map, key是vector的值，value是在vector中的索引, 然后当target-vector[i]是map中的一个key时，返回[map[target-vector[i]],i]
 * 代码
 ```c++
  vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int,int> dict;
        vector<int> result;
        for(int i=0;i<nums.size();i++){ //vector是size
            sizeif (dict.find(target-nums[i]) != dict.end()){
                result.push_back(dict[target-nums[i]]); //push_back从后往前
                result.push_back(i);
                return result;
            }else{
                dict.insert(map<int,int>::value_type(nums[i],i)); //也可以dict[nums[i]] = i
            }
        }
        result.push_back(-1);
        result.push_back(-1);
        return result;
        
    }
 ```
 
 ## Add Two Numbers
  * 思路：对应位置加后，新的节点的值是相加后的值%10, 并且保留相加后的值/10, 往后传递
  
  * 代码:
  
  ```c++
  ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode *dummy = new ListNode(0), *p = dummy;
        int carry = 0;
        
        while (l1 || l2 || carry){
            if (l1){
                carry += l1->val;
                l1 = l1->next;
            }
            if(l2){
                carry += l2->val;
                l2 = l2->next;
            }
            p->next = new ListNode(carry%10);
            carry /= 10;
            p = p->next;
        }
        return dummy->next;
    }
  ```

## Longest Subtring without Repeating Charaters
 * 思路: 保留一个left值，这个值记录没有重复字符串的起点，i往前循坏，一个数组记录字符是否重复，如果重复更改left的值
 * 代码:
 
 ```c++
  int lengthOfLongestSubstring(string s) {
        int ans = 0, left = 0, len = s.length();
        int last[255];
        memset(last,-1,sizeof last); //初始化为-1
        for (int i = 0;i < len;i++){
            if(last[s[i]] >= left) left = last[s[i]] + 1;//有重复的值, 改变left的值
            last[s[i]] = i;// 更新key
            ans = max(ans,i-left+1);
        }
        return ans;
    }
 ```
 
 ## Median of Two Sorted Arrays
  
  * 思路：每次剔除前k/2的元素，如果k=1, 则返回较小的数min(A[A_start],B[B_start]), 若某个数组搜索完，则返回另一个数组的start元素+k-1
  
  * 代码:
  ```c++
      double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int len = nums1.size() + nums2.size();
        if (len % 2 == 1){
            return findK(nums1, 0, nums2, 0, len/2+1);
        } else{
            return (findK(nums1,0, nums2, 0, len/2) + findK(nums1,0, nums2, 0, len/2+1))/2.0;
        }
    }
    
    double findK(vector<int>& A, int A_start, vector<int>& B, int B_start, int k){
        if (A_start >= A.size()){
            return B[B_start+k-1]; //找到超过A长度的元素，返回}
        if (B_start >= B.size()){
            return A[A_start+k-1];
        }
        if (k == 1){
            return min(A[A_start],B[B_start]);
        }
        int A_key = (A_start + k/2-1) < A.size()?A[A_start + k/2-1]:INT_MAX;
        int B_key = (B_start + k/2-1) < B.size()?B[B_start + k/2-1]:INT_MAX;
        if(A_key > B_key){
            return findK(A,A_start,B,B_start+k/2,k-k/2);
        }else{
            return findK(A,A_start+k/2,B,B_start,k-k/2);
        }
    }
  ```

 ## Longest Palindromic Substring
  * 思路: 采用动归思想，p[i][j] = (s[i] == s[j]) && (i-j<2 || p[j+1][i-1])
  * 代码:
 
  ```c++
   string longestPalindrome(string s) {
        int len = s.size();
        int p[len][len]; //声明数组存放每次的比较结果
       memset(p,0,len*len*sizeof(int));
        int maxL = 0, start=0, end=0;
        for(int i=0;i < s.size();i++){
            for(int j = 0;j<i;j++){
                p[j][i] = (s[j] == s[i]) && (i-j<2 || p[j+1][i-1]); //关键
                if(p[j][i] && maxL < (i-j+1)){
                    maxL = i-j+1;
                    start = j;
                    end = i;
                }
            }
            p[i][i] = 1;
        }
        return s.substr(start,end-start+1);
    }
  ```
