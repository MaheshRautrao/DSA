Problem link ---> https://practice.geeksforgeeks.org/problems/boundary-traversal-of-binary-tree/

class Solution {
public:

// left part of tree
void left(Node* root,vector<int> &ans)
{
    if(!root->left){
         ans.push_back(root->data);
        return ;
    } 
    
    queue<Node*> q;
    q.push(root);
    
    while(!q.empty())
    {
        Node* node = q.front();
        q.pop();
        
        
        
        if(node->left) q.push(node->left);
        else if(node->right ) q.push(node->right);
        else return;
        
        
        ans.push_back(node->data);
        
    }
}

// all leafs
void leaf(Node* root,vector<int> &ans)
{

     if(!root)  return;
     
     if(!root->left && !root->right) {
         ans.push_back(root->data);
         return;
     }
  
     leaf(root->left,ans);
     
     leaf(root->right,ans);
     
}

//right part of tree
void right(Node* root,vector<int> &ans)
{
    // root is already included in left
    root = root->right;
    
    if(!root) return ;
    
    queue<Node*> q;
    q.push(root);
    
    vector<int > temp;
    while(!q.empty())
    {
        Node* node = q.front();
        q.pop();
        
        if(node->right) q.push(node->right);
        else if(node->left) q.push(node->left);
        else 
        {
            for(int i=temp.size()-1;i>=0;i--) ans.push_back(temp[i]);
            return;
        }
        
        temp.push_back(node->data);
    }
    
    
}

    vector <int> boundary(Node *root)
    {
        //Your code here
        vector<int> ans;
        if(!root) return ans;
        if(!root->left && !root->right) {
            ans.push_back(root->data);
            return ans;
        }
        left(root,ans);
        leaf(root,ans);
        right(root,ans);
        return ans;
    }
};
