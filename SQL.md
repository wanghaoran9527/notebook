# MySQL

#### 查看所有数据库

```SQL
SHOW DATABASES [LIKE '数据库名'];
```

#### 使用数据库

```sql
USE <数据库名>;
```

[50道SQL练习题](https://note.youdao.com/web/#/file/recent/markdown/1496E82A186044DD886CC301B503AB0F/)

| student | SId  | Sname | Sage  | Ssex |
| ------- | ---- | ----- | ----- | ---- |
| teacher | TId  | Tname |       |      |
| sc      | SId  | CId   | score |      |
| course  | CId  | Cname | TId   |      |

1. 查询" 01 "课程比" 02 "课程成绩高的学生的信息及课程分数

   思路：

   在sc表中，

   1. 找出有01成绩的同学成绩信息
   2. 找出有02成绩的同学成绩信息
   3. 以上两种结果需要满足一定条件（1）SId要一致【同一人】（2）且01.score>02.score
   4. 以上3步查出的表与student表做拼接

   对应的代码：

   ```sql
   SELECT * FROM sc WHERE sc.CId = '01'
   ```

   ```sql
   SELECT * FROM sc WHERE sc.CId = '02'
   ```

   ```sql
   SELECT * FROM
   (SELECT * FROM sc WHERE sc.CId = '01') AS a,
   (SELECT * FROM sc WHERE sc.CId = '02') AS b
   WHERE a.SId = b.SId AND a.score > b.score;
   ```

   ```sql
   SELECT * FROM student
   INNER JOIN 
   (SELECT a.SId,a.score 01_score, b.score 02_score FROM
   (SELECT * FROM sc WHERE sc.CId = '01') AS a,
   (SELECT * FROM sc WHERE sc.CId = '02') AS b
   WHERE a.SId = b.SId AND a.score > b.score) AS c
   ON student.SId = c.SId;
   ```

   第3步到第4步代码有不同，主要是因为会报错`[Err] 1060 - Duplicate column name 'score'`,原因有两种情况：

    1.1、第一种情况：

   ​       MySQL这个这个错误的一种情况，保存数据时，id重复

   ​    1.2、第二种情况

   ​       多表关联查询，只有一层查询时，id重复不会报错，但是如果再套一层查询，就报这个错误。

    处理方式：需要哪些字段就写出来，该起别名的时候起别名，这样效率也高，也不会出错。

   最终的结果：

   ```sql
   SELECT * FROM student
   INNER JOIN 
   (SELECT a.SId,a.score 01_score, b.score 02_score FROM
   (SELECT * FROM sc WHERE sc.CId = '01') AS a,
   (SELECT * FROM sc WHERE sc.CId = '02') AS b
   WHERE a.SId = b.SId AND a.score > b.score) AS c
   ON student.SId = c.SId;
   ```

1. 1   查询同时存在" 01 "课程和" 02 "课程的情况

   思路和上一题一样。

   ```sql
   SELECT * FROM student
   INNER JOIN 
   (SELECT a.SId,a.score 01_score, b.score 02_score FROM
   (SELECT * FROM sc WHERE sc.CId = '01') AS a,
   (SELECT * FROM sc WHERE sc.CId = '02') AS b
   WHERE a.SId = b.SId) AS c
   ON student.SId = c.SId;
   ```

1. 2 查询存在" 01 "课程但可能不存在" 02 "课程的情况(不存在时显示为 null )

   这一题主要使用left join

   思路：

   1. 找出有01成绩的同学成绩信息
   2. 找出有02成绩的同学成绩信息
   3. 以上2张表做left join操作
   4. 以上3步查出的表与student表做拼接

   第3步代码：

   ```sql
   SELECT a.SId,a.score 01_score, b.score 02_score FROM
   (SELECT * FROM sc WHERE sc.CId = '01') AS a
   LEFT JOIN
   (SELECT * FROM sc WHERE sc.CId = '02') AS b
   ON a.SId = b.SId;
   ```

   最终的结果：

   ```sql
   SELECT * FROM student
   INNER JOIN 
   (SELECT a.SId,a.score 01_score, b.score 02_score FROM
   (SELECT * FROM sc WHERE sc.CId = '01') AS a
   LEFT JOIN
   (SELECT * FROM sc WHERE sc.CId = '02') AS b
   ON a.SId = b.SId) AS c
   ON student.SId = c.SId;
   ```

1. 3 查询不存在" 01 "课程但存在" 02 "课程的情况

   这一题和上一题要求是不同的，上一题是可能不存在" 02 "课程，本题是一定不存在" 01 "课程。

   思路：

   1. 选出一个没有选" 01 "课程同学的表
   2. 在第1步选出的表中选择有" 02 "课程的同学
   3. 与student表做拼接

   第2步代码：

   ```sql
   SELECT * FROM sc
   WHERE sc.SId NOT IN
   (SELECT sc.SId FROM sc WHERE sc.CId = '01')
   AND sc.CId = '02';
   ```

   最终的结果：

   ```sql
   SELECT * FROM student
   INNER JOIN 
   (SELECT * FROM sc
   WHERE sc.SId NOT IN
   (SELECT sc.SId FROM sc WHERE sc.CId = '01')
   AND sc.CId = '02') AS c
   ON student.SId = c.SId;
   ```

   **注意：**一定是NOT IN =，不能是IN ！= ，因为最后要根据sc.SId判断。有这么一种情况，一个同学既选了" 01 "课程又选了" 02 "课程。如果用IN ！= ，无法排除这位同学。

2. 查询平均成绩大于等于 60 分的同学的学生编号和学生姓名和平均成绩

   思路：根据学生编号分组

   注意：为平均成绩起别名

   查询平均成绩大于等于 60 分的代码：

   ```sql
   SELECT sc.SId,AVG(sc.score) 
   FROM sc
   GROUP BY sc.SId
   HAVING AVG(sc.score) >= 60;
   ```

   最终的结果：

   ```sql
   SELECT s.SId, s.Sname, a.avg_score 
   FROM student s
   INNER JOIN 
   (SELECT sc.SId,AVG(sc.score) avg_score 
   FROM sc
   GROUP BY sc.SId
   HAVING AVG(sc.score) >= 60) AS a
   ON s.SId = a.SId;
   ```

3. 查询在 SC 表存在成绩的学生信息

   我给出的答案和网上的答案不同，我的思路：

   1. 查出成绩不为空的SId
   2. 根据第1步查出的SId在student表中查出对应信息，并去重

   最终的结果：

   ```sql
   SELECT DISTINCT * 
   FROM student
   INNER JOIN 
   (SELECT sc.SId
   FROM sc
   WHERE sc.score IS NOT NULL) as a
   ON student.SId = a.SId;
   ```

4. 查询所有同学的学生编号、学生姓名、选课总数、所有课程的总成绩(没成绩的显示为 null )

   这个很简单，我想到的是连接查询，派生表查询，不会显示没选课的学生。

   ```sql
   SELECT  s.SId, s.Sname, a.count_course, a.sum_score
   FROM student s
   LEFT JOIN 
   (SELECT sc.SId,COUNT(DISTINCT sc.CId) count_course,SUM(sc.score) sum_score
   FROM sc
   GROUP BY sc.SId) AS a
   ON s.SId = a.SId;
   ```

   ```sql
   select student.sid, student.sname,r.coursenumber,r.scoresum
   from student,
   (select sc.sid, sum(sc.score) as scoresum, count(sc.cid) as coursenumber from sc 
   group by sc.sid)r
   where student.sid = r.sid;
   ```

4. 1 查有成绩的学生信息

   感觉和第3题问的是一样的。这一题涉及到in和exists的用法。

   ```sql
   select * from student 
   where exists (select sc.sid from sc where student.sid = sc.sid);
   ```

   ```sql
   select * from student
   where student.sid in (select sc.sid from sc);
   ```

   在这种小表中，两种方法的效率都差不多，但是请参考[SQL查询中in和exists的区别分析](https://www.jianshu.com/p/f212527d76ff)
    当表2的记录数量非常大的时候，选用exists比in要高效很多.
    EXISTS用于检查子查询是否至少会返回一行数据，该子查询实际上并不返回任何数据，而是返回值True或False.
    结论：IN()适合B表比A表数据小的情况
    结论：EXISTS()适合B表比A表数据大的情况

5. 查询「李」姓老师的数量

   ```sql
   SELECT COUNT(*)
   FROM teacher
   WHERE Tname LIKE "李%";
   ```

6. 查询学过「张三」老师授课的同学的信息

   自己想的嵌套查询：

   ```sql
   SELECT *
   FROM student
   WHERE student.SId IN
   (SELECT sc.SId
   FROM sc
   WHERE sc.CId IN
   (SELECT c.CId
   FROM course c
   WHERE c.TId IN
   (SELECT t.TId
   FROM teacher t
   WHERE t.Tname = "张三")));
   ```

   给出的多表联合查询：

   ```sql
   select student.*
   from teacher  ,course  ,student,sc
   where teacher.Tname='张三'
   and   teacher.TId=course.TId
   and   course.CId=sc.CId
   and   sc.SId=student.SId
   ```

7. 

