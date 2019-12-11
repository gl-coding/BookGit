# 第2节：算法优化

 ## 1.改进算法

一个良好的算法能够对性能起到关键作用，因此性能改进的首要点是对算法的改进。在算法的时间复杂度排序上依次是： 

O(1) -> O(lg n) -> O(n lg n) -> O(n^2) -> O(n^3) -> O(n^k) -> O(k^n) -> O(n!)

因此如果能够在时间复杂度上对算法进行一定的改进，对性能的提高不言而喻。但对具体算法的改进不属于本文讨论的范围，读者可以自行参考这方面资料。下面的内容将集中讨论数据结构的选择。

10.1 快速排序

10.1.1 Python

```python
def quick_sort(li, start, end):
  if start >= end:
​    return
  left = start
  right = end
  mid = li[left]
  while left < right:

​    while left < right and li[right] >= mid:
​      right -= 1
​    li[left] = li[right]
​    while left < right and li[left] < mid:
​      left += 1

​    li[right] = li[left]
  \# while结束后，把mid放到中间位置，left=right
  li[left] = mid
  \# 递归处理左边的数据
  quick_sort(li, start, left-1)
  \# 递归处理右边的数据
  quick_sort(li, left+1, end)

if __name__ == '__main__':
  l = [6,5,4,3,2,1]
  \# l = 3 [2,1,5,6,5,4]
  \# [2, 1, 5, 6, 5, 4]
  quick_sort(l,0,len(l)-1)
  print(l)
  \# 稳定性：不稳定
  \# 最优时间复杂度：O(nlogn)
\# 最坏时间复杂度：O(n^2)
```



10.1.2 Java

```java
package quickSort; 

public class QuickSort {

   private static int count;

   /**

​    \* 测试

​    \* @param args

​    */

   public static void main(String[] args) {

​      int[] num = {3,45,78,64,52,11,64,55,99,11,18};

​      System.out.println(arrayToString(num,"未排序"));

​      QuickSort(num,0,num.length-1);

​      System.out.println(arrayToString(num,"排序"));

​      System.out.println("数组个数："+num.length);

​      System.out.println("循环次数："+count);

​      

   }

   /**

​    \* 快速排序

​    \* @param num   排序的数组

​    \* @param left  数组的前针

​    \* @param right 数组后针

​    */

   private static void QuickSort(int[] num, int left, int right) {

​      //如果left等于right，即数组只有一个元素，直接返回

​      if(left>=right) {

​         return;

​      }

​      //设置最左边的元素为基准值

​      int key=num[left];

​      //数组中比key小的放在左边，比key大的放在右边，key值下标为i

​      int i=left;

​      int j=right;

​      while(i<j){

​         //j向左移，直到遇到比key小的值

​         while(num[j]>=key && i<j){

​            j--;

​         }

​         //i向右移，直到遇到比key大的值

​         while(num[i]<=key && i<j){

​            i++;

​         }

​         //i和j指向的元素交换

​         if(i<j){

​            int temp=num[i];

​            num[i]=num[j];

​            num[j]=temp;

​         }

​      }

​      num[left]=num[i];

​      num[i]=key;

​      count++;

​      QuickSort(num,left,i-1);

​      QuickSort(num,i+1,right);

   }

   /**

​    \* 将一个int类型数组转化为字符串

​    \* @param arr

​    \* @param flag

​    \* @return

​    */

   private static String arrayToString(int[] arr,String flag) {

​      String str = "数组为("+flag+")：";

​      for(int a : arr) {

​         str += a + "\t";

​      }

​      return str;

   }

 

}
```



 

10.1.1.3 C\C++

