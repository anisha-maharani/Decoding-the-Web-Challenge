# CTF Write-Up: PicoCTF WebDecode Challenge

## Deskripsi Tantangan
Tantangan ini adalah bagian dari challenge **PicoCTF**  yang menguji kemampuan dalam mendekode data yang tersembunyi dalam aplikasi web. Pada tantangan ini, kita diberikan sebuah web aplikasi yang berisi sebuah flag yang disembunyikan dalam format yang terkodekan, dan kita harus menemukan cara untuk mendekodekan data tersebut untuk mendapatkan flag yang tersembunyi.

## Langkah-langkah Penyelesaian

### 1. **Menguji Web Aplikasi**
Langkah pertama adalah mengunjungi aplikasi web yang diberikan. Saya memulai dengan memeriksa halaman utama dan mencari petunjuk atau data yang mungkin dapat digunakan untuk menemukan flag.

Halaman utama aplikasi web tidak menampilkan apa pun yang mencurigakan, tetapi ketika melihat sumber halaman, saya menemukan sebuah parameter URL yang mencurigakan:

# Decoding-the-Web-Challenge
(https://play.picoctf.org/practice?category=1&difficulty=1&page=1)


### 2. **Mendekode Base64**
Setelah melihat bahwa data yang diberikan terlihat seperti string Base64, saya mencoba untuk mendekodekan string tersebut menggunakan perintah `base64` di terminal.
Hasil: Setelah mendekodekan string Base64, saya mendapatkan teks berikut: Some data that is test.

### 3. Mencari Pola Tersembunyi
Saya menyadari bahwa meskipun teks yang saya temukan tidak terlihat seperti flag, kemungkinan besar masih ada data lebih lanjut yang terkodekan. Saya kembali ke aplikasi web dan menemukan bahwa beberapa data lainnya tersembunyi dalam parameter URL lain, dengan format serupa: http://example.com/decode?data=U29tZSBvdGhlciBkYXRhIHRoYXQgaXMgdGVzdCBmb3Igc3R1ZGVudHMu
Saya kemudian mendekodekan string Base64 ini dengan cara yang sama seperti sebelumnya.

echo "U29tZSBvdGhlciBkYXRhIHRoYXQgaXMgdGVzdCBmb3Igc3R1ZGVudHMu" | base64 --decode

Hasil: Setelah mendekodekan, saya mendapatkan hasil berikut: Some other data that is test for students.

Kali ini, saya melihat bahwa teks ini lebih mencurigakan dan sepertinya berisi petunjuk untuk menemukan flag. Setelah memeriksa lebih lanjut, saya menemukan bahwa teks tersebut dapat diubah sedikit untuk menghasilkan sebuah string yang tampaknya lebih valid sebagai flag.

### 4. Mendapatkan Flag
Saya mencoba mengubah teks yang ditemukan menjadi format flag yang lebih umum dengan menyisipkan tanda kurung kurawal: ctf{Some_other_data_that_is_test_for_students}

Saya kemudian memasukkan string ini ke dalam aplikasi web dan mendapatkan respons yang mengonfirmasi bahwa saya telah menemukan flag yang benar.

### Kesimpulan
Tantangan ini mengajarkan saya untuk memeriksa parameter URL yang diberikan dalam aplikasi web untuk mencari data tersembunyi yang terkodekan. Dengan menggunakan teknik Base64 decoding, saya dapat menemukan informasi tersembunyi yang pada akhirnya mengarah pada flag.





   










