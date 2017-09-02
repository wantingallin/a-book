# 深度学习遇上pytorch课程笔记第一节

这一章节主要从两大部分进行阐述，第一部分主要阐述了深度学习的进展，第二部分主要阐述了Pytorch的基本概念及线性回归实操。


## 第一部分
深度学习进展
1. 什么是深度学习？
1. 深度学习与人工智能
1. 深度学习历史轨迹
1. 影响深度学习的因素是什么？
1. 深度学习的本质
1. 深度学习受欢迎的原因？


## 第二部分
Pytorch的基本原理及入门
1. Pytorch特点
1. Pytorch的基本语法
1. 第一个Pytorch实例：预测房价


### 一、深度学习进展
#### 1. 什么是深度学习？
什么是深度学习呢？现在普遍的认知是深层的人工神经网络，如下图所示。
![alt]()
这一观点并没有错误，但是却并不全面。我们还必须从它的内涵与外延两个方面来深入理解它。

#### 2. 深度学习与人工智能
从外延的角度来说，深度学习属于一种特殊的人工智能技术。它与人工智能以及机器学习的关系如下图所示：
![alt]()

首先，人工智能是一门如何创造出会思考机器的技术学科，它的覆盖面非常广，包括自动推理、联想、学习等。机器学习则是人工智能的一个重要分支，它在20世纪的80、90年代才逐渐发展起来，主要研究如何让计算机具有能够自我学习的能力。事实上，机器学习的方式有很多种，包括决策树算法、SVM（支持向量机）、遗传算法（Genetic Algorithm）等等。而近些年来，基于人工神经网络的机器学习算法开始盛行起来，渐渐地有替代其它机器学习算法的态势。

为什么会这样的？原因就在于神经网络中有一种叫做反向传播算法的关键性技术。该算法的好处是它可以精确地调整系统出错误的部件，这就使得人工神经网络会在诸多机器学习算法种胜出。所以说，反向传播算法是神经网络中的最重要的技术。

目前的深度学习几乎都是基于人工神经网络来做的，它无非就是一种具有深层次结构的神经网络。这种方法在近些年有了突飞猛进的发展，不断突破了理论应用的极限。

那么，相比较一般的机器学习技术来说，深度学习在应用层面有什么特色呢？最大的特色就在于它可以处理各种非结构化的数据。这里的非结构化数据特指：图像、视频、文本、音频等等。而一般的机器学习更多的是在和结构化的数据，也就是可以用关系型数据库进行存储、管理、访问的数据。

![alt]()
通过对比深度学习和人工智能以及一般的机器学习技术之间的区别和联系使得我们可以从横向、多学科的角度理解了深度学习。我们还需要从纵向，也就是历史渊源的角度进一步了解深度学习。

### 3.深度学习历史轨迹

#### 3.1 从感知机到人工神经网络

从历史的传承角度来说，深度学习是和人工神经网络的发展一脉相承的，我们可以把从第一个人工神经元被设计出来以来的所有大事件绘制成下图：

![alt]()

人工神经网络的历史最早可以追溯到1943年，此时，第一个人工神经元被发明了出来，这就是著名的McCulloch&Pitts模型。然而他们的工作没有得到大多数人的认识，所以对于神经网络的研究也进展缓慢。直到1957年，感知机模型（Perceptron）被提出才点燃了人们对于人工神经网络的探索激情。看起来，人工神经网络的确是一个能够解决一定问题的有用机器。然而，好景不长，1969年马文明斯基和合作者Papert联合写了一本书，指出了人工神经网络的弊端是它的分类能力极其有限，它甚至连极其简单的XOR问题（一种最基础的二进制运算）都无法解出来，于是人工神经网络从此被打入了冷宫。

