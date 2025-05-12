# Tutorial 9
**Nama:**   Joshua Montolalu<br>
**NPM:**    2306275746<br>
**Kelas:**  Pengjut A<br>

## Modul 9
### Reflection 1
1. What is ***amqp***?
    -  AMQP adalah singkatan untuk Advanced Message Queuing Protocol, yaitu sebuah protokol untuk *message-oriented middleware*. AMQP berisi beberapa ketentuan mengenai *messaging provider* dan *client* yang salah satu tujuannya adalah menjamin bahwa implementasi yang berbeda-beda dapat saling berinteraksi dan berkomunikasi dengan aman dan konsisten. Dengan kata lain, aplikasi-aplikasi yang mengimplementasi protokol AMQP dapat saling berkomunikasi dan beroperasi, terlepas dari bahasa pemrograman yang digunakan. RabbitMQ merupakan salah satu *message broker* yang mengimplementasi protokol ini; contoh-contoh lainnya adalah Apache Qpid, Apache ActiveMQ, IBM MQ, dan lain-lain. 

2.  What does it mean? `guest:guest@localhost:5672`, what is the first `guest`, and what is the second `guest`, and what is `localhost:5672` is for?
    - `guest:guest@localhost:5672` adalah URL koneksi untuk menyambung ke RabbitMQ. `guest` pertama adalah username dari user yang ingin login, sementara `guest` kedua adalah password dari user yang ingin login. Keduanya bernilai `guest` secara default dan dapat berubah-ubah sesuai dengan user yang ingin menyambung ke RabbitMQ. `localhost:5672` adalah alamat dari instance RabbitMQ yang ingin dituju, dalam kasus ini kita ingin menyambung ke RabbitMQ yang berjalan pada komputer kita sendiri (localhost) pada port 5672.

### Reflection 2 (Simulating slow subcriber)
![Screenshot of RabbitMQ chart showing slow subscriber](SlowSubscriber.png)
- Terlihat pada graf pertama (graf di atas), terdapat lonjakan yang menunjukkan jumlah pesan yang tersimpan di dalam queue mengalami kenaikan. Ini terjadi karena *publisher* mengirim pesan lebih cepat daripada di-*consume* oleh *subscriber* (yang sengaja diberi *delay* untuk mensimulasikan *subscriber* yang lambat), sehingga pesan-pesan yang belum dapat diproses disimpan terlebih dahulu di dalam queue untuk kemudian di-*consume* oleh *subscriber* satu per satu. Saya menjalankan *publisher* sekitar 5 kali sehingga ada hampir 35 pesan yang tersimpan di dalam queue.