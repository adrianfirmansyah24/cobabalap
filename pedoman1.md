# PRODUCT REQUIREMENTS DOCUMENT (PRD)
## Prototipe Sistem Keselamatan dan Pemantauan Pengendara Sepeda Motor Berbasis IoT

| | |
|---|---|
| **Dokumen** | Product Requirements Document — Versi 2 |
| **Jenis Produk** | Prototipe Hardware + IoT + Backend + Application |
| **Konteks** | Program Kreativitas Mahasiswa (PKM) |
| **Tahap** | Perancangan dan pengembangan prototipe |
| **Target Utama** | Keselamatan, pemantauan kecepatan, lokasi, dan respons kondisi darurat |

---

## 1. Executive Summary

Produk yang dirancang adalah sebuah sistem keselamatan pengendara sepeda motor yang mengintegrasikan perangkat IoT pada kendaraan dengan aplikasi digital. Perangkat bertugas memperoleh data pergerakan kendaraan dan lokasi, kemudian data diproses untuk memantau kondisi berkendara. Ketika kecepatan melewati batas yang ditentukan, sistem memberikan peringatan kepada pengendara. Selain itu, sistem dirancang untuk mengenali pola gerakan yang mengindikasikan potensi kecelakaan. Jika kondisi tersebut memenuhi kriteria darurat, sistem meneruskan informasi lokasi dan status kejadian kepada kontak terpercaya yang telah didaftarkan pengguna.

Produk terdiri dari empat lapisan utama: perangkat/sensor pada kendaraan, komunikasi perangkat, backend untuk pemrosesan dan penyimpanan data, serta aplikasi sebagai antarmuka pengguna. Pada tahap PKM, fokus utama adalah membuktikan bahwa seluruh komponen dapat bekerja sebagai satu alur end-to-end dalam skenario pengujian yang terkontrol.

---

## 2. Latar Belakang dan Problem Statement

Keselamatan pengendara sepeda motor tidak hanya dipengaruhi oleh kemampuan kendaraan, tetapi juga oleh perilaku berkendara dan kecepatan respons ketika terjadi kondisi darurat. Dalam situasi kecelakaan, keterlambatan penyampaian informasi lokasi dapat menyulitkan orang terdekat untuk mengetahui kondisi pengendara. Di sisi lain, aplikasi pelacakan lokasi saja tidak secara langsung menghubungkan data kendaraan dengan kondisi keselamatan.

**Problem yang ingin diselesaikan:**
- Pengendara membutuhkan peringatan ketika kecepatan melewati batas yang telah ditentukan.
- Kontak terpercaya membutuhkan informasi lokasi pengendara ketika terjadi kondisi darurat.
- Deteksi kondisi darurat sebaiknya memanfaatkan data gerakan kendaraan, bukan hanya tombol manual.
- Data dari kendaraan, lokasi, dan notifikasi perlu berada dalam satu sistem terintegrasi.

---

## 3. Product Vision

Membangun prototipe sistem keselamatan berkendara yang mampu menghubungkan kondisi kendaraan dengan informasi digital secara cepat, terukur, dan mudah dipantau oleh pengendara maupun orang terpercaya.

---

## 4. Product Objectives

| ID | Objective |
|---|---|
| OBJ-01 | Membuat perangkat IoT yang mampu memperoleh data gerakan kendaraan. |
| OBJ-02 | Membangun mekanisme pemantauan kecepatan dan pemberian peringatan overspeed. |
| OBJ-03 | Menyediakan pemantauan lokasi pengendara pada aplikasi. |
| OBJ-04 | Menyediakan fitur trusted contacts sebagai tujuan informasi darurat. |
| OBJ-05 | Mengembangkan mekanisme deteksi indikasi kecelakaan berbasis data sensor. |
| OBJ-06 | Membuktikan pengiriman informasi darurat dari perangkat sampai ke kontak terpercaya. |

---

## 5. Target User dan Persona