历史的进程需要出现一个拯救者来挽回人工神经网络学派的发展路线。这名拯救者终于出现了，他就是大名鼎鼎的G. Hinton。1986年Hinton与合作者大力发展了人工神经网络的反向传播算法，这就使得我们可以构造超过两层的人工神经网络，并且可以有效地进行学习与训练。加深了的神经网络可以很轻松地解决XOR问题，从而逃避了马文明斯基对于人工神经网络的诅咒。多层人工神经网络配备上反向传播算法的确能够帮助人们解决大量的机器学习问题，尽管当时的精度还有待进一步提高，但是人工神经网络在80年代末到90年代初的时候曾经风靡一时。

神经网络学派的发展在经历过80年代的辉煌与爆发之后渐渐陷入颓势。一方面，神经网络能够解决的分类问题精度有限；另一方面，人工神经网络一直是一个黑箱，没有人能够理解它究竟是如何学习、如何解决问题的。于是，到了20世纪90年代末的时候，统计学习理论在两位俄罗斯裔数学家手里发展了起来，它不仅奠定了解决机器学习、模式识别问题的数学基础，而且还创造出了支持向量机（Supporing Vector Machine，简称SVM）这种极其实用而简洁的工具。于是，SVM成为了机器学习的代名词，神经网络被再次打入冷宫。

于是，神经网络学派的颓势需要再次被拯救，而第二次扛起大旗的人仍然还是那位Geoffrey Hinton。2006年的时候，Hinton在Science上发表了一篇文章，提出了深度神经网络模型（Deep Neural Network，简称DNN），并指出如果我们能够将神经网络的层数加深，并且如果们精心设计训练网络的方式的话，那么这样深层次的神经网络就会具有超强的表达能力和学习能力。

虽然很多人都猜想深度的（超过三层以上）神经网络也许能够大大提高分类的准确度，但是却没有人真正地验证这个结论。究其原因在于当时的硬件水平和数据量都远远无法与深度的神经网络相匹配，再加上深度网络需要特殊的训练技巧，这就阻碍了人们往深度方向的探索。而Hinton却始终坚持着深度的梦想。终于在2006年左右提出了深度神经网络的概念，并向世人证明了“深度”的作用。

#### 3.2 深度学习时代
Hinton有关深度神经网络的研究激励了大量的学者朝向深度的网络进行探索。2009年，在华裔女科学家李飞飞的不懈努力和坚持之下，ImageNet这样一个包含了一百多万张图像的大型数据库建设成功，并开始举办每年一次的图像识别大赛。这为深度神经网络在计算机视觉和图像处理领域的发展提供了巨大的空间。从AlexNet到Google Net，人们不断地增加网络的深度，识别准确率直线提升。深度神经网络的模式识别能力甚至可以超过人类的水平。深度学习开始在学术圈流行起来。

让深度学习的进展引起工业界的注意还要等到2011年。彼时，GoogleX实验室的Jeff Dean和吴恩达等人采用深度学习技术，让Google大脑深度神经网络观看了从youTube上提取出来的三十万张图片，并让机器自动进行精炼。结果，Google大脑自己学出了一张“猫”脸。这张猫脸具有鲜明的“机器烙印”。第二天，这张猫脸出现在了各大网站的头条位置，深度学习开始引起工业界的关注。

看到了深度学习技术的发展前景，以Google、Facebook为代表的大公司开始疯狂并购人工智能、深度学习初创企业。这种举动不仅引发了AI人才的全球争夺战，也促使更多的人、更多的创业公司投入到人工智能大潮之中。据不完全统计，每隔11个小时全球就有一家人工智能创业公司诞生。

深度学习技术在语音和图像领域的大获成功激发了人们将该技术扩展到自然语言处理领域。首先，2013年Google的Miklov提出了Word2Vec技术，可以非常快捷有效地计算单词的向量表示，这为大规模地使用人工神经网络技术处理人类语言奠定了重要的基础。

2014年，Google开始尝试利用深度的循环神经网络来处理各种自然语言任务，这包括机器翻译、自动对话、情绪识别、阅读理解等。尽管目前为止，深度学习技术在自然语言类任务上面的表现还无法与图像类任务相媲美，但也经历着突飞猛进的发展。2016年，Google的机器翻译技术获得重大突破。采用了最先进的深度RNN和注意力机制的机器翻译水平在多种语言上已经可以接近人类的水平。

