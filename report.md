## честно не помню какая это работа.09.23
![image](https://github.com/mor1n1488/MORIN/assets/144114975/1a32149e-6f7e-4e41-828e-12a11e045b37)
![image](https://github.com/mor1n1488/MORIN/assets/144114975/fe1418f4-96c5-4847-8655-63a803e40c38)
![image](https://github.com/mor1n1488/MORIN/assets/144114975/0d57fd42-bf14-499f-a838-5836004178e9)
![image](https://github.com/mor1n1488/MORIN/assets/144114975/83c42d07-f9d4-4f8e-97cf-66da778bc5cf)
![image](https://github.com/mor1n1488/MORIN/assets/144114975/4035844e-6971-4100-867e-fab3608c3966)
![image](https://github.com/mor1n1488/MORIN/assets/144114975/36d3c60b-0df6-414f-ac98-74904f1221d0)


## 26.09.23
--1--
```sql
SELECT * FROM students;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/ce38711c-e4d6-41ec-b022-56abe51bc4d5)

--2--
```sql
SELECT firstname, lastname
FROM students
WHERE age > 21;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/83f68ef0-30e8-4689-95a2-cbec7e028df7)

--3--
```sql
SELECT coursename FROM courses;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/1f272ef9-a40f-4f71-9d94-3bc6c26288b5)

--4--
```sql
SELECT firstname, lastname FROM students
JOIN studentcourses on studentcourses.studentid = students.studentid
WHERE courseid = (select courseid from courses where coursename = 'Математика');
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/84f97b8a-5c6f-4649-8f34-48543efee0de)

--5--
```sql
SELECT firstname, lastname FROM students
JOIN studentcourses on studentcourses.studentid = students.studentid
WHERE courseid = (select courseid from courses where coursename = 'История') and age = 20;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/e9b0091b-f2d6-4359-ad38-e420f0309037)

--6--
```sql
SELECT coursename, 
(SELECT count(studentid) 
FROM studentcourses 
WHERE c.courseid = studentcourses.courseid) 
FROM courses c;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/d0eedd30-b64b-4c9f-9f15-bd37430b66df)

--7--
```sql
SELECT avg(age) 
AS avg_age 
FROM students;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/aca7b15f-d034-43bb-95cc-9f226618377b)

--8--
```sql
SELECT firstname, lastname, studentid FROM students
WHERE studentid not in (select studentid from studentcourses);
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/2c8e0c4a-e132-4c38-8712-fbe8e7625380)

--9--
```sql
SELECT coursename, (select count(studentid) 
FROM studentcourses 
WHERE c.courseid = studentcourses.courseid) 
FROM courses c;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/41e01334-40d5-40e0-996c-1f99cde1936d)

--10--
```sql
SELECT firstname, lastname from students
JOIN studentcourses on studentcourses.studentid = students.studentid
WHERE courseid = (select courseid from courses where coursename = 'Биология') and age >= 22;
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


## задание 4 13.09.23
```sql
SELECT "id", "pizza_name" FROM "menu" UNION
SELECT "id", "name" FROM "person"
ORDER BY "id", "pizza_name";
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/aba4751f-f470-4e43-8ba3-bb56c35c0bd6)

```sql
SELECT "pizza_name" FROM "menu" UNION
SELECT "name" FROM "person"
ORDER BY "pizza_name";
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/2665c5a3-5203-4fe7-bc66-4c39ab6078f9)


## Задание 11.10 (17.10)

--Exercise 00--
```sql
CREATE INDEX idx_menu_pizzeria_id ON menu(pizzeria_id);
CREATE INDEX idx_person_order_person_id ON person_order(person_id);
CREATE INDEX idx_person_order_menu_id ON person_order(menu_id);
CREATE INDEX idx_person_visits_person_id ON person_visits(person_id);
CREATE INDEX idx_person_visits_pizzeria_id ON person_visits(pizzeria_id);
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/ea87f821-ea14-467b-b68b-a512d87f622a)


--Exercise 01--
```sql
SET enable_seqscan = OFF;
EXPLAIN ANALYZE SELECT pizza_name, pizzeria.name AS pizzeria_name FROM menu, pizzeria
WHERE menu.pizzeria_id = pizzeria.id
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/3a1dd5db-d9ae-4e90-93ae-010ad87f4cb4)


