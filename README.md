# Tutorial Git | PZN

Kode ini merupakan materi Git yang dibawakan oleh **Eko Kurniawan Khannedy** dari channel YouTube _Programmer Zaman Now_.

Link Playlist Tutorial: [Tutorial Git](https://youtube.com/playlist?list=PL-CtdCApEFH_lYGV8hxqjtKmFA_xeLupq&si=1W1FVpi0y89SHqua)

Bahasan Materi Meliputi:

- Pengenalan Version Control
- Git
- Configuration
- Repository
- Workflow
- Hash
- Menambah File
- Mengubah File
- Menghapus File
- Membatalkan Perubahan
- Commit Log
- Compare Commit
- Rename File
- Reset Commit
- Amend Commit
- Versi Sebelumnya
- Snapshot Sebelumnya
- Revert Commit
- Ignore
- Blame
- Alias
- Branch
- Multiple Branch
- Merge
- Merge Conflict
- Cherry Pick
- Tag
- Git Remote
- Git Server
- Git Server Repository
- SSH
- Remote Repository
- Push
- Clone
- Remote Branch

## Technology stack & Tools

**Program ini membutuhkan:**

| Tech Stack & Tools | Version |
| ------------------ | ------- |
| Git                | 2.30+   |
| Visual Studio Code | -       |

## Catatan Pribadi

Jika ingin klona di komputer lain. Taruh di direktori berikut:

    .
    ├── Course
    │   ├── Programmer Zaman Now
    |   |   ├── GIT
    |   |   └── ...
    |   └── ...
    └── ...

Jika sudah di berada di folder **GIT**, baru clone.

```shell
git clone https://github.com/bagusperdanay7/belajar-git-dasar.git
```

# Notes

Ini merupakan catatan pribadi mengenai materi dari **Git** dengan Pak _Eko Kurniawan Khannedy_.

## Git Configuration

```shell
git config --global user.name "Bagus Perdana Yusuf"
git config --global user.email "baguspyus@gmail.com"
```

## Inisialisasi Project Git

```shell
git init
```

## Melihat Status

```shell
git status
```

## Menambah file

```shell
git add nama_file
```

## Commit ke Repository

```shell
git commit -m "MASUKKAN PESAN COMMIT"
```

## Melihat Perubahan Git

```shell
git diff
```

## Membatalkan Penambahan File

```shell
git clean -f
```

## Membatalkan Perubahan File

```shell
git restore namafile
```

## Membatalkan Penghapusan File

```shell
git restore namafile
```

## Membatalkan dari Staging Index

Karena git restore hanya bisa dilakukan untuk membatalkan perubahan yang terjadi di **Working Directory**. Kita menggunakan `--staged` untuk mengembalikan posisi dari **staging index** ke **working directory**.

```shell
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

### Membuat Branch Baru

```shell
git branch namabranch
```

### Melihat Semua Branch

```shell
git branch --list or git branch
```

### Pindah ke Branch Lain

```shell
git switch namabranch
git checkout namabranch
```

### Mengubah nama Branch

Jika membuat kesalahan nama branch bisa dilakukan perubahan, namun pindah dahulu ke branch yang ingin kita rubah namanya. Setelah pindah baru lakukan commit:

```shell
git branch -m namabranchbaru
```

### Menghapus Branch

Untuk menghapus, keluar dari branch tersebut terlebih dahulu

```shell
git branch -d namabranch
git branch --delete namabranch
```

## Revert Commit

Git memiliki fitur revert commit, untuk membatalkan commit yang telah dilakukan dengan cara membuat commit baru yang membatalkan commit sebelumnya.

```shell
git revert hash
```

## Git Ignore

Jika ingin mengabaikan file atau folder apa saja yang tidak ingin dimasukkan ke repository, buat file `.gitignore` terlebih dahulu dan di dalam file `.gitignore`. Masukkan adapa saja yang ingin diabaikan.

## Blame

Blame adalah fitur di git yang digunakan untuk mencari tahu, siapa yang menambah perubahan serta commitnya.

```shell
git blame namafile
```

## Menambahkan Alias di git

Alias fitur menarik karena kita bisa membuat nama lain dari perintah git.

```shell
git config --global alias.ko commit
git config --global alias.komit commit
git config --global alias.logone "log --oneline"
```

## Merge

Merge adalah proses penggabungan dua buah branch. Untuk melakukan merge, pindah dahulu ke branch dimana lokasi merge akan dilakukan, lalu gunakan perintah:

```shell
git merge namabranch
```

Misalnya ketika saat ini kita berada di merge master, dan ingin merge feature/1, berarti kita merge feature/1 ke dalam master.

### Membatalkan Conflict Merge

```shell
git merge --abort
```

## Cherry Pick

Misal kita ingin mere branch feature/c, namun tidak ingin merge semua perubahan, maka bisa melakukan cherry pick untuk commit perubahannya. Caranya:

```shell
git cherry-pick commitId
```

## SSH

SSH adalah Secure shell yang merupakan protokol jaringan untuk komunikasi jaringan secara aman dan terenkripsi. SSH Key digunakan untuk autentikasi ke server SSH. Untuk membuat SSH Key, kita bisa gunakan perintah:

```shell
ssh-keygen
```

Setelah mengetikkan perintah di atas, secara otomatis akan terdapat 2 key di komputer lokal kita, yaitu `private key` dan `public key` yang terdapat pada **.ssh** home directory. File `id_rsa` adalah private key, dan `id_rsa_pub` adalah public key.

### Menguji SSH ke Server GitHub

```shell
ssh -T git@github.com
```

## Git Remote

Secara default, ketika kita membuat git project, git tidak tahu tentang remote repository. Maka kita perlu memberi tahu ke git project yang sudah kita buat tentang lokasi git repository.

### Menambah Remote

Untuk menambah remote repository, gunakan perintah:

```shell
git remote add nama ssh-url
```

### Melihat Remote

Untuk melihat remote repository yang ada di git project gunakan perintah:

```shell
git remote
```

Melihat URL detail remote repository dengan perintah:

```shell
git remote get-url nama
```

### Menghapus Remote Repository

```shell
git remote rm nama
```

## Push

Push digunakan untuk mensinkronisasikan project local dengan remote repository server, untuk mengirim perubahan di local ke git server, gunakan perintah:

```shell
# Mengirim perubahan branch ke remote dengan nama branch yang sama
git push namaremote localbranch

# Contoh
git push origin main

# Mengirim perubahan branch ke remote repository dengan nama branch yang berbeda
git push namaremote localbranch:remotebranch

# Contoh
git push origin main:develop
```

### Push Semua Branch

```shell
git push origin --all
```

### Push Menghapus Branch

```shell
git push --delete namaremote namabranch

git push --delete origin develop

```

## Clone

Clone di git berarti kita unduh project Git yang terdapat di server ke local dan secara otomatis diunduh sebagai git project

```shell
git clone urlremoterepository

# Klona dengan nama folder yang berbeda dengan nama remote repostiorynya
git clone urlremoterepository namafolder
```

Default clone akan berisi remote repository origin ke git remote repository yang kita clone, dan default clone berisi branch utama repository remotenya.

## Referensi

- YouTube TUTORIAL GIT - Programmer Zaman Now
