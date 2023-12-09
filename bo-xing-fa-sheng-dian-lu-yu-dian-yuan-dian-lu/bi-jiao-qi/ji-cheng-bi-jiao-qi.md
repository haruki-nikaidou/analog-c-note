# 集成比较器

依赖：

* 简单比较器

把运放当比较器用是教科书上的操作，实际上用的都是集成比较器。

集成比较器没啥可介绍的，这里就介绍一个LM393

LM393管脚如图所示

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption><p>LM393 管脚图</p></figcaption></figure>

这里面封装了两个比较器，每一个比较器的结构是这样的

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>比较器的具体结构</p></figcaption></figure>

其实，就是两级放大电路，最后控制晶体管T5的通断。

T1a\~T3b是输入端的差动放大电路，T4是第二级的单入单出放大电路。最后经过放大之后，控制T5的通断。T5要么处于饱和状态，要么处于截止状态。

总之会用就行，集成放大器种类挺多的。
