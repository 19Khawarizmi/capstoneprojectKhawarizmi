# capstoneprojectKhawarizmi
Judul dan Deskripsi Proyek:

Judul: "Data Pasien CRUD Project"
Deskripsi: Proyek ini adalah implementasi dari aplikasi manajemen data pasien rumah sakit menggunakan Python. Aplikasi ini memungkinkan pengguna untuk melakukan operasi dasar CRUD (Create, Read, Update, Delete) pada data pasien, seperti menambahkan, melihat, memperbarui, dan menghapus data pasien.
Struktur Kode:

Kode dimulai dengan mengimpor modul datetime untuk pengelolaan tanggal.
Daftar pasien awal dibuat sebagai variabel patients dan diisi dengan data dummy.
Fungsi-fungsi dibuat untuk validasi ketersediaan kamar, validasi nomor KTP, dan untuk setiap operasi CRUD (Create, Read, Update, Delete).
Fungsi-fungsi tersebut digunakan dalam main() untuk menyediakan menu utama kepada pengguna.
Setiap fitur memiliki fungsi khusus dengan validasi dan pengulangan yang memungkinkan pengguna untuk kembali ke menu utama setelah operasi selesai.
Fitur-fitur Utama:

Tambah Pasien (tambah_pasien): Memungkinkan pengguna untuk memasukkan data pasien baru, dengan validasi ketersediaan kamar dan panjang nomor KTP.
Lihat Pasien (lihat_semua_pasien, lihat_pasien_by_kamar, lihat_rata_rata_menginap): Memberikan opsi untuk melihat semua data pasien, data pasien berdasarkan nomor kamar, dan rata-rata lama menginap pasien yang sudah keluar.
Update Pasien (update_pasien): Memungkinkan pengguna untuk memperbarui data pasien dengan validasi ketersediaan kamar dan panjang nomor KTP.
Hapus Pasien (hapus_pasien): Memungkinkan pengguna untuk menghapus data pasien.
Menu Utama:

Menu utama (main()) memberikan opsi kepada pengguna untuk memilih operasi yang ingin dilakukan.
Setelah setiap operasi selesai, pengguna diberikan pilihan untuk kembali ke menu utama atau keluar dari program.
Validasi dan Pengulangan:

Terdapat validasi untuk ketersediaan kamar, panjang nomor KTP, dan penanganan kasus-kasus khusus seperti pasien yang sudah keluar dari rumah sakit.
Pengguna diberikan opsi untuk kembali ke menu utama setelah operasi selesai untuk kenyamanan dan navigasi yang lebih baik.
Dengan penjelasan ini, pembaca dapat memahami struktur dan fungsionalitas utama dari proyek Data Pasien CRUD Project ini.
