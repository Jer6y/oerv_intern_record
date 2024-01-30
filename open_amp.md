# 多核异构部署 OPENAMP规范

## 2024-01-28

- 今日进度
  - 查阅文档 , 按照官方搞了HTML ， 用APACHE2 部署了一下WEB服务器，方便手机上随时看
- 思考
  - 好像 openamp目前并不是很火爆的感觉，很新的东西，官方文档在github上的star 数比较少的样子
  - 但是应该是个比较前沿的，多核异构也确实是比较新的东西
  - 再看看文档，学学新东西, more power!!!!! 笑 : ）

### 2024-01-30

- 今日进度
  - 查阅文档，查阅Lichee rv nano datasheet 
- 思考
  - 总结了一下后面可能要干的事情
    - openEuler embedded  没有 lichee rv nano 的支持版本，可能会给embedded 做  相关的移植
    - lichee rv nano 有 linux 5.10 的支持SDK版本，openEuler embeded 的内核也是linux 5.10 所以应该不是太困难
    - 若较困难，后面尝试直接部署OPENAMP 不上 openEuler embeded 了
    - 目前正在等待硬件抵达
    - 在RTOS这一侧已经有实现了，在UniProton 这边是有的，根据其他架构和板子的实现，看出只需要依赖于UAPI 就可以实现了，其次是需要自己动手安排 用于IIPC 的共享区域，所以需要你提前对板子的异构的资源分配有所了解，和硬件的异构通信机制有所了解