```c++
 // 分治思想

 // [left, right] 左闭右闭区间

void QuickSort(Datatype* array, int left, int right)

{

  int mid = 0;

  int div = 0;

  Datatype key = 0;

  int begin = 0;

  int end = 0;

 

  // 解释一下这里 left 是有可能大于 right 的  边界细节 

  // 举个例子 如果此时序列是 1 2 3          

  // 以3为基准 左边划分没有问题 重点看一下右边 

  // 递归往右边走的时候 left指向3后面的元素（下标为3的元素）right 指向3（下标为2）

  // 那么此时就找不到递归出口(就会Stack overflow) 

  // 所以这里递归出口的判断条件必须是 ">=" 或者写成 !(left < right)

  if (left >= right)

  {

​    return;

  }

 

  // 这是我们的一种优化 三数取中法

  // 如果每次取序列最优端的那个元素 极易取到极值

  // 我们在序列中选择了三个数

  // 拿到这三个数的中间值 如果他不是最右边的元素就把他交换到最右边

  // 以此来提高快排的性能

  mid = GetMidIndex(array, left, right);

  if(mid != right)

  {

​    _swap(&array[mid], &array[right]);

  }

  key = array[right]; // 这是选的基准

  begin = left;

  end = right;

 

  // begin从前往后找第一个比基准值大的元素

  // end从后往前找第一个比基准值小的元素

  // 然后交换他们指向的元素 这样小数就在前面 大数就调到后面了 

  while (begin < end)

  {

​    // begin 找大

​    while (begin < end && array[begin] <= key)

​    {

​      ++begin;

​    }

​    // end 找小

​    while (begin < end && array[end] >= key)

​    {

​      --end;

​    }

​    if (begin < end)

​    {

​      _swap(&array[begin], &array[end]);

​    }

  }

 

  // 当begin与end相遇的时候 begin这个位置记录的元素应该是大于基准值的

  // 将begin位置元素与序列最右边元素交换

  _swap(&array[begin], &array[right]);

 

  // begin记录分割边界 div之前元素都比 div之后的元素小

  div = begin; 

 

  // 递归排序列的左半部分

  QuickSort(array, left, div - 1);

  // 递归排序列的右半部分

  QuickSort(array, div + 1, right);

}

 

\#include "Sort.h"

 

void Print(Datatype* array, int size);

 

void TestQSort()

{

  Datatype array[] = { 12, 2, 5, 37, 34, 88, 3, 77, 9, 21, 37 };

  int size = sizeof(array) / sizeof(array[0]);

  Print(array, size);

  QuickSort(array, 0, size-1); // 因为是[left, right]

  Print(array, size);

}

 

int main()

{

  TestQSort();

  system("pause");

  return 0;

}

 

void Print(Datatype* array, int size)

{

  int i = 0;

  for (i = 0; i < size; i++)

  {

​    printf("%d ", array[i]);

  }

  printf("\n");

} 
```

## 选择合适的数据结构

字典 (dictionary) 与列表 (list)

Python 字典中使用了 hash table，因此查找操作的复杂度为 O(1)，而 list 实际是个数组，在 list 中，查找需要遍历整个 list，其复杂度为 O(n)，因此对成员的查找访问等操作字典要比 list 更快。

清单 1. 代码 dict.py

```python
from time import time

 t = time()

 list = ['a','b','is','python','jason','hello','hill','with','phone','test',

'dfdf','apple','pddf','ind','basic','none','baecr','var','bana','dd','wrd']

 \#list = dict.fromkeys(list,True)

 print list

 filter = []

 for i in range (1000000):

   for find in ['is','hat','new','list','old','.']:

​     if find not in list:

​       filter.append(find)

 print "total run time:"

 print time()-t

 \```
```



上述代码运行大概需要 16.09seconds。如果去掉行 #list = dict.fromkeys(list,True) 的注释，将 list 转换为字典之后再运行，时间大约为 8.375 seconds，效率大概提高了一半。因此在需要多数据成员进行频繁的查找或者访问的时候，使用 dict 而不是 list 是一个较好的选择。

 

集合 (set) 与列表 (list)

set 的 union， intersection，difference 操作要比 list 的迭代要快。因此如果涉及到求 list 交集，并集或者差的问题可以转换为 set 来操作。

清单 2. 求 list 的交集：

```python
from time import time

t = time()

lista=[1,2,3,4,5,6,7,8,9,13,34,53,42,44]

listb=[2,4,6,9,23]

intersection=[]

for i in range (1000000):

  for a in lista:

​    for b in listb:

​      if a == b:

​        intersection.append(a)
 

print "total run time:"

print time()-t

```

 

上述程序的运行时间大概为：

total run time:

38.4070000648

 

清单 3. 使用 set 求交集

```python
from time import time

t = time()

lista=[1,2,3,4,5,6,7,8,9,13,34,53,42,44]

listb=[2,4,6,9,23]

intersection=[]

for i in range (1000000):

  list(set(lista)&set(listb))

print "total run time:"

print time()-t
```

改为 set 后程序的运行时间缩减为 8.75，提高了 4 倍多，运行时间大大缩短。读者可以自行使用表 1 其他的操作进行测试。



表 1. set 常见用法

语法 操作 说明

set(list1) | set(list2) union 包含 list1 和 list2 所有数据的新集合

set(list1) & set(list2) intersection   包含 list1 和 list2 中共同元素的新集合

set(list1) - set(list2) difference 在 list1 中出现但不在 list2 中出现的元素的集合



\## 代码优化

对循环的优化

对循环的优化所遵循的原则是尽量减少循环过程中的计算量，有多重循环的尽量将内层的计算提到上一层。 下面通过实例来对比循环优化后所带来的性能的提高。程序清单 4 中，如果不进行循环优化，其大概的运行时间约为 132.375。

 

清单 4. 为进行循环优化前

```python
from time import time

t = time()

lista = [1,2,3,4,5,6,7,8,9,10]

listb =[0.1,0.2,0.3,0.4,0.5,0.6,0.7,0.8,0.9,0.01]

for i in range (1000000):

  for a in range(len(lista)):

​    for b in range(len(listb)):

​      x=lista[a]+listb[b]

print "total run time:"

print time()-t 
```

