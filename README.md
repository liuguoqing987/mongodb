# 数据库操作
[中文文档](https://docs.mongoing.com/) 、 [官方文档](https://www.mongodb.com/docs/v4.2/)
- 展示数据库：show dbs；
- 显示当前db：db；
- 创建/切换db：use db；
- 插入一条数据：db.evan.insert({"name":"evan","age":28})；
- 删除数据库：db.dropDatabase();//慎用
- 删除集合：db.collection.drop();

# C
插入文档语法：db.COLLECTION_NAME.insert(document)  或者 db.COLLECTION_NAMEl.save(document)
*如果集合不存在会自动创建集合的呦*
db.col.insert({title: 'MongoDB 教程',
    description: 'MongoDB 是一个 Nosql 数据库',
    by: 'MongoDB中文网', 
    url: 'http://www.mongodb.org.cn', 
    tags: ['mongodb', 'database', 'NoSQL'],
    likes: 100  
})

doc=({...})
db.col.save(doc)

创建变量：document=({...})
# R
查询文档语法：db.COLLECTION_NAME.find( {} )
db.col.find({})


# U
update() 方法用于更新已存在的文档。语法格式如下：
db.col.update(    
    <query>, 
    <update>, 
    {       
    upsert: <boolean>,   
    multi: <boolean>,  
    writeConcern: <document>
    }
)
参数说明：

query : update的查询条件，类似sql update查询内where后面的。
update : update的对象和一些更新的操作符（如$,$inc...）等，也可以理解为sql update查询内
set后面的
upsert : 可选，这个参数的意思是，如果不存在update的记录，是否插入objNew,true为插入，
默认是false，不插入。
multi : 可选，mongodb 默认是false,只更新找到的第一条记录，如果这个参数为true,就把按条件
查出来多条记录全部更新。
writeConcern :可选，抛出异常的级别。

例如：db.col.update({'title':'MongoDB 教程'},{$set:{'title':'MongoDB'}})
以上语句只会修改第一条发现的文档，如果你要修改多条相同的文档，则需要设置 multi 参数为 true。
db.col.update({'title':'MongoDB 教程'},{$set:{'title':'MongoDB'}},{multi:true})
save() 方法通过传入的文档来替换已有文档。语法格式如下：
db.collection.save(    
    <document>,     
    {      
    writeConcern: <document> 
    }  
) 
参数说明：

document : 文档数据。
writeConcern :可选，抛出异常的级别。


# D
删除文档语法：db.col.remove({})  
db.collection.remove(     
    <query>,     
    {       
    justOne: <boolean>,
    writeConcern: <document> 
    } 
)
参数说明：

query :（可选）删除的文档的条件。
justOne : （可选）如果设为 true 或 1，则只删除一个文档。
writeConcern :（可选）抛出异常的级别。


