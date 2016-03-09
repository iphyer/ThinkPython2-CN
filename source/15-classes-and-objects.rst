Classes and objects 类和对象
============================

At this point you know how to use functions to organize code and
built-in types to organize data. The next step is to learn
“object-oriented programming”, which uses programmer-defined types to
organize both code and data. Object-oriented programming is a big topic;
it will take a few chapters to get there.

目前你已经知道如何使用函数来组织你的代码同时用内置的类型来管理数据。下一步我们会学习“面向对象编程”，我们将使用
程序员定义的代码和数据。面向对象编程是一个很广泛的领域，这个题目会花费不少章节学习。

Code examples from this chapter are available from
http://thinkpython2.com/code/Point1.py; solutions to the exercises are
available from http://thinkpython2.com/code/Point1_soln.py.

本章的示例代码可以在\ http://thinkpython2.com/code/Point1.py\ 获取；
练习的答案可以在\ http://thinkpython2.com/code/Point1_soln.py\ 获取。

Programmer-defined types 程序员自定义类型
------------------------------------------------

We have used many of Python’s built-in types; now we are going to define
a new type. As an example, we will create a type called Point that
represents a point in two-dimensional space.

我们已经使用过了许多Python的内置类型； 现在我们要定义一个新类型。
作为例子，我们来创建一个叫做Point的类型，代表二维空间的一个点。

In mathematical notation, points are often written in parentheses with a
comma separating the coordinates. For example, :math:`(0,0)` represents
the origin, and :math:`(x,y)` represents the point :math:`x` units to
the right and :math:`y` units up from the origin.

在数学记法中，点通常被写成在两个小括号中用一个逗号分隔坐标的形式。
例如\ :math:`(0,0)`\ 代表原点，\ :math:`(x,y)`\ 代表原点向右x个单位，向上y个单位的点。

There are several ways we might represent points in Python:

在Python中，有几种表示点的方法：

-  We could store the coordinates separately in two variables, x and y.
   
   我们可以将坐标存储在两个独立的变量，x和y中。

-  We could store the coordinates as elements in a list or tuple.

   我们可以将坐标作为一个列表或者元组的元素存储。

-  We could create a new type to represent points as objects.

   我们可以创建一个新类型将点表示为对象。

Creating a new type is more complicated than the other options, but it
has advantages that will be apparent soon.

创建一个新类型比另外的方法（有一点）更复杂，
但是它的优势一会儿会显现出来。

A programmer-defined type is also called a **class**. A class definition
looks like this:

程序员自定义类型( A programmer-defined type )也被称作\ **对象（class）**\ 。 像这样定义一个对象：

::

    class Point:
        """Represents a point in 2-D space."""

The header indicates that the new class is called Point. The body is a
docstring that explains what the class is for. You can define variables
and methods inside a class definition, but we will get back to that
later.

第一行表明新的类的名称是点( Point )。主体部分是文档字符串，用来解释这个类的作用。
你可以在一个类的定义中定义变量和函数，稍后会讨论这个。

Defining a class named Point creates a **class object**.

定义一个叫做Point的类便创建了一个类对象。

::

    >>> Point
    <class '__main__.Point'>

Because Point is defined at the top level, its “full name” is
``__main__.Point``.

由于Point是定义在顶层的，所以它的“全名”是\ ``__main__.Point``\ 。

The class object is like a factory for creating objects. To create a
Point, you call Point as if it were a function.

类对象就像是一个用来创造对象的工厂。
要创建一个点，你可以像调用函数那样调用Point。

::

    >>> blank = Point()
    >>> blank
    <__main__.Point object at 0xb7e9d3ac>

The return value is a reference to a Point object, which we assign to
blank.

返回值是一个Point对象的引用，我们将它赋值给blank。


Creating a new object is called **instantiation**, and the object is an
**instance** of the class.

创建一个新对象的过程叫做\ **实例化（instantiation）**\ ，这个新对象叫做这个类的一个\ **实例（instance）**\ 。

When you print an instance, Python tells you what class it belongs to
and where it is stored in memory (the prefix 0x means that the following
number is in hexadecimal).

当你试图打印一个实例，Python会告诉你它属于哪个类，
以及它在内存中的存储地址（前缀0x代表紧跟后面的数是以十六进制表示的）。

Every object is an instance of some class, so “object” and “instance”
are interchangeable. But in this chapter I use “instance” to indicate
that I am talking about a programmer-defined type.

每一个对象都是某种类的实例，所以对象和实例可以互换。但是在这章我用实例来表示我在讨论程序员自定义类型。

Attributes 属性
---------------