| User | Kebutuhan | Pain Point | Solusi Produk |
|---|---|---|---|
| Pengendara | Mengetahui kondisi berkendara dan mendapat peringatan. | Tidak selalu menyadari overspeed atau kondisi berbahaya. | Speed monitoring, alert, dan aplikasi. |
| Trusted Contact | Mengetahui kondisi/lokasi pengendara saat darurat. | Tidak mengetahui kejadian secara cepat. | Emergency notification + lokasi. |
| Tim Pengembang/Penguji | Memvalidasi kinerja prototipe. | Sulit menguji sistem end-to-end jika komponen terpisah. | Dashboard/data log dan skenario pengujian. |

---

## 6. Product Scope

| Area | Termasuk dalam Prototype | Batasan |
|---|---|---|
| Hardware | Sensor, microcontroller, komunikasi, indikator alert, power supply. | Belum ditujukan untuk produksi massal/sertifikasi kendaraan. |
| Speed | Monitoring kecepatan dan threshold overspeed. | Bukan alat penegakan hukum atau alat ukur tersertifikasi. |
| Location | GPS/GNSS dan tampilan lokasi pada aplikasi. | Akurasi bergantung pada kondisi sinyal. |
| Accident | Deteksi pola benturan/perubahan gerakan berdasarkan sensor. | Tidak menjamin seluruh kecelakaan terdeteksi. |
| Notification | Notifikasi ke trusted contact; integrasi platform dapat berupa prototipe/simulasi. | Layanan emergency response resmi berada di luar scope. |
| App | Akun, pairing, dashboard, speed status, map, trusted contacts, emergency status, history dasar. | Belum mencakup analitik skala besar. |

---

## 7. Feature Prioritization — MoSCoW

| Priority | Feature | Alasan |
|---|---|---|
| Must Have | Device pairing | Tanpa pairing, perangkat tidak dapat dikaitkan dengan pengguna. |
| Must Have | Speed monitoring | Fungsi inti keselamatan berkendara. |
| Must Have | Overspeed alert | Respons langsung terhadap kondisi overspeed. |
| Must Have | Location tracking | Data lokasi diperlukan untuk monitoring dan keadaan darurat. |
| Must Have | Trusted contacts | Tujuan utama pengiriman informasi darurat. |
| Must Have | Accident detection prototype | Membuktikan konsep keselamatan end-to-end. |
| Must Have | Emergency notification | Output utama ketika kondisi darurat terdeteksi. |
| Should Have | Trip history | Mendukung evaluasi dan pengalaman pengguna. |
| Could Have | Driving analytics | Dapat dikembangkan setelah MVP stabil. |
| Won't Have (MVP) | Integrasi emergency services resmi | Kompleksitas dan dependensi eksternal terlalu tinggi untuk tahap prototipe. |

---

## 8. User Journey

| Tahap | Aktivitas Pengguna | Respons Sistem |
|---|---|---|
| 1. Onboarding | Registrasi/login. | Membuat akun dan profil pengguna. |
| 2. Device Setup | Menghubungkan perangkat ke akun. | Sistem melakukan pairing dan menyimpan identitas perangkat. |
| 3. Safety Setup | Mengatur batas kecepatan dan trusted contacts. | Konfigurasi disimpan. |
| 4. Start Ride | Mengaktifkan perangkat dan berkendara. | Sensor mulai membaca data. |
| 5. Monitoring | Melihat status kecepatan dan lokasi. | Aplikasi menampilkan data yang diterima. |
| 6. Overspeed | Pengendara melewati threshold. | Alert diberikan dan event dicatat. |
| 7. Emergency | Terjadi pola benturan/gerakan ekstrem. | Sistem memvalidasi event sesuai aturan prototipe. |
| 8. Notification | Tidak ada pembatalan/konfirmasi aman sesuai rancangan. | Trusted contact menerima informasi dan lokasi. |

---

## 9. Use Cases

