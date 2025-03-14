## [torch 参数更多]torch.nn.CrossEntropyLoss
### [torch.nn.CrossEntropyLoss](https://pytorch.org/docs/stable/generated/torch.nn.CrossEntropyLoss.html#torch.nn.CrossEntropyLoss)

```python
torch.nn.CrossEntropyLoss(weight=None,
                          size_average=None,
                          ignore_index=- 100,
                          reduce=None,
                          reduction='mean',
                          label_smoothing=0.0)
```

### [paddle.nn.CrossEntropyLoss](https://www.paddlepaddle.org.cn/documentation/docs/zh/develop/api/paddle/nn/CrossEntropyLoss_cn.html#crossentropyloss)

```python
paddle.nn.CrossEntropyLoss(weight=None,
                           ignore_index=-100,
                           reduction='mean',
                           soft_label=False,
                           axis=-1,
                           name=None)
```

PyTorch 相比 Paddle 支持更多其他参数，具体如下：
### 参数映射
| PyTorch       | PaddlePaddle | 备注                                                   |
| ------------- | ------------ | ------------------------------------------------------ |
| weight  | weight           | 表示每个类别的权重。  |
| size_average | -            | PyTorch 已弃用，Paddle 无此参数，需要转写。|
| ignore_index  | ignore_index            | 表示忽略的一个标签值。  |
| reduce       | -            | PyTorch 已弃用， Paddle 无此参数，需要转写。  |
| reduction  | reduction            | 表示应用于输出结果的计算方式。  |
| label_smoothing | -            | 指定计算损失时的平滑量，Paddle 无此参数，暂无转写方式。  |
| -             | soft_label  | 指明 label 是否为软标签，PyTorch 无此参数，Paddle 保持默认即可。  |
| -             | axis       | 进行 softmax 计算的维度索引，PyTorch 无此参数，Paddle 保持默认即可。   |

### 转写示例
#### size_average
size_average 为 True
```python
# PyTorch 写法
torch.nn.CrossEntropyLoss(weight=w, size_average=True)

# Paddle 写法
paddle.nn.CrossEntropyLoss(weight=w, reduction='mean')

```

size_average 为 False
```python
# PyTorch 写法
torch.nn.CrossEntropyLoss(weight=w, size_average=False)

# Paddle 写法
paddle.nn.CrossEntropyLoss(weight=w, reduction='sum')
```

#### reduce
reduce 为 True
```python
# PyTorch 写法
torch.nn.CrossEntropyLoss(weight=w, reduce=True)

# Paddle 写法
paddle.nn.CrossEntropyLoss(weight=w, reduction='mean')
```

reduce 为 False
```python
# PyTorch 写法
torch.nn.CrossEntropyLoss(weight=w, reduce=False)

# Paddle 写法
paddle.nn.CrossEntropyLoss(weight=w, reduction='none')
```

#### reduction
reduction 为'none'
```python
# PyTorch 写法
torch.nn.CrossEntropyLoss(weight=w, reduction='none')

# Paddle 写法
paddle.nn.CrossEntropyLoss(weight=w, reduction='none')
```

reduction 为'mean'
```python
# PyTorch 写法
torch.nn.CrossEntropyLoss(weight=w, reduction='mean')

# Paddle 写法
paddle.nn.CrossEntropyLoss(weight=w, reduction='mean')
```

reduction 为'sum'
```python
# PyTorch 写法
torch.nn.CrossEntropyLoss(weight=w, reduction='sum')

# Paddle 写法
paddle.nn.CrossEntropyLoss(weight=w, reduction='sum')
```
