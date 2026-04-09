#  Penjelasan konsep array

Dalam pemrograman, Array (yang dalam bahasa Python direpresentasikan melalui objek List) berfungsi sebagai wadah atau kontainer yang mampu menyimpan sekumpulan data dalam satu variabel tunggal. Jika variabel biasa diibaratkan sebagai sebuah kotak kecil yang hanya muat satu barang, maka Array adalah sebuah lemari loker yang memiliki banyak laci bernomor. Dalam kode, Array digunakan secara dinamis melalui variabel daftarMahasiswa dan daftarNilai_Mahasiswa. Hal ini memungkinkan program untuk mengelola banyak data secara kolektif tanpa harus membuat variabel unik satu per satu untuk setiap inputan, sehingga kode menjadi lebih efisien dan jauh lebih bersih (clean code).

Konsep utama dari Array terletak pada sistem Indeks, di mana setiap elemen yang masuk akan diberikan nomor urut dimulai dari angka 0. Saat menjalankan fungsi .append(), program secara otomatis menambahkan slot baru di urutan paling belakang untuk menyimpan nama atau nilai yang baru dimasukkan. Menariknya, pada variabel daftarNilai_Mahasiswa, menerapkan konsep Array temporer; data nilai mahasiswa sebelumnya akan "direset" atau dikosongkan kembali setiap kali perulangan mahasiswa baru dimulai. Ini adalah strategi yang cerdas dalam manajemen memori karena program tidak perlu menanggung beban data yang tidak diperlukan untuk kalkulasi saat itu.

