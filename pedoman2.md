# **PRODUCT REQUIREMENTS DOCUMENT (PRD)** 

## **Prototipe Sistem Keselamatan dan Pemantauan Pengendara Sepeda Motor Berbasis IoT** 

|**Dokumen**|Product Requirements Document — Versi 2|
|---|---|
|**Jenis Produk**|Prototipe Hardware + IoT + Backend +<br>Application|
|**Konteks**|Program Kreativitas Mahasiswa (PKM)|
|**Tahap**|Perancangan dan pengembangan prototipe|
|**Target Utama**|Keselamatan, pemantauan kecepatan, lokasi, dan<br>respons kondisi darurat|



## **1. Executive Summary** 

Produk yang dirancang adalah sebuah sistem keselamatan pengendara sepeda motor yang mengintegrasikan perangkat IoT pada kendaraan dengan aplikasi digital. Perangkat bertugas memperoleh data pergerakan kendaraan dan lokasi, kemudian data diproses untuk memantau kondisi berkendara. Ketika kecepatan melewati batas yang ditentukan, sistem memberikan peringatan kepada pengendara. Selain itu, sistem dirancang untuk mengenali pola gerakan yang mengindikasikan potensi kecelakaan. Jika kondisi tersebut memenuhi kriteria darurat, sistem meneruskan informasi lokasi dan status kejadian kepada kontak terpercaya yang telah didaftarkan pengguna. 

Produk terdiri dari empat lapisan utama: perangkat/sensor pada kendaraan, komunikasi perangkat, backend untuk pemrosesan dan penyimpanan data, serta aplikasi sebagai antarmuka pengguna. Pada tahap PKM, fokus utama adalah membuktikan bahwa seluruh komponen dapat bekerja sebagai satu alur end-to-end dalam skenario pengujian yang terkontrol. 

## **2. Latar Belakang dan Problem Statement** 

Keselamatan pengendara sepeda motor tidak hanya dipengaruhi oleh kemampuan kendaraan, tetapi juga oleh perilaku berkendara dan kecepatan respons ketika terjadi kondisi darurat. Dalam situasi kecelakaan, keterlambatan penyampaian informasi lokasi dapat menyulitkan orang terdekat untuk mengetahui kondisi pengendara. Di sisi lain, aplikasi pelacakan lokasi saja tidak secara langsung menghubungkan data kendaraan dengan kondisi keselamatan. 

### **Problem yang ingin diselesaikan:** 

- Pengendara membutuhkan peringatan ketika kecepatan melewati batas yang telah ditentukan. 

- Kontak terpercaya membutuhkan informasi lokasi pengendara ketika terjadi kondisi darurat. 

- Deteksi kondisi darurat sebaiknya memanfaatkan data gerakan kendaraan, bukan hanya tombol manual. 

- Data dari kendaraan, lokasi, dan notifikasi perlu berada dalam satu sistem terintegrasi. 

## **3. Product Vision** 

Membangun prototipe sistem keselamatan berkendara yang mampu menghubungkan kondisi kendaraan dengan informasi digital secara cepat, terukur, dan mudah dipantau oleh pengendara maupun orang terpercaya. 

## **4. Product Objectives** 

|**ID**|**Objective**|
|---|---|
|OBJ-01|Membuat perangkat IoT yang mampu<br>memperoleh data gerakan kendaraan.|
|OBJ-02|Membangun mekanisme pemantauan kecepatan<br>dan pemberian peringatan overspeed.|
|OBJ-03|Menyediakan pemantauan lokasi pengendara<br>pada aplikasi.|
|OBJ-04|Menyediakan fitur trusted contacts sebagai<br>tujuan informasi darurat.|
|OBJ-05|Mengembangkan mekanisme deteksi indikasi<br>kecelakaan berbasis data sensor.|
|OBJ-06|Membuktikan pengiriman informasi darurat dari<br>perangkat sampai ke kontak terpercaya.|



## **5. Target User dan Persona** 

