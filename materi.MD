# Belajar Git Dasar

Materi dari Programmer Zaman Now

## Inisialisasi Project Git

```console
git init
```

## Melihat Status

```console
git status
```

## Menambah file

```console
git add nama_file
```

## Commit ke Repository

```console
git commit -m "MASUKKAN PESAN COMMIT"
```

## Melihat Perubahan Git

```console
git diff
```

## Membatalkan Penambahan File

```console
git clean -f
```

## Membatalkan Perubahan File

```console
git restore namafile
```

## Membatalkan Penghapusan File

```console
git restore namafile
```

## Membatalkan dari Staging Index

Karena git restore hanya bisa dilakukan untuk membatalkan perubahan yang terjadi di **Working Directory**. Kita menggunakan `--staged` untuk mengembalikan posisi dari **staging index** ke **working directory**.

```console
git restore --staged namafile
```
