>Ini adalah Rangkuman dari minggu ke **7** mulai dari minggu web dev basic atau minggu kedua BE-DEV
## Rangkuman BE-DEV Week 2
> ### Modul yang dipelajari:
> - Database Mysql
> - Middleware Authentication & Authorization with Express JS
> - Stress & Time Management Webinar
> - Web Services and Restful API with Express JS & Sequelize

## Database Mysql 
- **Database** merupakan set data yang dikelola sedemikian rupa berdasarkan ketentuan tertentu yang disimpan dalam sebuah sistem komputer. 
- **MySql** merupakan satu diantara database management system(dbms) relational.
- **Relational database** adalah database yang memungkinkan tabletable didalamnya memiliki hubungan.  relational database menyimpan data dalam bentuk baris dan kolom dan memungkinkan banyak user mengaksesnya.
- **Type data** yang sering ditemui:
  #### string
  - varchar(size) --letters,numbers, special character
  - char(size) --letters, numbers, and special characters
  - enum(value1,value2,...) --
  #### numeric
  - int(size) 
  - double(size, d) --d ->digits after decimal
  #### date & time
  - date --format :YYYY-MM-DD
  - datetime --Format: YYYY-MM-DD hh:mm:ss
  - timestamp --Format: YYYY-MM-DD hh:mm:ss


### Basic SQL
```sql
-- create database
create database store;

-- use database 
use store;

-- DDL create table
create table product(
id int primary key not null auto_increment,
name VARCHAR(50),
price int,
category_id int,
Foreign key (category_id) refferences category(id)
);

create table category (
id int primary key not null auto_increment,
name VARCHAR(25)
);

-- DML insert data to product table
insert into product(name, price, category_id) Values
("nasi goreng ", 20000, 1),
("nasi gila",25000, 1),
("kwetiaw", 20000,1),
("es teh", 5000, 2),
("air mineral", 0, 2),
("kerupuk", 5000,3),
("gorengan", 10000,3),
("sprite", 40000,3);

-- DQL select 
select * from product;
select name, price from product where price >10000 limit 3;
-- alias column
select name AS NAMA, price "HARGA MENU" from product
```
### Basic SQL Lanjutan

```sql
--agregate
select avg(price) from products;
select sum(price) from products p ;
select max(price) from products

-- agregate function with group by
select c.name "Category", count(category_id)
from product p inner join category c
on p.category_id = c.id group by p.category_id;

-- joins
select p.name, p.price, c.name "Categori" from product p INNER JOIN category c on p.category_id = c.id;
```
## Middleware Authentication & Authorization with Express JS
Authentication memverifikasi dan memvalidasi user atau service dan authorization menentukan hak akses yang akan diberikan. contohnya authentication dilakukan saat melakukan login, kemudian akan diberikan hak akses berdasarkan role yang sudah ditentukan oleh suatu system e.g. admin dapat mengelola data karyawan dan karyawan dapat melakukan presensi. 
- **Encryption** adalah cara mengubah data biasanya kata biasa menjadi kata yang tersandi dengan sebuah kunci. dengan mengetahui kunci dan jenis enkripsi maka setelah dibuat kata tersandi maka dapat diubah kembali menjadi kata biasa. **JWT** atau json web token menggunakan teknik  enkripsi untuk membuat authentication lebih aman
- Hash merupakan cara mengubah data biasanya kata biasa menjadi kata tersandi yang tidak dapat dikembalikan kembali menjadi kata biasa. Teknik ini digunakan untuk mengamankan password yang tersimpan didatabase supaya lebih aman.

## Web Services and Restful API with Express JS & Sequelize
Sequelize adalah node JS Object Relational Mapper(ORM) yang berarti dapat memetakan sebuah object kedalam schema database. Sequelize mendukung dbms relational seperti Oracle, Postgres, MySQL, MariaDB, SQLite and SQL Server dan lain lain. Sequelize seperti bekerja diantara server dan database. 
Untuk belajar dan menggunakannya selalu lihat dokumentasi. 
[Sequelize](https://sequelize.org/docs/v6/) dan [Sequelize-cli](https://github.com/sequelize/cli)

### installing Sequelize
project menggunakan express, database mysql dan sequelize versi stable yaitu 6
```bash
//depedency
npm install --save sequelize mysql2 sequelize-cli

// init bootstraping folder dan file
npx sequelize-cli init

// sesuaikan credential database dan port(optional) di folder config di config.js

// sequlize-cli untuk membuat model
npx sequelize-cli model:create --name User --attributes email:string,password:string

// sequlize-cli membuat table dari semua model yang dibuat
npx sequelize-cli db:migrate

// undo migrate
npx sequelize-cli db:migrate:undo
```