|**User**|**Kebutuhan**|**Pain Point**|**Solusi Produk**|
|---|---|---|---|
|Pengendara|Mengetahui kondisi<br>berkendara dan<br>mendapat peringatan.|Tidak selalu menyadari<br>overspeed atau kondisi<br>berbahaya.|Speed monitoring,<br>alert, dan aplikasi.|
|Trusted Contact|Mengetahui<br>kondisi/lokasi<br>pengendara saat<br>darurat.|Tidak mengetahui<br>kejadian secara cepat.|Emergency notification<br>+ lokasi.|
|Tim<br>Pengembang/Penguji|Memvalidasi kinerja<br>prototipe.|Sulit menguji sistem<br>end-to-end jika<br>komponen terpisah.|Dashboard/data log dan<br>skenario pengujian.|



## **6. Product Scope** 

|**Area**|**Termasuk dalam Prototype**|**Batasan**|
|---|---|---|
|Hardware|Sensor, microcontroller,<br>komunikasi, indikator alert,<br>power supply.|Belum ditujukan untuk<br>produksi massal/sertifikasi<br>kendaraan.|
|Speed|Monitoring kecepatan dan<br>threshold overspeed.|Bukan alat penegakan hukum<br>atau alat ukur tersertifikasi.|
|Location|GPS/GNSS dan tampilan lokasi<br>pada aplikasi.|Akurasi bergantung pada<br>kondisi sinyal.|
|Accident|Deteksi pola<br>benturan/perubahan gerakan<br>berdasarkan sensor.|Tidak menjamin seluruh<br>kecelakaan terdeteksi.|
|Notification|Notifikasi ke trusted contact;<br>integrasi platform dapat berupa<br>prototipe/simulasi.|Layanan emergency response<br>resmi berada di luar scope.|
|App|Akun, pairing, dashboard,<br>speed status, map, trusted<br>contacts, emergency status,<br>history dasar.|Belum mencakup analitik skala<br>besar.|



## **7. Feature Prioritization — MoSCoW** 

|**Priority**|**Feature**|**Alasan**|
|---|---|---|
|Must Have|Device pairing|Tanpa pairing, perangkat tidak<br>dapat dikaitkan dengan<br>pengguna.|
|Must Have|Speed monitoring|Fungsi inti keselamatan<br>berkendara.|
|Must Have|Overspeed alert|Respons langsung terhadap<br>kondisi overspeed.|
|Must Have|Location tracking|Data lokasi diperlukan untuk<br>monitoring dan keadaan<br>darurat.|
|Must Have|Trusted contacts|Tujuan utama pengiriman<br>informasi darurat.|
|Must Have|Accident detection prototype|Membuktikan konsep<br>keselamatan end-to-end.|
|Must Have|Emergency notification|Output utama ketika kondisi<br>darurat terdeteksi.|
|Should Have|Trip history|Mendukung evaluasi dan<br>pengalaman pengguna.|
|Could Have|Driving analytics|Dapat dikembangkan setelah|



|**Priority**|**Feature**|**Alasan**|
|---|---|---|
|||MVP stabil.|
|Won't Have (MVP)|Integrasi emergency services<br>resmi|Kompleksitas dan dependensi<br>eksternal terlalu tinggi untuk<br>tahap prototipe.|



## **8. User Journey** 

|**Tahap**|**Aktivitas Pengguna**|**Respons Sistem**|
|---|---|---|
|1. Onboarding|Registrasi/login.|Membuat akun dan profil<br>pengguna.|
|2. Device Setup|Menghubungkan perangkat ke<br>akun.|Sistem melakukan pairing dan<br>menyimpan identitas perangkat.|
|3. Safety Setup|Mengatur batas kecepatan dan<br>trusted contacts.|Konfigurasi disimpan.|
|4. Start Ride|Mengaktifkan perangkat dan<br>berkendara.|Sensor mulai membaca data.|
|5. Monitoring|Melihat status kecepatan dan<br>lokasi.|Aplikasi menampilkan data<br>yang diterima.|
|6. Overspeed|Pengendara melewati threshold.|Alert diberikan dan event<br>dicatat.|
|7. Emergency|Terjadi pola benturan/gerakan<br>ekstrem.|Sistem memvalidasi event<br>sesuai aturan prototipe.|
|8. Notification|Tidak ada<br>pembatalan/konfirmasi aman<br>sesuai rancangan.|Trusted contact menerima<br>informasi dan lokasi.|