You can assign values to an instance using dot notation:

你可以使用点标记法给一个实例进行赋值操作：

::

    >>> blank.x = 3.0
    >>> blank.y = 4.0

This syntax is similar to the syntax for selecting a variable from a
module, such as math.pi or string.whitespace. In this case, though, we
are assigning values to named elements of an object. These elements are
called **attributes**.

这个语法类似于从一个模块中使用变量的语法，比如math.pi和string.whitespace。
不过在这个例子中，我们是给一个类中已命名的元素赋值。
我们将这类元素称之为\ **属性（attributes）**\ 。

As a noun, “AT-trib-ute” is pronounced with emphasis on the first
syllable, as opposed to “a-TRIB-ute”, which is a verb.

作为名词的时候，“属性”的英文“AT-trib-ute”的重音在第一个音节上，
作为动词的时候，“a-TRIB-ute”重音在第二个音节上。

The following diagram shows the result of these assignments. A state
diagram that shows an object and its attributes is called an **object
diagram**; see Figure [fig.point].

下面这张图展示了这些赋值操作的结果。
这张状态图展示了一个对象和它的属性，我们称这张图为\ **对象图（object
diagram）**\ ； 见图[fig.point]。

.. figure:: figs/point.png
   :alt: Object diagram.

   Object diagram.

The variable blank refers to a Point object, which contains two
attributes. Each attribute refers to a floating-point number.

变量blank引用了一个Point类，这个类拥有了两个属性。
每个属性都引用了一个浮点数。

You can read the value of an attribute using the same syntax:

你可以使用相同的语法读出一个属性的值。

::

    >>> blank.y
    4.0
    >>> x = blank.x
    >>> x
    3.0

The expression blank.x means, “Go to the object blank refers to and get
the value of x.” In the example, we assign that value to a variable
named x. There is no conflict between the variable x and the attribute
x.

表达式blank.x的意思是，“前往blank所引用的对象并且将x的值拿出来”。
在这个例子中，我们将获取到的值赋值给了一个叫做x的变量。
变量x和属性x并不会冲突。

You can use dot notation as part of any expression. For example:

你可以在任何表达式中使用点标记法。例如：

::

    >>> '(%g, %g)' % (blank.x, blank.y)
    '(3.0, 4.0)'
    >>> distance = math.sqrt(blank.x**2 + blank.y**2)
    >>> distance
    5.0

You can pass an instance as an argument in the usual way. For example:

你可以像往常那样将一个实例作为参数传递。 例如：

::

    def print_point(p):
        print('(%g, %g)' % (p.x, p.y))

``print_point`` takes a point as an argument and displays it in
mathematical notation. To invoke it, you can pass blank as an argument:

``print_point``\ 将一个点作为参数，打印出其在数学中的表示方法。
调用它的时候，你可以将blank作为参数传递：

::

    >>> print_point(blank)
    (3.0, 4.0)

Inside the function, p is an alias for blank, so if the function
modifies p, blank changes.

在这个函数内部，p作为blank的别名，
所以，当函数修改了p，blank也会随之改变。

As an exercise, write a function called ``distance_between_points`` that
takes two Points as arguments and returns the distance between them.

编写一个叫做\ ``distance_between_points``\ 的函数，它将两个Point作为参数，
返回这两个点之间的距离。

Rectangles 矩形
---------------

Sometimes it is obvious what the attributes of an object should be, but
other times you have to make decisions. For example, imagine you are
designing a class to represent rectangles. What attributes would you use
to specify the location and size of a rectangle? You can ignore angle;
to keep things simple, assume that the rectangle is either vertical or
horizontal.

有时候，一个对象该拥有哪些属性是显而易见的，但有时候你需要好好考虑一番。
比如，你需要设计一个代表矩形的类。
为了描述一个矩形的位置和大小，你需要设计哪些属性呢？
角度是可以忽略的；为了使事情更容易，假设矩形是水平或者竖直的。

There are at least two possibilities:

至少有两种可能的设计：

-  You could specify one corner of the rectangle (or the center), the
   width, and the height.
   
   你可以指定矩形的一个角（或是中心），宽度，以及长度。

-  You could specify two opposing corners.

   你可以指定对角线上的两个角。

At this point it is hard to say whether either is better than the other,
so we’ll implement the first one, just as an example.

这个时候还不能够说明哪个方法优于哪个方法，为了举例，我们先来实现前者。

Here is the class definition:

这是类的定义：

::

    class Rectangle:
        """Represents a rectangle. 

        attributes: width, height, corner.
        """

