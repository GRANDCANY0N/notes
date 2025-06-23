## 规范类

pojo文件说明

| 名称   | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| Entity | 实体，通常与数据库的表对应                                   |
| DTO    | 数据传输对象，例如前端的json数据通过DTO封装成Java对象在各层之间传输 |
| VO     | 视图对象，为前端展示数据提供的对象，列表数据封装好传回前端   |
| POJO   | 普通Java对象，涵括之上，属性和对应的getter、setter方法       |

common和pojo分离出来，方便管理代码

pom文件分别开来，方便依赖管理

![image-20250422142759743](springbootNote.assets/image-20250422142759743.png)

## 开发类

员工登录流程

<img src="C:\Users\Canyon\AppData\Roaming\Typora\typora-user-images\image-20250422102702286.png" alt="image-20250422102702286" style="zoom:80%;" />

**为什么不在serviceImpl层直接将entity封装成vo放回controller？**

答：serviceImpl层只是处理业务逻辑，返回业务实体，如果将vo写死在serviceImpl层，后续代码方法复用很不方便，controller层处理请求和响应，因此从前端的数据封装和后端的数据返回封装都在controller层。

员工登录失败校验图

![image-20250422102723663](C:\Users\Canyon\AppData\Roaming\Typora\typora-user-images\image-20250422102723663.png)