## **9. Use Cases** 

|**ID**|**Use Case**|**Aktor**|**Hasil**|
|---|---|---|---|
|UC-01|Register/Login|Pengendara|Akun berhasil<br>dibuat/diakses.|
|UC-02|Pair Device|Pengendara|Device terhubung<br>dengan akun.|
|UC-03|Set Speed Limit|Pengendara|Threshold tersimpan.|
|UC-04|Monitor Ride|Pengendara|Kecepatan/status/lokasi<br>terlihat.|
|UC-05|Receive Overspeed<br>Alert|Pengendara|Peringatan diterima.|
|UC-06|Manage Trusted|Pengendara|Kontak|



|**ID**|**Use Case**|**Aktor**|**Hasil**|
|---|---|---|---|
||Contact||tersimpan/diubah/dihap<br>us.|
|UC-07|Detect Accident|System|Event kecelakaan<br>teridentifikasi<br>berdasarkan kriteria.|
|UC-08|Send Emergency Alert|System|Informasi darurat<br>diteruskan ke trusted<br>contact.|
|UC-09|View Emergency<br>Status|Trusted Contact|Kontak melihat status<br>dan lokasi yang<br>tersedia.|



## **10. Functional Requirements — Hardware/Device** 

|**ID**|**Requirement**|**Input**|**Process**|**Output**|**Priority**|
|---|---|---|---|---|---|
|HW-01|Read motion<br>sensor|Gyro/<br>accelerometer|Sampling<br>sensor|Motion data|Must|
|HW-02|Read location|GPS/GNSS|Parse<br>coordinates|Latitude/<br>longitude|Must|
|HW-03|Estimate speed|GPS/GNSS<br>and/or wheel<br>sensor|Calculate/<br>obtain speed|Speed value|Must|
|HW-04|Overspeed<br>decision|Speed +<br>threshold|Compare<br>threshold|Overspeed<br>state|Must|
|HW-05|Local alert|Overspeed<br>state|Activate<br>buzzer/LED|Alert to rider|Must|
|HW-06|Detect impact<br>pattern|Acceleration +<br>angular data|Filtering +<br>threshold/rules|Potential<br>accident event|Must|
|HW-07|Transmit data|Sensor/state<br>data|Package and<br>send|Telemetry<br>packet|Must|
|HW-08|Connection<br>state|Communicatio<br>n status|Monitor<br>connection|Online/offline<br>state|Should|



## **11. Functional Requirements — Application** 

|**ID**|**Feature**|**Requirement Detail**|**Priority**|
|---|---|---|---|
|APP-01|Authentication|User dapat register,|Must|
|||login, logout, dan||
|||mengelola profil dasar.||
|APP-02|Dashboard|Menampilkan status|Must|



|**ID**|**Feature**|**Requirement Detail**|**Priority**|
|---|---|---|---|
|||device, speed status,<br>lokasi, dan status<br>keselamatan.||
|APP-03|Device Pairing|User dapat<br>menghubungkan/memu<br>tus perangkat.|Must|
|APP-04|Speed Limit|User dapat menentukan<br>threshold kecepatan.|Must|
|APP-05|Overspeed Status|Menampilkan status<br>normal/overspeed dan<br>riwayat event dasar.|Must|
|APP-06|Map|Menampilkan posisi<br>pengendara pada peta.|Must|
|APP-07|Trusted Contacts|CRUD kontak<br>terpercaya dan<br>informasi penerima<br>notifikasi.|Must|
|APP-08|Emergency Status|Menampilkan status<br>kejadian, waktu, dan<br>lokasi yang tersedia.|Must|
|APP-09|Trip History|Menampilkan<br>ringkasan<br>perjalanan/event yang<br>tersimpan.|Should|
|APP-10|Settings|Mengelola preferensi<br>dasar notifikasi dan<br>device.|Should|



