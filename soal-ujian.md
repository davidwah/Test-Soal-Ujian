# Soal Ujian SMK Berbasis HOTS
## Mata Pelajaran: Sistem Operasi & Jaringan Komputer

> **Keterangan Tipe Soal:**
> - **[PG]** = Pilihan Ganda (pilih 1 jawaban: a/b/c/d/e)
> - **[MA]** = Multiple Answer (pilih **minimal 2** jawaban yang benar)
> - **[MT]** = Matching (pasangkan kolom A dengan kolom B)
>
> **Tingkat Kognitif:** C4 = Analisis | C5 = Evaluasi | C6 = Kreasi

---

# TOPIK 1: PERINTAH DASAR LINUX

---

### Soal 1 [PG – C4 Analisis]

**Stimulus:**
Seorang administrator mendapati log error berikut saat menjalankan script backup otomatis:

```
bash: /home/admin/backup.sh: Permission denied
```

Setelah menjalankan `ls -l /home/admin/backup.sh`, output yang muncul adalah:

```
-rw-r--r-- 1 admin admin 1024 May 20 08:00 backup.sh
```

**Pertanyaan:**
Analisislah situasi di atas. Perintah manakah yang paling tepat untuk menyelesaikan masalah tersebut sekaligus menerapkan prinsip **least privilege** (hak akses seminimal mungkin)?

- a. `chmod 777 backup.sh`
- b. `chmod 755 backup.sh`
- c. `chmod 700 backup.sh`
- d. `chmod 644 backup.sh`
- e. `chmod 711 backup.sh`

**Jawaban: c**
*(chmod 700 memberikan hak execute hanya kepada pemilik file, menerapkan prinsip least privilege)*

---

### Soal 2 [PG – C4 Analisis]

**Stimulus:**
Seorang administrator perlu mencari seluruh file konfigurasi di direktori `/etc/apache2` secara rekursif yang mengandung kata `ServerName`, dan ingin mengetahui pada baris ke berapa kata tersebut ditemukan agar dapat langsung mengedit konfigurasi yang tepat.

**Pertanyaan:**
Perintah manakah yang paling efisien untuk mencapai tujuan tersebut?

- a. `find /etc/apache2 -name "ServerName"`
- b. `grep "ServerName" /etc/apache2`
- c. `grep -rn "ServerName" /etc/apache2`
- d. `locate "ServerName" /etc/apache2`
- e. `cat /etc/apache2/* | grep "ServerName"`

**Jawaban: c**
*(Flag `-r` untuk rekursif, `-n` untuk menampilkan nomor baris)*

---

### Soal 3 [PG – C5 Evaluasi]

**Stimulus:**
Partisi `/` pada sebuah server Linux tiba-tiba penuh (100%) sehingga layanan-layanan kritis berhenti berjalan. Administrator perlu mengidentifikasi direktori mana yang menghabiskan paling banyak ruang disk di bawah `/` agar dapat segera mengambil tindakan.

**Pertanyaan:**
Evaluasilah pilihan berikut. Kombinasi perintah manakah yang paling tepat untuk menampilkan penggunaan disk tiap subdirektori di `/`, diurutkan dari yang terbesar ke terkecil?

- a. `df -h | sort -rh`
- b. `du -sh /* | sort -rh`
- c. `ls -lh / | sort -rh`
- d. `du -h / | tail -20`
- e. `fdisk -l | sort -rh`

**Jawaban: b**
*(`du -sh /*` menghitung ukuran tiap subdirektori, `sort -rh` mengurutkan dari terbesar secara human-readable)*

---

### Soal 4 [PG – C4 Analisis]

**Stimulus:**
Proses dengan PID **4521** tidak dapat dihentikan menggunakan perintah `kill 4521`. Setelah dicek dengan `ps aux | grep 4521`, proses tersebut masih terdaftar. Administrator menduga proses tidak merespons sinyal terminasi normal (SIGTERM).

**Pertanyaan:**
Berdasarkan skenario tersebut, perintah manakah yang harus dijalankan selanjutnya untuk memaksa penghentian proses tersebut?

- a. `kill -1 4521`
- b. `kill -15 4521`
- c. `kill -9 4521`
- d. `killall 4521`
- e. `stop 4521`

**Jawaban: c**
*(`kill -9` mengirim sinyal SIGKILL yang tidak dapat diabaikan oleh proses)*

---

### Soal 5 [PG – C4 Analisis]

**Stimulus:**
File `/var/log/syslog` memiliki ukuran 2 GB sehingga tidak dapat dibuka dengan editor teks biasa. Administrator perlu memantau entri log yang masuk **secara real-time** sekaligus melihat **50 baris terakhir** sebagai konteks awal.

**Pertanyaan:**
Perintah manakah yang paling tepat untuk tujuan tersebut?

- a. `cat /var/log/syslog | tail`
- b. `tail -50 /var/log/syslog`
- c. `tail -n 50 -f /var/log/syslog`
- d. `less /var/log/syslog`
- e. `head -50 /var/log/syslog`

**Jawaban: c**
*(`-n 50` menampilkan 50 baris terakhir, `-f` mengikuti file secara real-time)*

---

### Soal 6 [PG – C5 Evaluasi]

