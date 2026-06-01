# linked

##  1. Kenapa Harus Linked List?
* [cite_start]**Problem:** List bawaan Python itu dinamis, ukurannya bisa berubah-ubah[cite: 203, 204]. [cite_start]Tapi di bahasa pemrograman lain, ukuran *array/list* biasanya kaku (harus dipesan di awal)[cite: 206].
* [cite_start]**Solusi:** Bikin struktur data sendiri yang ukurannya bebas memanjang/memendek saat program jalan, namanya **Linked List**[cite: 206].
* [cite_start]Karena datanya nyebar di memori (nggak berurutan), kita butuh "penunjuk jalan" biar data satu dan lainnya tetap nyambung[cite: 214, 230].

###  2. Komponen Utama: Node
Node itu ibarat gerbong kereta. [cite_start]Di dalam satu gerbong (Node), pasti ada dua informasi[cite: 235, 236]:
1.  [cite_start]**Data:** Isi nilainya (misal angka 93)[cite: 247, 251].
2.  [cite_start]**Next:** *Pointer* / penunjuk ke gerbong selanjutnya[cite: 252]. [cite_start]Kalau dia gerbong terakhir, `next`-nya berisi `None` (Ground/Nil)[cite: 247, 252].

**Method Wajib di Node:**
* [cite_start]`getData()` & `setData()`: Buat ngambil dan ngubah isi datanya[cite: 239, 241].
* [cite_start]`getNext()` & `setNext()`: Buat ngambil dan ngubah penunjuk ke node selanjutnya[cite: 240, 242].

### 3. Linked List & Head
* [cite_start]Linked List itu kumpulan gerbong (node) tadi[cite: 280].
* Biar keretanya bisa jalan, kita wajib tahu mana lokomotif awalnya. [cite_start]Di sini namanya **`Head`**[cite: 231, 281].
* [cite_start]Kalau `Head` masih berisi `None`, berarti keretanya (Linked List) masih kosong melompong[cite: 286, 288].

---

### 4. Operasi Penting & Aturan Mainnya

#### A. Nambah Data (`add`)
* [cite_start]Data baru *default*-nya selalu ditambahin di **paling depan** (nempel ke Head)[cite: 313].
* **Aturan Nambah Data (JANGAN KEBALIK!):**
  1.  [cite_start]Node baru suruh nunjuk ke node lama (yang lagi dipegang Head)[cite: 315].
  2.  [cite_start]Baru Head-nya disuruh pegang node baru tersebut[cite: 316].
  [cite_start]*💡 Kalau Head-nya duluan yang dipindah, sisa gerbong di belakangnya bakal putus dan hilang dari memori!* [cite: 327]

#### B. Jalan-jalan / Traversal (`size`, `search`, `display`)
* Kita nggak bisa langsung loncat ke node ke-5. [cite_start]Harus jalan dari Head satu per satu pakai bantuan pointer `current`[cite: 380].
* [cite_start]Caranya: `current = current.getNext()` (geser terus sampai ketemu data yang dicari atau sampai nilainya `None`)[cite: 384, 385, 418].

#### C. Menghapus Data (`remove`)
* Ini agak *tricky*. [cite_start]Kita butuh dua tangan (pointer): `current` (buat nyari target) dan `previous` (buat ngikutin dari belakang)[cite: 517, 518].
* [cite_start]Kalau target ketemu, node sebelumnya (`previous`) langsung disambungin ke node sesudahnya target[cite: 516, 518]. Otomatis targetnya bakal terputus dan kehapus!
* [cite_start]**Pengecualian:** Kalau yang dihapus itu node pertama (Head), tinggal geser aja Head-nya ke node kedua[cite: 557].

---

###  5. Ordered List (List Terurut)
* [cite_start]Ini versi *upgrade*[cite: 654]. [cite_start]Datanya selalu diurutkan dari kecil ke besar setiap kali ada data masuk[cite: 655].
* [cite_start]**Keuntungannya:** Nyari data jadi jauh lebih cepet[cite: 653]. 
* [cite_start]Kalau kita nyari angka 10 tapi *current* udah nyentuh angka 15, pencarian langsung berhenti (`stop = True`), gak perlu repot ngecek sampai belakang[cite: 653, 701].

---

###  keseluruhan Code
```python
class Node:
    def __init__(self, init_data):
        self.data = init_data
        self.next = None
    def getData(self): return self.data
    def getNext(self): return self.next
    def setData(self, newdata): self.data = newdata
    def setNext(self, new_next): self.next = new_next

class LinkedList:
    def __init__(self):
        self.head = None
        
    def isEmpty(self):
        return self.head == None
        
    def add(self, item):
        temp = Node(item)
        temp.setNext(self.head)
        self.head = temp
        
    def display(self):
        current = self.head
        while current != None:
            print(current.getData(), end=" -> ")
            current = current.getNext()
        print("None")

    # ==========================================
    # JAWABAN LATIHAN: insertNext & insertPrevious
    # ==========================================
    
    def insertNext(self, item_cari, item_baru):
        """Nyelipin node baru SETELAH node tertentu"""
        current = self.head
        found = False
        
        # Cari dulu nodenya
        while current != None and not found:
            if current.getData() == item_cari:
                found = True
            else:
                current = current.getNext()
                
        if found:
            temp = Node(item_baru)
            # Node baru nunjuk ke tetangga kanannya current
            temp.setNext(current.getNext())
            # Current nunjuk ke node baru
            current.setNext(temp)
        else:
            print(f"Data {item_cari} tidak ditemukan!")

    def insertPrevious(self, item_cari, item_baru):
        """Nyelipin node baru SEBELUM node tertentu"""
        current = self.head
        previous = None
        found = False
        
        while current != None and not found:
            if current.getData() == item_cari:
                found = True
            else:
                previous = current
                current = current.getNext()
                
        if found:
            temp = Node(item_baru)
            # Kalau targetnya ada di paling depan (Head)
            if previous == None:
                temp.setNext(self.head)
                self.head = temp
            else:
                # Nyelip di tengah
                temp.setNext(current)
                previous.setNext(temp)
        else:
            print(f"Data {item_cari} tidak ditemukan!")

# --- TEST DRIVE JAWABAN LATIHAN ---
if __name__ == "__main__":
    print("=== TESTING LINKED LIST ===")
    mylist = LinkedList()
    mylist.add(45)
    mylist.add(34)
    mylist.add(70) # Urutan saat ini: 70 -> 34 -> 45 -> None
    
    print("Kondisi Awal:")
    mylist.display()
    
    print("\nInsert 99 SETELAH 34:")
    mylist.insertNext(34, 99)
    mylist.display()
    
    print("\nInsert 11 SEBELUM 45:")
    mylist.insertPrevious(45, 11)
    mylist.display()