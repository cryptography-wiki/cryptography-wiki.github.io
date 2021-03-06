# 介绍

* 40年前，1976年11月，Whitfield Diffie和Martin Hellman提出了一篇名为“New Directions in Cryptography”（密码学的新方向）的文章，其中提出了一种方法使得没有事先约定的两人能够在公共通信通道上进行私人通信。这种方法首次展示了双方如何在不安全的通道上进行密钥共享而不需要长期准备，它便是今日我们熟知的“Diffie-Hellman密钥交换”。它打开了公钥密码，一个建立在数学难题上的领域，的大门。特别的，DH密钥交换的根本问题，在给定公钥的情况下计算共享密钥，被称为DH计算问题。

* 公钥密码的一个基本概念是单向（one-way）函数，这意味着我们能够轻易计算出对于给定输入的结果，但是反过来计算给定结果的输入项是非常困难的。这个困难性便是本篇论文的核心。是否有可能知道关于输入的任何信息呢（除了比如函数的定义域和值域此类信息）？特别是对于输入的二进制表示：是否有可能计算或预测出它的某些位呢？在公钥密码发展的前二十年中此类问题收到了大家的广泛研究。

* 在DH密钥交换中，保留的是DH密钥，但是并没有给出位计算的困难程度。直到1996年8月，这个历史问题在Bineh和Venkatesan的开创性工作中取得了第一份结果。通过使用格基规约算法显示出，DH密钥中的一个相对较小的最高有效位（most significant bits）和完整的密钥一样难以计算。

    虽然已经对结果进行了改进，但实际上这是原始DH密钥交换方案的唯一已知结果。DH密钥交换依赖于有限域上的乘法运算。DH密钥交换方案的变体给出了后续结果，其中DH密钥是有限域中的元素，但是这些结果依赖于和原始DH交换方案中一样的格方法，所以对于那些DH密钥还是拥有一样的结果。另一方面，除了二次有限域上的椭圆曲线点群之外，对于不同的群，该方案没有结果是已知的，

* 该问题除了理论上的问题外还有实际的一面，例如，当双方进行密钥交换时，共享密钥是一个群组元素，他们需要给出一定长度的二进制串。最自然实用的方法是使用这个元素的二进制串。为了保证给出的内容的安全等级，有必要证明计算选择的二进制串并不比计算整个密钥容易。它的结果被称为位安全结果。

* 本篇论文的主题是隐藏数问题，这将详细介绍有关DH密钥的位安全问题的第二个要点。Boneh和Venkatesan在上述工作中介绍了这个问题。它的普适性使得HNP对于其他方向的研究变得可行，它收到了多个不同领域的关注并且取得了多项应用。特别是，它与容错学习（Learning With Error）问题有关，虽然我们不讨论这种关系，但是本篇论文研究了这个问题的变体，对于一个应用程序，我们专注于证明利用DH密钥的二进制位计算出完整的密钥是困难的。

* 这项研究的数学原理是进行归约。将计算整个内容的问题简化成计算它的部分信息。这需要证明如果一个算法能够从给出的“隐藏”值从恢复部分信息，那么就可以恢复出完整的内容。这代表计算部分内容并不比计算全部内容要容易。为了证明它，需要用到大量的数学工具，例如上面提到的格构造以及格基归约。找到正确的构造和工具是进行简化问题的关键。但不幸的是，从现有结果来看，目前文献的相关内容相当有限。