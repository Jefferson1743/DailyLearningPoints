# sandbox使用
## 运行

1. 通过脚本安装的方式监听对应的进程

```shell
./sandbox.sh -p 33342
```

2. 通过agent方式进行挂在

```shell
java test.class -javaagent:/opt/sandbox/lib/sandbox-agent.jar

注： javaagent方式可以确保sandbox代码在应用代码加载之前完成载入，避免引起目标JVM full GC。
```

## 事件介绍

BEFORE事件：执行方法体之前被调用
RETURN事件：执行方法体返回之前调用
THROWS事件：执行方法体抛出一场之前调用

LINE事件：方法被执行后调用，目前仅记录行号

CALL_BEFORE事件：一个方法被调用之前。
CALL_RETURN事件：一个方法被调用正常返回之后。
CALL_THROWS事件：一个方法被调用抛出异常之后。

## 生命周期

模块生命周期类型有模块加载、模块卸载、模块激活、模块冻结、模块加载完成五个状态。

+ 模块加载：创建ClassLoader，完成模块的加载
+ 模块卸载：模块增强的类会重新load，去掉增强的字节码
+ 模块激活：模块被激活后，模块所增强的类将会被激活，所有com.alibaba.jvm.sandbox.api.listener.EventListener将开始收到对应的事件
+ 模块冻结：模块被冻结后，模块所持有的所有com.alibaba.jvm.sandbox.api.listener.EventListener将被静默，无法收到对应的事件。需要注意的是，模块冻结后虽然不再收到相关事件，但沙箱给对应类织入的增强代码仍然还在。
+ 模块加载完成：模块加载已经完成，这个状态是为了做日志处理，本身不会影响模块变更行为

模块可以通过实现com.alibaba.jvm.sandbox.api.ModuleLifecycle接口，对模块生命周期进行控制，接口中的方法：

+ onLoad：模块开始加载之前调用
+ onUnload：模块开始卸载之前调用
+ onActive：模块被激活之前调用，抛出异常将会是阻止模块被激活的唯一方式
+ onFrozen：模块被冻结之前调用，抛出异常将会是阻止模块被冻结的唯一方式
