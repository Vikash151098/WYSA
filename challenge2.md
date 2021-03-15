/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
 # solution of valid Binary search Tree
class Solution {
    public boolean isValidBST(TreeNode root) {
        if(root==null)
        {
            return true;
        }
        TreeNode left =root.left;
        TreeNode right =root.right;
        boolean le=true,ri=true;
        if(left!=null&&root.val<=left.val)
        {
           return false;    
        }
        if(right!=null&&root.val>=right.val)
        {
           return false;   
        }
        
        return isValidBST(left)&&isValidBST(right);
    }
}