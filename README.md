# capstoneprojectKhawarizmi

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

from datetime import datetime

# Collection data types
      patients = []

# Data dummy
      dummy_data = [
          {"nama": "Muhammad Raihan", "usia": 30, "alamat": "Jl. Merdeka 1", "diagnosis": "Flu", "tanggal_masuk": "01/01/2024", "nomor_ktp": "1234567890", "kamar": "VIP 1", "tanggal_keluar": None},
          {"nama": "Fauzan Fadilah", "usia": 25, "alamat": "Jl. Merdeka 2", "diagnosis": "Demam", "tanggal_masuk": "02/01/2024", "nomor_ktp": "0987654321", "kamar": "VIP 2", "tanggal_keluar": None},
          {"nama": "Bimo Aryono", "usia": 45, "alamat": "Jl. Merdeka 3", "diagnosis": "Malaria", "tanggal_masuk": "03/01/2024", "nomor_ktp": "1122334455", "kamar": "VIP 3", "tanggal_keluar": None},
          {"nama": "Ray Rajendra", "usia": 35, "alamat": "Jl. Merdeka 4", "diagnosis": "DBD", "tanggal_masuk": "04/01/2024", "nomor_ktp": "2233445566", "kamar": "VIP 4", "tanggal_keluar": None},
          {"nama": "Butol", "usia": 50, "alamat": "Jl. Merdeka 5", "diagnosis": "Pneumonia", "tanggal_masuk": "05/01/2024", "nomor_ktp": "3344556677", "kamar": "VIP 5", "tanggal_keluar": None},
          {"nama": "Afif Abdurah", "usia": 28, "alamat": "Jl. Kemerdekaan 1", "diagnosis": "Tifus", "tanggal_masuk": "10/12/2023", "nomor_ktp": "4455667788", "kamar": "R1A", "tanggal_keluar": "15/12/2023"},
          {"nama": "Khawarizmi", "usia": 40, "alamat": "Jl. Kemerdekaan 2", "diagnosis": "Hepatitis", "tanggal_masuk": "11/12/2023", "nomor_ktp": "5566778899", "kamar": "R1B", "tanggal_keluar": "16/12/2023"},
          {"nama": "Hilman Mauanal", "usia": 33, "alamat": "Jl. Kemerdekaan 3", "diagnosis": "Apendisitis", "tanggal_masuk": "12/12/2023", "nomor_ktp": "6677889900", "kamar": "R2A", "tanggal_keluar": "17/12/2023"},
          {"nama": "Adjie Petir", "usia": 55, "alamat": "Jl. Kemerdekaan 4", "diagnosis": "Bronkitis", "tanggal_masuk": "13/12/2023", "nomor_ktp": "7788990011", "kamar": "R2B", "tanggal_keluar": "18/12/2023"},
          {"nama": "Aril Asker", "usia": 60, "alamat": "Jl. Kemerdekaan 5", "diagnosis": "Hipertensi", "tanggal_masuk": "14/12/2023", "nomor_ktp": "8899001122", "kamar": "R3A", "tanggal_keluar": "19/12/2023"}
      ]

patients.extend(dummy_data)

# Fungsi cek ketersediaan kamar
      def cek_kamar_tersedia(kamar):
          for patient in patients:
              if patient["kamar"] == kamar and patient["tanggal_keluar"] is None:
                  return False
          return True

# Fungsi validasi nomor KTP
      def validasi_nomor_ktp(nomor_ktp):
          return len(nomor_ktp) == 10 and nomor_ktp.isdigit()

# Create
      def tambah_pasien():
          while True:
              nama = input("Nama: ")
              usia = int(input("Usia: "))
              alamat = input("Alamat: ")
              diagnosis = input("Diagnosis: ")
              tanggal_masuk = input("Tanggal Masuk (dd/mm/yyyy): ")
              nomor_ktp = input("Nomor KTP: ")
              kamar = input("Kamar: ")
      
              if not cek_kamar_tersedia(kamar):
                  print(f"Kamar {kamar} tidak tersedia.")
              elif not validasi_nomor_ktp(nomor_ktp):
                  print("Nomor KTP harus terdiri dari 10 angka.")
              else:
                  patient = {
                      "nama": nama,
                      "usia": usia,
                      "alamat": alamat,
                      "diagnosis": diagnosis,
                      "tanggal_masuk": tanggal_masuk,
                      "nomor_ktp": nomor_ktp,
                      "kamar": kamar,
                      "tanggal_keluar": None  # Tanggal keluar diatur saat update
                  }
                  patients.append(patient)
                  print("Data pasien berhasil ditambahkan.")
              
              kembali = input("Kembali ke menu utama? (y/n): ")
              if kembali.lower() == 'y':
                  break

# Read all patients
      def lihat_semua_pasien():
          while True:
              print(f"{'Nama':<15} {'Usia':<5} {'Alamat':<20} {'Diagnosis':<10} {'Tanggal Masuk':<15} {'Nomor KTP':<12} {'Kamar':<10} {'Tanggal Keluar':<15}")
              print("="*102)
              for patient in patients:
                  tanggal_keluar = patient['tanggal_keluar'] if patient['tanggal_keluar'] else ""
                  print(f"{patient['nama']:<15} {patient['usia']:<5} {patient['alamat']:<20} {patient['diagnosis']:<10} {patient['tanggal_masuk']:<15} {patient['nomor_ktp']:<12} {patient['kamar']:<10} {tanggal_keluar:<15}")
              print()
      
              kembali = input("Kembali ke menu utama? (y/n): ")
              if kembali.lower() == 'y':
                  break