--Exercise 02--
```sql
CREATE INDEX idx_person_name ON person(name);
EXPLAIN ANALYZE SELECT UPPER(name) FROM person;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/3bafa71a-fa86-4307-a44c-2b72ab03d068)


--Exercise 03--
```sql
CREATE INDEX idx_person_order_multi ON person_order(person_id, menu_id);
EXPLAIN ANALYZE SELECT person_id, menu_id,order_date FROM person_order
WHERE person_id = 8 AND menu_id = 19;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/7873d0d9-6f64-45a0-8265-69238709fc35)


--Exercise 04--
```sql
CREATE UNIQUE INDEX idx_menu_unique ON menu(pizzeria_id, pizza_name);
EXPLAIN ANALYZE SELECT pizzeria_id, pizza_name FROM menu
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/5a377103-4834-4603-97e9-a04ce948135b)


--Exercise 05--
```sql
CREATE UNIQUE INDEX idx_person_order_order_date ON person_order(person_id, menu_id)
WHERE order_date = '2022-01-01';
EXPLAIN ANALYZE SELECT person_id, menu_id FROM person_order
WHERE order_date = '2022-01-01'
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/64ed5e25-0652-4e98-8d38-3c10b0c269b9)


--Exercise 06--
```sql
CREATE INDEX idx_1 ON pizzeria(id, rating);
EXPLAIN ANALYZE SELECT
  m.pizza_name AS pizza_name,
  max(rating) OVER (PARTITION BY rating ORDER BY rating ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS k
FROM  menu m INNER JOIN pizzeria pz ON m.pizzeria_id = pz.id
ORDER BY 1,2;
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/b03d8a7e-ac1b-449b-bf6a-50a288768e5c)


#  18.10.23
--номер 1-- 
```sql
SELECT cus.first_name, cus.last_name FROM customers cus
JOIN orders ord ON cus.customer_id = ord.customer_id
GROUP BY cus.first_name, cus.last_name, ord.order_date
HAVING COUNT(*) >= 2 AND ord.order_date BETWEEN '2023-07-17' AND '2023-10-17'
ORDER BY 1, 2
```
![image](https://github.com/mor1n1488/MORIN/assets/144114975/ddf4637e-b097-42d1-9cf2-ea242b572357)


--2--
```sql
SELECT AVG(ord.quantity) AS average, prd.category FROM orders ord
JOIN products prd ON prd.product_id = ord.product_id
WHERE price >= 50
GROUP BY prd.category
ORDER BY 2
```
![image](https://github.com/paramka0/db_practice/assets/74873667/0e293520-18b5-41dd-92a4-7fd76dc2b22b)

--3--
```sql
WITH sum_customers AS (
	SELECT ord.customer_id, SUM(prd.price) AS summa FROM orders ord
	JOIN products prd ON prd.product_id = ord.product_id
	GROUP BY ord.customer_id
), avg_sum AS (
	SELECT ord.order_id, ord.customer_id, ord.quantity, SUM(prd.price) AS summa FROM orders ord
	JOIN products prd ON prd.product_id = ord.product_id
	GROUP BY ord.order_id
)

SELECT cus.first_name, cus.last_name, cus.email FROM customers cus
JOIN sum_customers scus ON scus.customer_id = cus.customer_id
JOIN avg_sum asum ON asum.customer_id = cus.customer_id
GROUP BY cus.first_name, cus.last_name, cus.email, scus.summa
HAVING scus.summa > AVG(asum.summa)
```
![image](https://github.com/paramka0/db_practice/assets/74873667/b776ae03-f9a2-4a1c-b7e5-481d97b1abbe)

--4--
```sql
WITH sum_price AS (
	SELECT ord.order_id, ord.customer_id, ord.product_id, ord.quantity, SUM(prd.price) AS summa FROM orders ord
	JOIN products prd ON prd.product_id = ord.product_id
	GROUP BY ord.order_id
	HAVING SUM(prd.price) >= 1000
)

