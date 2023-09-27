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
