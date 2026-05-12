# Infix, Prefix, dan Postfix
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

# ==========================================
# KONVERSI INFIX KE POSTFIX & PREFIX
# ==========================================

def infix_to_postfix(ekspresi):
    prioritas = {'+': 1, '-': 1, '*': 2, '/': 2}
    stack, output = [], []

    for token in ekspresi.replace(" ", ""):
        if token.isalpha():
            output.append(token)
        elif token == '(':
            stack.append(token)
        elif token == ')':
            while stack and stack[-1] != '(':
                output.append(stack.pop())
            stack.pop()
        else:
            while (stack and stack[-1] != '(' and
                   prioritas.get(stack[-1], 0) >= prioritas.get(token, 0)):
                output.append(stack.pop())
            stack.append(token)

    while stack:
        output.append(stack.pop())

    return " ".join(output)

def infix_to_prefix(ekspresi):
    # Langkah 1: balik dan ganti kurung
    dibalik = ekspresi[::-1]
    ganti = ""
    for c in dibalik:
        if c == '(':   ganti += ')'
        elif c == ')': ganti += '('
        else:          ganti += c
            
    # Langkah 2: Konversi ke postfix
    postfix = infix_to_postfix(ganti)
    
    # Langkah 3: Balik hasil postfix
    return " ".join(postfix.split()[::-1])

# ==========================================
# UJI COBA SEMUA SOAL
# ==========================================
soal = ["A+B", "A+B*C", "(A+B)*C", "A*(B+C)", "(A-B)/(C+D)"]

print(f"{'Infix':<20} {'Postfix':<20} {'Prefix'}")
print("-" * 55)
for s in soal:
    print(f"{s:<20} {infix_to_postfix(s):<20} {infix_to_prefix(s)}")