**Stimulus:**
Kebijakan retensi log perusahaan menyatakan bahwa semua file log (berekstensi `.log`) di `/var/log` yang berumur lebih dari 7 hari harus dipindahkan ke direktori `/backup/logs` secara otomatis.

**Pertanyaan:**
Evaluasilah pilihan berikut. Perintah manakah yang paling tepat untuk memindahkan file sesuai kebijakan tersebut?

- a. `cp /var/log/*.log /backup/logs`
- b. `find /var/log -name "*.log" -mtime +7 -exec mv {} /backup/logs \;`
- c. `mv /var/log/*.log /backup/logs`
- d. `find /var/log -name "*.log" -newer 7 -exec cp {} /backup/logs \;`
- e. `ls -t /var/log/*.log | head -7 | xargs mv /backup/logs`

**Jawaban: b**
*(`find` dengan `-mtime +7` menemukan file lebih dari 7 hari, `-exec mv` memindahkannya)*

---

### Soal 7 [MA – C4 Analisis]

**Stimulus:**
Sebuah server Linux tiba-tiba tidak bisa terhubung ke internet maupun ke jaringan lokal. Administrator perlu mendiagnosis apakah masalah ada pada konfigurasi IP, routing, atau konektivitas fisik/layanan jaringan.

**Pertanyaan:**
Perintah-perintah manakah yang **relevan** untuk mendiagnosis masalah jaringan tersebut? **(Pilih minimal 2 jawaban yang benar)**

- a. `ip addr show` atau `ifconfig` — memeriksa konfigurasi IP interface
- b. `ping 8.8.8.8` — menguji konektivitas ke luar jaringan
- c. `df -h` — memeriksa penggunaan disk
- d. `ss -tuln` atau `netstat -tuln` — memeriksa port yang sedang listening
- e. `fdisk -l` — memeriksa partisi disk

**Jawaban: a, b, d**

---

### Soal 8 [MA – C5 Evaluasi]

**Stimulus:**
Administrator ingin memastikan layanan `apache2` langsung aktif saat ini **dan** secara otomatis berjalan setiap kali server di-reboot, tanpa perlu intervensi manual.

**Pertanyaan:**
Perintah-perintah manakah yang **keduanya harus** dijalankan untuk memenuhi kedua syarat tersebut? **(Pilih minimal 2 jawaban yang benar)**

- a. `sudo systemctl start apache2`
- b. `sudo systemctl enable apache2`
- c. `sudo service apache2 reload`
- d. `sudo systemctl disable apache2`
- e. `sudo systemctl status apache2`

**Jawaban: a, b**
*(`start` untuk menjalankan sekarang, `enable` agar otomatis berjalan saat boot)*

---

### Soal 9 [MA – C6 Kreasi]

**Stimulus:**
Seorang administrator diminta membuat akun user baru bernama `webdev` dengan spesifikasi:
- Home directory otomatis dibuat di `/home/webdev`
- Default shell adalah `/bin/bash`
- Ditambahkan ke group `www-data` dan `sudo`

**Pertanyaan:**
Perintah-perintah manakah yang diperlukan untuk memenuhi **semua** persyaratan tersebut? **(Pilih minimal 2 jawaban yang benar)**

- a. `sudo useradd -m -s /bin/bash webdev`
- b. `sudo usermod -aG www-data,sudo webdev`
- c. `sudo groupadd webdev`
- d. `sudo deluser webdev sudo`
- e. `sudo chown webdev /home/webdev`

**Jawaban: a, b**
*(`useradd -m -s` membuat user dengan home dir dan shell; `usermod -aG` menambahkan ke group)*

---

### Soal 10 [MT – C4 Analisis]

**Stimulus:**
Dalam pengelolaan file dan keamanan sistem Linux, administrator perlu memahami fungsi tepat dari setiap perintah agar tidak membuat kesalahan konfigurasi yang berbahaya.

**Pertanyaan:**
Pasangkan perintah Linux pada **Kolom A** dengan fungsinya yang tepat pada **Kolom B**!

| Kolom A | Kolom B |
|---|---|
| 1. `chmod 640 file.conf` | A. Menemukan semua file dengan SUID bit aktif untuk keperluan audit keamanan sistem |
| 2. `chown www-data:www-data /var/www/html` | B. Mengatur hak akses agar pemilik dapat membaca/menulis, group hanya membaca, dan lainnya tidak punya akses |
| 3. `find / -perm -4000 -type f` | C. Mengubah kepemilikan direktori web agar dapat dikelola oleh proses web server |

**Jawaban: 1-B, 2-C, 3-A**

---

# TOPIK 2: VIRTUALISASI DENGAN VIRTUALBOX

---

### Soal 11 [PG – C4 Analisis]

**Stimulus:**
Seorang siswa menginstal VirtualBox di komputer lab dan mencoba membuat VM baru dengan sistem operasi Ubuntu Server 64-bit. Namun pada langkah pemilihan OS, VirtualBox hanya menampilkan pilihan versi **32-bit** dan tidak ada pilihan 64-bit sama sekali.

**Pertanyaan:**
Analisislah situasi tersebut. Apa penyebab paling mungkin dari masalah ini?