## **12. Detailed Feature Descriptions** 

**12.1 Device Pairing** Pengguna menghubungkan perangkat fisik dengan akun aplikasi. Sistem memberikan identitas unik perangkat dan memastikan data telemetry dikaitkan dengan pengguna yang benar. 

**12.2 Speed Monitoring** Sistem menerima nilai kecepatan dari sumber yang dipilih. Aplikasi menampilkan status kecepatan secara ringkas, sedangkan perangkat dapat memberikan peringatan lokal agar pengendara tidak harus selalu melihat layar. 

**12.3 Overspeed Alert** Ketika kecepatan berada di atas threshold selama kondisi yang ditentukan, sistem mengubah status menjadi overspeed dan mengaktifkan mekanisme alert. Threshold dan durasi validasi harus ditentukan melalui pengujian. 

**12.4 Location Tracking** Perangkat atau sistem memperoleh koordinat lokasi dan mengirimkannya ke backend. Aplikasi menampilkan posisi terakhir yang tersedia. Jika koneksi atau GPS hilang, sistem harus menampilkan status data tidak tersedia/terakhir. 

**12.5 Trusted Contacts** Pengguna dapat mendaftarkan orang yang dipercaya sebagai penerima informasi darurat. Data minimum dapat mencakup nama, nomor kontak, hubungan, dan status aktif. 

**12.6 Accident Detection** Sistem menganalisis kombinasi percepatan, perubahan orientasi, dan/atau kondisi kecepatan untuk mencari pola yang mengindikasikan benturan atau kehilangan kendali. Pada tahap prototipe, parameter diperoleh dari kalibrasi dan skenario uji, sehingga hasil harus disebut sebagai indikasi, bukan kepastian kecelakaan. 

**12.7 Emergency Notification** Ketika event darurat memenuhi kriteria, sistem membuat emergency event yang memuat identitas pengguna, waktu, status kejadian, dan lokasi terakhir. Informasi tersebut kemudian dikirim ke trusted contact melalui mekanisme notifikasi yang tersedia pada prototipe. 

**12.8 Emergency Cancellation/Confirmation** Untuk mengurangi false positive, rancangan dapat menyediakan periode konfirmasi setelah indikasi kecelakaan. Jika pengguna menyatakan aman, notifikasi dapat dibatalkan. Jika tidak ada respons, sistem melanjutkan proses notifikasi. 

## **13. Hardware Architecture** 

```
Sensor Layer → Gyroscope + Accelerometer + GPS/GNSS / Wheel Rotation Sensor
    ↓
Processing Layer → Microcontroller
    ↓
Communication Layer
    ↓
Backend/API
    ↓
Application Layer → User & Trusted Contacts
```

### **Fungsi komponen:** 

- **Gyroscope** : mengukur angular velocity dan perubahan orientasi. 

- **Accelerometer** : mengukur percepatan linear dan membantu identifikasi benturan/deselerasi ekstrem. 

- **GPS/GNSS** : menyediakan posisi dan dapat menjadi sumber estimasi kecepatan. 

- **Wheel rotation sensor/encoder (opsional)** : menghitung rotasi roda sebagai alternatif/pembanding estimasi kecepatan. 

- **Microcontroller** : membaca sensor, melakukan filtering/logic dasar, dan mengirim telemetry. 

- **Communication module** : menyediakan jalur pengiriman data dari perangkat ke sistem. 

- **Alert actuator** : buzzer/LED atau mekanisme lain untuk alert lokal. 

## **14. Sensor Fusion dan Catatan Teknis** 

