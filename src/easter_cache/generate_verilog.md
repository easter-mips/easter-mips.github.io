# 生成 Verilog

EasterCache由Chisel3开发，因而使用`sbt`调用`Chisel3`模块来生成 verilog。下面的命令
```shell
mkdir target && sbt 'runMain cache.Cache --target-dir target'
```
能够生成Cache的verilog代码，保存在`target/`文件夹中。

注意项目中使用`BlackBox`封装了用Block Memory Generator生成的RAM Xilinx IP。IP名称分别为`bank_ram`与`data_bank_ram`。使用生成的verilog代码时，需要在工程中对应定制。

## 参数配置

修改`src/main/scala/cache/Cache.scala`文件中
```scala
object Cache extends App {
  new ChiselStage execute(args, Seq(ChiselGeneratorAnnotation(
    () =>
      new Cache(new CacheSettings(
        new CacheConfig(wayNum = 2, setWidth = 7, transNum = 1), new CacheConfig(wayNum = 2, setWidth = 7), vcacheDepth = 16
      )))))
}
```
的相关参数，即可以改变Cache配置。重新生成则得到新的Cache代码。