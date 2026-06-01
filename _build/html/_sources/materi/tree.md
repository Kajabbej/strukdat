**Materi:** Konsep Dasar Tree & Binary Tree

###  1. tree
* **Sifatnya:** *Non-linear*. (Catatan: Beda sama Stack atau Queue yang datanya berbaris lurus/linear).
* **Analogi:** Konsepnya ngambil dari pohon di dunia biologi, tapi bentuknya **kebalik**. 
* **Susunan:** Akarnya (root) ada di bagian paling atas, sedangkan daun (leaf) dan cabangnya ada di bawahnya.
* **Fungsi:** Biasanya dipakai untuk pencarian solusi. Kita mulai nyari dari atas (root), bergerak ke bawah mengikuti cabangnya (edge), sampai ketemu hasil akhirnya di daun.

###  2. Istilah Anatomi Tree 
* **Node:** Bagian dari tree yang menyimpan informasi atau *key*.
* **Edge:** Garis yang menghubungkan antara node yang satu dengan yang lain. Aturannya: cuma boleh ada **1 garis masuk** ke sebuah node, tapi garis keluarnya bisa satu atau lebih.
* **Root:** *Node* yang terletak di paling atas, tidak ada edge yang masuk ke dalam node root ini.
* **Leaf (Daun):** *Node* yang tidak memiliki edge yang keluar, atau node yang tidak memiliki children.
* **Parent:** *Node* yang memiliki edge yang keluar dari node tersebut.
* **Children:** *Node-node* yang memiliki edge masuk dari node yang sama. 
* **Siblings:** *Node-node* yang berasal dari *Parent* yang sama.
* **Path:** Urutan rute *node* dari *root* sampai ke tujuan.
* **Subtree:** Kumpulan dari node dan edge yang terdiri dari *parent* dan semua node setelahnya.
* **Level:** Tingkatan dari node. *Root* merupakan level ke-0, semakin ke bawah maka levelnya semakin besar.
* **Height:** Tinggi tree, nilai dari height ini adalah level maksimum dari tree.

---

###  Binary Tree (Pohon Biner)
* **Aturan Main:** Tiap *parent* hanya memiliki dua buah atau satu node *children* saja.
* Paling gampang diimplementasikan dengan menggunakan tipe data *Class*.
* **3 Properti Wajib di Class-nya**:
    1.  `key`: digunakan untuk informasi nilai yang terdapat pada node.
    2.  `leftChild`: *pointer* untuk menunjukkan child sebelah kiri.
    3.  `rightChild`: *pointer* untuk menunjukkan child sebelah kanan.

#### Menambah Data
Di dalam *Binary Tree*, ada *method* `insertLeft` dan `insertRight`. 

* **Kalau posisi kirinya masih kosong:** Subtree tersebut langsung dimasukkan pada `leftChild`.
* **Kalau posisi kirinya SUDAH ADA isinya:** Node baru bakal diselipin (tahapannya harus diatur sedemikian rupa).
* **Urutan Kode Nyelipin Node (Gak Boleh Kebalik!):**
    1.  `t.leftChild = self.leftChild`. (agar node di left child tetap ada)
    2.  `self.leftChild = t`.
    *💡 Kenapa gak boleh kebalik? Kalau dibalik, node yang merupakan leftchild dari node utama akan hilang, karena tidak ada pointer yang menunjuk ke leftchild tersebut.*

---

```python
class BinaryTree:
    def __init__(self, root):
        self.key = root
        self.leftChild = None
        self.rightChild = None
        
    def insertLeft(self, new_node):
        if self.leftChild == None:
            self.leftChild = BinaryTree(new_node)
        else:
            t = BinaryTree(new_node)
            t.leftChild = self.leftChild
            self.leftChild = t
            
    def insertRight(self, new_node):
        if self.rightChild == None:
            self.rightChild = BinaryTree(new_node)
        else:
            t = BinaryTree(new_node)
            t.rightChild = self.rightChild
            self.rightChild = t

    def getRightChild(self):
        return self.rightChild

    def getLeftChild(self):
        return self.leftChild

    def setRootVal(self, obj):
        self.key = obj

    def getRootVal(self):
        return self.key