Konsep awal menyebut penggunaan teori gyro untuk mendeteksi kecepatan. Secara teknis, gyroscope mengukur kecepatan sudut, bukan kecepatan linear kendaraan. Oleh karena itu PRD menggunakan pendekatan sensor fusion. GPS/GNSS dapat digunakan untuk memperoleh kecepatan 

dan lokasi, accelerometer untuk percepatan/benturan, serta gyroscope untuk perubahan orientasi dan dinamika gerakan. Bila diperlukan akurasi kecepatan berbasis roda, sensor rotasi/encoder dapat menjadi sumber tambahan. Pemilihan final harus ditentukan berdasarkan hasil eksperimen hardware. 

## **15. Software Architecture** 

|**Layer**|**Komponen**|**Tanggung Jawab**|
|---|---|---|
|Device|Firmware|Sensor reading, filtering, local<br>alert, telemetry.|
|Communication|BLE/Wi-Fi/Cellular sesuai<br>desain|Transport data device.|
|Backend|API + business logic|Authentication, device data,<br>event processing, contacts,<br>notification.|
|Database|Relational/NoSQL sesuai<br>implementasi|User, device, telemetry<br>summary, contacts, events.|
|Application|Mobile/Web|Dashboard, map, settings,<br>contact management,<br>emergency status.|
|External|Map/notification platform|Peta dan channel notifikasi bila<br>digunakan.|



## **16. Data Flow** 

1. Sensor membaca data → 

2. Microcontroller melakukan preprocessing → 

3. Telemetry dikirim → 

4. Backend memvalidasi dan menyimpan data penting → 

5. Rule engine mengevaluasi speed/emergency event → 

6. Aplikasi memperbarui dashboard → 

7. Jika event darurat memenuhi kriteria, notification service mengirimkan informasi kepada trusted contact. 

## **17. Data Requirements** 

|**Entity**|**Contoh Data**|**Kegunaan**|
|---|---|---|
|User|user_id, name, email, password<br>hash|Identitas pengguna.|



|**Entity**|**Contoh Data**|**Kegunaan**|
|---|---|---|
|Device|device_id, user_id, status,<br>firmware_version|Identitas dan status perangkat.|
|Speed Config|speed_limit, unit, updated_at|Konfigurasi threshold.|
|Telemetry|timestamp, latitude, longitude,<br>speed, accel, gyro|Data sensor/monitoring.|
|Trusted Contact|contact_id, user_id, name,<br>phone, relation, active|Penerima notifikasi.|
|Emergency Event|event_id, user_id, timestamp,<br>location, event_type, status|Catatan kejadian darurat.|
|Trip|trip_id, user_id, start_time,<br>end_time, summary|Riwayat perjalanan.|



## **18. Example Telemetry Packet** 

Secara konseptual, perangkat dapat mengirim paket data yang berisi `device_id` , `timestamp` , `latitude` , `longitude` , `speed` , `acceleration` , `gyroscope values` , `battery/status` , dan `connection status` . Format aktual dapat berupa JSON atau format ringan lain sesuai protokol komunikasi yang dipilih. 

## **19. Accident Detection Logic — Prototype** 

Deteksi kecelakaan tidak sebaiknya hanya menggunakan satu threshold. Algoritma awal dapat menggunakan kombinasi parameter seperti perubahan percepatan yang ekstrem, perubahan angular velocity/orientasi, kecepatan sebelum event, dan perubahan kondisi setelah event. Setelah event terdeteksi, sistem dapat memasuki status _Potential Accident_ , menjalankan periode konfirmasi, lalu mengubah status menjadi _Emergency_ apabila kriteria terpenuhi atau tidak ada pembatalan. 

|**State**|**Deskripsi**|
|---|---|
|NORMAL|Kondisi berkendara normal.|
|OVERSPEED|Kecepatan melewati threshold.|
|POTENTIAL_ACCIDENT|Pola sensor mencurigakan terdeteksi.|
|CONFIRMATION|Sistem menunggu konfirmasi pengguna jika<br>fitur digunakan.|
|EMERGENCY|Kejadian dianggap perlu diberitahukan ke<br>trusted contact.|
|RESOLVED|Event selesai/ditutup.|