Selain sebagai tempat penyimpanan, Array dalam kode ini juga menjadi fondasi bagi operasi Agregasi dan Traversing. Fungsi-fungsi seperti max(), min(), dan sum() tidak akan bisa bekerja jika data tidak tersimpan dalam bentuk Array, karena fungsi tersebut perlu memindai seluruh "loker" nilai untuk menentukan hasil statistik. Begitu juga saat pembuatan grafik dengan matplotlib, Array berperan sebagai sumber data yang terstruktur sehingga koordinat pada sumbu grafik dapat dipetakan dengan tepat. Tanpa penggunaan Array, mustahil bagi kita untuk melakukan pengolahan data dalam jumlah banyak secara otomatis dan dinamis seperti yang ditunjukkan dalam program tersebut.
# Screenshot hasil eksekusi
![image](https://github.com/CherieHannanya/proyek-1-Struktur-Data/blob/6257cac8f9ceba1ebbbabc2899ea6f30b31bad95/Hasil%20Struktur%20data.png)
![image](https://github.com/CherieHannanya/proyek-1-Struktur-Data/blob/613e9b126335aedcd568fe0f90f2c09e1e0759eb/hasil%202%20struktur%20data.png) 

# Analisis Kompleksitas
1. Analisis Kompleksitas Waktu 
   
   Secara keseluruhan, kode saya memiliki kompleksitas O(n x k). Artinya, waktu jalan program akan meningkat seiring bertambahnya jumlah mahasiswa dikali jumlah nilai mereka.
   
   Berikut rincian per bagian:

   Loop Mahasiswa (Lapis Luar): Saya menggunakan perulangan for i in range(jumlahMahasiswa). Kalau ada 100 mahasiswa, bagian ini jalan 100 kali. Ini disebut O(n).
   '''python
   for j in range(jumlahNilaiMahasiswa):
    nilaiMahasiswa = float(input(f"  > Nilai ke-{j+1} : "))
    daftarNilai_Mahasiswa.append(nilaiMahasiswa)
   '''
   
   Loop Nilai (Lapis Dalam): Di dalam setiap mahasiswa, ada lagi perulangan for j in range(jumlahNilaiMahasiswa). Jika setiap mahasiswa punya 10 nilai, maka total input nilai yang dilakukan komputer adalah 100 \times 10 = 1000 kali. Ini yang bikin rumusnya jadi O(n x k).

   Fungsi Kalkulasi (max, min, sum): Fungsi-fungsi bawaan Python ini bekerja secara "linear". Artinya, untuk nyari nilai tertinggi, Python harus ngecek nilai dari atas sampai bawah satu per satu. Jadi kalau nilainya ada k, butuh waktu O(k).

   Filter Kelulusan (List Comprehension): Bagian [n for n in daftarNilai_Mahasiswa if n >= 70] juga sama. Python harus ngintip setiap nilai satu per satu buat nentuin siapa yang lulus. Ini juga O(k).
   
3. Analisis Kompleksitas Ruang (Seberapa Makan Memori?)Kompleksitas ruangnya adalah O(n + k). Artinya, penggunaan RAM cukup hemat dan tidak "meledak".
  
   Daftar Mahasiswa: menyimpan semua nama mahasiswa di daftarMahasiswa. Jadi makin banyak orang, makin besar list-nya. Ini O(n).

   Daftar Nilai: list daftarNilai_Mahasiswa dibuat ulang setiap kali ganti mahasiswa. Jadi RAM cuma nampung nilai satu orang saja di satu waktu, terus dihapus dan diganti nilai orang berikutnya. Makanya cuma butuh O(k).

4. Catatan Penting: Hambatan "Blocking"
   Hal yang perlu di perhatikan yaitu: fungsi plt.show().

   Di dalam kode, plt.show() ditaruh di dalam perulangan mahasiswa. Secara teknis, ini bersifat blocking. Artinya, program bakal "berhenti total" dan nggak akan lanjut ke mahasiswa berikutnya sebelum menutup jendela grafiknya.

   Jadi, meskipun komputernya secepat kilat, performa aslinya bakal lambat karena harus menunggu "kecepatan tangan" manusia buat nge-klik tombol close grafik satu per satu.

# Refleksi pembelajaran
Melalui implementasi kode ini, pembelajaran utama yang didapatkan adalah bagaimana Struktur Data Linear (Array/List) menjadi tulang punggung dalam pengolahan informasi yang dinamis. Program ini membuktikan bahwa Array bukan sekadar deretan angka, melainkan sebuah kontainer cerdas yang memungkinkan dalam mengelompokkan data yang berbeda jenis (seperti nama mahasiswa dan nilai numerik) secara terorganisir. Penggunaan metode .append() menunjukkan fleksibilitas pemrograman modern dalam menangani ukuran data yang tidak pasti di awal, yang sangat relevan dengan skenario dunia nyata di mana jumlah mahasiswa atau nilai sering kali berubah-ubah.

Dari sisi logika komputasi, penggunaan Nested Loop (perulangan bersarang) memberikan pemahaman konkret mengenai hirarki proses. Dari ini dapat belajar bahwa sebuah sistem besar sering kali terdiri dari sub-proses yang saling bergantung; proses pengolahan kelas (loop luar) tidak akan tuntas tanpa menyelesaikan detail individu (loop dalam). Refleksi penting di sini adalah pemahaman tentang titik kritis performa. Kita menyadari bahwa setiap baris kode yang kita tulis, seperti fungsi max() atau sum(), memiliki biaya waktu yang berbanding lurus dengan jumlah data. Hal ini melatih insting kita untuk tidak hanya menulis kode yang "berhasil jalan," tetapi juga mulai mempertimbangkan seberapa efisien kode tersebut jika datanya meledak menjadi ribuan entri.

Selain teknis algoritma, aspek visualisasi menggunakan matplotlib memberikan pelajaran berharga tentang User Experience (UX) dalam pemrograman. Dari semua ini dapat belajar bahwa data mentah dalam bentuk angka sering kali sulit dicerna, dan grafik adalah jembatan komunikasi yang efektif antara mesin dan manusia. Namun, ada pelajaran kritis mengenai fungsi "blocking" dari plt.show(). Hal ini menyadarkan  bahwa alur eksekusi program harus selaras dengan interaksi pengguna, terkadang kode yang paling benar secara logika tetap membutuhkan penyesuaian strategi (seperti memisahkan tampilan grafik) agar tidak menghambat alur kerja sistem secara keseluruhan. Secara keseluruhan, proyek kecil ini merupakan jembatan antara teori struktur data dasar dengan aplikasi analisis data praktis.
