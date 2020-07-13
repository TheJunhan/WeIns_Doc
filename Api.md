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

## /blog

------

### /release

- type: POST
