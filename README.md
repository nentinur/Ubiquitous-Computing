# PROJECT UBICOM

## APLIKASI PREDIKSI WAKTU KEDATANGAN BUS DAN PELACAKAN POSISI BUS

### Latar belakang

Transportasi umum memainkan peran penting dalam mobilitas perkotaan dan konektivitas masyarakat. Bus menjadi salah satu sarana transportasi umum yang cukup banyak digunakan oleh masyarakat. Salah satu manfaat penggunaan bus ini adalah untuk mengurangi masalah kemacetan, namun masih banyak masyarakat yang lebih memilih menggunakan kendaraan pribadi dibanding kendaraan umum, dan salah satu alasannya yaitu masalah kenyamanan.

Salah satu penyebab ketidaknyamanan dalam menggunakan bus adalah terkait ketidakpastian jadwal keberangkatan bus. Terkadang bus tidak berangkat tepat waktu sesuai jadwal keberangkatan yang ada, hal ini mengakibatkan penumpang tertinggal bus maupun menunggu bus terlalu lama tanpa kepastian. 

Untuk mengatasi masalah tersebut dibutuhkan suatu sistem yang dapat melakukan prediksi waktu kedatangan bus dan pelacakan posisi bus, agar penumpang bisa tahu keberadaan bus yang ditujunya sudah sampai mana, sudah berangkat ataukah belum, dan sampai halte jam berapa. Sehingga penumpang tidak perlu khawatir akan ketinggalan bus, karena aplikasi akan memberi informasi posisi bus dan memberikan estimasi kedatangan bus kepada penumpang.

Aplikasi prediksi waktu kedatangan bus dan pelacakan posisi bus ini mampu melakukan pelacakan posisi bus dengan memanfaatkan perangkat GPS yang integrasikan di dalam bus dan sistem IoT (Internet of Things) untuk melaporkan posisi bus, sehingga pengguna dapat memantau secara langsung dimana posisi bus berada, dan juga memberikan estimasi waktu berapa lama lagi bus akan tiba di lokasi tempat pengguna menunggu bus.

### Branding

Merek: GObus

Inspirasi merek: Kata "Go" adalah kata kerja yang kuat dan positif. Ini memberi kesan bahwa pengguna akan "pergi" atau "bergerak" dengan bantuan aplikasi ini. Gobus merepresentasikan pengguna yang akan pergi dengan menggunakan bus, selain itu Gobus juga bermakna ajakan kepada pengguna untuk menggunakan bus sebagai kendaraan umum, demi mengurangi kemacetan yang kerap kali menjadi masalah terutama di perkotaan.

Tagline: The Smart Public Transportation. Take Public Transportation Without Worry.

Campaign: Memberikan kemudahan dalam menggunakan kendaraan umum, naik bus tanpa khawatir ketinggalan dan lelahnya menunggu dalam ketidakpastian.

Target user: usia 10+, pengguna kendaraan umum

User experience theme: informatif dan mudah digunakan, optimal, memberikan informasi seakurat mungkin

### User Story

| sebagai | Saya ingin bisa                                           | sehingga                                                      | prioritas  |
| ------- | --------------------------------------------------------- | ------------------------------------------------------------- | ---------- |
| sistem  | Mengirim lokasi terkini bus                               | Bisa membaca titik koordinat                                  | ⭐⭐⭐⭐⭐ |
| sistem  | Menampilkan posisi bus di peta                            | Bisa menempatkan koordinat di peta dengan akurat              | ⭐⭐⭐⭐⭐ |
| sistem  | Melakukan tracking secara realtime terhadap posisi bus    | Bisa memperbarui titik koordinat bus secara berkala           | ⭐⭐⭐⭐⭐ |
| sistem  | Melakukan pemesanan tiket online                          | Bisa melakukan transaksi pembelian tiket di aplikasi          | ⭐⭐⭐⭐ |
| sistem  | Menampilkan posisi bus yang dekat dengan pengguna         | Bisa membaca titik koordinat lebih dari 1 bus                 | ⭐⭐⭐      |
| sistem  | Memperkirakan waktu kedatangan bus kepada pengguna        | Bisa menghitung estimasi waktu terhadap jarak yang ditempuh bus untuk sampai ke pengguna | ⭐⭐⭐⭐⭐ |

### Metode dan algoritma

Sensor:

- GPS: Modul GPS UBlox NEO-6M. Penjelasan: Modul GPS ini cukup populer dan mudah digunakan serta menyediakan data posisi yang akurat dan dapat diintegrasikan dengan mikrokontroler seperti Arduino.
- Mobile software development: prototype
- Edge software development: prototype

### Struktur data

![struktur data](img/struktur%20data.drawio.png)

### Arsitektur sistem

![arsitektur sistem](img/arsitektur%20sistem_ubikom.drawio.png)

Sensor yang berupa modul GPS akan dihubungkan dengan mikrokontroller ESP8266, sensor ini akan menangkap infomasi koordinat bus, kemudian mikrokontroller, akan mengirimkan akan mengolah informasi tersebut menjadi format yang diinginkan dan melakukan publish pada broker MQTT, selanjutnya server/backend akan menangkap data yang dikirimkan ke MQTT dan menyimpannya dalam database, kemudian mengolahnya untuk memperkirakan waktu kedatangan bus, informasi yang sudah diolah ini dibungkus dalam bentuk API yang nantinya akan dikonsumsi oleh web yang diakses pengguna. di sisi lain, aplikasi yang digunakan oleh pengguna akan melakukan request terhadap server berupa informasi lokasi bus dan estimasi waktu bus ataupun request transaksi pemesanan tiket bus, setelah itu server akan memberikan respon kepada pengguna berupa informasi yang sudah diolah tadi.

### Deskripsi teknologi

Mesin komputasi:

- Edge Server: Arduino, Karena Arduino adalah mikrokontroller yang sederhana dan mudah dioperasikan serta memiliki dukungan komunitas yang cukup besar
- Cloud Server: GCP: Google Compute Engine untuk mesin komputasinya, karena sangat fleksibel dan mesin komputasinya dapat disesuaikan dengan kebutuhan. Google Cloud Dataflow, untuk mengelola aliran data secara realtime dan mengolah serta menganalisis data yang diterima dari perangkat IoT.
- Smartphone: Android & iPhone, karena Android & iPhone merupakan smartphone yang umum dan banyak digunakan saat ini.
  Software development:
- Front-end Developmnet: React.js, karena React.js merupakan library javascript yang umum digunakan dalam pembangunan aplikasi web maupun mobile.
- Backend Development: Express.js, karena Express.js adalah salah satu library backend yang cukup terkenal dan banyak digunakan oleh backend developer.
- Koneksi: NodeMCU (ESP8266).
  Sensor:
- GPS: Modul GPS UBlox NEO-6M. Penjelasan: Modul GPS ini cukup populer dan mudah digunakan serta menyediakan data posisi yang akurat dan dapat diintegrasikan dengan mikrokontroler.

### User Experience (UX) Design

| No | Tindakan pengguna | Tampilan Aplikasi |
| --- | --- | --- |
| 1 | Pertama kali membuka aplikasi | ![halaman home](img/home.png) |
| 2 | Klik pada tombol "BOOKING TIKET" (sebelum login | ![tombol login](img/tombol-login.png) |
| 3 | Klik pada tombol "LOGIN" | ![halaman login](img/login.png) |
| 4 | Klik pada tombol "DAFTAR" | ![halaman daftar](img/daftar.png) |
| 5 | Berhasil mendaftar | ![daftar berhasil](img/daftar-berhasil.png) |
| 6 | Klik pada tombol "OK " / "LOGIN" | ![halaman login](img/login.png) |
| 7 | Berhasil login | ![halaman login](img/home.png) |
| 8 | Klik pada tombol "BOOKING TIKET" | ![halaman pilih jurusan](img/pilih-jurusan.png) |
| 9 | Klik pada salah satu jurusan bus | ![halaman pilih bus](img/pilih-bus.png) |
| 10 | Klik pada salah satu pilihan bus | ![halaman booking](img/isi-booking.png) |
| 11 | klik pada tombol "BOOKING" | ![berhasil loin](img/booking-berhasil.png) |
| 12 | Klik tombol "YA" | ![halaman riwayat](img/riwayat.png) |
| 13 | Klik Riwayat pesanan teratas | ![halaman tracking](img/tracking.png) |
| 14 | Klik pada tombol "HUBUNGI SOPIR" | Redirect ke Whatsapp |
| 15 | Klik ikon riwayat | ![halaman riwayat](img/riwayat.png) |
| 16 | Klik ikon profil | ![halaman profil](img/profile.png) |
| 17 | Klik tombol "LOGOUT" | ![tombol logout](img/logout.png) |
