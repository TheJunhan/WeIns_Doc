# Footprint - Record what you have done

## Week1

### 07-06

* Ao Yuchen
  * 新建Vue项目
  * 新建Spring Boot项目
* Other members
  * 讨论项目大体以及学习掌握了git工作的要领

### 07-07

* Ao Yuchen
  * 更新架构讨论的文档
  * 完成注册界面
  * 完成底边栏footer
* Xu Junhan
  * 完成部分数据表设计
* Dou Jiawei
  * 测试IDEA连接GitHub
* Fu Yuhan
  * 完成LOGO设计

### 07-08

* Ao Yuchen
  * 完成侧边导航栏
  * 完成登录组件以及登录的弹出框
  * 完成Blog组件（半成品）
* Xu Junhan
  * 完成后端用户部分
  * 解决中文乱码问题
* Dou Jiawei
  * 完成顶部导航栏
* Fu Yuhan
  * LOGO背景虚化
  * 制作海报
  * 设计浏览器标识Icon

### 07-09

* Ao Yuchen
  * 完成发布动态的组件
  * 新增转发弹出框
  * 优化Blog交互
  * 更新项目文档至符合 [Document-style](https://github.com/sjtu-se128/Document-style) 规范
* Xu Junhan
  * 完成后端注册逻辑
* Dou Jiawei
  * 侧边栏、登录卡设置浮动
  * 优化部分输入框不能输入的bug
  * Ajax
* Fu Yuhan
  * 优化Blog组件样式
  * 完成计数器counter组件
  * 完成个人主页背景板（待调优）

### 07-10

* Ao Yuchen
  * 完成转发的弹出框
  * 完成个人主页页面布局
  * 个人资料卡组件
  * 我的动态组件
* Xu Junhan
  * 完成注册登录
  * 规范前后端接口，细节见[Week1文档](/meeting/week1.md)
  * 开始学习使用服务器
* Dou Jiawei
  * 优化前端逻辑，修复了图片显示、z-index错误、注册入口错误等bug
  * 添加了上传图片视频、转码、查看图片详情等功能
* Fu Yuhan
  * 完成个人资料页的组件代码编写
  * 调整需要用到的海报以及图片

## Week2

### 07-13

* Ao Yuchen
  * 这周转后端（全栈开发）
  * API文档用户部分
  * 后端User完成Dao, Service层
* Xu Junhan
  * 完成了后端数据库设计，接下来后端部分交由ayc负责，我负责服务器。
* Dou Jiawei
  * 添加了axios接口，修复了按钮不能点击的问题，添加了标签选择功能，能实现标签选择删除添加搜素。
  * 尝试修复路由切换出现僵死的bug，预计本周修复
  * 重新设计确认了数据库表结构
* Fu Yuhan
  * 完成了发布评论/查看评论组件

### 07-14

* Ao Yuchen
  * 用户登录/注册功能
  * 用户关注/取关功能
  * 优化了用户的数据库架构
* Xu Junhan
  * 生成label&发表动态
* Dou Jiawei
  * 完善前端用户登陆、注册、session和全局变量等功能
  * 定位了前端页面切换卡死的bug
* Fu Yuhan
  * 优化评论组件

### 07-15

* Ao Yuchen
  * user相关的所有单元测试
  * 修改用户权限的接口
* Xu Junhan
  * 发布动态、拉取当前用户可见动态、根据标签拉取动态、未登录界面展示动态接口正式上线
* Dou Jiawei
  * 完成了signin和signup的单元测试
  * 修改了前端bug：生日计算比正常少一个月
* Fu Yuhan
  * 修复个人中心页面bug，开始编写业务逻辑

### 07-16

* Ao Yuchen
  * 完成前端注册/登录业务逻辑的bug修复
  * 个人中心页面的前后端通信
  * 优化权限分级制度并实现auth接口
* Xu Junhan
  * 完成了点赞、收藏、转发等功能。
* Dou Jiawei
  * 添加了三个测试文件
* Fu Yuhan
  * 编写业务逻辑

### 07-17

* Ao Yuchen
  * 个人中心路由
  * 一些杂七杂八的优化
* Xu Junhan
  * 测试了后端动态部分接口正确性
* Dou Jiawei
  * 完成所有前端测试
* Fu Yuhan
  * 编写前端的关注粉丝相关组件

## Week3

### 07-20

* Ao Yuchen
  * 完成发布动态
  * 登录页面新增了管理员入口
  * 个人中心计数器组件和我的动态组件的拉取数据
* Xu Junhan
  * 完成了服务器的前后端部署，现在可以url访问了
* Dou Jiawei
  * 优化了个人信息界面ui和逻辑
* Fu Yuhan
  * 用户表组件

### 07-21

* Ao Yuchen
  * 魔改blog组件
* Xu Junhan
  * 增加了删评、通过id查看动态接口，修复了用户头像实时更新和评论不能显示bug
* Dou Jiawei
  * 研究了e2e测试文档
  * 编写了登陆card的测试js文件
* Fu Yuhan
  * 用户管理界面

### 07-22

* Ao Yuchen
  * blog 图片/点赞/收藏
* Xu Junhan
  * 后端增加了spring-security，可用性有待进一步确认
* Dou Jiawei
  * 修复了用户信息界面不能正确查重的bug
  * 修复了用户信息界面两个编辑面板不能同时编辑的bug
  * 新增了几个页面的e2e测试
* Fu Yuhan
  * 用户管理员界面

### 07-23

* Ao Yuchen
  * 动态的转发/评论功能
* Xu Junhan
  * spring-security发现前端无法访问，开始学习jwt。
* Dou Jiawei
  * 完善前后端的基本功能
  * 继续编写e2e测试
* Fu Yuhan
  * 整理文档

### 07-24

* Ao Yuchen
  * 实现了他人主页以及从公开动态上点击名字进入其主页的功能
  * 至此完成了基本功能的全部接口
* Xu Junhan
  * 增加了jwt，前端已经可以使用
* Dou Jiawei
  * 完成了e2e测试
  * 修改了管理员删除博客会自动登出的bug
  * 完善了管理界面搜算ban用户等等操作
  * 修改了管理员权限封禁的bug
* Fu Yuhan
  * 整理文档

## Week4

### 07-27

* Ao Yuchen
  * 转发的动态增加了引用原动态
  * 评论的优化
* Xu Junhan
  * 修改了getBlogsLogined返回值残缺的问题
  * 修改了getBLogsById的接口，变得更为符合业务需求，其他bug在自行测试时并没有发现，有待商榷。
* Dou Jiawei
  * 开始着手编写压力测试和性能测试
  * 优化前端页面
* Fu Yuhan
  * 优化前端页面

### 07-28

* Ao Yuchen
  * 上传头像功能
  * 优化前端的用户权限解析
  * 优化转发评论后的动态刷新
* Xu Junhan
  * 更改写评论接口
  * 新增返回某个动态接口
  * 新增修改动态接口
* Dou Jiawei
  * 前端发动态后自动刷新
* Fu Yuhan
  * 整理周一上课的内容

### 07-29

* Ao Yuchen
  * 评论时间
  * 动态文本的换行显示
  * 评论的删除
* Xu Junhan
  * 修复了某个bug
* Dou Jiawei
  * grafana完成
  * 测试文件基本完成
* Fu Yuhan
  * 优化前端页面

### 07-30

* Ao Yuchen
  * 回复评论
  * 多层评论的样式以及发布回复
* Xu Junhan
  * 数据库评论增加字段帮助实现多层评论
* Dou Jiawei
  * 完成性能测试
  * 着手优化
* Fu Yuhan
  * 优化前端页面

### 07-31

* Ao Yuchen
  * 评论折叠
  * 点击加载更多动态
* Xu Junhan
  * 删除评论后评论数不变的bug
  * 着手写jwt
  * 修复token和fliter的bug
* Dou Jiawei
  * 继续优化单元测试
  * 优化性能
* Fu Yuhan
  * 优化前端页面
