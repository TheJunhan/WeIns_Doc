# Project Introduction

> 📕 A document simply introduce to our project

## Main Features

基于兴趣的社交，功能可参考微博

* 用户
  * 注册登录
    * 使用手机号码登录，手机号码格式验证，每个手机号仅能注册一次
    * 需要填写生日，未满14岁禁止注册
    * 填写用户名，不能与其它用户重名
    * 表单完成后需要选择1 ~ 3 个感兴趣的话题
  * 管理员账户特殊权限
    * 封禁/解禁用户（用户管理员可见的用户列表）
    * 删帖子
    * 删评论
* 动态
  * 发布
    * 支持附带图片、emoji表情
    * 可为动态添加相关的话题便于其它用户读到该动态
    * 附加可见范围（全部（默认）/好友/自己）
  * 转发
    * 若动态为转发的其它动态，动态展示卡片会附带原动态的内容（不包括图片）
    * 附带评论到原动态的功能
  * 查看
    * 点击图片查看放大图片
    * 点击用户名进入个人主页
  * 点赞
    * 点赞完成图标及数目变化
  * 收藏
    * 收藏完成图标及数目变化
  * 修改
    * 只可修改可见状态，内容不可修改（参考微博仅vip用户能修改正文）
  * 删除
    * 仅自己及动态管理员可删除
    * 无权限删除者不可见该按钮
  * 评论
    * 直接评论动态
    * 对评论进行评论
    * 评论分级
      * 对动态作者的评论（根评论）
      * 对根评论的评论（子评论）
      * 对除根评论外的评论评论（孙评论）
      * 显示时子孙评论折叠到根评论下
      * 子孙评论显示@原评论用户
* 各种计数器
  * 评论数
  * 转发数
  * 点赞数
  * 收藏数
* 推荐算法
  * 用户画像：每一个感兴趣的标签对应一个权值
  * 根据用户感兴趣的话题推荐

## Tech Stack

* Front-end
  * Framework
    * Vue.js
  * Unit Test
    * vue@cli-jest
  * E2E test
    * cypress
* Back-end
  * Framework
    * Spring Boot
  * Security
    * Spring Security
    * JWT
    * Interceptor
  * Database
    * MySql
    * MongoDB
  * Cloud Server
    * AWS
  * Performance Test
    * Prometheus
    * Jmeter
    * Grafana
  * Other Tools
    * Postman
    * Junit5
* Devops
  * Container
    * Docker
  * CI/CD(optinal)
  * Container Organization(Optional)
  * Work Control Flow
    * GitHub
