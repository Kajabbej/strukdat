# ============================================================
#  Linked List — Unordered & Ordered Insert
#  Materi Praktikum Struktur Data
# ============================================================

class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


# ============================================================
#  UNORDERED LIST
# ============================================================
class UnorderedList:
    """
    Insert 18 ke dalam list tidak terurut:
    - Jika 18 ditemukan → sisipkan SETELAH node yang ditemukan
    - Jika 18 tidak ditemukan → sisipkan di AKHIR list
    """

    def __init__(self):
        self.head = None

    def append(self, data):
        """Tambah node di akhir (untuk membangun list awal)."""
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = new_node

    def insert_after_search(self, target, new_data):
        """
        Cari 'target' dalam list.
        Jika ditemukan  → sisipkan new_data SETELAH node target.
        Jika tidak ada  → sisipkan new_data di AKHIR list.
        """
        new_node = Node(new_data)
        current = self.head
        found = None

        # --- iterasi: cari node dengan nilai == target ---
        while current:
            if current.data == target:
                found = current
                break
            current = current.next

        if found:
            # sisipkan setelah node yang ditemukan
            new_node.next = found.next   # sambung ke node berikutnya
            found.next = new_node        # putus & arahkan ke node baru
            print(f"  [FOUND] {target} ditemukan → sisipkan {new_data} setelah node {target}")
        else:
            # cari ekor list, sisipkan di akhir
            if self.head is None:
                self.head = new_node
            else:
                tail = self.head
                while tail.next:
                    tail = tail.next
                tail.next = new_node          # setnext = temp (sesuai catatan)
            print(f"  [NOT FOUND] {target} tidak ditemukan → sisipkan {new_data} di akhir")

    def display(self):
        result = []
        current = self.head
        while current:
            result.append(str(current.data))
            current = current.next
        print("  Head -->", " --> ".join(result), "--> None")


# ============================================================
#  ORDERED LIST
# ============================================================
class OrderedList:
    """
    Insert ke dalam list terurut (ascending):
    - Iterasi selama current.data < new_data  → terus maju
    - Berhenti saat current.data >= new_data
    - Jika current.data == new_data (ada)     → sisipkan SETELAH current
    - Jika current.data > new_data  (tidak ada)→ sisipkan SEBELUM current
    """

    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = new_node

    def insert_ordered(self, new_data):
        new_node = Node(new_data)

        # --- kasus: list kosong atau new_data lebih kecil dari head ---
        if self.head is None or self.head.data > new_data:
            new_node.next = self.head
            self.head = new_node
            print(f"  Sisipkan {new_data} di awal list")
            return

        # --- iterasi: cari < sekarang, berhenti saat >= new_data ---
        prev = None
        current = self.head

        while current and current.data < new_data:
            prev = current
            current = current.next

        # Sekarang: current.data >= new_data  ATAU  current = None (akhir list)
        if current and current.data == new_data:
            # [CASE 1] nilai ada → sisipkan SETELAH current
            new_node.next = current.next
            current.next = new_node
            print(f"  [FOUND] {new_data} ada → sisipkan SETELAH node {current.data}")
        else:
            # [CASE 2] nilai tidak ada → sisipkan SEBELUM current (setelah prev)
            new_node.next = current       # sambung ke node yang lebih besar
            prev.next = new_node          # prev menunjuk ke node baru
            pos = current.data if current else "akhir list"
            print(f"  [NOT FOUND] {new_data} tidak ada → sisipkan sebelum {pos}")

    def display(self):
        result = []
        current = self.head
        while current:
            result.append(str(current.data))
            current = current.next
        print("  Head -->", " --> ".join(result), "--> None")


# ============================================================
#  DEMO / TEST
# ============================================================
if __name__ == "__main__":

    # ─── UNORDERED LIST ──────────────────────────────────────
    print("=" * 55)
    print("UNORDERED LIST")
    print("=" * 55)

    # Case 1: target 18 DITEMUKAN
    print("\nCase 1 — target ditemukan (18 ada di list):")
    ul1 = UnorderedList()
    for v in [7, 18, 6]:
        ul1.append(v)
    print("  Sebelum:", end=" "); ul1.display()
    ul1.insert_after_search(target=18, new_data=18)
    print("  Sesudah:", end=" "); ul1.display()

    # Case 2: target 18 TIDAK ditemukan
    print("\nCase 2 — target tidak ditemukan (18 tidak ada):")
    ul2 = UnorderedList()
    for v in [7, 10, 6]:
        ul2.append(v)
    print("  Sebelum:", end=" "); ul2.display()
    ul2.insert_after_search(target=18, new_data=18)
    print("  Sesudah:", end=" "); ul2.display()

    # ─── ORDERED LIST ────────────────────────────────────────
    print("\n" + "=" * 55)
    print("ORDERED LIST")
    print("=" * 55)

    # Case A: 18 sudah ada → sisipkan setelah
    print("\nCase A — nilai sudah ada (insert 18, list: 5→10→18→25):")
    ol1 = OrderedList()
    for v in [5, 10, 18, 25]:
        ol1.append(v)
    print("  Sebelum:", end=" "); ol1.display()
    ol1.insert_ordered(18)
    print("  Sesudah:", end=" "); ol1.display()

    # Case B: 18 belum ada → sisipkan sebelum yang lebih besar
    print("\nCase B — nilai belum ada (insert 18, list: 5→10→25):")
    ol2 = OrderedList()
    for v in [5, 10, 25]:
        ol2.append(v)
    print("  Sebelum:", end=" "); ol2.display()
    ol2.insert_ordered(18)
    print("  Sesudah:", end=" "); ol2.display()

    # Case C: insert di akhir (semua lebih kecil)
    print("\nCase C — insert di akhir (insert 30, list: 5→10→25):")
    ol3 = OrderedList()
    for v in [5, 10, 25]:
        ol3.append(v)
    print("  Sebelum:", end=" "); ol3.display()
    ol3.insert_ordered(30)
    print("  Sesudah:", end=" "); ol3.display()