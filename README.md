# Lab7Web_PHP

Latihan 1 - Menjalankan PHP

untuk menjalankan php saya memakai Laragon yang menyediakan PHP, jadi saya membuat file index.php dahulu di dalam folder htdocs/lab7_php, lalu saya menaruh foldernya di bagian www untuk dijalankan sebagai localhost
<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/398b5ea4-e6bb-4082-9178-2f2a178a43b6" />

lalu untuk menjalankannya cukup memasukkan link http://namafolder.test, lalu saya memasukkan kode yang berada di dalam modul dan berhasil membukanya lewat localhost
```php
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<title>Praktikum PHP</title>
</head>
<body>
<h5>Latihan 1 </h5>   
<h1>Belajar PHP</h1>
<?php
echo "<p>PHP berhasil dijalankan.</p>";
echo "<p>Waktu server: " . date("d-m-Y H:i:s") . "</p>";
?>
```

<img width="260" height="122" alt="image" src="https://github.com/user-attachments/assets/1310bdcd-06b1-4e70-ab4b-91698a128aa9" />


Latihan 2 — Variabel, operator, dan percabangan

jadi di latihan ini adalah kita memasukkan variabel lalu di operasikan dengan rata-rata yang dimana outputnya itu menggunakan if-else untuk predikatnya

```php
<?php
$nama = "Siti";
$tugas = 85;
$uts = 78;
$uas = 90;
$nilaiAkhir = ($tugas * 0.30) + ($uts * 0.30) + ($uas * 0.40);
if ($nilaiAkhir >= 85) {
$predikat = "A";
} elseif ($nilaiAkhir >= 75) {
$predikat = "B";
} elseif ($nilaiAkhir >= 60) {
$predikat = "C";
} else {
$predikat = "D";
}
echo "Nama: " . htmlspecialchars($nama) . "<br>";
echo "Nilai akhir: " . number_format($nilaiAkhir, 2) . "<br>";
echo "Predikat: " . $predikat;
?>
```

nah jadi untuk contoh dari modul disini adalah mengambil nilai akhir yang dimana rata-ratanya terdiri dari 3 bagian yaitu tugas, uts, uas, jadi ketika rata ratanya sudah ada hasilnya maka akan masuk ke if-else untuk mengambil predikat yang dimana ketika nilai diatas 85 maka mendapat A, jika diatas 75 mendapat B, jika diatas 60 mendapat C, jika dibawah 60 maka D

<img width="185" height="71" alt="image" src="https://github.com/user-attachments/assets/f6d7fd45-5bc0-4fab-b7c6-2651c3b5f9fa" />

berikut adalah contoh yang dimana siti mendapatkan nilai rata-rata 84.90 dan mendapatkan nilai B karena diatas 75

Latihan 3 — Perulangan dan array

```php
<?php
$mahasiswa = ["Alya", "Bima", "Citra", "Doni"];
echo "<h3>Daftar Mahasiswa</h3><ol>";
foreach ($mahasiswa as $nama) {
echo "<li>" . htmlspecialchars($nama) . "</li>";
}
echo "</ol>";
?>
```

dilatihan 3 disini kita belajar array dalam php yaitu foreach yang dimana fungsinya adalah membuat sebuah list, sebagai contoh dalam kodenya disini menggunakan <li></li> yang dimana berfungsi untuk membuat list berurutan, seperti pada gambar berikut yang sudah ditambahi 3 nama lagi

<img width="143" height="134" alt="image" src="https://github.com/user-attachments/assets/48cddfa6-0b18-465e-9744-1c49eef901ac" />

Latihan 4 — Membuat function
```php
<?php
function hitungDiskon($harga, $persen) {
$potongan = $harga * ($persen / 100);
return $harga - $potongan;
}
$hargaAkhir = hitungDiskon(150000, 10);
echo "Harga setelah diskon: Rp" . number_format($hargaAkhir, 0, ",", ".");
?>
```

dilatihan ini saya belajar membuat sebuah function yang berfungsi untuk menghitung sebuah rumus untuk contoh yang diatas adalah rumus harga setelah terkena diskon

untuk function yang saya buat sendiri adalah function menghitung luas persegi panjang
```php
<?php
function hitungluaspersegipanjang($panjang, $lebar)
{
    return $panjang * $lebar;
}
$Luaspersegipanjang = hitungluaspersegipanjang(10,5);
echo "Luas persegi panjang adalah :" . number_format($Luaspersegipanjang);
?>
```
jadi untuk rumusnya kita taruh dibagian function untuk outputnya kita atur di bagian echo yang fungsinya sama seperti print di python

<img width="260" height="52" alt="image" src="https://github.com/user-attachments/assets/992148fe-aa6b-440c-b1d8-04380725b4b4" />

