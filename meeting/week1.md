# Week 1

## 07-06

讨论了如何使用GitHub、如何注册AWS、简明地讨论了项目的结构

## 07-07

主要讨论了大体的架构

### 用户管理

单独的登陆注册页面，管理员可以封禁解禁账号。用户使用mysql，user(id, name, sex, avatar, phone(注册), birthday, auth(0(ban)/1(common)/2(admin)), signtime)

登陆之前可以查看分类，不能看到推荐/关注的动态，不能进行点赞等操作（会提示需要是否选择登录）

### 主页

登录入口（登录后看不见）/推荐/分类/关注(需要登录) 的动态

推荐（重点）：足迹记录所有查看过的动态，用一个标记来表示是否被用户删除，根据足迹维护一个常查看标签表，依此来推荐对应的内容；
如果是一个没有查看过任何内容的新用户，就推荐最新的动态。/空页面

### 个人中心

足迹/粉丝/关注/我的评论/我的转发/我的点赞/我的收藏/我的动态/个人资料/

维护以下表：
动态被哪些人评论/转发/点赞/收藏
哪些人评论/转发/点赞/收藏了哪些动态

关注/粉丝 直接在mongo里面存对应的所有id

### 动态

内容/标签（搜索依据）/评论/转发/点赞/收藏/删改

动态-发布人（动态id, 发布人id, 转发（-1/id））

动态（动态id, 内容（mongo: 图文音频，标签）, 发布时间, 点赞数, 评论数, 转发数, 删除flag)

转发：-1表示原创，只显示对应id的内容；否则，下面引用一个框显示转发的内容，若原动态已经删除，则显示“已删除”

评论 (id, 动态id, 内容, 时间, 评论用户id, 目标评论id(若直接评论动态，则为-1), 删除flag)

### 一些问题

- 管理员的权限分级（ban/删帖子/删评论）

- 推荐依靠标签？

- 不停地点击点赞

- 压力测试

- 搜索

- 删除

- 部署到服务器

- 测试脚本

- session 确认

## 07-08

### 管理员权限分级规定

- banned(-1)
- 普通用户(0)
- 用户管理员(4) (对应二进制：100)
- 删帖子(2) (对应二进制：010)
- 删评论(1) (对应二进制：001)
- 最高管理员(7) (对应二进制：111)

对于用户/管理员界面的说明： 管理员基本上复用普通用户的界面，对于管理员不同的权限所多出来的操作，只需要用v-if来处理即可

## 07-09

[什么是DevOps](https://blog.jjonline.cn/linux/238.html)

## 07-10

个人中心页面缩略规划

|------------背景板（头像，昵称，性别等基本信息）-------------|

|-----计数器--------|  |---------个人信息栏或者我的动态---------|

|----信息完整度----|    |---------个人信息栏或者我的动态---------|

|-----我的足迹-----|    |---------个人信息栏或者我的动态---------|

具体对应的组件请参考前端repo的README

- 完成了登录注册的接口，细节如下：
  - 注册发送请求：String name, Integer sex, String phone, String password, String birthday, String base64
    - sex为0、1、2分别代表未设置、男、女；
    - base64可以是base64的图片，也可以是"default"代表用户使用了默认头像，这样不必要在后端进行写入可以节省后端计算资源。
  - 登录
    - 发送请求：String phone, String password
    - 返回值：res为false时用电话或密码错误登陆失败、&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    base64可能返回字符串 "default"说明用了默认头像、&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    reg_time返回了一个BigDecimal型数据，具体值为该用户注册时new Date().getTime() / 1000.0，为减轻计算压力，发给前端计算、&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    其他返回值是平凡的(password和phone等暴露个人信息的值没有返回)：uid、name、sex、birthday
