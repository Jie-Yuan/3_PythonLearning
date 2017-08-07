> 类的方法与普通的函数只有一个特别的区别——它们必须有一个额外的第一个参数名称, 按照惯例它的名称是 self。

> 在类地内部，使用def关键字可以为类定义一个方法，与一般函数定义不同，类方法必须包含参数self,且为第一个参数:

## 类定义
```
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #类参数
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    #定义构造方法
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
```

## 实例化类
```
p = people('runoob',10,30)
p.speak()
```

## 单继承示例
```
class student(people):
    grade = ''
    def __init__(self,n,a,w,g):
        #调用父类的构函
        people.__init__(self,n,a,w)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
```

## 多重继承(继承多个类)
```
class speaker():
    topic = ''
    name = ''
    def __init__(self,n,t):
        self.name = n
        self.topic = t
    def speak(self):
        print("我叫 %s，我是一个演说家，我演讲的主题是 %s"%(self.name,self.topic))
        
class sample(speaker,student):
    a =''
    def __init__(self,n,a,w,g,t):
        student.__init__(self,n,a,w,g)
        speaker.__init__(self,n,t)
```
```
test = sample("Tim",25,80,4,"Python")
test.speak()   #方法名同，默认调用的是在括号中排前地父类的方法
```

## 装饰器
- @classmethod
> @classmethod意味着：当调用此方法时，我们将该类作为第一个参数传递，而不是该类的实例（正如我们通常使用的方法）。 这意味着您可以使用该方法中的类及其属性，而不是特定的实例。

- @staticmethod
> @staticmethod意味着：当调用此方法时，我们不会将类的实例传递给它（正如我们通常使用的方法）。 这意味着你可以在一个类中放置一个函数，但是你无法访问该类的实例（当你的方法不使用实例时这很实用）。

```
class A(object):  
    bar = 1  
    def foo(self):  
        print 'foo'  
 
    @staticmethod  
    def static_foo():  
        print 'static_foo'  
        print A.bar  
 
    @classmethod  
    def class_foo(cls):  
        print 'class_foo'  
        print cls.bar  
        cls().foo()
        
A.static_foo()  
A.class_foo()
```
```
static_foo
1

class_foo
1
foo
```