| ID | Use Case | Aktor | Hasil |
|---|---|---|---|
| UC-01 | Register/Login | Pengendara | Akun berhasil dibuat/diakses. |
| UC-02 | Pair Device | Pengendara | Device terhubung dengan akun. |
| UC-03 | Set Speed Limit | Pengendara | Threshold tersimpan. |
| UC-04 | Monitor Ride | Pengendara | Kecepatan/status/lokasi terlihat. |
| UC-05 | Receive Overspeed Alert | Pengendara | Peringatan diterima. |
| UC-06 | Manage Trusted Contact | Pengendara | Kontak tersimpan/diubah/dihapus. |
| UC-07 | Detect Accident | System | Event kecelakaan teridentifikasi berdasarkan kriteria. |
| UC-08 | Send Emergency Alert | System | Informasi darurat diteruskan ke trusted contact. |
| UC-09 | View Emergency Status | Trusted Contact | Kontak melihat status dan lokasi yang tersedia. |

---

## 10. Functional Requirements — Hardware/Device

| ID | Requirement | Input | Process | Output | Priority |
|---|---|---|---|---|---|
| HW-01 | Read motion sensor | Gyro/accelerometer | Sampling sensor | Motion data | Must |
| HW-02 | Read location | GPS/GNSS | Parse coordinates | Latitude/longitude | Must |
| HW-03 | Estimate speed | GPS/GNSS and/or wheel sensor | Calculate/obtain speed | Speed value | Must |
| HW-04 | Overspeed decision | Speed + threshold | Compare threshold | Overspeed state | Must |
| HW-05 | Local alert | Overspeed state | Activate buzzer/LED | Alert to rider | Must |
| HW-06 | Detect impact pattern | Acceleration + angular data | Filtering + threshold/rules | Potential accident event | Must |
| HW-07 | Transmit data | Sensor/state data | Package and send | Telemetry packet | Must |
| HW-08 | Connection state | Communication status | Monitor connection | Online/offline state | Should |

---

## 11. Functional Requirements — Application

| ID | Feature | Requirement Detail | Priority |
|---|---|---|---|
| APP-01 | Authentication | User dapat register, login, logout, dan mengelola profil dasar. | Must |
| APP-02 | Dashboard | Menampilkan status device, speed status, lokasi, dan status keselamatan. | Must |
| APP-03 | Device Pairing | User dapat menghubungkan/memutus perangkat. | Must |
| APP-04 | Speed Limit | User dapat menentukan threshold kecepatan. | Must |
| APP-05 | Overspeed Status | Menampilkan status normal/overspeed dan riwayat event dasar. | Must |
| APP-06 | Map | Menampilkan posisi pengendara pada peta. | Must |
| APP-07 | Trusted Contacts | CRUD kontak terpercaya dan informasi penerima notifikasi. | Must |
| APP-08 | Emergency Status | Menampilkan status kejadian, waktu, dan lokasi yang tersedia. | Must |
| APP-09 | Trip History | Menampilkan ringkasan perjalanan/event yang tersimpan. | Should |
| APP-10 | Settings | Mengelola preferensi dasar notifikasi dan device. | Should |

---

## 12. Detailed Feature Descriptions

**12.1 Device Pairing**
Pengguna menghubungkan perangkat fisik dengan akun aplikasi. Sistem memberikan identitas unik perangkat dan memastikan data telemetry dikaitkan dengan pengguna yang benar.

**12.2 Speed Monitoring**
Sistem menerima nilai kecepatan dari sumber yang dipilih. Aplikasi menampilkan status kecepatan secara ringkas, sedangkan perangkat dapat memberikan peringatan lokal agar pengendara tidak harus selalu melihat layar.

**12.3 Overspeed Alert**
Ketika kecepatan berada di atas threshold selama kondisi yang ditentukan, sistem mengubah status menjadi overspeed dan mengaktifkan mekanisme alert. Threshold dan durasi validasi harus ditentukan melalui pengujian.

