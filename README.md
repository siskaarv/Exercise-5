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
* LED hijau akan menyala selama 500 ms, kemudian mati selama 500 ms secara berulang-ulang.
Selama LED hijau menyala atau mati, fungsi AccessSharedData() dipanggil untuk mengecek atau mengubah status dari startFlag.
* LED merah akan menyala selama 100 ms, kemudian mati selama 100 ms secara berulang-ulang.
Seperti LED hijau, fungsi AccessSharedData() juga dipanggil di setiap siklus hidup LED merah.
* LED biru akan menyala untuk menunjukkan adanya interferensi (akses data bersama) di dalam fungsi AccessSharedData().
LED biru akan menyala selama 500 ms, menunjukkan bahwa startFlag sedang diubah atau diperiksa.

Karena FlashRedLedTask memiliki prioritas lebih tinggi, kemungkinan LED Merah akan lebih sering terlihat aktif dibandingkan dengan LED Hijau, terutama ketika terjadi konten bersamaan.
