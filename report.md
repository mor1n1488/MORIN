## 26.09.23
--1--
```sql
select firstname, lastname
from students
where age > 21;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/83f68ef0-30e8-4689-95a2-cbec7e028df7)

--2--
```sql
select coursename from courses;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/1f272ef9-a40f-4f71-9d94-3bc6c26288b5)

--3--
```sql
select firstname, lastname from students
join studentcourses on studentcourses.studentid = students.studentid
where courseid = (select courseid from courses where coursename = 'Математика');
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/84f97b8a-5c6f-4649-8f34-48543efee0de)

--4--
```sql
select firstname, lastname from students
join studentcourses on studentcourses.studentid = students.studentid
where courseid = (select courseid from courses where coursename = 'История') and age = 20;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/e9b0091b-f2d6-4359-ad38-e420f0309037)

--5--
```sql
select coursename, 
(select count(studentid) 
from studentcourses 
where c.courseid = studentcourses.courseid) 
from courses c;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/d0eedd30-b64b-4c9f-9f15-bd37430b66df)

--6--
```sql
select avg(age) 
as avg_age 
from students;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/aca7b15f-d034-43bb-95cc-9f226618377b)

--7--
```sql
select firstname, lastname,
studentid from students
where studentid 
not in (select studentid from studentcourses);
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/2c8e0c4a-e132-4c38-8712-fbe8e7625380)

--8--
```sql
select coursename, (select count(studentid) 
from studentcourses 
where c.courseid = studentcourses.courseid) 
from courses c;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/41e01334-40d5-40e0-996c-1f99cde1936d)