**12.4 Location Tracking**
Perangkat atau sistem memperoleh koordinat lokasi dan mengirimkannya ke backend. Aplikasi menampilkan posisi terakhir yang tersedia. Jika koneksi atau GPS hilang, sistem harus menampilkan status data tidak tersedia/terakhir.

**12.5 Trusted Contacts**
Pengguna dapat mendaftarkan orang yang dipercaya sebagai penerima informasi darurat. Data minimum dapat mencakup nama, nomor kontak, hubungan, dan status aktif.

**12.6 Accident Detection**
Sistem menganalisis kombinasi percepatan, perubahan orientasi, dan/atau kondisi kecepatan untuk mencari pola yang mengindikasikan benturan atau kehilangan kendali. Pada tahap prototipe, parameter diperoleh dari kalibrasi dan skenario uji, sehingga hasil harus disebut sebagai indikasi, bukan kepastian kecelakaan.

**12.7 Emergency Notification**
Ketika event darurat memenuhi kriteria, sistem membuat emergency event yang memuat identitas pengguna, waktu, status kejadian, dan lokasi terakhir. Informasi tersebut kemudian dikirim ke trusted contact melalui mekanisme notifikasi yang tersedia pada prototipe.

**12.8 Emergency Cancellation/Confirmation**
Untuk mengurangi false positive, rancangan dapat menyediakan periode konfirmasi setelah indikasi kecelakaan. Jika pengguna menyatakan aman, notifikasi dapat dibatalkan. Jika tidak ada respons, sistem melanjutkan proses notifikasi.

---

## 13. Hardware Architecture

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

**Fungsi komponen:**
- **Gyroscope**: mengukur angular velocity dan perubahan orientasi.
- **Accelerometer**: mengukur percepatan linear dan membantu identifikasi benturan/deselerasi ekstrem.
- **GPS/GNSS**: menyediakan posisi dan dapat menjadi sumber estimasi kecepatan.
- **Wheel rotation sensor/encoder (opsional)**: menghitung rotasi roda sebagai alternatif/pembanding estimasi kecepatan.
- **Microcontroller**: membaca sensor, melakukan filtering/logic dasar, dan mengirim telemetry.
- **Communication module**: menyediakan jalur pengiriman data dari perangkat ke sistem.
- **Alert actuator**: buzzer/LED atau mekanisme lain untuk alert lokal.

---

## 14. Sensor Fusion dan Catatan Teknis

Konsep awal menyebut penggunaan teori gyro untuk mendeteksi kecepatan. Secara teknis, gyroscope mengukur kecepatan sudut, bukan kecepatan linear kendaraan. Oleh karena itu PRD menggunakan pendekatan sensor fusion. GPS/GNSS dapat digunakan untuk memperoleh kecepatan dan lokasi, accelerometer untuk percepatan/benturan, serta gyroscope untuk perubahan orientasi dan dinamika gerakan. Bila diperlukan akurasi kecepatan berbasis roda, sensor rotasi/encoder dapat menjadi sumber tambahan. Pemilihan final harus ditentukan berdasarkan hasil eksperimen hardware.

---

## 15. Software Architecture

| Layer | Komponen | Tanggung Jawab |
|---|---|---|
| Device | Firmware | Sensor reading, filtering, local alert, telemetry. |
| Communication | BLE/Wi-Fi/Cellular sesuai desain | Transport data device. |
| Backend | API + business logic | Authentication, device data, event processing, contacts, notification. |
| Database | Relational/NoSQL sesuai implementasi | User, device, telemetry summary, contacts, events. |
| Application | Mobile/Web | Dashboard, map, settings, contact management, emergency status. |
| External | Map/notification platform | Peta dan channel notifikasi bila digunakan. |

---

## 16. Data Flow

1. Sensor membaca data →
2. Microcontroller melakukan preprocessing →
3. Telemetry dikirim →
4. Backend memvalidasi dan menyimpan data penting →
5. Rule engine mengevaluasi speed/emergency event →
6. Aplikasi memperbarui dashboard →
7. Jika event darurat memenuhi kriteria, notification service mengirimkan informasi kepada trusted contact.