## **20. Emergency Notification Payload** 

Minimal informasi yang dikirim: nama/ID pengguna, jenis event, waktu kejadian, lokasi terakhir yang tersedia, status event, dan informasi bahwa pesan berasal dari sistem prototipe. Untuk pengembangan nyata, isi pesan dan mekanisme autentikasi harus memperhatikan keamanan serta privasi pengguna. 

## **21. Non-Functional Requirements** 

|**Kategori**|**Requirement**|
|---|---|
|Performance|Pemrosesan alert harus cukup cepat untuk<br>skenario pengujian dan tidak membebani<br>microcontroller secara berlebihan.|
|Reliability|Sistem harus menangani sensor noise, data<br>hilang, dan koneksi terputus tanpa langsung<br>menghasilkan event kecelakaan palsu.|
|Availability|Komponen utama harus aktif selama skenario<br>pengujian dan menunjukkan status jika salah<br>satu layanan tidak tersedia.|
|Security|Authentication, authorization, credential, dan<br>data sensitif harus dikelola dengan aman.|
|Privacy|Lokasi hanya digunakan untuk tujuan yang<br>dijelaskan dan akses dibatasi kepada pihak yang<br>berwenang.|
|Usability|Pengguna dapat memahami status normal,<br>overspeed, dan emergency tanpa penjelasan<br>teknis.|
|Maintainability|Firmware, backend, database, dan aplikasi<br>dibuat modular.|
|Testability|Setiap fitur inti memiliki skenario uji dan<br>acceptance criteria.|



## **22. Acceptance Criteria** 

|**ID**|**Feature**|**Acceptance Criteria**|
|---|---|---|
|AC-01|Pairing|Device dapat dipasangkan dan<br>identitasnya muncul pada akun<br>yang benar.|
|AC-02|Speed|Nilai/status speed dapat<br>diterima dan ditampilkan.|
|AC-03|Overspeed|Ketika threshold pengujian<br>terlampaui sesuai aturan, alert<br>aktif.|



|**ID**|**Feature**|**Acceptance Criteria**|
|---|---|---|
|AC-04|Location|Aplikasi dapat menampilkan<br>koordinat lokasi yang diterima.|
|AC-05|Trusted Contact|User dapat menambah dan<br>menghapus minimal satu<br>kontak.|
|AC-06|Accident Detection|Skenario benturan yang telah<br>ditentukan menghasilkan event<br>sesuai threshold/algoritma uji.|
|AC-07|Emergency|Event darurat menghasilkan<br>payload yang berisi lokasi dan<br>informasi kejadian.|
|AC-08|Notification|Trusted contact menerima<br>notifikasi pada skenario<br>pengujian.|
|AC-09|Failure Handling|Ketika koneksi terputus,<br>aplikasi/device menampilkan<br>status offline/tidak tersedia.|
|AC-10|End-to-End|Skenario dari sensor →<br>backend → aplikasi →<br>notifikasi dapat<br>didemonstrasikan.|



## **23. Error & Exception Handling** 

|**Kondisi**|**Respons Sistem**|
|---|---|
|GPS unavailable|Tampilkan lokasi terakhir yang valid dan status<br>lokasi tidak tersedia.|
|Device disconnected|Tandai device offline; jangan membuat event<br>darurat hanya karena koneksi hilang.|
|Sensor invalid/noisy|Filter/abaikan pembacaan tidak valid dan catat<br>error untuk debugging.|
|Backend unavailable|Device dapat menyimpan data minimum<br>sementara jika hardware mendukung; aplikasi<br>menampilkan status layan[…]_(teks di dokumen_<br>_sumber terpotong di sini — perlu dilengkapi)_|
|Notification failure|Catat kegagalan dan tampilkan status<br>pengiriman; jangan mengklaim pesan berhasil<br>bila belum terkonfirmasi.|
|False accident suspected|Gunakan confirmation/cancellation flow jika<br>termasuk scope implementasi.|



