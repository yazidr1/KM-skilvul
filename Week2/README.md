# Rangkuman Week 2
> ## Modul yang Dipelajari: Full JS
> - Loop, Scope & Function
> - Data type, Built-in Method & Prototype
> - DOM Intro( selecting element, traversing element)
> - DOM Manipulation( elements, styles)
> - DOM Events

## Loop, Scope & Function
### Loop 
```js
// for biasa, ingat kondisinya start, stop step. 
for (let i = 1; i <= 10 ; i++) {
  console.log(i)
}

// while condition isTrue jalankan block code
let i = 10
while (i <= 10) {
  console.log(i)
  i++
}

i = 1
let isKetemu = false

while (!isKetemu) {
  if (
    i % 2 == 0 && 
    i % 3 == 0 && 
    i % 4 == 0 && 
    i % 5 == 0 &&
    i % 6 == 0 
    ) {
      console.log(i);
      isKetemu = true
    }

    i++
}
```
### Scope
Merupakan konsep dalam flow data variabel, yang mempengaruhi akses pada variabel tersebut.
- Blocks {}
  ->code yang didalam curly braces `{}` seperti dalam conditional, function dan looping blocks.
> 2 scope di JS yaitu Global Scope dan Local scope
- Global scope
  Variabel yang berada diluar block disebut variabel yang memiliki global scope.
  > Sekali mendefinisikan global variabel, kita dapat mengakses variabel didalam maupun luar block 
  
  ```js
  // di define di luar block
  let name = "Yazid"
  const status = true
  ```
- Local Scope
  Variabel yang berada didalam block disebut variabel yang memiliki local scope.
  > Variabel hanya dapat diakses dalam block
  
```js
  function submit(){
    // warn_teks adalah local variable karena didalam block code function submit
    let warn_teks = document.getElementById("warning");
  }
```
### Function
```js
// normal notation to use function
function checkString(s) {
	if (s.length >= 8) {
	    return true
	} else {
	    return false
	}
}
// call checkString function
checkString("Huahaha");

// Arrow function notation
// () => {//block of code}, () => a line of code
const checkString = (s) =>{
	if (s.length >= 8) {
	    return true
	} else {
	    return false
	}
}
// short sytax using ternary operator
let checkStringArrow = (s) => s.length >= 8 ? true : false
```
## Data type, Built-in Method & Prototype
### Data Type
Terdapat tipe data dasar di JS
- number 
- string
- boolean 
- null 
- undefined 
- object  {key: value}
- array [ ]
### Built-in Property dan Method
- String Property dan Method
[String MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)
Built-in properti `.length` dan method seperti `.concat()`, `.toUpperCase()`, `.toLowerCase()` adalah sedikit dari banyak built-in String yang dapat kita gunakan.
- Number Property dan Method
[Number MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)
Built-in properti `.MAX_VALUE` `.NAN` dan method seperti `.isNaN()` , `.isInteger()`, `.toFixed()`   adalah sedikit dari banyak built-in Number yang dapat kita gunakan.
## DOM Intro( selecting element, traversing element)
> - Singkatan dari Document Object Model.
> - The DOM is a W3C (World Wide Web Consortium) standard.
> - "The W3C Document Object Model (DOM) is a platform and language-neutral interface that allows programs and scripts to dynamically access and update the content, structure, and style of a document.

- Saat halaman web dimuat, browser membuat DOM halaman.
- HTML DOM dibuat seperti struktur pohon!
  ![Tree Structure DOM](../pic_htmltree.gif)
  
### Selecting Element
Ada beberapa cara untuk men-select element yaitu sebagai berikut:
- `document.getElementById(); // select id`
-   `document.getElementsByClassName() // select suatu class, dan mengembalikan HTML collection`
-   `document.getElementsByTagName() select tag html dan mengembalikan HTML collection`
-   `document.querySelector() // seperti selector css, akan menselect suatu tag, id, class dan mungkin atribut`
-   `document.querySelectorAll() // sama seperti selector css, dan mengembalikan Node List`
> Yang outputnya berupa HTML Collection dan NodeList, mengaksesnya mirip seperti mengakses array.

## DOM Manipulation( elements, styles)
### Elements
- Update Element
  ```js
  // Beberapa keyword dalam mengUpdate atau mengubah
  // innerHTML bisa memunculkan tag html ataupun text
  element.innerHTML = "<h1>My Bio</h1>" atau 'My BIO' 
  // innerText mengubah value text CMIIW
  element.innerText = "My BIO"
  ```
- Create Element & styles
```html
<body>
	<!-- Buat div tempat menyimpan element yang nanti dibuat -->
	<div class="App"></div>
</body>
<script>
	let app = document.getElementById("app");
	//create 
	let p = document.createElement("p");
	p.innerText = "ini adalah paragraf";

	//tambahkan p kedalam container App
	app.append(p);

	//styling
	app.style.color = "skyblue"
	app.style.height = "33vh"
	
</script>
```

## DOM Events
> ### Events merupakan kejadian/kegiatan/interaksi yang terjadi pada website
> Beberapa  contoh event:
> - click
> - submit
> - focus
> - hover
> - scroll
> - blur
> - dll

> 3 Cara memberi event:
> - inline
>   `<h1 onclick="alert('selamat datang')">Hallo</h1>`
> - External JS
```js
let paragraf = document.getElementById("paragraf")

paragraf.onclick = function () {
  alert("ini dari paragraf")
}
```
> - addEventListener, bisa multiple event
```js
let button = document.getElementById("btn")
button.addEventListener("click", function (event) {
  console.log(event.target)
  alert("ini dari button")
})
```
