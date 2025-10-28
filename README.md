# 在RT-Thread中使用LEDIndicatorPP的例程

## 测试PCB

核心板使用boring tech的STM32H750VBT6核心板，使用2MFlash。

底板见PCB文件夹中。

## 如何使用

生成cmake工程后用clion打开

```shell
// 进入rtt的env环境
pkgs --update
scons --target=cmake --project-name=LEDIndicatorPPExample
clion .
```

然后openocd使用根目录下的cfg，下载调试。

msh中使用`led_i gpio`等进行测试

## 注意点

* 需要开启软定时器，即`CONFIG_RT_USING_TIMER_SOFT`，因为我们会在update中分配和释放内存。
* 软定时器线程栈开大一点，因为我们在其中使用ulog。