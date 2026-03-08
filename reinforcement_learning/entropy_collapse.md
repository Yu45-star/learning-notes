# 熵塌陷（Entropy Collapse）

def： 策略熵（policy entropy）在训练初期急剧下降并且持续趋近于零的现象，即在少数的训练step之后，模型对于自己的回答过于自信（策略变得过度确定，overly confident），无法生成多样化的响应，从而陷入局部最优。