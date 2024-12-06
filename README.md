## **Materi Perkuliahan: jQuery Event & Selector**

### **I. Pengantar jQuery**

jQuery adalah sebuah pustaka JavaScript yang menyederhanakan proses pemrograman dengan menyediakan fungsi-fungsi untuk manipulasi DOM (Document Object Model), penanganan event, animasi, dan komunikasi Ajax. Dengan jQuery, pengembang web dapat menulis kode yang lebih bersih, singkat, dan kompatibel dengan berbagai browser.

#### **Fungsi utama jQuery:**
1. Manipulasi elemen HTML dan CSS.
2. Penanganan event.
3. Animasi dan efek visual.
4. Mempermudah komunikasi dengan server melalui Ajax.
5. Menyederhanakan operasi DOM.

---

### **II. jQuery Selector**

**Selector** adalah fitur utama jQuery yang memungkinkan Anda untuk memilih elemen-elemen dalam dokumen HTML berdasarkan kriteria tertentu. jQuery selector hampir mirip dengan CSS selector, namun jQuery mempermudah akses ke elemen-elemen tersebut untuk dimanipulasi dengan lebih cepat.

#### **1. Dasar Selector**
- **Selector ID**: Memilih elemen berdasarkan ID.
  ```javascript
  $('#elementId')
  ```
  Contoh:
  ```javascript
  $('#header').css('color', 'red');
  ```
- **Selector Kelas (Class)**: Memilih elemen berdasarkan kelas.
  ```javascript
  $('.className')
  ```
  Contoh:
  ```javascript
  $('.menu').hide();
  ```

- **Selector Tag**: Memilih elemen berdasarkan tag HTML.
  ```javascript
  $('div')
  ```
  Contoh:
  ```javascript
  $('p').css('font-size', '20px');
  ```

- **Selector Gabungan**: Memilih elemen berdasarkan kombinasi ID, kelas, dan tag.
  ```javascript
  $('#myId .myClass p')
  ```

#### **2. Selector Lanjutan**
- **:first**: Memilih elemen pertama dari sebuah koleksi.
  ```javascript
  $('li:first')
  ```

- **:last**: Memilih elemen terakhir dari sebuah koleksi.
  ```javascript
  $('li:last')
  ```

- **:eq(index)**: Memilih elemen pada posisi tertentu dalam koleksi.
  ```javascript
  $('li:eq(2)')
  ```

- **:even** dan **:odd**: Memilih elemen dengan nomor urut genap atau ganjil.
  ```javascript
  $('li:even')
  ```

- **:not(selector)**: Memilih elemen yang tidak cocok dengan selector yang diberikan.
  ```javascript
  $('li:not(.active)')
  ```

- **:contains(text)**: Memilih elemen yang berisi teks tertentu.
  ```javascript
  $('p:contains("Hello")')
  ```

---

### **III. jQuery Event**

**Event** dalam jQuery digunakan untuk menangani interaksi pengguna dengan elemen-elemen dalam halaman web, seperti klik, hover, perubahan input, dan lain-lain. jQuery menyediakan cara yang lebih mudah dan ringkas untuk menangani event dibandingkan dengan JavaScript murni.

#### **1. Menangani Event**
Untuk menangani event, Anda dapat menggunakan metode seperti `.click()`, `.hover()`, `.keyup()`, dll.

Contoh sederhana menangani event klik:
```javascript
$('#myButton').click(function() {
  alert('Button clicked!');
});
```

#### **2. Jenis-jenis Event dalam jQuery**
- **Click Event**: Terjadi saat pengguna mengklik elemen.
  ```javascript
  $('button').click(function() {
    alert('Button clicked!');
  });
  ```

- **Hover Event**: Digunakan untuk menangani dua event sekaligus, `mouseenter` dan `mouseleave`.
  ```javascript
  $('#myElement').hover(
    function() {
      $(this).css('background-color', 'blue');
    },
    function() {
      $(this).css('background-color', 'white');
    }
  );
  ```

