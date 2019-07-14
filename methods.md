## Python3 中类方法

**1. 静态方法**

用`@staticmethod`装饰的不带`self`参数的方法叫作静态方法。类的静态方法可以没有参数，可以直接使用类名调用. 不能和其他方法重名，不然会相互覆盖，后面定义的会覆盖前面的

**2. 普通方法**

默认有个self参数，且只能被对象调用

**3. 类方法**

默认有个 `cls` 参数，可以被类和对象调用，需要加上 `@classmethod` 装饰器。

**4. 私有方法**

两个下划线开头，只能在类内部访问

```python
class Classname:
	@staticmethod
	def fun():
		print('静态方法')

	@classmethod
	def a(cls):
		print('类方法')

	# 普通方法
	def b(self):
		print('普通方法')

Classname.fun()
Classname.a()

c = Classname()
c.fun()
c.a()
c.b()
```

```python
class People:

	#定义基本属性
	name = ''
	age = 0
	#定义私有属性外部无法直接访问
	__weight = 0
	def __init__(self, n, a, w):
		self.name = n
		self.age = a
		self.__weight = w

	def speak(self):
		print('%s says: I am %d.' % (self.name, self.age))

p = People('Philip', 10, 40)
p.speak()
#__weight无法直接访问
print(p.name, '--', p.age)
print(p.__weight)
```

**继承**

单继承:

```python
class Student(People):
	grade = ''
	def __init__(self, n, a, w, g):
		People.__init__(self, n, a, w)
		self.grade = g

	#覆写父类方法
	def speak():
		print('%s 说： 我 %d 岁了，我在读 %d 年纪。' % (self.n, self.a, self.g))

class Speak():
	topic = ''
	name = ''
	def __init__(self, n, t):
		self.name = n
		self.topic = t
	#普通方法，对象调用
	def speak(self):
		print("我叫 %s，我是一个演说家，我演讲的主题是 %s"%(self.name,self.topic))

	# 私有方法，self调用
	def __song(self):
        print('唱一首歌自己听',self);

    # 普通方法，对象调用
    def song(self):
        print('唱一首歌给你们听',self);

    #类方法，对象和类调用，不能和其他方法重名，不然会相互覆盖，后面定义的会覆盖前面的
    @classmethod
    def song(self):
        print('唱一首歌给类听:类方法',self)
```

**多继承:**

```python
class Sample(Speak, Student):
	a = ''
	def __init__(self, n, a, w, g, t):
		Student.__init__(self, n, a, w, g)
		Speak.__init__(self, n, t)

test = Sample('Song',24,56,7,'Python')
test.speak()
test.song()
Sample.song()
Sample.song()
test.song()

# test.__song() 无法访问私有方法
```

#### A further clarification

在 Python 中，方法分为三类实例方法、类方法、静态方法。三者区别看代码如下：

```python
class Test(object):
	def InstanceFun(self):
		print('InstanceFun')
		print(self)
		
	@classmethod
	def ClassFun(cls):
		print('ClassFun')
		print(cls)
		
	@staticmethod
	def Staticfun():
		print('StaticFun')

t = Test();　　　　　
t.InstanceFun();　　　# 输出InstanceFun，打印对象内存地址“<__main__.Test object at 0x0293DCF0>”
Test.ClassFun();     # 输出ClassFun，打印类位置 <class '__main__.Test'>
Test.StaticFun();    # 输出StaticFun
t.StaticFun();       # 输出StaticFun
t.ClassFun();        # 输出ClassFun，打印类位置 <class '__main__.Test'>
Test.InstanceFun();     # 错误，TypeError: unbound method instanceFun() must be called with Test instance as first argument
Test.InstanceFun(t);    # 输出InstanceFun，打印对象内存地址“<__main__.Test object at 0x0293DCF0>”
t.ClassFun(Test);       # 错误   classFun() takes exactly 1 argument (2 given)   
```

可以看到，在 Python 中，两种方法的主要区别在于参数。实例方法隐含的参数为类实例 self，而类方法隐含的参数为类本身 cls。
静态方法无隐含参数，主要为了类实例也可以直接调用静态方法。
所以逻辑上类方法应当只被类调用，实例方法实例调用，静态方法两者都能调用。主要区别在于参数传递上的区别，实例方法悄悄传递的是self引用作为参数，而类方法悄悄传递的是 cls 引用作为参数。
Python 实现了一定的灵活性使得类方法和静态方法，都能够被实例和类二者调用
