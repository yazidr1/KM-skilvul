# Summary Week 1

> ### Modul yang Dipelajari:
> - Unix Command Line
> - Git & Github
> - HTML
> - CSS
> - Algorithm
> - Javascript Conditional dan Looping

## Unix Command Line
- ### Shell
  Merupakan penerjemah command-line. Sebuah shell memproses perintah perintah dan mengeluarkan hasilnya. contoh: Windows powershell, bash, zsh dll
- ### Command Line Interface(CLI)
  Merupakan program komputer yang memproses perintah yang berbentuk barisan teks. Pengguna biasanya berinteraksi dengan shell melalui CLI.
- ### Terminal 
  Merupakan aplikasi yang berupa CLI, jadi ada area untuk kita memasukkan perintah dan menampilakan hasilnya yang berupa text.  Contoh windows terminal, linux Xterm, dan Mac terminal app
- ### git bash 
  merupakan bash yang membuat git commands dapat diakses dengan mudah. 

> Istilah Istilah ini sering dipakai terbalik balik walaupun secara teknikal sangat berbeda

### File System Structure
File System Structure merupakan cara Operating System mengatur bagaimana file akan disimpan dan diakses, struktur yang umum dipakai yaitu tree yg bercabang cabang seperti gambar dibawah ini
![[Pasted image 20220928165249.jpg]]
### Mengakses CLI di Windows 10 dari file explorer 
1. Pilih directory yang akan dituju
2. right click atau tekan shift+right click jika ingin memunculkan powershell
   ![[Pasted image 20220926152902.png]]
3. Pilih Powershell atau terminal lain
4. Terminal siap untuk menjalankan commands 

> Jika dalam VSCode, kita juga dapat mudah untuk membuka integrated terminalnya dengan memilih **New Terminal** di panel **Terminal** atau shortcut **ctrl+shift+\`**

- ### CLI Commands
  - pwd(print working directory), melihat path directory yang sedang diakses
  ![[Pasted image 20220926151434.png]]
  - dir(directory), melihat list dan directory
    ![[Pasted image 20220926154301.png]]
  - cd(change directory), untuk berpindah directory
    ```sh
    //cd directory_yang_dituju
    cd Week1
    ```
  - ls(list), melihat list file dan directory
    ```sh
    ls  
    ```
  - mkdir(make directory), buat directory
    ```sh
    //mkdir nama_directory
    mkdir Week2
    ```
  - touch, membuat sebuah file
    ```sh
    //touch nama_file
    touch LearningMarkdown.md
    ```
  - cp, copy file atau directory
    ```sh
    //cp [option] directory_asal directory_yg_dituju
    cp LearningMarkdown.md Week1/
    cp -R Week1 ../
    ```
  - mv, move file atau directory dan rename
    ```sh
	// mv [option] directory_asal directory_yg_dituju
	// rename
	mv LearningMarkdown.md LearningMD.md
	// to a directory
	mv LearningMarkdown.md Week1
	// directory to directory
	mv -R Week1 Backup
	```
  -  rm, remove file atau directory
	```sh
	//rm [option] file/directory
	rm -R LearningMarkdown.md
	rm -d Week1
	```
## Git & Github
### Git 
merupakan software free dan open source untuk distribusi version control; melacak perubahan; biasanya untuk kolaborasi bekerja bersama diantara programmers dalam membangun aplikasi

### Github
merupakan salah satu layanan untuk menyimpan repository source code yang mendukung git. 

>  Kebutuhan akan system version control dan service yang menyimpan source code sangat dibutuhkan oleh software developer karena biasanya project software dilakukan dalam team dan perlu adanya 
>  - system version control git untuk melacak perubahan,
>  - berkolaborasi secara paralel, dan
>  - tempat repository dimana anggota team dapat mengakses. 
>  Beberapa fungsi ini sangat diperlukan untuk kecepatan dalam developing dan menghindari bug pada softwarenya.
<br>

> #### Ada 2 usecase yang biasa saya temukan saat memulai
> 1. Sudah membuat folder project di lokal env dan ingin attach folder project ke github
> 2. Project sudah ada di github dan ingin clone ke lokal env
### Git Commands
#### Quick Setup
>Setelah 
![[Pasted image 20220926172337.jpg]]
1. Sudah membuat folder project
```bash
git init 
git add .
git commit -m "First Commit"
git branch -M main
git remote add origin <link_repo>
git push -u origin main
```
> - Setiap feature akan dilakukan commit 
> - Kemudian dapat di push ke branch main atau branch lain
2. Project sudah ada di github
```bash
git clone <link_repo>
//masukkan credential akun github apabila di prompt 
cd <dir_project>
```

## HTML 
> ### Definisi
> Singkatan dari HyperText Markup Language. Html merupakan bahasa markup untuk memunculkan kerangka dan content halaman web. Dokumen HTML yang berisi tag-tag HTML akan memberitahu browser bagaimana cara menampilkan sebuah konten.
### Membuat File HTML
Caranya sangat mudah:
1. buat new file
2. beri nama file diikuti ekstensi html 
   contohnya Hello.html
### Kerangka HTML 5

```HTML
	<!DOCTYPE html>
	<html lang="en">
		<head>
			<title>Judul Website</title>
		</head>
		<body>
		    <h1>saya sedang belajar pemrograman HTML dasar.</h1>
		</body>
	</html>
