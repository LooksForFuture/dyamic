# dyamic
A python library for creating dynamic variables which are changed according to the sub-variables change

# Installation

You can easily download this library from github and use it.

# Usage
There are two methods for using this library

```python
#method 1
from dynamic import dynam

x = 3
n = 4
d1 = dynam(lambda: x+n-2)
d2 = dynam(lambda: x-n+3)
print(d1, d2)

#Dynamic variables also support operators
print(d1+d2, d1==d2) #and more

#You can also use dynamic variables in another dynamic variable
d3 = dynam(lambda: d1*d2-3)

#For getting value of the dynamic variable, you should call it
z = d3()

#method 2
from dynamic import dynamic

#This type of dynamic needs access to your variables, so you should create a subclass from it
class dynamic(dynamic):
    def eval(self):
        return eval(self.val)

x = 3
n = 4
d1 = dynamic('x+n-2')
d2 = dynamic('x-n+3')
print(d1, d2)

#Dynamic variables also support operators
print(d1+d2, d1==d2) #and more

#You can also use dynamic variables in another dynamic variable
d3 = dynamic('d1*d2-3')

#For getting value of the dynamic variable, you should call it
z = d3()


#Attention! Both dynamicvariable types are compatible with each other
d1 = dynam(lambda: x+3)
d2 = dynamic('n-3')
print(d1-d2)
```