- a. VirtualBox yang diinstal adalah versi lama yang tidak mendukung 64-bit
- b. RAM komputer host kurang dari 4 GB
- c. Fitur virtualisasi hardware (VT-x/AMD-V) belum diaktifkan di pengaturan BIOS/UEFI
- d. Hard disk tidak memiliki ruang kosong yang cukup
- e. Sistem operasi host yang digunakan adalah versi 32-bit

**Jawaban: c**
*(VirtualBox membutuhkan dukungan virtualisasi hardware dari CPU untuk menjalankan guest 64-bit)*

---

### Soal 12 [PG – C4 Analisis]

**Stimulus:**
Sebuah VM VirtualBox dikonfigurasi dengan 2 network adapter: **Adapter 1 = NAT** dan **Adapter 2 = Host-Only**. VM dapat mengakses internet dengan lancar, namun komputer lain di jaringan kantor (subnet 192.168.1.0/24) tidak bisa mengakses layanan web yang berjalan di VM tersebut.

**Pertanyaan:**
Mengapa konfigurasi ini menyebabkan VM tidak dapat diakses dari komputer lain di jaringan?

- a. Adapter NAT tidak dikonfigurasi dengan benar
- b. Mode NAT bekerja seperti router yang melakukan masquerading — VM bisa keluar ke internet melalui host, tetapi tidak bisa diakses secara langsung dari jaringan luar
- c. Adapter Host-Only tidak terhubung dengan benar ke jaringan fisik
- d. VM perlu direstart setelah setiap perubahan konfigurasi jaringan
- e. Firewall host memblokir semua koneksi masuk ke VM

**Jawaban: b**

---

### Soal 13 [PG – C5 Evaluasi]

**Stimulus:**
Seorang administrator mengambil snapshot VM sebelum memulai konfigurasi server. Setelah 2 jam bekerja menginstal paket dan mengubah konfigurasi, ia menyadari terjadi kesalahan konfigurasi jaringan yang kompleks dan sulit diidentifikasi penyebabnya.

**Pertanyaan:**
Evaluasilah tindakan yang tersedia. Tindakan manakah yang paling efisien untuk mengembalikan VM ke kondisi stabil?

- a. Menghapus VM dan menginstal ulang OS dari awal
- b. Melakukan **Restore/Revert** ke snapshot yang diambil sebelum konfigurasi dimulai
- c. Membuat VM baru dengan konfigurasi identik
- d. Menjalankan perintah `apt autoremove` di dalam VM untuk membersihkan paket
- e. Mengimpor ulang file `.ova` dari backup lama

**Jawaban: b**
*(Snapshot dirancang tepat untuk skenario ini — restore instan ke kondisi stabil sebelumnya)*

---

### Soal 14 [PG – C5 Evaluasi]

**Stimulus:**
Sebuah lab memiliki komputer host dengan spesifikasi: RAM 8 GB, CPU 4 core. Administrator berencana menjalankan **3 VM secara bersamaan**, masing-masing dialokasikan 2 GB RAM dan 1 core CPU. OS host yang digunakan adalah Windows 10.

**Pertanyaan:**
Evaluasilah kelayakan rencana tersebut. Pernyataan manakah yang paling tepat?

- a. Rencana layak karena 3 × 2 GB = 6 GB < 8 GB RAM tersedia
- b. Rencana berisiko karena OS host Windows 10 sendiri membutuhkan sekitar 2–3 GB RAM, sehingga total kebutuhan mendekati atau melebihi kapasitas fisik dan dapat menyebabkan thrashing
- c. Rencana layak karena jumlah core yang dialokasikan (3) tidak melebihi total core (4)
- d. Rencana tidak layak karena VirtualBox hanya mendukung maksimal 2 VM secara bersamaan
- e. Rencana layak asalkan semua VM menggunakan OS yang sama untuk efisiensi memori

**Jawaban: b**

---

### Soal 15 [PG – C4 Analisis]

**Stimulus:**
Administrator sebuah SMK perlu memindahkan VM VirtualBox yang berisi server lab dari komputer lama ke komputer baru. VM tersebut memiliki konfigurasi jaringan, snapshot, dan data siswa yang tidak boleh hilang.

**Pertanyaan:**
Metode manakah yang paling tepat untuk memindahkan VM beserta **seluruh konfigurasi dan data**-nya?

- a. Menyalin hanya file `.vdi` (virtual disk) ke komputer tujuan
- b. Menggunakan fitur **Export Appliance** untuk mengekspor ke format `.ova`, kemudian melakukan Import di komputer tujuan
- c. Melakukan copy-paste folder VM melalui File Explorer tanpa langkah tambahan
- d. Menggunakan VirtualBox Remote Desktop untuk menduplikasi VM secara online
- e. Menyalin file snapshot saja ke komputer tujuan

**Jawaban: b**
*(Format `.ova` mengemas seluruh konfigurasi VM, termasuk hardware setting, secara portabel)*

---

### Soal 16 [PG – C4 Analisis]

**Stimulus:**
Setelah menginstal Guest Additions di VM Linux, siswa menemukan bahwa resolusi layar VM tetap tidak bisa disesuaikan dan masih terkunci di 1024×768. Pesan error tidak muncul selama proses instalasi Guest Additions.

**Pertanyaan:**
Langkah diagnosa yang paling tepat adalah?

