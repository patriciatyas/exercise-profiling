## Module 5 - Java Profiling

### Advanced Programming 2025

Patricia Herningtyas - 2306152241 - Class A


### Conclusion - JMeter Report and Test Results

#### Before Optimization
1. `/all-student` endpoint

![before test plan 1.jpg](../../Users/user/OneDrive/COLLEGE/Adpro/module-5%20testing%20screenshots/before%20test%20plan%201.jpg)

![log file test plan 1.jpg](../../Users/user/OneDrive/COLLEGE/Adpro/module-5%20testing%20screenshots/log%20file%20test%20plan%201.jpg)

2. `/all-student-name` endpoint

![before test plan 2.jpg](../../Users/user/OneDrive/COLLEGE/Adpro/module-5%20testing%20screenshots/before%20test%20plan%202.jpg)

![log file test plan 2.jpg](../../Users/user/OneDrive/COLLEGE/Adpro/module-5%20testing%20screenshots/log%20file%20test%20plan%202.jpg)

3. `/highest-gpa` endpoint

![before test plan 3.jpg](../../Users/user/OneDrive/COLLEGE/Adpro/module-5%20testing%20screenshots/before%20test%20plan%203.jpg)

![log file test plan 3.jpg](../../Users/user/OneDrive/COLLEGE/Adpro/module-5%20testing%20screenshots/log%20file%20test%20plan%203.jpg)

#### After Optimization
1. `/all-student` endpoint

![after test plan 1.jpg](../../Users/user/OneDrive/COLLEGE/Adpro/module-5%20testing%20screenshots/after%20test%20plan%201.jpg)

2. `/all-student-name` endpoint

![after test plan 2.jpg](../../Users/user/OneDrive/COLLEGE/Adpro/module-5%20testing%20screenshots/after%20test%20plan%202.jpg)

3. `/highest-gpa` endpoint

![after test plan 3.jpg](../../Users/user/OneDrive/COLLEGE/Adpro/module-5%20testing%20screenshots/after%20test%20plan%203.jpg)


### Reflection

**Perbedaan antara JMeter dan IntelliJ Profiler**
- JMeter digunakan untuk menguji beban kerja yang tinggi pada aplikasi dengan mensimulasikan banyak pengguna.
- IntelliJ Profiler digunakan untuk menemukan bagian-bagian kode dalam aplikasi yang menyebabkan kinerja menjadi lambat atau tidak optimal.

**Bagaimana proses profiling membantu untuk mengidentifikasi dan memahami titik lemah dalam aplikasi**

Profiling dapat membantu kita untuk menemukan *bottleneck* yang menyebabkan lambatnya performa aplikasi. Proses ini melibatkan pengumpulan data dan informasi seperti *CPU usage, memory allocation, garbage collection activity, dan thread concurrency*. 

**Efektivitas IntelliJ Profiler**

IntelliJ sudah sangat efektif karena IntelliJ menyediakan analisis *real-time* terhadap penggunaan CPU dan memori. Selain itu, IntelliJ membantu kita melihat *method* mana yang paling lambat dalam eksekusi. 

**Tantangan saat Performance Testing dan Profiling**

Menurut saya, data *profiling* sulit untuk dibaca karena hasil profiling bisa mengandung terlalu banyak informasi. Namun, solusinya adalah saya berfokus pada metode dengan waktu eksekusi tertinggi.
Selain itu, mengoptimalkan tanpa merusak fungsionalitas juga merupakan salah satu tantangan yang saya hadapi. Perubahan kode untuk optimasi bisa menyebabkan *bug*. Solusi dari hal ini adalah selalu jalankan *unit test* dan *integration test* setelah perubahan.

**Manfaat menggunakan IntelliJ Profiler**
Dengan menggunakan IntelliJ Profiler, saya dapat menganalisis performa kode secara akurat, pemantauan CPU real-time untuk menemukan *method* yang lambat, serta integrasi dengan IntelliJ IDEA sehingga mudah digunakan. 

**Cara mengatasi hasil profiling yang tidak konsisten dengan JMeter**
Jika hasil IntelliJ Profiler dengan JMeter tidak konsisten, hal yang akan saya lakukan adalah memeriksa kembali konfigurasi yang telah saya *set-up* pada JMeter dan memeriksa kembali hasil profiling yang saya dapat dari InteliiJ Profiler. Jika masih tidak konsisten, saya akan menggunakan *stack overflow* untuk mencari solusinya.

**Strategi optimasi kode setelah pengujian performa & profiling**
Pada *method* `joinStudentNames()`, penggunaan StringBuilder dapat menggantikan penggabungan string dengan operator "+" yang kurang efisien. Dengan StringBuilder, proses penggabungan nama mahasiswa menjadi lebih efisien karena kita hanya mengelola satu objek yang dapat dimodifikasi.
Untuk *method* `findStudentWithHighestGpa()`, implementasi Java Stream dapat menyederhanakan kode dan meningkatkan kinerja dengan memanfaatkan fungsi max() bersama Comparator untuk menemukan mahasiswa dengan GPA tertinggi dalam satu kali proses.
Pada metode `getAllStudentsWithCourses()`, prealokasi kapasitas ArrayList berdasarkan estimasi jumlah data dapat menghindari operasi resize yang mahal, sementara implementasi query database secara massal (bulk query) untuk mengambil semua data mahasiswa dan kursus dalam jumlah minimum panggilan database dapat mengurangi overhead jaringan yang signifikan.
Semua strategi ini bersamaan akan meningkatkan responsifitas aplikasi, terutama saat menangani data dalam jumlah besar.