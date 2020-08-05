# Variable计算
## Variable数据格式
输入纬度[b, c, h, w] 分别对应batch、 channel、 height、 width
输出纬度[b, num_filters, h, w]
有时候b表示为n, 如[n, c, h, w]
## Conv
Conv(num_channels, num_filters, filter_size, stride=1, padding=0, dilation=1, groups=None, param_attr=None, 
bias_attr=None, use_cudnn=True, act=None,  dtype='float32')

例程:
```
# 生成一个批次为1，通道数256，长宽长度都是6的Tensor
data = np.random.uniform(-1, 1, [1, 256, 6, 6]).astype('float32')
with fluid.dygraph.guard():
    # 定义一个输入通道数为256，输出通道数为64（或者称为过滤器/卷积核数量为64）,卷积核大小1x1的卷积层
    conv2d = fluid.dygraph.Conv2D(256, 64, 1)
    data = to_variable(data)
    conv = conv2d(data)
    print(conv.numpy().shape)
```
