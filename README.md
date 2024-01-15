C. SQL Test

Result_1
SELECT item
FROM asset
WHERE item IN ('notebook', 'bag', 'mobile phone');

Result_2
SELECT user_id, GROUP_CONCAT(DISTINCT item ORDER BY item) AS asset
FROM asset
WHERE item IN ('notebook', 'bag', 'mobile phone')
GROUP BY user_id;

E. ERD Test

1. function generatePattern(n) {
    for (let i = 1; i <= n; i++) {
        let line = "";
        for (let j = 1; j <= i; j++) {
            line += j;
        }
        line += "**";
        for (let k = i + 1; k <= n + 3; k++) {
            line += k;
        }
        console.log(line);
    }
}

generatePattern(5);

generatePattern(4);

2. function findMaximumDifference(arr) {
    if (arr.length < 2) {
        return "Array harus memiliki setidaknya dua elemen.";
    }

    let maxDifference = arr[1] - arr[0];
    let minElement = arr[0];

    for (let i = 1; i < arr.length; i++) {
        let currentDifference = arr[i] - minElement;
        maxDifference = Math.max(maxDifference, currentDifference);
        minElement = Math.min(minElement, arr[i]);
    }

    return maxDifference;
}

const harga = [10, 7, 5, 8, 11, 9, 1];
const result = findMaximumDifference(harga);
console.log(result);

F. Penjelasan Singkat

- Cypress adalah sebuah sebuah open source yang digunakan untuk menguji suatu web secara otomatis. Dengan kata lain, Cypress bisa digunakan untuk UAT suatu website.

- Kubernetes adalah platform open source untuk mengatur kumpulan kontainer dalam suatu cluster server. Kubernetes menggunakan bahasa Go

- Objek Relational Mapping (ORM) merupakan sebuah ide atau teknik yang digunakan untuk memetakan basis data menjadi sebuah class.

- Dalam konteks ORM (Object-Relational Mapping), "class" mengacu pada representasi pemetaan objek dari struktur data dalam basis data relasional. Dalam konteks HTML, "class" adalah atribut yang digunakan untuk memberikan satu atau lebih nama kelas (class names) kepada suatu elemen HTML. Kelas ini dapat digunakan untuk memberikan gaya atau penanganan khusus melalui CSS, atau sebagai referensi dalam skrip JavaScript.

- Dalam JavaScript, "function" adalah blok kode yang dirancang untuk melakukan tugas tertentu dapat dipanggil (dijalankan) di beberapa tempat dalam program.

- DevOps merupakan budaya kerja yang meningkatkan kolaborasi antara developer dan operasional IT. Tujuannya adalah untuk mengatasi batasan-batasan antara pengembangan dan operasi, dengan menciptakan alur kerja yang lebih terintegrasi dan efisien dalam seluruh siklus pengembangan, pengujian, dan pengiriman hasil.

- Docker adalah platform kontainer yang memungkinkan pengembang untuk membuat, mengemas, dan menjalankan aplikasi dalam kontainer. Docker menyediakan alat untuk membangun dan menjalankan kontainer, serta manajemen image.

G. Architecture Application

1. Microservices Architecture
   Java spring boot, ASP.NET

   Memungkinkan pengembangan, pengujian, dan penyebaran independen bagi setiap mikro layanan, memungkinkan skala secara horizontal untuk meningkatkan performa.
   Dapat ditulis dengan berbagai bahasa pemrograman yang paling cocok untuk kebutuhan spesifiknya.

2. Serverless Architecture
   AWS, Google Cloud

   Fungsi hanya dijalankan saat dipanggil, menghilangkan kebutuhan untuk mempertahankan server yang berjalan secara terus-menerus.
   Platform serverless secara otomatis menangani skalabilitas dan manajemen sumber daya, sehingga pengembang dapat fokus pada logika aplikasi.

3. Single Page Application (SPA) Architecture
   Angular, VueJS, ReactJS

   Memungkinkan pengguna dapat mengakeses lebih cepat dan responsif dengan mengurangi kebutuhan untuk memuat ulang halaman secara penuh.
   Memungkinkan pengembangan terpusat dan pemeliharaan aplikasi, karena logika aplikasi dan tampilan dapat diimplementasikan dalam satu basis kode.
