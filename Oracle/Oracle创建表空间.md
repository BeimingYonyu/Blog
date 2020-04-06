# Oracle 创建表空间

>  1.创建临时表空间

```
create temporary tablespace xing_temp
tempfile 'D:\oracledata\xing_temp.dbf'
size 50m 
autoextend on 
next 50m maxsize 20480m 
extent management local; 

```

> 2.创建数据表空间

```
create tablespace xing_data 
logging    /*logging 是对象的属性，创建数据库对象时，oracle 将日志信息记录到练级重做日志文件中。代表空间类型为永久型 */
datafile 'D:\oracledata\xing_data.dbf'
size 50m 
autoextend on       /*autoextend on    表空间大小不够用时自动扩展*/
next 50m maxsize 20480m    　/*next 50m 自动扩展增量为50MB */
extent management local;       /*extent management local   代表管理方式为本地*/

```

> 3.创建用户并指定表空间

```
create user xing identified by yuhang 
default tablespace xing_temp 
temporary tablespace xing_data; 

```

> 4.给用户授权

```grant connect,resource,dba to xing;


```