```
### Menjalankan HTML manual dan  live server
> 2 hal untuk membuat dan menjalankan html yaitu:
> - Browser
> - Code Editor atau Text Editor 
> - OS juga ya, kalau nggak ada gabisa bikin file

> ### Manual
> 1. Temukan file html / buat file dengan ekstensi html(.html)
> 2. Open dengan browser favorit
> #### catatan
> - setiap ada changes di file, harus mensave file dan merefresh tab file htmlnya di browser

>### Liveserver vscode
> 1. liveserver merupakan extension di vscode, install di extension marketplace vscode.
> 2. buka file html di vscode
> 3. lalu open click kanan **open with live server** atau **ctrl+shift+p** dan pilih **open with live server** atau shortcut nya **alt l alt o**
### Tag HTML
Tag merupakan cara HTML memberi tahu browser bagaimana teks, konten, atau lain lain ditampilkan pada browser nantinya.
> Tag tag html kebanyakan memiliki **tag pembuka** dan **tag penutup**, tetapi ada juga yang hanya tag pembuka. Tag penutup ditandai dengan **/** sebelum nama tag di tag penutup.
> Tag tag html juga dapat memiliki atribut seperti class, id, src, href dan lain lain.
```html
	<h1 class="Head1">hello</h1>
	<a href="https://www.w3schools.com">Visit W3Schools.com!</a>
	<img src="https://bit.ly/2EuFNQZ" alt="">
	<div id= "hello"></div>
```

> Pada perkembangannya, dulu untuk membuat area dengan fungsi tertentu selalu menggunakan div. Pada html 5 diperkenalkan banyak tag khusus banyak semantic element, beberapa tujuan dan manfaatnya sebagai berikut:
> - SEO friendly 
> - block of code yang meaningful 
> - mengurangi "endless" div, sehingga dalam membaca source code lebih enak
> Beberapa tag html semantics akan dicontohkan berikut ini

```html
// disini saya hanya menulis tag pembuka saja
<article>
<aside>
<details>
<figure>
<header>
<nav>
<main>
<summary>
<section>
<footer>
// dan masih banyak lainnya
```

### Publish/deploy ke Hosting Service
Banyak Hosting Service, tetapi untuk hosting web static yang paling terkenal yaitu **Netlify** karena bisa free dengan starter plannya dengan limit bandwith yang 
cukup besar untuk project pribadi, experiment, dan belajar web deelopment.

> #### Cara deploy sebagai berikut:
> - Buka browser, dan pergi ke halaman [Netlify](https://www.netlify.com/)
> - Login dengan akun github, gitlab, bitbucket atau email yang sudah terigistrasi.
> - Click **Add new site** lalu **Deploy manually**, Drag & drop file atau folder yang ingin kita host.
> - Setelah beberapa saat, project sudah dapat diakses dari mana saja(mobile, desktop) dengan link yang tertera.

# CSS
### Definisi
> Singkatan dari Cascading Style Sheet. Css merupakan cara untuk mengubah style kerangka dan struktur HTML sehingga tampilan terlihat bagus dan dengan layout layout yang diterapkan pada halaman web HTML(Web Tradisonal) maupun pada Web Modern. 
### Cara Menggunakan CSS
- #### Inline Styles
```html
	<p style= "color:f6f6f6">Tulisan ini berwarna putih keabuan</p>
```
- #### Internal CSS
  Masih di file HTML, tetapi diletakkan di tag Head.
```html
	<head>
		<style>
	      body {
	        background-color: yellow;
	      }
	      h1 {
	        color: blue;
	      }
	      p {
	        color: red;
	      }
	</head>
	<body>
		<h1>tulisan biru</h1>
	</body>
