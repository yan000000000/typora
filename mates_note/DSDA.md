# Insertion Sort 插入排序

### Pseudo-code 伪代码

```python
for j<-1 to n-1 do #从数列的第二项开始，遍历未排序的数列，直到末尾
	key<-A[j] #赋值
  i=j-1 #当未排序的数列是j时，已排序数列的元素个数i为j-1（为了遍历已排序的数列）
  while i >= 0 and A[i]>key do #从已排序的数列最后一项开始，如果还没遍历完整个数列且这一项如果比要插入的元素大，就进入循环
  	A[i+1] = A[i] #将此项向前移动一位
  	i-- 
  A[i+1] = key #如果前面跳出了while循环，情况1:找到第A[i]项比要插入元素小，那么第A[i+1]项就是合适的位置，情况2:所有元素都比插入元素大，那么就放在第一项
  
```

### 时间复杂度

<img src="assets/螢幕截圖 2024-03-29 上午11.44.28.png" alt="螢幕截圖 2024-03-29 上午11.44.28" style="zoom:33%;" />

#### 详细分析

* C1,C2,...C7代表不同操作的常数时间成本，n是元素的总数，tj表示第j次迭代中while循环的执行次数，是一个变量。对于每个tj，其成本为C4+C5+C6
* 左边的cost代表执行一次所需要的时间成本，times则是执行次数
* C1包含了赋值与比较，当到第n项时发现不符合条件了才跳出，所以times会是n
* C2与C3则因为第n次跳出循环少了一次，所以为n-1
* C4与C1同理，包含当i为负数时与while条件进行比较的一次，所以下面两行命令为tj-1
* C5,C6则在每次while的第tj次时就跳出循环没有执行，所以为tj-1
* **疑惑：**为什么最下面没有tj-1，那个-1的成本去哪了

#### Best/Worst/Average Case

* best case

Running time = f(n), each element already sorted, only need to go through and check

* worst case

Running time = f(n^2), elements are in inverse order, tj = j + 1

* average case

Running time = f(n^2), tj = (j+1)/2,



# Asymptotic Notation 渐进记号

