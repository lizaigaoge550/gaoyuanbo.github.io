## Two Sum
 * 思路：建一个map, key是vector的值，value是在vector中的索引, 然后当target-vector[i]是map中的一个key时，返回[map[target-vector[i]],i]
 * 代码
 ```c++
  vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int,int> dict;
        vector<int> result;
        for(int i=0;i<nums.size();i++){
            if (dict.find(target-nums[i]) != dict.end()){
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
