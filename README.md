# Analisis Kompleksitas
1. Analisis Kompleksitas Waktu (Seberapa Cepat?)
   
   Secara keseluruhan, kode saya memiliki kompleksitas O(n x k). Artinya, waktu jalan program akan meningkat seiring bertambahnya jumlah mahasiswa dikali jumlah nilai mereka.
   
   Berikut rincian per bagian:

   Loop Mahasiswa (Lapis Luar): Saya menggunakan perulangan for i in range(jumlahMahasiswa). Kalau ada 100 mahasiswa, bagian ini jalan 100 kali. Ini disebut O(n).
   
   Loop Nilai (Lapis Dalam): Di dalam setiap mahasiswa, ada lagi perulangan for j in range(jumlahNilaiMahasiswa). Jika setiap mahasiswa punya 10 nilai, maka total input nilai yang dilakukan komputer adalah $100 \times 10 = 1000$ kali. Ini yang bikin rumusnya jadi O(n x k).

   Fungsi Kalkulasi (max, min, sum): Fungsi-fungsi bawaan Python ini bekerja secara "linear". Artinya, untuk nyari nilai tertinggi, Python harus ngecek nilai dari atas sampai bawah satu per satu. Jadi kalau nilainya ada k, butuh waktu O(k).

   Filter Kelulusan (List Comprehension): Bagian [n for n in daftarNilai_Mahasiswa if n >= 70] juga sama. Python harus ngintip setiap nilai satu per satu buat nentuin siapa yang lulus. Ini juga O(k).
   
2. Analisis Kompleksitas Ruang (Seberapa Makan Memori?)Kompleksitas ruangnya adalah O(n + k). Artinya, penggunaan RAM cukup hemat dan tidak "meledak".
  
   Daftar Mahasiswa: menyimpan semua nama mahasiswa di daftarMahasiswa. Jadi makin banyak orang, makin besar list-nya. Ini O(n).

   Daftar Nilai: list daftarNilai_Mahasiswa dibuat ulang setiap kali ganti mahasiswa. Jadi RAM cuma nampung nilai satu orang saja di satu waktu, terus dihapus dan diganti nilai orang berikutnya. Makanya cuma butuh O(k).

3. Catatan Penting: Hambatan "Blocking"
Hal yang perlu di perhatikan yaitu: fungsi plt.show().

Di dalam kode, plt.show() ditaruh di dalam perulangan mahasiswa. Secara teknis, ini bersifat blocking. Artinya, program bakal "berhenti total" dan nggak akan lanjut ke mahasiswa berikutnya sebelum menutup jendela grafiknya.

Jadi, meskipun komputernya secepat kilat, performa aslinya bakal lambat karena harus menunggu "kecepatan tangan" manusia buat nge-klik tombol close grafik satu per satu.

# Screenshot hasil eksekusi

#  Analisis Kompleksitas

# Refleksi pembelajaran
