## [ torch 参数更多 ]torch.Tensor.index_add_
### [torch.Tensor.index_add_](https://pytorch.org/docs/stable/generated/torch.Tensor.index_add_.html#torch.Tensor.index_add_)

```python
torch.Tensor.index_add_(dim, index, source, *, alpha=1)
```

### [paddle.Tensor.index_add_]()

```python
paddle.Tensor.index_add_(index, axis, value)
```

其中 PyTorch 与 Paddle 参数有差异，具体如下：

### 参数映射
| PyTorch       | PaddlePaddle | 备注                                                   |
| ------------- | ------------ | ------------------------------------------------------ |
| <font color='red'> dim </font> | <font color='red'> axis </font> | 表示进行运算的轴，仅参数名不一致。  |
| <font color='red'> index </font> | <font color='red'> index </font> | 包含索引下标的 1-D Tensor。  |
| <font color='red'> source </font> | <font color='red'> value </font> | 被加的 Tensor，仅参数名不一致。  |
| <font color='red'> alpha </font> | - | source 的 缩放倍数， Paddle 无此参数，需要转写。Paddle 应将 alpha 和 source 的乘积作为 value。 |


### 转写示例
#### alpha：source 的缩放倍数
```python
# PyTorch 写法
x.index_add_(dim=1, index=index, source=source, alpha=alpha)

# Paddle 写法
x.index_add_(index=index, axis=1, value=alpha*source)
```
