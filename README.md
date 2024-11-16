# Exercise-5

Proyek ini bertujuan untuk mengontrol beberapa LED menggunakan mikrokontroler STM32 dengan FreeRTOS. Proyek ini memanfaatkan FreeRTOS untuk mengontrol tiga LED (Hijau, Merah, dan Biru) yang terhubung ke STM32. Dua task utama diimplementasikan, yaitu FlashGreenLedTask dan FlashRedLedTask.

## Cara Kerja

1. Task 'FlashGreenLedTask' mengontrol LED hijau dengan pola sebagai berikut:
   - Menyalakan LED Hijau.
   - Mengakses data bersama yang melibatkan penanganan status `StartFlag`.
   - Mematikan LED Hijau.
   - Menunggu atau jeda selama 0,5 detik sebelum mengulangi siklus.

2. Task 'FlashRedLedTask' mengontrol LED merah dengan pola sebagai berikut:
   - Menyalakan LED Merah.
   - Mengakses data bersama yang melibatkan penanganan status `StartFlag`.
   - Mematikan LED Merah.
   - Menunggu atau jeda selama 0,1 detik sebelum mengulangi siklus.

3. Akses data bersama dilakukan dengan memeriksa nilai `StartFlag`. Jika `StartFlag` diatur, maka akan diatur ulang dan LED Biru dinyalakan. Operasi ini mensimulasikan penulisan data dan menunggu selama 500 milidetik.

Pada proyek ini, FlashRedLedTask memiliki prioritas lebih tinggi dibandingkan dengan FlashGreenLedTask. Hal ini memastikan bahwa FlashRedLedTask akan selalu dijalankan terlebih dahulu oleh FreeRTOS jika kedua task dalam keadaan siap.

## Hardware