SELECT cus.first_name, cus.last_name FROM customers cus
JOIN sum_price spr ON spr.customer_id = cus.customer_id
JOIN products prd ON prd.product_id = spr.product_id
WHERE category != 'Electronics'
```
![image](https://github.com/paramka0/db_practice/assets/74873667/28270a27-2eac-48fa-b33b-08b022b054cf)

--5--
--6--
```sql
WITH customer_orders AS (
	SELECT * FROM (SELECT ord.customer_id, ord.order_date, row_number() over(partition by ord.customer_id order by ord.order_date DESC) as rn FROM orders ord) cus_ord
	WHERE rn < 3
	
), max_range_order AS (
	SELECT csod.customer_id, (MAX(csod.order_date) - MIN(csod.order_date)) AS order_range FROM customer_orders csod
	GROUP BY 1
)

SELECT cus.first_name, cus.last_name, MAX(mro.order_range) FROM max_range_order mro
JOIN customers cus ON cus.customer_id = mro.customer_id
GROUP BY 1, 2
HAVING MAX(mro.order_range) = (SELECT MAX(mro.order_range) FROM max_range_order mro)
```
![image](https://github.com/paramka0/db_practice/assets/74873667/309f6aa7-090e-4f85-96a3-831630f73463)

--7--
```sql
SELECT cus.first_name, cus.last_name FROM customers cus
LEFT JOIN orders ord ON ord.customer_id = cus.customer_id
WHERE ord.order_date BETWEEN '2023-08-23' AND '2023-10-23'
```
![image](https://github.com/paramka0/db_practice/assets/74873667/8018f072-ded5-45f1-82d4-167a1f358e8d)

--8--
```sql
UPDATE products
SET price = price - (price * 10 / 100)
WHERE category = 'Clothing';

SELECT * FROM products
WHERE category = 'Clothing'
```
![image](https://github.com/paramka0/db_practice/assets/74873667/4d4d1cc1-a26c-4f00-8458-440b54a567e6)

## 01.11.23
![image](https://github.com/paramka0/db_practice/assets/74873667/27e6cfcf-e1a1-40fb-9f53-3dca7c9ea320)

```sql
CREATE TABLE equipment (
id INT PRIMARY KEY,
name VARCHAR(255),
serial_number VARCHAR(255),
description VARCHAR(255),
manufacturer VARCHAR(255)
);

CREATE TABLE client (
client_id INT PRIMARY KEY,
family VARCHAR(50),
address VARCHAR(100),
telephone VARCHAR(20)
);

CREATE TABLE order_ (
order_id INT PRIMARY KEY,
equipment_id INT,
client_id INT,
tab_number_master INT,
order_status_id INT,
execution_code INT
);

CREATE TABLE staff (
tab_number INT PRIMARY KEY,
family VARCHAR(50),
post_cod INT,
passport_series VARCHAR(10),
passport_number VARCHAR(20),
address VARCHAR(100),
telephone VARCHAR(20),
date_accepted DATE
);

CREATE TABLE post (
post_cod INT PRIMARY KEY,
post VARCHAR(50)
);

CREATE TABLE order_status (
order_cod INT PRIMARY KEY,
name VARCHAR(50)
);

CREATE TABLE execution (
execution_code INT PRIMARY KEY,
type_repair VARCHAR(50),
total_cost FLOAT,
date_execution DATE
);

