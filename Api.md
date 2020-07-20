# API Document

This is a document of API. First of all, the port is 8088

## /user

------

### /getOne

- type: GET

- arg: id

- return: all attributes of user

### /getAll

- type: GET

- arg: null

- return: all user

### /login

- type: POST

- arg: ph(phone), pwd(password)

- return: User(id, name, sex, type, reg_time, birthday)

- intro: 若无对应用户，返回id为-1；密码错误返回id为-2；用户权限请参考[week1](meeting/week1.md)

### /reg

- type: POST

- arg: User(phone, password, birthday, name)

- return: String

- intro: 成功返回“success”，用户名已存在返回“name error”，电话号码已注册返回“phone error”；用户类型默认为0（普通用户），用户性别默认为1（男）

### /update

- type: POST

- arg: User(id, name ... ) any member of user need to be updated

- return: String

- intro: 成功返回“success”，用户名已存在返回“name error”，电话号码已注册返回“phone error”

### /follow

- type: POST

- arg: sub(动作的主语用户id)，obj(宾语用户id)，flag(1/-1)

- return: String

- intro: flag: 1 为关注，-1为取关；返回值"self"表示对自己操作，即sub等于obj，但是这种情形一般不存在（前端没有对应的入口）/"success"/"flag"表示flag不为1/-1；

> 后端实现存在可能已经关注但是依然收到了关注的请求/诸如此类没有核实存在性的bug，但是这个问题可以希望并且完全可以依靠在前端的实现--即用户只能看到自己关注的用户，不存在入口可以发送上述bug的请求

### /auth

- type: POST

- arg: Integer sub(发请求用户id), Integer obj(目标用户id), Integer tar(将授予的权限)

- return: String

- intro: 最新的权限等级划分规则见[week2 07-16](meeting/week2.md).对于不同的返回值有以下解释

  - "target error": 非法的target，大于等于8或者小于-8

  - "self": 对自己进行授权

  - "target equals": 新旧权限相同，没有更新的必要

  - "sub not admin": 动作主体没有管理员权限，越级

  - "obj is boss": 动作对象是老板，这叫僭越

  - "sub no ban auth": 动作主体是管理员，要封禁/解禁普通用户但是没有相应的权限

  - "sub not boss": 对管理员进行授权，但是动作主体不是老板

  - "success": 顾名思义

## /blog

------

### /setLabel

- type: POST

- arg: String label

- return: void

- intro: 给管理员用户使用，添加新的label

### /setBlog

- type: POST

- arg: Integer uid, Integer type, String content, Integer post_day,String video, String imag, String label, String username, String avatar

- return: Integer id（代表该动态的存储id）

- intro: type使用三位二进制代表动态的两种状态

    最高位0代表非转发，1代表转发；后两位00代表自己可见，01代表粉丝可见，11代表公开。例子：type=7代表转发且公开

    imag和label是使用JSON将数组转化为string的参数。他们的转化前类型为：imag: List< String>; label: List< Label>.

### /getPublicBlogs

- type: GET

- arg: 无

- return: List< JSONObject>

- intro: 给没有登陆的用户看的动态界面，所有不是公开的动态都不可见。JSONObject的格式为：
  
  [{key:"blog", valueType:Blog}, {key:"blogMongo", valueType:BlogMongo}, {key:"reblog", valueType:Blog/String}, {key:"reblogMongo", valueType:BlogMongo/String}]
  
  其中如果非转发，reblog和reblogMongo的值是"null"，如果转发的动态已经删除，那么reblog和reblogMongo返回的是"del",其他拉取动态在此方面的规则类似，不做赘述。
  
  由于上述格式较为复杂，下面提供一个实例(该例子只含blog和blogMongo)：
  
  [{"blogMongo":{"comments":[],"id":3,"images":["default","default","default","default"],"labels":[{"content":"学习","flag":0,"id":2},{"content":"游戏","flag":0,"id":3}],"useravatar":"default","video":"null","who_like":[]},"blog":{"com_number":0,"id":3,"like":0,"post_day":"2020-7-15","reblog":0,"type":3,"uid":1,"username":"徐珺涵"}}]

### /getBlogsByLabel

- type: GET

- arg: Integer lid, Integer uid

- return: List< JSONObject>

- intro: 根据标签请求动态，同样会屏蔽该用户不可见动态。

JSONObject的格式为：
  [{key:"blog", valueType:Blog}, {key:"blogMongo", valueType:BlogMongo}, {key:"reblog", valueType:Blog/String}, {key:"reblogMongo", valueType:BlogMongo/String}]

### /getBlogsLogined

- type: GET

- arg: Integer uid

- return: List< JSONObject>

- intro: 给登陆的用户看的动态界面。JSONObject的格式为：
  [{key:"blog", valueType:Blog}, {key:"blogMongo", valueType:BlogMongo}, {key:"reblog", valueType:Blog/String}, {key:"reblogMongo", valueType:BlogMongo/String}]
  
### /setLike

- type: POST

- arg: Integer uid, Integer bid

- return: boolean

- intro: 点赞。如果返回false则说明该用户已赞过。
  
### /removeLike

- type: POST

- arg: Integer uid, Integer bid

- return: boolean

- intro: 取消点赞。如果返回false则说明该用户没赞过。
  
### /collect

- type: POST

- arg: Integer uid, Integer bid, boolean flag

- return: boolean

- intro: flag=1收藏该动态。flag=0取消收藏。

### /setReblog

- type: POST

- arg: Integer uid, Integer bid, Integer type, String content, String post_day, String username, String useravatar

- return: boolean

- intro: 转发（转发时转发者仅允许添加文字）
  
### /removeBlog
  
- type: POST

- arg: Integer uid, Integer bid, Integer type

- return: boolean

- intro: 返回false时是该用户无权删除。返回true删除成功。
  
### /setComment

- type: POST

- arg: Integer uid, String username, Integer to_uid, String to_username, Integer bid, String content

- return: boolean

- intro: 评论
