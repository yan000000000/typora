





# **集合**

- ### 并查集(Union-Find)

  **定义**：并查集是一种用于处理一些元素分组问题的数据结构，它可以高效地**合并**两个集合，以及**查询**一个元素属于哪个集合。

  **代码实现**：

  ```python
  class UnionFind:
      def __init__(self, n):
          self.parent = list(range(n))
  
      def find(self, x):
          if self.parent[x] != x:
              self.parent[x] = self.find(self.parent[x])
          return self.parent[x]
  
      def union(self, x, y):	
          root_x = self.find(x)
          root_y = self.find(y)
          if root_x != root_y:
              self.parent[root_y] = root_x
  ```

  **解析**：

  	1. `parent`列表用于存储每个元素的父节点。初始时，每个元素的父节点都是它自己。
  	1. `find`方法用于查找元素的根节点（也就是所在集合的代表元素）。如果一个元素的父节点不是它自己，那么就继续向上查找。同时，为了优化后续的查找操作，我们在查找的过程中将元素的父节点直接设置为根节点。
  	1. `union`方法用于合并两个元素所在的集合。它首先找到两个元素的根节点，然后如果它们不在同一个集合中，就将其中一个集合的根节点的父节点设置为另一个集合的根节点，从而完成合并。

# 排序Sorting

- ## Bubble Sort 冒泡排序

  - **定义**：冒泡排序 bubble sort通过连续地比较与交换相邻元素实现排序。这个过程就像气泡从底部升到顶部一样，因此得名冒泡排序。

  - **代码实现**：

    ```python
    def bubble_sort(arr):
        n = len(arr)
        
        swapped = False					# 引入一个标记，表示这一轮中是否有元素被交换
        
        for i in range(n):				# 遍历所有数组元素
            							# 每一次大循环后，最后的i个元素已经是排序好的了，所以不需要再次遍历它们
            for j in range(0, n-i-1): 	# 遍历数组从0到n-i-1
                if arr[j] > arr[j+1]:	# 交换如果发现元素是逆序的,交换它们
                    arr[j], arr[j+1] = arr[j+1], arr[j]
                    swapped = True  	# 发生了交换，设置标记为True
            if not swapped:				# 如果这一轮没有发生交换，意味着数组已经是有序的，可以提前结束排序
                break
        return arr
    ```

  - **时间复杂度**：

    - 最坏：$f(n)=n+(n-1)+(n-2)+...+2+1=\frac{n(n+1)}{2}=O(n^2)$
    - 最好：$f(n)=\theta(n)$​