CREATE TABLE execution_components_details (
uniquelid INT PRIMARY KEY,
component_id INT,
component_cost FLOAT,
work_cost FLOAT,
execution_id INT,
discount FLOAT
);
```
# заполнеие таблиц

```sql
INSERT INTO client (client_id, family, address, telephone) 
VALUES ('1', 'Гасанов', 'Ивановская область, город Дмитров, ул. Домодедовская, 66', '+7 (969) 158-15-92'),
('2', 'Функ', 'Калужская область, город Орехово-Зуево, спуск Косиора, 26', '+7 (977) 198-75-39'),
('3', 'Фролова', 'Астраханская область, город Можайск, ул. 1905 года, 56', '+7 (906) 997-96-45'),
('4', 'Панфилов', 'Омская область, город Серпухов, ул. Ломоносова, 01', '+7 (975) 111-33-57'),
('5', 'Артемов', 'Самарская область, город Можайск, проезд Космонавтов, 67', '+7 (907) 542-12-56'),
('6', 'Комаров', 'Брянская область, город Егорьевск, бульвар Ломоносова, 46', '+7 (927) 259-61-53'),
('7', 'Федотова', 'Новосибирская область, город Чехов, пл. Чехова, 55', '+7 (984) 663-22-16'),
('8', 'Семина', 'Ульяновская область, город Луховицы, пер. Космонавтов, 52', '+7 (919) 117-48-33'),
('9', 'Шульгин', 'Волгоградская область, город Дорохово, бульвар Ладыгина, 52', '+7 (941) 802-90-96'),
('10', 'Воронов', 'Нижегородская область, город Пушкино, въезд Ладыгина, 51', '+7 (989) 758-94-41');
```
```sql
INSERT INTO equipment (id, name, serial_number, description, manufacturer) 
VALUES ('1', 'Тележка "Скейт"', '542321', 'Тележка RUSKLAD "Скейт" (400х600) d125мм Скейт 125 выполнена из цельного листового металла. Изделие оснащено четырьмя колесами, оно служит для перевозки пластиковых контейнеров и ящиков.', 'RUSKLAD'),
('2', 'Гидравлическая тележка', '763433', 'Гидравлическая тележка Gigant JHPT2000 подойдет для работы на складах со средней пропускной способностью. Наличие гидравлического узла позволяет перевозить палетированные грузы массой до 2 тонн. Минимальная высота подъема составляет 85 мм, максимальная - 195 мм. Длина вил - 115 см.', 'Gigant'),
('3', 'Тележка грузовая КГМ 200 с литыми колёсами', '756655', 'Тележка RUSKLAD грузовая КГМ 200 с литыми колёсами КГМ 200 литые позволяет быстро и удобно перевозить грузы весом до 150 кг. Изделие обладает платформой, благодаря которой вы с лёгкостью и максимальным комфортом сможете перевозить различные грузы. Оснащена литыми колёсами D 200 мм.', 'RUSKLAD'),
('4', 'Платформенная тележка с сетчатыми бортами', '112433', 'Платформенная тележка с сетчатыми бортами RUSKLAD ТС 2, 600x900 мм, d125 мм ТС 2 125 служит для бережной транспортировки различных грузов и товаров суммарной массой до 300 кг. Полимерное порошковое покрытие устойчиво к влиянию коррозии, что позволяет использовать приспособление на открытом воздухе даже при неблагоприятных погодных условиях.', 'RUSKLAD'),
('5', 'Тележка "Кега 3"', '867343', 'Тележка RUSKLAD "Кега 3" (440x281x1160) грузовая, с пневматическими колёсами d250мм Кега 3 пневмо 250 разработана для перевозки пивных кег или бочонков с квасом. Модель оснащена универсальной осью, на которую также можно установить литые колеса диаметром 250 мм. Предполагает перевозку грузов до 130 кг.', 'RUSKLAD'),
('6', 'Транспортно-роликовая платформа', '987445', 'Транспортно-роликовая платформа EURO-LIFT CRA6 г/п 6 т 00012451 обладает небольшими размерами и предназначена для перемещения грузов. Удобство транспортировки заключается в небольших полиуретановых колесах: они обеспечивают комфортное перемещение с минимальным трением даже при значительной нагрузке. Толщина деталей, надежная сварка, наличие ребер жесткости под платформой делают конструкцию более прочной и качественной.', 'EURO-LIFT'),
('7', 'Самоходный подъемник ножничного типа с питанием от аккумуляторов', '872325', 'Устройства самоходных моделей GROST TOWER представляют собой самоходные сопровождаемые гидравлические подъемники ножничного типа, оснащенные платформой для подъема и опускания грузов и людей с инструментом, сообразно с максимальной высотой подъема и грузоподъемностью. Горизонтальное транспортирование подъемника требует твердых, ровных и гладких полов с уклоном не более 10-15%.', 'Tower Drive'),
('8', 'Тележка Тара', '135436', 'Тележка Тара.ру п/э 600х400 чёрные резиновые колёса, зелёный 08167 выполнена из пластика. Модель используется для внутрицехового и внутрискладского перемещения загруженных или пустых пластиковых ящиков.', 'RUSKLAD'),
('9', 'Тележка для двух баллонов', '765444', 'Тележка RUSKLAD КП 2 представляет собой специализированное оборудование для перевозки баллонов или аналогичных по форме предметов. Ширина тележки обеспечивает возможность перевозки двух баллонов одновременно. Продукт обладает системой ремневой фиксации баллонов.', 'RUSKLAD'),
('10', 'Набор для перемещения мебели', '125636', 'Набор для перемещения мебели PARK в наборе: 4 тележки + домкрат 103935 поможет с легкостью передвинуть мебель в пределах любого помещения, защитить мебель, пол и стены от повреждений.', 'PARK');
SELECT * FROM equipment;
```
```sql
INSERT INTO execution (execution_code, type_repair, total_cost, date_execution) 
VALUES ('1', 'Косметический ремонт', '15000', '20012-02-05'),
('2', 'Капитальный ремонт', '15000', '20021-07-22'),
('3', 'Декорирование', '10000', '2023-10-14'),
('4', 'Ремонт без проблем', '20000', '2018-11-25'),
('5', 'Евроремонт', '75000', '20020-08-13');
SELECT * FROM execution;
```
```sql
INSERT INTO execution_components_details (uniquelid, component_id, component_cost, work_cost, execution_id, discount) 
VALUES ('1', '1', '13500', '15000', '1', '15'),
('2', '2', '11000', '15000', '2', '10'),
('3', '3', '9000', '10000', '3', '25'),
('4', '4', '22000', '25000', '4', '17'),
('5', '5', '65000', '75000', '5', '21');
SELECT * FROM execution_components_details;
```
```sql
INSERT INTO order_ (order_id, equipment_id, client_id, tab_number_master, order_status_id, execution_code) 
VALUES ('546', '1', '542353', '1', '1', '15'),
('653', '2', '655343', '2', '2', '25'),
('234', '3', '135446', '3', '3', '31'),
('122', '4', '766543', '4', '4', '34'),
('654', '5', '325655', '5', '5', '46');
SELECT * FROM order_;
```
```sql
INSERT INTO order_status (order_cod, name) 
VALUES ('1', 'принят'),
('2', 'проектирование'),
('3', 'в работе'),
('4', 'проверка'),
('5', 'готов');
SELECT * FROM order_status;
```
```sql
INSERT INTO post (post_cod, post) 
VALUES ('1', 'архитектор'),
('2', 'инженер-строитель'),
('3', 'технологов'),
('4', 'мастер монтажных и строительных работ'),
('5', 'электросварщик'),
('6', 'заведующий склада'),
('7', 'бригадир'),
('8', 'кладовщик'),
('9', 'комплектовщик'),
('10', 'грузчик');
SELECT * FROM post;
```
```sql
INSERT INTO staff (tab_number, family, post_cod, passport_series, passport_number, address, telephone, date_accepted) 
VALUES ('1', 'Крюков', '2', '4352', '430324', 'Омская область, город Балашиха, пер. Гагарина, 00', '+7 (929) 104-33-26', '2023-09-23'),
('2', 'Артемьев', '5', '6544', '534563', 'Пензенская область, город Кашира, шоссе Будапештсткая, 50', '+7 (929) 207-99-44', '2020-11-12'),
('3', 'Кузнецов', '3', '3254', '32543', 'Астраханская область, город Зарайск, пр. Космонавтов, 79', '+7 (932) 110-35-31', '2023-12-03'),
('4', 'Родионов', '4', '1453', '132433', 'Томская область, город Пушкино, ул. Косиора, 32', '+7 (907) 556-43-97', '2023-07-13'),
('5', 'Евдокимов', '6', '7645', '564321', 'Кировская область, город Павловский Посад, ул. Домодедовская, 46', '+7 (994) 420-75-66', '2023-01-04'),
('6', 'Семёнов', '10', '6453', '453221', 'Смоленская область, город Волоколамск, пл. Ладыгина, 55', '+7 (994) 437-52-69', '2023-04-08'),
('7', 'Лаврентьев', '10', '3253', '654321', 'Амурская область, город Талдом, ул. 1905 года, 73', '+7 (914) 529-81-62', '2022-10-22'),
('8', 'Стрелков', '9', '1214', '654322', 'Пензенская область, город Серебряные Пруды, спуск Славы, 94', '+7 (922) 312-22-75', '2022-07-10'),
('9', 'Самсонов', '8', '6543', '12453', 'Новосибирская область, город Шаховская, пр. Сталина, 54', '+7 (916) 783-26-32', '2023-12-21'),
('10', 'Агафонов', '7', '3254', '764343', 'Волгоградская область, город Серебряные Пруды, бульвар Косиора, 03', '+7 (947) 617-51-35', '2023-07-27');
SELECT * FROM staff;
```
# триггеры

-- тестовый тригер --
```sql
CREATE FUNCTION validate_telephone() RETURNS TRIGGER AS $$
BEGIN
IF NEW.telephone SIMILAR TO '^\+7 (\d{3}) \d{3}-\d{2}-\d{2}$' THEN
RETURN NEW;
ELSE
RAISE EXCEPTION 'Invalid telephone number format';
END IF;
END;
$$
LANGUAGE 'plpgsql';