- a. Menguninstal dan menginstal ulang VirtualBox di komputer host
- b. Menambah alokasi RAM VM dari 1 GB menjadi 2 GB
- c. Memeriksa apakah modul kernel Guest Additions berhasil dimuat dengan perintah `lsmod | grep vbox` dan memverifikasi versi Guest Additions sesuai dengan versi VirtualBox host
- d. Menghapus VM dan membuat VM baru dengan OS yang sama
- e. Mengubah jenis adapter grafis VM dari VBoxVGA ke VMSVGA di pengaturan Display

**Jawaban: c**
*(Diagnosa harus dimulai dengan memverifikasi apakah instalasi berhasil sebelum mengambil tindakan lain)*

---

### Soal 17 [MA – C4 Analisis]

**Stimulus:**
Seorang siswa diminta mengkonfigurasi satu VM agar memiliki kemampuan berikut secara bersamaan:
1. Mengakses internet untuk mengunduh paket
2. Dapat berkomunikasi langsung dengan komputer host
3. Dapat berkomunikasi dengan VM lain dalam jaringan lab yang terisolasi

**Pertanyaan:**
Tipe network adapter manakah yang perlu dikonfigurasi pada VM untuk memenuhi ketiga kebutuhan tersebut? **(Pilih minimal 2 jawaban yang benar)**

- a. **NAT** — agar VM dapat mengakses internet melalui host
- b. **Host-Only Adapter** — agar VM dapat berkomunikasi langsung dengan host
- c. **Internal Network** — agar VM dapat berkomunikasi dengan VM lain secara terisolasi
- d. **Not Attached** — untuk adapter yang tidak digunakan
- e. **Generic Driver** — untuk driver jaringan khusus

**Jawaban: a, b, c**

---

### Soal 18 [MA – C5 Evaluasi]

**Stimulus:**
Administrator lab sedang mengevaluasi penggunaan fitur Snapshot VirtualBox sebagai mekanisme manajemen kondisi VM untuk keperluan training yang sering membutuhkan reset ke kondisi awal.

**Pertanyaan:**
Pernyataan manakah yang **BENAR** mengenai Snapshot di VirtualBox? **(Pilih minimal 2 jawaban yang benar)**

- a. Snapshot yang diambil saat VM berjalan juga menyimpan state RAM (memory state) sehingga VM dapat dilanjutkan tepat dari titik tersebut
- b. Terlalu banyak snapshot berantai tidak mempengaruhi performa VM dan penggunaan disk sama sekali
- c. Terlalu banyak snapshot berantai dapat memperlambat operasi I/O disk VM dan menghabiskan ruang penyimpanan secara signifikan
- d. Snapshot dapat digunakan sebagai mekanisme pemulihan (recovery point) yang dapat di-restore kapan saja
- e. Snapshot di VirtualBox hanya dapat diambil saat VM dalam kondisi mati (powered off)

**Jawaban: a, c, d**

---

### Soal 19 [MA – C6 Kreasi]

**Stimulus:**
Administrator SMK diminta merancang infrastruktur lab virtualisasi di mana setiap siswa (30 siswa) memiliki VM sendiri dengan konfigurasi identik: OS Ubuntu 22.04, LAMP stack terpasang, dan beberapa file latihan.

**Pertanyaan:**
Strategi manakah yang sebaiknya diterapkan administrator untuk efisiensi waktu dan ruang penyimpanan? **(Pilih minimal 2 jawaban yang benar)**

- a. Membuat **satu VM template** yang sudah terkonfigurasi lengkap, kemudian menggunakan fitur Clone untuk mendistribusikan ke semua siswa
- b. Menginstal OS dan paket fresh satu per satu pada setiap VM dari awal
- c. Menggunakan **Linked Clone** agar setiap VM siswa hanya menyimpan perubahan dari template (menghemat ruang disk secara drastis)
- d. Mengalokasikan RAM dan CPU yang sama persis untuk semua VM tanpa mempertimbangkan beban kerja
- e. Menggunakan fitur **Group** di VirtualBox untuk mengelola semua VM siswa secara bersamaan (start/stop/snapshot sekaligus)

**Jawaban: a, c, e**

---

### Soal 20 [MT – C4 Analisis]

**Stimulus:**
Pemilihan mode jaringan yang tepat di VirtualBox sangat menentukan kemampuan komunikasi VM. Kesalahan memilih mode dapat menyebabkan VM tidak bisa diakses atau tidak bisa mengakses internet.

**Pertanyaan:**
Pasangkan mode jaringan VirtualBox pada **Kolom A** dengan karakteristiknya yang tepat pada **Kolom B**!

| Kolom A | Kolom B |
|---|---|
| 1. **NAT** | A. VM mendapatkan IP dari DHCP server jaringan fisik dan terlihat sebagai perangkat mandiri yang dapat diakses dari jaringan luar |
| 2. **Bridged Adapter** | B. VM dapat mengakses internet melalui host dengan NAT masquerading, tetapi tidak bisa diakses langsung dari jaringan luar |
| 3. **Host-Only Adapter** | C. VM hanya dapat berkomunikasi dengan host dan sesama VM dalam jaringan terisolasi, tanpa akses ke internet |

**Jawaban: 1-B, 2-A, 3-C**

---

# TOPIK 3: INSTALASI DAN KONFIGURASI WEB SERVER APACHE2

---

### Soal 21 [PG – C4 Analisis]

