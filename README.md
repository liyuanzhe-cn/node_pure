# small_node_server
这个是项目是用原生的nodejs 搭建的小型服务器，目前还不是跟完善，后续会跟进

1. 先创建数据库（暂时密码使用的是明文）
create database school;
CREATE TABLE `student` (
  `id` int(11) NOT NULL AUTO_INCREMENT COMMENT 'student id',
  `pass` varchar(128) NOT NULL,
  `stu_num` int(11) NOT NULL COMMENT 'student number',
  `name` varchar(32) NOT NULL COMMENT 'student name',
  `age` int(11) NOT NULL COMMENT 'student age',
  `class` int(11) NOT NULL COMMENT 'student class',
  PRIMARY KEY (`id`),
  UNIQUE KEY `table_name_stu_num_uindex` (`stu_num`)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8

insert into student(`stu_num`,`pass`, `name`, `age`,  `class`) value (1,'123', "李沅哲1", 24, 1901);
insert into student(`stu_num`,`pass`, `name`, `age`,  `class`) value (2,'123', "李沅哲2", 24, 1902);
insert into student(`stu_num`,`pass`, `name`, `age`,  `class`) value (3,'123', "李沅哲3", 24, 1903);
insert into student(`stu_num`,`pass`, `name`, `age`,  `class`) value (4,'123', "李沅哲4", 24, 1904);

端口号默认是3306 127.0.01  /dao/dbutil.js 数据库的链接接口文件中可以修改

2. npm install

3.文件夹和文件信息：

#根目录文件
config.js 解析config.conf文件

filterLoader.js 打包所有的拦截器，逐次执行

loader.js 打包所有的业务逻辑

logs.js 记录日志的方法文件

server.conf 服务器配置文件

server.js 服务器主入口文件

#子文件夹
-> dao 数据库操作
dbutil.js 数据库的链接接口文件
studentDao.js 对于学生的操作

-> filter （未登录用户）拦截器
loginFilter.js 对于未登录用户的拦截，让他们只能访问指定的页面

-> log 日志
server.log 服务器日志文件

-> utils 工具箱文件夹

-> page 静态资源

-> services 打包数据库操作
对数据库操作的打包处理

-> web 表单验证等业务逻辑
controllerSet.js 把所有的不需要登录权限的接口进行打包
