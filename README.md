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
![RTOS_Exercise 5](https://github.com/user-attachments/assets/dd364f0a-ee93-4936-a21f-9596993b4f7c)
![RTOS_Exercise 5](https://github.com/user-attachments/assets/7eb56810-4198-4df8-9887-998e2bb24fa1)


## Output Proyek
* LED Merah akan menyala dan mati dengan cepat setiap 100 milidetik.
* LED Hijau akan menyala dan mati lebih lambat setiap 500 milidetik.
* LED Biru akan menyala selama 500 milidetik ketika AccessSharedData diakses oleh task dan startFlag bernilai 0. Hal ini akan terjadi sebagai indikasi adanya akses ke data bersama yang berpotensi terjadi interferensi.
Karena FlashRedLedTask memiliki prioritas lebih tinggi, kemungkinan LED Merah akan lebih sering terlihat aktif dibandingkan dengan LED Hijau, terutama ketika terjadi konten bersamaan.
