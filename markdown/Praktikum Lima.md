# Praktikum Lima: Atribut dan Izin Akses File dan Direktori.

![permissions](img/permissions.png)

## Outline

- [Mengubah Izin Akses.](##Mengubah Izin Akses)
- [Mengubah User dan Group Pemilik File.](##Mengubah User dan Group Pemilik File)
- [Pengaruh Izin Akses pada File.](##Pengaruh Izin Akses pada File)
- [Challenge.](##Challenge)

## Mengubah Izin Akses

#### Teori

**1. Atribut File**

Setiap file memiliki atribut yang berisi keterangan tentang file tersebut.

- Cek atribut file: `ls -l`.

![atribut-file](img/atribut-file.png)

**2. Izin Akses File**

Izin akses untuk file terdiri dari 9 karakter yang dikelompokkan menjadi 3 bagian.

3 Bagian tersebut:

- 3 karaker pertama untuk user pemilik file.
- 3 karakter kedua untuk group pemilik file.
- 3 karakter ketiga untuk other (selain user dan group).

![izin-akses](img/izin-akses.png)

Keterangan:

- R (READ): Membaca File / Direktori.
- W (WRITE): Mengubah File / Direktori.
- X (EXECTURE): Mengeksekusi File / Masuk Direktori

**3. Mengubah Izin Akses**

Mengubah izin akses suatu file menggunakan perintah `chmod`.

`chmod` memiliki 2 cara untuk mengubah file:

1. Format Huruf.

   Syntax: `chmod [ugoa] [+-=] [rwx] nama-file`.

2. Format Angka.

   Syntax: `chmod [kode user] [kode group] [kode other] nama-file`.

   ![format-angka](img/format-angka.png)

Selesai.

#### Praktikum

**Mengubah Izin Akses**

**1. Format Angka**

- Buat file index.html: `touch index.html`.

- Lihat informasi file: `ls -l index.html`.

- Tambahkan u (user) hak akses x (excetute): `chmod u+x index.html`.

- Lihat informasi file: `ls -l index.html`.

- Kurangkan g (group) hak akses w (write): `chmod g-w index.html`.

- Lihat informasi file: `ls -l index.html`.

- Tambahkan g (group) dan other (other) hak akses x (execute):

  `chmod g+x, o+x index.html` atau `chmod go+x index.html`.

- Beri u (user), g (group), dan o (other) hak akses r (read) dan w (write):

  `chmod ugo=rw index.html`.

- Lihat informasi file: `ls -l index.html`.

**2. Format Huruf**

- Beri u (user), g (group), o (other) hak akses 644:

  `chmod 644 index.html`.

- Beri hak akses 64: `chmod 64 index.html`.

- Beri hak akses 6: `chmod 6 index.html`.

## Mengubah User dan Group Pemilik File

#### Teori

**1. Mengubah User pemilik file.**

Mengubah user pemilik file menggunakan perintah: `chown`.

Syntax: `chown [user-baru] nama-file`.

**2. Mengubah Group pemilik file.**

Mengubah user pemilik file menggunakan perintah: `chgrp`.

Syntax: `chown [group-baru] nama-file`.

#### Praktikum

- Membuat user alex: `sudo useradd -m alex`.
- Membuat file style.css: `touch style.css`.
- Cek informasi file: `ls -l style.css`.
- Mengubah pemilik file (user) menjadi alex: `chown alex style.css`.
- Cek informasi file: `ls -l style.css`.
- Mengubah pemilik file (group) menjadi alex: chgrp alex style.css
- Cek informasi file: `ls -l style.css`.

## Pengaruh Izin Akses pada File

**1. Pengaruh r (read) pada file**

File dapat dibaca jika memiliki akses r (read) namun tidak dapat dibaca jika tidak memiliki akses r (read) .

- Buat file latihan: `touch latihan`.
- Tambahkan kalimat: `Belajar izin akses file`.
- Cek informasi file: `ls -l latihan`.
- Baca file latihan: `cat latihan`.
- Hilangkan u (user) hak akses r (read): `chmod u-r latihan`.
- Cek informasi file: `ls -l latihan`.
- Baca file latihan: `cat latihan`.
- Tambahkan kembali u (user) hak akses r (read): `chmod u+r latihan`.
- Cek informasi file: `ls -l latihan`.

**2. Pengaruh w (write) pada file**

File dapat ditulis / diedit jika memiliki akses w (Write) namun tidak dapat diedit jika tidak memiliki akses w (Write) .

- Cek informasi file: `ls -l latihan`.
- Tambahkan kalimat: `File masih bisa diedit`.
- Hilangkan u (user) hak akses w (write): `chmod u-w latihan`.
- Cek informasi file: `ls -l latihan`.
- Buka file, tambahkan kalimat: `Mencoba mengedit file`.
- Save file tersebut.
- Tambahkan kembali u (user) hak akses w (write): `chmod u+w latihan`.
- Cek informasi file: `ls -l latihan`.

**3. Pengaruh x (execute) pada file**

File dapat dieksekusi / dijalankan jika memiliki akses x (Execute) namun tidak dapat dieksekusi jika tidak memiliki akses x (Execute) .

- Buat file cekuser: `touch cekuser`.
- Tambahkan kalimat: `who`.
- Lihat informasi file cekuser: `ls -l cekuser`.
- Eksekusi file cekuser: `./cekuser`.
- Tambahkan u (user) hak akses x (execute): `chmod u+x cekuser`.
- Eksekusi kembali file cekuser: ./cekuser.

## Challenge

1. Buat file latihan dan berikan hak akses seperti berikut (format huruf).

   ![challenge-satu](img/challenge-satu.png)

2. Buat file latihan dan berikan hak akses seperti berikut (format angka).

   ![challenge-dua](img/challenge-dua.png)

3. Buat file latihan dan ganti user dan group tersebut seperti berikut

   ![challenge-tiga](img/challenge-tiga.png)

4. Mengapa file atau direktori memerlukan hak akses?

5. Apa evaluasi praktikum lima? apa masukan dan saran?