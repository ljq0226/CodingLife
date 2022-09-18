# 安装使用






## CRUD

### Create



## Relations
### One to One
```prisma
model User {
  id      Int      @id @default(autoincrement())
  profile Profile? 
}
model Profile {
  id     Int  @id @default(autoincrement())
  user   User @relation(fields: [userId], references: [id])
  userId Int  @unique // relation scalar field (used in the `@relation` attribute above)
}
```
以上的[One to One](https://www.prisma.io/docs/concepts/components/prisma-schema/relations/one-to-one-relations) 关系表示为
>a user can have zero or one profile(the profile field is optional on User)
>a profile must always be conneced to one user

+ @relation必须声明在任意一方
+ @relation声明的一方外键**必须带有**@unique修饰符(` In Prisma versions 4.0.0 and later, if you introspect a relation of this type it will trigger a validation error.`)
+ 没有@relation修饰符的一方类型必须是**optional** (`the side of the relation without a relation scalar must be optional`)
+ [联合主键@@id @@unique](https://www.prisma.io/docs/concepts/components/prisma-schema/relations/one-to-one-relations#multi-field-relations-in-relational-databases)


### One to Many
```prisma
model User {
  id    Int    @id @default(autoincrement())
  posts Post[]
}
model Post {
  id       Int  @id @default(autoincrement())
  author   User @relation(fields: [authorId], references: [id])
  authorId Int
}
```
以上[One To Many](https://www.prisma.io/docs/concepts/components/prisma-schema/relations/one-to-many-relations)的关系表示为
>"a user can have zero or more posts"
>"a post must always have an author"

在[One To Many](https://www.prisma.io/docs/concepts/components/prisma-schema/relations/one-to-many-relations)关系中有两个关系域：
>a list relation field which is not annotated whit @relation
>the annotated relation field(including its relation scalar)

与One to One不同的是：
+ 没有@relation修饰符的一方类型必须是**mandatory**(必选的)
+ @relation声明的一方外键绑定**不是**必须带有@unique修饰符
### Many to Many
在关系数据库中，m-n关系通常通过关系表来建模。m-n-relations在Prisma模式中可以是**explicit显式的**，也可以是**implicit隐式**的。
#### Explicit
```prisma
model Post {
  id         Int                 @id @default(autoincrement())
  title      String
  categories CategoriesOnPosts[]
}
model Category {
  id    Int                 @id @default(autoincrement())
  name  String
  posts CategoriesOnPosts[]
}
model CategoriesOnPosts {
  post       Post     @relation(fields: [postId], references: [id])
  postId     Int // relation scalar field (used in the `@relation` attribute above)
  category   Category @relation(fields: [categoryId], references: [id])
  categoryId Int // relation scalar field (used in the `@relation` attribute above)
  assignedAt DateTime @default(now())
  assignedBy String
  @@id([postId, categoryId])
}
```
显示的多对多关系定义了三个model:
>Two models that have a many-to-many relation, such as Category and Post;
   One model that represents the relation table, such as CategoriesOnPosts (also sometimes called JOIN, link or pivot table) in the underlying database



#### Implicit
```prisma
model Post {
  id         Int        @id @default(autoincrement())
  title      String
  categories Category[]
}
model Category {
  id    Int    @id @default(autoincrement())
  name  String
  posts Post[]

}
```
创建隐式的多对多关系的规则：
+ Use a specific convention for relation tables
+ Do not require the @relation attribute unless you need to disambiguate relations with a name, e.g. @relation("MyRelation") or @relation(name: "MyRelation").
+ If you do use the @relation attribute, you cannot use the references, fields, onUpdate or onDelete arguments. This is because these take a fixed value for implicit m-n relations and cannot be changed.
+ Require both models to have a single @id. Be aware that:
	+ You cannot use a multi-field ID
	+ You cannot use a @unique in place of an @id



