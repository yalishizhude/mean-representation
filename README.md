# MEAN技术分享演讲稿

## mongodb
面向文档，那么什么是文档呢？很明显这不是我们常见的word文档。这里说的文档，是一种可以嵌套的数据集合。从关系数据库的范式的概念来说，嵌套是明显的反范式设计。范式设计的好处是消除了依赖，但是增加了关联，查询需要通过关联两张或者多张表来获得所需要的全部数据，但是更改操作是原子的，只需要修改一个地方即可。反范式则是增加了数据冗余来提升查询性能，但更新操作可能需要更新冗余的多处数据，需要注意一致性的问题。
{ 'id':1, 'author':'NinGoo', 'title':'白话MongoDB（一）', 'content':'按照官方的说法，此处省略一万字',

    comment:[ {'comment-author':'宋兵甲', 'comment-content':'有木有' } ,

              {'comment-author':'尼玛','comment-content':'伤不起啊' }

            ]

}

1. 相关数据存放在一起，针对性的查询可以消除join，性能比分散存储要高且方便。
2. 整个结构清晰自解析。所有字段名和值都存储，所以不需要提前设计结构，key的名字和数目可以任意指定，也就是所谓的schema-free。
3. 由于字段名在每一行每一列都需要重复存在，会带来一些额外的存储消耗，这在海量数据及字段较多的时候也需要考虑。
4. 一个document的长度有限，1.7.2之前是4MB，目前是8MB，以后可能增长到32MB。如果有更大的数据，可以使用MongoDB底层的GridFS直接作为文件存储。
5. 如果需要查找某个评论者的所有评论，则相对困难。当然，MongoDB支持任意key的索引，这也不是什么大问题。
### BSON
### 表链接与冗余数据
### sql与mongodb概念对比

<table>
    <thead>
        <th>SQL</th>
        <th>MongoDB</th>
    </thead>
    <tbody>
        <tr>
            <td>database</td>
            <td>database</td>
        </tr>
        <tr>
            <td>table</td>
            <td>collection</td>
        </tr>
        <tr>
            <td>row</td>
            <td>document|BSON document</td>
        </tr>
        <tr>
            <td>column</td>
            <td>field</td>
        </tr>
        <tr>
            <td>index</td>
            <td>index</td>
        </tr>
        <tr>
            <td>table joins</td>
            <td>embedded documents and linking</td>
        </tr>
        <tr>
            <td>primary key<br>Specify any unique column or column combination as primary key.</td>
            <td>primary key<br>In MongoDB, the primary key is automatically set to the _id field.</td>
        </tr>
        <tr>
            <td>aggregation (e.g. group by)</td>
            <td>aggregation pipeline</td>
        </tr>
    </tbody>
</table>

### SQL与mongodb的操作对比

<table>
    <thead>
        <th></th>
        <th>SQL</th>
        <th>MongoDB</th>
    </thead>
    <tbody>
        <tr>
            <td>建表</td>
            <td>
                CREATE TABLE users (
                    id MEDIUMINT NOT NULL
                        AUTO_INCREMENT,
                    user_id Varchar(30),
                    age Number,
                    status char(1),
                    PRIMARY KEY (id)
                )
            </td>
            <td>
                db.users.insert( {
                    user_id: "abc123",
                    age: 55,
                    status: "A"
                 } )
                 或者
                db.createCollection("users")
            </td>
        </tr>
        <tr>
            <td>查询</td>
            <td>
                SELECT user_id, status
                FROM users
                WHERE status = "A"
            </td>
            <td>database</td>
        </tr>
        <tr>
            <td>更新</td>
            <td>
                UPDATE users
                SET age = age + 3
                WHERE status = "A"
            </td>
            <td>
                db.users.update(
                   { status: "A" } ,
                   { $inc: { age: 3 } },
                   { multi: true }
                )
            </td>
        </tr>
        <tr>
            <td>新增</td>
            <td>
                INSERT INTO users(user_id, age, status)
                VALUES ("bcd001", 45, "A")
            </td>
            <td>
                db.users.insert({ user_id: "bcd001", age: 45, status: "A" } )
            </td>
        </tr>
        <tr>
            <td>删除</td>
            <td>
                DELETE FROM users WHERE status = "D"
            </td>
            <td>db.users.remove( { status: "D" } )</td>
        </tr>
    </tbody>
</table>


---

## Express.js
### koa.js

---

## node.js

### npm

---

## AngularJS

### vue.js

---

MEAN.js地址：https://github.com/meanjs/mean
