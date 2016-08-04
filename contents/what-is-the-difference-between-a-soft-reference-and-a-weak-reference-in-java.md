##soft reference 与 weak reference 的区别是什么

###问题
soft reference 与 weak reference 的区别是什么？


###回答
在 [From Understanding Weak References](http://weblogs.java.net/blog/enicholas/archive/2006/05/understanding_w.html) 中有写道：

> 
####Weak reference
>Weak reference, 正如其名，是一种无法强壮到可以将 object 保留在内存中的reference。 Weak reference 可以借助垃圾回收器来确定某块内存是否应当被回收。所以开发者可以从垃圾回收的细节中解放出来。
Weak reference 的用法如下：
首先创建WeakReference，
```java
WeakReference weakWidget = new WeakReference(widget);
```
在你之后的代码中，你可以用 ```weakWidget.get()``` 来得到 ```widget``` 的引用。因为Weak reference 并不足以使被引用 object 免予被回收，所以你可能会得到 ```null``` 。
...
>####Soft reference

Soft reference 与 weak reference 非常相似，不过Soft reference 在内存充沛的情况下可以将索引的对象一直保留在内存中。这个特性使它成为实现缓存基础。 Soft reference 使得垃圾回收器并不立即回收内存，而是综合内存使用率决定何时回收。

Peter Kessler 补充道：
使用了 -server 的JRE会为了提升性能而在内存富余的情况下尽量保留Soft reference 索引的对象, 而使用 -client 的JRE会更倾向于立刻清理Soft reference 的索引对象。

stackoverflow链接
http://stackoverflow.com/questions/299659/what-is-the-difference-between-a-soft-reference-and-a-weak-reference-in-java
