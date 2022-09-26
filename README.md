# Membuat Layanan Mikroservice Sederhana
## Download Maven Projek Menggunakan Spring
#### Langkah 1:
Buat proyek Maven menggunakan Spring Initializr https://start.spring.io/
#### Langkah 2:
Pilih Spring Boot versi **2.2.0 M6** atau versi yang lebih tinggi. Jangan memilih versi snapshot. Disini saya mengunakan versi **2.6.11**.
#### Langkah 3:
Berikan nama **Grup** . Dalam kasus saya **com.afifpermana**
#### Langkah 4:
Berikan **Artifact id**. Disini saya membuat **latihan-service**
#### Langkah 5:
Pilih Java sesuai dengan yang dipakai pada komputer.
#### Langkah 6:
Tambahkan dependensi berikut: **Spring Web**.

![gambar](https://drive.google.com/uc?export=view&id=1e-GesQK8KruRqm_aVksaM23RnABZXH8Q)
#### Langkah 7:
Klik tombol **Generate the project** . File zip akan diunduh, ekstrak ke dalam hard disk.
#### Langkah 8:
Open projek yang telah di ekstrak tadi di **Acapche NetBeans**
#### Langkah 9:
Klik kanan di projek **latihan-service** pilih *Build with Dependencies*. Tunggu proses Build. 


## Projek Spring Boot baru
#### Langkah 1: Mulai proyek Spring Boot baru
Menggunakan [start.spring.io](https://start.spring.io/) untuk membuat proyek "web". Dalam dialog "Dependencies" cari dan tambahkan ketergantungan "web" seperti yang ditunjukkan pada tangkapan layar. Tekan tombol "Generate", unduh zip, dan buka kemasannya ke dalam folder di komputer Anda.
![gambar1](https://spring.io/images/quick-img-1-12bfde9c5c280b1940d85dee3d81772d.png)
Proyek yang dibuat oleh [start.spring.io](https://start.spring.io/) berisi Spring Boot,framework yang membuat Spring siap bekerja di dalam aplikasi Anda, tetapi tanpa banyak kode atau konfigurasi yang diperlukan. Spring Boot adalah cara tercepat dan terpopuler untuk memulai proyek Spring.
#### Langkah 2: Tambahkan kode Anda
Buka proyek di IDE Anda dan cari file **LatihanServiceApplication.java** di **Source Packages** pada folder **com.afifpermana.latihanservice**. Sekarang ubah isi file dengan menambahkan metode tambahan dan anotasi yang ditunjukkan pada kode di bawah ini. Anda dapat menyalin dan menempelkan kode atau cukup mengetiknya.
```java
package com.afifpermana.latihan2service;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@SpringBootApplication
@RestController
public class Latihan2ServiceApplication {

    public static void main(String[] args) {
        SpringApplication.run(LatihanServiceApplication.class, args);
    }

    @GetMapping("/hello")
    public String hello(@RequestParam(value = "name", defaultValue = "Latihan 2") String name) {
        return String.format("Hello %s!", name);
    }

}
````
Metode `hello()` yang di tambahkan dirancang untuk mengambil parameter String yang disebut `name`, dan kemudian menggabungkan parameter ini dengan kata `"Hello"`dalam kode. Ini berarti bahwa jika Anda menyetel nama Anda ke `“World”` dalam permintaan, responsnya adalah `“Hello World”`.


Anotasi `@RestController` memberi tahu Spring bahwa kode ini menjelaskan titik akhir yang harus tersedia melalui web. `@GetMapping(“/hello”)` memberi tahu Spring untuk menggunakan method `hello()` untuk menjawab permintaan yang dikirim ke alamat  `http://localhost:8080/hello`. Akhirnya, `@RequestParamSpring` memberi tahu Spring untuk mengharapkan nilai `name` dalam permintaan, tetapi jika tidak ada, itu akan menggunakan kata "Dunia" secara default.
#### Langkah 3: Cara menukar port
Pada projek kita, pergi ke **Other Sources** >> **src/main/resources** >> **default package** >> **application.properties**. Lalu buat `server.port= *nomorPort*` pada application.packages agar tidak terjadi bentrok antar port.

![gambar](https://drive.google.com/uc?export=view&id=1UM2_CzmblZs_8gpz9iq4nj4Vl7zLr92J)

#### Langkah 4: Cobalah !
Run file **LatihanService2Application.java**. 

![gambar](https://drive.google.com/uc?export=view&id=13uL9KrAbIxVXwgXNSbDmvkd3x1lZDyTX)

Beberapa baris terakhir di sini memberi tahu kami bahwa Spring telah dimulai. Server Apache Tomcat tertanam pada Spring Boot bertindak sebagai server web dan mendengarkan permintaan pada `localhost` port `8080`. Buka browser Anda dan di bilah alamat di bagian atas enter `http://localhost:8080/halo`. Anda harus mendapatkan respons ramah yang bagus seperti ini:

![gambar](https://drive.google.com/uc?export=view&id=1spLch48tRqsYzVVANu0JAHqb7LHY2RV1)
