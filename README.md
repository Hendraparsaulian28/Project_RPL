## Sistem Penyewaan Kendaraan
```py
class Kendaraan:
    def __init__(self, nomor_plat, merk, tahun, harga_sewa_per_hari, tersedia=True):
        self.nomor_plat = nomor_plat
        self.merk = merk
        self.tahun = tahun
        self.harga_sewa_per_hari = harga_sewa_per_hari
        self.tersedia = tersedia

    def informasi_kendaraan(self):
        return f"{self.merk} {self.tahun} - Nomor Plat: {self.nomor_plat}"

    def cek_ketersediaan(self):
        if self.tersedia:
            return "Tersedia untuk disewa"
        else:
            return "Tidak tersedia untuk disewa"

    def sewakan(self):
        if self.tersedia:
            self.tersedia = False
            return f"{self.merk} {self.tahun} berhasil disewakan"
        else:
            return f"{self.merk} {self.tahun} tidak tersedia saat ini"

    def kembalikan(self):
        if not self.tersedia:
            self.tersedia = True
            return f"{self.merk} {self.tahun} berhasil dikembalikan"
        else:
            return f"{self.merk} {self.tahun} sudah tersedia"


class Rental:
    def __init__(self):
        self.kendaraan_disewa = []

    def tambah_kendaraan(self, kendaraan):
        self.kendaraan_disewa.append(kendaraan)

    def daftar_kendaraan(self):
        if self.kendaraan_disewa:
            print("Daftar Kendaraan yang Sedang Disewakan:")
            for kendaraan in self.kendaraan_disewa:
                print(kendaraan.informasi_kendaraan())
        else:
            print("Belum ada kendaraan yang disewakan")

    def kendaraan_dipinjam(self):
        return len(self.kendaraan_disewa)


# Contoh penggunaan
if __name__ == "__main__":
    kendaraan1 = Kendaraan("B 1234 CD", "Toyota Avanza", 2020, 300000)
    kendaraan2 = Kendaraan("B 5678 EF", "Honda Jazz", 2019, 250000)

    rental = Rental()
    rental.tambah_kendaraan(kendaraan1)
    rental.tambah_kendaraan(kendaraan2)

    print("Jumlah Kendaraan yang Sedang Disewakan:", rental.kendaraan_dipinjam())
    rental.daftar_kendaraan()

    print("\n--- Proses Penyewaan ---")
    print(kendaraan1.sewakan())
    print(kendaraan2.sewakan())

    print("\nJumlah Kendaraan yang Sedang Disewakan:", rental.kendaraan_dipinjam())
    rental.daftar_kendaraan()

    print("\n--- Proses Pengembalian ---")
    print(kendaraan1.kembalikan())
    print(kendaraan2.kembalikan())

    print("\nJumlah Kendaraan yang Sedang Disewakan:", rental.kendaraan_dipinjam())
    rental.daftar_kendaraan()
```