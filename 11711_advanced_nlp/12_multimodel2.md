## Basic generative modeling paradigms

### Autoregressive

Generate one dimension at a time given the previous ones

#### Autoregressive modeling of pixels

challenge 1: sequence length. 1024x1024 with 3 channels $\Rightarrow$ 3 million tokens.

challenge 2: each pixel carries relatively little semantic information compared to a word token. $\Rightarrow$ lots of data needed.

### Variational Auto-encoders (VAE)

Learn to reconstruct the image by compressing it into a vector and  uncompressing it.

idea: Learn a tokenizer that compactily represents an image as a sequence of discrete tokens.

Training:
- cross entropy loss
- use KL divergence, making the encoder's output distribution close to a standard Gaussian

Reparameterization trick（重参数化技巧）: 
目的： 解决包含随机采样操作的计算图无法进行反向传播的问题
反向传播本质是链式法则的连续应用，这要求计算图上的每一步都是可导的。
采样是一个随机操作。你无法计算一个随机采样的结果z对于分布参数均值和标准差的导数。
于是引用重参数化的技巧：核心思想：将随机性从包含参数的网络主干种剥离出来，作为一个独立的输入。即不直接从概率分布中采样z，而是引入一个服从正态分布的额外噪声变量，然后用一个确定性可导的数学公式来计算z。

Jensen's inequality:
核心：如果函数是一个凸函数（其图像呈现向下凸的“U”型），那么该不等式表示为 期望的函数值<=函数值的期望。如果函数是凹函数，不等式的符号会反过来。
实际问题：在复杂的概率模型中，我们经常需要最大化数据的对数边际似然。但在包含隐变量的模型中，这个对数内部通常包含一个关于隐变量的复杂积分或者期望，这在数学和计算上通常是不可解的 (intractable)。
通过引入一个近似分布，并且利用Jensen不等式，我们可以把log挪到期望的里面。这样就巧妙地将原本无法计算的积分目标，转化为了一个可以优化的下界（Lower Bound）

### VQ-VAE

Standard VAE give us a way to encode and decode images using a continuous vector.

idea: make a discrete VAE to let us: 1. encode an image as a sequence of discrete tokens. 2. decode an image from a sequence of discrete tokens

Pros: unified generative model (autoregressive, everything is tokens)

Cons: information loss from image tokenizer / detokenizer

### Generative adversarial networks (GAN)

Learn to generate an image by fooling a discriminator that detects whether an image is fake.

### Diffusion models

Gradually add noise to an image then learn to de-noise.

