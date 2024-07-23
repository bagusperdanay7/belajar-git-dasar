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

## Melihat Commit Log

### Default Commit

```shell
git log
```

### Log Sederhana

Jika Ingin menampilkan tampilan log yang sederhana, gunakan `--oneline`.

```shell
git log --oneline
```

### Graph

Graph fungsinya untuk melihat hubungan commit log satu dengan sebelumnya.

```shell
git log --oneline --graph
```

### Detail Commit

`hash` diisi dengan hash dari commit yang dipilih.

```shell
git show hash
```

## Compare Commit

`hash1`, dan `hash2` adalah commit hash yang berbeda. Jadi membandingkan commit satu dengan commit lainnya.

```shell
git diff hash1 hash2
```

### Difftool

Harus sesuai configuration tool yang digunakan. Contoh VS Code.

```shell
git difftool hash1 hash2
```

## Reset Commit

Jika ingin membatalkan perubahan yang telah dicommit ke Repository, bisa melakukan reset commit. Mekanismenya menggeser HEAD pointer ke posisi commit yang kita mau. Mode git reset `<mode>` bisa diisi dengan `--soft` atau `--mixed` (default), atau `--hard`. Selama belum membuat commit baru, masih bisa kembali keatas.

- `--soft`, memindahkan HEAD pointer, namun tidak melakukan perubahan apapun di Staging Index dan Working directory.
- `--mixed`, memindahkan HEAD pointer, mengubah Staging Index menjadi sama seperti Repository, tetapi tidak mengubah apapun di Working directory.
- `--hard`, memindahkan HEAD pointer, dan mengubah Staging Index & Working Directory (sama dengan Repository).

```shell
git reset <mode> hash

git reset --soft 3b1000b
git reset --mixed 3b1000b
git reset --hard 3b1000b
```

## Amend Commit

Amend commit bisa digunakan ketika ingin menambahkan perubahan yang terlupakan ketika sudah dicommit. Amend akan mengubah hash commit.

```shell
git commit --amend -m "isi commit"
```

## Versi Sebelumnya

Git memiliki fitur untuk dapat melihat versi file pada commit sebelumnya, Saat mengambil versi file sebelumnya, file tersebut akan berada di **Staginng Index**.

```shell
git checkout hash -- namafile
git checkout 3b1000b -- file1.txt
```

## Snapshot Sebelumnya

Git memiliki fitur seperti mesin waktu, kita bisa kembali ke snapshot sebelumnya.

```shell
git checkout hash

# kembali ke awal
git checkout namabranch
```

## Git Branch

Untuk melihat nama branch saat ini, gunakan perintah:

```shell
git branch --show-current
```

## Revert Commit

Git memiliki fitur revert commit, untuk membatalkan commit yang telah dilakukan dengan cara membuat commit baru yang membatalkan commit sebelumnya.

```shell
git revert hash
```
