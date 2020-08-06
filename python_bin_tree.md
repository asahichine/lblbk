##### 前序遍历 迭代

~~~python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        ret, stack = [], [root]
        while stack:
            node = stack.pop()
            if node:
                ret.append(node.val)
                stack.append(node.right)  # 栈是先进后出
                stack.append(node.left)
        return ret
~~~

##### 中序遍历

~~~python
Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    def inorderTraversal(self, root):
        ret, stack = [], []
        while stack or root:
            if root:
	            stack.append(root)
	            root = root.left
	        else:
		        temNode = stack.pop()
		        ret.append(temNode.val)
		        root = temNode.right
		return ret
~~~

后续

~~~python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        ret, stack = [], []
        while root or stack:
            if root:
                stack.append(root)
                ret.insert(0, root.val)
                root = root.right
            else:
                node = stack.pop()
                root = node.left
        return ret
~~~

~~~python
# 层次遍历 搞不明白
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        ans, level = [], [root]
        while any(level):
            ans.append([node.val for node in level])
            level = [kid for n in level for kid in (n.left, n.right) if kid]
        return ans
~~~

