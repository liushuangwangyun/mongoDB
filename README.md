# mongoDB

## 安装配置mongodb

1.添加公共的keyserver
```
$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
```
2.3.4创建/etc/apt/sources.list.d / mongodb - org。名单列表文件使用Ubuntu的命令适合您的版本:
```
$ echo "deb [ arch=amd64,arm64 ] http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
```
3.发出以下命令来重新加载本地包数据库:
```
$ sudo apt-get update
```
4.nstall MongoDB的最新的稳定版本。发出以下命令:
```
sudo apt-get install -y mongodb-org
```
5.装好以后应该会自动运行mongod程序，通过"pgrep mongo -l "查看进程是否已经启动
```
启动：sudo service mongod restart
查看进程：pgrep mongo -l
```

## 数据库的创建

使用use dbname命令创建新数据库，如果dbname已经存在，那么切换到数据库,db查看当前所在的数据库位置
```
> use stu
switched to db stu
> db
stu
```
show dbs 查看创建的数据库
```
> show dbs
local 0.000GB
stu   0.000GB
```
db.dropDatabase()来删除数据库
```
> db 
stu
> db.dropDatabase()
{ "dropped":"stu","ok":1 }
> show dbs
```
## mongodb集合的创建和删除

### 集合的创建

创建db.collectionName.insert()创建集合，collectionName：集合名称
```
> db.liu.insert({"name":"liushuang","age":22})
WriteResult({nInserted:1})
```

删除集合：db.collectionName.drop() 
```
> db.liu.drop()
true
```

查看所有集合：show.collections
查看集合中的所有内容：db.collectionName.find()

## mongodb 文档操作

所有存储在集合中的数据都是BSON格式，BSON：是一种二进制形式的存储格式
插入文档：
db.collectionName.insert(doc)
db.collectionName.save(doc)
```
直接插入，插入新的内容在下面一条不会覆盖上面插入的信息
> db.collectionName.insert({'name":"lisi","age":20})
WriteResult({ "nInserted" : 1 })

查看文档中的内容：db.collectioname.find()
> db.collectionName.find()
{ "_id" : ObjectId("578b4fc554ec6d203080b398"), "name" : "lisi", "age" : 20 }

第二种插入的方法，先保存于变量中
> doc = ({"name":"wang","love":"game"});
{"name":"wang","love":"game"}
> db.two.inser(doc);
WriteResult({ "nInserted" : 1 })
>db.two.find()
{ "_id" : ObjectId("58f1bcf0f1c9905a573e047a"), "name" : "zhang" }
{ "_id" : ObjectId("58f1c021f1c9905a573e047c"), "name" : "liu", "home" : "baotou" }
{ "_id" : ObjectId("58f1c2e1f1c9905a573e047d"), "name" : "zhangsan", "love" : "game" }
```
注：如果不指定_id 字段save()方法类似于insert()方法。如果指定_id字段，则会更新该_id的数据。

## 更新文档














