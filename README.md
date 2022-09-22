// Solution Uploaded By Surendra Tholiya (IIT2021097)

class Solution {
public:
    void solve(int idx,vector<int>&arr,int n,vector<int>&ans,set<vector<int>>&ds){
        if(idx==n){
            ds.insert(ans);
            return;
        }
        for(int i=idx;i<n;i++){
            if(i>idx && arr[i]==arr[i-1]){
                continue;
            }
            ans.push_back(arr[i]);
            solve(i+1,arr,n,ans,ds);
            ans.pop_back();
            
            solve(i+1,arr,n,ans,ds);
        }
    }
    
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
       int n=nums.size();
        sort(nums.begin(),nums.end());
        vector<int>ans;
        set<vector<int>>ds;
        vector<vector<int>>v1;
        solve(0,nums,n,ans,ds);
        for(auto it:ds){
            v1.push_back(it);
        }
        return v1;
    }
};
