## Rangkuman Week 4
> ## Modul yang dipelajari:
> - Async, await dan fetch
> - Responsive 
> - Bootstrap

## Async, await dan fetch
Ketiga keyword diatas adalah satu diantara cara melakukan asynchronous yang biasa digunakan untuk meminta panggilan dan menerima objek data dari API. 
```js
//Basic syntax
//using arrow function
let getAPI = async () => {
	//api endpoint
	let URL = "httpshttps://digimon-api.vercel.app/api/digimon"
	// catch response
	let res = await fetch(URL)
	// unpackage the response
	let digimons = await res.json()

	// API biasa berbentuk Array of Object, jadi kita dapat meloop untuk berbagai keperluan 
	// biasa untuk meloop-nya menggunakan for of, forEach atau map.
	digimons.slice(0,20).forEach((item, index)=>{
	// disini item adalah objek digimons dari index 0 hingga 20
	// block of code
	})
}
```
## Responsive 
Responsive desain pada web merupakan cara yang membuat perubahan yang dinamik pada tampilan web, tergantung pada ukuran layar dan orientasi device(potrait dan landscape) yang digunakan sehingga terlihat dan terasa sama walaupun berbeda ukuran layar.
### Beberapa faktor supaya web responsive
1.  meta viewport
```html
<html>
	<head>
	<meta name= "viewport" content= "width=device-width, initial-scale=1.0" />
	<!-- tag meta ini ingin memberi tahu browser saat user me-load web ini bahwa set width setara device-width yaitu sekian px dan skala inisiasi atau zoom level setara 1.0 -->
	</head>
	<body></body>
</html>
```
2.  max-width
3.  relative unit 
    `vw`, `vh`, `%`, `em`, `rem` adalah ukuran relative,  `vw` relative kepada width viewport, vh relative kepada height viewport, % relative ke element parent, em relative kepada font size element induk, rem relative kepada font size element root.
4.  media query
   Kita ingin mengganti properti element tertentu apabila 
```css
/** ketika browser kurang sama dengan dari width 600px body background color berubah light blue */
@media only screen and (max-width: 600px) {  body {    background-color: lightblue;  }}

@media (max-width: 600px ) {
	/* Dapat juga memilih banyak element*/
	.menu {
		display: none;
	}

	.toggle-menu {
		width: 40px;
		height: 40px;
		background: url(./menu.svg);
		background-position: center;
		background-repeat: no-repeat;
		background-size: 30px;
		background-repeat: no-repeat;
}
```
5.  flex system
```css
/* pilih element container set properti display*/
.forms__container{
	display: flex;
	justify-content: space-between;
}
```
6.  grid system
```css
.form__container{
	display: grid;
}
```

## Bootstrap
Bootstrap adalah css framework yang didevelop pertama kali oleh developer twitter. Bootstrap digunakan untuk membuat styling yang cepat dan 
element yang sudah dibuat dan contohnya menurut bootstrap element ini seharusnya berwarna ini dan ini, itu memudahkan tetapi sekaligus seperti 2 kali styling dengan bootstrap dan custom css lagi ketika ingin berwarna lain sesuai design web yang ada misalnya.
### layout
[Bootstrap Layout](https://getbootstrap.com/docs/5.2/layout/breakpoints/) untuk lengkapnya
```html 
<!-- FLEX -->
```html
<div class="d-flex flex-row bd-highlight mb-3">
  <div class="p-2 bd-highlight">Flex item 1</div>
  <div class="p-2 bd-highlight">Flex item 2</div>
  <div class="p-2 bd-highlight">Flex item 3</div>
</div>
<div class="d-flex flex-row-reverse bd-highlight">
  <div class="p-2 bd-highlight">Flex item 1</div>
  <div class="p-2 bd-highlight">Flex item 2</div>
  <div class="p-2 bd-highlight">Flex item 3</div>
</div>
```

```html
<!-- GRID -->
<div class="container text-center">
  <div class="row">
    <div class="col">
      Column
    </div>
    <div class="col">
      Column
    </div>
    <div class="col">
      Column
    </div>
  </div>
</div>
```

```html
<!-- Content->Tables -->
<table class="table">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">First</th>
      <th scope="col">Last</th>
      <th scope="col">Handle</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>Mark</td>
      <td>Otto</td>
      <td>@mdo</td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Jacob</td>
      <td>Thornton</td>
      <td>@fat</td>
    </tr>
    <tr>
      <th scope="row">3</th>
      <td colspan="2">Larry the Bird</td>
      <td>@twitter</td>
    </tr>
  </tbody>
</table>
```

```html
<!-- Component->Card -->
<div class="card" style="width: 18rem;">
  <img src="..." class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
    <a href="#" class="btn btn-primary">Go somewhere</a>
  </div>
</div>
```
### Breakpoint 
[Breakpoint(media query)](https://getbootstrap.com/docs/5.2/layout/breakpoints/) untuk lengkapnya

#### Min-width
```scss
.custom-class {
  display: none;
}
/* min width*/
@include media-breakpoint-up(sm) {
  .custom-class {
    display: block;
  }
}
```

```scss
// X-Small devices (portrait phones, less than 576px)
// No media query for `xs` since this is the default in Bootstrap

// Small devices (landscape phones, 576px and up)
@media (min-width: 576px) { ... }

// Medium devices (tablets, 768px and up)
@media (min-width: 768px) { ... }

// Large devices (desktops, 992px and up)
@media (min-width: 992px) { ... }

// X-Large devices (large desktops, 1200px and up)
@media (min-width: 1200px) { ... }

// XX-Large devices (larger desktops, 1400px and up)
@media (min-width: 1400px) { ... }
```

#### Max-width
```scss
.custom-class {
  display: none;
}

@include media-breakpoint-down(md) {
  .custom-class {
    display: block;
  }
}
```

```scss
// `xs` returns only a ruleset and no media query
// ... { ... }

// `sm` applies to x-small devices (portrait phones, less than 576px)
@media (max-width: 575.98px) { ... }

// `md` applies to small devices (landscape phones, less than 768px)
@media (max-width: 767.98px) { ... }

// `lg` applies to medium devices (tablets, less than 992px)
@media (max-width: 991.98px) { ... }

// `xl` applies to large devices (desktops, less than 1200px)
@media (max-width: 1199.98px) { ... }

// `xxl` applies to x-large devices (large desktops, less than 1400px)
@media (max-width: 1399.98px) { ... }
```