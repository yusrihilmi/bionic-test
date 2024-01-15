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

- 