The docstring lists the attributes: width and height are numbers; corner
is a Point object that specifies the lower-left corner.

文档字符串中列出了属性：width和height是数字；
corner是一个Point对象，代表了左下角的那个点。

To represent a rectangle, you have to instantiate a Rectangle object and
assign values to the attributes:

为了描述一个矩形，你需要实例化一个Rectangle对象，并且为它的属性赋值。

::

    box = Rectangle()
    box.width = 100.0
    box.height = 200.0
    box.corner = Point()
    box.corner.x = 0.0
    box.corner.y = 0.0

The expression box.corner.x means, “Go to the object box refers to and
select the attribute named corner; then go to that object and select the
attribute named x.”

表达式box.corner.x的意思是，
“前往box所引用的对象，找到叫做corner的属性；
然后前往corner所引用的对象，找到叫做x的属性。

.. figure:: figs/rectangle.pdf
   :alt: Object diagram.

   Object diagram.

Figure [fig.rectangle] shows the state of this object. An object that is
an attribute of another object is **embedded**.

图[fig.rectangle]展示了这个对象的状态。
一个对象作为另一个对象的属性叫做\ **嵌套（embedded）**\ 。

Instances as return values 实例作为返回值
-----------------------------------------

Functions can return instances. For example, ``find_center`` takes a
Rectangle as an argument and returns a Point that contains the
coordinates of the center of the Rectangle:

函数可以返回实例。例如，\ ``find_center``\ 将一个Rectangle作为参数
返回一个Point，代表了这个Rectangle的中心坐标：

::

    def find_center(rect):
        p = Point()
        p.x = rect.corner.x + rect.width/2
        p.y = rect.corner.y + rect.height/2
        return p

Here is an example that passes box as an argument and assigns the
resulting Point to center:

这个例子将box作为参数传递，将返回的Point赋值给center：

::

    >>> center = find_center(box)
    >>> print_point(center)
    (50, 100)

Objects are mutable 对象是可变的
--------------------------------

You can change the state of an object by making an assignment to one of
its attributes. For example, to change the size of a rectangle without
changing its position, you can modify the values of width and height:

你可以通过给一个对象的属性赋值来改变这个对象的状态。
例如，要改变一个矩形的大小而不改变它的位置，你可以修改width和height的值：

::

    box.width = box.width + 50
    box.height = box.height + 100

You can also write functions that modify objects. For example,
``grow_rectangle`` takes a Rectangle object and two numbers, dwidth and
dheight, and adds the numbers to the width and height of the rectangle:

你也可以编写函数来修改对象。
例如，\ ``grow_rectangle``\ 接受了一个Rectangle对象和两个数字，
dwidth和dheight，并将其加到矩形的宽度和高度上：

::

    def grow_rectangle(rect, dwidth, dheight):
        rect.width += dwidth
        rect.height += dheight

Here is an example that demonstrates the effect:

这个例子展示了调用后的结果：

::

    >>> box.width, box.height
    (150.0, 300.0)
    >>> grow_rectangle(box, 50, 100)
    >>> box.width, box.height
    (200.0, 400.0)

Inside the function, rect is an alias for box, so when the function
modifies rect, box changes.

在函数内部，rect是box的一个别名，
所以如果函数修改了rect，则box也随之改变。

As an exercise, write a function named ``move_rectangle`` that takes a
Rectangle and two numbers named dx and dy. It should change the location
of the rectangle by adding dx to the x coordinate of corner and adding
dy to the y coordinate of corner.

编写一个叫做\ ``move_rectangle``\ 的函数，接受一个Rectangle以及两个数字，
dx和dy。 它把corner的x坐标加上dx，把corner的y坐标加上dy，
从而改变矩形的位置。

Copying 复制
------------

Aliasing can make a program difficult to read because changes in one
place might have unexpected effects in another place. It is hard to keep
track of all the variables that might refer to a given object.

别名会造成程序的可读性降低，因为一个地方的变动可能会意外影响另一个地方。
跟踪所有引用同一个对象的变量是非常困难的。

Copying an object is often an alternative to aliasing. The copy module
contains a function called copy that can duplicate any object:

通常用复制对象的方法取代为对象起别名。
copy模块拥有一个叫做copy的函数，可以复制任何对象：

::

    >>> p1 = Point()
    >>> p1.x = 3.0
    >>> p1.y = 4.0

    >>> import copy
    >>> p2 = copy.copy(p1)

p1 and p2 contain the same data, but they are not the same Point.

p1和p2拥有相同的数据，但是它们并不是同一个Point对象。

