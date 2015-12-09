# MEAN技术分享演讲稿

## mongodb

### SQL和noSQL数据库
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
