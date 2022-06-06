# MachineLearning

## 1. Abstrak
Menemukan buku bacaan yang sesuai dengan selera dan kesukaan kadang sangat menyulitkan. Kita bisa mencari referensi di internet, tetapi pencarian pada internet sangatlah luas sehingga membuat kita malah semakin bingung dalam menemukan buku yang kita inginkan. Maka dari itu, perlu adanya suatu sistem dalam bentuk aplikasi rekomendasi buku yang dapat mengatasi masalah tersebut. Melalui aplikasi yang dikembangkan ini juga akan diidentifikasi faktor-faktor yang memengaruhi rekomendasi buku untuk memenuhi dan menyesuaikan apa yang coba ditemukan oleh pengguna aplikasi.

## 2. Pendahuluan
Sistem rekomendasi adalah suatu sistem yang menyajikan, menyediakan, atau merekomendasikan item-item yang dibutuhkan oleh pengguna untuk membuat suatu keputusan atau untuk mencari referensi. Pada proyek ini, dibuat sistem rekomendasi untuk menyediakan judul ataupun jenis buku yang sesuai dengan kebutuhan dan keinginan pengguna. Dalam membuat sistem rekomendasi ini digunakan 2 teknik, yaitu :
- Content-based Filtering : filtering yang menggunakan kesamaan antar item untuk merekomendasikan item yang memiliki kesamaan dengan apa yang disukai pengguna. Contohnya jika pengguna A menonton dua video kucing lucu, maka sistem dapat merekomendasikan video hewan lucu kepada pengguna tersebut.
- Collaborative Filtering : filtering yang menggunakan kesamaan antara kueri dan item secara bersamaan untuk memberikan rekomendasi. Contohnya jika pengguna A memiliki kesamaan dengan pengguna B, dan pengguna B menyukai video 1, maka sistem dapat merekomendasikan video 1 kepada pengguna A (walaupun pengguna A belum pernah melihat video yang mirip dengan video 1).

## 2. Data
Terdapat 2 dataset yang digunakan yang diambil dari referensi Kaggle, yaitu :
### a. book_dataset 
Pada dataset book_dataset terdapat 1536 data dengan 16 kolom yang digunakan, yaitu :
- bookTitle   : berisi judul buku yang digunakan sebagai dataset
- bookRating  : berisi peringkat buku, dimana nilai yang lebih tinggi menunjukkan buku tersebut memiliki apresiasi yang lebih tinggi
- ISBN        : berisi nilai ISBN (International Standard Book Number), yaitu "pengindentikasian unik" untuk buku-buku yang digunakan secara komersial
- bookAuthor	: berisi nama penulis buku sesuai dengan masing-masing buku
- yearOfPublication : berisi tahun publikasi buku sesuai dengan masing-masing buku
- Publisher   : berisi nama penerbit buku sesuai dengan masing-masing buku
- url         : berisi link url menuju informasi buku
- bookImage   : berisi link url menuju gambar cover buku
- bookDesc	  : berisi informasi singkat mengenai buku 
- ratingCount : berisi nilai berapa kali buku diberi peringkat/rate
- bookPages   : berisi jumlah halaman buku
- bookGenres	: berisi semua jenis genre yang sesuai dengan masing-masing buku
- bookGenre1	: berisi jenis genre yang pertama paling relevan sesuai dengan masing-masing buku
- bookGenre2	: berisi jenis genre yang kedua paling relevan sesuai dengan masing-masing buku
- bookGenre3	: berisi jenis genre yang ketiga paling relevan sesuai dengan masing-masing buku
- books       : berisi nilai encode buku sesuai dengan urutan data paling atas
### b. rating_dataset
Pada dataset book_dataset terdapat 21831 data dengan 6 kolom yang digunakan, yaitu :
- userId      : berisi nilai Id pengguna
- ISBN	      : berisi nilai ISBN (International Standard Book Number), yaitu "pengindentikasian unik" untuk buku-buku yang digunakan secara komersial
- bookRating	: berisi peringkat buku, dimana nilai yang lebih tinggi menunjukkan buku tersebut memiliki apresiasi yang lebih tinggi
- bookTitle   : berisi judul buku yang digunakan sebagai dataset
- user	      : berisi nilai Id pengguna yang telah diencode
- books       : berisi nilai ISBN yang telah diencode

## 3. Data Preparation
### a. Content-based Filtering
Pada Content-based Filtering, menggunakan library TF-IDF dan cosine similarity untuk mengubah data menjadi angka berupa matriks. 
### b. Collaborative Filtering
Pada Collaborative Filtering, sebelum data digunakan untuk membuat model, data harus terlebih dulu dibagi menjadi data latih dan data uji. Digunakan rasio 80:20 untuk data latih dan data uji. 

## 4. Modelling
### a. Content-based Filtering
Pada Content-based Filtering, dibuat fungsi untuk rekomendasi buku yang sama sesuai hasil dari TF-IDF dan cosine similarity yang telah dibuat. Hasil yang akan ditampilkan berupa 10 judul buku yang hampir sama dengan judul buku yang didefinisikan.
### b. Collaborative Filtering
Pada Collaborative Filtering, dibuat fungsi menggunakan tf.keras.Model. Hasil yang akan ditampilkan berupa 10 judul buku yang direkomendasikan

## 5. Evaluasi
### Collaborative Filtering
Evaluasi yang digunakan pada Collaborative Filtering adalah RMSE (Root Mean Squared Error). RMSE bekerja dengan mengukur perbedaan nilai dari prediksi sebuah model sebagai estimasi atas nilai yang diobservasi. Secara umum, persamaannya adalah : 
![image](https://user-images.githubusercontent.com/106024364/172191893-7ede6c8c-3571-442d-bedb-aba4b9094f01.png)
Hasil yang didapatkan : 
![image](https://user-images.githubusercontent.com/106024364/172192087-52f67eb3-e209-44c5-82f8-b224635db476.png)

## 6. Deployment 
Model disimpan dengan mengguakan pickle dan dideploy menggunakan Flask sebagai API.



