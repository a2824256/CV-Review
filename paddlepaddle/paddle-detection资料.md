# 模型yml文件配置资料
## API
配置系统的大多数功能由 ppdet.core.workspace 模块提供

- register: 装饰器，将类注册为可配置模块；能够识别类定义中的一些特殊标注。
- __category__: 为便于组织，模块可以分为不同类别。
- __inject__: 如果模块由多个子模块组成，可以这些子模块实例作为构造函数的参数注入。对应的默认值及配置项可以是类名字符串，yaml序列化的对象，指向序列化对象的配置键值或者Python dict（构造函数需要对其作出处理，参见下面的例子）。
- __op__: 配合 __append_doc__ （抽取目标OP的 注释）使用，可以方便快速的封装PaddlePaddle底层OP。
- serializable: 装饰器，利用 pyyaml 的序列化机制，可以直接将一个类实例序列化及反序列化。
- create: 根据全局配置构造一个模块实例。
- load_config and merge_config: 加载yaml文件，合并命令行提供的配置项。

## 什么是OP？
Operations,也称为Ops,计算节点