# 2024-10

- [x] 完成Aws Drive Cloud App (基本完成，剩余删除，虚拟文件夹，文件功能，后续改为aws rust sdk)
- [x] 发布GenUI的内置组件库v0.1.0
- [x] 更新组件库文档 （40%）
- [x] GenUI内置库单独项目
- [ ] 集成GenUI内置库 （重构中， to mouth 11）
- [ ] Makepad动态脚本能力 80% （重构中 ， to mouth 11）
- [x] 尝试RustPixel
  - [ ] 当前设计使用wasm + js 通道通信(需要设计新wasm流程库)
- [x] GOSIM Meeting
- [x] 发布AWS Drive Cloud App（Windows）

- 对GenUI内置组件库进行优化性重构(以及组件库文档编写)
  - [x] icon(lib)
  - [x] Svg
  - [x] Image
  - [x] Divider
  - [x] Link
  - [x] Scroll
  - [x] Macros
  - [x] 修复以外出现功能 

- Windows端 设计并解决了Maekpad Plugin插件打包无法设置应用图标问题
- Mac端 Linux端 待解决
## Makepad
  - Fix Makepad Label DrawWalk Error
  - Makepad issue (561 ~ 563) 文档提出，待解决
## GOSIM 
  - 今天看了一下汽车领域方面的，多数是做基础设施的，其实他们对UI上面了解比较少，了解到目前汽车领域不同的厂商大多都有一套自己的UI，没有统一性的东西，可以在仿真软件，操控类，仪表盘，大屏这些地方使用到UI（多为3D）较多
  - 去嵌入式了解了一下，也都是做底层，对UI和嵌入式的一些软件不是很了解，在嵌入式上面可能就和Slint那样去做一些控制类的软件和面板