---

## 17. Data Requirements

| Entity | Contoh Data | Kegunaan |
|---|---|---|
| User | user_id, name, email, password hash | Identitas pengguna. |
| Device | device_id, user_id, status, firmware_version | Identitas dan status perangkat. |
| Speed Config | speed_limit, unit, updated_at | Konfigurasi threshold. |
| Telemetry | timestamp, latitude, longitude, speed, accel, gyro | Data sensor/monitoring. |
| Trusted Contact | contact_id, user_id, name, phone, relation, active | Penerima notifikasi. |
| Emergency Event | event_id, user_id, timestamp, location, event_type, status | Catatan kejadian darurat. |
| Trip | trip_id, user_id, start_time, end_time, summary | Riwayat perjalanan. |

---

## 18. Example Telemetry Packet

Secara konseptual, perangkat dapat mengirim paket data yang berisi `device_id`, `timestamp`, `latitude`, `longitude`, `speed`, `acceleration`, `gyroscope values`, `battery/status`, dan `connection status`. Format aktual dapat berupa JSON atau format ringan lain sesuai protokol komunikasi yang dipilih.

---

## 19. Accident Detection Logic — Prototype

Deteksi kecelakaan tidak sebaiknya hanya menggunakan satu threshold. Algoritma awal dapat menggunakan kombinasi parameter seperti perubahan percepatan yang ekstrem, perubahan angular velocity/orientasi, kecepatan sebelum event, dan perubahan kondisi setelah event. Setelah event terdeteksi, sistem dapat memasuki status *Potential Accident*, menjalankan periode konfirmasi, lalu mengubah status menjadi *Emergency* apabila kriteria terpenuhi atau tidak ada pembatalan.

| State | Deskripsi |
|---|---|
| NORMAL | Kondisi berkendara normal. |
| OVERSPEED | Kecepatan melewati threshold. |
| POTENTIAL_ACCIDENT | Pola sensor mencurigakan terdeteksi. |
| CONFIRMATION | Sistem menunggu konfirmasi pengguna jika fitur digunakan. |
| EMERGENCY | Kejadian dianggap perlu diberitahukan ke trusted contact. |
| RESOLVED | Event selesai/ditutup. |

---

## 20. Emergency Notification Payload

Minimal informasi yang dikirim: nama/ID pengguna, jenis event, waktu kejadian, lokasi terakhir yang tersedia, status event, dan informasi bahwa pesan berasal dari sistem prototipe. Untuk pengembangan nyata, isi pesan dan mekanisme autentikasi harus memperhatikan keamanan serta privasi pengguna.

---

## 21. Non-Functional Requirements

| Kategori | Requirement |
|---|---|
| Performance | Pemrosesan alert harus cukup cepat untuk skenario pengujian dan tidak membebani microcontroller secara berlebihan. |
| Reliability | Sistem harus menangani sensor noise, data hilang, dan koneksi terputus tanpa langsung menghasilkan event kecelakaan palsu. |
| Availability | Komponen utama harus aktif selama skenario pengujian dan menunjukkan status jika salah satu layanan tidak tersedia. |
| Security | Authentication, authorization, credential, dan data sensitif harus dikelola dengan aman. |
| Privacy | Lokasi hanya digunakan untuk tujuan yang dijelaskan dan akses dibatasi kepada pihak yang berwenang. |
| Usability | Pengguna dapat memahami status normal, overspeed, dan emergency tanpa penjelasan teknis. |
| Maintainability | Firmware, backend, database, dan aplikasi dibuat modular. |
| Testability | Setiap fitur inti memiliki skenario uji dan acceptance criteria. |

---

## 22. Acceptance Criteria