## **24. Security & Privacy** 

- Password tidak disimpan dalam bentuk plaintext; gunakan password hashing yang sesuai. 

- Gunakan authentication dan authorization untuk membatasi akses data pengguna. 

- Data lokasi merupakan data sensitif secara operasional sehingga akses dan penyimpanannya harus dibatasi. 

- Trusted contacts hanya dapat dikelola oleh pengguna yang berhak. 

- API harus memvalidasi device/user identity agar perangkat tidak dapat mengirim data atas nama pengguna lain. 

- Untuk demo PKM, gunakan data pengujian dan hindari membagikan data lokasi pribadi secara terbuka. 

## **25. Prototype Testing Plan** 

|**Test Area**|**Scenario**|**Expected Result**|
|---|---|---|
|Sensor|Kendaraan bergerak normal|Data sensor berubah sesuai<br>gerakan.|
|Speed|Kecepatan di bawah threshold|Status normal.|
|Speed|Kecepatan di atas threshold|Overspeed alert aktif.|
|Location|Perangkat berpindah lokasi|Lokasi pada aplikasi diperbarui.|
|Accident|Simulasi benturan terkontrol|Potential Accident/Event<br>muncul sesuai kriteria.|
|Notification|Event emergency dibuat|Trusted contact menerima<br>informasi.|
|Connectivity|Koneksi diputus|Status offline ditampilkan dan<br>sistem tidak salah mendeteksi<br>kecelakaan.|
|End-to-End|Jalankan seluruh skenario|Data sensor sampai notifikasi<br>berhasil mengalir.|



## **26. Success Metrics** 

|**Metric**|**Cara Evaluasi**|
|---|---|
|Overspeed Detection Accuracy|Bandingkan event yang terdeteksi dengan<br>skenario uji overspeed yang diketahui.|
|Accident Detection Performance|Uji false positive dan false negative pada<br>skenario normal vs simulasi benturan.|
|Location Availability|Ukur persentase pengujian ketika lokasi berhasil<br>diterima.|
|Notification Success Rate|Hitung keberhasilan pengiriman notifikasi pada|



|**Metric**|**Cara Evaluasi**|
|---|---|
||skenario yang valid.|
|End-to-End Success|Hitung skenario penuh yang berhasil dari sensor<br>hingga trusted contact.|
|Usability|Observasi keberhasilan pengguna<br>menyelesaikan setup tanpa bantuan teknis.|



## **27. Risks and Mitigation** 

|**Risk**|**Impact**|**Mitigation**|
|---|---|---|
|Gyro tidak langsung mengukur<br>speed linear|Konsep pengukuran tidak<br>akurat|Gunakan sensor<br>fusion/GPS/encoder dan<br>jelaskan fungsi tiap sensor.|
|False positive accident|Kontak menerima alarm palsu|Multi-parameter detection +<br>confirmation window.|
|False negative accident|Alarm tidak terkirim|Pengujian banyak skenario dan<br>dokumentasikan batasan.|
|GPS error|Lokasi tidak tepat|Gunakan last valid location dan<br>status accuracy.|
|Network loss|Data/notifikasi terlambat|Connection state, retry, dan<br>buffer bila memungkinkan.|
|Sensor noise|Event salah|Calibration dan filtering.|
|Battery/power issue|Device mati|Monitoring power dan desain<br>supply yang stabil.|
|API platform berubah|Notifikasi gagal|Abstraction layer/simulasi pada<br>tahap prototype.|



## **28. MVP Definition** 

MVP prototipe dianggap selesai apabila perangkat dapat membaca data sensor, memperoleh lokasi, menghasilkan status kecepatan, memberikan overspeed alert, terhubung ke aplikasi, menyimpan trusted contact, menghasilkan event kecelakaan berdasarkan skenario uji, dan mengirim notifikasi darurat beserta lokasi kepada trusted contact. MVP tidak menargetkan deployment publik atau jaminan keselamatan layaknya perangkat medis/emergency service tersertifikasi. 