**Stimulus:**
Setelah menginstal Apache2 di Ubuntu dan membuat file `index.html` di `/var/www/html/`, siswa mencoba mengakses `http://localhost` dari browser namun mendapat error:

```
403 Forbidden
You don't have permission to access this resource.
```

Konfigurasi virtual host di `/etc/apache2/sites-available/000-default.conf` sudah mengarah ke DocumentRoot yang benar.

**Pertanyaan:**
Analisislah kemungkinan penyebab error 403 Forbidden tersebut. Jawaban manakah yang paling tepat?

- a. Port 80 belum dibuka di firewall UFW
- b. Service Apache2 belum dijalankan
- c. Permission direktori `/var/www/html` atau file `index.html` tidak mengizinkan user `www-data` (Apache) untuk membacanya
- d. Modul PHP belum diinstal sehingga Apache tidak dapat memproses request
- e. Apache2 berjalan dua instance sekaligus sehingga terjadi konflik

**Jawaban: c**
*(Error 403 umumnya disebabkan oleh permission yang tidak mengizinkan Apache membaca file/direktori)*

---

### Soal 22 [PG – C4 Analisis]

**Stimulus:**
Administrator sebuah sekolah ingin menghosting dua website berbeda — `sekolah.local` dan `perpustakaan.local` — pada **satu server fisik** dengan **satu alamat IP** yang sama, menggunakan Apache2.

**Pertanyaan:**
Fitur Apache2 manakah yang harus dikonfigurasi untuk memungkinkan dua website berjalan di satu server dengan IP yang sama?

- a. `mod_rewrite` untuk pengalihan URL
- b. **Virtual Host berbasis nama (Name-based Virtual Hosting)**
- c. `mod_proxy` untuk meneruskan request ke backend
- d. File `.htaccess` di masing-masing direktori
- e. `mod_ssl` untuk enkripsi HTTPS

**Jawaban: b**

---

### Soal 23 [PG – C5 Evaluasi]

**Stimulus:**
Log Apache2 menampilkan pesan warning berikut setiap kali service di-restart:

```
AH00558: apache2: Could not reliably determine the server's fully qualified domain name,
using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
```

Website masih bisa diakses, tetapi warning ini terus muncul.

**Pertanyaan:**
Tindakan manakah yang paling tepat untuk menghilangkan warning ini?

- a. Mengubah file `/etc/hosts` dan menambahkan entri baru
- b. Menambahkan directive `ServerName localhost` pada file `/etc/apache2/apache2.conf`
- c. Menginstal ulang Apache2 untuk memperbaiki konfigurasi default
- d. Mengubah port Apache2 dari 80 ke 8080
- e. Menonaktifkan IPv6 di konfigurasi sistem

**Jawaban: b**

---

### Soal 24 [PG – C4 Analisis]

**Stimulus:**
Seorang developer perlu mengamankan website development lokal dengan HTTPS menggunakan sertifikat **self-signed** karena belum menggunakan domain publik. Server menggunakan Apache2 di Ubuntu.

**Pertanyaan:**
Urutan langkah yang benar untuk mengaktifkan HTTPS dengan self-signed certificate di Apache2 adalah?

- a. Instal Apache2 → Buat sertifikat → Salin ke `/var/www/html` → Restart Apache2
- b. `sudo a2enmod ssl` → Buat self-signed certificate dengan `openssl` → Konfigurasi Virtual Host untuk port 443 dengan path sertifikat → `sudo a2ensite` → `sudo systemctl restart apache2`
- c. Buka port 443 di firewall → Instal `mod_ssl` → Restart Apache2
- d. Buat sertifikat → Aktifkan `mod_ssl` → Ubah port 80 ke 443 di `ports.conf` → Restart Apache2
- e. Instal `openssl` → Buat sertifikat → Salin ke `/etc/ssl/` → Restart Apache2 tanpa konfigurasi tambahan

**Jawaban: b**

---

### Soal 25 [PG – C5 Evaluasi]

**Stimulus:**
Seorang siswa membuat file `.htaccess` di `/var/www/html/` dengan isi sebagai berikut:

```apache
Options -Indexes
Deny from all
```

Setelah file tersebut disimpan, semua halaman website — termasuk halaman utama — menampilkan error 403 Forbidden.

**Pertanyaan:**
Mengapa konfigurasi ini menyebabkan seluruh website tidak bisa diakses?

- a. Sintaks penulisan `.htaccess` tidak valid
- b. Direktif `Deny from all` memblokir **semua** akses ke direktori tersebut tanpa pengecualian, termasuk pengunjung yang sah
- c. `mod_rewrite` tidak aktif sehingga directive tidak diproses
- d. Apache2 tidak membaca file `.htaccess` karena `AllowOverride` diset `None`
- e. Permission file `.htaccess` tidak mengizinkan Apache untuk membacanya

**Jawaban: b**

---

### Soal 26 [PG – C4 Analisis]

**Stimulus:**
Setelah membuat konfigurasi virtual host baru di `/etc/apache2/sites-available/mysite.conf` dan menjalankan:

```bash
sudo a2ensite mysite.conf
```

Administrator menemukan bahwa website `mysite.local` tetap tidak bisa diakses dan konfigurasi lama masih berlaku.

