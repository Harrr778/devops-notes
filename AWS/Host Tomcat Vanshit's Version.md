.............................................Deploying Application..........................

1.Create an instance by using ec2-service and create database by RDS service.
2.Create custom security group by adding SSH, custom tcp 8080 , for maria db add a port custom tcp 3306.
3.Add this Security group to EC2 instance and Database instance.
4.Login to instance.
5.Search tomcat 9 on google and Download its zip file.
6.Use curl -O https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.97/bin/apache-tomcat-9.0.97.zip.
7.unzip it
8. Install java-17 package:-
yum install java-17 -y
9.Change directory :- cd apache-tomcat-9.0.97/bin
10.bash catalina.sh start
11.After this steps search with your instance public ip (For ex, 192.25.26.244:8080)
12.Install git :- yum install git -y
13.Run command :- #git clone https://github.com/Pritam-Khergade/student-ui
14. 2 folders will be downloaded in bin dir.
15.cd student-ui
16.Install maven :- yum install maven -y
17.mvn clean package.
18.After cleaning package u should see build success notification.
19.cd target
20.Rename file :- mv studentapp-2.2-SNAPSHOT.war studentapp.war
21.Move this folder in tomcat/webapps dir :- 
mv studentapp.war /root/apache-tomcat-9.0.97/webapps/
22.Search with public ip u should see a registeration form :- 192.25.26.244:8080/studentapp

.................................................Database part......................................................

1.Install maria db in instance :-  yum install mariadb105 -y
2.Connect to database :- MySQL -h van-db.cduscwa84wb4.ap-south-1.rds.amazonaws.com(endpoint) -u <username-admin> -p <password>
3.After this u will get into database.
4.Create DATABASE with name studentapp and tables,

CREATE DATABASE studentapp;
use studentapp;

```sql
CREATE TABLE if not exists students(student_id INT NOT NULL AUTO_INCREMENT,
	student_name VARCHAR(100) NOT NULL,
    student_addr VARCHAR(100) NOT NULL,
	student_age VARCHAR(3) NOT NULL,
	student_qual VARCHAR(20) NOT NULL,
	student_percent VARCHAR(10) NOT NULL,
	student_year_passed VARCHAR(10) NOT NULL,
	PRIMARY KEY (student_id)
);
```

5.After this exit from database.
6.vim /apache-tomcat-9.0.97/conf/context.xml
7.Write this configuration :- 

```xml
<context>
<Resource name="jdbc/TestDB" auth="Container" type="javax.sql.DataSource"
           maxTotal="500" maxIdle="30" maxWaitMillis="1000"
           username="admin" password="Remote#123" driverClassName="com.mysql.jdbc.Driver"
           url="jdbc:mysql://van-db.cduscwa84wb4.ap-south-1.rds.amazonaws.com:3306/studentapp?useUnicode=yes&amp;characterEncoding=utf8"/>
<context>
```
8.save and exit.
9.After this download mysqlconnector.jar file from this link:- 
https://s3-us-west-2.amazonaws.com/studentapi-cit/mysqlconnector.jar
10.cd apache-tomcat-9.0.97/lib/
11.Download this file in lib folder :- curl -O https://s3-us-west-2.amazonaws.com/studentapi-cit/mysqlconnector.jar
12.After this the data u entered in your form should be stored in this database.










