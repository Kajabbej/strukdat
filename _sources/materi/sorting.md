# Sorting
# Algoritma Sorting (Pengurutan Data)

## E. BUBBLE SORT
**Konsep Dasar:** Membandingkan dua elemen yang berdekatan. Jika elemen kiri lebih besar dari elemen kanan, maka posisinya ditukar. Proses ini diulang terus sampai tidak ada lagi elemen yang perlu ditukar. Elemen terbesar akan "menggelembung" ke posisi paling kanan di setiap iterasinya.
* **Time Complexity:** O(n²) worst case, O(n) best case (jika ditambah optimasi *early exit*).
* **Space Complexity:** O(1) (In-place sorting).
* **Sifat:** Stabil (*Stable*).

**Tracing Bubble Sort (Contoh Data: [64, 34, 25, 12, 22, 11, 90]):**
| Pass   | Hasil Setelah Pass              |
|--------|---------------------------------|
| Pass 1 | [34, 25, 12, 22, 11, 64, 90]    |
| Pass 2 | [25, 12, 22, 11, 34, 64, 90]    |
| Pass 3 | [12, 22, 11, 25, 34, 64, 90]    |
| Pass 4 | [12, 11, 22, 25, 34, 64, 90]    |
| Pass 5 | [11, 12, 22, 25, 34, 64, 90]    |
| Selesai| **[11, 12, 22, 25, 34, 64, 90]**|

---

## F. SELECTION SORT
**Konsep Dasar:** Di setiap iterasinya, algoritma ini mencari elemen **minimum** dari bagian list yang belum terurut, lalu menukarnya dengan elemen di posisi paling depan dari bagian tersebut. Hanya ada **1 kali pertukaran (swap) per pass**.
* **Time Complexity:** O(n²) untuk Best, Average, dan Worst case.
* **Sifat:** Tidak Stabil (*Unstable*).
* **Kelebihan:** Sangat efisien jika operasi *swap* (pertukaran memori) memakan biaya/waktu yang mahal.

**Tracing Selection Sort (Contoh Data: [29, 10, 14, 37, 13]):**
| Pass   | Elemen Min   | Ditukar dengan  | Hasil                    |
|--------|--------------|-----------------|--------------------------|
| Pass 1 | 10 (idx 1)   | 29 (idx 0)      | [10, 29, 14, 37, 13]     |
| Pass 2 | 13 (idx 4)   | 29 (idx 1)      | [10, 13, 14, 37, 29]     |
| Pass 3 | 14 (idx 2)   | sudah di posisi | [10, 13, 14, 37, 29]     |
| Pass 4 | 29 (idx 4)   | 37 (idx 3)      | [10, 13, 14, 29, 37]     |

---

## G. INSERTION SORT
**Konsep Dasar:** Bekerja seperti cara orang mengurutkan kartu di tangan. Algoritma mengasumsikan bagian awal list sudah terurut, lalu mengambil satu data baru dan **menyisipkannya** (*insert*) ke posisi yang benar di dalam bagian yang sudah terurut tersebut dengan cara menggeser (*shift*) elemen yang lebih besar.
* **Time Complexity:** O(n) saat *best case* (data hampir terurut).
* **Sifat:** Stabil (*Stable*).
* **Kelebihan:** Sangat cepat untuk data berskala kecil atau data yang sudah hampir terurut secara alami.

**Tracing Insertion Sort (Contoh Data: [12, 11, 13, 5, 6]):**
| Pass   | Kunci | Hasil Setelah Disisipkan       |
|--------|-------|--------------------------------|
| Pass 1 | 11    | [11, 12, 13, 5, 6]             |
| Pass 2 | 13    | [11, 12, 13, 5, 6]             |
| Pass 3 | 5     | [5, 11, 12, 13, 6]             |
| Pass 4 | 6     | [5, 6, 11, 12, 13]             |

---

## 📊 BONUS: Tabel Perbandingan Semua Sorting

