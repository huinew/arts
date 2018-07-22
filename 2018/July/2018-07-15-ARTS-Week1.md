### ##Algorithm
题目来源： leetcode

```
Remove Element(题目编号27)
难度: easy
```

> 题目描述:
> Given an array nums and a value val, remove all instances of that value in-place and return the new length.
> 
> Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.
> 
> The order of elements can be changed. It doesn't matter what you leave beyond the new length.
> 
> 示例: Given nums = [3,2,2,3], val = 3,
> 
> Your function should return length = 2, with the first two elements of nums being 2.
> 
> It doesn't matter what you leave beyond the returned length.


体会：本题其实很简单，但最后还是因为理解错误，以及对java里面一些函数用法不熟，导致走了好一段弯路。

错误思路：既然只是要将指定元素去掉，而且剩下的元素不要求顺序，只用往前排，所以可以采取对数组进行排序，将
指定元素都去掉后，将该元素后边的所有元素都前移；

然而binarySearch并不是想象中能返回数组中指定元素的初始位置，查了下binarySearch并不能处理有多个重复值时的情况，该思路失败。

然后又偷偷地看了下discussion。。看到了答案，按照这思路写的：


```
        int start = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != val) {
                nums[start++] = nums[i];
            }
        }
```

基本就是用两指针扫描法，start记录要被替换的下标，临时变量i记录当前扫描到的下标，如果没有碰到指定val，就将i所在下标的元素赋给start，这样就可以保证前面的元素就是答案想要的。


### ##Review
#### 文章：创建你自己的 Java 注解类
原文链接：https://www.codeproject.com/Articles/799268/Creating-Your-Own-Java-Annotations


感想：其实也是今天看到这篇文章，才具体了解了下注解这东西。查了下相关的资料，目前的理解是，如果你希望有一些要跟业务处理紧密相关的，而且也是较为通用的方法，不妨考虑写个自定义注解。这样可能会较好地提升代码的可读性。当然，注解这块的应用和原理还可以进一步梳理下大纲，以便更好理解。

## ##Tips
#### 刚看到优先队列，就应用上项目了

之前在杨老的Java核心36讲专栏里，看到了一个PriorityQueue 优先队列的容器，然后我把这个应用到项目中了。具体场景是，我是一个通用的云执行器，负责执行别人发来的事件，但这些事件有优先级，而且一个实例里面可能有多个事件，这些事件的执行顺序必须是先来后到的执行，根据上述需求，我就选择了这个数据结构。聊了下，身边Java玩得比我溜的小伙伴也还不知道这种优先队列的存在，不禁感叹一句：多知道一点，其实对平时工作的帮助就挺大的。

### ##Share
#### 为什么获得提拔的不是你？——读MackTalk一文有感

最近在池大大的微信公众号上看到了这篇文章，讲述了一个新入职的人员，希望获得有挑战的工作，结果因为承受不了节奏而迅速离职了；相比之下，另外一位实习生，她被分配到了客服这种脏活累活，结果根据客户反馈的结果，跟部门里的研发，运营团队进行沟通，推进了整个产品的优化，协助建立了客服运营体系，做得非常出色。

其实我们工作中有很多脏活累活的地方，我们如果可以把这些事情做得细致而且有效率，甚至从里面给公司创造价值，相信未来会有越来越多的机会来青睐我们。不过现实中，面对脏活累活的态度，我们可能很多人的第一反应是，把它弄完就得了，可能不会去想做优化。

从这文章里面得到的启示是，我们可以把事情做得再深一点。例如，老大让我负责招聘这边的事情，因为涉及到跟集团的其他子公司抢人，我们通常要去给人力较大压力，催促她们来把简历发给我们。我之前手动弄了个excel表来统计招聘信息，但感觉这样太累了，而且一旦事情多起来后，很容易忘掉统计。我打算写个程序，可以列出招聘简历和面试数的统计信息，这样有数据，hr也不会以人难招为借口来推脱责任，同时我们也可以根据这个信息来了解我们的招聘进度。

你有哪些不同的看法，欢迎跟我一起讨论！

