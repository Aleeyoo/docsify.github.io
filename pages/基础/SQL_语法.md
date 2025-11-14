## **SQL 语法**

> [!TIP]
> [一个视频了解。](https://www.bilibili.com/video/BV1bQxMehETa/)<br>
> [Sqliteviz 在线练习](https://sqliteviz.com/app/  )

### 基础介绍

#### 数据库表

一个数据库通常包含一个或多个表，每个表有一个名字标识（例如:"Websites"），表包含带有数据的记录（行）。

#### 语句

> [!ATTENTION]
> SQL 对大小写不敏感：SELECT 与 select 是相同的。
> 某些数据库系统要求在每条 SQL 语句的末端使用分号。

### 基础查询语法

<!-- tabs:start -->

#### **SELECT**
`SELECT column1, column2, ...`<br>
`FROM table_name;`<br>
或<br>
`SELECT * FROM table_name;`<br>
<br>
**说明：**<br>
- `SELECT` 语句用于从数据库表中查询数据。
- `column1, column2, ...` 是要查询的列名，多个列名之间用逗号分隔。
- `table_name` 是要查询的表名。
- `*` 表示查询所有列。
**例如：**<br>
`SELECT * FROM Websites;`<br>
- 以上示例查询 `Websites` 表中的所有列数据。

#### **SELECT DISTINCT**
`SELECT DISTINCT column1, column2, ...`<br>
`FROM table_name;`<br>
<br>
**说明：**<br>
- `SELECT DISTINCT` 语句用于从数据库表中查询不重复的数据。
- `column1, column2, ...` 是要查询的列名，多个列名之间用逗号分隔。
- `table_name` 是要查询的表名。
**例如：**<br>
`SELECT DISTINCT country FROM Websites;`<br>
- 以上示例查询 `Websites` 表中 `country` 列的不重复值。

#### **WHERE**
`SELECT column1, column2, ...`<br>
`FROM table_name`<br>
`WHERE condition;`<br>
<br>
**说明：**<br>
- `WHERE` 子句用于过滤查询结果，只返回符合条件的行。
- `condition` 是一个表达式，用于指定过滤条件。
- `column1, column2, ...` 是要查询的列名，多个列名之间用逗号分隔。
- `table_name` 是要查询的表名。
**例如：**<br>
`SELECT * FROM Websites`<br>
`WHERE country='USA' AND alexa>100;`<br>
- 以上示例查询 `Websites` 表中 `country` 列值为 'USA' 且 `alexa` 列值大于 100 的所有列数据。

#### **AND & OR**
`SELECT column1, column2, ...`<br>
`FROM table_name`<br>
`WHERE condition1 AND/OR condition2;`<br>
<br>
**说明：**<br>
- `AND` 运算符用于组合多个条件，只有当所有条件都为真时，才返回行。
- `OR` 运算符用于组合多个条件，只要有一个条件为真，就返回行。
- `condition1` 和 `condition2` 是要组合的条件表达式。
- `column1, column2, ...` 是要查询的列名，多个列名之间用逗号分隔。
- `table_name` 是要查询的表名。
**例如：**<br>
`SELECT * FROM Websites`<br>
`WHERE country='USA' AND alexa>100;`<br>
- 以上示例查询 `Websites` 表中 `country` 列值为 'USA' 且 `alexa` 列值大于 100 的所有列数据。

#### **ORDER BY**
`SELECT column1, column2, ...`<br>
`FROM table_name`<br>
`ORDER BY column1, column2, ... ASC/DESC;`<br>
<br>
**说明：**<br>
- `ORDER BY` 子句用于对查询结果进行排序。
- `column1, column2, ...` 是要排序的列名，多个列名之间用逗号分隔。
- `ASC` 表示升序排序（默认），`DESC` 表示降序排序。
- `table_name` 是要查询的表名。
**例如：**<br>
`SELECT * FROM Websites`<br>
`ORDER BY name ASC;`<br>
- 以上示例查询 `Websites` 表中的所有列数据，并按 `name` 列进行升序排序。

#### **INSERT INTO**
`INSERT INTO table_name (column1, column2, ...)`<br>
`VALUES (value1, value2, ...);`<br>
<br>
**说明：**<br>
- `INSERT INTO` 语句用于向数据库表中插入新的行数据。
- `table_name` 是要插入数据的表名。
- `column1, column2, ...` 是要插入数据的列名，多个列名之间用逗号分隔。
- `value1, value2, ...` 是要插入的具体数值，多个数值之间用逗号分隔。
**例如：**<br>
`INSERT INTO Websites (name, url, alexa, country)`<br>
`VALUES ('Google', 'https://www.google.com/', 1, 'USA');`<br>
- 以上示例向 `Websites` 表中插入了一行数据，包含 `name`、`url`、`alexa` 和 `country` 列的具体数值。

#### **UPDATE**
`UPDATE table_name`<br>
`SET column1=value1, column2=value2, ...`<br>
`WHERE condition;`<br>
<br>
**说明：**<br>
- `UPDATE` 语句用于更新数据库表中的数据。
- `table_name` 是要更新数据的表名。
- `column1=value1, column2=value2, ...` 是要更新的列名和对应数值，多个列名和数值之间用逗号分隔。
- `WHERE` 子句用于指定要更新的行，只有符合条件的行才会被更新。
**例如：**<br>
`UPDATE Websites`<br>
`SET name='Google LLC', url='https://www.google.com/'`<br>
`WHERE name='Google';`<br>
- 以上示例将 `Websites` 表中 `name` 列值为 'Google' 的行的 `name` 和 `url` 列值更新为 'Google LLC' 和 'https://www.google.com/'。

#### **DELETE**
`DELETE FROM table_name`<br>
`WHERE condition;`<br>
<br>
**说明：**<br>
- `DELETE FROM` 语句用于从数据库表中删除行数据。
- `table_name` 是要删除数据的表名。
- `WHERE` 子句用于指定要删除的行，只有符合条件的行才会被删除。
**例如：**<br>
`DELETE FROM Websites`<br>
`WHERE name='Google LLC';`<br>
- 以上示例从 `Websites` 表中删除了 `name` 列值为 'Google LLC' 的行。

<!-- tabs:end -->

### 高级查询

<!-- tabs:start -->

#### **TOP**
`SELECT TOP number|percent column1, column2, ...`<br>
`FROM table_name;`<br>
<br>
**说明：**<br>
- `SELECT TOP` 语句用于查询数据库表中的前几行数据。
- `number` 是要查询的行数，`percent` 是要查询的行数占比（百分比）。
- `column1, column2, ...` 是要查询的列名，多个列名之间用逗号分隔。
- `table_name` 是要查询的表名。
**例如：**<br>
`SELECT TOP 5 * FROM Websites;`<br>
- 以上示例查询 `Websites` 表中的前 5 行数据。

#### **LIMIT**
`SELECT column1, column2, ...`<br>
`FROM table_name`<br>
`LIMIT number;`<br>
<br>
**说明：**<br>
- `SELECT LIMIT` 语句用于查询数据库表中的前几行数据。
- `number` 是要查询的行数。
- `column1, column2, ...` 是要查询的列名，多个列名之间用逗号分隔。
- `table_name` 是要查询的表名。
**例如：**<br>
`SELECT * FROM Websites`<br>
`LIMIT 5;`<br>
- 以上示例查询 `Websites` 表中的前 5 行数据。

#### **ROWNUM**
`SELECT column1, column2, ...`<br>
`FROM table_name`<br>
`WHERE ROWNUM <= number;`<br>
<br>
**说明：**<br>
- `SELECT ROWNUM` 语句用于查询数据库表中的前几行数据。
- `number` 是要查询的行数。
- `column1, column2, ...` 是要查询的列名，多个列名之间用逗号分隔。
- `table_name` 是要查询的表名。
**例如：**<br>
`SELECT * FROM Websites`<br>
`WHERE ROWNUM <= 5;`<br>
- 以上示例查询 `Websites` 表中的前 5 行数据。

#### **LIKE**
`SELECT column1, column2, ...`<br>
`FROM table_name`<br>
`WHERE column LIKE pattern;`<br>
<br>
**说明：**<br>
- `SELECT LIKE` 语句用于查询数据库表中符合指定模式的行数据。
- `column` 是要查询的列名。
- `pattern` 是要匹配的模式，包含通配符 `%`（表示任意字符序列）和 `_`（表示任意单个字符）。
- `table_name` 是要查询的表名。
**例如：**<br>
`SELECT * FROM Websites`<br>
`WHERE name LIKE '%oo%';`<br>
- 以上示例查询 `Websites` 表中 `name` 列值包含 'oo' 的所有列数据。<br>

> [!TIP]
> **通配符**<br>
> - `%` 表示任意字符序列（包括空字符串）。<br>
> - `_` 表示任意单个字符。<br>
> - `[charlist]` 字符列中的任何单一字符。（LIKE '[a-z]%'）<br>
> - `[^charlist]` 或 `[!charlist]` 不在字符列中的任何单一字符。<br>

#### **IN**
`SELECT column1, column2, ...`<br>
`FROM table_name`<br>
`WHERE column IN (value1, value2, ...);`<br>
<br>
**说明：**<br>
- `SELECT IN` 语句用于查询数据库表中符合指定值列表的行数据。
- `column` 是要查询的列名。
- `value1, value2, ...` 是要匹配的值列表，多个值之间用逗号分隔。
- `table_name` 是要查询的表名。
**例如：**<br>
`SELECT * FROM Websites`<br>
`WHERE country IN ('USA', 'CANADA');`<br>
- 以上示例查询 `Websites` 表中 `country` 列值为 'USA' 或 'CANADA' 的所有列数据。

#### **BETWEEN**
`SELECT column1, column2, ...`<br>
`FROM table_name`<br>
`WHERE column BETWEEN value1 AND value2;`<br>
<br>
**说明：**<br>
- `SELECT BETWEEN` 语句用于查询数据库表中符合指定范围的行数据。
- `column` 是要查询的列名。
- `value1` 和 `value2` 是要匹配的范围值，`value1` 必须小于等于 `value2`。
- `table_name` 是要查询的表名。
**例如：**<br>
`SELECT * FROM Websites`<br>
`WHERE id BETWEEN 1 AND 5;`<br>
- 以上示例查询 `Websites` 表中 `id` 列值在 1 到 5 之间的所有列数据。

#### **AS <span class="tab-badge-blue">别名</span>**
`SELECT column1 AS alias1, column2 AS alias2, ...`<br>
`FROM table_name;`<br>
<br>
**说明：**<br>
- `SELECT AS` 语句用于为查询结果中的列指定别名。
- `column1, column2, ...` 是要查询的列名。
- `alias1, alias2, ...` 是为列指定的别名，多个别名之间用逗号分隔。
- `table_name` 是要查询的表名。
**例如：**<br>
`SELECT name AS website_name, url AS website_url FROM Websites;`<br>
- 以上示例查询 `Websites` 表中 `name` 列值为 'website_name'，`url` 列值为 'website_url' 的所有列数据。

#### **JOIN <span class="tab-badge-blue">连接</span>**
`SELECT column1, column2, ...`<br>
`FROM table1`<br>
`JOIN table2`<br>
`ON table1.column = table2.column;`<br>
<br>
**说明：**<br>
- `SELECT JOIN` 语句用于查询数据库表中符合指定条件的行数据。
- `column1, column2, ...` 是要查询的列名，多个列名之间用逗号分隔。
- `table1` 和 `table2` 是要查询的表名。
- `table1.column` 和 `table2.column` 是要匹配的列名，用于指定连接条件。
**例如：**<br>
`SELECT Websites.name, Websites.url, Users.name, Users.email FROM Websites`<br>
`JOIN Users`<br>
`ON Websites.user_id = Users.id;`<br>
- 以上示例查询 `Websites` 表和 `Users` 表中符合连接条件的所有列数据。

> [!TIP]
> - `INNER JOIN` **内连接**（只返回符合连接条件的行数据）<br>
> - `LEFT JOIN` **左连接**（返回左表所有行数据，符合连接条件的右表行数据）<br>
> - `RIGHT JOIN` **右连接**（返回右表所有行数据，符合连接条件的左表行数据）<br>
> - `FULL OUTER JOIN` **并集**（返回左表和右表所有行数据，符合连接条件的行数据）

#### **UNION**
`SELECT column1, column2, ... FROM table1`<br>
`UNION`<br>
`SELECT column1, column2, ... FROM table2;`<br>
<br>
**说明：**<br>
- `SELECT UNION` 语句用于查询数据库表中符合指定条件的行数据。
- `column1, column2, ...` 是要查询的列名，多个列名之间用逗号分隔。
- `table1` 和 `table2` 是要查询的表名。
**例如：**<br>
`SELECT Websites.name, Websites.url FROM Websites`<br>
`UNION`<br>
`SELECT Users.name, Users.email FROM Users;`<br>
- 以上示例查询 `Websites` 表和 `Users` 表中符合连接条件的所有列数据。<br>

> [!TIP]
> UNION ALL 选取所有、重复的值。

#### **INTO**
`SELECT column1, column2, ... `<br>
`INTO new_table FROM table_name;`<br>
<br>
**说明：**<br>
- `SELECT INTO` 语句用于将查询结果存储到新表中。
- `column1, column2, ...` 是要查询的列名，多个列名之间用逗号分隔。
- `new_table` 是要创建的新表名。
- `table_name` 是要查询的表名。
**例如：**<br>
`SELECT Websites.name, Websites.url INTO Websites_backup FROM Websites;`<br>
- 以上示例查询 `Websites` 表中 `name` 列值和 `url` 列值，将结果存储到新表 `Websites_backup` 中。

> [!ATTENTION]
> MySQL 数据库不支持 SELECT ... INTO 语句，但支持 INSERT INTO ... SELECT 。<br>
> 当然你可以使用以下语句来拷贝表结构及数据：<br>
> `CREATE TABLE new_table`<br>
> `AS`<br>
> `SELECT * FROM table_name`

#### **INSERT INTO SELECT**
`INSERT INTO new_table (column1, column2, ...) `<br>
`SELECT column1, column2, ... FROM table_name;`<br>
<br>
**说明：**<br>
- `INSERT INTO SELECT` 语句用于将查询结果插入到新表中。
- `column1, column2, ...` 是要查询的列名，多个列名之间用逗号分隔。
- `new_table` 是要创建的新表名。
- `table_name` 是要查询的表名。
**例如：**<br>
`INSERT INTO Websites_backup (name, url) `<br>
`SELECT name, url FROM Websites;`<br>
- 以上示例查询 `Websites` 表中 `name` 列值和 `url` 列值，将结果插入到新表 `Websites_backup` 中。

#### **CREATE DATABASE**
`CREATE DATABASE database_name;`<br>
<br>
**说明：**<br>
- `CREATE DATABASE` 语句用于创建新的数据库。
- `database_name` 是要创建的数据库名。
**例如：**<br>
`CREATE DATABASE mydatabase;`<br>
- 以上示例创建名为 `mydatabase` 的新数据库。

#### **CREATE TABLE**
`CREATE TABLE table_name `<br>
`(`<br>
`column1 datatype, `<br>
`column2 datatype, `<br>
`...`<br>
`);`<br>
<br>
**说明：**<br>
- `CREATE TABLE` 语句用于创建新的数据库表。
- `table_name` 是要创建的表名。
- `column1, column2, ...` 是要创建的列名，多个列名之间用逗号分隔。
- `datatype` 是要创建的列的数据类型。
**例如：**<br>
`CREATE TABLE Websites (id INT PRIMARY KEY, name VARCHAR(255), url VARCHAR(255));`<br>
- 以上示例创建名为 `Websites` 的新数据库表，包含 `id`、`name` 和 `url` 三列。<br>

> [!TIP]
> **datatype**<br>
> 数据类型用于定义数据库表中列的数据类型。<br>
> 常用的数据类型有：<br>
> - `INT` 整数类型
> - `VARCHAR(n)` 可变长度字符串类型，`n` 是字符串最大长度
> - `DATE` 日期类型
> - `DATETIME` 日期时间类型
> - `FLOAT` 单精度浮点数类型
> - `DOUBLE` 双精度浮点数类型
> - `TEXT` 长文本类型

#### **Constraints <span class="tab-badge-blue">约束</span>**
`CREATE TABLE table_name `<br>
`(`<br>
`column1 datatype constraint_name, `<br>
`column2 datatype constraint_name, `<br>
`...`<br>
`);`<br>
<br>
**说明：**<br>
- `CREATE TABLE` 语句用于创建新的数据库表。
- `table_name` 是要创建的表名。
- `column1, column2, ...` 是要创建的列名，多个列名之间用逗号分隔。
- `datatype` 是要创建的列的数据类型。
- `constraint_name` 是要创建的列的约束名。
**例如：**<br>
`CREATE TABLE Websites (id INT PRIMARY KEY, name VARCHAR(255) NOT NULL, url VARCHAR(255) UNIQUE);`<br>
- 以上示例创建名为 `Websites` 的新数据库表，包含 `id`、`name` 和 `url` 三列。<br>
- `id` 列是主键约束，确保每一行数据的 `id` 值是唯一的。<br>
- `name` 列是非空约束，确保每一行数据的 `name` 值不能为空。<br>
- `url` 列是唯一约束，确保每一行数据的 `url` 值是唯一的。<br>

> [!TIP]
> **constraint_name**<br>
> - 约束用于定义数据库表中列的规则和限制。
> - 常用的约束有：<br>
> - `NOT NULL` 非空约束，用于确保列中的值不能为空。
> - `UNIQUE` 唯一约束，用于确保列中的值是唯一的。
> - `PRIMARY KEY` 主键约束，用于唯一标识表中的每一行数据。
> - `FOREIGN KEY` 外键约束，用于建立表与表之间的关联关系。
> - `CHECK` 检查约束，用于确保列中的值满足指定的条件。
> - `DEFAULT` 默认值约束，用于为列指定默认值。
> - `INDEX` 索引约束，用于提高查询效率。

#### **CREATE INDEX <span class="tab-badge-blue">索引</span>**
`CREATE INDEX index_name `<br>
`ON table_name (column1, column2, ...);`<br>
<br>
**说明：**<br>
- `CREATE INDEX` 语句用于创建数据库表的索引。
- `index_name` 是要创建的索引名。
- `table_name` 是要创建索引的表名。
- `column1, column2, ...` 是要创建索引的列名，多个列名之间用逗号分隔。
**例如：**<br>
`CREATE INDEX idx_name ON Websites (name);`<br>
- 以上示例创建名为 `idx_name` 的索引，用于加速查询 `Websites` 表中 `name` 列的操作。<br>
`CREATE UNIQUE idx_name ON Websites (name, url);`<br>
- 以上示例创建名为 `idx_name` 的**唯一索引**，唯一索引确保每一行数据的 `name` 值和 `url` 值是唯一的。<br> 

> [!TIP]
> 索引可以提高查询效率，但也会增加数据库的存储空间和维护成本。<br>
> 因此，在创建索引时需要权衡利弊，根据实际情况选择是否创建索引。

#### **DROP <span class="tab-badge-blue">删除</span>**
`DROP INDEX [IF EXISTS] index_name ON table_name;`<br>
`DROP TABLE [IF EXISTS] TABLE_NAME;`<br>
`DROP DATABASE [IF EXISTS] database_name;`<br>
<br>
**说明：**<br>
- `DROP INDEX` 语句用于删除数据库表的索引。
- `DROP TABLE` 语句用于删除数据库表。
- `DROP DATABASE` 语句用于删除数据库。
- `IF EXISTS` 是可选子句，用于在索引不存在时避免错误。
- `index_name` 是要删除的索引名。
- `table_name` 是要删除索引的表名。
**例如：**<br>
`DROP INDEX IF EXISTS idx_name ON Websites;`<br>
- 以上示例删除名为 `idx_name` 的索引，从 `Websites` 表中移除该索引。<br>

> [!TIP]
> **TRUNCATE TABLE**<br>
> `TRUNCATE TABLE table_name;`<br>
> - 仅删除表内的数据，但并不删除表本身。

#### **ALTER TABLE <span class="tab-badge-blue">增删改</span>**
`ALTER TABLE table_name `<br>
`ADD column_name datatype;`<br>
`DROP COLUMN column_name;`<br>
`MODIFY column_name datatype;`<br>
<br>
**说明：**<br>
- `ALTER TABLE` 语句用于修改数据库表的结构。
- `table_name` 是要修改的表名。
- `column_name` 是要添加、删除或修改的列名。
- `datatype` 是要添加或修改的列的数据类型。
**例如：**<br>
`ALTER TABLE Websites ADD email VARCHAR(255);`<br>
- 以上示例在 `Websites` 表中添加名为 `email` 的新列，数据类型为 `VARCHAR(255)`。<br>
`ALTER TABLE Websites DROP COLUMN email;`<br>
- 以上示例从 `Websites` 表中删除名为 `email` 的列。<br>
`ALTER TABLE Websites MODIFY name VARCHAR(50);`<br>
- 以上示例将 `Websites` 表中 `name` 列的数据类型修改为 `VARCHAR(50)`。

#### **AUTO INCREMENT <span class="tab-badge-blue">自动递增</span>**
`CREATE TABLE table_name (`<br>
`column1 datatype AUTO_INCREMENT,`<br>
`column2 datatype,`<br>
 `...`<br>
`);`<br>
<br>
**说明：**<br>
- `AUTO_INCREMENT` 约束用于为列自动生成唯一的递增值。
- `table_name` 是要修改的表名。
- `column_name` 是要添加自动递增约束的列名。
- `datatype` 是要添加自动递增约束的列的数据类型。
**例如：**<br>
`ALTER TABLE Websites MODIFY id INT AUTO_INCREMENT;`<br>
- 以上示例将 `Websites` 表中 `id` 列添加自动递增约束，确保每一行数据的 `id` 值是唯一的递增值。

#### **CREATE Views <span class="tab-badge-blue">视图</span>**
`CREATE VIEW view_name AS `<br>
`SELECT column1, column2, `<br>
`... `<br>
`FROM table_name `<br>
`WHERE condition;`<br>
<br>
**说明：**<br>
- `CREATE VIEW` 语句用于创建数据库视图。
- `view_name` 是要创建的视图名。
- `column1, column2, ...` 是要包含在视图中的列名，多个列名之间用逗号分隔。
- `table_name` 是要创建视图的基础表名。
- `condition` 是可选的筛选条件，用于限制视图中包含的数据行。
**例如：**<br>
`CREATE VIEW v_Websites AS SELECT id, name, url FROM Websites;`<br>
- 以上示例创建名为 `v_Websites` 的视图，包含 `Websites` 表中的 `id`、`name` 和 `url` 三列。<br>
`CREATE VIEW v_Websites_Email AS SELECT id, name, url, email FROM Websites WHERE email IS NOT NULL;`<br>
- 以上示例创建名为 `v_Websites_Email` 的视图，包含 `Websites` 表中 `email` 列不为空的行，包含 `id`、`name`、`url` 和 `email` 四列。<br>
> [!TIP]
> 更新视图 <br>
> `UPDATE table_name SET column1 = value1, column2 = value2, ... WHERE condition;` <br>
> 撤销视图 <br>
> `DROP VIEW [IF EXISTS] view_name;`

#### **Date <span class="tab-badge-blue">日期</span>**
**Date 函数：**<br>
- `NOW()`：返回当前日期和时间。
- `CURDATE()`：返回当前日期。
- `CURTIME()`：返回当前时间。
- `DATE(date)`：返回日期部分，不包含时间。
- `YEAR(date)`：返回日期的年份部分。
- `MONTH(date)`：返回日期的月份部分。
- `HOUR(time)`：返回时间的小时部分。
- `MINUTE(time)`：返回时间的分钟部分。
- `SECOND(time)`：返回时间的秒部分。
- `EXTRACT(unit FROM date)`：从日期中提取指定的单位，如年、月、日、时、分、秒等。
- `DATE_ADD(date, INTERVAL value unit)`：在日期上添加指定的时间间隔。
- `DATE_SUB(date, INTERVAL value unit)`：在日期上减去指定的时间间隔。
- `DATEDIFF(date1, date2)`：计算两个日期之间的天数差。
- `DATE_FORMAT(date, format)`：将日期格式化为指定的字符串格式。

#### **NULL <span class="tab-badge-blue">空值</span>**
**NULL 函数：**<br>
- `IS NULL`：检查列是否为空值。
- `IS NOT NULL`：检查列是否不为空值。
- `COALESCE(value1, value2, ...)`：返回第一个非空值。
- `NULLIF(value1, value2)`：如果两个值相等，则返回 NULL，否则返回第一个值。

<!-- tabs:end -->

### 数据类型（MySQL）

+ 通用数据类型 +

  - `CHARACTER(n)`	字符/字符串。固定长度 n。
  - `VARCHAR(n)` 或
  - `CHARACTER VARYING(n)`	字符/字符串。可变长度。最大长度 n。
  - `BINARY(n)`	二进制串。固定长度 n。
  - `BOOLEAN`	存储 TRUE 或 FALSE 值
  - `VARBINARY(n)` 或
  - `BINARY VARYING(n)`	二进制串。可变长度。最大长度 n。
  - `INTEGER(p)`	整数值（没有小数点）。精度 p。
  - `SMALLINT`	整数值（没有小数点）。精度 5。
  - `INTEGER`	整数值（没有小数点）。精度 10。
  - `BIGINT`	整数值（没有小数点）。精度 19。
  - `DECIMAL(p,s)`	精确数值，精度 p，小数点后位数 s。例如：decimal(5,2) 是一个小数点前有 3 位数，小数点后有 2 位数的数字。
  - `NUMERIC(p,s)`	精确数值，精度 p，小数点后位数 s。（与 DECIMAL 相同）
  - `FLOAT(p)`	近似数值，尾数精度 p。一个采用以 10 为基数的指数计数法的浮点数。该类型的 size 参数由一个指定最小精度的单一数字组成。
  - `REAL`	近似数值，尾数精度 7。
  - `FLOAT`	近似数值，尾数精度 16。
  - `DOUBLE PRECISION`	近似数值，尾数精度 16。
  - `DATE`	存储年、月、日的值。
  - `TIME`	存储小时、分、秒的值。
  - `TIMESTAMP`	存储年、月、日、小时、分、秒的值。
  - `INTERVAL`	由一些整数字段组成，代表一段时间，取决于区间的类型。
  - `ARRAY`	元素的固定长度的有序集合
  - `MULTISET`	元素的可变长度的无序集合
  - `XML`	存储 XML 数据

+ 数据库的数据类型：Text 类型 +

  - `CHAR(size)`	保存固定长度的字符串（可包含字母、数字以及特殊字符）。在括号中指定字符串的长度。最多 255 个字符。
  - `VARCHAR(size)`	保存可变长度的字符串（可包含字母、数字以及特殊字符）。在括号中指定字符串的最大长度。最多 255 个字符。注释：如果值的长度大于 255，则被转换为 TEXT 类型。
  - `TINYTEXT`	存放最大长度为 255 个字符的字符串。
  - `TEXT`	存放最大长度为 65,535 个字符的字符串。
  - `BLOB`	用于 BLOBs（Binary Large OBjects）。存放最多 65,535 字节的数据。
  - `MEDIUMTEXT`	存放最大长度为 16,777,215 个字符的字符串。
  - `MEDIUMBLOB`	用于 BLOBs（Binary Large OBjects）。存放最多 16,777,215 字节的数据。
  - `LONGTEXT`	存放最大长度为 4,294,967,295 个字符的字符串。
  - `LONGBLOB`	用于 BLOBs (Binary Large OBjects)。存放最多 4,294,967,295 字节的数据。
  - `ENUM(x,y,z,etc.)`	允许您输入可能值的列表。可以在 ENUM 列表中列出最大 65535 个值。如果列表中不存在插入的值，则插入空值。注释：这些值是按照您输入的顺序排序的。可以按照此格式输入可能的值： ENUM('X','Y','Z')
  - `SET(x,y,z,etc.)`	与 ENUM 类似，不同的是，SET 最多只能包含 64 个列表项且 SET 可存储一个以上的选择。

+ 数据库的数据类型：Number 类型 +

  - `TINYINT(size)`	带符号-128到127 ，无符号0到255。 size 默认为 4。
  - `SMALLINT(size)`	带符号范围-32768到32767，无符号0到65535, size 默认为 6。
  - `MEDIUMINT(size)`	带符号范围-8388608到8388607，无符号的范围是0到16777215。 size 默认为9
  - `INT(size)`	带符号范围-2147483648到2147483647，无符号的范围是0到4294967295。 size 默认为 11。
  - `BIGINT(size)`	带符号的范围是-9223372036854775808到9223372036854775807，无符号的范围是0到18446744073709551615。size 默认为 20。
  - `FLOAT(size,d)`	带有浮动小数点的小数字。在 size 参数中规定显示最大位数。在 d 参数中规定小数点右侧的最大位数。
  - `DOUBLE(size,d)`	带有浮动小数点的大数字。在 size 参数中规显示定最大位数。在 d 参数中规定小数点右侧的最大位数。
  - `DECIMAL(size,d)`	作为字符串存储的 DOUBLE 类型，允许固定的小数点。在 size 参数中规定显示最大位数。在 d 参数中规定小数点右侧的最大位数。

  + 数据库的数据类型：Date 类型 +

  - `DATE()`	日期。格式：YYYY-MM-DD 注释：支持的范围是从 '1000-01-01' 到 '9999-12-31'
  - `DATETIME()`	*日期和时间的组合。格式：YYYY-MM-DD HH:MM:SS 注释：支持的范围是从 '1000-01-01 00:00:00' 到 '9999-12-31 23:59:59'
  - `TIMESTAMP()`	*时间戳。TIMESTAMP 值使用 Unix 纪元('1970-01-01 00:00:00' UTC) 至今的秒数来存储。格式：YYYY-MM-DD HH:MM:SS  注释：支持的范围是从 '1970-01-01 00:00:01' UTC 到 '2038-01-09 03:14:07' UTC
  - `TIME()`	时间。格式：HH:MM:SS 注释：支持的范围是从 '-838:59:59' 到 '838:59:59'
  - `YEAR()`	2 位或 4 位格式的年。 注释：4 位格式所允许的值：1901 到 2155。2 位格式所允许的值：70 到 69，表示从 1970 到 2069。