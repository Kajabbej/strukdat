# Stack & Queue
## A. Stack (Tumpukan)

Stack adalah koleksi data yang menggunakan prinsip **LIFO (Last In, First Out)**. Elemen yang terakhir dimasukkan akan menjadi yang pertama kali dikeluarkan.

- **Push**: Menambahkan elemen ke posisi teratas.
- **Pop**: Menghapus dan mengambil elemen teratas.
- **Peek**: Melihat elemen teratas tanpa menghapusnya.
- **IsEmpty/Size**: Mengecek kondisi kosong atau jumlah elemen.

## B. Queue (Antrean)

Queue menggunakan prinsip **FIFO (First In, First Out)**. Data yang pertama masuk adalah yang pertama diproses.

- **Enqueue**: Menambah elemen di bagian belakang (rear).
- **Dequeue**: Menghapus elemen dari bagian depan (front).

## C. Deque (Double-Ended Queue)

Koleksi data di mana penambahan atau penghapusan elemen dapat dilakukan dari kedua ujung (depan dan belakang).

## D. Notasi Matematika (Infix, Prefix, Postfix)

Posisi operator menentukan jenis notasi:

1. **Infix**: Operator di tengah (`A + B`).
2. **Prefix**: Operator di depan (`+ A B`).
3. **Postfix**: Operator di belakang (`A B +`).

- **Aturan Precedence**: Urutan prioritas dari yang tertinggi adalah Kurung `()`, Eksponen `**`, Perkalian/Pembagian `* /`, dan Penjumlahan/Pengurangan `+ -`.

## E. Algoritma Sorting (Pengurutan)

- **Bubble Sort**: Membandingkan elemen bersebelahan dan menukarnya jika urutannya salah.
- **Selection Sort**: Mencari nilai minimum dan memindahkannya ke awal posisi yang belum terurut.
- **Insertion Sort**: Menyisipkan elemen satu per satu ke posisi yang tepat dalam sublist yang sudah terurut.
- **Quick Sort**: Menggunakan strategi *divide-and-conquer* dengan membagi list berdasarkan nilai *pivot*.

## F. Hashing

Proses pengindeksan data untuk pencarian cepat menggunakan kunci hash.

- **Collision**: Terjadi jika dua kunci memiliki nilai hash yang sama.
- **Solusi**: *Open Addressing* (Linear/Quadratic Probing) atau *Chaining* (Closed Addressing).
## Implementasi Kode Python

### Stack, Queue & Deque

```python
class Stack:
    def __init__(self, maks=None):
        self.items = []
        self.maks = maks

    def isEmpty(self):
        return len(self.items) == 0

    def push(self, item):
        if self.maks and len(self.items) >= self.maks:
            print(f"OVERFLOW! Stack penuh (maks {self.maks})")
        else:
            self.items.append(item)

    def pop(self):
        if self.isEmpty():
            print("UNDERFLOW! Stack kosong")
            return None
        return self.items.pop()

    def peek(self):
        if self.isEmpty(): return None
        return self.items[-1]

class Queue:
    def __init__(self):
        self.items = []

    def enqueue(self, item):
        self.items.insert(0, item)

    def dequeue(self):
        if len(self.items) == 0: return None
        return self.items.pop()
```

### Algoritma Sorting

```python
def bubbleSort(lst):
    n = len(lst)
    for k in range(1, n):
        for i in range(0, n-1):
            if lst[i] > lst[i+1]:
                lst[i], lst[i+1] = lst[i+1], lst[i]
    return lst

def selectionSort(lst):
    for i in range(len(lst)-1):
        min_idx = i
        for j in range(i+1, len(lst)):
            if lst[j] < lst[min_idx]:
                min_idx = j
        lst[i], lst[min_idx] = lst[min_idx], lst[i]
    return lst

def insertionSort(lst):
    for i in range(1, len(lst)):
        value = lst[i]
        hole = i
        while hole > 0 and lst[hole-1] > value:
            lst[hole] = lst[hole-1]
            hole = hole - 1
        lst[hole] = value
    return lst
```

### Hashing (Chaining)

```python
class HashTable:
    def __init__(self, size=11):
        self.table = [[] for _ in range(size)]

    def hashFunction(self, key):
        return key % len(self.table)

    def insert(self, key, value):
        idx = self.hashFunction(key)
        self.table[idx].append(value)
```

### Uji Coba

```python
data = [54, 26, 93, 17, 77, 31, 44, 55, 20]
print("Bubble Sort:", bubbleSort(data.copy()))
print("Selection Sort:", selectionSort(data.copy()))
print("Insertion Sort:", insertionSort(data.copy()))
```