```
- External CSS
#### CSS Syntax
Syntax pada css cukup mudah dipahami, digunakan untuk memilih semua element(tanda bintang*) 
tag, class, id, dan atribut([attr=value]). Syntax CSS umumnya terdiri dari selector, property dan value.
```css
h1{
	color: skyblue;
}
```
- h1 disebut selector
- color disebut property
- skyblue disebut value dari property
# Algoritma 
### Definisi
- Algoritma adalah cara cara atau tahapan yang terstruktur untuk mencapai tujuan/menyelesaikan masalah tertentu. 
- Ciri-ciri Algoritma yang baik yaitu terdapat input, output, memiliki batasan/titik berhenti, dan efektif secara waktu dan resource yang dipakai
- Data Structure(DS) adalah cara penyimpanan yang dipakai untuk menyimpan dan mengelola data. DS adalah cara mengatur data di komputer sehingga dapat diakses dan diupdate secara efisien 
- contoh algoritma sederhana
![[Pasted image 20220928210315.png]]
Di convert ke javascript, dapat berupa seperti di bawah:
```js
let lampu = "merah"
if (lampu == "merah"){
	console.log("STOP")
} else if(lampu == "kuning"){
	console.log("WAIT")
} else{
	console.log("GO")
}
```

### Big O Notation
Merupakan tolak ukur kita dalam hal kecepatan dan resource yang dipakai dan mungkin faktor lain pada solusi pada function atau algoritma search atau apapun itu sehingga kita bisa bilang algoritma kita sangat bagus, bagus, cukup bagus, kurang, kurang sekali. Kita juga dapat mengkomparasi satu algoritma dengan yang lain dengan Big O ini.
Contoh notasi yaitu O(n), O(n^2), O log n, O(n log n) dan lain lain.

# Javascript
### Definisi
> - Merupakan salah satu bahasa pemograman yang sangat populer karena komunitasnya banyak dan juga banyak menciptakan framework framework yang memudahkan programmer. Javascript atau JS ini pada web Tradisional(HTML, CSS, JS) berfungsi sebagai otak jika dianalogikan pada manusia, logika logika pada web dapat kita tulis dengan JS supaya Halaman web kita tidak statis, contoh ketika mengklik button berpindah ke halaman lain dan sebagainya.
> - Pada Web Modern menggunakan JS ini dapat "berperan" layaknya html bahkan css dengan css in JS CMIIW. Istilahnya dengan Memahami JS ini kita dapat menciptakan Full blown Website / Web App yang dynamic dengan dapat menerima dan mengirim data dan sebagainya. Dulunya untuk membuat full blown Web App harus menguasai html, css, js, dan 1 atau lebih bahasa pemograman untuk bagian backend-nya. Dengan JS di Front-end dengan library atau framework JS nya sendiri dan Backend dengan library atau framework JS sendiri ini, fullstack dapat dikuasai dengan hanya 1 basis bahasa pemograman yaitu JS. Full-stack Framework ada seperti Nextjs dengan basis JS atau Typescript, Laravel, Django dll.


### Menjalankan Javascript(JS)
- Dapat me-link an JS file pada HTML Head dengan atribute defer atau di bagian bawah body, kemudian dapat melihat hasilnya dengan browser di html tersebut
- Dapat juga apabila telah terinstall node js runtime, kita dapat menjalankan node tanpa browser. Caranya:
- masuk ke working directory tempat file js berada
- lalu buka dengan code editor
- buka terminal dan ketikkan node<spasi><lokasi_file>. Contoh file getContact.js ada di folder Contact-App dan terminal kita telah masuk cd Contact-App, lalu kita dapat jalankan di terminal `node ./getContact.js`.

### Tipe Data
Terdapat tipe data dasar di JS
- number 
- string
- boolean 
- null 
- undefined 
- object  {}
- array []

### Operator 
> Binary(butuh 2 operand)[aritmatika(+-*/%),
> penugasan(=,+=,-=,*=,/=,%=) x += y === x= x+ y
> perbandingan(==, !=, ===, !==, >, <, >=, < ) output boolean(true, false),
> logika(&& || !) output boolean(true, false),
> string(+, "apple" + " " +"pen" = "apple pen")]
> Ternary(butuh 3 operand (kondisi) ? benar: salah )((x % 2 == 0) ? "genap": "ganjil")[Kondisional]
> Unary[typeof] typeof("10") //string

### Control Flow 
#### Conditional (If switch)
```js
let lampu = "merah"
if (lampu == "merah"){
	console.log("STOP")
} else if(lampu == "kuning"){
	console.log("WAIT")
} else{
	console.log("GO")
}
```

#### Looping (for,while)

```js
for (let i = 1; i <= 10 ; i++) {
	if (i == 6) {
		console.log(i , "yess ketemu")
	} else {
		console.log(i)
	}
}
```