[recommend webpage lang = "cn"](https://blog.csdn.net/so_geili/article/details/53353593?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171169602016800180667167%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171169602016800180667167&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-53353593-null-null.142^v100^pc_search_result_base2&utm_term=%E6%B8%90%E8%BF%9B%E8%AE%B0%E5%8F%B7&spm=1018.2226.3001.4187)

### Big O-NOTATION 渐进上界符号

- **定义**：O-Notation（大O表示法）是一种用于描述算法复杂度的数学符号，它表示了**算法执行时间与输入数据量**之间的关系。大O表示法通常用于算法分析中，以估计算法在**最坏情况**下的性能表现。

- English Definition:  $f(n)$ is $O(g(n))$, if there exists constants $c$ and $n_0$ s.t. $f(n)<= c\ g(n)$ for all $n >= n_0$ 

- 大O表示法主要用于理论分析，它**忽略了常数因子和低阶项**，因为当输入数据足够大时，这些因素对算法的影响相对较小。它允许我们专注于算法性能随输入规模增长的主要趋势，而不是具体的执行时间。

- often used for worst-case analysis

- 根据符号O的定义，我们可以知道这个上界阶越低，评估越精确，越有价值
	- e.g.  $f(n) = n^2 + n$, 则 $f(n)=O(n^2)$,取 $c = 2,n_0 = 1$即可， $f(n) = O(n^3)$,取 $c = 1,n_0 = 2$即可，我们可以看出 $O(n^2)$作为上界更为精确，更好地逼近 $f(n)$ 


> 通俗的说n满足一定条件范围内，函数f(n)的阶不高于函数g(n)

- Example:

$$
 f(n)=10n^2*log(n)+100n+10
$$

$$
O(f(n))=n^2
$$

- Some Extra

  - $$
    O[max(f(n),g(n))]=O(f(n)+g(n))
    $$
  
  

<img src=".assets/big0.webp" alt="big0" style="zoom:33%;" />

###  $\Omega$ Big Omega 渐进下界符号

  描述的是算法运行时间的**下界**，即算法在任何情况下的**最低性能**。如果一个算法的时间复杂度是 $\Omega(g(n))$，意味着存在一个常数$C$和一个$n_0$，使得当$n \geq n_0$时，算法的运行时间至少是$Cg(n)$​​​。

* often used for best case analysis

* 根据符号 $\Omega$ 的定义，我们可以知道这个下界的阶越高，评估越精确，越有价值
	- e.g.  $f(n) = n^2 + n$, 则 $f(n)=\Omega(n^2)$,取 $c = 1,n_0 = 1$即可， $f(n) = \Omega(100n)$,取 $c = \frac{1}{100},n_0 = 1$即可，我们可以看出 $\Omega(n^2)$作为上界更为精确，更好地逼近 $f(n)$​ 

> 通俗地说，n满足一定条件范围内，函数 $f(n)$的阶不低于函数 $g(n)$ 

<img src=".assets/omega.webp" alt="omega" style="zoom: 33%;" />

###  $\theta$ Big Theta 渐进准确界符号

* 定义

​    在五个记号中要求最严格，因为它**同时描述了上界和下界**。如果说一个算法$f(n)$的时间复杂度是 $\theta(g(n))$，意味着既存在常数$C_1$和$C_2$，也存在一个$N_0$，使得当$n\geq N_0$时，$C_1\ h(n)\leq f(n)\leq C_2\ h(n)$。这意味着算法的运时间随输入大小 $n$ 的增加，其增长率被 $h(n)$ 紧密包围。

> 通俗理解为 $f(n)$ 和 $g(n)$ 同阶

<img src="assets/theta.png-1691841.webp" alt="theta.png" style="zoom:33%;" />

### little o 非渐进紧确上界

#### 定义

设 $f(n)$ 和 $g(n)$ 是定义域为自然数集 $\N$ 上的函数。若对于任意正数 $c$,都存在 $n_0$, 使得对一切 $n \geq  n_0$ 都有 $0 \leq f(n) < cg(n)$成立，则称 $f(n)$ 的渐进的非紧确上界是 $g(n)$, 记作 $f(n) = o(g(n))$ 

> 通俗得说 $n$ 满足一定条件范围内，函数 $f(n)$ 的阶**低于**函数 $g(n)$​

#### 紧确与非紧确

 $2n^2 = O(n^2)$ 是渐进紧确的， $2n = O(n^2)$ 是非紧确上界

e.g.  $f(n) = n^2 + n$, 那么 $f(n) = o(n^3)$,  $f(n) = o(n^2)$ 是错误的

### $\omega$​ small omega 非渐进紧确下界

#### 定义

设 $f(n)$ 和 $g(n)$ 是定义域为自然数集 $\N$ 上的函数。若对于任意正数 $c$,都存在 $n_0$, 使得对一切 $n \geq  n_0$ 都有 $0 \leq cg(n) < f(n) $成立，则称 $f(n)$ 的渐进的非紧确下界是 $g(n)$, 记作 $f(n) = \omega(g(n))$​ 

> 通俗地说 $n$ 满足一定条件范围内，函数 $f(n)$ 的阶高于函数 $g(n)$ 

### relationship

| notation | meaning    | frankly speaking    |
| -------- | ---------- | ------------------- |
| $\Theta$ | 紧确界     | 相当于  $f(n)=$     |
| $O$      | 上界       | 相当于  $f(n) \leq$ |
| $o$      | 非紧的上界 | 相当于  $f(n) <$    |
| $\Omega$ | 下界       | 相当于  $f(n) \geq$ |
| $\omega$ | 非紧的下界 | 相当于  $f(n) >$    |

![3FCbB](.assets/3FCbB.png)

### by the way

#### 常见复杂度关系

 $O(1)<O(log(n))<O(n)<O(nlog\ n)<O(n^2)<O(2^n)<O(n!)<O(n^n)$​

需要注意：对数函数没有底数时，默认底数为2，e.g.  $lg\ n =log \ n = log_2 \ n$​ ,因为很多计算中程序都是用二分法来实现的

#### 名称

| name        | notation                |
| ----------- | ----------------------- |
| logarithmic | $O(log \ n)$            |
| linear      | $O(n)$                  |
| quadratic   | $O(n^2)$                |
| polynomial  | $O(n^k)$ and  $k\geq 1$ |
| exponential | $O(a^n)$ and  $a > 1$   |

# Abstract Data Type(ADT)

## 简介


ADT，或抽象数据类型（Abstract Data Type），是一种计算机科学中的概念，用来描述数据和对数据操作的一系列规范。ADT 通过提供数据的抽象表示和对数据的操作定义，而不暴露数据的具体实现，使得数据结构的使用和实现可以分离。

### 核心概念

* **抽象**：ADT关注于数据的逻辑特性而不是数据的具体实现。例如，一个列表ADT定义了如何添加元素、删除元素、遍历元素等操作，但不指定这些操作是如何实现的。
* **封装**：ADT通过隐藏其内部结构的具体实现，只通过一组定义良好的接口与外界交互，实现了封装。这样，即使内部实现改变，只要接口保持不变，使用ADT的代码就不需要修改。
* **数据操作**：ADT定义了一组操作，这些操作是与ADT数据结构交互的唯一方式。这包括创建、修改、检索和删除数据等基本操作。

### 常见的ADT示例

* **栈**（Stack）：一种后进先出（LIFO）的数据结构，常见操作有`push`（入栈）、`pop`（出栈）和`peek`（查看栈顶元素）。
* **队列**（Queue）：一种先进先出（FIFO）的数据结构，主要操作包括`enqueue`（入队）、`dequeue`（出队）和`front`（查看队首元素）。
* **列表**（List）：可以存储一序列元素的数据结构，允许添加、删除和访问元素。
* **树**（Tree）：模拟层次结构的数据结构，包括二叉树、平衡树等，常用于实现搜索和排序算法。
* **图**（Graph）：由节点（顶点）和边组成的集合，用于模拟实体之间的多对多关系。

### ADT的优势

* **抽象层次高**：用户只需了解接口的功能，无需关心具体实现细节。
* **可重用性**：同一个ADT可以有多种不同的实现，便于在不同场景下重用。
* **易于维护和修改**：修改ADT的内部实现不会影响到使用它的代码，使得程序更加模块化

## array 数组

### 数组的定义

* 数组是一种将索引集映射到单元格类型的数据结构。
* 通常，数组中的每个单元格（cell）大小相同。如果不相同，则使用指针。
* 数组的对象是一组连续存储的单元格。

### 数组的操作

* **创建数组**：`create(A, n, dtype)`用于创建数组，其中`A`是数组名，`n`是数组大小，`dtype`是数据类型。
* **获取元素**：`A.get(v, idx)`或`A[idx]`用于获取数组中的元素，其中`idx`是索引。
* **修改/设置元素**：`A.put(v, idx)`或`A[idx] = x`用于修改数组中的元素，或者转化数据类型
* **聚合**: sum, count, max, min, avg

### 多维数组

* 对于二维或更高维度的数组，需要将多维索引映射到一维空间。这是因为我们抽象主存储器和外部存储器为连续的一维空间。
* 典型的顺序是按维度从左到右排序，也称为字典顺序。

#### 通过一维数组操作二维数组

引入：为什么可以通过 `int *A = new int[nRow * nCol]` 创建一个一维数组，并使用 `A[i][j]` 的方式来操作它就好像一个二维数组一样？

答： 实际上是在连续的内存当中存储所有元素，通过计算索引，将一维数组的位置映射到二维数组空间中的行和列。索引的计算公式通常是 `index = i * nCol + j` ,其中 `i` 是行索引（即第几行）， `j` 是列索引（即第几列）， `nCol` 是一行的元素个数， 这样 `A[index]`就等价于二维数组中的 `A[i][j]`

### 特殊情况 

1. **空间填充曲线(SFC)**：如Z-order和希尔伯特曲线，这些是处理多维数据索引的特殊方法。
2. **稀疏数组**：特别是在矩阵或张量中使用，用于优化存储和计算效率，避免浪费空间存储大量的零值。

<img src=".assets/zorder_why_zcurve.png" alt="zorder_why_zcurve" style="zoom:33%;" />

z curve

### 动态数组 dynamic array

#### 引入

如何实现insert函数和delete函数

#### 分析

##### time complexity

`Insert`

* Best case: $O(1)$ 
* Worst case: $O(n)$
* Average case:  $\sum_{i = 0}^{n}\frac{1}{n+1}(c_{shift}(n-i)+c_{insert})$
  * While $\frac{1}{n+1}$ 是插入任意一个位置的概率
  *  $c_{shift}$ 是移动一个元素的成本
  *  $c_{insert}$ 是插入操作的固定成本（如增大数列空间
  * 计算之后大概是 $\frac{1}{2}c_{shift}n+c_{insert}$ ,时间复杂度为 $\theta(n)$​

`Delete`

 $O(n)$ ,similar to insert

##### space complexity

 $O(maxsize)$ due to copy and paste to another array

###### strategy

* if maxsize is too large, space will be wasted
* if maxsize is too small, it is easy to be ran out of space

###### solution

* use a dynamic or growable array when there is limited insertion
* Else use a linked list 

#### 链表

##### 分类

###### 单向链表

* 有指向下一个的指针

* e.g.

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        last_node = self.head
        while last_node.next:
            last_node = last_node.next
        last_node.next = new_node

    def print_list(self):
        current_node = self.head
        while current_node:
            print(current_node.data)
            current_node = current_node.next
```





###### 双向链表

* 有分别指向下一个和前一个的指针

###### 循环链表

* 最后一个会指向回开头
* 可以动态地保持空间的平衡



## Stack 栈

- **定义**：栈（Stack）是一种遵循后进先出（LIFO, Last In First Out）原则的数据结构。这意味着最后添加到栈中的元素会是第一个被移除的元素。栈通常支持两种主要操作：**压栈（push）**，即在栈顶添加一个元素；和**弹栈（pop）**，即移除栈顶元素。此外，许多栈实现还提供了**查看栈顶元素（peek 或 top）**的操作，但不移除它。

  ```python
  class Stack:
      def __init__(self):
          self.items = []
      def push(self, item):
          self.items.append(item)
      def pop(self):
          return self.items.pop() if not self.is_empty() else None
      def peek(self):
          return self.items[-1] if not self.is_empty() else None
      def is_empty(self):
          return len(self.items) == 0
      def size(self):
          return len(self.items)
  ```

  

  #### **前缀/后缀表达式 Pre/Postfix Evaluator**

  后缀表达式（也称为逆波兰表示法）和前缀表达式（也称为波兰表示法）是两种不同的方式来表示和计算数学表达式，它们都不需要使用括号来指定操作符的优先级。

  - 前缀表达式：**操作符位于其操作数之前**。例如，表达式 `(3 + 4) * 5` 在前缀表示法中写作 `* + 3 4 5`。

    ```python
    def evaluate_prefix(expression):
        stack = []
        for token in reversed(expression.split()):
            if token in "+-*/":
                a, b = stack.pop(), stack.pop()  # 这里的顺序也很重要
                stack.append(str(eval(f"{a}{token}{b}")))  # 计算结果并推回栈中
            else:
                stack.append(token)  # 将数字推入栈中
        return int(stack.pop())
    ```

    

  - 后缀表达式：**操作符位于其操作数之后**。例如，表达式 `(3 + 4) * 5` 在后缀表示法中写作 `3 4 + 5 *`。

    ```python
    def evaluate_postfix(expression):
        stack = []
        for token in expression.split():
            if token in "+-*/":
                b, a = stack.pop(), stack.pop()  # 注意非交换运算的顺序
                stack.append(str(eval(f"{a}{token}{b}")))  # 计算结果并推回栈中
            else:
                stack.append(token)  # 将数字推入栈中
        return int(stack.pop())
    ```

    

  ### **摊销时间 Amortized Time**

  指在执行一系列操作时，**每个操作的平均时间成本**。这个概念在分析那些**偶尔需要大量时间但通常很快的操作**时特别有用。摊销分析的目的是展示即使单个操作可能昂贵，整个操作序列的平均成本仍然可以保持低。

  - 其中增长策略的计算就用到了这个思想，到底是以常数 $c$​ 的增长速度增加还是每次翻倍增加
  	- 常数 $c$​​ 增长速度，计算将 $n$ 个数推入栈（或者数组）的总时间 $T(n)$ 
  		- 将 $n$ 个数分成 $k = \frac{n}{c}$ 份，那么总时间为 $T(n) = n + c+2c+3c+\cdots+kc = n+ck(k+1)/2$, 其中 $c,2c,3c$ 表示将 $ic$ 个元素( $i \in1,2,3,\cdots ,k$)复制到新数组所用的时间，最终我们有 $T(n)\approx O(n+k^2)$ i.e., $O(n^2)$​
  		- thus, the amortized time of a push operation is $O(n)$
  	- 翻倍增加
  		- 将 $n$ 个数分成 $k = log_2 \ n $ 份，那么总时间为 $T(n) = n + 1+2+4+\cdots+2^k = n+2^{k+1} - 1 =3n-1$, 其中 $1,2,4 $ 表示将 $2^{k+1}$ 个元素( $i \in1,2,3,\cdots ,k$)复制到新数组所用的时间，最终我们有 $T(n)\approx O(n)$ 
  		- thus, the amortized time of a push operation is $O(1)$ 

## Queue 队列

- **定义**：队列（Queue）是一种**先进先出**（FIFO, First-In-First-Out）的数据结构，用于存储对象，并按照元素进入队列的顺序进行插入和删除操作。在队列中，插入操作通常发生在队列的后端，而删除操作发生在队列的前端。

  ```python
  class Queue:
      def __init__(self):
          self.items = []
      
      def enqueue(self, item):
          self.items.append(item)
      
      def dequeue(self):
          if not self.is_empty():
              return self.items.pop(0)
          else:
              raise Exception("EmptyQueueException")
      
      def front(self):
          if not self.is_empty():
              return self.items[0]
          else:
              raise Exception("EmptyQueueException")
      
      def size(self):
          return len(self.items)
      
      def is_empty(self):
          return len(self.items) == 0
  ```



# Heap 堆

- **定义**：堆（Heap）是一种**特殊的完全二叉树**，它满足特定的堆属性：在最小堆中，每个节点的值都小于或等于其子节点的值；而在最大堆中，每个节点的值都大于或等于其子节点的值。这意味着在最小堆的根节点是树中的最小值，在最大堆中根节点是树中的最大值。

  堆通常用于实现优先队列，因为它可以有效地提供**最小或最大元素的访问**，并且可以在对数时间$log(n)$内插入新元素或删除最小（最大）元素

- **操作**：

  - **insert 插入 $O(log⁡(n))$**：首先填满一层，从左到右、从上到下依次填入

    1. 将新元素推入至堆的末尾

    2. 将其与父节点比较，若父节点较大则进行交换

    3. 重复第二步得到最小堆

    > 在最坏的情况下，新元素可能需要从最底层一直上浮到根节点。由于堆是一个完全二叉树，树的高度是 $log⁡(n)$，所以上浮操作的最大次数是树的高度，即 $O(log⁡(n))$。

  - **delete 删除** $O(log⁡(n))$：删除root节点

    1. 比较左右字节点，较小的节点向上调
    2. 重复第一步直到堆底

    > 同样地，在最坏的情况下，这个元素可能需要从根节点下沉到最底层。因此，下沉操作的最大次数也是树的高度 $log(n)$，即 $O(log(n))$​。

  - **FindMin 输出最小值** $O(1)$

  - **Heapify 堆化 $O(nlog⁡(n))$​**：

    1. 从$1$到$N$逐个insert，要进行$n$次$O(log(n))$的操作，时间复杂度近似为$O(log(n))$

    2. （数组）从$N/2$到$1$进行PercDown（下沉）操作，时间复杂度为$O(n)$​

       > **时间复杂度分析**
       >
       > 假设 $N = 2^{(h+1)} - 1$​ 其中 $h$ 是树的高度。则$1$到$N/2皆为非子叶点$。
       >
       > 对于$N/2$到$N$第$h$层皆为子叶点，无需进行下沉操作。
       >
       > 对于$1$到$h-1$层，$h-j$层需要下沉$j$​次
       >
       > 公式为：$T(n) = \sum_{j=0}^{h} {(h-j)} \cdot 2^{j} = 2^{h+1}-(h+2)$ 又$h=log_{2}{(N+1)}-1$
       >
       > 则$T(n) =N-log_{2}{(N+1)}=O(N)$

       

    ```python
    Root node = A[1]
    Children of A[i] = A[2i], A[2i + 1]
    Parent of A[j] = A[ j // 2 ]
    Keep track of current size N (number of nodes)
    
    PercDown(i:integer, x: integer): {
    // N is the number elements, i is the hole, x is the value to insert
    Case{
        2i > N : A[i] := x; 						//at bottom, no child//
        2i = N : if A[2i] < x then					//one child//
        			A[i] := A[2i]; A[2i] := x;
        		 else A[i] := x;
        2i < N : if A[2i] < A[2i+1] then j := 2i;	//two children//
        		 else j := 2i+1;
       			 if A[j] < x then
      				A[i] := A[j]; PercDown(j,x);
       			 else A[i] := x;
    }}
    
    
    BuildHeap{
    	for i = N/2 to 1
    		PercDown(i,A[i])
    }
    ```

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

- ## Merge Sort 归并排序

  - **定义**：归并排序是一种高效的排序算法，采用**分治法**的一个典型应用。它将一个列表分成最小可能的单元（通常是一个元素），然后将它们合并成两个有序的序列，最后再将这两个有序序列合并成一个最终的排序序列。

  - **代码实现**：

    ```python
    def merge_sort(arr):
        """
        对数组arr进行归并排序。
        :param arr: 要排序的数组
        :return: 排序后的数组
        """
        if len(arr) > 1:
            # 找到中点，对半分
            mid = len(arr) // 2
            # 分别对左半部分和右半部分进行归并排序
            L = arr[:mid]
            R = arr[mid:]
    
            merge_sort(L)  # 对左半部分归并排序
            merge_sort(R)  # 对右半部分归并排序
    
            # 合并过程
            i = j = k = 0
    
            # 将数据从两个数组中取出来，比较后放入原数组
            while i < len(L) and j < len(R):
                if L[i] < R[j]:
                    arr[k] = L[i]
                    i += 1
                else:
                    arr[k] = R[j]
                    j += 1
                k += 1
    
            # 检查是否有遗留元素，将它们加到原数组后面
            while i < len(L):
                arr[k] = L[i]
                i += 1
                k += 1
    
            while j < len(R):
                arr[k] = R[j]
                j += 1
                k += 1
    
        # 当数组长度为1时，递归结束，开始回溯，合并
        return arr
    
    ```

  - **时间复杂度**：

    1. 分解阶段：在每一层递归调用中，数组被分成两半。这意味着递归的深度2是 $O(log⁡n)$，因为每次分解操作都将数据集大小减半，直到大小变为1。因此，可以将数组分解成最小单元的操作次数表示为 $O(log⁡n)$​。
    2. 合并阶段：对于每一层递归调用，需要将两个有序的数组合并成一个有序数组。不论数组的初始状态如何，这个合并操作的时间复杂度都是 $O(n)$​，因为每个元素最终都需要被比较和移动至其正确的位置。
    3. 总和：$O(nlogn)$​

    - 分治类型的时间复杂度：$T(n)=T(n/2)+\theta(n)$



# 分治Divide and Conquer

> **定义**："**分而治之**"（Divide and Conquer）是一种算法设计策略，它将一个复杂的问题分解成几个较小的子问题，每个子问题类似于原问题但规模更小，然后逐个解决这些子问题，并最终将子问题的解合并以得到原问题的解。
>
> 1. **分割（Divide）**：将原问题分解成一系列子问题。
> 2. **征服（Conquer）**：递归地解决这些子问题。如果子问题的规模足够小，就可以直接求解。
> 3. **合并（Combine）**：将子问题的解合并成原问题的解。

## 主定理 Master Theorem

- **定义**：用来分析某些特定类型的**递归算法的**运行时间的一种方法，为具有特定形式的递归关系提供了一种快速解决时间复杂度的技术

- **公式**：$T(n)=aT(\frac{n}{b})+O(n^d)$

  1. $T(n)$ 是解决大小为 $n$的问题所需的时间。
  2. $a$ 是每次递归产生的子问题数量。
  3. $\frac{n}{b}$ 是每个子问题的大小，$b$ 是分割因子。
  4. $O(n^d)$​​ 是每次递归在分解和合并步骤中所需的时间。

- **解析**：$Total work = \sum_{i=0}^{\log_b n} O(n^d) \left(\frac{a}{b^d}\right)^i$ 等比数列且公比为$\frac{a}{b^d}$

  > 1. 公比$>1$ :整个算法的时间复杂度由第一项决定，结果为$O(n^{d})$
  > 2. 公比$<1$ :整个算法的时间复杂度由最后一项决定，结果为$O(n^{log_ba})$​
  > 3.  公比$=1$ :整个算法的时间复杂度求和，结果为$O(n^{d}log_bn)$

## 二分查找 Binary Search

- **定义**：用于在一个有序的项目列表中查找特定项目。它通过重复地将可能包含目标项的列表部分一分为二，直到将可能的位置缩小到只有一个为止。

- **代码实现**：

  ```python
  def binary_search(arr, target):
      """
      二分搜索
      :param arr: 有序数组
      :param target: 需要搜索的目标值
      :return: 目标值在数组中的索引，如果不存在则返回-1
      """
      low = 0  # 设置最低索引为数组起始位置
      high = len(arr) - 1  # 设置最高索引为数组的最后一个元素的位置
  
      while low <= high:  # 当最低索引不大于最高索引时
          mid = (low + high) // 2  # 计算中间索引
          guess = arr[mid]  # 获取中间索引对应的值
          if guess == target:  # 如果猜测值等于目标值，返回中间索引
              return mid
          if guess > target:  # 如果猜测值大于目标值，调整最高索引为中间索引的前一个位置
              high = mid - 1
          else:  # 如果猜测值小于目标值，调整最低索引为中间索引的后一个位置
              low = mid + 1
      return -1  # 如果未找到目标值，返回-1
  ```

- **时间复杂度**：$O(n)=(logn)$​

## **Karatsuba 算法**

- **定义**：Karatsuba算法是一种快速乘法算法，用于大数的乘法，由安纳托利·卡拉次巴*Anatolii Alexeevitch Karatsuba*在1960年发明。它是基于分治法的原理，通过减少大数乘法问题所需的基本乘法运算次数来提高效率。

- **算法原理**：

  > **原乘法**：两个长度为$n$的大数相乘，$X$每一位对$Y$乘后相加，总时间复杂度为$O(n^2)$
  >
  > **改良**：将$X$和$Y$分成两个部分：$X = 10^{\frac{n}{2}} * A + B$ 以及 $Y = 10^{\frac{n}{2}} * C + D$ ，$a$和$b$是$X$的高位和低位部分，$c$和$d$是$Y$​的高位和低位部分。
  >
  > 传统算法通过计算四个乘积：$ab,cd,ac,bd$，并将其处理后求和，*Karatsuba*则使用三个乘积：
  >
  > 1. 计算$ac$
  > 2. 计算$bd$
  > 3. 计算$(a+b) \times (c+d)$（这实际上等于$ac + ad + bc + bd$​）
  > 4. $X \times Y = 10^n \cdot ac + 10^{n/2} \times [(a+b) \times (c+d) - ac - bd] + bd$

- **代码实现**：

  ```python
  def karatsuba(x, y):
      if x < 10 or y < 10:
          return x * y
  
      # 计算大小
      n = max(len(str(x)), len(str(y)))
      half = n // 2
      
      # 分割输入数字
      a = x // 10**(half)
      b = x % 10**(half)
      c = y // 10**(half)
      d = y % 10**(half)
      
      # 递归计算
      ac = karatsuba(a, c)
      bd = karatsuba(b, d)
      ad_plus_bc = karatsuba(a + b, c + d) - ac - bd
      
      # 合并结果
      product = ac * 10**(2*half) + (ad_plus_bc * 10**half) + bd
  
      return product
  ```

- **时间复杂度**：$O(n^{log_2 3})$或约为$O(n^{1.585})$ 

## **快速排序 Quicksort**

- **定义**：快速排序是一种高效的排序算法，由Tony Hoare在1960年代初提出。它使用**分治法**（Divide and Conquer）的策略来对一个数组进行排序，其核心思想是通过一个分区操作将要排序的数组分割成独立的两部分，其中一部分的所有数据都比另一部分的所有数据都要小，然后再递归地对这两部分数据分别进行快速排序。

- **实现**：

  >1. **选择基准值（Pivot）**：从数组中选择一个元素作为基准值。基准值的选择可以有多种方式，例如选择第一个元素、最后一个元素、中间元素或随机元素。
  >2. **分区（Partition）**：重新排列数组，使得所有比基准值小的元素都移动到基准值的前面，所有比基准值大的元素都移动到基准值的后面。这一步结束时，基准值就处于其最终位置。
  >3. **递归排序**：递归地对基准值前后的两个子数组进行快速排序。
  >
  >

- **代码实现**：

  ```python
  # Simple way
  def quicksort(arr):
      if len(arr) <= 1:
          return arr
      else:
          pivot = arr[0]
          left = [x for x in arr[1:] if x <= pivot]
          right = [x for x in arr[1:] if x > pivot]
          return quicksort(left) + [pivot] + quicksort(right)
  ```

  ```py
  # In-place way 空间复杂度优化
  def quicksort(arr, low, high):
      if low < high:
          # partitionIndex是分区操作正确放置基准值的索引位置
          partitionIndex = partition(arr, low, high)
  
          # 分别对基准值左右两边的子数组递归排序
          quicksort(arr, low, partitionIndex - 1)
          quicksort(arr, partitionIndex + 1, high)
  
  def partition(arr, low, high):
      pivot = arr[high]  # 选择最后一个元素作为基准
      i = low - 1  # i是小于基准值元素的最后一个元素的索引
  
      for j in range(low, high):
          # 当前元素小于或等于基准值
          if arr[j] <= pivot:
              i += 1
              arr[i], arr[j] = arr[j], arr[i]
  
      # 将基准值移动到正确的位置
      arr[i+1], arr[high] = arr[high], arr[i+1]
      return i + 1
  ```

  - **时间复杂度分析**：

    - **最好情况**：如果每次都能将数组分为两个几乎相等的部分，那么快速排序的时间复杂度为$\Theta(n \log n)$

      **公式**：$T(n) = 2T(n/2) + \Theta(n)$

      其中，$T(n/2)$表示对半分的子数组排序的时间，$(\Theta(n))$表示分区操作的时间。

    - **最坏情况**：如果每次分区操作后，一个子数组包含了除基准元素外的所有元素，那么快速排序的时间复杂度退化为$(O(n^2))$。

      **公式**：$T(n) = T(n-1) + \Theta(n)$

      这种情况通常发生在数组已经是正序或逆序的情况下。

    - **平均情况**：考虑到所有可能的分区方式，快速排序的平均时间复杂度也是$(O(n \log n))$。

## 快速搜索 Quick Select

- **定义**：Quick Select 是一种在未排序的列表中找到第 k 小（或第 k 大）元素的算法。它是由 Tony Hoare 于1961年提出，同样也是快速排序算法的发明者。Quick Select 的工作原理与快速排序相似，但它仅递归地处理找到第 k 个元素所需的那一部分数组，而不是像快速排序那样处理整个数组。这使得它在找到特定顺序元素方面比完全排序整个数组更高效。

- **原理**：

  > 1. **选择一个枢纽（Pivot）元素**：从数组中选择一个元素作为枢纽。
  > 2. **分区（Partitioning）**：重新排列数组，使得所有比枢纽小的元素都移到枢纽的左边，所有比枢纽大的元素都移到枢纽的右边。枢纽元素现在在其最终位置上。
  > 3. 递归选择：
  >    - 如果枢纽元素正好是第 $k$ 小的元素，算法结束。
  >    - 如果枢纽元素的位置大于 $k$，那么只在枢纽的左边数组中递归地执行 Quick Select。
  >    - 如果枢纽元素的位置小于 $k$，那么只在枢纽的右边数组中递归地执行 Quick Select，调整 $k$ 的值为 -$k - (枢纽的位置 + 1)$。

- **代码实现**：

  ```py
  def quick_select(arr, left, right, k):
      """
      找到数组 arr 中第 k 小的元素。
      :param arr: 输入的数组
      :param left: 考虑数组的起始索引
      :param right: 考虑数组的结束索引
      :param k: 找到的元素的顺序（第k小的元素）
      :return: 第 k 小的元素
      """
      if left <= right:
          # 进行分区
          pivot_index = partition(arr, left, right)
          # 如果 pivot 正好是第k小的元素
          if pivot_index == k:
              return arr[pivot_index]
          elif pivot_index < k:
              # 在右侧寻找
              return quick_select(arr, pivot_index + 1, right, k)
          else:
              # 在左侧寻找
              return quick_select(arr, left, pivot_index - 1, k)
      return -1  # 如果 k 超出范围
  
  def partition(arr, left, right):
      """
      以最右侧的元素作为枢纽进行分区，并返回枢纽的索引。
      :param arr: 输入的数组
      :param left: 考虑数组的起始索引
      :param right: 考虑数组的结束索引
      :return: 枢纽的索引
      """
      pivot = arr[right]
      i = left
      for j in range(left, right):
          if arr[j] < pivot:
              arr[i], arr[j] = arr[j], arr[i]
              i += 1
      arr[i], arr[right] = arr[right], arr[i]  # 将枢纽放到最终位置
      return i
  ```

- **复杂度**：

  > **平均时间复杂度**：$O(n)$，其中 n 是数组的大小。
  >
  > **最坏情况时间复杂度**：$O(n²)$，这发生在每次分区操作都极度不平衡时。
  >
  > **空间复杂度**：$O(1)$（迭代实现）或 $O(log(n))$（递归实现，因为递归调用堆栈）。

# 动态规划 Dynamic Programming

- **定义**：动态规划（Dynamic Programming，简称 DP）是一种算法设计方法，它将复杂问题分解为简单的子问题，并用这些子问题的解来构建原问题的解。动态规划通常用于**优化递归算法**，特别是在递归过程中有大量重复计算时。动态规划的核心思想是**记忆化（Memorization）**与**表格化（Tabulation）**，这两种技术都是为了存储子问题的解以避免重复计算。

## 最优分箱问题 Optimal Binning Problem

- **定义**：最优分箱问题（Optimal Binning Problem），这是一个数据分箱（binning）或数据离散化的统计方法。数据分箱通常用于将连续变量转换为分类变量，或者创建数据的分段分布。目标是选择这些区间的边界，以最小化某种损失函数，通常是各区间内部值的总方差。这在统计学中是减少模型过拟合、处理异常值、改善模型性能等方面有很多应用。

- **基本概念**：

  1. **元素（n elements）**：你有一个包含 n 个连续值的数据集。
  2. **分箱（B bins）**：将数据集分割成 B 个连续的段，每个段称为一个箱子。
  3. **代表性（Represent each segment）**：用箱子中所有值的平均值来代表该箱子。

- **成本函数**：


  最优分箱问题是一种数据预处理技术，它涉及将连续变量的值分组到称为"箱子"（bins）的离散区间。目标是选择这些区间的边界，以最小化某种损失函数，通常是各区间内部值的总方差。这在统计学中是减少模型过拟合、处理异常值、改善模型性能等方面有很多应用。

- **基本概念**

  1. **元素（n elements）**：你有一个包含 n 个连续值的数据集。
  2. **分箱（B bins）**：将数据集分割成 B 个连续的段，每个段称为一个箱子。
  3. **代表性（Represent each segment）**：用箱子中所有值的平均值来代表该箱子。

- **成本函数**

  - **单个箱子的成本**：对于每个箱子，成本计算为箱子中所有元素的平方误差和（**SSE**: Sum Square Error）。这是每个元素的值和箱内平均值差的平方的总和。平方误差和是一种常用的度量方法，用来评估数据点与某个中心点（在这种情况下是平均值）之间的差异。

    $cost(bin) = \sum_{i=l}^{m} (x_i - \bar{x})^2$   (其中 $\bar{x}$ 是箱子中所有元素的平均值)

  - **所有箱子的总成本**：将每个箱子的成本相加，得到所有 B 个箱子的总成本。

$$
OPT(x[1..n], B) = \min_{i \in [n]} \{SSE(x[1..i]) + OPT(x[i+1..n], B-1)\}
$$








