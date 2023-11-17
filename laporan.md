# SQL DATA MANIPULATION LANGUAGE
Praktikum 3 - Amelia Vega - 225150600111021 - DBDSQL Kelas A
#
#
### TAHAP-TAHAP PENGERJAAN
Laporan ini dibagi menjadi 2 bagian. Pertama ada Data Definition yang berisi `create schema` dan `create table`. Adapun yang kedua yaitu Data Manipulation berisi `use schema` dan `insert into`.
#
#
### DATA DEFINITION
1. Membuat schema AKADEMIK

   Schema AKADEMIK digunakan untuk mengorganisasi dan mengelompokkan tabel yang terkait dengan data akademik.
   ```
   create schema AKADEMIK;
   ```

   ![schema](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/d0b574c4-6bfd-4cd1-9f77-94f5a0e5c028)

2. Buat table FAKULTAS

   Tabel FAKULTAS digunakan untuk menyimpan informasi tentang fakultas-fakultas yang ada di institusi akademik.
   ```
   create table AKADEMIK.FAKULTAS (
	ID_FAKULTAS smallint primary key,
	FAKULTAS VARCHAR(45)
   )
   ```
   ![fakultas](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/295db81b-9474-4795-b38e-d364b6740842)

3. Buat tabel JURUSAN

   Tabel JURUSAN menyimpan informasi tentang jurusan-jurusan yang terkait dengan fakultas di institusi akademik.
   ```
   create table AKADEMIK.JURUSAN (
	ID_JURUSAN smallint not null primary key,
	ID_FAKULTAS smallint,
	JURUSAN VARCHAR(45),
	foreign key (ID_FAKULTAS) references AKADEMIK.FAKULTAS(ID_FAKULTAS)
   )
   ```
   ![jurusan](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/6d743991-7857-4be6-a8ce-d241539fffe3)

4. Buat tabel STRATA

   Tabel STRATA menyimpan informasi tentang tingkat pendidikan dalam konteks akademik.
   ```
   create table AKADEMIK.STRATA (
	ID_STRATA smallint not null primary key,
	SINGKAT VARCHAR(10),
	STRATA VARCHAR(45)
   )
   ```
   ![strata](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/d1ff3166-da8c-4135-8762-2f2eb88c7515)

5. Buat tabel PROGRAM_STUDI

   Tabel PRODI digunakan untuk menyimpan informasi tentang program studi yang terkait dengan jurusan di institusi akademik.
   ```
   create table AKADEMIK.PROGRAM_STUDI (
	ID_PROGRAM_STUDI smallint not null primary key,
	ID_STRATA smallint,
	ID_JURUSAN smallint,
	PROGRAM_STUDI VARCHAR(60),
	foreign key (ID_STRATA) references AKADEMIK.STRATA(ID_STRATA),
	foreign key (ID_JURUSAN) references AKADEMIK.JURUSAN(ID_JURUSAN)
   )
   ```
   ![prodi](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/4f8c0bb4-da0b-4ac1-af12-fbc28b446a9b)

6. Buat tabel SELEKSI_MASUK

   Tabel SELEKSI_MASUK digunakan untuk menyimpan informasi tentang proses seleksi masuk ke institusi akademik.
   ```
   create table AKADEMIK.SELEKSI_MASUK (
	ID_SELEKSI_MASUK smallint not null primary key,
	SINGKAT VARCHAR(12),
	SELEKSI_MASUK VARCHAR(60)
   )
   ```
   ![seleksi masuk](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/206ec251-ff48-4185-972d-0eabb3d8240a)