CREATE TRIGGER check_telephone BEFORE INSERT OR UPDATE ON client FOR EACH ROW EXECUTE FUNCTION validate_telephone();
```
![image](https://github.com/paramka0/db_practice/assets/74873667/20e63a38-2235-40cd-aafb-33b2b94e2b79)

-- Триггер 1: Проверка наличия заказа для каждого сотрудника, принимающего заказы --
```sql
CREATE OR REPLACE FUNCTION check_order_exists()
RETURNS TRIGGER AS $$
BEGIN
    IF (
        SELECT COUNT(*) FROM order_
        WHERE tab_number_master = NEW.tab_number
    ) = 0 THEN
        RAISE EXCEPTION 'There are no orders for this staff member.';
    END IF;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER check_order_exists_trigger
AFTER INSERT OR UPDATE ON staff
FOR EACH ROW
EXECUTE FUNCTION check_order_exists();
```
![image](https://github.com/paramka0/db_practice/assets/74873667/b91c2bda-c1b2-4535-9997-133c9b72747a)

-- Триггер 2: Проверка статуса заказа при обновлении --
```sql
CREATE OR REPLACE FUNCTION check_order_status()
RETURNS TRIGGER AS $$
BEGIN
    IF (
        SELECT order_status_id FROM order_
        WHERE order_id = NEW.order_id
    ) = 4 THEN
        RAISE EXCEPTION 'Cannot update completed order.';
    END IF;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER check_order_status_trigger
