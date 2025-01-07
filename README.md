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


---

