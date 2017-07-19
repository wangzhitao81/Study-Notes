# MongoDB

> MongoDB 是一个基于分布式文件存储的数据库。由 C++ 语言编写。旨在为 WEB 应用提供可扩展的高性能数据存储解决方案。MongoDB 是一个介于关系数据库和非关系数据库之间的产品，是非关系数据库当中功能最丰富，最像关系数据库的。

## 关系型数据库
> 1. 数据库有行、列的概念，数据有关系，数据不是散的。
> 2. 数据库能够提供非常方便的接口，让增删改查操作变得简单
> 3. 数据库不能自己玩，要给向PHP、.net、jsp等语言提供接口

## NoSQL
> 没有行、列的概念。用JSON来存储数据。集合就相当于“表”，文档就相当于“行”。

## SQL和NOSQL的比较
NoSQL数据库在以下的这几种情况下比较适用：
1. 数据模型比较简单；
2. 需要灵活性更强的IT系统；
3. 对数据库性能要求较高；
4. 不需要高度的数据一致性；
5. 对于给定key，比较容易映射复杂值的环境。

> 有些系统，特别需要筛选。比如，筛选出所有女生大于20岁的。那么SQL型数据库，非常擅长！因为它有行、列的概念。但是，有些系统，真的不需要进行那么多的筛选，比如站内信。站内信只需要存储就好了。不需要筛选。那么NoSQL的。

## MongoDB 适应场景
1. 游戏场景，使用 MongoDB 存储游戏用户信息，用户的装备、积分等直接以内嵌文档的形式存储，方便查询、更新
2. 物流场景，使用 MongoDB 存储订单信息，订单状态在运送过程中会不断更新，以 MongoDB 内嵌数组的形式来存储，一次查询就能将订单所有的变更读取出来。
3. 社交场景，使用 MongoDB 存储存储用户信息，以及用户发表的朋友圈信息，通过地理位置索引实现附近的人、地点等功能
4. 物联网场景，使用 MongoDB 存储所有接入的智能设备信息，以及设备汇报的日志信息，并对这些信息进行多维度的分析
5. 视频直播，使用 MongoDB 存储用户信息、礼物信息等

### 场景一
> 1. 用在应用服务器的日志记录，查找起来比文本灵活，导出也很方便。也是给应用练手，从外围系统开始使用MongoDB。
> 2. 用在一些第三方信息的获取或者抓取，因为MongoDB的schema-less，所有格式灵活，不用为了各种格式不一样的信息专门设计统一的格式，极大的减少开发的工作。

### 场景二
> mongodb之前有用过，主要用来存储一些监控数据，No schema 对开发人员来说，真的很方便，增加字段不用改表结构，而且学习成本极低。

### 场景三
> 使用MongoDB做了O2O快递应用，·将送快递骑手、快递商家的信息（包含位置信息）存储在 MongoDB，然后通过 MongoDB 的地理位置查询，这样很方便的实现了查找附近的商家、骑手等功能，使得快递骑手能就近接单，目前在使用MongoDB 上没遇到啥大的问题，官网的文档比较详细，很给力。

