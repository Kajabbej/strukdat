# 4. Hashing

**Hashing** adalah proses pembuatan indeks dan pengambilan data (elemen) dari sebuah struktur data untuk menyediakan cara pencarian yang jauh lebih cepat. Hashing bekerja dengan menggunakan sebuah fungsi matematika khusus yang disebut **Hash Function**.

## H1. Konsep Dasar

- **Hash Function:** Fungsi yang mengubah sebuah nilai (*Key*) menjadi angka indeks (*Hash Value*).
- **Rumus Dasar:** `Hash Value = Key % Ukuran_Tabel` (Nilai sisa bagi).
- **Contoh:** Jika ukuran tabel adalah 11, dan data yang masuk adalah `54`, maka indeksnya adalah `54 % 11 = 10`. Data `54` akan disimpan di laci ke-10.

## H2. Collision (Tabrakan)

**Collision** terjadi ketika dua data atau lebih menghasilkan *Hash Value* (indeks) yang sama.

- Contoh: Data `77` dan `44`.
  - `77 % 11 = 0`
  - `44 % 11 = 0`

Keduanya berebut ingin masuk ke laci indeks ke-0.

Untuk mengatasi tabrakan ini, ada dua strategi utama:

### 1. Open Addressing (Mencari Slot Kosong)

Jika slot tujuan sudah penuh, algoritma akan mencari slot kosong lain di sebelahnya.

- **Linear Probing:** Mencari slot kosong secara berurutan satu per satu (indeks + 1, indeks + 2, dst) hingga ketemu yang kosong.
- **Quadratic Probing:** Mencari slot kosong dengan lompatan jarak kuadrat ($h+1^2$, $h+2^2$, $h+3^2$, dst). Artinya melompat +1, +4, +9, +16 dari titik awal. Langkah ini membantu menyebar data agar tidak menumpuk di satu area.

### 2. Closed Addressing (Chaining)

Daripada mencari laci kosong lain, strategi **Chaining** membiarkan beberapa data menumpuk di laci yang sama. Caranya adalah dengan mengubah setiap laci menjadi sebuah *List/Array* baru.

- Jika `77` dan `44` masuk ke indeks 0, maka isi indeks 0 menjadi list: `[77, 44]`.

---