# TrafficSignBot

TrafficSignBot adalah robot mobil berbasis Arduino yang menggunakan teknologi Computer Vision untuk mendeteksi rambu lalu lintas dan memberikan respons otomatis. Proyek ini dirancang untuk mensimulasikan kendaraan pintar yang dapat beroperasi secara mandiri di jalan raya.

## Fitur Utama Robot

- **Line Following**  
  Robot dilengkapi dengan kemampuan untuk mendeteksi garis pada jalur, yang berfungsi sebagai track yang harus diikuti. Robot akan bergerak dengan lancar mengikuti jalur yang terdeteksi.

- **Merespons Input**  
  Robot dapat merespons perintah input sesuai dengan situasi yang ada. Misalnya, jika robot diminta untuk belok kanan, robot akan berbelok ke arah yang sesuai berdasarkan jalur yang ada.

- **Deteksi Rambu Lalu Lintas Menggunakan Model YOLOv10**  
  Pemilihan model YOLOv10 didasarkan pada popularitas dan efektivitasnya dalam melakukan deteksi objek, khususnya dalam konteks real-time.

- **Integrasi Antara Model Deteksi dan Arduino**  
  Proyek ini mengintegrasikan model deteksi dengan Arduino, di mana kedua komponen ini berkolaborasi dengan komponen lainnya untuk menghasilkan robot mobil yang mampu melakukan berbagai tugas yang diminta.

- **Respons Otomatis Terhadap Rambu**  
  Robot dapat mendeteksi rambu lalu lintas dan memberikan respons sesuai dengan jenis rambu yang terdeteksi. Misalnya, jika robot mendeteksi rambu lampu merah, robot akan berhenti. Jika robot diminta untuk berhenti tetapi mendeteksi rambu dilarang berhenti, robot akan tetap melanjutkan pergerakan.

## Teknologi yang Digunakan

Berikut adalah beberapa teknologi dan library yang digunakan dalam proyek ini:

- **Computer Vision**: OpenCV, TensorFlow, YOLOv10
- **Hardware**: Arduino, Infrared Sensor, DC Motor, Motor Driver, dan lain-lain.
- **Bahasa Pemrograman**: Python untuk pengolahan data Computer Vision dan C++ untuk pemrograman Arduino.

## Cara Kerja

### Pengoperasian Dasar Robot

- Robot dilengkapi dengan sensor line follower yang memungkinkan deteksi dan pengikutan garis yang ada di jalan. Sensor ini memberikan umpan balik ke Arduino untuk mengatur motor dan memastikan robot tetap berada di jalur.

### Perekaman Gambar

- Selama robot bergerak di sepanjang jalur, kamera yang terhubung ke komputer atau mikroprosesor akan terus-menerus menangkap gambar lingkungan sekitar, termasuk rambu lalu lintas yang mungkin muncul.

### Deteksi Rambu Lalu Lintas

- Gambar yang ditangkap oleh kamera kemudian dikirim ke model YOLOv11 yang telah dilatih untuk mendeteksi berbagai jenis rambu lalu lintas. Model ini akan menganalisis gambar dan mengidentifikasi rambu lalu lintas yang terdeteksi, seperti lampu merah, lampu hijau, dan rambu dilarang berhenti.

## Perilaku Robot Berdasarkan Rambu

| **ID** | **Nama Rambu**                                     | **Aksi**                                                                                   | **Logika**                                                                                   |
|--------|----------------------------------------------------|-------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| 0      | Lampu Hijau                                        | Robot melanjutkan pergerakan mengikuti garis.                                              | Motor robot terus bergerak maju.                                                           |
| 1      | Lampu Kuning                                       | Robot memperlambat pergerakan.                                                            | Mengurangi kecepatan sebagai peringatan.                                                   |
| 2      | Lampu Merah                                        | Robot berhenti sepenuhnya.                                                                | Motor robot dimatikan untuk menghentikan pergerakan.                                        |
| 3      | Larangan Belok Kanan                               | Robot menghindari belokan ke kanan.                                                       | Tetap di jalur lurus atau belok ke arah lain.                                              |
| 4      | Larangan Belok Kiri                                | Robot menghindari belokan ke kiri.                                                        | Tetap di jalur lurus atau belok ke arah lain.                                              |
| 5      | Larangan Berhenti                                  | Robot terus bergerak meskipun ada sinyal berhenti.                                         | Mengabaikan perintah berhenti jika terdeteksi.                                              |
| 6      | Larangan Berjalan Terus Wajib Berhenti Sesaat      | Robot berhenti sejenak sebelum melanjutkan perjalanan.                                    | Berhenti beberapa detik sebelum bergerak maju.                                             |
| 7      | Larangan Masuk                                     | Robot berputar arah.                                                                      | Menghentikan perjalanan dan kembali ke jalur sebelumnya.                                    |
| 8      | Larangan Memutar Balik                             | Robot menghindari perintah untuk memutar arah.                                             | Tetap di jalur yang ada tanpa melakukan putar balik.                                       |
| 9      | Larangan Parkir                                    | Robot terus bergerak tanpa berhenti di area tersebut.                                      | Mengabaikan perintah untuk berhenti.                                                       |
| 10     | Peringatan Alat Pemberi Isyarat Lalu Lintas        | Robot melambat dan bersiap untuk merespons rambu berikutnya.                               | Mengantisipasi lampu lalu lintas di depan.                                                 |
| 11     | Peringatan Banyak Pejalan Kaki                    | Robot melambat dan berhenti jika diperlukan.                                              | Memperhatikan lingkungan sekitar untuk menghindari tabrakan.                               |
| 12     | Perintah Masuk Jalur Kiri                          | Robot berpindah ke jalur kiri.                                                            | Mengatur arah untuk masuk ke jalur kiri.                                                   |
| 13     | Perintah Pilihan Memasuki Salah Satu Jalur         | Robot memilih jalur yang sesuai berdasarkan kondisi jalan.                                | Memilih jalur berdasarkan algoritma jalur terbaik.                                         |
| 14     | Petunjuk Area Parkir                               | Robot mencari area parkir dan berhenti di sana.                                           | Mencari lokasi berhenti yang sesuai.                                                       |
| 15     | Petunjuk Lokasi Pemberhentian Bus                 | Robot berhenti di lokasi yang ditentukan.                                                 | Berhenti di tempat yang sesuai.                                                            |
| 16     | Petunjuk Lokasi Putar Balik                       | Robot berputar balik di area yang ditentukan.                                             | Mengatur arah untuk memutar balik.                                                         |
| 17     | Petunjuk Penyeberangan Jalan Kaki                 | Robot berhenti untuk memberi prioritas kepada pejalan kaki.                               | Berhenti sampai jalan aman untuk dilalui.                                                  |

### Reaksi Dinamis

Robot beroperasi dalam mode loop, di mana setiap deteksi rambu dan respons diulang secara terus menerus. Ini memungkinkan robot untuk beradaptasi dengan kondisi lalu lintas dan merespons secara real-time terhadap berbagai rambu yang ditemui di jalur.

## Dataset dan Pelatihan Model

Proyek ini menggunakan dataset yang disediakan oleh [Adhy Wiranto](https://github.com/AdhyWiranto44/object-detection-indonesian-traffic-signs-using-yolo-algorithm), yang mencakup berbagai jenis rambu lalu lintas di Indonesia. Dataset ini terdiri dari gambar rambu lalu lintas yang telah dilabeli, termasuk kategori seperti lampu merah, lampu hijau, dan rambu dilarang berhenti.

### Proses Pelatihan Model

1. **Persiapan Dataset**: Dataset diunduh dari repositori GitHub di atas dan disiapkan dalam format yang sesuai untuk pelatihan model YOLOv10. Data dibagi menjadi set pelatihan dan set pengujian untuk memastikan model dapat dievaluasi dengan baik.

2. **Konfigurasi Model**: File konfigurasi untuk YOLOv10 disiapkan, termasuk pengaturan untuk arsitektur model, parameter pelatihan, dan jumlah kelas yang sesuai dengan dataset rambu lalu lintas.

3. **Pelatihan**: Menggunakan framework seperti TensorFlow, model YOLOv10 dilatih dengan dataset yang telah disiapkan. Proses pelatihan mencakup pengoptimalan bobot model untuk memaksimalkan akurasi deteksi rambu.

4. **Evaluasi Model**: Setelah pelatihan, model dievaluasi menggunakan data pengujian untuk mengukur performa dalam mendeteksi rambu lalu lintas.

### Contoh Gambar

Berikut adalah beberapa contoh gambar dari dataset yang menunjukkan jenis rambu lalu lintas yang dikenali oleh model:

![Lampu Merah](https://link-to-your-example-image-red-light.jpg)  
_Contoh rambu lampu merah_

![Lampu Hijau](https://link-to-your-example-image-green-light.jpg)  
_Contoh rambu lampu hijau_

![Dilarang Berhenti](https://link-to-your-example-image-no-stop.jpg)  
_Contoh rambu dilarang berhenti_
