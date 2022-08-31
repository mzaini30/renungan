# Berbagai Bentuk Website

Sebenarnya agak bingung sih memberi judul pada artikel satu ini. Soalnya, website yang aku maksud di sini, bukan hanya website yang dibuka di browser, melainkan dalam bentuk yang lain, seperti aplikasi Android dan aplikasi desktop. Jadi, ayo kita bahas.

## Orientasi Iklan

Iklan di sini adalah Adsense dan Admob.

### Website Pada Umumnya

Website pada umumnya berarti website yang dibuka di browser. Berarti, kita mengandalkan Adsense. Kalau ingin menggunakan Adsense, nggak cocok framework JavaScript. Jadi, kita harus menggunakan HTML biasa. Ada banyak pilihan untuk membangun website tanpa framework JavaScript:

- Astro
- Iles
- Pug

Itu adalah beberapa caranya.

Tapi, tentu saja kita nggak meninggalkan JavaScript sama sekali. Makanya, aku ada menyebutkan Astro dan Iles yang memiliki konsep partial hydration. Lalu, misal kita pakai Pug, berarti menggunakan Petite Vue atau Alpine JS.

Lalu, untuk komunikasi antar dua app Petite Vue di halaman yang sama, kita bisa menggunakan event storage:

```coffeescript
# getter
addEventListener "storage", ->
	console.log localStorage.data

# setter
tombol = document.querySelector "button"
tombol.addEventListener "click", ->
	localStorage.data = Math.random()
	dispatchEvent new Event "storage"
```

Atau bisa juga kita modif localStorage:

```coffeescript
# modif
realStorage = localStorage.setItem
localStorage.setItem = (key, value) ->
	realStorage key, value
	dispatchEvent new Event "storage"

# getter
addEventListener "storage", ->
	console.log localStorage.data

# setter
tombol = document.querySelector "button"
tombol.addEventListener "click", ->
	localStorage.setItem "data", Math.random()
```

### Aplikasi Android

Kalau untuk aplikasi Android, kita pakai Admob. Di situ, nggak terlalu diperhatikan kode HTML-nya, maupun porsinya dengan JavaScript. Kalau di web untuk browser kan harus lebih banyak HTML daripada JavaScript-nya. Tapi, kalau bentuk aplikasi Android, karena Admob itu nggak dipengaruhi sama elemen HTML, nggak masalah kita full pakai framework JavaScript. Yang penting, dia pakai routing hash.

Nah, untuk convert dari bentuk web ke bentuk aplikasi Android, aku pakai [andro](https://github.com/mzaini30/andro).

## Tanpa Iklan

### Extension Chrome

### Aplikasi Desktop