| Algoritma      | Best Case | Average | Worst Case | Space | Stable |
|----------------|-----------|---------|------------|-------|--------|
| Bubble Sort    | O(n)      | O(n²)   | O(n²)      | O(1)  | ✅     |
| Selection Sort | O(n²)     | O(n²)   | O(n²)      | O(1)  | ❌     |
| Insertion Sort | O(n)      | O(n²)   | O(n²)      | O(1)  | ✅     |

# ==========================================
# 1. KUMPULAN FUNGSI BUBBLE SORT
# ==========================================

def bubble_sort_ascending(data):
    arr = data.copy()
    n = len(arr)
    total_swap = 0
    print(f"Data awal Bubble: {arr}")

    for i in range(n - 1):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:  # jika kiri > kanan
                arr[j], arr[j+1] = arr[j+1], arr[j]  # tukar
                total_swap += 1
    
    print(f"Hasil Akhir (Asc) : {arr} | Total Swap: {total_swap}")
    return arr

def bubble_sort_descending(data):
    arr = data.copy()
    n = len(arr)
    for i in range(n - 1):
        for j in range(0, n - i - 1):
            if arr[j] < arr[j + 1]:  # ubah > menjadi < untuk descending
                arr[j], arr[j+1] = arr[j+1], arr[j]
    print(f"Hasil Akhir (Desc): {arr}")
    return arr

def bubble_sort_optimized(data):
    arr = data.copy()
    n = len(arr)
    for i in range(n - 1):
        sudah_terurut = True   # flag optimasi
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
                sudah_terurut = False
        
        if sudah_terurut:   # tidak ada swap = sudah urut, stop!
            print(f"Early exit: Selesai lebih awal di pass {i+1}")
            break
    return arr


# ==========================================
# 2. KUMPULAN FUNGSI SELECTION SORT
# ==========================================

def selection_sort(data):
    arr = data.copy()
    n = len(arr)
    print(f"\nData awal Selection: {arr}")

    for i in range(n - 1):
        idx_min = i
        for j in range(i + 1, n):
            if arr[j] < arr[idx_min]:
                idx_min = j
        
        # Tukar tepat 1 kali per pass
        if idx_min != i:
            arr[i], arr[idx_min] = arr[idx_min], arr[i]
            
    print(f"Hasil Akhir (Asc)  : {arr}")
    return arr

def selection_sort_nama(nama):
    arr = nama.copy()
    n = len(arr)
    for i in range(n - 1):
        idx_min = i
        for j in range(i + 1, n):
            if arr[j].lower() < arr[idx_min].lower():   # bandingkan alfabet
                idx_min = j
        arr[i], arr[idx_min] = arr[idx_min], arr[i]
    return arr


# ==========================================
# 3. KUMPULAN FUNGSI INSERTION SORT
# ==========================================

def insertion_sort(data):
    arr = data.copy()
    n = len(arr)
    print(f"\nData awal Insertion: {arr}")

    for i in range(1, n):
        kunci = arr[i]
        j = i - 1
        
        # Geser elemen yang lebih besar ke kanan
        while j >= 0 and arr[j] > kunci:
            arr[j + 1] = arr[j]
            j -= 1
            
        arr[j + 1] = kunci   # sisipkan kunci

    print(f"Hasil Akhir (Asc)  : {arr}")
    return arr

def insertion_sort_desc(data):
    arr = data.copy()
    n = len(arr)
    for i in range(1, n):
        kunci = arr[i]
        j = i - 1
        while j >= 0 and arr[j] < kunci:   # ubah > menjadi < untuk descending
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = kunci
    print(f"Hasil Akhir (Desc) : {arr}")
    return arr


# ==========================================
# UJI COBA KODE
# ==========================================
if __name__ == "__main__":
    angka_tes = [64, 34, 25, 12, 22, 11, 90]
    
    bubble_sort_ascending(angka_tes)
    bubble_sort_descending(angka_tes)
    
    selection_sort(angka_tes)
    
    nama_tes = ["Sari", "Ahmad", "Budi", "Rina", "Doni"]
    print(f"Selection Sort Nama: {selection_sort_nama(nama_tes)}")
    
    insertion_sort(angka_tes)
    insertion_sort_desc(angka_tes)