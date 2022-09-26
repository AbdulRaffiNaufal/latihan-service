# Membuat Microservice Sederhana
## Latihan Service
#### Langkah 1:
Buat proyek web menggunakan link berikut [start.spring.io](https://start.spring.io/), kemudian pilih Maven Project, Bahasanya Java. Pilih Spring Boot versi 2.6.6. Lalu buat project metadata group dengan nama : **com.naufal**, Artifact dan name dengan nama : **latihan-service**, serta package name dengan nama : **com.naufal.latihanservice**. Disini saya pakai jdk versi 18 dan apache netbeans versi 15. Kemudian tambahkan Dependencies **Spring Web**.kemudian Generate dan extrack dari zip menjadi file kemudian import ke dalam apache netbeans.
#### Langkah 2:
Buka proyek di IDE Anda dan cari file **LatihanServiceApplication.java** di **Source Packages** pada folder **com.naufal.latihan.service**. Sekarang ubah isi file dengan menambahkan metode tambahan dan anotasi yang ditunjukkan pada kode di bawah ini. Anda dapat menyalin dan menempelkan kode atau cukup mengetiknya.
#### Langkah 3:
```java
package com.naufal.latihan.service;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@SpringBootApplication
@RestController
public class LatihanServiceApplication {
    public static void main(String[] args) {
        SpringApplication.run(LatihanServiceApplication.class, args);
    }
    @GetMapping("/hello")
    public String hello(@RequestParam(value = "name", defaultValue = "world") String name) {
        return String.format("Hello %s!", name);
    }
}
```
Metode ``hello()`` yang di tambahkan dirancang untuk mengambil parameter String yang disebut ``name``, dan kemudian menggabungkan parameter ini dengan kata ``"Hello"``dalam kode. Ini berarti bahwa jika Anda menyetel nama Anda ke ``“World”`` dalam permintaan, responsnya adalah ``“Hello World”``.

Anotasi `@RestController` memberi tahu Spring bahwa kode ini menjelaskan titik akhir yang harus tersedia melalui web. `@GetMapping(“/hello”)` memberi tahu Spring untuk menggunakan method `hello()` untuk menjawab permintaan yang dikirim ke alamat  `http://localhost:8010/hello`. Akhirnya, `@RequestParamSpring` memberi tahu Spring untuk mengharapkan nilai `name` dalam permintaan, tetapi jika tidak ada, itu akan menggunakan kata "Dunia" secara default.
#### Langkah 3:
Run file **LatihanServiceApplication.java**.

![Screenshot 2022-09-26 221415](https://user-images.githubusercontent.com/113502265/192315029-28ec5430-8a1a-4ab4-8969-226d0bed08dc.png)

Beberapa baris terakhir di sini memberi tahu kami bahwa Spring telah dimulai. Server Apache Tomcat tertanam pada Spring Boot bertindak sebagai server web dan mendengarkan permintaan pada `localhost` port `8010`. Buka browser Anda dan di bilah alamat di bagian atas enter `http://localhost:8010/hello`. Anda harus mendapatkan respons ramah yang bagus seperti ini:

![Screenshot 2022-09-26 222057](https://user-images.githubusercontent.com/113502265/192316990-fed70b74-5f0d-4052-b878-b3a5bea30467.png)
