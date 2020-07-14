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

## /blog

------

### /release

- type: POST
