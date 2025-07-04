# uas_basisdataLeni

# 🎓 Sistem Akademik Mini - Universitas Pelita Bangsa

## 📌 Output yang Dikumpulkan

✅ **Folder project web** (`.php`, `.css`, `.js`, dll.)  
✅ **File backup database MySQL** (`.sql`)  
✅ **Dokumentasi singkat dalam README ini berisi:**
- Struktur tabel
- Penjelasan fitur
- Screenshot tampilan aplikasi
- Cuplikan fungsi SQL/UDF yang digunakan

---

## 🗄️ Struktur Tabel

### 🧑‍🎓 Mahasiswa
- `nim` (VARCHAR, PK)
- `nama` (VARCHAR)
- `alamat` (TEXT)

### 👨‍🏫 Dosen
- `kd_ds` (VARCHAR, PK)
- `nama` (VARCHAR)

### 📚 Matakuliah
- `kd_mk` (VARCHAR, PK)
- `nama` (VARCHAR)
- `sks` (INT)

### 🗓️ Jadwal Mengajar
- `kd_mk` (VARCHAR, FK)
- `kd_ds` (VARCHAR, FK)
- `hari` (VARCHAR)
- `jam` (VARCHAR)
- `ruang` (VARCHAR)

### 📋 KRS Mahasiswa
- `nim` (VARCHAR, FK)
- `kd_mk` (VARCHAR, FK)
- `kd_ds` (VARCHAR, FK)
- `semester` (INT)
- `nilai` (CHAR)

---

## 🚀 Penjelasan Fitur

✅ Dashboard real-time dengan jam & quotes motivasi  
✅ Statistik Mahasiswa, Dosen, Matakuliah, Jadwal Mengajar, dan KRS  
✅ CRUD Mahasiswa, Dosen, Matakuliah  
✅ Laporan KRS dengan multi-table JOIN  
✅ Pencarian data dengan SQL LIKE  
✅ UI modern dengan Bootstrap 5  
✅ Desain responsif dengan animasi fade-in dan hover card

---

## 🖥️ Screenshot Tampilan Aplikasi

| Dashboard | Mahasiswa | Dosen |
|:---:|:---:|:---:|

<img src="/dashboard.png" width="500">|

<img src="/mahasiswa.png" width="500"> |

<img src="/dosen.png" width="500">|

<img src="/matakuliah.png" width="500">|

<img src="/jadwal.png" width="500">|

<img src="/krs.png" width="500">|

## 💻 Cuplikan Fungsi SQL/UDF yang Digunakan

```sql
-- Hitung jumlah data untuk dashboard
SELECT COUNT(*) AS total FROM mahasiswa;
SELECT COUNT(*) AS total FROM dosen;

-- Pencarian data
SELECT * FROM mahasiswa WHERE nama LIKE '%keyword%';

-- Laporan KRS dengan multi-table JOIN
SELECT m.nim, m.nama AS nama_mahasiswa, mk.nama AS nama_mk,
d.nama AS nama_dosen, jm.hari, jm.jam, jm.ruang
FROM krsmahasiswa km
JOIN mahasiswa m ON km.nim = m.nim
JOIN matakuliah mk ON km.kd_mk = mk.kd_mk
JOIN dosen d ON km.kd_ds = d.kd_ds
JOIN jadwalmengajar jm ON jm.kd_mk = km.kd_mk AND jm.kd_ds = km.kd_ds;


[def]: screenshots/krs.png
