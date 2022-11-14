>Ini adalah Rangkuman dari minggu ke **8** mulai dari minggu web dev basic atau minggu ketiga BE-DEV

## Rangkuman BE-DEV Week 3
> ### Modul yang dipelajari:
> - Web Services and Restful API with Express JS & Sequelize
> - Database Design with MongoDB 
> - Web Services and RESTful API with Express JS & Mongoose
> - Container & Docker 

## Web Services and Restful API with Express JS & Sequelize
Setelah selesai installing dan bootstraping folder sequelize. [click here jika belum](https://github.com/yazidr1/KM-skilvul/blob/main/BE-Bootcamp/Week2/README.md).
Setelah melakukan `npx sequelize-cli init` maka akan memunculkan folder `config`, `models`, `migrations` dan `seeders`.
dengan 
- `config` tempat configurasi sambungan database
- `models` tempat kita menyimpan model schema table sql nya, saat menggunakan `sequelize model:create` juga file yang digenerate ada disini
- `migrations` tempat hasil implementasi setiap kali model dimigrate ke database, catatan model yang pernah dimigrate juga
- `seeders` tempat menampung file data yang akan dimasukkan kedalam table dengan format yang sesuai sequelize tetapkan

#### Migration
[official doc](https://sequelize.org/docs/v6/other-topics/migrations/)
#### Seeding
[dev blog](https://dev.to/idmega2000/seeding-data-with-sequelize-1f3o)
#### Basic CRUD
[Basic querying](https://sequelize.org/docs/v6/core-concepts/model-querying-basics/)
-   findAll() mencari banyak data dalam database, dapat memasukkan argumen maupun tidak.
-   findOne() mencari satu spesifik data berdasarkan argumen.
-   create() membuat data baru pada database.
-   update() melakukan pengubahan data.
-   destroy() menghapus data.

## Database Design with MongoDB
>- Peserta mampu memahami basic dari MongoDB
>- Peserta mampu melakukan operasi CRUD pada MongoDB
>- Peserta mampu memahami dan membuat skema serta relasi pada MongoDB

#### Basic Mongodb terms
- database -> tempat menyimpan collection
- collection-> tempat menyimpan document
- document-> unit terkecil yang menyimpan data dalam format seperti json.
#### Operasi CRUD MongoDB
- kita dapat menggunakan mogosh atau mongo shell
- [official doc](https://www.mongodb.com/docs/manual/reference/method/)
- `show dbs` untuk cek list database
- `use <nama_database>` untuk menselect suatu database yang sudah ada ataupun tidak.
- `db.createCollections(“olahraga”)` untuk membuat collection todo
- `db.olahraga.insertOne({"nama": "bulutangkis", "level": "medium"})` untuk membuat data bulutangkis dan levelnya
- `db.olahraga.find({"nama":"bulutangkis"})` untuk mencari data nama bulutangkis di collection olahraga
- `db.olahraga.find()` untuk melihat semua document di collection olahraga.
- `db.olahraga.updateOne({"nama": "bulutangkis"}, {$set:{"nama":"renang"}})` untuk mengubah 1 data nama bulutangkis menjadi renang.
- `db.olahraga.deleteOne({"nama":"bulutangkis"})` untuk menghapus 1 data dengan nama buluttangkis di collection olahraga.
#### Relasi di MongoDB
> embedding lebih cepat t
- #### One to one
```json
{
    "_id": "ObjectId('AAA')",
    "name": "Joe Karlsson",
    "company": "MongoDB",
    "twitter": "@JoeKarlsson1",
    "twitch": "joe_karlsson",
    "tiktok": "joekarlsson",
    "website": "joekarlsson.com"
}
```
- #### One-to-Few
- > prefer embedding 
```json
"_id": "ObjectId('AAA')",
    "name": "Joe Karlsson",
    "company": "MongoDB",
    "twitter": "@JoeKarlsson1",
    "twitch": "joe_karlsson",
    "tiktok": "joekarlsson",
    "website": "joekarlsson.com",
    "addresses": [
        { "street": "123 Sesame St", "city": "Anytown", "cc": "USA" },  
        { "street": "123 Avenue Q",  "city": "New York", "cc": "USA" }
    ]
```
- #### One to many
- product:
```json
{
    "name": "left-handed smoke shifter",
    "manufacturer": "Acme Corp",
    "catalog_number": "1234",
    "parts": ["ObjectID('AAAA')", "ObjectID('BBBB')", "ObjectID('CCCC')"]
}
```
- parts
```json
{
    "_id" : "ObjectID('AAAA')",
    "partno" : "123-aff-456",
    "name" : "#4 grommet",
    "qty": "94",
    "cost": "0.94",
    "price":" 3.99"
}
```
- #### one to squillions
- hosts:
```json
{
    "_id": ObjectID("AAAB"),
    "name": "goofy.example.com",
    "ipaddr": "127.66.66.66"
}
```
- log message:
```json
{
    "time": ISODate("2014-03-28T09:42:41.382Z"),
    "message": "cpu is on fire!",
    "host": ObjectID("AAAB")
}
```
- #### Many to many
- users:
```json
{
    "_id": ObjectID("AAF1"),
    "name": "Kate Monster",
    "tasks": [ObjectID("ADF9"), ObjectID("AE02"), ObjectID("AE73")]
}
```
- Tasks:
```json
{
    "_id": ObjectID("ADF9"),
    "description": "Write blog post about MongoDB schema design",
    "due_date": ISODate("2014-04-01"),
    "owners": [ObjectID("AAF1"), ObjectID("BB3G")]
}
```
 Dalam mendesain ada 2 cara untuk menggunakan mengasosiasikan suatu data ke data lain, yaitu embedding dan refferencing. 
#### Recap:
>- **One-to-One** - Prefer key value pairs within the document
>- **One-to-Few** - Prefer embedding
>- **One-to-Many** - Prefer embedding
>- **One-to-Squillions** - Prefer Referencing
>- **Many-to-Many** - Prefer Referencing

>- General Rules for MongoDB Schema Design:
>-   **Rule 1**: Favor embedding unless there is a compelling reason not to.  
>-   **Rule 2**: Needing to access an object on its own is a compelling reason not to embed it.  
>-   **Rule 3**: Avoid joins and lookups if possible, but don't be afraid if they can provide a better schema design.
>-   **Rule 4**: Arrays should not grow without bound. If there are more than a couple of hundred documents on the _many_ side, don't embed them; if there are more than a few thousand documents on the _many_ side, don't use an array of ObjectID references. High-cardinality arrays are a compelling reason not to embed.
>- **Rule 5**: As always, with MongoDB, how you model your data depends **entirely** on your particular application's data access patterns. You want to structure your data to match the ways that your application queries and updates it.

## Web Services and RESTful API with Express JS & Mongoose
[official doc](https://mongoosejs.com/docs/guide.html)
>Dalam mendesain dan mengelola data dengan mongoose selalu diawali dengan defining schema.
#### contoh schema:
```node
import mongoose from 'mongoose';
const { Schema } = mongoose;

const blogSchema = new Schema({
  title:  String, // String is shorthand for {type: String}
  author: String,
  body:   String,
  comments: [{ body: String, date: Date }],
  date: { type: Date, default: Date.now },
  hidden: Boolean,
  meta: {
    votes: Number,
    favs:  Number
  }
});
```
#### Simple CRUD
[learn queries](https://mongoosejs.com/docs/queries.html)
-   [`Model.deleteMany()`](https://mongoosejs.com/docs/api.html#model_Model-deleteMany)
-   [`Model.deleteOne()`](https://mongoosejs.com/docs/api.html#model_Model-deleteOne)
-   [`Model.find()`](https://mongoosejs.com/docs/api.html#model_Model-find)
-   [`Model.findById()`](https://mongoosejs.com/docs/api.html#model_Model-findById)
-   [`Model.findByIdAndDelete()`](https://mongoosejs.com/docs/api.html#model_Model-findByIdAndDelete)
-   [`Model.findByIdAndRemove()`](https://mongoosejs.com/docs/api.html#model_Model-findByIdAndRemove)
-   [`Model.findByIdAndUpdate()`](https://mongoosejs.com/docs/api.html#model_Model-findByIdAndUpdate)
-   [`Model.findOne()`](https://mongoosejs.com/docs/api.html#model_Model-findOne)
-   [`Model.findOneAndDelete()`](https://mongoosejs.com/docs/api.html#model_Model-findOneAndDelete)
-   [`Model.findOneAndRemove()`](https://mongoosejs.com/docs/api.html#model_Model-findOneAndRemove)
-   [`Model.findOneAndReplace()`](https://mongoosejs.com/docs/api.html#model_Model-findOneAndReplace)
-   [`Model.findOneAndUpdate()`](https://mongoosejs.com/docs/api.html#model_Model-findOneAndUpdate)
-   [`Model.replaceOne()`](https://mongoosejs.com/docs/api.html#model_Model-replaceOne)
-   [`Model.updateMany()`](https://mongoosejs.com/docs/api.html#model_Model-updateMany)
-   [`Model.updateOne()`](https://mongoosejs.com/docs/api.html#model_Model-updateOne)
nama method beberapa queries mirip dengan crud di mongoDB, untuk di mongoose ini tampaknya memiliki lebih banyak argumen yang bisa digunakan.
## Container & Docker
Docker merupakan sebuah program untuk membantu membangun, membagikan dan menjalankan aplikasi. Salah satu isu yang banyak dijumpai pada dunia development yaitu aplikasi yang telah dibuat tidak bekerja di komputer server atau production karena misalnya teknologi yang dipakai berbeda versi, depedency library yang tidak ada dsb.
Hal tersebut dapat diselesaikan dengan bantuan container docker yang depedency nya dapat kita tetapkan.
> - docker image -> template tak dapat diubah yang menentukan bagaimana sebuah container akan dijalankan.
> - docker container -> sebuah service atau runtime yang menjalankan docker image yang dibuat saat `docker run ` command dijalankan
> - Dockerfile -> docker dapat membuat image berdasarkan   set instruksi dari file bernama Dockerfile 
>   [learn more about Dockerfile](https://docs.docker.com/engine/reference/builder/)
>   
Contoh Dockerfile

```Dockerfile
// define install node v berapa 
FROM node:16

// define workdir image
WORKDIR /usr/src/app

// copy all file named that start with "package" with extension json
COPY package*.json .

// npm install to genenrate npm module based from package.json
RUN npm install

// copy semua file di workdir ini ke workdir image
COPY . .

EXPOSE 8080

// run node app.js in cmd
CMD [ "node", "app.js" ]
```
> - Docker Compose -> sebuah cara untuk menentukan spesifikasi dan dapat menjalankan beberapa container bersamaan.  configurasi di file dengan ekstensi .yaml
>   [learn more about docker compose](https://docs.docker.com/compose/gettingstarted/)
Contoh .yaml file
```yaml
version: "3"
services:
	express:
	image: "dollong/demo-express"
	ports:
		- "3000:3000"

hello-world:
	image: "hello-world"
```
