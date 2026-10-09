# Leaf-Similar-Trees
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def leafSimilar(self, root1: TreeNode | None, root2: TreeNode | None) -> bool:
        if root1 is None or root2 is None:
            return False
        r1=[]
        r2=[]
        def add(root,r):
            if root is None:
                return
            if root.left is None and root.right is None:
                r.append(root.val)
                return
            add(root.left,r)
            add(root.right,r)
        add(root1,r1)
        add(root2,r2)
        if len(r1)!=len(r2):
            return False
        for i in range(len(r1)):
            if r1[i]!=r2[i]:
                return False
        return True
