# 3. Sorting
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

## Tabel Perbandingan Semua Sorting

| Algoritma      | Best Case | Average | Worst Case | Space | Stable |
|----------------|-----------|---------|------------|-------|--------|
| Bubble Sort    | O(n)      | O(n²)   | O(n²)      | O(1)  | ✅     |
| Selection Sort | O(n²)     | O(n²)   | O(n²)      | O(1)  | ❌     |
| Insertion Sort | O(n)      | O(n²)   | O(n²)      | O(1)  | ✅     |