BEFORE UPDATE ON order_
FOR EACH ROW
EXECUTE FUNCTION check_order_status();
```
![image](https://github.com/paramka0/db_practice/assets/74873667/c8aca933-98f5-4ef8-8965-3a0da149945b)


-- Триггер 3: Установка кода выполнения при изменении статуса заказа --
```sql
CREATE OR REPLACE FUNCTION set_execution_code()
RETURNS TRIGGER AS $$
BEGIN
    IF (
        OLD.order_status_id <> NEW.order_status_id
    ) THEN
        CASE NEW.order_status_id
            WHEN 1 THEN NEW.execution_code := 15;
            WHEN 2 THEN NEW.execution_code := 25;
            WHEN 3 THEN NEW.execution_code := 31;
            WHEN 4 THEN NEW.execution_code := 34;
            WHEN 5 THEN NEW.execution_code := 46;
        END CASE;
    END IF;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER set_execution_code_trigger
BEFORE UPDATE ON order_
FOR EACH ROW
EXECUTE FUNCTION set_execution_code();
```
- было -
![image](https://github.com/paramka0/db_practice/assets/74873667/321b377d-7628-4677-b80d-01a999aef250)

- стало -
![image](https://github.com/paramka0/db_practice/assets/74873667/087df38a-a606-48da-bd08-f84b13295ead)


-- Триггер 4: Проверка даты принятия уволенного сотрудника --
```sql
CREATE OR REPLACE FUNCTION check_date_accepted()
RETURNS TRIGGER AS $$
BEGIN
    IF (
        SELECT date_accepted FROM staff
        WHERE tab_number = OLD.tab_number
    ) <= CURRENT_DATE THEN
        RAISE EXCEPTION 'The accepted date of a dismissed staff member cannot be in the future.';
    END IF;
    RETURN OLD;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER check_date_accepted_trigger
BEFORE DELETE ON staff
FOR EACH ROW
EXECUTE FUNCTION check_date_accepted();
```
![image](https://github.com/paramka0/db_practice/assets/74873667/5b057a6e-7cca-4f03-94ce-d52eaeefc236)