- **Keypress dan Keyup**: Digunakan untuk menangani event saat pengguna mengetik di input field.
  ```javascript
  $('#myInput').keyup(function() {
    console.log('Key pressed: ' + $(this).val());
  });
  ```

- **Submit Event**: Terjadi saat form disubmit.
  ```javascript
  $('form').submit(function(e) {
    e.preventDefault(); // Mencegah form untuk submit secara default
    alert('Form Submitted!');
  });
  ```

#### **3. Menambah dan Menghapus Event Handler**
jQuery menyediakan cara mudah untuk menambah dan menghapus handler event.

- **Menambah Event Handler**:
  ```javascript
  $('#myElement').on('click', function() {
    alert('Element clicked');
  });
  ```

- **Menghapus Event Handler**:
  ```javascript
  $('#myElement').off('click');
  ```

#### **4. Event Delegation**
Jika Anda menambahkan elemen baru secara dinamis setelah halaman dimuat, Anda bisa menggunakan event delegation untuk menangani event pada elemen-elemen yang baru dibuat.

Contoh:
```javascript
$('#parentDiv').on('click', '.childDiv', function() {
  alert('Child div clicked!');
});
```

Dalam hal ini, meskipun elemen `.childDiv` mungkin ditambahkan setelah halaman dimuat, event handler tetap dapat menangani klik pada elemen tersebut.

#### **5. Event Propagation dan Bubbles**
Event dalam DOM mengikuti alur "bubbling" atau penggelembungan, yang berarti event dimulai dari elemen target dan "menggelembung" ke elemen induk. Anda dapat mengontrol perilaku ini menggunakan metode `stopPropagation()` dan `preventDefault()`.

- **stopPropagation**: Mencegah event untuk menggelembung ke elemen induk.
  ```javascript
  $('#childElement').click(function(event) {
    event.stopPropagation();
  });
  ```

- **preventDefault**: Mencegah perilaku default elemen, seperti pengiriman form.
  ```javascript
  $('form').submit(function(event) {
    event.preventDefault();
    alert('Form not submitted!');
  });
  ```

---

### **IV. Kombinasi Selector dan Event**

Anda bisa menggabungkan penggunaan selector dengan event handling untuk lebih efektif dalam manipulasi elemen.

Contoh:
```javascript
$('ul li').click(function() {
  $(this).css('color', 'red');
});
```
Pada contoh di atas, setiap kali salah satu elemen `<li>` diklik, teksnya akan berubah menjadi merah.

---

### **V. Praktikum dan Contoh Kasus**

#### **Kasus 1: Membuat Dropdown Menu**
Gunakan jQuery untuk menampilkan dropdown menu ketika elemen tertentu diklik.
```javascript
$('#dropdownButton').click(function() {
  $('#dropdownMenu').toggle();
});
```

#### **Kasus 2: Mengubah Konten dengan Input**
Gunakan event input untuk mengubah konten paragraf berdasarkan input pengguna.
```javascript
$('#inputField').on('input', function() {
  $('#output').text($(this).val());
});
```

---

### **VI. Kesimpulan**

- **Selector jQuery** memungkinkan kita untuk memilih elemen dengan cara yang sangat fleksibel dan mudah, memanfaatkan kombinasi ID, kelas, tag, dan selektor lanjutan.
- **Event handling** dengan jQuery sangat menyederhanakan cara kita menangani interaksi pengguna di halaman web, termasuk penanganan event klik, hover, input, dan banyak lagi.
- Dengan menggunakan selector dan event handling secara bersama-sama, kita bisa membuat interaksi web yang dinamis dan responsif.

---

### **Tugas Praktikum:**
1. Implementasikan menu dropdown menggunakan jQuery.
2. Buatlah form dengan input dan tampilkan hasil input menggunakan jQuery.
3. Tambahkan beberapa event lainnya (click, hover, focus) pada elemen-elemen halaman.

---

Semoga materi ini dapat membantu dalam memahami dasar penggunaan jQuery, terutama dalam hal selector dan event handling!
