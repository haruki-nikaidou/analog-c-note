# 简单放大电路 & 静态工作点

依赖

* 三极管

因为三极管基极小电流的**小幅度**变化可以引起发射极的大电流的**大幅度**变化，所以，可以用三极管搭建信号放大电路。

以放大正弦波为例，因为三极管是单向导通的，所以需要首先把正弦波抬起来，使电流保持同向。然后，用一个直流电源产生大电流，让需要被放大的正弦波由基极输入控制直流电源产生的大电流，**使得原来电流变化幅度被放大**。

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption><p>简单放大电路的电路图</p></figcaption></figure>

不过，三极管的输入伏安特性中，电阻并非常数或者近似常数，这会造成一定程度上的失真，因为电压经过非恒定电阻的非线性变换后，不再是正弦波了。这个问题在这里可以暂时忽略。

注意，我上面加粗的字为幅度。尽管三极管确实能够放大直流电流，但是放大直流电流是没什么意义的。直流电流不带有信息，因为没有变化。

### 静态工作点

注意，我们抬高了正弦波的电流，这个操作是通过抬高电压实现的（毕竟正弦波电源是电压源）。如果我们抬的不够高，那么正弦波底下的一部分会被截止区削去。而且，被抬高的正弦波电压不能太高，否则会到达饱和区而被削去上面的部分。

所以说，我们需要控制抬高的幅度。为了实现正确的放大，需要让晶体管在不加入信号（等于信号位移为0）时，电压处于一个合适的位置。这个合适的位置,就是晶体管的**静态工作点**。

如果已知交流信号的最大波峰，显然，可以通过修改以下电路的电阻来找到合适的静态工作点。

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption><p>设置静态工作点的电路</p></figcaption></figure>

因为放大电路只有必要放大交流信号，所以常常会隔绝直流部分后再放大。一个常见的隔绝直流信号的操作是加个电容。加电容后接入放大电路的电路叫做阻容耦合放大电路。这种电路之后会提到。