7. Buat tabel MAHASISWA

   Tabel MAHASISWA digunakan untuk menyimpan informasi tentang mahasiswa-mahasiswa yang terdaftar di institusi akademik.
   ```
   create table AKADEMIK.MAHASISWA (
	NIM VARCHAR(15) not null primary key,
	ID_SELEKSI_MASUK smallint,
	ID_PROGRAM_STUDI smallint,
	NAMA VARCHAR(45),
	ANGKATAN smallint,
	TGL_LAHIR DATE,
	KOTA_LAHIR VARCHAR(60),
	JENIS_KELAMIN CHAR(1),
	foreign key (ID_SELEKSI_MASUK) references AKADEMIK.SELEKSI_MASUK(ID_SELEKSI_MASUK),
	foreign key (ID_PROGRAM_STUDI) references AKADEMIK.PROGRAM_STUDI(ID_PROGRAM_STUDI)
	foreign key (ID_SELEKSI_MASUK) references AKADEMIK.SELEKSI_MASUK(ID_SELEKSI_MASUK)
   )
   ```
   ![mahasiswa](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/f290bbaa-59c7-40c8-a65e-1b672b4e6ec3)  
#
#
### DATA MANIPULATION 
1. Run script use AKADEMIK

   Perintah USE digunakan untuk memilih database yang akan digunakan dalam operasi manipulasi data.
    ```
    use AKADEMIK;
    ```
    ![use](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/ba5e9b77-4116-4d7e-9ef4-19fcbbf5e40c)

2. Insert into FAKULTAS

   Perintah INSERT into ... digunakan untuk memasukkan data baru ke dalam tabel tertentu (berlaku dari poin 2 sampai poin 7).
    ```
    insert into FAKULTAS(ID_FAKULTAS, FAKULTAS) values (1, 'Ekonomi & Bisnis'), (2, 'Ilmu Komputer');
    ```
    ![insert fakultas](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/be21cdfd-b522-4949-bbff-e80b8fca30ab)

3. Insert into JURUSAN
    ```
    insert into JURUSAN(ID_JURUSAN, ID_FAKULTAS, JURUSAN) values (21, 2, 'Informatika'), (22, 2, 'Sistem Informasi'), (23, 2, 'Teknik Komputer');
    ```
    ![insert jurusan](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/ad89c884-0ede-4fbc-8a53-dc2633e42278)

4. Insert into STRATA
    ```
    insert into STRATA(ID_STRATA, SINGKAT, STRATA) values (1, 'D1', 'Diploma'), (2, 'S1', 'Sarjana'), (3, 'S2', 'Magister');
    ```
    ![insert strata](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/5b6533d9-2c37-4eb3-83c6-5d41faf32b5c)

5. Insert into PROGRAM_STUDI
    ```
    insert into PROGRAM_STUDI(ID_PROGRAM_STUDI, ID_STRATA, ID_JURUSAN, PROGRAM_STUDI) values (211, 2, 21, 'Teknik Informatika'), (212, 2, 21, 'Teknik Komputer'), (219, 3, 21, 'Magister Ilmu Komputer');
    ```
    ![insert prodi](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/44865c6e-2ed6-4b07-9e6a-fb67a46a56ba)

6. Insert into SELEKSI_MASUK
    ```
    insert into SELEKSI_MASUK(ID_SELEKSI_MASUK, SINGKAT, SELEKSI_MASUK) values (1, 'SNMPTN', 'SELEKSI NASIONAL MAHASISWA PERGURUAN TINGGI NEGERI'), (2, 'SBMPTN', 'SELEKSI BERSAMA MAHASISWA PERGURUAN TINGGI NEGERI');
    ```
    ![insert seleksi masuk](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/c8c105b0-82c2-4010-8e22-e7ec96df84ee)

7. Insert into MAHASISWA
    ```
    insert into MAHASISWA(NIM, ID_SELEKSI_MASUK, ID_PROGRAM_STUDI, NAMA, ANGKATAN, TGL_LAHIR, KOTA_LAHIR, JENIS_KELAMIN) values ('225150600111021', 1, 211, 'NANA', 2022, '2003-03-01', 'Jakarta', 'W'), ('235150600111021', 2, 212, 'ANTO', 2023, '2005-10-02', 'Balikpapan', 'P');
    ```
    ![insert mahasiswa](https://github.com/AmeliaVegaa/Amelia-Vega_Praktikum-DBDSQL_Tugas-3/assets/133181467/b3cbe75b-4982-4a5b-a68f-7ddd4d01d7b9)
