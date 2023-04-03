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

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Data Mahasiswa</title>

  <!-- CSS -->
  <style>
body {
  font-family: monospace;
  margin: 0;
  padding: 0;
  background-color: #f2f2f2;
}

h1 {
  text-align: center;
  margin-top: 0;
  margin-bottom: 20px;
  padding-top: 14px;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-bottom: 20px;
  box-shadow: 0px 0px 10px rgba(0,0,0,0.1);
  font-family: monospace;
}

thead {
  background-color: #27E1C1;
  color: #fff;
}

th, td {
  padding: 10px;
  text-align: left;
  border: 1px solid #1b1a1a;
}

tr:nth-child(even) {
  background-color: #FFB4B4;
}

.btn {
  display: inline-block;
  padding: 8px 16px;
  background-color: #4CAF50;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  text-align: center;
  text-decoration: none;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #3e8e41;
}

a {
  text-decoration: none;
}
	</style>
</head>
<body>
  <h1>Table Mahasiswa</h1>
  <table>
    <thead>
      <tr>
        <th>No.</th>
        <th>Kehadiran</th>
        <th>NIM</th>
        <th>Nama</th>
        <th>Action</th>
      </tr>
    </thead>
    <tbody>
      <?php
      for ($i = $start_index; $i <= $end_index && $i < $total_absensi; $i++) {
        echo '<tr>';
        echo '<td>' . ($i + 1) . '</td>';
        if ($absensi[$i]['1'] == 'M') {
          echo "<td>Masuk</td>";
        } else if ($absensi[$i]['1'] == 'S') {
          echo "<td>Sakit</td>";
        } else if ($absensi[$i]['1'] == 'I') {
          echo "<td>Izin</td>";
        } else if ($absensi[$i]['1'] == '-') {
          echo "<td>Tidak Masuk</td>";
        } else {
          echo "<td>" . $absensi[$i]['1'] . "</td>";
        }
        echo '<td>' . $absensi[$i]['NIM'] . '</td>';
        echo '<td>' . $absensi[$i]['Nama'] . '</td>';
        echo '<td><button class="btn" onclick="showModal(' . $absensi[$i]['NO'] . ')">Lihat Detail</button></td>';
        echo '</tr>';
      }
      echo '</tbody>';
      echo '</table>';

      echo '<div class="pagination">';
      echo '<a href="?page=1">&laquo;First </a>';
      for ($i = 1; $i <= $total_halaman; $i++) {
        echo '<a href="?page=' . $i . '"';
        if ($i == $page) {
          echo ' class="active"';
        }
        echo '> ' . $i . '  </a>';
      }
      echo '<a href="?page=' . $total_halaman . '"> &raquo;Last</a>';
      echo '</div>';
    ?>
</body>
</html>

# Langkah kedua

Untuk Mengirim data ke dalam table, menggunakan link : https://api.steinhq.com/v1/storages/642a1ee5eced9b09e9c762e8/21a1

Dengan Cara seperti ini

$url = 'https://api.steinhq.com/v1/storages/642a1ee5eced9b09e9c762e8/21a1';

# Langkah ketiga

Jika ingin memperindah table yang sudah dibuat, bisa menggunakan CSS 

Maka hasilnya akan seperti ini 

![Screenshot Table](https://user-images.githubusercontent.com/92637117/229396649-4e2bc4fb-a9fe-46cd-9593-79abec350409.png)

# Terimakasih