# Read by room
      def lihat_pasien_by_kamar():
          while True:
              kamar = input("Masukkan nomor kamar: ")
              for patient in patients:
                  if patient["kamar"] == kamar:
                      if patient["tanggal_keluar"] is None:
                          tanggal_keluar = patient['tanggal_keluar'] if patient['tanggal_keluar'] else ""
                          print(f"{'Nama':<15} {'Usia':<5} {'Alamat':<20} {'Diagnosis':<10} {'Tanggal Masuk':<15} {'Nomor KTP':<12} {'Kamar':<10} {'Tanggal Keluar':<15}")
                          print("="*102)
                          print(f"{patient['nama']:<15} {patient['usia']:<5} {patient['alamat']:<20} {patient['diagnosis']:<10} {patient['tanggal_masuk']:<15} {patient['nomor_ktp']:<12} {patient['kamar']:<10} {tanggal_keluar:<15}")
                          break
              else:
                  print(f"Kamar {kamar} tidak ada pasien atau sudah kosong.")
              
              kembali = input("Kembali ke menu utama? (y/n): ")
              if kembali.lower() == 'y':
                  break

# Read average stay duration
      def lihat_rata_rata_menginap():
          while True:
              total_days = 0
              patient_count = 0
              for patient in patients:
                  if patient["tanggal_keluar"]:
                      tgl_masuk = datetime.strptime(patient["tanggal_masuk"], "%d/%m/%Y")
                      tgl_keluar = datetime.strptime(patient["tanggal_keluar"], "%d/%m/%Y")
                      lama_menginap = (tgl_keluar - tgl_masuk).days
                      total_days += lama_menginap
                      patient_count += 1
              if patient_count == 0:
                  print("Tidak ada data pasien yang sudah keluar.")
              else:
                  rata_rata = total_days / patient_count
                  print(f"Rata-rata lama pasien menginap: {rata_rata:.2f} hari")
              
              kembali = input("Kembali ke menu utama? (y/n): ")
              if kembali.lower() == 'y':
                  break

# Update
      def update_pasien():
          while True:
              nama = input("Nama pasien yang akan diperbarui: ")
              usia = int(input("Usia: "))
              alamat = input("Alamat: ")
              diagnosis = input("Diagnosis: ")
              tanggal_masuk = input("Tanggal Masuk (dd/mm/yyyy): ")
              nomor_ktp = input("Nomor KTP: ")
              kamar = input("Kamar: ")
              tanggal_keluar = input("Tanggal Keluar (dd/mm/yyyy) atau biarkan kosong jika belum keluar: ") or None
      
              for patient in patients:
                  if patient["nama"].lower() == nama.lower():
                      if tanggal_keluar and not cek_kamar_tersedia(kamar):
                          print(f"Kamar {kamar} tidak tersedia.")
                      elif not validasi_nomor_ktp(nomor_ktp):
                          print("Nomor KTP harus terdiri dari 10 angka.")
                      else:
                          patient["usia"] = usia
                          patient["alamat"] = alamat
                          patient["diagnosis"] = diagnosis
                          patient["tanggal_masuk"] = tanggal_masuk
                          patient["nomor_ktp"] = nomor_ktp
                          patient["kamar"] = kamar
                          patient["tanggal_keluar"] = tanggal_keluar
                          print("Data pasien berhasil diperbarui.")
                      break
              else:
                  print("Pasien tidak ditemukan.")
              
              kembali = input("Kembali ke menu utama? (y/n): ")
              if kembali.lower() == 'y':
                  break

# Delete
      def hapus_pasien():
          while True:
              nama = input("Nama pasien yang akan dihapus: ")
              for patient in patients:
                  if patient["nama"].lower() == nama.lower():
                      konfirmasi = input(f"Apakah Anda yakin ingin menghapus data pasien {nama}? (y/n): ")
                      if konfirmasi.lower() == 'y':
                          patients.remove(patient)
                          print("Data pasien berhasil dihapus.")
                          return
              else:
                  print("Pasien tidak ditemukan.")
              
              kembali = input("Kembali ke menu utama? (y/n): ")
              if kembali.lower() == 'y':
                  break
# Main Menu
      def main():
          while True:
              print("\nMenu:")
              print("1. Tambah Pasien")
              print("2. Lihat Pasien")
              print("3. Update Pasien")
              print("4. Hapus Pasien")
              print("5. Keluar")
      
              pilihan = input("Pilih menu (1/2/3/4/5): ")
      
              if pilihan == '1':
                  tambah_pasien()
              elif pilihan == '2':
                  print("\nSubmenu Lihat Pasien:")
                  print("1. Lihat Semua Pasien")
                  print("2. Lihat Pasien Berdasarkan Nomor Kamar")
                  print("3. Lihat Rata-rata Lama Menginap Pasien")
                  sub_pilihan = input("Pilih submenu (1/2/3): ")
                  if sub_pilihan == '1':
                      lihat_semua_pasien()
                  elif sub_pilihan == '2':
                      lihat_pasien_by_kamar()
                  elif sub_pilihan == '3':
                      lihat_rata_rata_menginap()
                  else:
                      print("Pilihan tidak valid.")
              elif pilihan == '3':
                  update_pasien()
              elif pilihan == '4':
                  hapus_pasien()
              elif pilihan == '5':
                  print("Terima kasih dan sampai jumpa!")
                  break
              else:
                  print("Pilihan tidak valid.")
      
      if __name__ == "__main__":
          main()