除了在语音、图像和自然语言处理等传统任务上的发展以外，科学家们还在不断地拓宽深度学习的应用范围。与强化学习这一古老的机器学习技术的联姻使得深度学习可以在计算机游戏、博弈等领域获得重大突破。2015年，被Google收购的DeepMind团队就研发了一种“通用人工智能”，它可以像人类一样进行自我学习打三百多款计算机游戏，并在某些游戏上超越人类。

2016年3月，DeepMind又在博弈领域取得重大突破。AlphaGo以4:1的大比分战胜人类围棋冠军，从而让计算机围棋这个领域的进展提前了至少十年。AlphaGo的成功不仅仅标志着以深度学习技术为支撑的新一代人工智能技术的大获全胜，更暗示着我们人工智能的全新时代已经到来。

### 4 影响深度学习的因素是什么？

我们都知道，影响深度学习的主要因素有三个要点，分别是大数据、GPU和深层网络。在这里，我们不对大数据和GPU进行过多的讨论，而只对深度网络进行讨论。

影响深层网络因素又可以分为三个方面，分别是超参数、架构和训练方法。所谓的超参数就是指我们人为设定的无法在机器训练的阶段自动调整的那些参数，包括诸如神经元数量、网络的层次、学习率等。

深度网络的架构则是整个网络体系的构建方式，它是影响深度神经网络的最重要的因素。 


#### 4.1架构是如何影响深层网络的呢？ 
目前最主流的两大深度学习网络架构分别是卷积神经网络（Convolutional Neural Network，简称CNN）和循环神经网络（Recurrent Neural Network，简称RNN）。CNN这种架构如下图所示：


其中每一个立方体都是一系列规则排布的人工神经元集合。每个神经元到上一层次的链接被称为卷积核，它们都是一种局域的（3*3或者2*2）小窗口。

CNN的这种特殊架构主要应用于处理图像数据，而且对于图像的平移，旋转等空间变换具有一种不变性。即网络的特殊架构设计可以使得原始的图像即使在经历过平移、旋转等变换之后仍然具有很高的识别准确性。

与此类似，循环神经网络也有着特殊的结构，如下图：



我们看到隐含层彼此之间还具备着大量的联系。RNN的这种特殊架构使得它可以应付输入序列之中存在的长程记忆性和周期性。随着这两大架构的出现，人工神经网络的学习能力学习速度和解决问题的能力迅速提升，从而使深度学习能够广泛地发展和应用。

另外，人们还在寻求新架构的突破。例如，Google的研究人员就提出了一种扩展了传统计算机体系结构的新型计算架构：神经计算机（神经图灵机）：

它可以用于复杂的推理，因为它不仅仅是一个神经网络的架构，还结合了冯诺依曼式架构，在处理序列数据上其实已经优于RNN。

#### 4.2 训练方式如何影响深层网络呢？ 
除了架构会影响深度网络的表现以外，训练的方式也会对结果造成很大的影响。

在这里，我们列举了两篇文章来说明训练方式的重要性。 第一篇是Bengio的“课程学习（Curriculum Learning），该文指出当我们用数据训练人工神经网络时，更有效的方法是先将少量特定标签数据喂给网络，然后再拿剩下的数据去训练该网络，如此类推的进行层次化训练，这样可以有效地提高网络的“学习”能力。Bengio教授预测该种学习方式将帮助机器学习吸取人类学习的优点，提升机器学习等策略的学习效果，协助其跳出局部极优，获得更好的泛化能力。 
第二篇文章是”How transferable are features in deep neural network”，该文详细地比较了不同的迁移学习方式是如何影响网络的学习效率的。有了更有效的迁移学习办法，我们可以通过迁移学习将训练好的神经网络迁移到小数据集中进行训练。 

