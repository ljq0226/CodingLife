
### Add Documents
 **db.[collection].[api]**
#### insertOne()

```MongoDB Shell
bookstore> db.books.insert0ne({ "title": "test1", "author":"mongosh", "pages": 400})


{# 表示操作成功
acknowledged: true ，
insertedId: 0bj ectId("6315af2ea80c2b2857f6b335" )
}
bookstore>

```
#### insertMany()
```MongoDB Shell
bookstore> db. books . insert0ne([{ "title": "test1", "author": "mongosh", "pages": 400},{ "title": "test2", "author": "mongosh", "pages": 400}])

```

