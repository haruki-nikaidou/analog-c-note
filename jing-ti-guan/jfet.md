# JFET

依赖：

* 场效应晶体管

JFET的符号如下图所示

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption><p>JFET符号</p></figcaption></figure>

由于场效应晶体管的输入阻抗很高，而且$$i_G$$几乎为0，所以只能研究输入电压和输出电流之间的关系。

输入电压$$u_{GS}$$与输出电流$$i_D$$的关系称为转移特性，输出电压$$u_{DS}$$与输出电流$$i_D$$之间的关系称为输出特性。

JFET的特性主要有

* 夹断电压$$U_{GSOFF}$$
* 零偏漏极电流$$I_{DSS}$$
* 转移特性
* 输出伏安特性

### 夹断电压

JFET初始状态是导通的。夹断电压是使JFET从导通状态转变到截止状态的临界点。当越过这个临界点时，JFET关闭。

显然，对于N沟道JFET，栅极电压需要比源极更负是越过；对于P沟道JFET，栅极电压需要比源极更正是越过。

一般的N型JFET的夹断电压在-0.2V\~-10V之间。

### 零偏漏极电流

输入电压会降低JFET的导电性，所以，显然，当$$u_{GS}=0$$时，JFET提供最大电流。

对于N沟道JFET，施加负电压会降低导电性，那么施加正电压会如何？

事实上，此时确实会提供更大的电流，但此时JFET不再是高阻的了，所以禁止N沟道JFET$$u_{GS}>0$$。

### 转移特性

因为神奇的半导体特性，在正常工作状态（恒流区）下，转移特性是平方曲线。近似为

$$
i_D = I_{DSS} \left(1-\frac{u_{GS}}{U_{GSOFF}}\right)^2=\frac{I_{DSS}}{U_{GSOFF}^2}(u_{GS}-U_{GSOFF})^2=K(u_{GS}-U_{GSOFF})^2
$$

其中K是JFET的主要参数，单位为$$A/V^2$$，是影响转移特性曲线增长速率的参数。

### 输出伏安特性

给定一个非夹断的$$U_{GS}$$，输出伏安特性有2段

第一段：当$$u_{DS}$$从0开始增加时，电流$$i_D$$也不断增加，就像一个电阻一样。这个电阻取决于$$U_{GS}$$，且$$U_{GS}$$越靠近0，电阻越小。这一段是可变电阻区。

第二段：当$$u_{DS}$$足够大之后，电流$$i_D$$几乎不再增加。这一段是恒流区。

分界点电压定义为$$U_{DSdv}$$

如果把JFET用于放大电流，显然它应该工作在恒流区，这样才能获得最大的信号。但是，如果把JFET当作可变电阻使用，使用一个电压控制它的电阻，那么就应该工作在可变电阻区。

这个输出伏安特性的原理是很简单明了的。如果$$U_{GS}$$不变，在$$U_{DS}$$较小时，它显然是接近电阻的，而这个电阻的大小显然是和沟道宽度有关的。但当$$U_{DS}$$较大时，因为半导体内部就只有那些载流子，所以就算增大电压，电流也不会显著增大。

而且，不难理解：随着$$U_{GS}$$增加，分界点电压$$U_{DSdv}$$也在增加。实验验证，近似满足：

$$
U_{DSdv}=U_{GS}-U_{GSOFF}
$$

可以通过这个公式简单判断工作状态。
