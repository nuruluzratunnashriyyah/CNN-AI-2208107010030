# Review CNN

Convolutional Neural Networks (CNN) adalah teknik dalam deep learning yang digunakan untuk pengenalan visual, seperti mengenali objek dalam gambar atau video.

### Aplikasi CNN antara lain:
- Facebook: Otomatis menandai wajah teman atau keluarga.
- CCTV: Mendeteksi wajah secara online dan real-time.

Komputer belajar mengenali objek dengan proses training dan pengujian menggunakan teknik CNN. Tingkat akurasi CNN sangat bergantung pada kualitas dataset yang digunakan. Sebagai contoh, untuk melatih CNN mengenali gambar kucing, dataset harus berisi gambar kucing yang jelas dan relevan.

### Representasi pixel:
- Gambar monokrom dikonversi menjadi array 2D dengan nilai 0-255 (0 = putih, 255 = hitam).
- Gambar berwarna direpresentasikan sebagai array 3D dengan tiga komponen warna: Red, Green, Blue (RGB), di mana setiap pixel memiliki nilai intensitas 0-255 untuk masing-masing warna.

### Hasil output dari CNN dapat berupa:
- Prediksi probabilitas yang diurutkan.
- Jawaban langsung tentang objek.
- Jawaban biner (ya/tidak).

## Berikut adalah tahapan Convolutional Neural Network:
![image](https://github.com/user-attachments/assets/1d31828d-9e9c-470b-ae5d-754e13a7491d)

## 1. Convolution
Proses convolution adalah langkah awal dalam CNN yang mengubah gambar menjadi unit pixel menggunakan matriks yang disebut feature detector (juga dikenal sebagai kernel atau filter).

### Proses:
- Gambar awal, misalnya berukuran 7x7, dikonversi dengan feature detector berukuran 3x3 untuk menghasilkan feature map berukuran lebih kecil (5x5).
- Setiap elemen pixel pada gambar dikalikan dengan elemen dalam feature detector, lalu dijumlahkan.
- Feature map merepresentasikan seberapa besar kesamaan gambar dengan feature detector; semakin tinggi nilainya, semakin sesuai fitur tersebut.

### Fungsi ReLU (Rectified Linear Unit):
- Setelah convolution, ReLU digunakan untuk mengurangi linearitas dengan menghilangkan nilai negatif dari feature map, membuat data lebih mudah dioptimalkan.

![image](https://github.com/user-attachments/assets/ce7c333a-0a50-4e95-8623-b65242d13d61)
![image](https://github.com/user-attachments/assets/20441b05-b339-4ba9-8e62-125eb82b9e90)
![image](https://github.com/user-attachments/assets/12d72a6f-0498-4029-bc5a-e2835c141095)

## 2. Max Pooling
Pooling bertujuan mempertahankan fitur penting sambil mengurangi sensitivitas terhadap perubahan pada gambar.

### Proses:
- Dari kelompok pixel (misalnya, ukuran 2x2), hanya nilai maksimum yang dipilih untuk dimasukkan ke dalam layer baru.
- Pooling mengurangi ukuran feature map hingga 75% dengan menggeser pixel sebanyak 2 kolom atau baris untuk menghindari redundansi data.

### Manfaat:
- Menangkap fitur utama sambil mempertahankan fleksibilitas terhadap variasi posisi, pencahayaan, dan ukuran objek.
- Mempercepat proses komputasi dengan mengurangi jumlah data.

Contoh: Dalam gambar kucing dengan berbagai posisi, max pooling membantu mengenali bahwa semua gambar tersebut adalah kucing, karena hanya fitur penting yang dipertahankan.

![image](https://github.com/user-attachments/assets/84b0f870-5285-4982-ae63-e15a3dcb6834)
![image](https://github.com/user-attachments/assets/7234774d-2420-4642-99ff-a6cf6bb8c886)
![image](https://github.com/user-attachments/assets/dbc3b276-a0e8-4c32-beff-1edf09cdfb2c)
![image](https://github.com/user-attachments/assets/b6f92ebf-189f-4247-a937-ae7235eeb80c)
![image](https://github.com/user-attachments/assets/210c6997-96ca-4569-b648-9fc3a5b745ae)

## 3. Flattening
Proses flattening mengubah matriks dari pooling layer menjadi vektor satu dimensi.

### Proses:
- Semua baris dari pooling layer digabung menjadi satu kolom.

Contoh: Matriks ![image](https://github.com/user-attachments/assets/b86f6242-f627-4b07-ae76-da1cb91e4c25) diubah menjadi vektor ![image](https://github.com/user-attachments/assets/4573cd35-d9a1-410e-9854-51cf499844e8)

### Tujuan:
Hasil flattening menjadi input untuk Artificial Neural Networks (ANN) di tahap selanjutnya.

![image](https://github.com/user-attachments/assets/3d4a9ec2-10d9-4074-ac68-9c037bca2536)

## 4. Full Connection
Pada tahap ini, hasil flattening diproses dalam jaringan ANN yang terdiri dari input layer, hidden layer, dan output layer.

### Proses:
- Setiap node di ANN terhubung dengan semua node di layer sebelumnya dan berikutnya.
- Output layer berisi node sebanyak jumlah kategori yang akan diprediksi. Misalnya, jika terdapat dua kategori (kucing dan anjing), maka output layer memiliki dua node.

### Output:
- Hasil prediksi berupa probabilitas untuk setiap kategori. Misalnya, gambar diprediksi sebagai kucing dengan probabilitas 0.87 dan anjing 0.2.
- Softmax digunakan untuk memastikan total probabilitas adalah 1.

![image](https://github.com/user-attachments/assets/b5b66a95-d0ad-491b-91c6-2702a0bda480)
