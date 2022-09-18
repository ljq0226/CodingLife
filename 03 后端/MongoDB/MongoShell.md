
## mongosh

在终端输入mongosh,开始进入mongosh模式，连接默认本地数据库操作。
更多connect操作查看[官网](https://www.mongodb.com/docs/mongodb-shell/connect/)
```shell
mongosh # connect to a MongoDB instance running on your localhost with default port 27017. equals "mongodb://localhost:27017"

mongosh "[远程mongodb]" 
```

### 常用指令
`show dbs`  用于查看所有的数据库
`use [someDB]`  进入名为[someDB]的数据库(若无此数据库，则自动创建一个新的)
`show collections/tables` 查看该数据库下所有collections
> 类似的还有 show profile    show users   show roles    show  logs 
> 输入 help 查看更多
 
`cls`  清除之前的信息
`exit`  退出mongosh模式


