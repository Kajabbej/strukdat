# Hashing
# H. HASHING

[cite_start]**Hashing** adalah proses pembuatan indeks dan pengambilan data (elemen) dari sebuah struktur data untuk menyediakan cara pencarian yang jauh lebih cepat[cite: 4024]. Hashing bekerja dengan menggunakan sebuah fungsi matematika khusus yang disebut **Hash Function**.

## H1. Konsep Dasar
* [cite_start]**Hash Function:** Fungsi yang mengubah sebuah nilai (*Key*) menjadi angka indeks (*Hash Value*)[cite: 4032, 4033].
* [cite_start]**Rumus Dasar:** `Hash Value = Key % Ukuran_Tabel` (Nilai sisa bagi)[cite: 4037, 4041].
* [cite_start]**Contoh:** Jika ukuran tabel adalah 11, dan data yang masuk adalah `54`, maka indeksnya adalah `54 % 11 = 10`[cite: 4043]. Data `54` akan disimpan di laci ke-10.

## H2. Collision (Tabrakan)
[cite_start]**Collision** terjadi ketika dua data atau lebih menghasilkan *Hash Value* (indeks) yang sama[cite: 4042, 4045]. 
* Contoh: Data `77` dan `44`. 
  * `77 % 11 = 0`
  * `44 % 11 = 0`
Keduanya berebut ingin masuk ke laci indeks ke-0. 

Untuk mengatasi tabrakan ini, ada dua strategi utama:

### 1. Open Addressing (Mencari Slot Kosong)
[cite_start]Jika slot tujuan sudah penuh, algoritma akan mencari slot kosong lain di sebelahnya[cite: 4048].
* [cite_start]**Linear Probing:** Mencari slot kosong secara berurutan satu per satu (indeks + 1, indeks + 2, dst) hingga ketemu yang kosong[cite: 4049].
* **Quadratic Probing:** Mencari slot kosong dengan lompatan jarak kuadrat ($h+1^2$, $h+2^2$, $h+3^2$, dst). [cite_start]Artinya melompat +1, +4, +9, +16 dari titik awal[cite: 4050]. Langkah ini membantu menyebar data agar tidak menumpuk di satu area.

### 2. Closed Addressing (Chaining)
[cite_start]Daripada mencari laci kosong lain, strategi **Chaining** membiarkan beberapa data menumpuk di laci yang sama[cite: 4149, 4150]. Caranya adalah dengan mengubah setiap laci menjadi sebuah *List/Array* baru. 
* [cite_start]Jika `77` dan `44` masuk ke indeks 0, maka isi indeks 0 menjadi list: `[77, 44]`[cite: 4177].

# ==========================================
# IMPLEMENTASI HASHING DAN PENANGANAN COLLISION
# ==========================================

# ------------------------------------------
# 1. STRATEGI: LINEAR PROBING
# ------------------------------------------
def insert_linear_probing(table, key):
    ukuran = len(table)
    indeks = key % ukuran
    
    # Jika slot kosong, langsung masukkan
    if table[indeks] is None:
        table[indeks] = key
    else:
        # COLLISION! Lakukan Linear Probing (Maju 1 langkah berulang kali)
        found = False
        indeks_baru = (indeks + 1) % ukuran
        
        while not found and indeks_baru != indeks:
            if table[indeks_baru] is None:
                table[indeks_baru] = key
                found = True
            else:
                indeks_baru = (indeks_baru + 1) % ukuran
                
        if not found:
            print(f"Tabel Penuh! Tidak bisa memasukkan {key}")

# ------------------------------------------
# 2. STRATEGI: QUADRATIC PROBING
# ------------------------------------------
def insert_quadratic_probing(table, key):
    ukuran = len(table)
    indeks = key % ukuran
    
    if table[indeks] is None:
        table[indeks] = key
    else:
        # COLLISION! Lakukan Quadratic Probing (Lompat 1, 4, 9, 16...)
        found = False
        i = 1
        
        while not found and i < ukuran:
            indeks_baru = (indeks + (i * i)) % ukuran
            if table[indeks_baru] is None:
                table[indeks_baru] = key
                found = True
            else:
                i += 1
                
        if not found:
            print(f"Gagal memposisikan {key} dengan Quadratic Probing")

# ------------------------------------------
# 3. STRATEGI: CHAINING (CLOSED ADDRESSING)
# ------------------------------------------
def insert_chaining(table, key):
    ukuran = len(table)
    indeks = key % ukuran
    # Langsung tambahkan ke dalam list di indeks tersebut (append)
    table[indeks].append(key)


# ==========================================
# UJI COBA KODE
# ==========================================
if __name__ == "__main__":
    # Data dari PDF Dosen
    data_uji = [54, 26, 93, 17, 77, 31, 44, 55, 20]
    ukuran_tabel = 11

    # Uji 1: Linear Probing
    tabel_linear = [None] * ukuran_tabel
    for data in data_uji:
        insert_linear_probing(tabel_linear, data)
    print("Hasil Linear Probing :")
    print(tabel_linear)
    print("-" * 50)

    # Uji 2: Quadratic Probing
    tabel_quadratic = [None] * ukuran_tabel
    for data in data_uji:
        insert_quadratic_probing(tabel_quadratic, data)
    print("Hasil Quadratic Probing :")
    print(tabel_quadratic)
    print("-" * 50)

    # Uji 3: Chaining
    # Buat tabel yang berisi list kosong [] di setiap slotnya
    tabel_chaining = [[] for _ in range(ukuran_tabel)]
    for data in data_uji:
        insert_chaining(tabel_chaining, data)
    print("Hasil Chaining :")
    print(tabel_chaining)