现在进行如下优化，将长度计算提到循环外，range 用 xrange 代替，同时将第三层的计算 lista[a] 提到循环的第二层。 

清单 5. 循环优化后

```python
from time import time

t = time()

lista = [1,2,3,4,5,6,7,8,9,10]

listb =[0.1,0.2,0.3,0.4,0.5,0.6,0.7,0.8,0.9,0.01]

len1=len(lista)

len2=len(listb)

for i in xrange (1000000):

  for a in xrange(len1):

​    temp=lista[a]

​    for b in xrange(len2):

​      x=temp+listb[b]

print "total run time:"

print time()-t
```

上述优化后的程序其运行时间缩短为 102.171999931。在清单 4 中 lista[a] 被计算的次数为 1000000*10*10，而在优化后的代码中被计算的次数为 1000000*10，计算次数大幅度缩短，因此性能有所提升。

 

充分利用 Lazy if-evaluation 的特性

python 中条件表达式是 lazy evaluation 的，也就是说如果存在条件表达式 if x and y，在 x 为 false 的情况下 y 表达式的值将不再计算。因此可以利用该特性在一定程度上提高程序效率。



清单 6. 利用 Lazy if-evaluation 的特性

```python
from time import time

t = time()

abbreviations = ['cf.', 'e.g.', 'ex.', 'etc.', 'fig.', 'i.e.', 'Mr.', 'vs.']

for i in range (1000000):

  for w in ('Mr.', 'Hat', 'is', 'chasing', 'the', 'black', 'cat', '.'):

​    if w in abbreviations:

​    \#if w[-1] == '.' and w in abbreviations:

​      pass

print "total run time:"

print time()-t


```

在未进行优化之前程序的运行时间大概为 8.84，如果使用注释行代替第一个 if，运行的时间大概为 6.17。

 

字符串的优化

python 中的字符串对象是不可改变的，因此对任何字符串的操作如拼接，修改等都将产生一个新的字符串对象，而不是基于原字符串，因此这种持续的 copy 会在一定程度上影响 python 的性能。对字符串的优化也是改善性能的一个重要的方面，特别是在处理文本较多的情况下。字符串的优化主要集中在以下几个方面：

 

在字符串连接的使用尽量使用 join() 而不是 +：在代码清单 7 中使用 + 进行字符串连接大概需要 0.125 s，而使用 join 缩短为 0.016s。因此在字符的操作上 join 比 + 要快，因此要尽量使用 join 而不是 +。

清单 7. 使用 join 而不是 + 连接字符串

```python
from time import time

t = time()

s = ""

list = ['a','b','b','d','e','f','g','h','i','j','k','l','m','n']

for i in range (10000):

  for substr in list:

​    s+= substr

print "total run time:"

print time()-t
```

同时要避免：

 

s = ""

for x in list:

  s += func(x)

而是要使用：

 

slist = [func(elt) for elt in somelist]

s = "".join(slist)

当对字符串可以使用正则表达式或者内置函数来处理的时候，选择内置函数。如 str.isalpha()，str.isdigit()，str.startswith(('x', 'yz'))，str.endswith(('x', 'yz'))

对字符进行格式化比直接串联读取要快，因此要使用

1

out = "<html>%s%s%s%s</html>" % (head, prologue, query, tail)

而避免

1

out = "<html>" + head + prologue + query + tail + "</html>"

使用列表解析（list comprehension）和生成器表达式（generator expression）

列表解析要比在循环中重新构建一个新的 list 更为高效，因此我们可以利用这一特性来提高运行的效率。

```python
from time import time

 t = time()

 list = ['a','b','is','python','jason','hello','hill','with','phone','test',

'dfdf','apple','pddf','ind','basic','none','baecr','var','bana','dd','wrd']

 total=[]

 for i in range (1000000):

   for w in list:

​     total.append(w)

 print "total run time:"

 print time()-t
```



使用列表解析：

for i in range (1000000):

  a = [w for w in list]

上述代码直接运行大概需要 17s，而改为使用列表解析后 ，运行时间缩短为 9.29s。将近提高了一半。生成器表达式则是在 2.4 中引入的新内容，语法和列表解析类似，但是在大数据量处理时，生成器表达式的优势较为明显，它并不创建一个列表，只是返回一个生成器，因此效率较高。在上述例子上中代码 a = [w for w in list] 修改为 a = (w for w in list)，运行时间进一步减少，缩短约为 2.98s。

 

其他优化技巧

如果需要交换两个变量的值使用 a,b=b,a 而不是借助中间变量 t=a;a=b;b=t；

总结

本文初步探讨了 python 常见的性能优化技巧以及如何借助工具来定位和分析程序的性能瓶颈，并提供了相关可以进行性能优化的工具或语言，希望能够更相关人员一些参考。