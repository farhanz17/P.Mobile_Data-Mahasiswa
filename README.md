# Membuat Table data menggunakan Rest API

## Profil
| #               | Biodata           |
| --------------- | ----------------- |
| **Nama**        | Muhammad Farhan   |
| **NIM**         | 312110128         |
| **Kelas**       | TI.21.A.1         |
| **Mata Kuliah** | P.Mobile 2        |

# Langkah Pertama

Membuat program terlebih dahulu

<?php

$url = 'https://api.steinhq.com/v1/storages/642a1ee5eced9b09e9c762e8/21a1';
$data = file_get_contents($url);
$absensi = json_decode($data, true);
$total_absensi = count($absensi);
$data_per_halaman = 10;
$total_halaman = ceil($total_absensi / $data_per_halaman);
$page = isset($_GET['page']) ? $_GET['page'] : 1;
$start_index = ($page - 1) * $data_per_halaman;
$end_index = $start_index + $data_per_halaman - 1;
?>

# Langkah kedua

Untuk Mengirim data ke dalam table, menggunakan link : https://api.steinhq.com/v1/storages/642a1ee5eced9b09e9c762e8/21a1

Dengan Cara seperti ini

$url = 'https://api.steinhq.com/v1/storages/642a1ee5eced9b09e9c762e8/21a1';

# Langkah ketiga

Jika ingin memperindah table yang sudah dibuat, bisa menggunakan CSS 

Maka hasilnya akan seperti ini 

![Screenshot Table](https://user-images.githubusercontent.com/92637117/229396649-4e2bc4fb-a9fe-46cd-9593-79abec350409.png)

# Terimakasih