Latihan 5 — Memproses form dengan GET
```php
<!-- cari.php -->
<form method="GET" action="">
<label for="kata">Kata kunci:</label>
<input id="kata" name="kata" type="text">
<button type="submit">Cari</button>
</form>
<?php
if (isset($_GET["kata"])) {
$kata = trim($_GET["kata"]);
echo "Kata kunci: " . htmlspecialchars($kata, ENT_QUOTES, "UTF-8");
}
?>
```

jadi dilatihan ini kita belajar mengisi form di PHP yang menggunakan GET untuk mengirimkan sebuah form, dan jangan gunakan GET untuk mengirimi data sensitif karena dengan GET kita dapat melihat apa yang kita isi dan mudah bocor

<img width="194" height="61" alt="image" src="https://github.com/user-attachments/assets/5174b934-fa43-464e-8122-d2a61ec7f090" />

Latihan 6 — Memproses form dengan POST
```php
<!-- index.php -->
<form method="POST" action="">
<label for="nama">Nama:</label>
<input id="nama" name="nama" type="text" required>
<label for="prodi">Program Studi:</label>
<input id="prodi" name="prodi" type="text" required>
<button type="submit" name="kirim">Kirim Data</button>
</form>
<?php
if ($_SERVER["REQUEST_METHOD"] === "POST") {
$nama = trim($_POST["nama"] ?? "");
$prodi = trim($_POST["prodi"] ?? "");
if ($nama === "" || $prodi === "") {
echo "<p>Semua kolom wajib diisi.</p>";
} else {
echo "<h3>Data diterima</h3>";
echo "Nama: " . htmlspecialchars($nama, ENT_QUOTES, "UTF-8") . "<br>";
echo "Program Studi: " . htmlspecialchars($prodi, ENT_QUOTES, "UTF-8");
}
}
?>
```

jadi dilatihan ini kita akan menguji sebuah logika untuk pengiriman sebuah form, jadi yang dimana ketika kita mengosongkan kolom kita kita akan mendapatkan peringatan yang sudah kita buat dalam if

<img width="326" height="67" alt="image" src="https://github.com/user-attachments/assets/a5ab8631-4eda-46fb-a438-ba59c38ef981" />

dan untuk output ketika kita mengisi formnya adalah seperti ini

<img width="343" height="89" alt="image" src="https://github.com/user-attachments/assets/89a8d5eb-5c18-4c47-afb2-708274a4b718" />

Latihan 7 — Pengolahan data sederhana
```php
<?php
$hasil = null;
if ($_SERVER["REQUEST_METHOD"] === "POST") {
$barang = trim($_POST["barang"] ?? "");
$hargaInput = $_POST["harga"] ?? "";
$jumlahInput = $_POST["jumlah"] ?? "";
if ($barang === "" || !is_numeric($hargaInput) ||
!ctype_digit((string)$jumlahInput) ||
(float)$hargaInput < 0 || (int)$jumlahInput < 1) {
$error = "Periksa kembali nama barang, harga, dan jumlah.";
} else {
$harga = (float)$hargaInput;
$jumlah = (int)$jumlahInput;
$subtotal = $harga * $jumlah;
}
}
?>
<form method="POST">
<label>Nama barang <input name="barang" required></label>
<label>Harga <input name="harga" type="number" min="0" step="0.01" required></label>
<label>Jumlah <input name="jumlah" type="number" min="1" step="1" required></label>
<button type="submit">Hitung</button>
</form>
<?php
if (isset($error)) {
echo "<p>" . htmlspecialchars($error) . "</p>";
} elseif (isset($subtotal)) {
echo "<p>Barang: " . htmlspecialchars($barang) . "</p>";
echo "<p>Subtotal: Rp" . number_format($subtotal, 0, ",", ".") . "</p>";
}
?>
```

dilatihan ini kita akan menguji sebuah kode diatas yang dimana merupakan sebuah kode untuk memasukkan sebuah data yang dimana datanya dihitung dulu sebelum dimasukkan ke database

<img width="428" height="80" alt="image" src="https://github.com/user-attachments/assets/3a42de7c-7f2b-4365-9474-4464a3f63055" />

gambar diatas adalah contoh bagaimana kita memasukkan sebuah data kedalam formnya untuk dihitung terlebih dahulu

<img width="434" height="80" alt="image" src="https://github.com/user-attachments/assets/fb6ebf51-9cd9-4d7a-9214-a0750ab789a4" />

gambar diatas adalah output dari data yang kita masukkan, subtotal adalah hasil dari harga dikali jumlah barangnya

<img width="419" height="79" alt="image" src="https://github.com/user-attachments/assets/c616ba19-8514-44de-9875-e852dd8d83fd" />

ketika kita memasukkan angka 0 atau -, maka tidak bisa dihitung karena jumlah barangnya tidak ada

