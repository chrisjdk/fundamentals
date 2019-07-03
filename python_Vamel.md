[TOC]

### 1. 简单介绍

1. 电脑硬件：

   1. 控制器

   2. 运算器

      1+2 构成计算机cpu

   3. cpu存储器

   4. 输入设备

   5. 输出设备

2. 编程是什么？

   1. 操作系统(operation system)提供了一套系统调用(system call)，规定操作系统支持的操作。

   2. 系统调用定义一些**库函数(library routine)**将系统调用组合成特定的功能。

   3. 许多特定的指令重复出现，为了在程序中复用这些代码需要对代码进行**封装(packaging)**：将执行特殊功能的指令打包成一个程序块并将其命名方便查询和重复使用。

   4. 操作系统将底层硬件操作组合**封装**共上层应用程序调用。封装代码的方式有多种，根据不同的方式，编写程序时需要遵守特性的的编程风格，即**编程范式 (programming pradigm)**. 现代编程语言都支持多种范式。'Python'即为多范式语言.

      ​	_面向过程是一件事“该怎么做“，面向对象是一件事“该让谁来做”，然后那个“谁”就是对象，他要怎么做是他自己的事，反正最后一群对象合力能把事做好就行了._

   **Demo**

   ​	在终端输入`python`，如果想退出`python`，则输入

   ```shell
   >>>exit()
   ```

   ​	将 Python程序`hello.py`改成一个可执行的脚本，需在 Python 文本第一行加上 需要使用的 Python 编译器：

   ```python
   #!/usr/bin/env python
   ```

   ​	然后在终端中将 `hello.py` 的权限改为可执行：

   ```shell
   $chmod 755 hello.py
   ```

   ​	在终端中输入 python 文件的名字可以运行该程序

   ```shell
   $./hello.py
   ```

### 2. Python 语法

#### 2.1 运算

​	**1. 数值运算**

​		字符串也能进行加法运算，即把两个字符串连接为一个字符串。

​	**2. 逻辑运算**

​		`1: True`

​		`0: False`

​		**布尔值（Boolean)**:`True`和`False` 

​		`not`: 非运算 

```shell
>>>not True #结果为False
```

​	**3. 判别表达式**

​		`==`: 等于

​	**4. 运算优先级**

| 乘方：**                       |
| ------------------------------ |
| 乘除： *    ／                 |
| 加减： +    -                  |
| 判断： ==    >    >=    <   <= |
| 逻辑：!    and    or           |

#### 2.2 变量

​	为了保证数据在程序运行结束后不会消失需要将数据存储在存储器中，以便在后面的程序中可以重复使用。

​	计算器存储器中的每个存储单元都有一个地址，如同门牌号。数据被存入特定门牌号之间的隔间，可以通过门牌号来提取之前存储的数据。但用内存地址作为存储的地址索引有如下缺点：

  - 内存地址过长，难以记忆
  - 每个地址对应的存储空间大小固定，无法适应类型多变的数据
  - 对某个地址进行操作前无法确定该地址的存储空间是否已经被占用



​	设置**变量**存储数据

​	变量名作为变量空间的索引被调动从而提取所存储的数据。变量可以被给予

他的值。

#####2.2.1 变量的类型

​	Python能自由改变变量类型的特征被称为动态类型（Dynamic Typing）;

​	在静态类型（Static Typing）的语言中，变量有事先说明好的类型。特定类型的数据必须存入特定类型的变量。

​	Python的变量也是有类型的，可以用`type()`来查看变量的类型。

```python
var_integer = 1000
print(type(var_integer))
```

​	计算机存储空间以位 （bit）为单位，每一位只能存储一个0或1的数字。`bool`值存储空间只需要一位，因为布尔值`True`= 1, `False` = 0。`int`类型数据，以4为例，二进制表示为100，因此需要三个存储空间。

​	为了效率和实用性，计算机在内存中必须要分类型存储。静态类型语言中，新建变量必须说明类型，就是这个道理。动态类型的语言看起来不需要说明类型，但其实是把区分类型的工作交给解释器。这也是Python的速度不如C语言等静态类型语言的一个原因。

##### 2.2.2 容器型变量

**1. 序列**

​	序列是==有顺序==的数据集合。序列包含的一个数据被称为序列的一个**元素**（element）。序列可以包含一个或多个元素，也可以是完全没有任何元素的空序列。

​	序列有两种，**元组**（Tuple）和**列表**（List）。两者的主要区别在于，一旦建立，元组的各个元素不可再变更，而列表元素可以变更。元组看起来就像一种特殊的表，有固定的数据。因此，有的翻译也把元组称为“定值表”。

```shell
>>>example_tuple = (2, 1.3, "love", 5.6, 9, 12, False) #一个元组
>>>example_list = [True, 5, "smile"]  #一个列表
```

​	同一个序列可以包含不同类型的元素，这也是Python动态类型的一个体现。还有，序列的元素不仅可以是基本类型的数据，还可以是另外一个序列。

```shell
>>>nest_list = [1, [3, 4, 5]] #列表中嵌套另一个列表
```

​	元组不能改变数据，所以很少会建立一个空的元组。而序列可以增加和修改元素，所以Python程序中经常会建立空表。

​	序列中的元素是有序排列，所以可以根据每个元素中的位置来找到对应元素。序列元素的位置索引称为**下标**（Index）。Python中序列的下标从0开始，即第一个元素的对应下标为0。

```shell
>>>nest_list[1][2]     # 结果为5
```

​	表的数据可变更，因此可以对单个元素进行赋值。

​	对于序列来说，除了可以用下标来找到单个元素外，还可以通过范围引用的方式，来找到多个元素。范围引用的基本样式是：

​					序列名[下限:上限:步长]

​	在范围引用的时候，如果写明上限，那么这个上限下标指向的元素将不包括在结果中。

```shell
>>>example_tuple[:5]              # 从小标0到下标4，不包括下标5的元素
>>>example_tuple[2:]              # 从下标2到最后一个元素
>>>sliced = example_tuple[2:0:-1] # 从下标2到下标1
```

​	Python还提供了一种尾部引用的语法，用于引用序列尾部的元素:

```shell
>>>example_tuple[-1]             # 序列最后一个元素
>>>example_tuple[-3]             # 序列倒数第三个元素
>>>example_tuple[1:-1]           # 序列的第二个到倒数第二个元素
```

**2. 词典**：

​	词典不是以位置来作为索引的。词典允许用自定义的方式来建立数据的索引：

```shell
>>>example_dict = {"tom":11, "sam":57,"lily":100}
```

​	词典包含有多个元素，每个元素以逗号分隔。词典的元素包含两部分，键（Key）和值（Value）。键是数据的索引，值是数据本身。键和值一一对应。比如上面的例子中，"tom"对应11，"sam"对应57，"lily"对应100。由于键值之间的一一对应关系，所以词典的元素可以通过键来引用。

```shell
>>>example_dict["tom"]        # 结果为11
```

​	在词典中修改或增添一个元素的值：

```powershell
>>>example_dict["tom"]   = 30
>>>example_dict["lilei"] = 99
>>>example_dict  #结果为{"tom": 30, "lily": 100, "lilei": 99, "sam": 57}
```

​	构建一个新的空的词典：

```shell
>>>example_dict = {}
>>>example_dict        # 结果为{}
```

​	词典不具备序列那样的连续有序性，所以适于存储结构松散的一组数据。

#### 2.3 选择结构

​	`if ..., else ...`

​	else也并非必需的: 没有else，实际上与空的else等价。如果if后的条件不成立，那么计算机什么都不用执行。

​	`if ..., elif ...`:

	> 现在大部分的主流语言，如C、C++、Java、JavaScript，都是用花括号来标记程序块的，缩进也不是强制的。

#### 2.4 循环结构

​	`for`循环：有的时候，我们只是想简单地重复特定的次数，不想建立序列，那么我们可以使用Python提供的range()函数。

```python
for i in range(5):
	print(i, "Hello World!")
```

​	Python中`range()`提供的计数也是从0开始的，和表的下标一样。我们还看到`print()`的新用法，就是在括号中说明多个变量，用逗号分开。函数`print()`会把它们都打印出来。

​	`while`循环: `while`后面紧跟着一个条件。如果条件为真，则while会不停地循环执行隶属于它的语句。只有条件为假时，程序才会停止。

**Python代码规范**：

​	1．在下列运算符的前后各保留一个空格：

​		`= + - > == >= < <= and or not`

​	2．下列运算符的前后不用保留空格：

​		`* / **`

​	3．如果有多行赋值，那么将上下的赋值号=对齐，比如：

```python
num    = 1
secNum = 2
```

​	4．变量的所有字母小写，单词之间用下画线连接：

```python
example_number = 10
```

### 3. 函数和模块

​	函数和模块把成块的指令封装成可以重复调用的代码块，并借着函数名和模块名整理出一套接口，方便未来调用。输入数据被称为参数，参数能影响函数的行为。

#### 3.1 基本介绍

​	**定义函数**

​	制作函数的过程又称为定义函数(define function)。定义一个计算两个数的平方和的函数`square_sum()`。

```python
def square_sum(a,b):
	a = a**2
	b = b**2
	c = a + b
	return c
```

​	函数定义中的参数是一个形式代表，并非真正数据，所以又称为形参（Parameter）。在函数的具体执行中，参数所代表的数据确实是作为一个变量存在的。关键字`return`用于说明函数的返回值，即函数的输出数据。

​	在Python的语法中，`return`并不是必需的。如果没有`return`, 或者`return`后面没有返回值时，则函数将返回`None`。`None`是Python中的空数据，用来表示什么都没有。关键字`return`也返回多个值。多个值跟在`return`后面，以逗号分隔。从效果上看，其等价于返回一个有多个数据的元组。

**调用函数**

​	在函数调用时出现的参数称为实参（argument）。

​	如果一个函数有其他返回值，那么我们可以获得这个返回值。一个常见的做法是把返回值赋予给变量，方便以后使用。下面程序中调用了`square_sum()`函数：

```python
x = square_sum(3,4)
print(x)
```

**函数文档**

​	内置函数`help()`来找到某个函数的说明文档。

#### 3.2 参数传递

**基本传参**

​	把数据用参数的形式输入到函数，被称为参数传递。如果有多个参数，那么在调用函数时，Python会根据位置来确认数据对应哪个参数。

​	也可以用关键字（Keyword）的方式来传递参数。在定义函数时，我们给了形参一个符号标记，即参数名。关键字传递是根据参数名来让数据与符号对应上。因此，如果在调用时使用关键字传递，那么不用遵守位置的对应关系。

```python
def print_arguments(a, b, c):
	print(a, b, c)
	
print_arguments(1, 3, 5) #位置传递
print_arguments(c=5,b=3,a=1) #用关键字（Keyword）的方式来传递参数
```

​	位置传递与关键字传递可以混合使用，即一部分的参数传递根据位置，另一部分根据参数名。在调用函数时，所有的位置参数都要出现在关键字参数之前。如果把位置参数放在关键字参数后面，则Python将报错

```python
print_arguments(1, c=5,b=3)
```

**包裹传参**：

​	有时在定义函数时，我们并不知道参数的个数。其原因有很多，有时是确实不知道参数的个数，需要在程序运行时才能知道。有时是希望函数定义的更加松散，以便于函数能运用于不同形式的调用。这时候，用包裹（packing）传参的方式来进行参数传递会非常有用。

​	包裹传参也有位置和关键字两种形式。下面是包裹位置传参的例子：

```python
def package_position(*all_arguments):
	print(type(all_arguments))
  print(all_arguments)
  
package_position(1,4,6)
package_position(5,6,7,1,2,3)
```

​	在调用`package_position()`时，所有的数据都根据先后顺序，收集到一个元组。在函数内部，我们可以通过元组来读取传入的数据。这就是包裹位置传参。为了提醒Python参数`all_arguments`是包裹位置传递所用的元组名，我们在定义`package_position()`时要在元组名`all_arguments`前加`*`号。

​	包裹关键字传递的例子。这一参数传递方法把传入的数据收集为一个词典：

```python
def package_keyword(**all_arguments):
    print(type(all_arguments))
    print(all_arguments)
    
package_keyword(a=1,b=9)
package_keyword(m=2,n=1,c=11)
```