::

    >>> print_point(p1)
    (3, 4)
    >>> print_point(p2)
    (3, 4)
    >>> p1 is p2
    False
    >>> p1 == p2
    False

The is operator indicates that p1 and p2 are not the same object, which
is what we expected. But you might have expected == to yield True
because these points contain the same data. In that case, you will be
disappointed to learn that for instances, the default behavior of the ==
operator is the same as the is operator; it checks object identity, not
object equivalence. That’s because for programmer-defined types, Python
doesn’t know what should be considered equivalent. At least, not yet.

正如我们预期的，is运算符显示了p1和p2并非同一个对象。
不过你可能会认为==运算的结果应该是True，因为这两个点的数据是相同的。
然而结果并不如你想象的那样，==运算符的默认行为和is运算符相同；
它检查对象的身份是否相同，而非对象的值是否相同。
因为Python并不知道什么样可以被认为相同。至少目前Python不知道。

If you use copy.copy to duplicate a Rectangle, you will find that it
copies the Rectangle object but not the embedded Point.

如果你使用copy.copy来复制一个矩形，
你会发现它仅仅复制了Rectangle对象，但没有复制嵌套的Point对象。

::

    >>> box2 = copy.copy(box)
    >>> box2 is box
    False
    >>> box2.corner is box.corner
    True

.. figure:: figs/rectangle2.pdf
   :alt: Object diagram.

   Object diagram.

Figure [fig.rectangle2] shows what the object diagram looks like. This
operation is called a **shallow copy** because it copies the object and
any references it contains, but not the embedded objects.

图[fig.rectangle2]展示了这个对象图。 这个操作叫做\ **浅复制（shallow
copy）**\ ，因为仅复制了对象以及其包含的引用， 但未复制嵌套的对象。

For most applications, this is not what you want. In this example,
invoking ``grow_rectangle`` on one of the Rectangles would not affect
the other, but invoking ``move_rectangle`` on either would affect both!
This behavior is confusing and error-prone.

对大多数应用来说，这并非是你想要的结果。
在这个例子中，对其中一个Rectangle对象调用\ ``grow_rectangle``\ 并不会影响到另外一个，
然而当对任何一个Rectangle对象调用\ ``move_rectangle``\ 的时候，两者都会被影响！
这个行为很容易带来疑惑和错误。

Fortunately, the copy module provides a method named deepcopy that
copies not only the object but also the objects it refers to, and the
objects *they* refer to, and so on. You will not be surprised to learn
that this operation is called a **deep copy**.

幸运的是，copy模块拥有一个叫做deepcopy的方法，
它不仅可以复制一个对象，还可以复制这个对象所引用的对象，
甚至可以复制\ *这个对象所引用的对象*\ 所引用的对象，等等。
你可以很显然地想到这个操作叫做\ **深复制（deep copy）**\ 。

::

    >>> box3 = copy.deepcopy(box)
    >>> box3 is box
    False
    >>> box3.corner is box.corner
    False

box3 and box are completely separate objects.

box3和box是完全互不相干的对象。

As an exercise, write a version of ``move_rectangle`` that creates and
returns a new Rectangle instead of modifying the old one.

编写另一个版本的\ ``move_rectangle``\ ，
它创建并返回一个新的Rectangle对象而非修改原先的那个。

Debugging 调试
--------------

When you start working with objects, you are likely to encounter some
new exceptions. If you try to access an attribute that doesn’t exist,
you get an AttributeError:

当你开始学习对象的时候，你可能会遇到一些新的异常。
如果你企图使用一个不存在的属性，你会得到Attributeerror的错误提示：

::

    >>> p = Point()
    >>> p.x = 3
    >>> p.y = 4
    >>> p.z
    AttributeError: Point instance has no attribute 'z'

If you are not sure what type an object is, you can ask:

如果你不确定一个对象的类型，你可以询问：

::

    >>> type(p)
    <class '__main__.Point'>

You can also use isinstance to check whether an object is an instance of
a class:

你也可以用 isinstance 来检查某个对象是不是某个类的实例。

::

    >>> isinstance(p, Point)
    True

If you are not sure whether an object has a particular attribute, you
can use the built-in function hasattr:

如果你不确定一个对象是否拥有某个属性， 你可以使用内置函数hasattr：

::

    >>> hasattr(p, 'x')
    True
    >>> hasattr(p, 'z')
    False

The first argument can be any object; the second argument is a *string*
that contains the name of the attribute.

第一个参数可以是任何对象；
第二个参数是一个\ *字符串*\ ，代表了某个属性的名字。


You can also use a try statement to see if the object has the attributes
you need:

