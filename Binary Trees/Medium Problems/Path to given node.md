problem link --> https://www.interviewbit.com/problems/path-to-given-node/

```
 bool helper(vector<int>&ans,TreeNode* root,int node)
 {
     if(!root) return false;
     
     ans.push_back(root->val);
     
     if(root->val == node) return true;
     
     if(helper(ans,root->left,node) || helper(ans,root->right,node)) return true;
     
     ans.pop_back();
     return false;
 }
 
vector<int> Solution::solve(TreeNode* A, int B) {
    vector<int> ans;
    helper(ans,A,B);
    return ans;
}
```