​	在包裹关键字传递的时候，数据容器不再是一个元组，而是一个字典。每个关键字形式的参数调用，都会成为字典的一个元素。参数名成为元素的键，而数据成为元素的值。字典`all_arguments`收集了所有的参数，把数据传递给函数使用。为了提醒，参数`all_arguments`是包裹关键字传递所用的字典，因此在`all_arguments`前加`**`。

​	包裹位置传参和包裹关键字传参还可以混合使用，比如：

```python
def package_mix(*positions, **keywords):
  print(positions)
  print(keywords)
  
package_mix(1, 2, 3, a=7, b=8, c=9)
```

​	还可以更进一步，把包裹传参和基本传参混合使用。它们出现的先后顺序是：位置→关键字→包裹位置→包裹关键字。

**解包裹**

​	除了用于函数定义，`*`和`**`还可用于函数调用。这时候，两者是为了实现一种叫作解包裹（unpacking）的语法。解包裹允许我们把一个数据容器传递给函数，再自动地分解为各个参数。需要注意的是，包裹传参和解包裹并不是相反操作，而是两个相对独立的功能。下面是解包裹的一个例子：

```python
def unpackage(a,b,c):
  print(a,b,c)
  
args = (1, 3, 4)
unpackage(*args) # 结果为1 3 4
```

​	在这个例子中，unpackage()使用了基本的传参方法。函数有三个参数，按照位置传递。但在调用该函数时，我们用了解包裹的方式。可以看到，我们调用函数时传递的是一个元组。按照基本传参的方式，一个元组是无法和三个参数对应上的。但我们通过在args前加上*符号，来提醒Python，我想把元组拆成三个元素，每一个元素对应函数的一个位置参数。于是，元组的三个元素分别赋予了三个参数。

​	相应的，词典也可用于解包裹，使用相同的unpackage()定义：

```python
args = {"a":1,"b":2,"c":3}
unpackage(**args)      # 打印1、2、3
```

#### 3.3 递归

​	递归是函数调用其自身的操作。

​	用编程的方法来解决高斯求和：

```python
sum = 0

for i in range(1,101): # range()这样的写法表示从1开始，直到100
  sum = sum + i

print(sum)
```

​	我们还可以用下面的方式解题：

```python
def gaussian_sum(i):
	if i==1:
		return 1
  else:
    return i + print_gaussian(i-1)
  print gaussian_sum(i)
  
gaussian_sum(100)
```

​	上面的解法使用了递归（Recursion），即在一个函数定义中，调用了这个函数自身。为了保证计算机不陷入死循环，递归要求程序有一个能够达到的终止条件（Base Case）。

**函数栈（stack**）

​	程序中的递归需要用到**栈**（Stack）这一数据结构。所谓数据结构，是计算机存储数据的组织方式。栈是数据结构的一种，可以有序地存储数据。

​	栈最显著的特征是**“后进先出”**（LIFO，Last In，First Out）。栈的每个元素，称为一个**帧**（frame）。栈只支持两个操作：pop和 push。栈用弹出（pop）操作来取出栈顶元素，用推入（push）操作将一个新的元素存入栈顶。

#### 3.4 模块

​	Python通过模块调用其他文件中的函数。除了函数，我们还可以引入其他文件中包含的数据。对于面向过程语言来说，模块是比函数更高一层的封装模式。程序可以以文件为单位实现复用。典型的面向过程语言，如C语言，有很完善的模块系统。把常见的功能编到模块中，方便未来使用，就成为所谓的**库**（library）。

**搜索路径**

​	在引入模块时，把库文件和应用文件放在了同一文件夹下。当在该文件夹下运行程序时，Python会自动在当前文件夹搜索它想要引入的模块。

​	但Python还会到其他的地方寻找库：

​	（1）标准库的安装路径

​	（2）操作系统环境变量`PYTHONPATH`所包含的路径

​	标准库是Python官方提供的库。Python会自动搜索标准库所在的路径。因此，Python总能正确地引入标准库中的模块。

​	如果你是自定义的模块，则可以放在自认为合适的地方，然后修改`PYTHONPATH`这个环境变量。当PYTHONPATH包含模块所在的路径时，Python便可以找到那个模块。

#### 3.5 异常处理

​	只有在运行时，编译器才会发现的错误被称为**运行时错误**（Runtime Error）。由于Python是动态语言，许多操作必须在运行时才会执行，比如确定变量的类型等。因此，Python要比静态语言更容易产生运行时错误。

​	还有一种错误，称为**语义错误**（Semantic Error）。编译器认为你的程序没有问题，可以正常运行。但当检查程序时，却发现程序并非你想做的。

​	对于运行时可能产生的错误，我们可以提前在程序中处理。这样做有两个可能的目的：一个是让程序中止前进行更多的操作，比如提供更多的关于错误的信息。另一个则是让程序在犯错后依然能运行下去。

​	异常处理还可以提高程序的容错性。下面的一段程序就用到了异常处理：

```python
while True:
  inputStr = input("Please input a number:")
  try:
    num = float(inputstr)
    print("Input number:", num)
    print("result:", 10/num)
  except ValueError:
     print("Illegal input．Try Again.")
  except ZeroDivisionError:
        print("Illegal devision by zero．Try Again.")
```

异常处理完整的语法形式为：

```python
try:
  ...
except exception1:
  ...
except exception2:
  ...
else:
  ...
finally:
  
```

