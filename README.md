# Alfa_Express

## Group Members
- **Khalissa Raihana Azhari** (4523210124)
- **Muhammad Abiyu Muflih Az Arianto** (4523210124)




### Study Program
Bachelor of Informatics Engineering, Universitas Pancasila, Academic Year 2024/2025

---

## Features
- **Employee Management**: Track cashier and customer service staff information.
- **Store Management**: Manage minimarket locations and details.
- **Product Management**:  Track product inventory and categories.
- **Warehouse Management**: Handle warehouse operations and stock.
- **Transaction Inventory**: Process customer transactions.
- **Order Management**: Handle warehouse orders and stock requests.


---

## Database Setup

### 1. Create the Database
```sql
CREATE DATABASE alfa_express1 CHARACTER SET utf8 COLLATE utf8_general_ci;
```
![image](https://github.com/user-attachments/assets/62039615-97ae-475b-864e-32f20dd03796)


### 2. Create Tables

#### detail_order_warehouse
```sql
CREATE TABLE `detail_order_warehouse` (
  `id_order` int(11) DEFAULT NULL,
  `id_produk` int(11) DEFAULT NULL,
  `jumlah_order` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

```
![image](https://github.com/user-attachments/assets/ba975a3d-f722-46cc-aad2-09ca30f5e34a)


#### detail_transaksi
```sql
CREATE TABLE `detail_transaksi` (
  `id_bon` varchar(255) DEFAULT NULL,
  `id_produk` int(11) DEFAULT NULL,
  `jumlah_produk` int(11) DEFAULT NULL,
  `harga_produk` decimal(10,2) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
```
![image](https://github.com/user-attachments/assets/9806a52d-7d41-41e0-ab27-1915388b7afc)


#### karyawan
```sql
CREATE TABLE `karyawan` (
  `id_karyawan` int(11) NOT NULL,
  `nama_kasir` varchar(255) DEFAULT NULL,
  `nomor_kasir` varchar(255) DEFAULT NULL,
  `nomor_cs` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
```
![image](https://github.com/user-attachments/assets/27edc0b2-4ee6-44f2-92e0-00b466346a31)


#### minimarket
```sql
CREATE TABLE `minimarket` (
  `id_npwp` varchar(255) DEFAULT NULL,
  `id_minimarket` int(11) NOT NULL,
  `nama_minimarket` varchar(255) DEFAULT NULL,
  `alamat_minimarket` varchar(255) DEFAULT NULL,
  `no_telp_minimarket` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
```
![image](https://github.com/user-attachments/assets/eef93f0f-7d5d-4c9d-8c48-ce84dd2e966f)


#### order_produk_warehouse
```sql
CREATE TABLE `order_produk_warehouse` (
  `id_order` int(11) NOT NULL,
  `id_karyawan` int(11) DEFAULT NULL,
  `id_warehouse` int(11) DEFAULT NULL,
  `tanggal_order` date DEFAULT NULL,
  `nama_order` varchar(255) DEFAULT NULL,
  `status_order` enum('pending','accepted','declined') DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

```
![image](https://github.com/user-attachments/assets/554972e9-7d71-4882-b75f-7c72c587cba5)


#### Produk
```sql
CREATE TABLE `produk` (
  `id_produk` int(11) NOT NULL,
  `nama_produk` varchar(255) DEFAULT NULL,
  `kategori_produk` varchar(255) DEFAULT NULL,
  `harga_produk` decimal(10,2) DEFAULT NULL,
  `jumlah_produk` int(11) DEFAULT NULL,
  `id_warehouse` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

```
![image](https://github.com/user-attachments/assets/3e5b8fed-8557-40da-a27d-b7f7deb5b5f6)


#### transaksi
```sql
CREATE TABLE `transaksi` (
  `id_bon` varchar(255) NOT NULL,
  `id_karyawan` int(11) DEFAULT NULL,
  `id_minimarket` int(11) DEFAULT NULL,
  `tanggal_transaksi` date DEFAULT NULL,
  `waktu_transaksi` datetime DEFAULT NULL,
  `total_harga` decimal(10,2) DEFAULT NULL,
  `total_item` int(11) DEFAULT NULL,
  `ppn` decimal(5,2) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
```
![image](https://github.com/user-attachments/assets/fc94b214-587e-49b1-9a0f-0cf45a5c160f)

#### warehouse
```sql
CREATE TABLE `warehouse` (
  `id_warehouse` int(11) NOT NULL,
  `nama_warehouse` varchar(255) DEFAULT NULL,
  `alamat_warehouse` varchar(255) DEFAULT NULL,
  `no_telp_minimarket` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

```
![image](https://github.com/user-attachments/assets/12353e9c-6ca0-40df-8003-def650b86162)


---

## Input 20 data

### detail_order_warehouse
```sql
INSERT INTO `detail_order_warehouse` (`id_order`, `id_produk`, `jumlah_order`) VALUES
(1, 101, 50),
(1, 102, 30),
(2, 103, 40),
(2, 104, 25),
(3, 105, 20),
(3, 106, 35),
(4, 107, 45),
(4, 108, 50),
(5, 109, 60),
(5, 110, 70),
(6, 111, 30),
(6, 112, 40),
(7, 113, 25),
(7, 114, 35),
(8, 115, 20),
(8, 116, 45),
(9, 117, 55),
(9, 118, 60),
(10, 119, 50),
(10, 120, 70);
```
![image](https://github.com/user-attachments/assets/a8abada6-d0fb-4b2f-806b-2a88665d1bf9)

### detail_transaksi
```sql
INSERT INTO `detail_transaksi` (`id_bon`, `id_produk`, `jumlah_produk`, `harga_produk`) VALUES
('BON001', 101, 2, 3500.00),
('BON002', 102, 1, 4000.00),
('BON003', 103, 3, 9500.00),
('BON004', 104, 5, 3500.00),
('BON005', 105, 2, 2000.00),
('BON006', 106, 1, 25000.00),
('BON007', 107, 4, 12000.00),
('BON008', 108, 3, 17000.00),
('BON009', 109, 1, 24000.00),
('BON010', 110, 2, 18000.00),
('BON011', 111, 6, 6000.00),
('BON012', 112, 3, 8000.00),
('BON013', 113, 2, 12000.00),
('BON014', 114, 1, 35000.00),
('BON015', 115, 2, 32000.00),
('BON016', 116, 4, 4000.00),
('BON017', 117, 3, 15000.00),
('BON018', 118, 5, 3000.00),
('BON019', 119, 2, 9000.00),
('BON020', 120, 1, 15000.00);
```
![image](https://github.com/user-attachments/assets/67159bb7-4789-48fd-bdf4-9d0ec2993ec7)

### karyawan
```sql
INSERT INTO `karyawan` (`id_karyawan`, `nama_kasir`, `nomor_kasir`, `nomor_cs`) VALUES
(1, 'Andi Santoso', 'KSR001', 'CS001'),
(2, 'Budi Rahmat', 'KSR002', 'CS002'),
(3, 'Citra Dewi', 'KSR003', 'CS003'),
(4, 'Diana Putri', 'KSR004', 'CS004'),
(5, 'Eko Saputra', 'KSR005', 'CS005'),
(6, 'Fitri Ayu', 'KSR006', 'CS006'),
(7, 'Gilang Pratama', 'KSR007', 'CS007'),
(8, 'Hendra Wijaya', 'KSR008', 'CS008'),
(9, 'Indah Permata', 'KSR009', 'CS009'),
(10, 'Joko Riyadi', 'KSR010', 'CS010'),
(11, 'Kartika Sari', 'KSR011', 'CS011'),
(12, 'Lina Puspita', 'KSR012', 'CS012'),
(13, 'Maya Anggraini', 'KSR013', 'CS013'),
(14, 'Nina Wulandari', 'KSR014', 'CS014'),
(15, 'Oka Mahendra', 'KSR015', 'CS015'),
(16, 'Putri Lestari', 'KSR016', 'CS016'),
(17, 'Rendy Kusuma', 'KSR017', 'CS017'),
(18, 'Siti Nurhaliza', 'KSR018', 'CS018'),
(19, 'Taufik Hidayat', 'KSR019', 'CS019'),
(20, 'Umar Zulkarnain', 'KSR020', 'CS020');
```
![image](https://github.com/user-attachments/assets/b14a1455-3da3-4c7d-a4b4-2ee81175de94)

### minimarket
```sql
INSERT INTO `minimarket` (`id_npwp`, `id_minimarket`, `nama_minimarket`, `alamat_minimarket`, `no_telp_minimarket`) VALUES
('01.123.456.7-001.000', 1, 'Alfa Express Jakarta Pusat', 'Jl. Sudirman No. 45, Jakarta Pusat', '021-5556789'),
('02.234.567.8-002.000', 2, 'Alfa Express Bandung Timur', 'Jl. Asia Afrika No. 12, Bandung', '022-5432109'),
('03.345.678.9-003.000', 3, 'Alfa Express Surabaya Barat', 'Jl. Darmo Permai No. 89, Surabaya', '031-9876543'),
('04.456.789.0-004.000', 4, 'Alfa Express Medan Selatan', 'Jl. Sisingamangaraja No. 23, Medan', '061-7654321'),
('05.567.890.1-005.000', 5, 'Alfa Express Tangerang', 'Jl. Ahmad Yani No. 34, Tangerang', '021-6789101'),
('06.678.901.2-006.000', 6, 'Alfa Express Bekasi', 'Jl. Juanda No. 56, Bekasi', '021-1234567'),
('07.789.012.3-007.000', 7, 'Alfa Express Depok', 'Jl. Margonda Raya No. 78, Depok', '021-1122334'),
('08.890.123.4-008.000', 8, 'Alfa Express Bogor', 'Jl. Pajajaran No. 90, Bogor', '0251-4455667'),
('09.901.234.5-009.000', 9, 'Alfa Express Yogyakarta', 'Jl. Malioboro No. 101, Yogyakarta', '0274-9988776'),
('10.012.345.6-010.000', 10, 'Alfa Express Semarang', 'Jl. Pandanaran No. 11, Semarang', '024-5544332'),
('11.123.456.7-011.000', 11, 'Alfa Express Solo', 'Jl. Slamet Riyadi No. 55, Solo', '0271-8877665'),
('12.234.567.8-012.000', 12, 'Alfa Express Malang', 'Jl. Ijen Boulevard No. 33, Malang', '0341-7766554'),
('13.345.678.9-013.000', 13, 'Alfa Express Denpasar', 'Jl. Gatot Subroto No. 22, Denpasar', '0361-6677889'),
('14.456.789.0-014.000', 14, 'Alfa Express Balikpapan', 'Jl. MT Haryono No. 44, Balikpapan', '0542-3344556'),
('15.567.890.1-015.000', 15, 'Alfa Express Makassar', 'Jl. Pettarani No. 88, Makassar', '0411-5566774'),
('16.678.901.2-016.000', 16, 'Alfa Express Pontianak', 'Jl. Gajahmada No. 12, Pontianak', '0561-1122334'),
('17.789.012.3-017.000', 17, 'Alfa Express Palembang', 'Jl. Rajawali No. 65, Palembang', '0711-3344552'),
('18.890.123.4-018.000', 18, 'Alfa Express Pekanbaru', 'Jl. Sudirman No. 99, Pekanbaru', '0761-5566771'),
('19.901.234.5-019.000', 19, 'Alfa Express Padang', 'Jl. Khatib Sulaiman No. 77, Padang', '0751-8877664'),
('20.012.345.6-020.000', 20, 'Alfa Express Banda Aceh', 'Jl. Panglima Nyak Makam No. 88, Banda Aceh', '0651-6677883');
```
![image](https://github.com/user-attachments/assets/0982efbe-b299-4752-a2ae-ad5c8eac2ab8)

### order_produk_warehouse
```sql
INSERT INTO `order_produk_warehouse` (`id_order`, `id_karyawan`, `id_warehouse`, `tanggal_order`, `nama_order`, `status_order`) VALUES
(1, 1, 1, '2025-01-01', 'Order Produk 1', 'pending'),
(2, 2, 1, '2025-01-01', 'Order Produk 2', 'accepted'),
(3, 3, 2, '2025-01-02', 'Order Produk 3', 'declined'),
(4, 4, 2, '2025-01-02', 'Order Produk 4', 'pending'),
(5, 5, 3, '2025-01-03', 'Order Produk 5', 'accepted'),
(6, 6, 3, '2025-01-03', 'Order Produk 6', 'declined'),
(7, 7, 4, '2025-01-04', 'Order Produk 7', 'pending'),
(8, 8, 4, '2025-01-04', 'Order Produk 8', 'accepted'),
(9, 9, 5, '2025-01-05', 'Order Produk 9', 'declined'),
(10, 10, 5, '2025-01-05', 'Order Produk 10', 'pending'),
(11, 1, 6, '2025-01-06', 'Order Produk 11', 'accepted'),
(12, 2, 6, '2025-01-06', 'Order Produk 12', 'declined'),
(13, 3, 7, '2025-01-07', 'Order Produk 13', 'pending'),
(14, 4, 7, '2025-01-07', 'Order Produk 14', 'accepted'),
(15, 5, 8, '2025-01-08', 'Order Produk 15', 'declined'),
(16, 6, 8, '2025-01-08', 'Order Produk 16', 'pending'),
(17, 7, 9, '2025-01-09', 'Order Produk 17', 'accepted'),
(18, 8, 9, '2025-01-09', 'Order Produk 18', 'declined'),
(19, 9, 10, '2025-01-10', 'Order Produk 19', 'pending'),
(20, 10, 10, '2025-01-10', 'Order Produk 20', 'accepted');
```
![image](https://github.com/user-attachments/assets/89aa6cfd-5074-47c3-b8ed-51cb649df1c3)

### produk
```sql
INSERT INTO `produk` (`id_produk`, `nama_produk`, `kategori_produk`, `harga_produk`, `jumlah_produk`, `id_warehouse`) VALUES
(1, 'Aqua Botol 600ml', 'Minuman', 3500.00, 50, 1),
(2, 'Teh Botol Sosro', 'Minuman', 4000.00, 30, 1),
(3, 'Pop Mie Ayam Bawang', 'Makanan Instan', 9500.00, 40, 2),
(4, 'Indomie Goreng', 'Makanan Instan', 3500.00, 100, 2),
(5, 'Beng-Beng', 'Snack', 2000.00, 70, 3),
(6, 'SilverQueen Chunky Bar', 'Cokelat', 25000.00, 20, 3),
(7, 'Chitato Ayam Bakar', 'Snack', 12000.00, 35, 3),
(8, 'Lifebuoy Sabun Cair 250ml', 'Kebutuhan Rumah Tangga', 17000.00, 25, 4),
(9, 'Sampo Clear Men 170ml', 'Kebutuhan Pribadi', 24000.00, 15, 4),
(10, 'Rexona Roll On', 'Kebutuhan Pribadi', 18000.00, 20, 4),
(11, 'Ultra Milk Cokelat 200ml', 'Minuman', 6000.00, 60, 1),
(12, 'Roma Biskuit Kelapa', 'Snack', 8000.00, 50, 3),
(13, 'Yakult 5pcs', 'Minuman', 12000.00, 20, 1),
(14, 'Gatsby Styling Wax', 'Kebutuhan Pribadi', 35000.00, 10, 4),
(15, 'Baygon Semprot 300ml', 'Kebutuhan Rumah Tangga', 32000.00, 12, 4),
(16, 'Sprite 390ml', 'Minuman', 4000.00, 40, 1),
(17, 'Sari Roti Tawar', 'Roti', 15000.00, 30, 2),
(18, 'Good Day Cappuccino', 'Minuman', 3000.00, 100, 1),
(19, 'Tango Wafer Cokelat', 'Snack', 9000.00, 45, 3),
(20, 'Dettol Antiseptik 100ml', 'Kebutuhan Rumah Tangga', 15000.00, 20, 4);
```
![image](https://github.com/user-attachments/assets/aba92f8a-994b-445b-9652-98c5bb962248)

### transaksi
```sql
INSERT INTO `transaksi` (`id_bon`, `id_karyawan`, `id_minimarket`, `tanggal_transaksi`, `waktu_transaksi`, `total_harga`, `total_item`, `ppn`) VALUES
('BON001', 1, 1, '2025-01-01', '2025-01-01 10:15:00', 7500.00, 2, 10.00),
('BON002', 2, 1, '2025-01-01', '2025-01-01 10:30:00', 4000.00, 1, 10.00),
('BON003', 3, 2, '2025-01-01', '2025-01-01 11:00:00', 28500.00, 3, 10.00),
('BON004', 4, 2, '2025-01-01', '2025-01-01 11:45:00', 17500.00, 5, 10.00),
('BON005', 5, 3, '2025-01-01', '2025-01-01 12:00:00', 4000.00, 2, 10.00),
('BON006', 6, 3, '2025-01-02', '2025-01-02 09:15:00', 25000.00, 1, 10.00),
('BON007', 7, 4, '2025-01-02', '2025-01-02 09:30:00', 48000.00, 4, 10.00),
('BON008', 8, 4, '2025-01-02', '2025-01-02 10:00:00', 51000.00, 3, 10.00),
('BON009', 9, 5, '2025-01-02', '2025-01-02 10:30:00', 48000.00, 2, 10.00),
('BON010', 10, 5, '2025-01-02', '2025-01-02 11:00:00', 108000.00, 6, 10.00),
('BON011', 1, 6, '2025-01-03', '2025-01-03 08:45:00', 24000.00, 3, 10.00),
('BON012', 2, 6, '2025-01-03', '2025-01-03 09:15:00', 36000.00, 2, 10.00),
('BON013', 3, 7, '2025-01-03', '2025-01-03 09:45:00', 24000.00, 2, 10.00),
('BON014', 4, 7, '2025-01-03', '2025-01-03 10:30:00', 35000.00, 4, 10.00),
('BON015', 5, 8, '2025-01-03', '2025-01-03 11:00:00', 70400.00, 2, 10.00),
('BON016', 6, 8, '2025-01-04', '2025-01-04 09:00:00', 36000.00, 4, 10.00),
('BON017', 7, 9, '2025-01-04', '2025-01-04 09:30:00', 18000.00, 3, 10.00),
('BON018', 8, 9, '2025-01-04', '2025-01-04 10:15:00', 27000.00, 5, 10.00),
('BON019', 9, 10, '2025-01-04', '2025-01-04 10:45:00', 45000.00, 2, 10.00),
('BON020', 10, 10, '2025-01-04', '2025-01-04 11:30:00', 75000.00, 1, 10.00);
```
![image](https://github.com/user-attachments/assets/4e130680-a6a3-4bd4-9cbb-d71009320706)

### warehouse
```sql
INSERT INTO `warehouse` (`id_warehouse`, `nama_warehouse`, `alamat_warehouse`, `no_telp_minimarket`) VALUES
(1, 'Gudang Utama Jakarta', 'Jl. Sudirman No. 45, Jakarta', '021-5556789'),
(2, 'Gudang Alfa Bandung Timur', 'Jl. Asia Afrika No. 12, Bandung', '022-5432109'),
(3, 'Gudang Alfa Surabaya Barat', 'Jl. Darmo Permai No. 89, Surabaya', '031-9876543'),
(4, 'Gudang Alfa Medan Selatan', 'Jl. Sisingamangaraja No. 23, Medan', '061-7654321'),
(5, 'Gudang Alfa Tangerang', 'Jl. Ahmad Yani No. 34, Tangerang', '021-6789101'),
(6, 'Gudang Alfa Bekasi', 'Jl. Juanda No. 56, Bekasi', '021-1234567'),
(7, 'Gudang Alfa Depok', 'Jl. Margonda Raya No. 78, Depok', '021-1122334'),
(8, 'Gudang Alfa Bogor', 'Jl. Pajajaran No. 90, Bogor', '0251-4455667'),
(9, 'Gudang Alfa Yogyakarta', 'Jl. Malioboro No. 101, Yogyakarta', '0274-9988776'),
(10, 'Gudang Alfa Semarang', 'Jl. Pandanaran No. 11, Semarang', '024-5544332'),
(11, 'Gudang Alfa Solo', 'Jl. Slamet Riyadi No. 55, Solo', '0271-8877665'),
(12, 'Gudang Alfa Malang', 'Jl. Ijen Boulevard No. 33, Malang', '0341-7766554'),
(13, 'Gudang Alfa Denpasar', 'Jl. Gatot Subroto No. 22, Denpasar', '0361-6677889'),
(14, 'Gudang Alfa Balikpapan', 'Jl. MT Haryono No. 44, Balikpapan', '0542-3344556'),
(15, 'Gudang Alfa Makassar', 'Jl. Pettarani No. 88, Makassar', '0411-5566774'),
(16, 'Gudang Alfa Pontianak', 'Jl. Gajahmada No. 12, Pontianak', '0561-1122334'),
(17, 'Gudang Alfa Palembang', 'Jl. Rajawali No. 65, Palembang', '0711-3344552'),
(18, 'Gudang Alfa Pekanbaru', 'Jl. Sudirman No. 99, Pekanbaru', '0761-5566771'),
(19, 'Gudang Alfa Padang', 'Jl. Khatib Sulaiman No. 77, Padang', '0751-8877664'),
(20, 'Gudang Alfa Banda Aceh', 'Jl. Panglima Nyak Makam No. 88, Banda Aceh', '0651-6677883');
```
![image](https://github.com/user-attachments/assets/4e95eece-3d6f-42fb-8dc5-b796528a0a0c)


## Implementasi Transaksi
```sql
START TRANSACTION;

-- 1. Insert data transaksi ke tabel `transaksi`
INSERT INTO transaksi (
    id_bon, id_karyawan, id_minimarket, tanggal_transaksi, waktu_transaksi, total_harga, total_item, ppn
)
VALUES (
    'BON12345', 1, 1, CURDATE(), NOW(), 150000, 3, 10.00
);

-- 2. Insert detail transaksi ke tabel `detail_transaksi`
INSERT INTO detail_transaksi (
    id_bon, id_produk, jumlah_produk, harga_produk
)
VALUES
    ('BON12345', 1, 2, 50000.00),
    ('BON12345', 2, 1, 50000.00);

-- 3. Update stok produk di tabel `produk`
UPDATE produk
SET jumlah_produk = jumlah_produk - 2
WHERE id_produk = 1;

UPDATE produk
SET jumlah_produk = jumlah_produk - 1
WHERE id_produk = 2;

-- Validasi konsistensi: Periksa apakah stok produk valid (tidak negatif)
-- Jika ada stok yang negatif, rollback transaksi
IF EXISTS (
    SELECT 1
    FROM produk
    WHERE jumlah_produk < 0
) THEN
    ROLLBACK;
    SIGNAL SQLSTATE '45000' 
        SET MESSAGE_TEXT = 'Gagal: Stok tidak mencukupi';
ELSE
    -- Commit transaksi jika semua langkah berhasil
    COMMIT;
END IF;

```
## Skenario apabila ada kesalahan maka transaksi batal
```sql
DELIMITER $$

CREATE PROCEDURE proses_transaksi(
    IN bon_id VARCHAR(255),
    IN karyawan_id INT,
    IN minimarket_id INT,
    IN tanggal DATE,
    IN waktu DATETIME,
    IN total DECIMAL(10,2),
    IN item INT,
    IN ppn DECIMAL(5,2),
    INOUT error_status VARCHAR(255)
)
BEGIN
    -- Mulai transaksi
    DECLARE EXIT HANDLER FOR SQLEXCEPTION 
    BEGIN
        -- Rollback jika ada kesalahan
        ROLLBACK;
        SET error_status = 'Error: Transaksi dibatalkan';
    END;

    START TRANSACTION;

    -- 1. Insert data ke tabel transaksi
    INSERT INTO transaksi (id_bon, id_karyawan, id_minimarket, tanggal_transaksi, waktu_transaksi, total_harga, total_item, ppn)
    VALUES (bon_id, karyawan_id, minimarket_id, tanggal, waktu, total, item, ppn);

    -- 2. Insert data ke tabel detail_transaksi (contoh detail)
    INSERT INTO detail_transaksi (id_bon, id_produk, jumlah_produk, harga_produk)
    VALUES 
        (bon_id, 1, 3, 15000.00),
        (bon_id, 2, 5, 20000.00);

    -- 3. Update stok produk
    UPDATE produk 
    SET jumlah_produk = jumlah_produk - 3 
    WHERE id_produk = 1;

    UPDATE produk 
    SET jumlah_produk = jumlah_produk - 5 
    WHERE id_produk = 2;

    -- Jika tidak ada error, commit transaksi
    COMMIT;
    SET error_status = 'Success: Transaksi berhasil';
END$$

DELIMITER ;
```





