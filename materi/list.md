# linked

##  1. Kenapa Harus Linked List?
**Problem:** List bawaan Python itu dinamis, ukurannya bisa berubah-ubah. Tapi di bahasa pemrograman lain, ukuran *array/list* biasanya kaku (harus dipesan di awal).
Solusi:** Bikin struktur data sendiri yang ukurannya bebas memanjang/memendek saat program jalan, namanya **Linked List**.
Karena datanya nyebar di memori (nggak berurutan), kita butuh "penunjuk jalan" biar data satu dan lainnya tetap nyambung.

###  2. Komponen Utama: Node
Node itu ibarat gerbong kereta. Di dalam satu gerbong (Node), pasti ada dua informasi:
1.  **Data:** Isi nilainya (misal angka 93).
2.  **Next:** *Pointer* / penunjuk ke gerbong selanjutnya. Kalau dia gerbong terakhir, `next`-nya berisi `None` (Ground/Nil).

**Method Wajib di Node:**
* `getData()` & `setData()`: Buat ngambil dan ngubah isi datanya.
* `getNext()` & `setNext()`: Buat ngambil dan ngubah penunjuk ke node selanjutnya.

### 3. Linked List & Head
* Linked List itu kumpulan gerbong (node) tadi.
* Biar keretanya bisa jalan, kita wajib tahu mana lokomotif awalnya. Di sini namanya **`Head`**
* Kalau `Head` masih berisi `None`, berarti keretanya (Linked List) masih kosong melompong.

---

### 4. Operasi Penting & Aturan Mainnya

#### A. Nambah Data (`add`)
* Data baru *default*-nya selalu ditambahin di **paling depan** (nempel ke Head).
* **Aturan Nambah Data (JANGAN KEBALIK!):**
  1.  Node baru suruh nunjuk ke node lama (yang lagi dipegang Head).
  2.  Baru Head-nya disuruh pegang node baru tersebut.
  *Kalau Head-nya duluan yang dipindah, sisa gerbong di belakangnya bakal putus dan hilang dari memori!* 

#### B. Jalan-jalan / Traversal (`size`, `search`, `display`)
* Kita nggak bisa langsung loncat ke node ke-5. Harus jalan dari Head satu per satu pakai bantuan pointer `current`.
* Caranya: `current = current.getNext()` (geser terus sampai ketemu data yang dicari atau sampai nilainya `None`).

#### C. Menghapus Data (`remove`)
* Ini agak *tricky*. Kita butuh dua tangan (pointer): `current` (buat nyari target) dan `previous` (buat ngikutin dari belakang).
* Kalau target ketemu, node sebelumnya (`previous`) langsung disambungin ke node sesudahnya target. Otomatis targetnya bakal terputus dan kehapus!
* **Pengecualian:** Kalau yang dihapus itu node pertama (Head), tinggal geser aja Head-nya ke node kedua.

---

###  5. Ordered List (List Terurut)
* Ini versi *upgrade*. Datanya selalu diurutkan dari kecil ke besar setiap kali ada data masuk.
* **Keuntungannya:** Nyari data jadi jauh lebih cepet. 
* Kalau kita nyari angka 10 tapi *current* udah nyentuh angka 15, pencarian langsung berhenti (`stop = True`), gak perlu repot ngecek sampai belakang.

---