| ID | Feature | Acceptance Criteria |
|---|---|---|
| AC-01 | Pairing | Device dapat dipasangkan dan identitasnya muncul pada akun yang benar. |
| AC-02 | Speed | Nilai/status speed dapat diterima dan ditampilkan. |
| AC-03 | Overspeed | Ketika threshold pengujian terlampaui sesuai aturan, alert aktif. |
| AC-04 | Location | Aplikasi dapat menampilkan koordinat lokasi yang diterima. |
| AC-05 | Trusted Contact | User dapat menambah dan menghapus minimal satu kontak. |
| AC-06 | Accident Detection | Skenario benturan yang telah ditentukan menghasilkan event sesuai threshold/algoritma uji. |
| AC-07 | Emergency | Event darurat menghasilkan payload yang berisi lokasi dan informasi kejadian. |
| AC-08 | Notification | Trusted contact menerima notifikasi pada skenario pengujian. |
| AC-09 | Failure Handling | Ketika koneksi terputus, aplikasi/device menampilkan status offline/tidak tersedia. |
| AC-10 | End-to-End | Skenario dari sensor → backend → aplikasi → notifikasi dapat didemonstrasikan. |

---

## 23. Error & Exception Handling

| Kondisi | Respons Sistem |
|---|---|
| GPS unavailable | Tampilkan lokasi terakhir yang valid dan status lokasi tidak tersedia. |
| Device disconnected | Tandai device offline; jangan membuat event darurat hanya karena koneksi hilang. |
| Sensor invalid/noisy | Filter/abaikan pembacaan tidak valid dan catat error untuk debugging. |
| Backend unavailable | Device dapat menyimpan data minimum sementara jika hardware mendukung; aplikasi menampilkan status layan[…] *(teks di dokumen sumber terpotong di sini — perlu dilengkapi)* |
| Notification failure | Catat kegagalan dan tampilkan status pengiriman; jangan mengklaim pesan berhasil bila belum terkonfirmasi. |
| False accident suspected | Gunakan confirmation/cancellation flow jika termasuk scope implementasi. |

---

## 24. Security & Privacy

- Password tidak disimpan dalam bentuk plaintext; gunakan password hashing yang sesuai.
- Gunakan authentication dan authorization untuk membatasi akses data pengguna.
- Data lokasi merupakan data sensitif secara operasional sehingga akses dan penyimpanannya harus dibatasi.
- Trusted contacts hanya dapat dikelola oleh pengguna yang berhak.
- API harus memvalidasi device/user identity agar perangkat tidak dapat mengirim data atas nama pengguna lain.
- Untuk demo PKM, gunakan data pengujian dan hindari membagikan data lokasi pribadi secara terbuka.

---

## 25. Prototype Testing Plan

| Test Area | Scenario | Expected Result |
|---|---|---|
| Sensor | Kendaraan bergerak normal | Data sensor berubah sesuai gerakan. |
| Speed | Kecepatan di bawah threshold | Status normal. |
| Speed | Kecepatan di atas threshold | Overspeed alert aktif. |
| Location | Perangkat berpindah lokasi | Lokasi pada aplikasi diperbarui. |
| Accident | Simulasi benturan terkontrol | Potential Accident/Event muncul sesuai kriteria. |
| Notification | Event emergency dibuat | Trusted contact menerima informasi. |
| Connectivity | Koneksi diputus | Status offline ditampilkan dan sistem tidak salah mendeteksi kecelakaan. |
| End-to-End | Jalankan seluruh skenario | Data sensor sampai notifikasi berhasil mengalir. |

---

## 26. Success Metrics

| Metric | Cara Evaluasi |
|---|---|
| Overspeed Detection Accuracy | Bandingkan event yang terdeteksi dengan skenario uji overspeed yang diketahui. |
| Accident Detection Performance | Uji false positive dan false negative pada skenario normal vs simulasi benturan. |
| Location Availability | Ukur persentase pengujian ketika lokasi berhasil diterima. |
| Notification Success Rate | Hitung keberhasilan pengiriman notifikasi pada skenario yang valid. |
| End-to-End Success | Hitung skenario penuh yang berhasil dari sensor hingga trusted contact. |
| Usability | Observasi keberhasilan pengguna menyelesaikan setup tanpa bantuan teknis. |