**Pertanyaan:**
Langkah apa yang terlewat sehingga konfigurasi baru belum berlaku?

- a. Perlu mengedit file `/etc/hosts` untuk menambahkan entri `mysite.local`
- b. Perlu menjalankan `sudo systemctl reload apache2` atau `sudo systemctl restart apache2` agar Apache membaca ulang konfigurasi yang baru diaktifkan
- c. Perlu menginstal modul Apache tambahan
- d. Perlu membuat direktori DocumentRoot yang ditetapkan dalam konfigurasi
- e. Perlu membuka port 80 di firewall UFW

**Jawaban: b**
*(a2ensite hanya membuat symlink; Apache harus di-reload agar membaca konfigurasi baru)*

---

### Soal 27 [MA – C4 Analisis]

**Stimulus:**
Website yang berjalan di server Apache2 tiba-tiba menjadi sangat lambat. Administrator menduga ada permintaan yang tidak wajar, script yang error, atau konfigurasi yang salah.

**Pertanyaan:**
Perintah dan file manakah yang **relevan** untuk mendiagnosis penyebab masalah performa Apache2 tersebut? **(Pilih minimal 2 jawaban yang benar)**

- a. `sudo tail -f /var/log/apache2/access.log` — memantau pola request masuk secara real-time untuk mendeteksi anomali atau serangan
- b. `sudo tail -f /var/log/apache2/error.log` — melihat error yang sedang terjadi dan mungkin mempengaruhi performa
- c. `apache2ctl status` atau `apache2ctl fullstatus` — melihat statistik koneksi dan worker Apache2
- d. `ls -la /var/www/html` — memeriksa daftar file website
- e. `ping localhost` — mengecek koneksi jaringan lokal

**Jawaban: a, b, c**

---

### Soal 28 [MA – C5 Evaluasi]

**Stimulus:**
Dalam audit keamanan, ditemukan bahwa server Apache2 mengekspos informasi versi (`Apache/2.4.41`) di setiap halaman error, directory listing aktif di beberapa direktori, dan metode HTTP TRACE diaktifkan — semua ini merupakan potensi vektor serangan.

**Pertanyaan:**
Konfigurasi manakah yang sebaiknya diterapkan untuk meningkatkan keamanan Apache2? **(Pilih minimal 2 jawaban yang benar)**

- a. `ServerTokens Prod` — menyembunyikan detail versi Apache dari header HTTP response
- b. `Options -Indexes` — menonaktifkan directory listing agar struktur direktori tidak terekspos
- c. `ServerSignature On` — mengaktifkan tanda tangan server di halaman error
- d. `TraceEnable Off` — menonaktifkan metode HTTP TRACE yang rentan terhadap Cross-Site Tracing (XST)
- e. `AllowOverride All` — mengizinkan semua override di `.htaccess`

**Jawaban: a, b, d**

---

### Soal 29 [MA – C6 Kreasi]

**Stimulus:**
Siswa diminta merancang konfigurasi Apache2 untuk website resmi sekolah dengan kebutuhan berikut:
- Halaman `/admin` hanya dapat diakses dengan username dan password
- Website menjalankan skrip PHP untuk dinamisme konten
- Log akses disimpan dalam format kustom yang berbeda dari default

**Pertanyaan:**
Modul-modul Apache2 manakah yang perlu diaktifkan untuk memenuhi semua kebutuhan tersebut? **(Pilih minimal 2 jawaban yang benar)**

- a. `mod_auth_basic` dan `mod_authn_file` — untuk autentikasi berbasis file `.htpasswd` pada direktori `/admin`
- b. `libapache2-mod-php` / modul PHP — untuk menjalankan skrip PHP
- c. `mod_deflate` — untuk kompresi response HTTP
- d. `mod_evasive` — untuk proteksi DDoS
- e. `mod_log_config` — untuk mengkonfigurasi format log akses secara kustom

**Jawaban: a, b, e**

---

### Soal 30 [MT – C4 Analisis]

**Stimulus:**
Memahami kode status HTTP sangat penting bagi administrator web server untuk mendiagnosis masalah dengan cepat tanpa harus memeriksa semua log secara manual.

**Pertanyaan:**
Pasangkan kode status HTTP pada **Kolom A** dengan skenario penyebab paling umum di Apache2 pada **Kolom B**!

| Kolom A | Kolom B |
|---|---|
| 1. **Error 404 Not Found** | A. Script PHP pada halaman mengandung syntax error, atau proses Apache2 tidak memiliki izin membaca file konfigurasi yang dibutuhkan |
| 2. **Error 500 Internal Server Error** | B. URL yang diminta tidak sesuai dengan file atau resource yang ada di DocumentRoot server |
| 3. **Error 403 Forbidden** | C. Permission file atau direktori tidak mengizinkan Apache mengaksesnya, atau akses dibatasi secara eksplisit oleh konfigurasi `Deny from` |

**Jawaban: 1-B, 2-A, 3-C**

---

# TOPIK 4: INSTALASI DAN PENGGUNAAN MYSQL DATABASE

---

### Soal 31 [PG – C4 Analisis]

**Stimulus:**
Setelah menginstal MySQL di Ubuntu, administrator mencoba login sebagai root dengan perintah:

```bash
mysql -u root -p
```

Namun mendapat error:

```
ERROR 1698 (28000): Access denied for user 'root'@'localhost'
```

Administrator yakin password yang dimasukkan sudah benar.

**Pertanyaan:**
Analisislah penyebab error tersebut. Jawaban manakah yang paling tepat?

- a. MySQL belum terinstal dengan benar, perlu diinstal ulang
- b. Password root MySQL sudah kadaluarsa dan perlu direset
- c. Pada Ubuntu, user root MySQL secara default menggunakan plugin `auth_socket` yang memerlukan akses melalui socket sistem operasi, bukan password — sehingga login harus menggunakan `sudo mysql -u root`
- d. Service MySQL belum dijalankan, perlu `sudo systemctl start mysql`
- e. Port 3306 belum terbuka di firewall

**Jawaban: c**

---

### Soal 32 [PG – C4 Analisis]

**Stimulus:**
Seorang developer menjalankan query berikut pada database MySQL:

```sql
SELECT * FROM siswa WHERE nama = 'Ahmad';
```

Query mengembalikan 0 baris, padahal data dengan nama `'ahmad'` (huruf kecil) jelas ada di tabel. Tabel `siswa` menggunakan collation `utf8mb4_bin`.

**Pertanyaan:**
Mengapa query tersebut gagal menemukan record yang dimaksud?

- a. Sintaks SQL yang ditulis salah
- b. Kolom `nama` tidak memiliki index sehingga pencarian gagal
- c. Collation `utf8mb4_bin` melakukan perbandingan secara **case-sensitive** (membedakan huruf besar dan kecil), sehingga `'Ahmad'` dan `'ahmad'` dianggap berbeda
- d. MySQL tidak mendukung pencarian berdasarkan kolom bertipe string
- e. Tabel `siswa` tidak ada, perlu dibuat terlebih dahulu

**Jawaban: c**

---

### Soal 33 [PG – C5 Evaluasi]

**Stimulus:**
Dalam audit keamanan database, ditemukan bahwa user `'appuser'@'%'` memiliki privilege `GRANT ALL PRIVILEGES ON *.* TO 'appuser'@'%'`, artinya user tersebut bisa melakukan apa saja pada semua database dari IP manapun. Ini dianggap sebagai risiko keamanan kritis.

**Pertanyaan:**
Tindakan manakah yang paling tepat untuk memperbaiki konfigurasi ini sesuai prinsip **least privilege**?

- a. Menghapus user `appuser` dan membuat ulang dari awal
- b. Mencabut semua privilege lalu hanya memberikan privilege yang diperlukan: `REVOKE ALL ON *.* FROM 'appuser'@'%';` diikuti `GRANT SELECT, INSERT, UPDATE, DELETE ON app_db.* TO 'appuser'@'%';`
- c. Mengubah password user `appuser` menjadi lebih kuat
- d. Memblokir akses dari host `%` menggunakan firewall
- e. Mengganti host `%` menjadi `localhost` saja

**Jawaban: b**

---

### Soal 34 [PG – C4 Analisis]

**Stimulus:**
Administrator perlu membuat backup harian database production bernama `school_db` secara otomatis menggunakan cron job. Backup harus berupa file SQL yang bisa di-restore kapan saja.

**Pertanyaan:**
Perintah manakah yang paling tepat untuk membuat backup database MySQL ke file SQL?

- a. `mysql -u root -p school_db > backup.sql`
- b. `mysqldump -u root -p school_db > backup_school_db.sql`
- c. `mysqlbackup school_db backup.sql`
- d. `cp /var/lib/mysql/school_db /backup/`
- e. `mysql -u root -p --export school_db > backup.sql`

**Jawaban: b**
*(`mysqldump` adalah alat resmi untuk mengekspor struktur dan data database ke format SQL)*

---

### Soal 35 [PG – C5 Evaluasi]

**Stimulus:**
Tabel `transaksi` memiliki 15 juta record. Query berikut yang sering dijalankan aplikasi berjalan sangat lambat (>30 detik):

```sql
SELECT * FROM transaksi WHERE id_pelanggan = 99;
```

Hasil `EXPLAIN` menunjukkan tipe akses `ALL` (full table scan).

**Pertanyaan:**
Tindakan optimasi yang paling tepat berdasarkan hasil analisis EXPLAIN tersebut adalah?

- a. Menambah kapasitas RAM server database
- b. Membuat **INDEX** pada kolom `id_pelanggan`: `CREATE INDEX idx_pelanggan ON transaksi(id_pelanggan);`
- c. Memecah tabel `transaksi` menjadi beberapa tabel yang lebih kecil berdasarkan tahun
- d. Menambahkan `LIMIT 100` pada query untuk membatasi jumlah hasil
- e. Mengubah tipe data kolom `id_pelanggan` dari INT menjadi VARCHAR

**Jawaban: b**
*(Full table scan menandakan tidak ada index pada kolom filter; penambahan index menyelesaikan akar masalah)*

---

### Soal 36 [PG – C4 Analisis]

**Stimulus:**
Administrator perlu memberikan akses database `school_db` kepada user baru bernama `guru_user` dengan ketentuan:
- User hanya boleh melakukan operasi **SELECT** (hanya baca)
- Akses hanya diizinkan dari komputer dengan IP **192.168.1.100**
- User belum ada di MySQL

