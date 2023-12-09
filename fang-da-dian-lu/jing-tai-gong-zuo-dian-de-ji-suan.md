# 静态工作点的计算

依赖

* 简单放大电路&静态工作点
* 欧姆定律
* 基尔霍夫定律
* 戴维宁定理

默认条件下，为了取得最佳效果，静态工作点应该设置为三极管输出特性曲线的线性区域中心。这样可以确保在放大信号时，晶体管不会进入饱和或截止状态，从而减少失真。

也就是说，最佳静态工作点与输入信号无关。

那么，这个过程就变得很简单了。

### 大致步骤

首先，需要知道，$$U_{BEQ}=0.7V$$。

需要明确集电极电流$$I_C$$和输出电压$$U_{CE}$$，这两个参数决定了晶体管的工作状态。

主要步骤是：

1. 计算发射极电阻$$R_E$$（如果有）
2. 计算基极电阻$$R_B$$（可能是2个）
3. 计算集电极电阻$$R_C$$

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>两种阻容耦合放大电路</p></figcaption></figure>

需要知道的是，就算基极只有一个电阻，而且发射极没有电阻（也就是说，和前面的「[简单放大电路](../jing-ti-guan/jian-dan-fang-da-dian-lu-jing-tai-gong-zuo-dian.md)」一样，只有2个电阻），电路也能够正常工作，只不过会不稳定。

### 4电阻形

左边那个复杂的东西需要用到戴维宁等效

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>应用戴维宁等效</p></figcaption></figure>

所以，在基极处，电压为

$$
E_B=\frac{R_{B2}}{R_{B1}+R_{B2}}E_C
$$

以及

$$
R_B=R_{B1}//R_{B2}=\frac{R_{B1}R_{B2}}{R_{B1}+R_{B2}}
$$

利用基尔霍夫电压定律，有

$$
E_B=I_{BQ}R_B+U_{BEQ}+(1+\beta)I_{BQ}R_E
$$

解得

$$
I_{BQ}=\frac{E_B-U_{BEQ}}{R_B+(1+\beta)R_E}
$$

根据欧姆定律，有

$$
U_{EQ}=I_{EQ}R_E
$$

$$
U_{CQ}=E_C-I_{CQ}R_C
$$

于是，就能得到

$$
U_{CEQ}=U_{CQ}-U_{EQ}=E_C-I_{CQ}R_C-I_{EQ}R_E
$$

其中

$$
I_{CQ}=\beta I_{BQ}
$$

$$
I_{EQ}=(1+\beta)I_{BQ}
$$

展开$$U_{CEQ}$$，则有

$$
U_{CEQ}=E_C-\beta\frac{E_B-U_{BEQ}}{R_B+(1+\beta)R_E}R_C-(1+\beta)\frac{E_B-U_{BEQ}}{R_B+(1+\beta)R_E}R_E
$$

整理，有

$$
\begin{align} U_{CEQ}&=E_C-\beta\frac{E_B-U_{BEQ}}{R_B+(1+\beta)R_E}R_C-(1+\beta)\frac{E_B-U_{BEQ}}{R_B+(1+\beta)R_E}R_E\\ &=E_C-\left[\beta R_c+(1+\beta)R_E \right]\frac{E_B-U_{BEQ}}{R_B+(1+\beta)R_E}\\ &=E_C-(E_B-U_{BEQ})\frac{\beta R_c+(1+\beta)R_E }{R_B+(1+\beta)R_E} \\ &=E_C-(E_B-U_{BEQ})\frac{\beta R_C-R_B+R_B+(1+\beta)R_E }{R_B+(1+\beta)R_E} \\ &=E_C-(E_B-U_{BEQ})\left(1+\frac{\beta R_C-R_B}{R_B+(1+\beta)R_E} \right) \end{align}
$$

当$$\beta$$比较大时，就有

$$
\lim_{\beta \rightarrow \infty}U_{CEQ}=E_C-(E_B-U_{BEQ})\left(1+\frac{R_C}{R_E}\right)
$$

这样一来，静态工作点就不会因为三极管$$\beta$$参数变化而变化了。

三极管的$$\beta$$参数对温度是有些敏感的，这种电路就不会出现类似于冬天正常的静态工作点，夏天漂移了这种神奇情况。

而且，三极管的$$\beta$$参数是比较分散的，可能只有100，150，200的三极管，没有中间的三极管。分散的三极管参数可能使电阻很难配。
