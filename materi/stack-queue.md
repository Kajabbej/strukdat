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