# 浮点运算：问题与局限

浮点数在计算机硬件中被表示为二进制数。比如，小数部分：

> 0.125

等价于1/10 + 2/100 + 5/1000，同样的二进制数：

> 0.001

等价于0/2 + 0/4 + 1/8。这两个小数具有相同的值，唯一的真正区别在于第一个是以十进制小数记数法写的，第二个是以二进制。

不幸的是，大多数小数不能精确地表示为二进制数。结果是，一般来说，您输入的浮点小数仅由实际存储在机器中的二进制浮点数来估算。

首先问题在一位小数的时候比较容易被理解，比如小数1/3。你可以近似计算它为：

> 0.3

或者，更好一点的，

> 0.33

再或者，更好一点的，

> 0.333

等等。无论你愿意写下多少位数，结果都将不会真正的等于1/3，但是，会越来越接近

同样的，无论你想用多少二进制位数，值为0.1小数不能被二进制数精确表示。在二进制中1/10是无限循环小数。

> 0.0001100110011001100110011001100110011001100110011...

最终停在有限的字节数上，你将会得到一个近似值。

在运行Python的典型机器上，Python浮标有53位精度，因此当您输入十进制数0.1时，内部存储的值是二进制分数。

> 0.00011001100110011001100110011001100110011001100110011010

接近但不完全等于1/10。

很容易忘记，存储值是原始小数的近似值，原因在于浮点数在解释器上显示的方式。Python只打印机器存储的二进制近似值所对应的小数值。如果Python要打印存储为0.1的二进制近似值的真正十进制值，则必须显示

```
>>> 0.1
0.1000000000000000055511151231257827021181583404541015625
```

这比大多数人有用的数字多，所以Python通过显示舍入值来保持数字的可管理性。

```
>>> 0.1
0.1
```

重要的是要认识到，在实际意义上，这是一种错觉：机器中的值不完全是1/10，只是简单地舍入真实机器值的显示。当你尝试用这些值做晕死时，这个事实就变得明显了。

```
>>> 0.1 + 0.2
0.30000000000000004
```

注意，这是二进制浮点的本质：这不是Python中的一个bug，它也不是代码中的一个bug。您将看到支持所有硬件的浮点运算的所有语言中的相同类型（虽然有些语言默认不显示差异，也可能在所有输出模式下显示差异）。

其他惊喜如下。例如，如果您试图将值2.675四舍五入转为两个小数点，就可以得到这个值。

```
>>> round(2.675, 2)
2.67
```

内置的`round()`函数的文档表示，它循环到最近的值，舍入零。因为小数部分2.675正好介于2.67和2.68之间，所以你可以预期这里的结果是（二进制近似）2.68。它不是，因为当十进制字符串‘2.675’被转换成二进制浮点数时，它又用二进制近似代替，它的精确值是

> 2.67499999999999982236431605997495353221893310546875

因为这个近似值稍微接近2.67，而不是2.68，它被舍入。

如果你处于一种你关心小数中间值的情况是什么样子的情况，你应该考虑使用十进制模块。顺便说一句，**“十进制”**模块还提供了一种很好的方式来“查看”存储在任何特定Python浮标中的确切值。

```
>>> from decimal import Decimal
>>> Decimal(2.675)
Decimal('2.67499999999999982236431605997495353221893310546875')
```

另一个结果是，由于0.1不完全是1/10，求和的十个值的0.1可能不能精确地得到1，也可以是：

```
>>> sum = 0.0
>>> for i in range(10):
...     sum += 0.1
...
>>> sum
0.9999999999999999
```

二进制浮点运算有很多类似的惊喜。“0.1”的问题在下面的“表示错误”部分有详细解释。请参阅[The Perils of Floating Point](http://www.lahey.com/float.htm)更详细的说明其他常见的惊喜。

正如最后所说的，“没有简单的答案。”不过，不要过分警惕浮点！Python浮点运算中的错误是从浮点硬件继承的，并且在大多数机器中，每个操作的顺序不超过1×2×53。这对于大多数任务来说都是足够的，但是您需要记住它不是十进制算术，并且每个浮点运算都会受到新的舍入误差的影响。

虽然误差问题确实存在，但对于大多数偶然使用的浮点运算，如果只需将最终结果的显示与预期的十进制数字相比较，就会看到最终的结果。为了控制浮点如何显示，请看`str.format()`方法中的格式说明符[Format String Syntax](https://docs.python.org/2/library/string.html#formatstrings).

### 1. 表示误差

本节详细解释了“0.1”示例，并展示了如何自己对这种情况进行精确分析。假定基本熟悉二进制浮点表示。

表示误差是指一些（大多数，实际上）小数部分不能精确地表示为二进制小数。这就是为什么Python的主要原因（或Perl，C，C++，java，FORTRAN，和其他语言）通常不会显示出你期望的十进制数值：

```
>>> 0.1 + 0.2
0.30000000000000004
```

为什么会这样？1/10和2/10不能精确地表示为二进制分数。几乎所有的机器今天（2010年7月）都使用IEEE-754浮点运算，几乎所有的平台都将Python浮标映射到IEEE-754“双精度”。754个加法器包含53位精度，因此在输入端，计算机力求将0.1转换成J/2**n形式的最接近的部分，其中J是一个正好包含53位的整数。重写

> 1 / 10 ~= J / (2**N)

as

> J ~= 2**N / 10

并且回调J正好有53位（IS>＝2 ** 52但＜2×*53），n的最佳值是56：

```
>>> 2**52
4503599627370496
>>> 2**53
9007199254740992
>>> 2**56/10
7205759403792793
```

也就是说，56是n的唯一值，j正好等于53位。J的最佳可能值是商舍入：

```
>>> q, r = divmod(2**56, 10)
>>> r
6
```

由于余数大于10的一半，最好的近似是通过舍入得到的：

```
>>> q+1
7205759403792794
```

因此，1/10在754倍精度的情况下，最好的近似值是2**56，或

> 7205759403792794 / 72057594037927936

注意，因为我们四舍五入，这实际上有点大于1/10；如果我们没有舍入，商会比1/10稍微小一点。但绝对不会精确等于1/10！

所以计算机从来没有“看到”1/10：它所看到的是上面给出的精确分数，它可以得到最好的754倍近似：、

```
>>> 0.1 * 2**56
7205759403792794.0
```

如果我们将该小数乘以10 ** 30，我们可以看到它的30个最重要的十进制数字的（截断）值：

```
>>> 7205759403792794 * 10**30 // 2**56
100000000000000005551115123125L
```

这意味着存储在计算机中的确切数字大约等于十进制值0.100000000000000005551115123125。在Python 2.7和Python 3.1之前的版本中，Python将这个值舍入到17个有效数字，给出了“0.10000000000000001”。在当前版本中，Python显示一个基于最短小数部分的值，该值精确地返回到真正的二进制值，从而简单地出现在“0.1”中。