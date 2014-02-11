#### python slots

```

    class A(object):

        __slots__ = ['a']


    class B(object):
        pass


    class C(B):
        __slots__ = ['a']


    c = C()
    c.b = 10 # no exception

    a = A()
    a.b =10 # exception

```

c.b 不会报出异常是因为，C 从B 继承了__dict__属性，因而可以动态添加属性，  
如果也严格限制了父类的__slots__那么C一样会异常

slots 的作用就是在严格限制对对象属性的添加，在对象实例很多的时候，可以节省内存

###### 相关链接

[python slots](http://stackoverflow.com/questions/472000/python-slots)

    The proper use of __slots__ is to save space in objects.  
    Instead of having a dynamic dict that allows adding attributes to objects at anytime,  
    there is a static structure which does not allow additions after creation.  
    This saves the overhead of one dict for every object that uses slots.  
    While this is sometimes a useful optimization,  
    it would be completely unnecessary if the Python interpreter was dynamic enough   
    so that it would only require the dict when there actually were additions to the object.