## **29. Future Development** 

- Pengembangan model machine learning untuk klasifikasi kecelakaan berbasis dataset sensor. 

- Kalibrasi sensor berdasarkan tipe kendaraan dan kondisi jalan. 

- Optimasi casing, mounting, waterproofing, dan power management. 

- Integrasi layanan notifikasi resmi yang sesuai dengan kebijakan platform. 

- Penambahan geofencing dan analisis perilaku berkendara. 

- Penambahan dashboard keluarga/organisasi dengan kontrol privasi yang jelas. 

- Pengujian lapangan yang lebih luas dan evaluasi statistik performa. 

## **30. Roadmap Prototipe** 

|**Tahap**|**Output**|
|---|---|
|1. Requirement|PRD, use case, scope, acceptance criteria.|
|2. Hardware Proof of Concept|Sensor + microcontroller membaca data.|
|3. Firmware|Sampling, filtering, threshold, telemetry.|
|4. Backend|API, database, event processing.|
|5. Application|Dashboard, map, contacts, status.|
|6. Integration|Hardware → backend → application.|
|7. Testing|Speed, location, accident simulation,<br>notification.|
|8. Evaluation|Analisis hasil, limitations, dan perbaikan.|



## **31. Final Product Definition** 

Produk akhir pada tahap PKM adalah demonstrator sistem keselamatan pengendara yang menunjukkan integrasi hardware dan software secara end-to-end. Hardware dipasang pada sepeda motor untuk membaca parameter gerakan/lokasi, sedangkan software menyediakan monitoring, konfigurasi keselamatan, trusted contacts, dan emergency notification. Sistem ditujukan sebagai proof of concept yang dapat dikembangkan lebih lanjut, bukan sebagai perangkat keselamatan tersertifikasi atau pengganti layanan darurat resmi. 

## **32. Kesimpulan** 

PRD ini menetapkan kebutuhan produk dari sisi pengguna, fitur, hardware, software, data, arsitektur, pengujian, keamanan, hingga batasan prototipe. Konsep utama yang dibangun adalah integrasi sensor kendaraan dengan aplikasi sehingga informasi mengenai kecepatan, lokasi, dan indikasi kondisi darurat dapat diproses dalam satu sistem. Untuk menjaga validitas teknis, pengukuran kecepatan dan deteksi kecelakaan menggunakan pendekatan sensor fusion dan harus divalidasi melalui eksperimen prototipe. 

## **33. Lampiran Harga Alat dan Bahan** 

|No|Komponen|Fungsi|Qty|Estimasi Harga|
|---|---|---|---|---|
|1|ESP32 DevKit V1|Microcontroller + Wi-Fi/Bluetooth|1|Rp80.000–100.000|
|2|MPU6050 / GY-521|Accelerometer + gyroscope|1|Rp25.000–55.000|
|3|GPS NEO-6M|GPS/GNSS untuk lokasi dan<br>estimasi kecepatan|1|Rp55.000–80.000|
|4|SIM800L|Komunikasi GSM/GPRS|1|Rp20.000–110.000|
|5|Buzzer|Local alert|1|Rp3.000–10.000|
|6|LED|Indikator status|1 set|Rp1.000–5.000|
|7|Push Button|Tombol konfirmasi / I’m ok|1|Rp2.000–5.000|
|8|Kabel Jumper|I'm OK Wiring prototype|1 set|Rp10.000–20.000|
|9|Breadboard / PCB<br>Prototype|Perakitan rangkaian|1|Rp10.000–30.000|
|10|Battery / Power<br>Supply|Sumber daya perangkat|1|Rp30.000–80.000|
|11|Casing + Mounting|Pelindung dan pemasangan pada<br>motor|1|Rp30.000–100.000|



**Estimasi hardware inti:** sekitar Rp250.000–400.000. 

**Estimasi realistis untuk 1 prototype** : sekitar Rp400.000–600.000 

