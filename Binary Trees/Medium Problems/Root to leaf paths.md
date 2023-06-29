https://practice.geeksforgeeks.org/problems/root-to-leaf-paths/

bool isLeaf(Node* root)
 {
     return !root->left && !root->right;
 }

// here we pass temp with reference so we need to pop it after returning. Dry run for better understanding. 
 
void helper1(Node* root,vector<vector<int>>&ans, vector<int>&temp)
{
    if(!root) return ;
    
    temp.push_back(root->data);
    
    if(isLeaf(root))
    {
        ans.push_back(temp);
        return ;
    }
    
    helper(root->left,ans,temp);
    if(root->left) temp.pop_back();
    helper(root->right,ans,temp);
      if(root->right) temp.pop_back();
}

// here we pass temp without reference 

void helper1(Node* root,vector<vector<int>>&ans, vector<int> temp)
{
    if(!root) return ;
    
    temp.push_back(root->data);
    
    if(isLeaf(root))
    {
        ans.push_back(temp);
        return ;
    }
    
    helper(root->left,ans,temp);
    helper(root->right,ans,temp);
     
}
 --------------------------------------------------- function ---------------------------
vector<vector<int>> Paths(Node* root)
{
 
    vector<vector<int>> ans;
    vector<int> temp;

//    helper1(root,ans,temp);
    helper2(root,ans,temp);

    return ans;
}