​	The [`raise`](https://docs.python.org/3/reference/simple_stmts.html#raise) statement allows the programmer to force a specified exception to occur. For example:

```shell
>>> raise NameError('HiThere')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: HiThere
```

#### 3.6 搜索路径的设置

​	在Python内部，可以用下面的方法来查询搜索路径：

```shell
>>>import sys
>>>print(sys.path)
```

​	`sys.path`是一个列表。列表中的每个元素都是一个会被搜索的路径。我们可以通过增加或删除这个列表中的元素，来控制Python的搜索路径。

```shell
export PYTHONPATH=/new/python/lib:$PYTHONPATH
```

### 4.面向对象

#### 4.1 对象（object）

###### 4.1.1 类（class）

​	日常生活中，我们把相近的东西归为一类，而且给这个类起一个名字。比如说，鸟类的共同属性是有羽毛，通过产卵生育后代。任何一只特别的鸟都是建立在鸟类的原型基础上的。

​	下面我们用Python语言来记录上面的想法，描述鸟类：

```python
class Bird(object):
  feather = True
  reproduction = "egg"
```

​	在这里，我们用关键字`class`来定义一个类。类的名字就是鸟（Bird）。括号里有一个关键词`object`，也就是“东西”的意思，即某一个个体。在计算机语言中，我们把个体称为对象。一个类别下，可以有多个个体。

​	冒号和缩进说明了属于这个类的代码。在隶属于这个类别的程序块中，我们定义了两个量，一个用于说明鸟类有羽毛（feather），另一个用于说明鸟类的繁殖方式（reproduction），这两个量称为类的属性（attribute）。

​	除了用数据性的属性来分辨类别外，有时也会根据这类东西能做什么事情来区分。比如说，鸟会移动。这样，鸟就和房屋的类别就区分开了。这些动作会带来一定的结果，比如移动导致位置的变化。这样的一些“行为”属性称为**方法**（method）。Python中，一般通过在类的内部定义函数来说明方法。

```python
class Bird(object):
  feather = True
  reproduction = "egg"
  def chirp(self, sound):
    print(sound)
```

​	我们给鸟类新增一个方法属性，就是表示鸟叫的方法`chirp()`。方法`chirp()`看起来很像一个函数。它的第一个参数是`self`，是为了在方法内部引用对象自身，我将在后面详细解释。需要强调的是，无论该参数是否用到，==方法的第一个参数必须是用于指代对象自身的`self`==。剩下的参数`sound`是为了满足我们的需求设计的，它代表了鸟叫的内容。方法`chirp()`会把`sound`打印出来。

###### 4.1.2 对象

​	通过调用类，我们可以创造出这个类下面的一个对象。比如说，我养了一只小鸡，叫`summer`。它是个对象，且属于鸟类。我们使用前面已经定义好的鸟类，产生这个对象：

```python
summer = Bird()
```

​	通过这一句创建对象，并说明`summer`是属于鸟类的一个对象。现在，我们就可以使用鸟类中已经写好的代码了。作为对象的`summer`将拥有鸟类的属性和方法。对属性的引用是通过**对象.属性**（`object.attribute`）的形式实现的。比如说：

```python
print(summer.reproduction) #打印‘egg’
```

​	此外，我们还可以调用方法，让summer执行鸟类允许的动作。比如：

```python
summer.chirp("jijiji")          # 打印'jijiji'
```

​	在调用方法时，我们只传递了一个参数，也就是字符串"jijiji"。这正是方法与函数有所区别的地方。尽管在定义类的方法时，我们必须加上这个`self`参数，但`self`只用能在类定义的内部，所以在调用方法时不需要对`self`传入数据。通过调用`chirp()`方法，我的`summer`就可以叫了。

​	到现在为止，描述对象的数据都存储于类的属性中。类属性描述了一个类的共性，比如鸟类都有羽毛。所有属于该类的对象会共享这些属性。比如说，summer是鸟类的一个对象，因此summer也有羽毛。当然，我们可以通过某个对象来引用某个类属性。

​	对于一个类下的全部个体来说，==某些属性可能存在个体差异==。比如说，我的summer是黄色的，但并非所有的鸟儿都是黄色的。再比如说人这个类。性别是某个人的一个性质，不是所有的人类都是男，或者都是女。这个性质的值随着对象的不同而不同。李雷是人类的一个对象，性别是男。韩美美也是人类的一个对象，性别是女。

​	因此，为了完整描述个体，除了共性的类属性外，我们还需要用于说明个性的对象属性。==在类中，我们可以通过self来操作对象的属性。==现在我们拓展Bird类：

```python
class Bird(object):
  def chirp(self, sound):
    print(sound)
  def set_color(self, color):
    self.color = color
    
summer = Bird()
summer.set_color("yellow")
print(summer.color)
```

​	在方法`set_color()`中，我们通过`self`参数设定了对象的属性`color`。和类属性一样，我们能通过**对象.属性**的方式来操作对象属性。由于对象属性依赖于`self`，所以我们必须在某个方法内部才能操作类属性。因此，对象属性没办法像类属性一样，在类下方直接赋初值。

​	Python还是提供了初始化对象属性的办法。Python定义了一系列**特殊方法**。特殊方法又被称为**魔法方法**（Magic Method）。特殊方法的方法名很特别，前后有两个下画线，比如`__init__()`、`__add__()`、`__dict__()`等。程序员可以在类定义中设定特殊方法。Python会以特定的方式来处理各个特殊方法。对于类的`__init__()`方法，Python会在每次创建对象时自动调用。因此，我们可以在`__init__()`方法内部来初始化对象属性：

```python
class Bird(object):
	def __init__(self, sound):
		self.sound = sound
		print("my sound is:", sound)
  def chirp(self):
  	print(self.sound)
  	
summer = Bird("ji")
summer.chirp()  #打印'ji'
```

​	在上面的类定义中，我们通过`__init__()`方法说明了这个类的初始化方式。每当对象建立时，比如创建`summer`对象时，`__init__()`方法就会被调用。它会设定`sound`这个对象属性。在后面的`chirp()`方法中，就可以通过`self`调用这一对象属性。除了设定对象属性外，我们还可以在`__init__()`中加入其他指令。这些指令会在创建对象时执行。在调用类时，类的后面可以跟一个参数列表。这里放入的数据将传给`__init__()`的参数。通过`__init__()`方法，我们可以在创建对象时就初始化对象属性。

​	除了操作对象属性外，`self`参数还有另外一个功能，就是能让我们在一个方法内部调用同一类的其他方法，比如：

```python
class Bird(object):
  def chirp(self, sound):
    print(sound)
    
  def chirp_repeat(self,sound,n):
    for i in range(n):
      self.chirp(sound)
      
summer = Bird()
summer.chirp_repeat('ji',10) 
#在方法chirp_repeat()中，我们通过self调用了类中的另一个方法chirp()。
```

####4.2 子对象

######4.2.1 子类

​	类别本身还可以进一步细分成子类。比如说，鸟类可以进一步分成鸡、天鹅。在面向对象编程中，我们通过**继承**（Inheritance）来表达上述概念。

```python
class Bird(object):
  feather = True
  reproduction = 'egg'
  def chirp(self, sound):
    print(sound)
    
class Chicken(Bird):
  how_to_move='walk'
  edible = True
  
class Swan(Bird):
  how_to_move='swim'
  edible = False
  
summer = Chicken()
print(summer.feather)   # 打印True
summer.chirp('ji')			# 打印'ji'
```

​	新定义的鸡（`Chicken`）类，增加了两个属性：移动方式（`how_to_move`）和可以食用（`edible`）

​	在类定义时，括号里为`Bird`。这说明，鸡类是属于鸟类（`Bird`）的一个子类，即`Chicken`继承自`Bird`。自然而然，鸟类就是鸡类的父类。`Chicken`将享有`Bird`的所有属性。尽管我们只声明了`summer`是鸡类，但它通过继承享有了父类的属性，比如数据性的属性`feather`，还有方法性的属性`chirp()`。新定义的天鹅`（Swan）`类，同样继承自鸟类。在创建一个天鹅对象时，该对象自动拥有鸟类的属性。

​	继承提高了程序的可重复使用性。最基础的情况，是类定义的括号中是`object`。类`object`其实是Python中的一个内置类。它充当了所有类的祖先。

###### 4.2.2 属性覆盖

​	在继承的过程中，我们可以在子类中增加父类不存在的属性，从而增强子类的功能。此外，我们还可以在子类中替换父类已经存在了的属性。

```python
class Bird(object):
    def chirp(self):
        print("make sound")
    
class Chicken(Bird):
    def chirp(self):
        print("ji")
    
bird    = Bird()
bird.chirp()       # 打印'make sound'

summer = Chicken()
summer.chirp()     # 打印'make sound'和'ji'
```

​	通过对方法的覆盖，我们可以彻底地改变子类的行为。但有的时候，子类的行为是父类行为的拓展。这时，我们可以通过`super`关键字在子类中调用父类中被覆盖的方法，比如：

```python
class Bird(object):
    def chirp(self):
        print("make sound")
    
class Chicken(Bird):
    def chirp(self):
        super().chirp()
        print("ji")
    
bird    = Bird()
bird.chirp()       # 打印"make sound"
    
summer = Chicken()
summer.chirp()     # 打印"make sound"和"ji"
```

​	在鸡类的`chirp()`方法中，我们使用了`super`。它是一个内置类，能产生一个指代父类的对象。通过`super`，我们在子类的同名方法中调用了父类的方法。这样，子类的方法既能执行父类中的相关操作，又能定义属于自己的额外操作。

​	调用`super`的语句可以出现在子类方法的第一句，也可以出现在子类方法的任意其他位置。

####4.3 对象的分类

###### 4.3.1 列表对象

​	数据容器中的列表。它是一个类，用内置函数可以找到类的名字：

```shell
>>>a = [1, 2, 5, 3, 5]
>>>type(a)
```

​	根据返回的结果，我们知道`a`属于`list`类型，也就是列表类型。其实，所谓的类型就是对象所属的类的名字。每个列表都属于这个`list`类。这个类是Python自带的，已经提前定义好的，所以称为内置类。当我们新建一个表时，实际上是在创建`list`类的一个对象。我们还可以用其他两个内置函数来进一步调查类的信息：`dir()`和`help()`。函数`dir()`用来查询一个类或者对象的所有属性。

```shell
>>>dir(list)
```

​	制作类的说明文档的方式，与制作函数说明文档类似，我们只需在类定义下用多行字符串加入自己想要的说明就可以了：

```python
class HelpDemo(object):
    """
    This is a demo for using help() on a class
    """
    pass
    
print(help(HelpDemo))
```

​	程序中的`pass`是Python的一个特殊关键字，用于说明在该语法结构中“什么都不做”。这个关键字保持了程序结构的完整性。

**列表的其他操作方法**：

​	下面一些list的方法，可以返回列表的信息：

```shell
>>>a = [1, 2, 3, 5, 9.0, "Good", -1, True, False, "Bye"]
>>>a.count(5)       # 计数，看总共有多少个元素5
>>>a.index(3)       # 查询元素3第一次出现时的下标
```

​	有些方法还允许我们对列表进行修改操作：

```shell
>>>a.append(6)             # 在列表的最后增添一个新元素6
>>>a.sort()                # 排序
>>>a.reverse()             # 颠倒次序
>>>a.pop()                 # 去除最后一个元素，并将该元素返回。
>>>a.remove(2)             # 去除第一次出现的元素2
>>>a.insert(0,9)           # 在下标为0的位置插入9
>>>a.clear()               # 清空列表
```

###### 4.3.2 元组与字符串对象

​	元组与列表一样，都是序列。但元组不能变更内容。因此，元组只能进行查询操作，不能进行修改操作。

​	字符串是特殊的元组,但字符串（`string`）有一些方法能改变字符串。这听起来似乎违背了元组的不可变性。其实，这些方法并不是修改字符串对象，而是删除原有字符串，再建立一个新的字符串，所以并没有违背元组的不可变性。

​	下面总结了字符串对象的方法。`str`为一个字符串，`sub`为`str`的一个子字符串。`s`为一个序列，它的元素都是字符串。`width`为一个整数，用于说明新生成字符串的宽度。这些方法经常用于字符串的处理。

```python
>>>str = "Hello World!"
>>>sub = "World"
    
>>>str.count(sub)           # 返回：sub在str中出现的次数
>>>str.find(sub)            # 返回：从左开始，查找sub在str中第一次出现的位置。如果str中不包含sub，返回 -1
>>>str.index(sub)           # 返回：从左开始，查找sub在str中第一次出现的位置。如果str中不包含sub，举出错误
>>>str.rfind(sub)           # 返回：从右开始，查找sub在str中第一次出现的位置.如果str中不包含sub，返回 -1
>>>str.rindex(sub)          # 返回：从右开始，查找sub在str中第一次出现的位置.如果str中不包含sub，举出错误
>>>str.isalnum()            # 返回：True，如果所有的字符都是字母或数字
>>>str.isalpha()            # 返回：True，如果所有的字符都是字母
>>>str.isdigit()            # 返回：True，如果所有的字符都是数字
>>>str.istitle()            # 返回：True，如果所有的词的首字母都是大写
>>>str.isspace()            # 返回：True，如果所有的字符都是空格
>>>str.islower()            # 返回：True，如果所有的字符都是小写字母
>>>str.isupper()            # 返回：True，如果所有的字符都是大写字母
>>>str.split([sep, [max]])     # 返回：从左开始，以空格为分隔符（separator），将str分割为多个子字符串，总共分割max次。将所得的子字符串放在一个表中返回。可以以str.split(",")的方式使用其他分隔符
>>>str.rsplit([sep, [max]])    # 返回：从右开始，以空格为分隔符（separator），# 将str分割为多个子字符串，总共分割max次。将所得的子字符串放在一个表中返回。可以以str.rsplit(",")的方式使用其他分隔符
>>>str.join(s)                 # 返回：将s中的元素，以str为分隔符，合并成为一个字符串。
>>>str.strip([sub])   # 返回：去掉字符串开头和结尾的空格。 也可以提供参数sub，去掉位于字符串开头和结尾的sub
>>>str.replace(sub, new_sub)   # 返回：用一个新的字符串new_sub替换str中的sub
>>>str.capitalize()            # 返回：将str第一个字母大写
>>>str.lower()                 # 返回：将str全部字母改为小写
>>>str.upper()                 # 返回：将str全部字母改为大写
>>>str.swapcase()              # 返回：将str大写字母改为小写，小写字母改为大写
>>>str.title()                 # 返回：将str的每个词（以空格分隔）的首字母# 大写
>>>str.center(width)           # 返回：长度为width的字符串，将原字符串放入该字符串中心，其他空余位置为空格。
>>>str.ljust(width)      # 返回：长度为width的字符串，将原字符串左对齐放入该字符串，其他空余位置为空格。
>>>str.rjust(width)      # 返回：长度为width的字符串，将原字符串右对齐放入. 该字符串，其他空余位置为空格。
```

######4.3.3 词典对象

​	词典同样是一个类：

```python
>>>example_dict = {"a":1, "b":2}
>>>type(example_dict)
```

​	我们可以通过词典的`keys()`方法，来循环遍历每个元素的键：

```python
for k in example_dict.keys():
    print(example_dict[k])
```

​	通过`values()`方法，可以遍历每个元素的值。或者用`items`方法，直接遍历每个元素：

```python
for v in example_dict.values():
    print(v)
for k,v in example_dict.items():
    print(k, v)
```

​	我们也可以用`clear()`方法，清空整个词典：

```python
example_dict.clear()          # 清空example_dict，example_dict变为{}
```

###### 4.3.4 循环对象

​	所谓的循环对象包含有一个`__next__()`方法[(2)](opeb://31fe54eaa82223b74751beaeb4113f2e/epubbook.xhtml#Textpart0008.xhtmlch2)。这个方法的目的是生成循环的下一个结果。在生成过循环的所有结果之后，该方法将抛出`StopIteration`异常

​	当一个像`for`这样的循环语法调用循环对象时，它会在每次循环的时候调用`__next__()`方法，直到`StopIteration`出现。循环接收到这个异常，就会知道循环已经结束，将停止调用`__next__()`。

​	我们用内置函数`iter()`把一个列表转变为循环对象。这个循环对象将拥有`__next__()`方法。我们多次调用`__next__()`方法，将不断返回列表的值，直到出现异常：

```python
>>>example_iter = iter([1, 2])
>>>example_iter.__next__()  # 显示1
>>>example_iter.__next__()  # 显示2
>>>example_iter.__next__()  # 出现StopIteration异常。
```

​	我们可以借助**生成器**（generator）来自定义循环对象。生成器的编写方法和函数定义类似，只是在`return`的地方改为`yield`。生成器中可以有多个`yield`。当生成器遇到一个`yield`时，会暂停运行生成器，返回`yield`后面的值。当再次调用生成器的时候，会从刚才暂停的地方继续运行，直到下一个`yield`。生成器自身又构成一个循环对象，每次循环使用一个`yield`返回的值。

​	下面是一个生成器：

```python
def gen():
  a = 100
  yield a
  a = a*8
  yield a
  yield 1000 
```

​	该生成器共有三个yield，如果用作循环对象时，会进行三次循环。

```python
for i in gen():
    print(i)
```

​	再考虑下面一个生成器:

```python
def gen():
    i = 0
    while i < 10000000:
       i = i + 1
       yield i
```

###### 4.3.5 函数对象

​	函数也是一种对象。实际上，任何一个有`__call__()`特殊方法的对象都被当作是函数。比如下面的例子：

```python
class SampleMore(object):
  def __call__(self, a):
      return a + 5
    
add_five = SampleMore()         # 生成函数对象
print(add_five(2))              #像一个函数一样调用函数对象，结果为7。
```

######4.3.6 模块对象

​	模块也是对象。比如，我们直接引入标准库中的模块`time`：

```python
import time
    
print(dir(time))
```

​	`time`有很多属性可以调用，例如`sleep()`方法。我们之前用`import`语句引入其他文件中定义的函数，实际上就是引入模块对象的属性，比如：

```python
from time import sleep

sleep(10)
print("wake up")
```

​	模块`time`的`sleep()`会中止程序。调用时的参数说明给了中止的时间。我们还可以用简单暴力的方法，一次性引入模块的所有属性：

```python
from time import *
sleep(10)
```

​	既然知道了sleep()是time的一个方法，那么我们当然可以利用对象.属性的方式来调用它。

```python
import time
time.sleep(10)
```

​	在引入模块时，我们还可以给模块换个名字:

```python
import time as t
t.sleep(10)
```

​	可以将功能相似的模块放在同一个文件夹中，构成一个模块包。比如放在`this_dir`中：

```python
import this_dir.module
```

​	引入this_dir文件夹中的module模块。

​	该文件夹中必须包含一个`__init__.py`的文件，提醒Python，该文件夹为一个模块包。`__init__.py`可以是一个空文件。

​	每个模块对象都有一个`__name__`属性，用来记录模块的名字，例如：

```python
import time
print(time.__name__)
```

​	当一个`.py`文件作为主程序运行时，比如python foo.py，这个文件也会有一个对应的模块对象。但这个模块对象的`__name__`属性会是`__main__`。因此，我们在很多`.py`文件中可以看到下面的语句：

```python
if __name__ == "__main__"：
    ...
```

​	它的意思是说，如果这个文件作为一个主程序运行，那么将执行下面的操作。有的时候，一个`.py`文件中同时有类和对象的定义，以及对它们的调用。当这些`.py`文件作为库引入时，我们可能并不希望执行这些调用。通过把调用语句放到上面的`if`中，就可以在调用时不执行这些调用语句了。

###### 4.3.7 异常对象

​	可以在程序中加入异常处理的`try`结构，捕捉程序中出现的异常。实际上，我们捕捉到的也是一个对象，比如：

```python
try:
	m = 1/0
except ZeroDivisionError as e:
  print("Catch NameError in the sub-function")
  
print(type(e))			 # 类型为"exceptions.ZeroDivisionError"
print(dir(e))				# 异常对象的属性
print(e.message)    # 异常信息integer division or modulo by zero
```

### 5 对象式编程

#### 5.1 存储

**文件**

​	我们可以通过内置函数`open`来创建文件对象。在调用`open`时，需要说明文件名，以及打开文件的方式：

```python
f = open(文件名，方式)
```

​	打开文件的常用方式有：

```python
"r" # 读取已经存在的文件
"w" # 新建文件，并写入
"a" # 如果文件存在，那么写入到文件的结尾。如果文件不存在，则新建文件并写入
```

​	例如：

```python
>>>f = open("test.txt","r") #用只读的方式，打开了一个名为test.txt的文件
```

​	通过上面返回的对象，我们可以读取文件：

```python
content = f.read(10)         # 读取10个字节的数据
content = f.readline()       # 读取一行
content = f.readlines()      # 读取所有行，储存在列表中，每个元素是一行。
```

​	如果以`"w"`或`"a"`方式打开，那么我们可以写入文本：

```python
f = open("test.txt", "w")
f.write("I like apple")      # 将"I like apple"写入文件
```

​	在打开的文件中输入一行需要在字符串末尾添加换行符号`\n`

```python
f.write("I like apple.\n")
```

​	关闭文件：

```python
f.close()
```

**上下文管理器**

​	文件操作常常和上下文管理器一起使用。**上下文管理器**（context manager）用于规定某个对象的使用范围。一旦进入或者离开该使用范围，则会有特殊操作被调用，比如为对象分配或者释放内存。上下文管理器可用于文件操作。对于文件操作来说，我们需要在读写结束时关闭文件。程序员经常会忘记关闭文件，无谓的占用资源。上下文管理器可以在不需要文件的时候，自动关闭文件。

​	下面是一段常规的文件操作程序：

```python
# 常规文件操作
f = open("new.txt", "w")
print(f.closed) # 检查文件是否打开
f.write("Hello, world!")
f.close() 

print(f.closed) #打印True
```

​	加入上下文管理器的语法，就可以把程序改写为：

```python
#上下文管理器

with open("new.txt","w") as f:
  f.write("Hello, world!")
  
print(f.closed)
```

​	上面的上下文管理器基于`f`对象的`__exit__()`特殊方法。使用上下文管理器的语法时，Python会在进入程序块之前调用文件对象的`__enter__()`方法，在结束程序块的时候调用文件对象的`__exit__()`方法。在文件对象的`__exit__()`方法中，有`self.close()`语句。因此，在使用上下文管理器时，我们就不用明文关闭文件了。

​	任何定义了`__enter__()`方法和`__exit__()`方法的对象都可以用于上下文管理器。下面，我们自定义一个类`Vow`，并定义它的`__enter__()`方法和`__exit__()`方法。因此，由`Vow`类的对象可以用于上下文管理器：

```python
class Vow(object):
  def __init__(self, text):
    self.text = text
# __enter__()返回一个对象。上下文管理器会使用这一对象作为as所指的变量
  def __enter__(self):
    self.text = "I say: " + self.text
    return self
#__exit__()有四个参数。当程序块中出现异常时，__exit__()参数中的exc_type、exc_value、traceback用于描述异常。我们可以根据这三个参数进行相应的处理。如果正常运行结束，则这三个参数都是None
  def __exit__(self, exc_type, exc_value, traceback):
    self.text = self.text + "!"
    
with Vow("I'm fine")as myVow:
  print(myVow.text)
  
print(myVow.text)
```

**Pickle Package**

​	我们能把文本存于文件。但Python中最常见的是对象，当程序结束或计算机关机时，这些存在于内存的对象会消失。Pickle package可以把某个对象保存下来，再存成磁盘里的文件。

​	实际上，对象的存储分为两步。第一步，我们将对象在内存中的数据直接抓取出来，转换成一个有序的文本，即所谓的序列化（Serialization）。第二步，将文本存入文件。等到需要时，我们从文件中读出文本，再放入内存，就可以获得原有的对象。下面是一个具体的例子，首先是第一步序列化，将内存中的对象转换为文本流：

```python
import pickle

class Bird(object):
  have_feather = True
  reproduction_method = "egg"
  
summer = Bird()  # 创建对象
pickle_string = pickle.dumps(summer) # 序列化对象
```

​	使用pickle包的`dumps()`方法可以将对象转换成字符串的形式。随后我们用字节文本的存储方法，将该字符串储存在文件。继续第二步：

```python
with open("summer.pkl", "wb") as f:
	f.write(pickle_string)
```

​	读取对象与存储对象的过程正好相反。首先，我们从文件中读出文本。然后使用pickle的`loads()`方法，将字符串形式的文本转换为对象。我们也可以使用pickle的`load()`的方法，将上面两步合并。

​	有时候，仅仅是反向恢复还不够。对象依赖于它的类，所以Python在创建对象时，需要找到相应的类。因此当我们从文本中读取对象时，程序中必须已经定义过类。对于Python总是存在的内置类，如列表、词典、字符串等，不需要再在程序中定义。但对于用户自定义的类，就必须要先定义类，然后才能从文件中载入该类的对象。下面是一个读取对象的例子：

```python
import pickle

class Bird(object):
  have_feather = True
  reproduction_method = "egg"
  
with open("summer.pkl","rb") as f:
  summer = pickle.load(f)
  
print(summer.have_feather)
```

#### 5.2 计时

**time包**

​	我们能通过Python编程来管理时间和日期。标准库的time包提供了基本的时间功能。下面使用time包：

```python
import time

print(time.time()) # 挂钟时间，单位是秒
```

​	还能借助模块time测量程序运行时间。比如：

```python
import time

start = time.clock()
for i in range(100000):
  print(i**2)

end = time.clock()
print(end - start)
```

​	上面的程序调用了两次`clock()`方法，从而测量出镶嵌其间的程序所用的时间。在不同的计算机系统上，`clock()`的返回值会有所不同。在UNIX系统上，返回的是处理器时间。当CPU处于闲置状态时，处理器时间会暂停。因此，我们获得的是CPU运行时间。在Windows系统上，返回的则是挂钟时间。

​	方法`sleep()`可以让程序休眠。根据`sleep()`接收到的参数，程序会在某时间间隔之后醒来继续运行：

```python
import time

print('start')
time.sleep(10)

print('wake up')
```

​	time包还定义了`struct_time`对象。该对象将挂钟时间转换为年、月、日、时、分、秒等，存储在该对象的各个属性中，比如`tm_year`、`tm_mon`、`tm_mday`……下面几种方法可以将挂钟时间转换为`struct_time`对象：

```python
st = time.gmtime()  #返回struct_time格式的UTC时间
st = time.localtime()
```

​	我们也可以反过来，把一个`struct_time`对象转换为`time`对象：

```python
s = time.mktime(st) 
```

**datetime包**

​	datetime包是基于time包的一个高级包，用起来更加便利。datetime可以理解为由date和time两个部分组成。date是指年、月、日构成的日期，相当于日历。time是指时、分、秒、毫秒构成的一天24小时中的具体时间，提供了与手表类似的功能。因此，`datetime`模块下有两个类：`datetime.date`类和`datetime.time`类。你也可以把日历和手表合在一起使用，即直接调用`datetime.datetime`类。这里只介绍综合性的`datetime.datetime`类，单独的`datetime.date`和`datetime.time`类与之类似。

​	一个时间点，比如2012年9月3日21时30分，我们可以用如下方式表达：

```python
import datetime

t= datetime.datetime(2012,9,3,21,30)
print(t)
```

​	对象t有如下属性：

```
hour, minute, second, millisecond,microsecond：小时、分、秒、毫秒、微秒
year, month, day, weekday：年、月、日、星期几
```

​	借助`datetime`包，我们还可以进行时间间隔的运算。它包含一个专门代表时间间隔对象的类，即`timedelta`。一个`datetime.datetime`的时间点加上一个时间间隔，就可以得到一个新的时间点。比如今天的上午3点加上5个小时，就可以得到今天的上午8点。同理，两个时间点相减可以得到一个时间间隔：

```python
import datetime

t      = datetime.datetime(2012,9,3,21,30)
t_next = datetime.datetime(2012,9,5,23,30) 
delta1 = datetime.timedelta(seconds = 600) 
delta2 = datetime.timedelta(weeks = 3) 

print(t + delta1)   # 打印2012-09-03 21:40:00
print(t + delta2)   # 打印2012-09-24 21:30:00
print(t_next - t)   # 打印2 days, 2:00:00
```

​	在给`datetime.timedelta`传递参数时，除了上面的秒（seconds）和星期（weeks）外，还可以是天（days）、小时（hours）、毫秒（milliseconds）、微秒（microseconds）。

​	两个`datetime`对象能进行比较运算，以确定哪个时间间隔更长。比如使用上面的`t`和`t_next`：

```
print(t>t_next) # False
```

**日期格式**

​	对于包含有时间信息的字符串来说，我们可以借助datetime包，把它转换成datetime类的对象，比如：

```python
from datetime import datetime

str = 'output-1997-12-23-030000.txt'

format = 'output-%Y-%m-%d-%H%M%S.txt'
t = datetime.strptime(str, format)

print(t)  #打印1997-12-23 03:00:00
```

​	包含有时间信息的字符串是`"output-1997-12-23-030000.txt"`，是一个文件名。字符串`format`定义了一个格式。这个格式中包含了几个由`%`引领的特殊字符，用来代表不同时间信息。`%Y`表示年份、`%m`表示月、`%d`表示日、`%H`表示24小时制的小时、`%M`表示分、`%S`表示秒。通过`strptime`方法，Python会把需要解析的字符串往格式上凑。比如说，在格式中`%Y`的位置，正好看到`"1997"`，就认为`1997`是`datetime`对象`t`的年。以此类推，就从字符串中获得了`t`对象的时间信息。

​	反过来，我们也可以调用`datetime`对象的`strftime`方法，将一个`datetime`对象转换为特定格式的字符串，比如：

```python
from datetime import datetime
format = "%Y-%m-%d %H:%M"
t = datetime(2012,9,5,23,30)
print(t.strftime(format))              # 打印2012-09-05 23:30
```

常用特殊符号：

```python
%A: 表示英文的星期几，如Sunday、Monday……
%a：简写的英文星期几，如Sun、Mon……
%I：表示小时，12小时制
%p：上午或下午，即AM或PM
%f：表示毫秒，如2、0014、000001
```

#### 5.3 正则表达式

######5.3.1 re Package

​	Python 中用`re` package来处理正则表达式。如下时应用`re` to locate a No. in a string.

```python
import re
m = re.search("[0-9]", "abcd4ef")
print(m.group(0))
```

​	`re.search()`接收两个参数，第一个参数`"[0-9]"`就是我们所说的正则表达式，它告诉Python，“听着，我想从字符串中找从0到9的任意一个数字字符”。

​	`re.search()`如果从第二个参数中找到符合要求的子字符串，就返回一个对象`m`，你可以通过`m.group()`的方法查看搜索到的结果。如果没有找到符合要求的字符，则`re.search()`会返回`None`。

​	`除了search()`方法外，`re`包还提供了其他搜索方法，它们的功能有所差别：

```python
m = re.search(pattern, string) # look over a string to locate the targeted string

m = re.match(pattern, string) # look over a string to check whether the regular expressions match, and they should match from the 1st char.
```

​	还可以在搜索之后将搜索到的子字符串进行**替换**。下面的`sub()`利用正则`pattern`在字符串`string`中进行搜索。对于搜索到的字符串，用另一个字符串`replacement`进行替换。函数将返回替换后的字符串：


```python
str = re.sub(pattern, string)
```

​	**Other Methods**

```python
re.split() # 根据正则表达式分割字符串，将分割后的所有子字符串放在一个表(list)中返回

re.findall()      # 根据正则表达式搜索字符串，将所有符合条件的子字符串放在一个表(list)中返回
```

###### 5.3.2 Define a Regular Expression

```python
.             # 任意的一个字符
a|b           # 字符a或字符b
[afg]         # a或者f或者g的一个字符        
[0-4]         # 0-4范围内的一个字符
[a-f]         # a-f范围内的一个字符
[^m]          # 不是m的一个字符
\s            # 一个空格
\S            # 一个非空格
\d            # 一个数字，相当于[0-9]
\D            # 一个非数字，相当于[^0-9]
\w            # 数字或字母，相当于[0-9a-zA-Z]
\W            # 非数字非字母，相当于[^0-9a-zA-Z
```

​	正则表达式还可以用某些符号来表示某种形式的重复，这些符号紧跟在单个字符之后，就表示多个这样类似的字符：

```python
*          # 重复超过0次或更多次
+          # 重复1次或超过1次
?          # 重复0次或1次
{m}        # 重复m次。比如，a{4}相当于aaaa，再比如，[1-3]{2}相当于[1-3][1-3]
{m, n}     # 重复m到n次。比如说a{2, 5}表示a重复2到5次。小于m次的重复，或者大于n次的重复都不符合条件
```

​	下面是重复符号的例子：

| Regular Expressionn | Matched String | Unmatched String |
| ------------------- | -------------- | ---------------- |
| [0-9]{3, 5}         | '9678'         | '12'.  '1234567' |
| a?b                 | 'b' 'ab'       | 'cb'             |
| a+b                 | 'aaab'         | 'b'              |

​	位置相关的符号：

```python
^             # 字符串的起始位置
$             # 字符串的结尾位置
```

​	下面是位置符号的一些例子：

| Regular Expression | Matched String | Unmatched Strng |
| ------------------ | -------------- | --------------- |
| ^ab.*c$            | abeec          | cabeec          |

######5.3.3 进一步提取

​	想在搜索的同时，对结果进一步提炼。比如说，我们从下面一个字符串中提取信息：

```python
content = 'abcd_output_1994_abcd_1912_abcd'
```

​	如果我们把正则表达式写成：


```python
'output_4\d{4}'
```

​	那么用`search()`方法可以找到`"output_1994"`。但如果我们想进一步提取出`1994`本身，则可以在正则表达式上给目标加上括号：

```python
output_(\d{4})
```

​	括号`()`包围了一个小的正则表达式`\d{4}`。这个小的正则表达式能从结果中进一步筛选信息，即四位的阿拉伯数字。用括号`()`圈起来的正则表达式的一部分，称为群（group）。一个正则表达式中可以有多个群。

​	我们可以`group(number)`的方法来查询群。需要注意的是，`group(0)`是整个正则表达的搜索结果。`group(1)`是第一个群，以此类推：

```python
import re

m = re.search('output_(\d{4})', 'output_1986.txt')
print(m.group(1)) # return the value- 1986, composed of 4 digits
```

​	To name a group for a more convenient search by the `group` method

```python
import re

m = re.search('output_(?P<year>\d{4})', 'output_1986.txt') #(?P<year>...) used to name the group
print(m.group('year')) #print the output- 1986
```

​	上面的`(?P<year>…)`括住了一个群，并把它命名为`year`。用这种方式来产生群，就可以通过"year"这个键来提取结果。

####5.4 HTTP 网络协议

​	HTTP协议是最常见的一种网络协议。它的全名是the Hypertext Transfer Protocol，即超文本传输协议。HTTP协议能实现文件，特别是超文本文件的传输。

​	HTTP的工作方式类似于快餐点单：

1）请求（request）：顾客向服务员提出请求“来个鸡腿汉堡”。

2）回复（response）：服务员根据情况，回应顾客的请求。

​	根据情况不同，服务员的回应可能有很多种，比如：

- 服务员准备鸡腿汉堡，将鸡腿汉堡交给顾客。（一切OK）

- 服务员发现自己工作在甜品站。他让顾客前往正式柜台点单。（重新定向）

- 服务员告诉顾客鸡腿汉堡没有了。(无法找到)

  

  计算机发出请求会遵照下面的格式：

```
GET /index.html HTTP/1.1 
Host: www.example.com
```

​	在起始行中，有三段信息:

- GET方法。用于说明想要服务器执行的操作。
- /index.html 资源的路径。这里指向服务器上的index.html文件。
- HTTP/1.1协议的版本。HTTP第一个广泛使用的版本是1.0，当前版本为1.1。



​	早期的HTTP协议只有GET方法。遵从HTTP协议，服务器接收到GET请求后，会将特定资源传送给客户。这类似于客户点单，并获得汉堡的过程。GET方法之外，最常用的是**POST**方法。==它用于从客户端向服务器提交数据，请求的后面会附加上要提交的数据。服务器会对POST方法提交的数据进行一定的处理。==样例请求中有一行头信息。这个头信息的类型是Host，说明了想要访问的服务器的地址。

​	服务器在接收到请求之后，会根据程序，生成对应于该请求的回复，比如:

>HTTP/1.1.200 OK
>
>Content-type: text/plain
>
>content-length: 12
>
>
>Hello World!

​	回复的起始行包含三段信息：

- HTTP/1.1：协议版本
- 200：状态码（status code）
- OK：状态描述



​	OK是对状态码200的文字描述，它只是为了便于人类的阅读。电脑只关心三位的状态码（Status Code），即这里的200。200表示一切OK，资源正常返回。状态码代表了服务器回应的类型。其他常见的状态码还有很多，例如：

- 302，重新定向（Redirect）：我这里没有你想要的资源，但我知道另一个地方xxx有，你可以去那里找。
- 404，无法找到（Not Found）：我找不到你想要的资源，无能为力。



​	下一行Content-type说明了主体所包含的资源的类型。根据类型的不同，客户端可以启动不同的处理程序（比如显示图像文件、播放声音文件等）。下面是一些常见的资源：

- text/plain：普通文本
- text/html：HTML文本
- image/jpeg：jpeg图片
- image/gif：gif图片



​	Content-length说明了主体部分的长度，以字节（byte）为单位。

​	剩下的是回复的主体部分，包含了主要的文本数据。这里是普通类型的一段文本，即：

> Hello World!

​	*The above is a brief introduction about how HTTP works.*

###### 5.4.1 http.client Package

​	The below is a simple example.

```python
import http.clent

coon = http.client.HTTPConnection("www.example.com") # Host address
coon.request("GET", "/") #请求方法和返回路径
response = coon.getresponse() #请求恢复

print(response.status.reason) #回复的状态码和状态描述
content = respond.read() #回复的主体内容
print(content)
```

​	如果网络正常，那么上面的程序将访问网址，并获得对应位置的超文本文件。

###### 5.4.2 webscrapper

**Info of a webpage**

​	用爬虫做一件简单的事，即让它访问笔者的博客首页，提取出最近文章的发表日期和阅读量。

​	第一步是访问博客首页，获得首页的内容。博客的地址是www.cnblogs.com/vamei，主机地址是www.cnblogs.com，资源位置是/vamei。这个页面是一个超文本文件，所以我们用HTTP协议访问：

```python
import http.client

conn  = http.client.HTTPConnection('www.cnblogs.com') # Define the host address
coon.request("GET", '/vamei')  # the request method and the resource path
response = conn.getresponse()   # request a response

content = response.read()  #the content in a response
content = content.split('\r\n')  #split into a row
```

​	返回的content是一个列表，列表的每个元素是超文本的一行。

### 6. 对象

####6.1  一切皆对象

**运算符**

​	`list`是列表的类。如果用`dir(list)`调查`list`的属性，能看到一个属性是`__add__()`。从样式上看，`__add__()`是特殊方法。它特殊在哪呢？这个方法定义了“+”运算符对于`list`对象的意义，两个`list`的对象相加时，会进行合并列表的操作。结果为合并在一起的一个列表。

​	运算符，比如`+、-、>、<、and、or`等，都是通过特殊方法实现的

​	列表没有定义“-”运算符。我们可以创建一个列表的子类，通过增加`__sub__()`方法，来添加减法操作的定义，例如：

```python
class SuperList(list):
	def __sub__(self, b):
		a = self[:]
		b = self[:]
		while len(b) > 0:
			element_b = b.pop()
			if element_b in a:
				a.remove(element_b)
    return a
   
print(SuperList([1, 2, 3]) - SuperList([3, 4])) #打印[1, 2]
```

**元素引用**

下面是我们常见的表元素引用方式：

```python
li = [1, 2, 3, 4, 5, 6]
print(li[3])   #Print 4
```

​	上面的程序运行到`li[3]`的时候，Python发现并理解`[]`符号，然后调用`__getitem__()`方法。

```python
li = [1, 2, 3, 4, 5, 6]
print(li.__getitem(3)) #Print 4
```

​	Another Example:

```python
li = [1, 2, 3, 4, 5, 6]
li.__setitem(3,0)
print(li)  #Return [1, 2, 3, 0, 5, 6]

example_dict = {"a":1, "b":2}
example_dict.__delitem__("a")
print(example_dict)      # 返回{"b":2}
```

#### 6.2 内置函数的实现

###### 6.2.1 属性覆盖

​	为了深入理解属性覆盖，我们有必要理解Python的`__dict__`属性。当我们调用对象的属性时，这个属性可能有很多来源。除了来自对象属性和类属性，这个属性还可能是从祖先类那里继承来的。一个类或对象拥有的属性，会记录在`__dict__`中。这个`__dict__`是一个词典，键为属性名，对应的值为某个属性。Python在寻找对象的属性时，会按照继承关系依次寻找`__dict__`。

​	我们看下面的类和对象，`Chicken`类继承自`Bird`类，而`summer`为`Chicken`类的一个对象：

```python
Class Bird(object):
	feather = True
	
	def chirp(self):
		print("some sound")
		
Class Chicken(Bird):
  fly = False
  
  def __init__(self, age):
  	self.age = age
	
  def chirp(self):
    print("ji")
    	
summer = Chicken(2)
print("===> summer")
print(summer.__dict__) 
    
print("===> Chicken")
print(Chicken.__dict__) 
    
print("===> Bird")
print(Bird.__dict__)
    
print("===> object")
print(object.__dict__)
    
```

 	The below is the output.

```python
===> summer
{'age': 2}
===> Chicken
{'fly': False, 'chirp': <function chirp at 0x10c550410>, '__module__': '__main__', '__doc__': None, '__init__': <function __init__ at 0x10c550398>}
===>Bird
{'__module__': '__main__', 'chirp': <function chirp at 0x10c550320>, '__dict__': <attribute '__dict__' of 'Bird' objects>, 'feather': True, '__weakref__': <attribute '__weakref__' of 'Bird' objects>, '__doc__': None}
===>object
{'__setattr__': <slot wrapper '__setattr__' of 'object' objects>, '__reduce_ex__': <method '__reduce_ex__' of 'object' objects>, '__new__': <built-in method __new__ of type object at 0x10c14fa80>, '__reduce__': <method '__reduce__' of 'object' objects>, '__str__': <slot wrapper '__str__' of 'object' objects>, '__format__': <method '__format__' of 'object' objects>, '__getattribute__': <slot wrapper '__getattribute__' of 'object' objects>, '__class__': <attribute '__class__' of 'object' objects>, '__delattr__': <slot wrapper '__delattr__' of 'object' objects>, '__subclasshook__': <method '__subclasshook__' of 'object' objects>, '__repr__': <slot wrapper '__repr__' of 'object' objects>, '__hash__': <slot wrapper '__hash__' of 'object' objects>, '__sizeof__': <method '__sizeof__' of 'object' objects>, '__doc__': 'The most base type', '__init__': <slot wrapper '__init__' of 'object' objects>}
```

​	如果我们用内置函数`dir`来查看对象`summer`的属性的话，可以看到`summer`对象包含了全部四个部分。也就是说，对象的属性是分层管理的。对象`summer`能接触到的所有属性，分别存在`summer/Chicken/Bird/object`这四层。当我们需要调用某个属性的时候，Python会一层层向下遍历，直到找到那个属性。由于对象不需要重复存储其祖先类的属性，所以分层管理的机制可以节省存储空间。

​	某个属性可能在不同层被重复定义。Python在向下遍历的过程中，会选取先遇到的那一个。这正是属性覆盖的原理所在。在上面的输出中，我们能看到，`Chicken`和`Bird`都有`chirp()`方法。如果从`summer`调用`chirp()`方法，那么使用的将是和对象`summer`关系更近的`Chicken`的版本：

```python
summer.chirp()  #Print 'ji'
```

​	子类的属性比父类的同名属性有优先权，这正是属性覆盖的关键。

​	值得注意的是，上面都是*调用属性*的操作。如果进行*赋值*，那么Python就不会分层深入查找了。下面创建一个新的`Chicken`类的对象`autumn`，并通过`autumn`修改`feather`这一类属性：

```python
autumn = Chicken(3)
autumn.feather = False
print(summer.feather) #True
print(autumn.feather) #False
```

###### 6.2.2 特性

​	同一个对象的属性间存在依赖关系。某个属性改变，相关联的其他属性也会出现变化。这时，我们不能通过`__dict__`的静态词典方式来储存属性。Python提供了多种即时生成属性的方法。其中一种称为==**特性**（property）==。特性是特殊的属性。比如我们为`Chicken`类增加一个表示成年与否的特性`adult`。当对象的年龄（age）超过1时，adult为真，否则为假：

```python
class Bird(object):
	feather = True
	
class Chicken(Bird):
	fly = False
	def __init__(self, age):
		self.age = age
    
  def get_adult(self):
    if self.age > 0:
      return True
  	else:
      return False
  adult = property(get_adult) # property is built-in
  
summer = Chicken(2)
print(summer.adult) # return True

summer.age = 0.5
print(summer.adult) # return false
```

​	特性使用内置函数`property()`来创建。`property()`最多可以加载四个参数。前三个参数为函数，分别用于设置获取、修改和删除特性时，Python应该执行的操作。最后一个参数为特性的文档，可以为一个字符串，起说明作用。

​	A further example to introduce `property`:

```python
class num(object):
  def __init__(self, value):
    self.value = value
    
  def get_neg(self):
    return - self.value
  
  def set_neg(self, value):
    self.value = -value
    
  def del_neg(self):
    print("value also deleted")
    del self.value
    
   neg = property(get_neg, set_neg, del_neg, "I'm negative")
  
x = num(1.1) 
print(x.neg)              # 打印-1.1
x.neg = -22 
print(x.value)            # 打印22
print(num.neg.__doc__)    # 打印"I'm negative"
del x.neg                 # 打印"value also deleted"
```

​	上面的`num`为一个数字，而`neg`为一个特性，用来表示数字的负数。当一个数字确定的时候，它的负数总是确定的。而当我们修改一个数的负数时，它本身的值也应该变化。这两点由`get_neg()`和`set_neg()`来实现。而`del_neg()`表示的是，如果删除特性`neg`，那么应该执行的操作是删除属性`value`。`property()`的最后一个参数`（"I'm negative"）`为特性`neg`的说明文档。

###### 6.2.3 `__getattr__()`方法

​	除内置函数`property`外，还可用`__getattr__(self, name)`来查询即时生成的属性。当我们调用对象的一个属性时，如果通过`__dict__`机制无法找到该属性，那么Python就会调用对象的`__getattr__()`方法，==来即时生成该属性==，比如：

```python
class Bird(object):
  feather = True
  
class Chicken(Bird):
  fly = False
  
  def __init__(self, age):
    self.age = age
    
  def __getattr__(self, name):
    if name == "adult":
      if self.age > 1.0:
        return True
      else:
        return False
    else:
      raise AttributeError(name)
      
summer = Chicken(2)
print(summer.adult)

summer.age = 0.5
print(summer.adult)
print(summer.male)
```

​	需要注意的是，`__getattr__()`只能用于查询不在`__dict__`系统中的属性。`__setattr__(self, name, value)`和`__delattr__(self, name)`可用于修改和删除属性。它们的应用面更广，可用于任意属性。

​	即时生成属性还有其他的方式，比如使用`descriptor`类。

####6.3 动态类型 (Dynamic Typing)

​	Python的变量不需要声明。在赋值时，变量可以重新赋值为其他任意值,这就是动态类型的体现。The below is a simple example:

```python
a = 1
```

​	整数1是一个对象。对象的名字是"a"。但更精确地说，对象名其实是指向对象的一个引用。对象是存储在内存中的实体。但我们并不能直接接触到该对象。对象名是指向这一对象的引用（reference）。
​	
​	通过内置函数`id()`，我们能查看到引用指向的是哪个对象。==这个函数返回对象的编号==：


```python
a = 1
print(id(a))
print(id(1))
```
​	每次赋值时，我们让左侧的引用指向右侧的对象。引用能随时指向一个新的对象.

​	`is`用来判断两个引用是否指向同一个对象。

###### 6.3.1 可变与不可变对象

​	一个对象可以有多个引用，看下面一个例子：

```python
a = 5
print(id(5))

b = a
print(id(b))
print(id(a))

a = a + 2
print(id(a))
print(id(7))
print(id(b))
```

​	我们让a、b指向同一个整数对象5。其中，`b = a`的含义是让引用b指向引用a所指的那一个对象。我们接下来对对象进行操作，让a增加2，再赋值给a。可以看到，a指向了整数对象7，而b依然指向对象5。本质上，加法操作并没有改变对象5。相反，Python只是让a指向加法的结果—另一个对象7。

```python
list2 = [1, 2, 3]
list1 = list2

list1[0] = 10

print(list2) #output is [10, 2, 3]
```

​	在我们改变`list1`时，`list2`的内容发生了改变。引用之间似乎失去了独立性。其实这并不矛盾。因为`list1`、`list2`的指向没有发生变化，依然是同一个列表。==但列表是一个包含了多个引用的集合。每个元素是一个引用==，比如`list1[0]`、`list1[1]`等。每个引用又指向一个对象，	比如1、2、3 。而`list1[0] = 10`这一赋值操作，并不是改变`list1`的指向，而是对`list1[0]`。==也就是说，列表对象的一部分，即一个元素的指向发生了变化。因此，所有指向该列表对象的引用都受到影响。==

> 两个列表仍是指向同一个对象，即两个列表的值相等。但列表中的元素又分别指向不同的对象，其中一个列表发生变化会导致另一个列表发生相同的变化。词典同理，元组是不可变对象

​	因此，在操作列表时，如果通过元素引用改变了某个元素，那么列表对象自身会发生改变（in-place change）。列表这种自身能发生改变的对象，称为**可变对象**（Mutable Object）。==我们之前见过的词典也是可变数据对象。==但之前的整数、浮点数和字符串，则不能改变对象本身。==赋值最多只能改变引用的指向。==这种对象称为**不可变对象**（Immutable Object）。==元组包含多个元素，但这些元素完全不可以进行赋值，所以也是不可变数据对象。==

###### 6.3.3 从动态类型看函数的参数传递

​	函数的参数传递，本质上传递的是引用，比如：

```python
def f(x):
  print(id(x))
  x = 100
  print(id(x))
  
a = 1
print(id(a))
  
f(a)
print(id(a))
```

​	参数x是一个新的引用。当我们调用函数f时，a作为数据传递给函数，因此x会指向a所指的对象，也就是进行一次赋值操作。如果a是不可变对象，那么引用a和x之间相互独立，即对参数x的操作不会影响引用a。

​	如果传递的是可变对象，那么情况就发生了变化：

```python
def f(x):
  x[0] = 100
  print(x)
  
a = [1, 2, 3]
f(a)
print(a) #[100, 2, 3]
```

#### 6.4 内存管理

###### 6.4.1 引用管理

​	对象内存管理是基于对引用的管理。一个对象可以有多个引用，而每个对象中都存有指向该对象的引用总数，即**引用计数**（Reference Count)。 我们可以使用标准库中`sys`包中的`getrefcount()`，来查看某个对象的引用计数。需要注意的是，当使用某个引用作为参数，传递给`getrefcount()`时，参数实际上是创建了一个临时的引用。因此，`getrefcount()`所得到的结果，会比期望的多1：

```python
from sys import getrefcount

a = [1, 2, 3]
print(getrefcount(a))

b = a 
print(getrefcount)
```

​	由于上述原因，两个`getrefcount()`将返回2和3，而不是期望的1和2。

###### 6.4.2．对象引用对象

​	我们之前提到了一些可变对象，如列表和词典。它们都是数据容器对象，可以包含多个对象。实际上，容器对象中包含的并不是元素对象本身，而是指向各个元素对象的引用。我们也可以自定义一个对象，并引用其他对象：

```python
class from_obj(object):
  def __init__(self, to_obj):
    self.to_obj = to_obj
    
b = [1, 2, 3]
a = from_obj(b)

print(id(a.to_obj))
print(id(b))  #a和b指向编号相同
```

​	可以看到，a引用了对象b。对象引用对象，在Python中十分常见。比如在主程序使用a = 1，会把引用关系存入到一个词典中。该词典对象用于记录所有的全局引用。赋值`a=1`，实际上是让词典中一个键值为"a"的元素引用整数对象1。我们可以通过内置函数`globals()`来查看该词典。

​	当一个对象a被另一个对象b引用时，a的引用计数将增加1：

```python
from sys import getrefcount

a = [1, 2, 3]
print(getrefcount(a))

b = [a, a]
print(getrefcount(a))  # 由于对象b引用了两次a，因此a的引用计数增加了2。
```

​	容器对象的引用可能会构成很复杂的拓扑结构，如所示。

![](https://pic1.zhimg.com/80/v2-ac8e9f330ba3c580889b8450799e21c8_hd.jpg)

我们可以用`objgraph`包来绘制其引用关系，比如：

```python
x = [1,2,3]
y = [x, dict(key1=x)]
z = [y,(x, y)]

import objgraph
objgraph.show_refs([z], filename="erf_topo.png")  # 第二个参数说明了绘图文件的文件名
```

​	某个对象的引用计数可能减少。比如，可以使用`del`关键字删除某个引用：

```python
from sys import getrefcount

a = [1, 2, 3]
b = a
print(getrefcount(b))  # print 3
del a
print(getrefcount(b))  # print 2
```

​	`del`也可以用于删除容器中的元素，比如：

```python
a = [1,2,3]
del a[0]
print(a)
```

​	如果某个引用指向对象a，那么当这个引用被重新定向到某个其他对象b时，对象a的引用计数将减少

```python
from sys import getrefcount

a = [1, 2, 3]
b = a
print(getrefcount(b))

a = 1
print(getrefcount(b))
```

###### 6.4.3 垃圾回收

​	当Python中的对象越来越多时，它们将占据越来越大的内存.它会在适当的时候启动**垃圾回收**（Garbage Collection），将没用的对象清除。

​	原理上，当Python的某个对象的引用计数降为0，即没有任何引用指向该对象时，该对象就成为要被回收的垃圾了。比如某个新建对象，它被分配给某个引用，对象的引用计数变为1。如果引用被删除，对象的引用计数为0，那么该对象就可以被垃圾回收。比如下面的表：

```python
a = [1,2,3]
del a
```

​	垃圾回收时，Python不能进行其他的任务。频繁的垃圾回收将大大降低Python的工作效率。如果内存中的对象不多，就没有必要频繁启动垃圾回收。所以，Python只会在特定条件下，自动启动垃圾回收。当Python运行时，会记录其中分配对象（Object Allocation）和取消分配对象（Object Deallocation）的次数。当两者的差值高于某个阈值时，垃圾回收才会启动。

​	我们可以通过gc模块的`get_threshold()`方法，查看该阈值:

```python
import gc
print(gc.get_threshold())
```

​	返回`（700, 10, 10）`，后面的两个10是与分代回收相关的阈值，后文中会详细说明。700即垃圾回收启动的阈值。可以通过gc中的`set_threshold()`方法重新设置。当然，我们也可以手动启动垃圾回收，即使用`gc.collect()`。

​	除了上面的基础回收方式外，Python同时还采用了**分代**（Generation）回收的策略。这一策略的基本假设是，存活时间越久的对象，越不可能在后面的程序中变成垃圾。我们的程序往往会产生大量的对象，许多对象很快产生和消失，但也有一些对象长期被使用。出于信任和效率，对于这样一些“长寿”对象，我们相信它们还有用处，所以减少在垃圾回收中扫描它们的频率。

​	Python将所有的对象分为0、1、2三代。所有的新建对象都是0代对象。当某一代对象经历过垃圾回收，依然存活，那么它就被归入下一代对象。垃圾回收启动时，一定会扫描所有的0代对象。如果0代经过一定次数垃圾回收，那么就启动对0代和1代的扫描清理。当1代也经历了一定次数的垃圾回收后，就会启动对0、1、2代的扫描，即对所有对象进行扫描。

​	这两个次数即上面`get_threshold()`返回的`（700, 10, 10）`返回的两个10。也就是说，每10次0代垃圾回收，会配合1次1代的垃圾回收；而每10次1代的垃圾回收，才会有1次2代的垃圾回收。

​	同样可以用`set_threshold()`来调整次数，比如对2代对象进行更频繁的扫描。

```python
import gc 
gc.set_threshold(700, 10, 5)
```

## 7. **函数式编程**（Functional Programming）

#### 7.1 Python中的函数式

​	面向过程编程利用选择和循环结构，以及函数、模块等，对指令进行封装。面向对象实现了另一种形式的封装。包含有数据的对象的一系列方法。这些方法能造成对象的状态改变。作为第三种编程范式，函数式编程的本质也在于封装。

​	函数式编程以函数为中心进行代码封装。Python中的函数实际上是一些特殊的对象。这一条已经符合了函数式编程的一个重要方面：函数是第一级对象，能像普通对象一样使用。

​	函数式编程强调了函数的**纯粹性**（purity）。一个纯函数是没有副作用的（Side Effect），即这个函数的运行不会影响其他函数。纯函数像一个沙盒，把函数带来的效果控制在内部，从而不影响程序的其他部分。我们曾在函数内部改变外部列表的元素，其他调用该列表的函数也会看到该函数的作用效果。这样就造成了副作用。我们知道，造成这样效果的原因是我们使用了可变更的对象，如列表和词典。==因此，为了达到纯函数的标准，函数式编程要求其变量都是不可变更的。==

​	纯函数也方便进行并行化运算。在并行化编程时，我们经常要担心不同进程之间相互干扰的问题。当多个进程同时修改一个变量时，进程的先后顺序会影响最终结果。比如下面两个函数：

```python
from threading import Thread

x = 5

def double():
  global x
  x = x * 2
  
def plus_ten():
  global x
  x = x + 10
  
thread1 = Thread(target=double)
thread2 = Thread(target=plus_ten)
thread1.start()
thread2.start()
thread1.join()
thread2.join()

print(x)
```

​	上面的两个函数中使用了关键字`global`。`global`说明了`x`是一个全局变量。函数对全局变量的修改能被其他函数看到，因此有副作用。如果两个进程并行地执行两个函数，函数的执行顺序不确定，则结果可能是`double()`中的`x = x*2`先执行，最终结果为20；也有可能是`plus_ten()`中的`x = x + 10`先执行，最终结果为30。这被称为竞跑条件（Race Condition），是并行编程中需要极力避免的。

​	函数式编程的思路是自上而下的。它先提出一个大问题，在最高层用一个函数来解决这个大问题。在这个函数内部，再用其他函数来解决小问题。在这样递归式的分解下，直到问题得到解决。

###### 7.1.1 并行运算

​	并行运算，是指多条指令同时执行。一般来说，一台单处理器的计算机同一时间内只能执行一条指令。这种每次执行一条指令的工作方式称为串行运算。

​	大规模并行运算通常是在有多个主机组成的**集群**（Cluster）上进行的。主机之间可以借助高速的网络设备通信。一个集群的造价不菲。然而，我们可以在单机上通过多进程或多线程的方式，模拟多主机的并行处理。即使一台单机中，也往往存在着多个运行着的程序，即所谓的进程。

​	集群上的多进程分布在不同的主机，而单机的多进程存在于同一主机，并借着“分时复用”来实现并行。

​	下面是多进程编程的一个例子：

```python
import multiprocessing

def proc1():
  return 999999**9999

def proc2():
  return 888888**8888

p1 = multiprocessing.Process(target=proc1)
p2 = multiprocessing.Process(target=proc2)

p1.start()
p2.start()

p1.join()
p2.join()
```

​	上面程序用了两个进程。进程的工作包含在函数中，分别是函数`proc1()`和函数`proc2()`。方法`start()`用于启动进程，而`join()`方法用于在主程序中等待相应进程完成。

​	区分一下多进程和多线程。一个程序运行后，就成为一个进程。进程有自己的内存空间，用来存储自身的运行状态、数据和相关代码。一个进程一般不会直接读取其他进程的内存空间。进程运行过程中，可以完成程序描述的工作。但在一个进程内部，又可以有多个称为“线程”的任务，处理器可以在多个线程之间切换，从而形成并行的多线程处理。线程看起来和进程类似，但线程之间可以共享同一个进程的内存空间.

#### 7.2 被解放的函数

###### 7.2.1 函数作为参数和返回值

​	在函数式编程中，函数是第一级对象。所谓“第一级对象”，即函数能像普通对象一样使用。因此，函数的使用变得更加自由。对于“一切皆对象”的Python来说，这是自然而然的结果。既然如此，那么函数可以像一个普通对象一样，成为其他函数的参数。

​	比如下面的程序，函数就充当了参数：

```python
def square_sum(a,b):
  return a**2 + b**2

def cubic_sum(a,b):
  return a**3 + b**3

def argument_demo(f, a, b):
  return f(a,b)

print(argument_demo(square_sum, 3, 5))
print(argument_demo(cubic_sum, 3, 5))
```

​	很多语言都能把函数作为参数使用，例如C语言。在图形化界面编程时，这样一个作为参数的函数经常起到回调（Callback）的作用。当某个事件发生时，比如界面上的一个按钮被按下，回调函数就会被调用。下面是一个GUI回调的例子：

```python
import tkinter as tk

def callback():
  """
  callback function for button click
  """
  listbox.insert(tk.END, "Hello World!")
  
if __name__ == "__main__":
  master = tk.Tk()
  
  button = tk.Button(master, text="OK", command=callback)
  button.pack()
  
  listbox = tk.Listbox(master)
  listbox.pack()
  
  tk.mainloop()
```

###### 7.2.2 函数作为返回值

​	既然函数是一个对象，那么它就可以成为另一个函数的返回结果。

```python
def line_conf():
  def line(x):
    return 2*x+1
  return line  # return a function object

my_line = line_conf()
print(my_line(5)) # print 11
```

​	上面的代码可以成功运行。`line_conf()`的返回结果被赋给line对象。上面的代码将打印11。

###### 7.2.3 闭包

​	上面函数中，line()定义嵌套在另一个函数内部。如果函数的定义中引用了外部变量，会发生什么呢？

```python
def line_conf():
  b = 15
  def line(x):
    return 2*x+b
  
  b = 5
  return line # return the funciton object

if __name__ == "__main__":
  my_line = line_conf()
  print(my_line(5))  # print 15
```

​	`line()`定义的隶属程序块中引用了高层级的变量`b`。`b`的定义并不在`line()`的内部，而是一个外部对象。我们称`b`为`line()`的环境变量。尽管`b`位于`line()`定义的外部，但当`line`被函数`line_conf()`返回时，还是会带有 `b`的信息。

​	一个函数和它的环境变量合在一起，就构成了一个**闭包**（Closure）。上面程序中，b分别在`line()`定义的前后有两次不同的赋值。上面的代码将打印15，也就是说，`line()`参照的是值为5的b值。==因此，闭包中包含的是内部函数返回时的外部对象的值。==

​	在Python中，==所谓的闭包是一个包含有环境变量取值的函数对象。==环境变量取值被复制到函数对象的__closure__属性中。比如下面的代码：	

```python
def line_conf():
  b = 15
  
  def line(x):
    return 2*x+b
  b = 5
  return line # return function object

if __name__ == "__main__":
  my_line = line_conf()
  print(my_line.__closure__)
  print(my_line.__closure__[0].cell_contents) 
```

​	`my_line()`的`__closure__`属性中包含了一个元组。这个元组中的每个元素都是cell类型的对象。第一个cell包含的就是整数5，也就是我们返回闭包时的环境变量b的取值。

​	闭包可以提高代码的可复用性。我们看下面三个函数：

```python
def line(x):
  return x + 1

def line2(x):
  return 4*x + 1

def line3(x):
  return 5*x + 10

def line4(x):
  return -2*x - 6
```

​	如果把上面的程序改为闭包，那么代码就会简单很多：

```python
def line_conf(a,b):
  def line(x):
    return a*x + b
  return line

line1 = line_conf(1,1)
```

​	除了复用代码，闭包还能起到减少函数参数的作用：

```python
def curve_closure(a,b,c):
  def curve(x):
    return a*x**2 + b*x + c
  return curve

curve1 = curve_closure(1,2,1)
```

​	函数`curve()`是一个二次函数。它除了自变量*x*外，还有a、b、c三个参数。通过`curve_closure()`这个闭包，我们可以预设a、b、c三个参数的值。从而起到减参的效果。

#### 7.3 装饰函数

###### 7.3.1 装饰器（decorator）

​	**装饰器**（decorator）是一种高级Python语法。装饰器可以对一个函数、方法或者类进行加工。在Python中，我们有多种方法对函数和类进行加工。装饰器从操作上入手，为函数增加额外的指令。

​	我们先定义两个简单的数学函数，一个用来计算平方和，一个用来计算平方差：

```python
def square_sum(a,b):
  return a**2 + b**2

def square_diff(a,b):
  return a**2 - b**2

if __name__ == "__main__":
  print(square_sum(3,4))
  print(square_diff(3, 4) 
```

​	在拥有了基本的数学功能之后，我们可能想为函数增加其他的功能，比如打印输入。我们可以改写函数来实现这一点：

```python
# 装饰：打印输入

def square_sum(a, b):
  print("input:", a, b)
  return a**2 + b**2

def square_diff(a, b):
  print("input:", a, b)
  return a**2 - b**2

if __name__ == "__main__":
  print(square_sum(3, 4))
  print(square_diff(3, 4))
```

​	我们修改了函数的定义，为函数增加了功能。从代码中可以看到，这两个函数在功能上的拓展有很高的相似性，都是增加了`print("input", a, b)`这一打印功能。我们可以改用装饰器，定义功能拓展本身，再把装饰器用于两个函数：

```python
def decorator_demo(old_function):
  def new_function(a, b):
    print("input:", a, b)
    return old_function(a, b)
  return new_function

@decorator_demo
def square_sum(a, b):
  return a**2 + b**2 

@decorator_demo
def square_diff(a, b):
  return a**2 - b**2

if __name__ == "__main__":
  print(square_sum(3, 4))
  print(square_diff(3, 4))
```

​	装饰器可以用`def`的形式定义，如上面代码中的`decorator_demo()`。装饰器接收一个可调用对象作为输入参数，并返回一个新的可调用对象。装饰器新建了一个函数对象，也就是上面的`new_function()`。在`new_function()`中，我们增加了打印的功能，并通过调用`old_function(a, b)`来保留原有函数的功能。

​	定义好装饰器后，我们就可以通过`@`语法使用了。在函数`square_sum()`和`square_diff()`定义之前调用`@decorator_demo`，实际上是将`square_sum()`或`square_diff()`传递给了`decorator_demo()`，并将`decorator_demo()`返回的新的函数对象赋给原来的函数名`square_sum()`和`square_diff()`。所以，当我们调用`square_sum(3, 4)`的时候，实际上发生的是：

```python
square_sum = decorator(square_sum)
square_sum(3, 4)
```

​	Python中的变量名和对象是分离的。变量名其实是指向一个对象的引用。从本质上，装饰器起到的作用就是**名称绑定**（name binding），让同一个变量名指向一个新返回的函数对象，从而达到修改函数对象的目的。只不过，我们很少彻底地更改函数对象。在使用装饰器时，我们往往会在新函数内部调用旧的函数，以便保留旧函数的功能。这也是“装饰”名称的由来。

​	下面看一个更有实用功能的装饰器。我们可以利用time包来测量程序运行的时间。把测量程序运行时间的功能做成一个装饰器，将这个装饰器运用于其他函数，将显示函数的实际运行时间：

```python
import time

def decorator_demo(old_func):
  def new_func(*arg, **dict_arg):
    t1 = time.time()
    result = old_func(*arg, **dict_arg)
    t2 = time.time()
    print("time:", t2 - t1)
    return result
  return new_func  # call new_func to work
```

​	在`new_func()`中，除调用旧函数外，还前后额外调用了一次`time.time()`。由于`time.time()`返回挂钟时间，它们的差值反映了旧函数的运行时间。此外，我们通过打包参数的办法，可以在新函数和旧函数之间传递所有的参数。

###### 7.3.2 带参装饰器

​	在上面的装饰器调用中，比如`@decorator_demo`，该装饰器默认它后面的函数是唯一的参数。装饰器的语法允许我们调用`decorator`时，提供其他参数，比如`@decorator(a)`。这样，就为装饰器的编写和使用提供了更大的灵活性。

```python
# 带参装饰器
def pre_str(pre=""):
  def decorator(old_function):
    def new_function(a, b):
      print("input:", a, b)
      return old_function(a, b)
     return new_function
    
   return decorator

# 装饰square_sum()
@pre_str("^_^")
def square_sum(a, b):
  return a**2 + b**2

# 装饰square_diff()
@pre_str("T_T")
def square_diff(a, b):
  return a**2 - b**2

if __name__ == "__main__":
  print(square_sum(3, 4))
  print(square_diff(3, 4))  
  
```

​	上面的`pre_str`是一个带参装饰器。它实际上是对原有装饰器的一个函数封装，并返回一个装饰器。我们可以将它理解为一个含有环境参量的闭包。当我们使用`@pre_str("^_^")`调用的时候，Python能够发现这一层的封装，并把参数传递到装饰器的环境中。该调用相当于：

```python
square_sum = pre_str("^_^") (square_sum)
```

###### 7.3.3 装饰类

​	在上面的例子中，装饰器接收一个函数，并返回一个函数，从而起到加工函数的效果。装饰器还拓展到了类。一个装饰器可以接收一个类，并返回一个类，从而起到加工类的效果。

```python
def decorator_class(SomeClass):
    class NewClass(object):
        def __init__(self, age):
            self.total_display = 0
            self.wrapped = SomeClass(age)
        def display(self):
            self.total_display += 1
            print("total display:", self.total_display)
            self.wrapped.display()
    return  NewClass
  
@decorator_class
class Bird:
     def __init__(self, age):
         self.age = age
     def display(self):
         print("my age is:", self.age)
        
if __name__ == "__main__":
     eagle_lord = Bird(5)
     for i in range(3):
         eagle_lord.display()        
```

​	在装饰器`decorator_class`中，我们返回了一个新类`NewClass`。在新类的构造器中，我们用一个属性`self.wrapped`记录了原来类生成的对象，并附加了新的属性`total_display`，用于记录调用`display()`的次数。我们也同时更改了`display`方法。通过装饰，我们的`Bird`类可以显示调用`display()`的次数。

#### 7.4 高阶函数

###### 7.4.1  `lambda` & `map`

​	能接收其他函数作为参数的函数，被称为**高阶函数**（high-order function）。7.3节中介绍的装饰器，本质上就是高阶函数。本节我们讲介绍最具有代表性的高阶函数：`map()`、`filter()`和`reduce()`。

​	除了`def`，还可以用`lambda`语法来定义匿名函数:

```python
lambda_sum = lambda x,y: x + y
print(lambda_sum(3, 4))
```

​	这种用lambda来产生匿名函数的方式适用于简短函数的定义。

​	我们从`map()`开始介绍。函数map()是Python的内置函数。它的第一个参数就是一个函数对象。函数map()把这一个函数对象作用于多个元素, `map()`第二个参数是一个==可循环对象==。对于data_list的每个元素， lambda函数都会调用一次。那个元素会成为lambda函数的参数。换个角度说，map()把接收到的函数对象依次作用于每一个元素。最终，`map()`会返回一个迭代器:

```python
data_list = [1, 3, 5, 6]
result = map(lambda x: x + 3, data_list)
```

​	上面的代码相当于：

```python
def equivalent_generator(func, iter):
  for iterm in iter:
    yield func(iterm)
    
data_list = [1, 3, 5, 6]
result   = map(lambda x: x+3, data_list)
```

上面的`lambda`函数只有一个参数。这个函数也可以是一个多参数的函数。这个时候，`map()`的参数列表中就需要提供相应数目的可循环对象。


```python
def square_sum(x, y):
		return x**2 + y**2
		
data_list1 = [1, 3, 5, 7]
data_list2 = [2,4,6,8]
result= map(square_sum,data_list1, data_list2)
```

一定程度上，`map()`函数能替代循环的功能。在并行运算中，`map`是一个很重要的过程。通过`Map`这一步，一个大问题可以分拆成很多小问题，从而能交给不同的主机处理。例如在图像处理中，就可以把一张大图分拆成许多张小图。每张小图分配给一台主机处理。

**`filter`函数**

内置函数`filter()`的第一个参数也是一个函数对象。它也将这个函数对象作用于可循环对象的多个元素。如果函数对象返回的是`True`，则该次的元素被放到返回的迭代器中。也就是说，`filter()`通过调用函数来筛选数据。

下面是使用`filter()`函数的一个例子。作为参数的`larger100()`函数用于判断元素是否比100大：

```python
def larger100(a):
	if a > 100:
		return True
	else:
		return False
		
for item in filter(larger100,[10, 56, 101, 500]):
	print(item)
```	


`map()`函数和`filter()`函数的功能有相似的地方，都是把同一个函数应用于多个数据。

**`reduce`函数**

函数`reduce()`在标准库的`functools`包中, `reduce()`函数的第一个参数是函数，但reduce()对作为参数的函数对象有一个特殊要求，就是这个作为参数的函数必须能接收两个参数。`reduce()`可以把函数对象累进的作用于各个参数。这个功能可以用一个简单的例子来说明：

```python
from functools import reduce

data_list = [1,2,5,7,9]
result = reduce(lambda x,y: x+y, data_list)
print(result)  # Print 24
```


函数`reduce()`的第一个参数是求和的`sum()`函数，它接收两个参数`x`和`y`。在功能上，`reduce()`累进的运用传给它的二参函数。上一次运算的结果将作为下一次调用的第一个参数。首先，`reduce()`将用表中的前两个元素`1`和`2`做`sum()`函数的参数，得到`3`。该返回值`3`将作为`sum()`函数的第一个参数，而将表中的下一个元素`5`作为`sum()`函数的第二个参数，进行下一次求和得到`8`。`8`会成为新的参数，与下一个元素`7`求和。上面过程不断重复，直到列表中元素耗尽。函数`reduce()`将返回累进的运算结果，这里是一个单一的整数。上面的例子相当于`(((1+2)+5)+7)+9`，结果为`24`。


上面的`map()`、`reduce()`函数都是单线程的，所以运行效果和循环差不多。`但map()`、`reduce()`可以方便地移植到并行化的运行环境下。在并行运算中，Reduce运算紧接着Map运算。Map运算的结果分布在多个主机上，Reduce运算把结果收集起来。因此，谷歌用于并行运算的软件架构，就称为MapReduce


**并行处理**

下面的程序就是在多进程条件下使用了多线程的`map()`方法。这段程序多线程地下载同一个URL下的资源。程序用了第三方包`requests`来进行HTTP下载：


```python
import time
from multiprocessing import Pool

import requests

def decorator_timer(old_function):
	def new_function(*arg, **dict_arg):
		t1 = time.time()
		result = old_function(*arg, **dict_arg)
		t2 = time.time()
		print("time:", t2 - t1)
		
		return result
		
	return new_function
	
	
def visit_once(i, address="http://www.cnblogs.com"):
	r = requests.get(address)
	return r.status_code
	

@decorator_timer
def single_thread(f, counts):
	result = map(f, range(counts))
	return list(result)
	

@decorator_timer
def multiple_thread(f, counts, process_number=10):
	p = Pool(process_number)
	return p.map(f, range(counts))

if __name__ == "__main__":
	TOTAL = 	100
	print(single_thread(visit_once, TOTAL))
	print(multiple_thread(visit_once, TOTAL))
	
```	

####7.5 自上而下

######7.5.1．便捷表达式

函数式编程的思维是自上而下式的。Python中也有不少体现这一思维的语法，如==生成器表达式、列表解析和词典解析==。生成器表达式是构建生成器的便捷方法。考虑下面一个生成器：

```python
def gen():
	for i in range(4):
		yield i
```

等价的，上面程序可以写成生成器表达式（Generator Expression）：

```python
gen = (x for x in range(4))
```

我们再来看看生成一个列表的方法：

```python
l = []

for x in range(10):
	l.append(x**2)
```

上述代码生成了表l，但有更快的方式。列表解析（List Comprehension）是快速生成列表的方法。它的语法简单，很有实用价值。列表解析的语法和生成器表达式很像，只不过把小括号换成了中括号:	

```python
l = [x**2 for x in range(10)]
```

列表解析的语法很直观。我们直截了当地说明了想要的是元素的平方，然后再通过for来增加限定条件，即哪些元素的平方。除了for，列表解析中还可以使用if。比如下面一个更复杂的例子：

```python
xl = [1, 3, 5]
yl = [9, 12, 13]

l = [ x**2 for (x,y) in zip(xl, yl) if y > 10]
```

词典解析可用于快捷的生成词典。它的语法也与之前的类似：

```python
d = {k: v for k,v in enumerate("Vamei") if v not in "Vi"}

print(d) #{1: 'a', 2: 'm', 3: 'e'}
```


`enumerate()`:


>class enumerate(object)
   enumerate(iterable, start=0)
 
>Return an enumerate object.
 
>iterable
an object supporting iteration
 
>The enumerate object yields pairs containing a count (from start, which defaults to zero) and a value yielded by the iterable argument.
 
>enumerate is useful for obtaining an indexed list:
>(0, seq[0]), (1, seq[1]), (2, seq[2]), ...
 
>Methods defined here:
 
>  ` __getattribute__(self, name, /)`
       Return getattr(self, name).
 
 >  `__iter__(self, /)`
       Implement iter(self).
 
  > `__next__(self, /)`
       Implement next(self).
 
   >`__reduce__(...)`
       Return state information for pickling.
 


######7.5.2 懒惰求值
 
Python中的迭代器也很有函数式编程的意味。从功能上说，迭代器很多时候看起来就像一个列表。比如下面的迭代器和列表，效果上都一样：

```python
for i in (x**2 for x in range(10)):
	print(i)
	
for i in [x**2 for x in range(10)]:
	print(i)
```

迭代器的元素是实时计算出来的。==在使用该元素之前，元素并不会占据内存空间==。与之相对应，列表在建立时，就已经产生了各个元素的值，并保存在内存中。==迭代器的工作方式正是函数式编程中的懒惰求值（Lazy Evaluation）==。我们可以对迭代器进行各种各样的操作。但只有在需要时，迭代器才会计算出具体的值。	

懒惰求值可以最小化计算机要做的工作。比如下面的程序可以在Python 3中飞速运行完成：

```python
a = range(100000000)
result = map(lambda x: x**2, a)	
```

在Python 3中，上面程序可以迅速执行。因为`map`返回的是迭代器，所以会懒惰求值。更早之前的range调用返回的同样是迭代器，也是懒惰求值。除非通过某种方式调用迭代器中的元素，或者把迭代器转化成列表，运算过程才会开始。因此，在下面的程序中，如果把结果转化成列表，那么运算时间将大为增加。

```python
a = range(100000000)
result = map(lambda x: x**2, a)
result = list(result)						
```
比如下面的情况中，列表提前准备数据的方式，就浪费了很多运算资源：

```python
for i in (x**2 for x in range(100000000)):
	if i > 1000:
		break;
		
for i in [x**2 for x in range(100000000)]:
	if i > 1000:
		break;		
```
除了用`map()`、`filter()`等函数外，Python中的`itertools`包还提供了丰富的操作迭代器的工具。	

###### 7.5.3 `itertools`包
```python
#引入itertools
from itertools import *
```
这个包中提供了很多有用的生成器。下面两个生成器能返回无限循环的迭代器：

```python
count(5, 2)     #从5开始的整数迭代器，每次增加2，即5, 7, 9, 11, 13 ...
cycle("abc")    #重复序列的元素，既a, b, c, a, b, c ...
```
`repeat()`既可以返回一个不断重复的迭代器，也可以是有次数限制的重复：

```python
repeat(1.2)     #重复1.2，构成无穷迭代器，即1.2, 1.2, 1.2, ...
repeat(10, 5)   #重复10，共重复5次
```

我们还能组合旧的迭代器，来生成新的迭代器：

```python
chain([1, 2, 3], [4, 5, 7])    # 连接两个迭代器成为一个。1, 2, 3, 4, 5, 7
product("abc", [1, 2])         # 多个迭代器集合的笛卡儿积。相当于嵌套循环
```
所谓的笛卡儿积可以得出集合元素所有可能的组合方式：

```python
for m, n in product("abc", [1, 2]):
     print(m, n)     
```    
显示结果：

```python
a 1
a 2
b 1
b 2
c 1
c 2
```
itertools包中还提供了许多有用的高阶函数：

```python