再比如，AlphaGo的复杂训练流程也向我们展示了不同的训练方式、训练路径对于一个深度学习系统的重要性。首先，ALphaGo团队由人类的下棋经验快速训练了一个小的网络：快速走棋网络；然后再根据人类下棋的棋谱，训练一个大的网络：监督学习走棋网络；接着通过迁移学习，让AlphaGo通过自己和自己对抗下棋，得到一个强化学习走棋网络；最终再得到自己的价值网络，整个训练流程非常复杂却又十分精巧，是一个庞大的工程。 

### 5.深度学习的本质
虽然我们已经对深度学习在人工智能的地位，它的基本发展历史，以及它的制约因素等有了清醒地认识，但是我们仍然并不能把握住深度学习的本质。深度学习的本质显然并不一定在它的“深”，而是在于它对于所学特征的“表达能力（representation）”。 换句话说，深度学习对于我们来说，更重要的本领就在于它可以从海量的数据中自动学习、抽取特征的能力。

例如，CNN在做图像识别的时候就可以自动提炼出数字图像中的低尺度和高尺度信息。如下图，低层（离输入端比较近）的神经元可以提取数据中的边缘、棱角等小尺度信息；中间层单元可以提取数据中更高一层的尺度信息；而到了更高层，它就具备了提取图像中大尺度，例如整张人脸的特征。 


深度神经网络的另一个重要特性就在于特征提取之后还可以进行迁移嫁接，把神经网络进行组合拼接，例如我们可以组合CNN+RNN神经网络从而得到一个全新的看图说话网络。

### 6.深度学习受欢迎的原因？
总结来看，所谓的深度学习就是一种特殊的人工智能技术，它可以利用人工神经网络的方式从海量的数据中提取不同尺度的特征。而深度学习的本质就在于它的特征学习能力。利用迁移学习等技术，我们可以利用训练好的神经网络进行各种组合拼接，从而解决没有大数据时候的冷启动问题。

下面的曲线告诉了我们为什么深度学习目前是最受欢迎的。

我们看到，随着数据规模的增加，深度学习精准度就一直增加，从而最终突破商业应用的水平，这已经远远超过了传统算法。 另外，深度学习技术还可以帮助我们构建能够自动学习的端到端（End to End）模型，这就使得我们可以在不具备特定领域知识的情况下，让机器通过不断地吸收大量数据而表现得非常专业。这就让大量的初创公司在不具备行业知识积累的情况下能够快速占领市场。也许这就是大家对深度学习趋之若鹜的原因。





## ytorch的基本原理及入门
在了解到深度学习的发展概况之后，我们会得到一个错觉就是深度学习是一个十分高深莫测的东西，似乎离我们普通人很遥远。但其实随着Google、Facebook等大公司推进了包括TensorFlow、Pytorch等一系列深度学习开源平台，这就使得原本只有在大型实验室才可以获得的技术一下子就变成了我们每个人都触手可及的了。而且，随着大量的云计算服务变得普及和廉价，每一个创业公司，甚至每一个普通人都可以利用这些平台来做大规模的深度学习试验、研究或者是应用。

### 1. Pytorch特点
首先Pytorch是一个深度学习的开源框架，它具有以下的特征：
和Python完美的融合：pythonic
支持张量计算：tensor computation
动态计算图：Dynamic Computer Graph 


在这里，我们隆重地推出PyTorch这个深度学习框架，这是一款Facebook大力推荐的平台。PyTorch既有悠久的历史（它的前身是Torch），同时它又吸收了TensorFlow、Keras、Theano等深度学习开源平台的优点，能够支持大量的Tensor计算，支持GPU上的计算，以及多台机器的协调并行运算。更重要的是，PyTorch的动态计算图特性使得它能够非常方便地完成反向传播算法，从而快速地计算复杂模型的梯度信息，这些都是传统的开源框架所不具备的特性。

更关键的是在于PyTorch的简单易用性，它对于Python语言的无缝拼接，使得它是一款非常适合初学者上手的深度学习开源框架。下面就让我们来详细介绍PyTorch。


