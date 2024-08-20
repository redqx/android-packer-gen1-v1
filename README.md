

# 加壳器

涉及的加壳器: 自动化实现apk解包,打包, AndroidManifest.xml修改, apk签名



# gen1_v1

position => android-packer/packer/gen1_v1



简单的一代壳原理实现, 基于[dpt-shell](https://github.com/luoyesiqiu/dpt-shell) 基础上做一个修改. 主要是提取了其中的加壳模块

=>  [原理分析](./analysis/gen1_v1.md)



```
项目布局:
	-dpt: java项目, 用于加壳. 可以生成jar包
	-shell: Android Studio项目, 实现application代理, 动态加载dex
ps: Android studio也可以调试java项目, 比如调试单个java文件之类的
```



usage:

```
usage: java -jar dpt.jar [option] -f <apk>
 -D,--debug            Make apk debuggable.
 -l,--noisy-log        Open noisy log.
 -x,--no-sign          Do not sign apk.


λ java -jar dpt.jar -f org_v01.apk

ps: 之后会生成一个org_v01_signed.apk文件, 安装运行即可
```



> 不足之处: 

对于org_v1.apk的测试案例, 不知道为什么只能触发 Application的代理类执行, 不能触发AppComponentFactory代理类的执行

在有限的知识储备下,我认为AppComponentFactory和 Application类好像不能并发执行







