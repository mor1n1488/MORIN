## честноне помнюкакая это работа.09.23
![image](https://github.com/mor1n1488/MORIN/assets/144114975/1a32149e-6f7e-4e41-828e-12a11e045b37)
![image](https://github.com/mor1n1488/MORIN/assets/144114975/fe1418f4-96c5-4847-8655-63a803e40c38)
![image](https://github.com/mor1n1488/MORIN/assets/144114975/0d57fd42-bf14-499f-a838-5836004178e9)
![image](https://github.com/mor1n1488/MORIN/assets/144114975/83c42d07-f9d4-4f8e-97cf-66da778bc5cf)
![image](https://github.com/mor1n1488/MORIN/assets/144114975/4035844e-6971-4100-867e-fab3608c3966)
![image](https://github.com/mor1n1488/MORIN/assets/144114975/36d3c60b-0df6-414f-ac98-74904f1221d0)






## 26.09.23
--1--
```sql
select * from students;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/ce38711c-e4d6-41ec-b022-56abe51bc4d5)

--2--
```sql
select firstname, lastname
from students
where age > 21;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/83f68ef0-30e8-4689-95a2-cbec7e028df7)

--3--
```sql
select coursename from courses;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/1f272ef9-a40f-4f71-9d94-3bc6c26288b5)

--4--
```sql
select firstname, lastname from students
join studentcourses on studentcourses.studentid = students.studentid
where courseid = (select courseid from courses where coursename = 'Математика');
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/84f97b8a-5c6f-4649-8f34-48543efee0de)

--5--
```sql
select firstname, lastname from students
join studentcourses on studentcourses.studentid = students.studentid
where courseid = (select courseid from courses where coursename = 'История') and age = 20;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/e9b0091b-f2d6-4359-ad38-e420f0309037)

--6--
```sql
select coursename, 
(select count(studentid) 
from studentcourses 
where c.courseid = studentcourses.courseid) 
from courses c;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/d0eedd30-b64b-4c9f-9f15-bd37430b66df)

--7--
```sql
select avg(age) 
as avg_age 
from students;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/aca7b15f-d034-43bb-95cc-9f226618377b)

--8--
```sql
select firstname, lastname,
studentid from students
where studentid 
not in (select studentid from studentcourses);
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/2c8e0c4a-e132-4c38-8712-fbe8e7625380)

--9--
```sql
select coursename, (select count(studentid) 
from studentcourses 
where c.courseid = studentcourses.courseid) 
from courses c;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/41e01334-40d5-40e0-996c-1f99cde1936d)

--10--
```sql
select firstname, lastname from students
join studentcourses on studentcourses.studentid = students.studentid
where courseid = (select courseid from courses where coursename = 'Биология') and age >= 22;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/329a318b-de02-46be-8e0e-95a0c9c45e9c)


## к сожалению не помню.09.23

--1--
```sql
SELECT * FROM person, pizzeria
ORDER BY person.id, pizzeria.id
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/852f6dcd-ded5-4d15-916f-f598dd70adfb)

--2--
```sql
SELECT person_visits.visit_date AS action_date, person.name
FROM person_visits, person
WHERE person_visits.visit_date
IN (SELECT order_date FROM person_order)
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/75123a0c-bdfc-4969-b574-05ba7caeb7d8)

--3--
```sql
SELECT order_date, (person.name  ' (age: '  person.age || ')') AS person_info
FROM person_order
JOIN person
ON person_order.person_id = person.id
ORDER BY order_date, person_info
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/5bdecffe-798f-4985-b36d-4984dc783188)

--4--
```sql
SELECT order_date, (person.name  ' (age: '  person.age || ')') AS person_info FROM person_order
NATURAL JOIN person
ORDER BY order_date, person_info
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/850e51d8-2633-4b22-9b12-814db5cc630c)

--5--
```sql
SELECT pizzeria.name
FROM pizzeria
WHERE pizzeria.id
NOT IN (SELECT pizzeria_id FROM person_visits);
SELECT pizzeria.name
FROM pizzeria
WHERE NOT EXISTS (SELECT pizzeria_id FROM person_visits WHERE pizzeria_id = pizzeria.id);
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/701b6c09-2fcf-4ad4-8c10-0dc2f79e6c8b)

--6--
```sql
SELECT person.name AS person_name, menu.pizza_name, pizzeria.name AS pizzeria_name FROM person, pizzeria
JOIN menu ON pizzeria.id = menu.pizzeria_id
ORDER BY person_name, menu.pizza_name, pizzeria_name;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/c5efde12-5df2-4fb7-b999-64fc3c7878cc)
