# 2. Infix, Prefix, dan Postfix
## D2. Konversi Infix ke Prefix

**Cara:** Balik string → ganti kurung → konversi ke postfix → balik hasil

| Infix              | Prefix            |
|--------------------|-------------------|
| A + B              | **+ A B** |
| A + B * C          | **+ A * B C** |
| (A + B) * C        | **\* + A B C** |
| A * (B + C)        | **\* A + B C** |
| (A - B) / (C + D)  | **/ - A B + C D** |

### Contoh langkah: (A + B) * C → **\* + A B C**

| Langkah              | Proses                          | Hasil          |
|----------------------|---------------------------------|----------------|
| 1. Balik infix       | `(A+B)*C` → `C*)B+A(`           | C * ) B + A (  |
| 2. Ganti kurung      | ) → ( dan ( → )                 | C * ( B + A )  |
| 3. Konversi postfix  | Menggunakan aturan Postfix      | C B A + * |
| 4. Balik hasil       | Reverse hasil langkah 3         | **\* + A B C** |
