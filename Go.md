### 进程、协程、线程的区别

	线程是进程内的一个执行单元，进程内至少有一个线程，进程有自己独立的地址空间。
	进程是资源分配和拥有的单位,线程是处理器调度的基本单位。
	协程是一种用户态的轻量级线程（比线程更小），由Go运行时管理。
	-----
	进程拥有自己的堆栈，进程之间不共享堆栈，由操作系统调度
	线程拥有自己的栈，共享堆，也是由操作系统调度
	协程共享堆，不共享栈，协程不被操作系统内核管理，而是由用户程序调度控制。是用户态协程，切换效率更加高。

### gmp原理

	Go调度器很轻量也很简单，足以撑起 goroutine 的调度工作，并且让 Go 具有了原生（强大）并发的能力。
	Go调度本质是把大量的 goroutine 分配到少量线程上去执行，并利用多核并行，实现更强大的并发。
	-----
	goroutine 协程	
	processor 处理器	
	thread 线程
	全局队列：存放等待执行的协程(G)
	处理器(P)的本地队列：当创建一个新的 协程(G) 之后优先加入本地队列，如果本地队列满了，会将本地队列的一般 协程(G) 移动到全局队列里面，
	本地队列保存 协程(G) 数量默认不超过256个
	处理器(P)的列表：在初始化的时候根据GOMAXPROCS来设置
	线程(M)：线程想运行任务就得获取 处理器(P)，从 处理器(P) 的本地队列获取 协程(G)，处理器(P) 队列为空时，线程(M) 也会尝试从全局队列
	拿一批 协程(G) 放到 处理器(P) 的本地队列，或从其他 处理器(P) 的本地队列偷一半放到自己 处理器(P) 的本地队列。线程(M) 运行 协程(G)，
	协程(G) 执行之后，线程(M) 会从 处理器(P) 获取下一个 协程(G)，不断重复下去。
[gmp原理](https://blog.csdn.net/bingshiwuyu/article/details/107783490)

### 高并发处理

	goroutine是Go并行设计的核心。goroutine说到底其实就是协程，但是它比线程更小，几十个goroutine可能体现在底层就是五六个线程，
	Go语言内部帮你实现了这些goroutine之间的内存共享。执行goroutine只需极少的栈内存(大概是4~5KB)，当然会根据相应的数据伸缩。
	也正因为如此，可同时运行成千上万个并发任务。goroutine比thread更易用、更高效、更轻便。
	协程更轻量，占用内存更小，这是它能做到高并发的前提。
	高并发的每一个请求都由一个单独的goroutine去执行。
[高并发处理](https://blog.csdn.net/feifeixiang2835/article/details/88261685)

### 大数据处理

[大数据处理](https://studygolang.com/topics/8546)

### go锁机制

[go锁机制](https://www.jianshu.com/p/d941af226b92)

### chan的实现原理

[chan的实现原理](http://c.biancheng.net/view/97.html)