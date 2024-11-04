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
