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

- Gambar yang ditangkap oleh kamera kemudian dikirim ke model YOLOv10 yang telah dilatih untuk mendeteksi berbagai jenis rambu lalu lintas. Model ini akan menganalisis gambar dan mengidentifikasi rambu lalu lintas yang terdeteksi, seperti lampu merah, lampu hijau, dan rambu dilarang berhenti.

### Pengolahan dan Respons

- Berdasarkan hasil deteksi, robot akan melakukan tindakan yang sesuai:
  - **Rambu Lampu Merah**: Jika model mendeteksi lampu merah, Arduino akan menerima perintah untuk menghentikan motor robot, sehingga robot berhenti.
  - **Rambu Lampu Hijau**: Jika mendeteksi lampu hijau, Arduino mengirimkan perintah untuk melanjutkan pergerakan robot.
  - **Rambu Dilarang Berhenti**: Jika robot sedang diminta untuk berhenti tetapi mendeteksi rambu dilarang berhenti, robot akan tetap bergerak dan tidak akan berhenti.

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
