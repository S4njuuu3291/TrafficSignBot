# TrafficSignBot

Robot Mobil berbasis Arduino yang menggunakan Computer Vision untuk mendeteksi rambu lalu lintas dan merespon secara otomatis. Proyek ini dibuat untuk mensimulasikan kendaraan pintar yang dapat beroperasi di jalan raya

Fitur Utama Robot:

- Line Following

Robot mampu mendeteksi garis yang mana garis ini akan menjadi seolah track untuk dilalui robot, robot akan bergerak mengikuti track

- Merespons Input

Robot mampu merespon input dan melakukan sesuatu tergantung input. Misal jika input menyuruh robot untuk belok kanan, robot akan belok kanan (Tergantung track).

- Deteksi Rambu lalu lintas menggunakan model YOLOv10.

Alasan pemilihan model ini karena YOLO merupakan model yang paling populer dan efektif dalam deteksi objek, terutama dalam tugas yang memerlukan deteksi cepat secara realtime

- Integrasi antara Model Deteksi dan Arduino

Dalam hal ini akan dilakukan integrasi antara model deteksi dan Arduino. Kedua komponen ini beserta komponen lainnya saling berkolaborasi untuk menghasilkan robot mobil yang mampu melakukan tugas yang diminta

- Respons Otomatis Terhadap Rambu

Robot mampu mendeteksi rambu lalu lintas dan merespons terkait jenis rambu, misal jika robot mendeteksi rambu lampu merah, robot akan berhenti. Juga misal jika robot mendeteksi rambu dilarang berhenti, jika robot diminta untuk berhenti, robot tidak akan melakukannya.

Teknologi yang Digunakan:

Terdapat beberapa teknologi atau library yang digunakan dalam proyek ini yaitu:

- Conputer Vision: OpenCV, Tensorflow, YOLOV10
- Hardware: Arduino, Infrared Sensor, DC Motor, Motor Driver, dll.
- Bahasa pemrograman: Python untuk computer vision dan C++ untuk Arduino

Cara Kerja:

Pengoperasian Dasar Robot:

- Robot dilengkapi dengan sensor line follower yang memungkinkan robot untuk mendeteksi dan mengikuti garis yang ada di jalan.
- Sensor ini memberikan umpan balik ke Arduino untuk mengatur motor dan memastikan robot tetap berada di jalur.

Perekaman Gambar:

- Sementara robot bergerak di sepanjang jalur, kamera (yang terhubung ke komputer atau mikroprosesor) secara terus-menerus menangkap gambar dari lingkungan sekitar, termasuk rambu lalu lintas yang mungkin muncul.

Deteksi Rambu Lalu Lintas:

- Gambar yang diambil oleh kamera kemudian dikirim ke model YOLOv9 yang telah dilatih untuk mendeteksi berbagai jenis rambu lalu lintas.
- Model ini menganalisis gambar dan mengidentifikasi rambu lalu lintas yang terlihat, seperti lampu merah, lampu hijau, dan rambu dilarang berhenti.

Pengolahan dan Respons:

- Berdasarkan hasil deteksi, robot akan melakukan tindakan yang sesuai:
  Rambu Lampu Merah: Jika model mendeteksi lampu merah, Arduino akan menerima perintah untuk menghentikan motor robot, sehingga robot berhenti.
  Rambu Lampu Hijau: Jika mendeteksi lampu hijau, Arduino mengirimkan perintah untuk melanjutkan pergerakan robot.
  Rambu Dilarang Berhenti: Jika robot sedang diminta untuk berhenti tetapi mendeteksi rambu dilarang berhenti, robot akan tetap bergerak dan tidak akan berhenti.
  dan seterusnya untuk rambu lain (menyusul)

Reaksi Dinamis:

Robot beroperasi dalam mode loop, di mana setiap deteksi rambu dan respons diulang secara terus menerus. Ini memungkinkan robot untuk beradaptasi dengan kondisi lalu lintas dan merespons secara real-time terhadap rambu yang berbeda yang ditemui di jalur.

Dataset dan Pelatihan Model:
