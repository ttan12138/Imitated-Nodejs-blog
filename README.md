## 仿 Nodejs 多人博客

### 目录结构

```javascript
app.js	项目的入口文件
models	存储使用mongoose设计的数据模型
node_modules	第三方包
package.json	包描述文件
package-lock.json	第三方包版本锁定文件（npm5之后才有）
public	公共静态资源
routes
views	存储视图目录
```

### 模板页

- [子模板](https://aui.github.io/art-template/zh-cn/docs/syntax.html#%E5%AD%90%E6%A8%A1%E6%9D%BF)
- [模板继承](https://aui.github.io/art-template/zh-cn/docs/syntax.html#%E6%A8%A1%E6%9D%BF%E7%BB%A7%E6%89%BF)

### 路由设计


| 路由            | 方法 | get参数 | post参数                | 是否需要登录 | 备注             |
| --------------- | ---- | ------- | ----------------------- | ------------ | ---------------- |
| /               | get  |         |                         |              | 渲染首页         |
| /register(登录) | get  |         |                         |              | 渲染注册页面     |
| /register       | post |         | email,nickname,password |              | 处理注册请求     |
| /login          | get  |         |                         |              | 渲染登陆界面     |
| /login          | post |         | email,password          |              | 处理登录请求     |
| /loginout       | get  |         |                         |            | 处理退出请求     |
| /topics/show    | get  | id      |                         |            | 渲染话题详情界面 |
| /topic/new      | get  |         |                         |              | 渲染发表文章页面 |
| /topic/new      | post |         | topic   |            | 处理新话题页表单 |
| /page/choose    | get  | num     |                         |            | 处理话题页数请求 |
| /settings/profile       | get  |    email     |            |            | 渲染基本信息请求页面 |
| /settings/profile       | post |         |   user |      | 处理基本信息请求   |
| /settings/admin       | get|         |                         |              | 渲染账户设置页面   |
| /settings/admin       |  |         | user |              | 处理账户设置请求 |
| /logoff | get | email |  | | 处理注销请求 |
| /comment        | post |         | comment |              | 提交评论         |
| /getfun         | get  | id |                         |              | 关注请求         |

### 模型设计


### 功能实现

### 步骤

- 创建目录结构
- 整合静态页-模板页
  - include
  - block
  - extend
- 设计用户登陆，退出，注册的路由
- 用户注册
  - 先处理客户端页面的内容（表单控件的name，收集表单数据，发起请求）
  - 服务端
    - 获取从客户端收到的数据
    - 操作数据库
      - 如果有错，发送500告诉客户端服务器错了‘
      - 其他的根据业务发送不同的响应数据
- 登录
- 退出
- 个人设置
- 文章
