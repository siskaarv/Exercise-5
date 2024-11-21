# RTOS Exercise 5

Proyek ini bertujuan untuk mengontrol beberapa LED menggunakan mikrokontroler STM32 dengan FreeRTOS. Proyek ini memanfaatkan FreeRTOS untuk mengontrol tiga LED (Hijau, Merah, dan Biru) yang terhubung ke STM32. Dua task utama diimplementasikan, yaitu FlashGreenLedTask dan FlashRedLedTask.

## Cara Kerja

1. Task FlashGreenLedTask mengontrol LED hijau dengan pola sebagai berikut:
   - Menyalakan LED Hijau.
   - Mengakses data bersama yang melibatkan penanganan status `StartFlag`.
   - Mematikan LED Hijau.
   - Menunggu atau jeda selama 0,5 detik sebelum mengulangi siklus.

2. Task FlashRedLedTask mengontrol LED merah dengan pola sebagai berikut:
   - Menyalakan LED Merah.
   - Mengakses data bersama yang melibatkan penanganan status `StartFlag`.
   - Mematikan LED Merah.
   - Menunggu atau jeda selama 0,1 detik sebelum mengulangi siklus.

3. Akses data bersama dilakukan dengan memeriksa nilai `StartFlag`. Jika `StartFlag` diatur, maka akan diatur ulang dan LED Biru dinyalakan. Operasi ini mensimulasikan penulisan data dan menunggu selama 500 milidetik.

Pada proyek ini, FlashRedLedTask memiliki prioritas lebih tinggi dibandingkan dengan FlashGreenLedTask. Hal ini memastikan bahwa FlashRedLedTask akan selalu dijalankan terlebih dahulu oleh FreeRTOS jika kedua task dalam keadaan siap.

## Hardware
![https://drive.google.com/file/d/1hOwbhqC0BFZt6Tv_SRF9xP-DU8YvtP5a/view?usp=drive_link]()
![https://drive.google.com/file/d/1hVxPWR0SnrUj7aKJ7Qzs-cB_WDCTz6OK/view?usp=drive_link]()

## Output Proyek
1. Task FlashGreenLedTask
- LED biru dinyalakan dan LED hijau berkedip 80 kali dengan interval 50 ms per kedipan (ON/OFF).
- Setelah berkedip 80 kali, LED hijau dan LED biru dimatikan.
- Delay selama 6 detik sebelum mengulangi siklus yang sama.
2. Task FlashRedLedTask
- LED kuning dinyalakan dan LED merah berkedip 10 kali dengan interval 50 ms per kedipan (ON/OFF).
- Setelah berkedip 10 kali, LED merah dan LED kuning dimatikan.
- Delay selama 1.5 detik sebelum mengulangi siklus yang sama.

Kedua task ini berjalan secara paralel, sehingga LED hijau dan LED merah dapat berkedip bersamaan pada saat tertentu jika siklusnya tumpang tindih.