---

## 27. Risks and Mitigation

| Risk | Impact | Mitigation |
|---|---|---|
| Gyro tidak langsung mengukur speed linear | Konsep pengukuran tidak akurat | Gunakan sensor fusion/GPS/encoder dan jelaskan fungsi tiap sensor. |
| False positive accident | Kontak menerima alarm palsu | Multi-parameter detection + confirmation window. |
| False negative accident | Alarm tidak terkirim | Pengujian banyak skenario dan dokumentasikan batasan. |
| GPS error | Lokasi tidak tepat | Gunakan last valid location dan status accuracy. |
| Network loss | Data/notifikasi terlambat | Connection state, retry, dan buffer bila memungkinkan. |
| Sensor noise | Event salah | Calibration dan filtering. |
| Battery/power issue | Device mati | Monitoring power dan desain supply yang stabil. |
| API platform berubah | Notifikasi gagal | Abstraction layer/simulasi pada tahap prototype. |

---

## 28. MVP Definition

MVP prototipe dianggap selesai apabila perangkat dapat membaca data sensor, memperoleh lokasi, menghasilkan status kecepatan, memberikan overspeed alert, terhubung ke aplikasi, menyimpan trusted contact, menghasilkan event kecelakaan berdasarkan skenario uji, dan mengirim notifikasi darurat beserta lokasi kepada trusted contact. MVP tidak menargetkan deployment publik atau jaminan keselamatan layaknya perangkat medis/emergency service tersertifikasi.

---

## 29. Future Development

- Pengembangan model machine learning untuk klasifikasi kecelakaan berbasis dataset sensor.
- Kalibrasi sensor berdasarkan tipe kendaraan dan kondisi jalan.
- Optimasi casing, mounting, waterproofing, dan power management.
- Integrasi layanan notifikasi resmi yang sesuai dengan kebijakan platform.
- Penambahan geofencing dan analisis perilaku berkendara.
- Penambahan dashboard keluarga/organisasi dengan kontrol privasi yang jelas.
- Pengujian lapangan yang lebih luas dan evaluasi statistik performa.

---

## 30. Roadmap Prototipe

| Tahap | Output |
|---|---|
| 1. Requirement | PRD, use case, scope, acceptance criteria. |
| 2. Hardware Proof of Concept | Sensor + microcontroller membaca data. |
| 3. Firmware | Sampling, filtering, threshold, telemetry. |
| 4. Backend | API, database, event processing. |
| 5. Application | Dashboard, map, contacts, status. |
| 6. Integration | Hardware → backend → application. |
| 7. Testing | Speed, location, accident simulation, notification. |
| 8. Evaluation | Analisis hasil, limitations, dan perbaikan. |

---

## 31. Final Product Definition

Produk akhir pada tahap PKM adalah demonstrator sistem keselamatan pengendara yang menunjukkan integrasi hardware dan software secara end-to-end. Hardware dipasang pada sepeda motor untuk membaca parameter gerakan/lokasi, sedangkan software menyediakan monitoring, konfigurasi keselamatan, trusted contacts, dan emergency notification. Sistem ditujukan sebagai proof of concept yang dapat dikembangkan lebih lanjut, bukan sebagai perangkat keselamatan tersertifikasi atau pengganti layanan darurat resmi.

---

## 32. Kesimpulan

PRD ini menetapkan kebutuhan produk dari sisi pengguna, fitur, hardware, software, data, arsitektur, pengujian, keamanan, hingga batasan prototipe. Konsep utama yang dibangun adalah integrasi sensor kendaraan dengan aplikasi sehingga informasi mengenai kecepatan, lokasi, dan indikasi kondisi darurat dapat diproses dalam satu sistem. Untuk menjaga validitas teknis, pengukuran kecepatan dan deteksi kecelakaan menggunakan pendekatan sensor fusion dan harus divalidasi melalui eksperimen prototipe.