**Pertanyaan:**
Rangkaian perintah SQL manakah yang benar untuk memenuhi semua ketentuan tersebut?

- a. `GRANT ALL ON school_db.* TO 'guru_user'@'192.168.1.100';`
- b. `CREATE USER 'guru_user'@'192.168.1.100' IDENTIFIED BY 'P@ssw0rd';` diikuti `GRANT SELECT ON school_db.* TO 'guru_user'@'192.168.1.100';`
- c. `GRANT SELECT ON school_db.* TO 'guru_user'@'%';`
- d. `INSERT INTO mysql.user VALUES ('guru_user', '192.168.1.100', 'SELECT');`
- e. `SET PERMISSION 'guru_user' SELECT ON school_db FROM '192.168.1.100';`

**Jawaban: b**

---

### Soal 37 [MA – C4 Analisis]

**Stimulus:**
DBA melaporkan bahwa server MySQL berjalan sangat lambat dan beberapa query aplikasi time out. DBA perlu mengidentifikasi query mana yang bermasalah dan memahami bagaimana MySQL mengeksekusinya.

**Pertanyaan:**
Perintah dan teknik manakah yang **relevan** untuk mendiagnosis masalah performa MySQL tersebut? **(Pilih minimal 2 jawaban yang benar)**

- a. `SHOW PROCESSLIST;` — melihat semua query yang sedang berjalan saat ini beserta durasinya
- b. `EXPLAIN SELECT ... FROM ... WHERE ...;` — menganalisis rencana eksekusi query untuk mendeteksi full table scan
- c. `SHOW TABLES;` — menampilkan daftar tabel dalam database
- d. `SHOW STATUS LIKE 'Slow_queries';` — melihat jumlah query yang terdeteksi lambat sejak server berjalan
- e. `DESCRIBE nama_tabel;` — melihat struktur kolom tabel

**Jawaban: a, b, d**

---

### Soal 38 [MA – C5 Evaluasi]

**Stimulus:**
Setelah instalasi MySQL baru, tim keamanan melakukan evaluasi dan menemukan beberapa konfigurasi default yang berisiko: terdapat anonymous user, database `test` dengan akses terbuka, dan root bisa login dari remote.

**Pertanyaan:**
Langkah-langkah manakah yang sebaiknya dilakukan segera setelah instalasi MySQL untuk meningkatkan keamanan? **(Pilih minimal 2 jawaban yang benar)**

- a. Menjalankan `mysql_secure_installation` untuk mengotomatiskan pengamanan konfigurasi default secara interaktif
- b. Menghapus database `test` dan menghapus anonymous user yang dibuat secara otomatis saat instalasi
- c. Membiarkan anonymous user aktif agar memudahkan akses dari aplikasi
- d. Menonaktifkan kemampuan login root dari remote host (`'root'@'%'`)
- e. Mengekspor semua database ke file SQL sebagai backup sebelum melakukan konfigurasi apapun

**Jawaban: a, b, d**

---

### Soal 39 [MA – C6 Kreasi]

**Stimulus:**
Siswa diminta merancang struktur database untuk aplikasi **perpustakaan digital sekolah** yang harus mencatat: data buku (judul, ISBN, pengarang), data anggota (siswa/guru), riwayat peminjaman, dan denda keterlambatan.

**Pertanyaan:**
Prinsip-prinsip desain database manakah yang harus diterapkan dalam perancangan tersebut? **(Pilih minimal 2 jawaban yang benar)**

- a. Membuat tabel terpisah untuk `buku`, `anggota`, `peminjaman`, dan `denda`, dihubungkan dengan **Foreign Key** untuk menjaga integritas referensial
- b. Menyimpan semua data dalam satu tabel besar agar query lebih sederhana
- c. Menggunakan **Primary Key** dengan `AUTO_INCREMENT` pada setiap tabel sebagai identifier unik
- d. Menerapkan **normalisasi database minimal hingga 3NF** untuk menghilangkan redundansi data dan anomali update
- e. Menyimpan data tanggal peminjaman dan pengembalian dalam tipe data `VARCHAR(20)` agar fleksibel

**Jawaban: a, c, d**

---

### Soal 40 [MT – C4 Analisis]

**Stimulus:**
Pengelolaan hak akses user dan pemahaman struktur tabel merupakan tugas rutin seorang DBA MySQL. Menguasai perintah-perintah berikut sangat penting untuk administrasi database yang efektif dan aman.

**Pertanyaan:**
Pasangkan perintah MySQL pada **Kolom A** dengan fungsinya yang tepat pada **Kolom B**!

| Kolom A | Kolom B |
|---|---|
| 1. `SHOW GRANTS FOR 'appuser'@'localhost';` | A. Menampilkan struktur tabel: nama kolom, tipe data, NULL/NOT NULL, default value, dan key |
| 2. `FLUSH PRIVILEGES;` | B. Memuat ulang tabel grant di memori agar perubahan hak akses yang dilakukan secara manual pada tabel sistem langsung berlaku |
| 3. `DESCRIBE nama_tabel;` | C. Menampilkan semua privilege yang dimiliki oleh user tertentu dalam format pernyataan GRANT |

**Jawaban: 1-C, 2-B, 3-A**

---

*— Selesai | Total: 40 Soal (10 soal × 4 Topik) —*
