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
