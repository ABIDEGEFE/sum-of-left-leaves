# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def sumOfLeftLeaves(self, root):
        lsum = []
        isLeft = False
        def helper(root, lsum, isLeft):
            if not root:
                return 
            if not root.left and not root.right:
                if isLeft:
                    lsum.append(root.val)
            isLeft = True
            helper(root.left, lsum, isLeft)
            isLeft = False
            helper(root.right, lsum, isLeft)

            return lsum
        return sum(helper(root, lsum, isLeft))
        
        