你也可以使用 try　语句来检查某个对象是不是有你需要的属性:

::

    try:
        x = p.x
    except AttributeError:
        x = 0

This approach can make it easier to write functions that work with
different types; more on that topic is coming up in
Section [polymorphism].

这个方法可以让你更容易书写可以适应多种数据结构的函数。你可以在[polymorphism]节查看更多内容。

Glossary 术语表
---------------

class:
    A programmer-defined type. A class definition creates a new class
    object.
    
类:
    一种程序员自定义的类型。类定义创建了一个新的类对象。

class object:
    An object that contains information about a programmer-defined type.
    The class object can be used to create instances of the type.

类对象:
    包含程序员自定义类型的细节信息的对象。类对象可以被用于创建该类型的实例。

instance:
    An object that belongs to a class.
    
实例:
    属于某个类的对象。

instantiate:
    To create a new object.

实例化:
    创建新的对象。

attribute:
    One of the named values associated with an object.

属性:
    和某个对象相联系的变量值。
    
embedded object:
    An object that is stored as an attribute of another object.

嵌套对象:
    作为另一个对象的属性存储的对象。

shallow copy:
    To copy the contents of an object, including any references to
    embedded objects; implemented by the copy function in the copy
    module.

浅复制:
    在复制对象内容的时候，只包含嵌套对象的引用，是copy模块的copy函数的实现方式。
    
deep copy:
    To copy the contents of an object as well as any embedded objects,
    and any objects embedded in them, and so on; implemented by the
    deepcopy function in the copy module.

深复制:
    在复制对象内容的时候，既复制对象属性也复制所有嵌套对象和其中的所有嵌套对象，是copy模块deepcopy函数的实现方式。
    
object diagram:
    A diagram that shows objects, their attributes, and the values of
    the attributes.

对象图:
    展示对象及其属性和属性值的图。
    
Exercises 练习
--------------

习题 15-1
^^^^^^^^^^

Write a definition for a class named Circle with attributes center and
radius, where center is a Point object and radius is a number.

定义一个叫做 Circle　的类，类的属性是中心(center) 和 半径(radius),其中　中心(center) 是一个　Point 类而 半径(radius)　是一个数字。

Instantiate a Circle object that represents a circle with its center at
:math:`(150, 100)` and radius 75.

实例化一个中心(center)是:math:`(150, 100)`,半径(radius)是75的 Circle 对象。

习题 15-2
^^^^^^^^^^

Write a function named ``point_in_circle`` that takes a Circle and a
Point and returns True if the Point lies in or on the boundary of the
circle.

写一个名称为``point_in_circle``的函数，该函数可以接受一个圆类(Circle)对象和点类 (Point)对象，然后可以判断该点是否在圆内。在园内返回True。


习题 15-3
^^^^^^^^^^

Write a function named ``rect_in_circle`` that takes a Circle and a
Rectangle and returns True if the Rectangle lies entirely in or on the
boundary of the circle.

写一个名称为 ``rect_in_circle`` 的函数，该函数可以接受一个圆类(Circle)对象和矩形(Rectangle)对象，同时判断该矩形是否完全在圆内或者在圆上。

习题 15-3
^^^^^^^^^^

Write a function named ``rect_circle_overlap`` that takes a Circle and a
Rectangle and returns True if any of the corners of the Rectangle fall
inside the circle. Or as a more challenging version, return True if any
part of the Rectangle falls inside the circle.

写一个名称为``rect_circle_overlap``函数，该函数可以接受一个圆类对象和一个矩形类对象，如果矩形有任意一个角落在圆内则返回True。或者做一个更具有挑战性的版本，如果该矩形有任何部分落在圆内返回True。 


Solution: http://thinkpython2.com/code/Circle.py.

答案:http://thinkpython2.com/code/Circle.py.


习题 15-4
^^^^^^^^^^
Write a function called ``draw_rect`` that takes a Turtle object and a
Rectangle and uses the Turtle to draw the Rectangle. See
Chapter [turtlechap] for examples using Turtle objects.

写一个名称为``draw_rect``的函数，该函数接受一个Turtle对象和一个Rectangle对象，使用Turtle画出该矩形。参考[turtlechap]章的例子来学习如何使用 Turtle 对象。 

习题 15-5
^^^^^^^^^^

Write a function called ``draw_circle`` that takes a Turtle and a Circle
and draws the Circle.

写一个名称为　``draw_circle`` 的函数来接受一个　Turtle 对象和Circle对象同时画出该圆。

Solution: http://thinkpython2.com/code/draw.py.

答案:http://thinkpython2.com/code/draw.py.