## 下载MongoDB
[https://www.mongodb.com/download-center?jmp=nav#community](https://www.mongodb.com/download-center?jmp=nav#community)

## 安装环境
> Windows 7 64位

## 安装MongoDB
![](http://i.imgur.com/tXIe2rl.png)
> 如果你的系统是 Windows Server 2008 R2 or Windows 7 ，需要安装一个补丁<br>
> [https://support.microsoft.com/zh-cn/help/2731284/33-dos-error-code-when-memory-memory-mapped-files-are-cleaned-by-usin](https://support.microsoft.com/zh-cn/help/2731284/33-dos-error-code-when-memory-memory-mapped-files-are-cleaned-by-usin)

![](http://i.imgur.com/g3QPCl8.png)

## 加载环境变量
![](http://i.imgur.com/Vz7BWNI.png)
> 测试

![](http://i.imgur.com/G1xasUP.png)

> mongo   使用数据库<br>
> mongod  开机<br>
> mongoimport  导入数据

## 开启数据库
> mongod --dbpath D:\AppServ\Mongo<br>
> --dbpath就是选择数据库文档所在的文件夹<br>
> mongoDB中，真的有物理文件，对应一个个数据库。U盘可以拷走<br>
> 一定要保持，开机这个CMD不能动了，不能关，不能ctrl+c。 一旦这个cmd有问题了，数据库就自动关闭了。

![](http://i.imgur.com/nZxvOxA.png)

> 新开窗口，输出 `mongo` 连接数据库

![](http://i.imgur.com/GArOujF.png)

## MongoDB 可视化工具
> MongoVUE<br>
> 下载地址：[http://www.mongovue.com/](http://www.mongovue.com/)<br>
> 需要翻墙

![](http://i.imgur.com/f4OH8B2.png)

## 官方手册
> [https://docs.mongodb.com/manual/](https://docs.mongodb.com/manual/)

# 数据库操作
## 使用数据库或者创建数据库
```SQL
use School
``` 
> 如果真的想把这个数据库创建成功，那么必须插入一个数据。

## 删除数据库
> 删除数据库，删除当前所在的数据库

``` SQL
db.dropDatabase();
```

## 添加数据
### 命令行单条插入
``` SQL
db.student.insert({"name":"Gavin",age:"20",sex:"male"})
```
![](http://i.imgur.com/VD0jka8.png)

### 通过文件导入
```
mongoimport --db School --collection student --drop --file D:/mongo.json
```
> --db School  想往哪个数据库里面导入<br>
> --collection student  想往哪个集合中导入<br>
> --drop 把集合清空<br>
> --file D:/mongo.json  哪个文件

![](http://i.imgur.com/TGU7v2r.png)<br>
![](http://i.imgur.com/ky17LV0.png)

## 查询数据
### 查询所有数据
```SQL
db.student.find()
```
![](http://i.imgur.com/cKtqkD4.png)
### 条件查询
```SQL
db.student.find({"name":"Gavin"})
```
![](http://i.imgur.com/GLRHbYH.png)


### 查询嵌套数据
> 先插入数据

```SQL
db.student.insert({"name":"Gavin", "age": "20", "score":{"math": 90, "Chinese":90}})
```
> 查询数据

```SQL
 db.student.find({"score.math":90})
```
![](http://i.imgur.com/rliFma7.png)

### 多条件查询
```SQL
db.student.find({"name": "Gavin", "score.math":90})
```
![](http://i.imgur.com/VhQLV6S.png)

### 查询条件
> 比较语句

操作|格式|范例
--|--|---
等于|	{<key>:<value>}	| db.student.find({"name":"Gavin"})
小于|	{<key>:{$lt:<value>}}|	db.student.find({"age":{$lt:20}})
小于或等于|	{<key>:{$lte:<value>}}|	db.student.find({"age":{$lte:20}})
大于|	{<key>:{$gt:<value>}}|	db.student.find({"age":{$gt:20}})
大于或等于|	{<key>:{$gte:<value>}}|	db.student.find({"age":{$gte:20}})
不等于|	{<key>:{$ne:<value>}}|	db.student.find({"age":{$ne:20}})

> 逻辑语句

#### AND
```SQL
 db.student.find({"score.math":90})
```
> 官方手册

![](http://i.imgur.com/lZYrTdg.png)

#### OR
> 寻找所有年龄是9岁，或者11岁的学生 

```SQL
db.student.find({$or:[{"age":9},{"age":11}]});
```
![](http://i.imgur.com/ichTi8t.png)

#### AND 和 OR 混合使用
![](http://i.imgur.com/alNqaic.png)

## 更新数据
> 更新格式

```SQL
db.collection.updateOne(<filter>, <update>, <options>)
db.collection.updateMany(<filter>, <update>, <options>)
db.collection.replaceOne(<filter>, <replacement>, <options>)
db.collection.update(<filter>, <replacement>, <options>)
```
> 实例

```SQL
db.student.update({"name": "Gavin"},{$set:{"age":"21"}});
```
> DOS 记录

```SHELL
> db.student.find()
{ "_id" : ObjectId("596da94b7d8c9bcb984713fa"), "name" : "Gavin", "age" : "20",
"sex" : "male" }
> db.student.update({"name": "Gavin"},{$set:{"age": "21"}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.student.find()
{ "_id" : ObjectId("596da94b7d8c9bcb984713fa"), "name" : "Gavin", "age" : "21",
"sex" : "male" }
>
```
![](http://i.imgur.com/wX0idcv.png)
> 详细解释

```SQL
db.student.update(
	{
		"name": "Gavin" //定位到要更改的地方
	},
	{
		$set:{
				"age":"21" //更改字段的内容
			}
	}
);
```
![](http://i.imgur.com/R0z1WWa.png)

### 更改所以匹配项
> 加入 multi: true 可以更改所有匹配项

```SQL
db.student.update({"sex":"male"},{$set:{"age":33}},{multi: true});
```

### 完整替换
> 但没有给$set的时候，会将后面的json数据完整替换掉前面匹配到的数据

```SQL
db.student.update({"name": "Gavin"},{$set:{"age":"21"}});
```
> DOS 记录

```SQL
> db.student.find()

{ "_id" : ObjectId("596ef8b427b1e053b47adf48"), "name" : "Gavin1", "age" : 21, "sex" : "male", "score" : { "math" : 90, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf49"), "name" : "Gavin3", "age" : 23, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4a"), "name" : "Gavin5", "age" : 25, "sex" : "male", "score" : { "math" : 90, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4b"), "name" : "Gavin6", "age" : 26, "sex" : "male", "score" : { "math" : 80, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4c"), "name" : "Gavin2", "age" : 22, "sex" : "male", "score" : { "math" : 90, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4d"), "name" : "Gavin7", "age" : 27, "sex" : "male", "score" : { "math" : 90, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4e"), "name" : "Gavin8", "age" : 28, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4f"), "name" : "Gavin9", "age" : 29, "sex" : "male", "score" : { "math" : 90, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf50"), "name" : "Gavin4", "age" : 24, "sex" : "male", "score" : { "math" : 90, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf51"), "name" : "Gavin10", "age" : 30,"sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }

> db.student.update({"name": "Gavin1"},{"modify":"all json"})

WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

> db.student.find()

{ "_id" : ObjectId("596ef8b427b1e053b47adf48"), "modify" : "all json" }
{ "_id" : ObjectId("596ef8b427b1e053b47adf49"), "name" : "Gavin3", "age" : 23, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4a"), "name" : "Gavin5", "age" : 25, "sex" : "male", "score" : { "math" : 90, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4b"), "name" : "Gavin6", "age" : 26, "sex" : "male", "score" : { "math" : 80, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4c"), "name" : "Gavin2", "age" : 22, "sex" : "male", "score" : { "math" : 90, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4d"), "name" : "Gavin7", "age" : 27, "sex" : "male", "score" : { "math" : 90, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4e"), "name" : "Gavin8", "age" : 28, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4f"), "name" : "Gavin9", "age" : 29, "sex" : "male", "score" : { "math" : 90, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf50"), "name" : "Gavin4", "age" : 24, "sex" : "male", "score" : { "math" : 90, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf51"), "name" : "Gavin10", "age" : 30,"sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }

>
```

### 其他
> 见文档 [https://docs.mongodb.com/manual/tutorial/update-documents/](https://docs.mongodb.com/manual/tutorial/update-documents/)

## 删除数据
### 删除一条数据
```SHELL
db.student.deleteOne({"name": "Gavin2"})
```
> DOS 记录

```Shell
> db.student.find()

{ "_id" : ObjectId("596ef8b427b1e053b47adf48"), "modify" : "all json" }
{ "_id" : ObjectId("596ef8b427b1e053b47adf49"), "name" : "Gavin3", "age" : 23, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4a"), "name" : "Gavin5", "age" : 25, "sex" : "male", "score" : { "math" : 90, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4b"), "name" : "Gavin6", "age" : 26, "sex" : "male", "score" : { "math" : 80, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4c"), "name" : "Gavin2", "age" : 22, "sex" : "male", "score" : { "math" : 90, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4d"), "name" : "Gavin7", "age" : 27, "sex" : "male", "score" : { "math" : 90, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4e"), "name" : "Gavin8", "age" : 28, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4f"), "name" : "Gavin9", "age" : 29, "sex" : "male", "score" : { "math" : 90, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf50"), "name" : "Gavin4", "age" : 24, "sex" : "male", "score" : { "math" : 90, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf51"), "name" : "Gavin10", "age" : 30, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }

> db.student.deleteOne({"name":"Gavin2"})

{ "acknowledged" : true, "deletedCount" : 1 }

> db.student.find()

{ "_id" : ObjectId("596ef8b427b1e053b47adf48"), "modify" : "all json" }
{ "_id" : ObjectId("596ef8b427b1e053b47adf49"), "name" : "Gavin3", "age" : 23, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4a"), "name" : "Gavin5", "age" : 25, "sex" : "male", "score" : { "math" : 90, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4b"), "name" : "Gavin6", "age" : 26, "sex" : "male", "score" : { "math" : 80, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4d"), "name" : "Gavin7", "age" : 27, "sex" : "male", "score" : { "math" : 90, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4e"), "name" : "Gavin8", "age" : 28, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4f"), "name" : "Gavin9", "age" : 29, "sex" : "male", "score" : { "math" : 90, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf50"), "name" : "Gavin4", "age" : 24, "sex" : "male", "score" : { "math" : 90, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf51"), "name" : "Gavin10", "age" : 30, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
```

### 删除全部数据
```SQL
db.student.deleteMany({})
```

### 删除多条数据
> 删除匹配到的所以数据

```SQL
db.student.deleteMany({"score.math":90})
```
> DOS 记录

``` SHELL
> db.student.find()

{ "_id" : ObjectId("596ef8b427b1e053b47adf48"), "modify" : "all json" }
{ "_id" : ObjectId("596ef8b427b1e053b47adf49"), "name" : "Gavin3", "age" : 23, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4a"), "name" : "Gavin5", "age" : 25, "sex" : "male", "score" : { "math" : 90, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4b"), "name" : "Gavin6", "age" : 26, "sex" : "male", "score" : { "math" : 80, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4d"), "name" : "Gavin7", "age" : 27, "sex" : "male", "score" : { "math" : 90, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4e"), "name" : "Gavin8", "age" : 28, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4f"), "name" : "Gavin9", "age" : 29, "sex" : "male", "score" : { "math" : 90, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf50"), "name" : "Gavin4", "age" : 24, "sex" : "male", "score" : { "math" : 90, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf51"), "name" : "Gavin10", "age" : 30, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }

> db.student.deleteMany({"score.math":90})

{ "acknowledged" : true, "deletedCount" : 4 }

> db.student.find()

{ "_id" : ObjectId("596ef8b427b1e053b47adf48"), "modify" : "all json" }
{ "_id" : ObjectId("596ef8b427b1e053b47adf49"), "name" : "Gavin3", "age" : 23, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4b"), "name" : "Gavin6", "age" : 26, "sex" : "male", "score" : { "math" : 80, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4e"), "name" : "Gavin8", "age" : 28, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf51"), "name" : "Gavin10", "age" : 30, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }

>
```

### 即可删除单条又可删除多条
```SQL
db.collection.remove(
   <query>,
   {
     justOne: <boolean>,
     writeConcern: <document>,
     collation: <document>
   }
)
```
#### remove 删除匹配到的单条数据
> `{justOne:true}` 加上这个表示只删除一个

```SQL
db.student.remove({"score.Chinese":89},{justOne:true})
```
> DOS 记录

```SHELL
> db.student.find()

{ "_id" : ObjectId("596ef8b427b1e053b47adf48"), "modify" : "all json" }
{ "_id" : ObjectId("596ef8b427b1e053b47adf49"), "name" : "Gavin3", "age" : 23, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4b"), "name" : "Gavin6", "age" : 26, "sex" : "male", "score" : { "math" : 80, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4e"), "name" : "Gavin8", "age" : 28, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf51"), "name" : "Gavin10", "age" : 30, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }

> db.student.remove({"score.Chinese":89},{justOne:true})

WriteResult({ "nRemoved" : 1 })

> db.student.find()

{ "_id" : ObjectId("596ef8b427b1e053b47adf48"), "modify" : "all json" }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4b"), "name" : "Gavin6", "age" : 26, "sex" : "male", "score" : { "math" : 80, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4e"), "name" : "Gavin8", "age" : 28, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf51"), "name" : "Gavin10", "age" : 30, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }

>
```
#### remove 删除匹配到的所有数据
> SQL语句

```SQL
db.student.remove({"score.math":80})
```
> DOS 记录

```SHELL
> db.student.find()

{ "_id" : ObjectId("596ef8b427b1e053b47adf48"), "modify" : "all json" }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4b"), "name" : "Gavin6", "age" : 26, "sex" : "male", "score" : { "math" : 80, "Chinese" : 88 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf4e"), "name" : "Gavin8", "age" : 28, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }
{ "_id" : ObjectId("596ef8b427b1e053b47adf51"), "name" : "Gavin10", "age" : 30, "sex" : "male", "score" : { "math" : 80, "Chinese" : 89 } }

> db.student.remove({"score.math":80})

WriteResult({ "nRemoved" : 3 })

> db.student.find()

{ "_id" : ObjectId("596ef8b427b1e053b47adf48"), "modify" : "all json" }

>
```