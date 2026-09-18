◀*Back to:* [[00_Index_Programmazione_Procedurale]]

# Raccolta Esercizi d'Esame e Ripasso

- [[#Prova d'Esame 13/01/2025]]
- [[#Prova d'Esame 15/01/2026]]
- [[#Prova d'Esame 30/01/2026]]
- [[#Prova d'Esame 13/02/2026]]
- [[#Prova d'Esame 03/06/2026]]
- [[#Prova d'Esame 22/06/2026]]
- [[#Prova d'Esame 08/07/2026]]
- [[#Prova d'Esame 01/09/2026]]
- [[#Altri Esercizi e Conversioni]]
- [[#Esercizi Extra sulle Liste Concatenate]]

---

# Prova d'Esame 13/01/2025

### Esercizio 3: Cancellazione elemento in 3ª posizione

Data la struttura nodo e il puntatore globale `pFirst`:
```c
struct Node {
    int info;
    struct Node* pNext;
};
```
Definire `cancella_se_3_posizione(int key)` che cancella il terzo nodo solo se il suo campo `info` è uguale a `key`. Se la lista ha meno di 3 nodi o il valore non coincide, stampare un messaggio.

```c
void cancella_se_3_posizione(int key) {
    // Controllo che esistano almeno 3 elementi
    if (pFirst != NULL && pFirst->pNext != NULL && pFirst->pNext->pNext != NULL) {
        struct Node *prev = pFirst->pNext;        // 2° nodo
        struct Node *target = prev->pNext;        // 3° nodo

        if (target->info == key) {
            prev->pNext = target->pNext;          // Salta il 3° nodo
            free(target);
        } else {
            printf("L'elemento in terza posizione e' diverso da %d\n", key);
        }
    } else {
        printf("La lista ha meno di tre elementi\n");
    }
}
```

---

### Esercizio 5: Mappa di Memoria e Puntatori

```c
int a[5] = {INT_MAX - 7, 1287, INT_MIN + 528, -10, 312};
short int *p = (short int*) a;
char *q = (char*) a;
p[3] = SHRT_MAX;
p[5] += 2048;
q[18] = ~q[19];
```

- Tipi (32-bit arch): `int` = 4 byte, `short` = 2 byte, `char` = 1 byte.
- Little-Endian e complemento a due.
- Offset: `a[i]` ogni 4 byte, `p[i]` ogni 2 byte, `q[i]` ogni 1 byte (20 byte totali, 0..19).

#### Valori iniziali
- `a[0] = INT_MAX - 7` = `0x7FFFFFF8` $\to$ Byte 0..3: `F8 FF FF 7F`
- `a[1] = 1287` = `1024 + 256 + 7` = `0x00000507` $\to$ Byte 4..7: `07 05 00 00`
- `a[2] = INT_MIN + 528` = `0x80000000 + 0x0210` = `0x80000210` $\to$ Byte 8..11: `10 02 00 80`
- `a[3] = -10` = `0xFFFFFFF6` $\to$ Byte 12..15: `F6 FF FF FF`
- `a[4] = 312` = `256 + 56` = `0x00000138` $\to$ Byte 16..19: `38 01 00 00`

#### Modifiche
1. `p[3] = SHRT_MAX` (`0x7FFF`): sovrascrive Byte 6..7 con `FF 7F`.
2. `p[5] += 2048`: `p[5]` (Byte 10..11) vale `0x8000` ($-32768$). Somma `0x0800` ($2048$) $\to$ `0x8800` (Byte 10: `0x00`, Byte 11: `0x88`).
3. `q[18] = ~q[19]`: `q[19]` è `0x00` $\to \sim 0\text{x}00 = \text{0xFF}$. Byte 18 diventa `0xFF`.

#### Mappa di memoria finale

| Byte | Puntatori | Hex | Binario Esame (LSB $\to$ MSB) | Note |
| :---: | :--- | :---: | :---: | :--- |
| **0** | `a`, `&p[0]`, `&q[0]` | `0xF8` | `00011111` | Iniziale `a[0]` (LSB) |
| **1** | `&q[1]` | `0xFF` | `11111111` | `a[0]` |
| **2** | `&p[1]`, `&q[2]` | `0xFF` | `11111111` | `a[0]` |
| **3** | `&q[3]` | `0x7F` | `11111110` | `a[0]` (MSB) |
| **4** | `a+1`, `&p[2]`, `&q[4]` | `0x07` | `11100000` | Iniziale `a[1]` (LSB) |
| **5** | `&q[5]` | `0x05` | `10100000` | `a[1]` |
| **6** | `&p[3]`, `&q[6]` | `0xFF` | `11111111` | `p[3] = SHRT_MAX` |
| **7** | `&q[7]` | `0x7F` | `11111110` | `p[3] = SHRT_MAX` |
| **8** | `a+2`, `&p[4]`, `&q[8]` | `0x10` | `00001000` | Iniziale `a[2]` (LSB) |
| **9** | `&q[9]` | `0x02` | `01000000` | `a[2]` |
| **10** | `&p[5]`, `&q[10]` | `0x00` | `00000000` | `p[5] += 2048` |
| **11** | `&q[11]` | `0x88` | `00010001` | `p[5] += 2048` |
| **12** | `a+3`, `&p[6]`, `&q[12]` | `0xF6` | `01101111` | Iniziale `a[3]` (LSB = -10) |
| **13** | `q+13`, `&q[13]` | `0xFF` | `11111111` | `a[3]` |
| **14** | `&p[7]`, `&q[14]` | `0xFF` | `11111111` | `a[3]` |
| **15** | `&q[15]` | `0xFF` | `11111111` | `a[3]` (MSB) |
| **16** | `a+4`, `&p[8]`, `&q[16]` | `0x38` | `00011100` | Iniziale `a[4]` (LSB) |
| **17** | `&q[17]` | `0x01` | `10000000` | `a[4]` |
| **18** | `&p[9]`, `&q[18]` | `0xFF` | `11111111` | `q[18] = ~q[19]` |
| **19** | `&q[19]` | `0x00` | `00000000` | `a[4]` (MSB) |

#### Verifica asserzioni
- **A.** `(q[0] | q[1]) + q[17]`
  - `q[0] = 0xF8 = -8`, `q[1] = 0xFF = -1`.
  - `-8 | -1 = -1`.
  - `q[17] = 1`.
  - `-1 + 1 = 0` $\implies$ **FALSA (0)**.
- **B.** `*((short*)&q[17]) < 0`
  - Byte 17..18: `0x01, 0xFF` $\to$ short `0xFF01` = $-255$.
  - $-255 < 0$ $\implies$ **VERA (1)**.
- **C.** `(((int)(q + 13) - (int)(a + 1)) - q[1]) % 3`
  - `(int)(q + 13) = 13`, `(int)(a + 1) = 4` $\to 13 - 4 = 9$.
  - `q[1] = -1` $\to 9 - (-1) = 10$.
  - $10 \pmod 3 = 1$ $\implies$ **VERA (1)**.

---

# Prova d'Esame 15/01/2026

### Esercizio 1: Conversioni di tipo

```c
long int g2(unsigned long p) {
    return p + 'e' - 'a';
}

int g1(int p) {
    char c = 'k';           // 'k' = 107
    return g2(p + c - 'd'); // 65531 + 107 - 100 = 65538 -> passato a unsigned long
}

int main(void) {
    unsigned short x = -5L; // -5L convertito a unsigned short = 65531
    double b = g1(x);       // g2 restituisce 65542L -> g1 ritorna 65542 -> b = 65542.0
    printf("%f\n", b);     // Stampa: 65542.000000
}
```

---

### Esercizio 3: Cancellazione condizionata (divisibilità)

Cancellare il 3° nodo solo se il suo campo `info` **non è divisibile** per `x` (`curr->info % x != 0`).

```c
void cancella_se_3_posizione(int x) {
    if (pFirst == NULL || pFirst->pNext == NULL || pFirst->pNext->pNext == NULL)
        return;

    struct Node *prev = pFirst->pNext;
    struct Node *curr = prev->pNext;

    if (curr->info % x != 0) {
        prev->pNext = curr->pNext;
        free(curr);
    }
}
```

---

### Esercizio 5: Mappa di Memoria e Puntatori

```c
long long a[3] = {1536, -2, LLONG_MIN + 512};
short int *p = (short*) a;
char *q = (char*) a;
p[1] = 4098, p[3] = 4095 - 2, *(q + 15) = 73, p[9] = 4096 * 4 + 1;
```

- `long long` = 8 byte, `short` = 2 byte, `char` = 1 byte (24 byte totali).
- `a[0] = 1536` (`0x0600`), `a[1] = -2` (`0xFFFFFFFFFFFFFFFE`), `a[2] = LLONG_MIN + 512` (`0x8000000000000200`).

#### Modifiche
1. `p[1] = 4098` (`0x1002`): Byte 2..3 $\to$ `02 10`.
2. `p[3] = 4093` (`0x0FFD`): Byte 6..7 $\to$ `FD 0F`.
3. `*(q + 15) = 73` (`0x49`): Byte 15 $\to$ `49`.
4. `p[9] = 16385` (`0x4001`): Byte 18..19 $\to$ `01 40`.

#### Mappa di memoria finale

| Byte | Puntatori | Hex | Binario Esame (LSB $\to$ MSB) | Note |
| :---: | :--- | :---: | :---: | :--- |
| **0** | `a`, `&p[0]`, `&q[0]` | `0x00` | `00000000` | `a[0]` (LSB) |
| **1** | | `0x06` | `01100000` | `a[0]` ($1536/256$) |
| **2** | `&p[1]` | `0x02` | `01000000` | `p[1] = 4098` |
| **3** | | `0x10` | `00001000` | `p[1] = 4098` |
| **4** | `&p[2]` | `0x00` | `00000000` | `a[0]` |
| **5** | | `0x00` | `00000000` | `a[0]` |
| **6** | `&p[3]` | `0xFD` | `10111111` | `p[3] = 4093` |
| **7** | | `0x0F` | `11110000` | `p[3] = 4093` |
| **8** | `a+1`, `&p[4]`, `&q[8]` | `0xFE` | `01111111` | `a[1] = -2` |
| **9** | | `0xFF` | `11111111` | `a[1]` |
| **10** | `p+5`, `&p[5]` | `0xFF` | `11111111` | `a[1]` |
| **11** | | `0xFF` | `11111111` | `a[1]` |
| **12** | `&p[6]` | `0xFF` | `11111111` | `a[1]` |
| **13** | | `0xFF` | `11111111` | `a[1]` |
| **14** | `&p[7]` | `0xFF` | `11111111` | `a[1]` |
| **15** | `q+15`, `&q[15]` | `0x49` | `10010010` | `*(q+15) = 73` |
| **16** | `a+2`, `&p[8]` | `0x00` | `00000000` | `a[2]` (LSB) |
| **17** | | `0x02` | `01000000` | `a[2]` ($+512$) |
| **18** | `&p[9]`, `&q[18]` | `0x01` | `10000000` | `p[9] = 16385` |
| **19** | | `0x40` | `00000010` | `p[9] = 16385` |
| **20** | `&p[10]` | `0x00` | `00000000` | `a[2]` |
| **21** | | `0x00` | `00000000` | `a[2]` |
| **22** | `p+11`, `&p[11]` | `0x00` | `00000000` | `a[2]` |
| **23** | | `0x80` | `00000001` | `a[2]` (`LLONG_MIN` MSB) |

#### Verifica asserzioni
- **A.** `(*(p + 5) - p[4]) % 2`
  - `p[5]` (Byte 10..11) = `0xFFFF` = $-1$.
  - `p[4]` (Byte 8..9) = `0xFFFE` = $-2$.
  - $(-1 - (-2)) \pmod 2 = 1 \pmod 2 = 1$ $\implies$ **VERA (1)**.
- **B.** `(((int)(p + 11) - (int)(a + 2)) + q[18]) % 7`
  - `(int)(p + 11) = 22`, `(int)(a + 2) = 16` $\to 22 - 16 = 6$.
  - `q[18] = 1`.
  - $(6 + 1) \pmod 7 = 0$ $\implies$ **FALSA (0)**.
- **C.** `((&p[9] - &p[2]) + p[8]) % 2`
  - Sottrazione puntatori: `&p[9] - &p[2] = 9 - 2 = 7`.
  - `p[8]` (Byte 16..17) = `0x0200` = $512$.
  - $(7 + 512) \pmod 2 = 519 \pmod 2 = 1$ $\implies$ **VERA (1)**.

---

# Prova d'Esame 30/01/2026

### Esercizio 4: Promozione di tipo in confronto

```c
int i = -1;
unsigned int limit = 200U;

if (i < limit) {
    printf("%d", i);
}
```
`i` (`int`) ha rank inferiore/uguale a `unsigned int`: viene convertito a `unsigned int` assumendo valore `UINT_MAX` ($4294967295\text{U}$).  
Il confronto $4294967295\text{U} < 200\text{U}$ è **falso**, quindi l'`if` non viene eseguito.

---

### Esercizio 7: Mappa di Memoria e Puntatori

```c
long long a[3] = {1537, -67, (LLONG_MAX + 1) + 512};
int *p = (int*) a;
char *q = (char*) a;
p[1] = INT_MAX, p[4] += 2048, q[19] = ~q[19];
```

- `a[0] = 1537` (`0x0000000000000601`) $\to$ Byte 0..7: `01 06 00 00 00 00 00 00`
- `a[1] = -67` (`0xFFFFFFFFFFFFFFBD`) $\to$ Byte 8..15: `BD FF FF FF FF FF FF FF`
- `a[2] = LLONG_MIN + 512` (`0x8000000000000200`) $\to$ Byte 16..23: `00 02 00 00 00 00 00 80`

#### Modifiche
1. `p[1] = INT_MAX` (`0x7FFFFFFF`): Byte 4..7 $\to$ `FF FF FF 7F`.
2. `p[4] += 2048`: `p[4]` (Byte 16..19) parte da $512$ (`0x0200`). Somma $2048$ ($0\text{x}0800$) $\to 2560$ (`0x00000A00`), Byte 16..19: `00 0A 00 00`.
3. `q[19] = ~q[19]`: Byte 19 diventa `0xFF`.

#### Mappa di memoria finale

| Byte | Puntatori | Hex | Binario Esame (LSB $\to$ MSB) | Note |
| :---: | :--- | :---: | :---: | :--- |
| **0** | `a`, `&p[0]`, `&q[0]` | `0x01` | `10000000` | `a[0]` (LSB) |
| **1** | | `0x06` | `01100000` | `a[0]` |
| **2** | | `0x00` | `00000000` | `a[0]` |
| **3** | | `0x00` | `00000000` | `a[0]` |
| **4** | `&p[1]`, `&q[4]` | `0xFF` | `11111111` | `p[1] = INT_MAX` |
| **5** | | `0xFF` | `11111111` | `p[1] = INT_MAX` |
| **6** | | `0xFF` | `11111111` | `p[1] = INT_MAX` |
| **7** | | `0x7F` | `11111110` | `p[1] = INT_MAX` |
| **8** | `a+1`, `&p[2]`, `&q[8]` | `0xBD` | `10111101` | `a[1] = -67` |
| **9** | | `0xFF` | `11111111` | `a[1]` |
| **10** | | `0xFF` | `11111111` | `a[1]` |
| **11** | | `0xFF` | `11111111` | `a[1]` |
| **12** | `&p[3]`, `&q[12]` | `0xFF` | `11111111` | `a[1]` |
| **13** | | `0xFF` | `11111111` | `a[1]` |
| **14** | | `0xFF` | `11111111` | `a[1]` |
| **15** | | `0xFF` | `11111111` | `a[1]` |
| **16** | `a+2`, `&p[4]`, `&q[16]` | `0x00` | `00000000` | `p[4] += 2048` |
| **17** | | `0x0A` | `01010000` | `p[4] += 2048` |
| **18** | | `0x00` | `00000000` | `a[2]` |
| **19** | `&q[19]` | `0xFF` | `11111111` | `q[19] = ~q[19]` |
| **20** | `&p[5]`, `&q[20]` | `0x00` | `00000000` | `a[2]` |
| **21** | | `0x00` | `00000000` | `a[2]` |
| **22** | | `0x00` | `00000000` | `a[2]` |
| **23** | | `0x80` | `00000001` | `a[2]` (`LLONG_MIN` MSB) |

#### Verifica asserzioni
- **A.** `(~(p[3] & p[1])) == p[5]`
  - `p[3] = 0xFFFFFFFF` ($-1$), `p[1] = 0x7FFFFFFF` (`INT_MAX`).
  - `p[3] & p[1] = 0x7FFFFFFF`.
  - `~0x7FFFFFFF = 0x80000000` (`INT_MIN`).
  - `p[5]` (Byte 20..23) = `0x80000000` (`INT_MIN`).
  - `INT_MIN == INT_MIN` $\implies$ **VERA (1)**.
- **B.** `*((long long*)(&p[1])) < *((long long*)(&p[2]))`
  - `&p[1]` legge Byte 4..11 $\to$ bit più significativo (Byte 11) a 1 $\implies$ numero negativo ($pprox -2.8 	imes 10^{11}$).
  - `&p[2]` legge Byte 8..15 $\to -67$.
  - $-2.8 	imes 10^{11} < -67$ $\implies$ **VERA (1)**.
- **C.** `((long long*)(&p[1])) < ((short int*)(&p[2]))`
  - Confronto tra indirizzi: Byte 4 < Byte 8 $\implies$ **VERA (1)**.

---

# Prova d'Esame 13/02/2026

### Esercizio 2: Creazione lista alternata

Creare una nuova lista con elementi alternati da `l1` e `l2` (`e1_l1, e1_l2, e2_l1, e2_l2, ...`).

```c
struct Node* alternate(struct Node* l1, struct Node* l2) {
    struct Node *head = NULL, *tail = NULL;

    while (l1 != NULL && l2 != NULL) {
        // Nodo da l1
        struct Node *n1 = malloc(sizeof(struct Node));
        if (n1 == NULL) return NULL;
        n1->info = l1->info;
        n1->pNext = NULL;
        if (head == NULL) head = tail = n1;
        else { tail->pNext = n1; tail = n1; }
        l1 = l1->pNext;

        // Nodo da l2
        struct Node *n2 = malloc(sizeof(struct Node));
        if (n2 == NULL) return NULL;
        n2->info = l2->info;
        n2->pNext = NULL;
        tail->pNext = n2;
        tail = n2;
        l2 = l2->pNext;
    }
    return head;
}
```

---

# Prova d'Esame 03/06/2026

### Esercizio 3: Sposta nodi dispari in testa (In-Place e Stabile)

Spostare i nodi dispari in testa mantenendo l'ordine relativo sia dei dispari che dei pari, senza allocare/deallocare memoria.

```c
void sposta_dispari_in_testa(void) {
    struct Node *dispH = NULL, *dispT = NULL;
    struct Node *pariH = NULL, *pariT = NULL;
    struct Node *curr = pFirst;

    while (curr != NULL) {
        struct Node *next = curr->pNext;
        curr->pNext = NULL;

        if (curr->info % 2 != 0) { // Dispari: accoda a dispari
            if (dispH == NULL) dispH = dispT = curr;
            else { dispT->pNext = curr; dispT = curr; }
        } else {                   // Pari: accoda a pari
            if (pariH == NULL) pariH = pariT = curr;
            else { pariT->pNext = curr; pariT = curr; }
        }
        curr = next;
    }

    // Concatenazione finale
    if (dispH == NULL) {
        pFirst = pariH;
    } else {
        pFirst = dispH;
        dispT->pNext = pariH;
    }
}
```

---

# Prova d'Esame 22/06/2026

### Esercizio 1: Conversioni e Tracciamento

```c
int x = 0L, i = -2.5L;
char a = (char) 70, b = (char) 70, c = (char) 50;
a = (a * b) / c;
unsigned int limit = 8U;
long n = 30L;
if (i < limit)
    x = limit * n;
printf("%d %d\n", a, i);
```

- `-2.5L` troncato a `int` $\implies i = -2$.
- `(a * b) / c`: promotion a `int` $\to (70 	imes 70) / 50 = 98$, riassegnato a `char a = 98`.
- `i < limit`: `i` convertito a `unsigned int` $\to 4294967294\text{U} < 8\text{U}$ è **falso** (il ramo `if` non viene eseguito).
- **Output:** `98 -2`

---

### Esercizio 2: Tracciamento Ciclo for

```c
int a = 0x14, i = !00, *b = &a;
for (int *p = &i; (a++, (*p)++) ? (++(*p), (a--) - 1) : ((*p) += 3, a - 1); (*p)++) {
    --a;
    printf("%d %d\n", a, *p);
    if (*p > 3) {
        a = (!(!a) && a++) ? 3 : 2;
        break;
    }
    else continue;
}
printf("%d\n", a);
```

- Inizio: `a = 20`, `i = 1`, `p = &i`, `b = &a`.
- **Iterazione 1:**
  - Condizione ternario `(a++, (*p)++)`: `a` diventa 21, `*p` diventa 2 (ritorna 1, vero).
  - Ramo vero `(++(*p), (a--) - 1)`: `*p` diventa 3; `a` torna 20, ritorna 20 (vero).
  - Corpo: `--a` $\to a = 19$. Stampa: `19 3`.
  - `*p > 3` è falso ($3 > 3$). `continue`.
  - Aggiornamento `(*p)++` $\to *p = 4$.
- **Iterazione 2:**
  - Condizione ternario `(a++, (*p)++)`: `a` diventa 20, `*p` diventa 5 (ritorna 4, vero).
  - Ramo vero: `*p` diventa 6; `a` torna 19, ritorna 19 (vero).
  - Corpo: `--a` $\to a = 18$. Stampa: `18 6`.
  - `*p > 3` è vero ($6 > 3$). Ternario `(!(!a) && a++) ? 3 : 2` $\implies a = 3$. `break`.
- Fine ciclo: Stampa `3`. Valore puntato da `b`: `*b = 3`.

**Output:**
```text
19 3
18 6
3
```

---

### Esercizio 3: Cancellazione elemento per posizione (1-based)

```c
void canc_elem(int pos) {
    if (pos < 1 || pFirst == NULL) return;

    if (pos == 1) {
        struct Node *tmp = pFirst;
        pFirst = pFirst->pNext;
        free(tmp);
        return;
    }

    struct Node *prev = pFirst;
    for (int k = 1; k < pos - 1 && prev != NULL; k++)
        prev = prev->pNext;

    if (prev == NULL || prev->pNext == NULL) return;

    struct Node *target = prev->pNext;
    prev->pNext = target->pNext;
    free(target);
}
```

---

### Esercizio 4: Compilazione Modulare e Linkage

```c
/* calc.c */
int totale = 5;
void logga(int totale);

int main(void) {
    int totale = 5;
    do {
        logga(totale);
    } while (totale >= 0);
    return 0;
}
```
```c
/* stampa.c */
#include <stdio.h>
extern int totale;

void logga(int a) {
    static int k = 0;
    printf("%d\n", totale - (a + k));
    k += 5;
}
```

1. **Errori comandi:**
   - `gcc -c stampa.c`: OK (compila solo l'oggetto `stampa.o`).
   - `gcc -o prog calc.c`: **Errore Linker** (`undefined reference to logga`).
   - `gcc -o stampa stampa.c`: **Errore Linker** (`undefined reference to main` e `totale`).
   - `gcc -c calc.c`: OK (`calc.o`).
   - `gcc calc.c stampa.c -o prog`: OK.
2. **Correzione:** Il punto 5 non ha errori.
3. **Tabella Linkage:**
   - `totale` (in `calc.c`): Linkage **esterno** (globale).
   - `logga` (in `stampa.c`): Linkage **esterno** (funzione non statica).
   - `k` (in `stampa.c`): **Nessun linkage** (locale statica con persistenza).
4. **Comportamento a runtime:**  
   In `calc.c` la variabile locale `int totale = 5` oscura la globale e non viene mai modificata nel ciclo $\to$ **ciclo infinito**.  
   `totale` globale vale 5, `a` vale 5, espressione: $5 - (5 + k) = -k$.  
   **Output:** `0, -5, -10, -15, ...` all'infinito.

---

### Esercizio 5: Mappa di Memoria e Puntatori

```c
int a[4] = {5 + 2 * 32, INT_MIN + 21, [2] = 65540, 262144 / 2 + 99};
short int *p = (short*) a;
char *q = (char*) a;
*(q + 3) = -1;
*((short int*)&q[5]) = 257;
```

- `a[0] = 69` (`0x00000045`), `a[1] = INT_MIN + 21` (`0x80000015`), `a[2] = 65540` (`0x00010004`), `a[3] = 131171` (`0x00020063`).
- Modifiche:
  - `*(q + 3) = -1` $\to$ Byte 3 = `0xFF`.
  - `*((short int*)&q[5]) = 257` (`0x0101`) $\to$ Byte 5 = `0x01`, Byte 6 = `0x01`.

#### Mappa di memoria finale

| Byte | Puntatori | Hex | Binario Esame (LSB $\to$ MSB) | Note |
| :---: | :--- | :---: | :---: | :--- |
| **0** | `a`, `&p[0]`, `&q[0]` | `0x45` | `10100010` | `a[0]` (LSB) |
| **1** | | `0x00` | `00000000` | `a[0]` |
| **2** | `&p[1]`, `&q[2]` | `0x00` | `00000000` | `a[0]` |
| **3** | `&q[3]` | `0xFF` | `11111111` | `*(q+3) = -1` |
| **4** | `a+1`, `&p[2]`, `&q[4]` | `0x15` | `10101000` | `a[1]` (LSB) |
| **5** | `&q[5]` | `0x01` | `10000000` | `short @ q[5] = 257` |
| **6** | `&p[3]`, `&q[6]` | `0x01` | `10000000` | `short @ q[5] = 257` |
| **7** | | `0x80` | `00000001` | `a[1]` (`INT_MIN` MSB) |
| **8** | `a+2`, `&p[4]`, `&q[8]` | `0x04` | `00100000` | `a[2]` (LSB) |
| **9** | | `0x00` | `00000000` | `a[2]` |
| **10** | `&p[5]`, `&q[10]` | `0x01` | `10000000` | `a[2]` |
| **11** | | `0x00` | `00000000` | `a[2]` |
| **12** | `a+3`, `&p[6]`, `&q[12]` | `0x63` | `11000110` | `a[3]` (LSB) |
| **13** | | `0x00` | `00000000` | `a[3]` |
| **14** | `&p[7]`, `&q[14]` | `0x02` | `01000000` | `a[3]` |
| **15** | | `0x00` | `00000000` | `a[3]` |

#### Verifica asserzioni
- **A.** `((&a[4] - a) + p[5]) % 2`
  - `&a[4] - a = 4`.
  - `p[5]` (Byte 10..11) = `0x0001` = $1$.
  - $(4 + 1) \pmod 2 = 1$ $\implies$ **VERA (1)**.
- **B.** `(((int)(a + 2) - (int)&q[2]) + q[14]) % 2`
  - `(int)(a + 2) = 8`, `(int)&q[2] = 2` $\to 8 - 2 = 6$.
  - `q[14] = 2`.
  - $(6 + 2) \pmod 2 = 0$ $\implies$ **FALSA (0)**.
- **C.** `((q[12] >> 4) | q[4]) >= 35`
  - `q[12] = 99` (`0x63`) $\gg 4 = 6$.
  - `q[4] = 21` (`0x15`).
  - $6 \mid 21 = 23$.
  - $23 \ge 35$ $\implies$ **FALSA (0)**.

---

# Prova d'Esame 08/07/2026

### Esercizio 1: Espressioni Logiche e Puntatori

```c
int a = 5, *b = &a; // b = 0x7fff54824ff8
int c = !(a -= 2, ((a -= 3) && ++a));
int d = c || (a -= 1, ((a -= 4) || a++));
int e = (d -= 1, (a || d) || (c = a -= 2, ++a));
printf("%d %d %d %d\n", a, c, d, e);
printf("%p %p %lu\n", b, (long *)(short *)b + 2, sizeof(*b));
```

- `c`: `a -= 2` ($a=3$). `a -= 3` ($a=0$, falso) $\to$ cortocircuito su `++a`. `!(0) = 1` $\implies c = 1, a = 0$.
- `d`: `c = 1` (vero) $\to$ cortocircuito dell'`||`. $\implies d = 1, a = 0$.
- `e`: `d -= 1` ($d=0$). `(a || d)` $\to (0 \lor 0) = 0$. Valuta ramo destro: `c = a -= 2` ($a=-2, c=-2$), `++a` ($a=-1$, vero) $\implies e = 1$.
- `(long *)(short *)b + 2`: avanza di $2 	imes \text{sizeof(long)} = 16\text{ byte}$ (`0x10`) $\to \texttt{0x7fff54825008}$.
- `sizeof(*b)` = $\text{sizeof(int)} = 4$.

**Output:**
```text
-1 -2 0 1
0x7fff54824ff8 0x7fff54825008 4
```

---

### Esercizio 2: Array con successione di Fibonacci

```c
#include <stdlib.h>

int* creafib(unsigned int n) {
    int *v = malloc(n * sizeof(int));
    if (v == NULL) return NULL;

    for (unsigned int i = 0; i < n; i++) {
        if (i < 2) v[i] = 1;
        else v[i] = v[i - 1] + v[i - 2];
    }
    return v;
}
```

---

### Esercizio 3: Inserimento ordinato in lista

```c
void inserisci_ordinato(int x) {
    struct Node *nuovo = malloc(sizeof(struct Node));
    if (nuovo == NULL) return;
    nuovo->info = x;

    if (pFirst == NULL || x <= pFirst->info) {
        nuovo->pNext = pFirst;
        pFirst = nuovo;
        return;
    }

    struct Node *prev = pFirst;
    while (prev->pNext != NULL && prev->pNext->info < x)
        prev = prev->pNext;

    nuovo->pNext = prev->pNext;
    prev->pNext = nuovo;
}
```

---

### Esercizio 4: Compilazione Modulare e Linkage

```c
/* main.c */
int val;
int val = 3;
void stampa(int val);

int main(void) {
    extern int val;
    while (val >= 0) {
        stampa(val);
    }
    return 0;
}
```
```c
/* out.c */
#include <stdio.h>
int j = 2;
static int val = 6;

void stampa(int a) {
    a++;
    printf("%d\n", val = val - j);
}
```

1. **Errori comandi:**
   - `gcc -c out.c`: OK.
   - `gcc -o main main.c`: **Errore Linker** (`undefined reference to stampa`).
   - `gcc -o out out.c`: **Errore Linker** (`undefined reference to main`).
   - `gcc -c main.c`: OK.
   - `gcc main.c out.c -o prog`: OK.
2. **Tabella Linkage:**
   - `val` (in `main.c`): Linkage **esterno**.
   - `val` (in `out.c`): Linkage **interno** (`static`).
   - `j` (in `out.c`): Linkage **esterno**.
   - `stampa` (in `out.c`): Linkage **esterno**.
   - `a` (parametro): **Nessun linkage** (locale stack).
3. **Comportamento a runtime:**  
   `val` in `main.c` rimane costantemente 3 (passata per valore ad `a`) $\to$ **ciclo infinito**.  
   `stampa()` decrementa `static int val` in `out.c` di 2 ogni volta (parte da 6).  
   **Output:** `4, 2, 0, -2, -4, ...` all'infinito.

---

### Esercizio 5: Mappa di Memoria e Puntatori

```c
int a[4] = {3 + 2 * 64, INT_MIN + 9, [2] = 131076, 524288 / 4 + 33};
short int *p = (short*) a;
char *q = (char*) a;
*(q + 2) = -1;
*((short int*)&q[9]) = 513;
```

- `a[0] = 131` (`0x00000083`), `a[1] = INT_MIN + 9` (`0x80000009`), `a[2] = 131076` (`0x00020004`), `a[3] = 131105` (`0x00020021`).
- Modifiche:
  - `*(q + 2) = -1` $\to$ Byte 2 = `0xFF`.
  - `*((short int*)&q[9]) = 513` (`0x0201`) $\to$ Byte 9 = `0x01`, Byte 10 = `0x02`.

#### Mappa di memoria finale

|  Byte  | Puntatori                |  Hex   | Binario Esame (LSB $\to$ MSB) | Note                   |
| :----: | :----------------------- | :----: | :---------------------------: | :--------------------- |
| **0**  | `a`, `&p[0]`, `&q[0]`    | `0x83` |          `11000001`           | `a[0]` (LSB)           |
| **1**  |                          | `0x00` |          `00000000`           | `a[0]`                 |
| **2**  | `&p[1]`, `&q[2]`         | `0xFF` |          `11111111`           | `*(q+2) = -1`          |
| **3**  |                          | `0x00` |          `00000000`           | `a[0]`                 |
| **4**  | `a+1`, `&p[2]`, `&q[4]`  | `0x09` |          `10010000`           | `a[1]` (LSB)           |
| **5**  |                          | `0x00` |          `00000000`           | `a[1]`                 |
| **6**  | `&p[3]`, `&q[6]`         | `0x00` |          `00000000`           | `a[1]`                 |
| **7**  |                          | `0x80` |          `00000001`           | `a[1]` (`INT_MIN` MSB) |
| **8**  | `a+2`, `&p[4]`, `&q[8]`  | `0x04` |          `00100000`           | `a[2]` (LSB)           |
| **9**  | `&q[9]`                  | `0x01` |          `10000000`           | `short @ q[9] = 513`   |
| **10** | `&p[5]`, `&q[10]`        | `0x02` |          `01000000`           | `short @ q[9] = 513`   |
| **11** |                          | `0x00` |          `00000000`           | `a[2]`                 |
| **12** | `a+3`, `&p[6]`, `&q[12]` | `0x21` |          `10000100`           | `a[3]` (LSB)           |
| **13** |                          | `0x00` |          `00000000`           | `a[3]`                 |
| **14** | `&p[7]`, `&q[14]`        | `0x02` |          `01000000`           | `a[3]`                 |
| **15** |                          | `0x00` |          `00000000`           | `a[3]`                 |

#### Verifica asserzioni
- **A.** `((&a[3] - a) + p[5]) % 2`
  - `&a[3] - a = 3`.
  - `p[5]` (Byte 10..11) = `0x0002` = $2$.
  - $(3 + 2) \pmod 2 = 1$ $\implies$ **VERA (1)**.
- **B.** `(((int)(a + 3) - (int)&q[6]) + q[10]) % 4`
  - `(int)(a + 3) = 12`, `(int)&q[6] = 6` $\to 12 - 6 = 6$.
  - `q[10] = 2`.
  - $(6 + 2) \pmod 4 = 0$ $\implies$ **FALSA (0)**.
- **C.** `((q[12] >> 2) | q[4]) >= 9`
  - `q[12] = 33` (`0x21`) $\gg 2 = 8$.
  - `q[4] = 9`.
  - $8 \mid 9 = 9$.
  - $9 \ge 9$ $\implies$ **VERA (1)**.

---

# Prova d'Esame 01/09/2026

### Esercizio 1: Espressioni Logiche e Puntatori

```c
int a = 7, *b = &a; // b = 0x7ffee2b4c9ac
int c = ((a -= 4) || a--) && (a -= 2, !a);
int d = !c && (a += 3, ((a -= 1) && ++a));
int e = (c += 1, (d && c) && (d = a + 2, a--));
printf("%d %d %d %d\n", a, c, d, e);
printf("%p %p %lu\n", b, (int *)(char *)b + 3, sizeof(*b));
```

- `c`: `a -= 4` ($a=3$, vero) $\to$ corto su `a--`. Ramo destro: `a -= 2` ($a=1$), `!1 = 0` $\implies c = 0, a = 1$.
- `d`: `!c` (vero). Destra: `a += 3` ($a=4$), `a -= 1` ($a=3$, vero), `++a` ($a=4$) $\implies d = 1, a = 4$.
- `e`: `c += 1` ($c=1$). `(d && c)` ($1$). Destra: `d = a + 2` ($d=6$), `a--` (restituisce 4, $a$ diventa 3) $\implies e = 1, a = 3, d = 6$.
- `(int *)(char *)b + 3`: avanza di $3 	imes 4 = 12\text{ byte}$ (`0x0C`) $\to \texttt{0x7ffee2b4c9b8}$.
- `sizeof(*b)` = $4$.

**Output:**
```text
3 1 6 1
0x7ffee2b4c9ac 0x7ffee2b4c9b8 4
```

---

### Esercizio 2: Array con successione di numeri triangolari

I numeri triangolari sono $T_i = \sum_{k=1}^i k = rac{i(i+1)}{2}$ ($1, 3, 6, 10, 15, 21, \dots$).

```c
#include <stdlib.h>

int* creatriang(unsigned int n) {
    int *v = malloc(n * sizeof(int));
    if (v == NULL) return NULL;

    for (unsigned int i = 0; i < n; i++) {
        if (i == 0) v[i] = 1;
        else v[i] = v[i - 1] + (i + 1);
    }
    return v;
}
```

---

### Esercizio 3: Eliminazione del primo nodo con valore x

```c
void elimina_valore(int x) {
    if (pFirst == NULL) return;

    if (pFirst->info == x) {
        struct Node *tmp = pFirst;
        pFirst = pFirst->pNext;
        free(tmp);
        return;
    }

    struct Node *prev = pFirst;
    while (prev->pNext != NULL && prev->pNext->info != x)
        prev = prev->pNext;

    if (prev->pNext != NULL) {
        struct Node *tmp = prev->pNext;
        prev->pNext = tmp->pNext;
        free(tmp);
    }
}
```

---

### Esercizio 4: Compilazione Modulare e Linkage

```c
/* main.c */
int k;
int k = 5;
void mostra(int k);

int main(void) {
    extern int k;
    while (k > 0) {
        mostra(k);
        k -= 2;
    }
    return 0;
}
```
```c
/* out.c */
#include <stdio.h>
static int k = 10;
int w = 3;

void mostra(int a) {
    a--;
    printf("%d\n", k += w);
}
```

1. **Errori comandi:**
   - `gcc -c main.c`: OK.
   - `gcc -o main main.c`: **Errore Linker** (`undefined reference to mostra`).
   - `gcc main.c out.c -o prog`: OK.
   - `gcc -c out.c`: OK.
   - `gcc -o out out.c`: **Errore Linker** (`undefined reference to main`).
2. **Tabella Linkage:**
   - `k` (in `main.c`): Linkage **esterno**.
   - `k` (in `out.c`): Linkage **interno** (`static`).
   - `w` (in `out.c`): Linkage **esterno**.
   - `mostra` (in `out.c`): Linkage **esterno**.
   - `a` (parametro): **Nessun linkage**.
3. **Comportamento a runtime:**  
   `k` in `main.c` parte da 5 e decrementa di 2 ogni giro ($5 \to 3 \to 1 \to -1$).  
   `k` in `out.c` parte da 10 e incrementa di 3 ogni volta ($10 \to 13 \to 16 \to 19$).  
   Il ciclo esegue 3 iterazioni e **termina**.

**Output:**
```text
13
16
19
```

---

### Esercizio 5: Mappa di Memoria e Puntatori

```c
int a[4] = {5 + 2 * 128, INT_MIN + 17, [2] = 262148, 1048576 / 4 + 65};
short int *p = (short*) a;
char *q = (char*) a;
*(q + 1) = -1;
*((short int*)&q[10]) = 258;
```

- `a[0] = 261` (`0x00000105`), `a[1] = INT_MIN + 17` (`0x80000011`), `a[2] = 262148` (`0x00040004`), `a[3] = 262209` (`0x00040041`).
- Modifiche:
  - `*(q + 1) = -1` $\to$ Byte 1 = `0xFF`.
  - `*((short int*)&q[10]) = 258` (`0x0102`) $\to$ Byte 10 = `0x02`, Byte 11 = `0x01`.

#### Mappa di memoria finale

| Byte | Puntatori | Hex | Binario Esame (LSB $\to$ MSB) | Note |
| :---: | :--- | :---: | :---: | :--- |
| **0** | `a`, `&p[0]`, `&q[0]` | `0x05` | `10100000` | `a[0]` (LSB) |
| **1** | `&q[1]` | `0xFF` | `11111111` | `*(q+1) = -1` |
| **2** | `&p[1]`, `&q[2]` | `0x00` | `00000000` | `a[0]` |
| **3** | `&q[3]` | `0x00` | `00000000` | `a[0]` |
| **4** | `a+1`, `&p[2]`, `&q[4]` | `0x11` | `10001000` | `a[1]` (LSB) |
| **5** | `&q[5]` | `0x00` | `00000000` | `a[1]` |
| **6** | `&p[3]`, `&q[6]` | `0x00` | `00000000` | `a[1]` |
| **7** | `&q[7]` | `0x80` | `00000001` | `a[1]` (`INT_MIN` MSB) |
| **8** | `a+2`, `&p[4]`, `&q[8]` | `0x04` | `00100000` | `a[2]` (LSB) |
| **9** | `&q[9]` | `0x00` | `00000000` | `a[2]` |
| **10** | `&p[5]`, `&q[10]` | `0x02` | `01000000` | `short @ q[10] = 258` |
| **11** | `&q[11]` | `0x01` | `10000000` | `short @ q[10] = 258` |
| **12** | `a+3`, `&p[6]`, `&q[12]` | `0x41` | `10000010` | `a[3]` (LSB) |
| **13** | `&q[13]` | `0x00` | `00000000` | `a[3]` |
| **14** | `&p[7]`, `&q[14]` | `0x04` | `00100000` | `a[3]` |
| **15** | `&q[15]` | `0x00` | `00000000` | `a[3]` |

#### Verifica asserzioni
- **A.** `((&a[2] - a) + p[4]) % 3`
  - `&a[2] - a = 2`.
  - `p[4]` (Byte 8..9) = `0x0004` = $4$.
  - $(2 + 4) \pmod 3 = 0$ $\implies$ **FALSA (0)**.
- **B.** `(((int)(a + 2) - (int)&q[3]) + q[12]) % 4`
  - `(int)(a + 2) = 8`, `(int)&q[3] = 3` $\to 8 - 3 = 5$.
  - `q[12] = 65` (`0x41`).
  - $(5 + 65) \pmod 4 = 70 \pmod 4 = 2$ $\implies$ **VERA (1)**.
- **C.** `((q[8] << 2) | q[10]) <= 18`
  - `q[8] = 4` $\ll 2 = 16$.
  - `q[10] = 2`.
  - $16 \mid 2 = 18$.
  - $18 \le 18$ $\implies$ **VERA (1)**.

---

# Altri Esercizi e Conversioni

### Esercizio 1: Conversioni e Operatore Ternario

```c
double f(float a) {
    return (a - 1);
}

int main(void) {
    unsigned a = 3LL;             // long long -> unsigned int (3)
    int b = -1U;                  // unsigned int (4294967295) -> int (-1)

    // b < a: b convertito a unsigned int (4294967295 < 3 è FALSO)
    // f riceve a = 3.0f -> ritorna 2.0f
    float c = f((b < a) ? b : a); // c = 2.0f
    float d = UINT_MAX + c - 7;   // promosso a float: 4294967295.0 + 2.0 - 7.0 = 4294967290.0
}
```

---

### Esercizio 2: Conversioni di Tipo

```c
long int f(unsigned int a) {
    return (a - 5);
}

int main(void) {
    short x = -10S;               // -10
    unsigned int y = 20U;         // 20
    // (x > y): x promosso a unsigned int (4294967286 > 20 è VERO)
    // f riceve 4294967286U -> ritorna a - 5 = 4294967281 (long int)
    double z = f((x > y) ? x : y);// z = 4294967281.0
    float d = USHRT_MAX + z - 12; // USHRT_MAX (65535) + 4294967281.0 - 12 = 4295032804.0
}
```

---

# Esercizi Extra sulle Liste Concatenate

### Extra 1: Inversione In-Place (`inverti_lista`)

Inverte l'ordine dei nodi aggiornando i puntatori `pNext` senza allocare memoria.

```c
void inverti_lista(void) {
    struct Node *prev = NULL;
    struct Node *curr = pFirst;
    struct Node *next = NULL;

    while (curr != NULL) {
        next = curr->pNext;  // Salva il prossimo
        curr->pNext = prev;  // Inverte la freccia
        prev = curr;         // Avanza prev
        curr = next;         // Avanza curr
    }
    pFirst = prev;           // Nuova testa
}
```

---

### Extra 2: Cancellazione di tutti i nodi con valore target (`cancella_tutti`)

```c
void cancella_tutti(int val) {
    // 1. Elimina eventuali occorrenze consecutive in testa
    while (pFirst != NULL && pFirst->info == val) {
        struct Node *tmp = pFirst;
        pFirst = pFirst->pNext;
        free(tmp);
    }

    if (pFirst == NULL) return;

    // 2. Elimina nel resto della lista
    struct Node *curr = pFirst;
    while (curr->pNext != NULL) {
        if (curr->pNext->info == val) {
            struct Node *target = curr->pNext;
            curr->pNext = target->pNext;
            free(target);
            // Non avanzare curr: il nuovo curr->pNext va verificato
        } else {
            curr = curr->pNext;
        }
    }
}
```

---

### Extra 3: Eliminazione duplicati da lista ordinata (`elimina_duplicati`)

```c
void elimina_duplicati(void) {
    if (pFirst == NULL) return;

    struct Node *curr = pFirst;
    while (curr->pNext != NULL) {
        if (curr->info == curr->pNext->info) {
            struct Node *dup = curr->pNext;
            curr->pNext = dup->pNext;
            free(dup);
        } else {
            curr = curr->pNext;
        }
    }
}
```

---

### Extra 4: Fusione ordinata in-place di due liste (`fondi_liste_ordinate`)

```c
struct Node* fondi_liste_ordinate(struct Node* l1, struct Node* l2) {
    if (l1 == NULL) return l2;
    if (l2 == NULL) return l1;

    struct Node *head = NULL, *tail = NULL;

    // Scegli la testa iniziale
    if (l1->info <= l2->info) {
        head = tail = l1;
        l1 = l1->pNext;
    } else {
        head = tail = l2;
        l2 = l2->pNext;
    }

    // Unisci i nodi
    while (l1 != NULL && l2 != NULL) {
        if (l1->info <= l2->info) {
            tail->pNext = l1;
            tail = l1;
            l1 = l1->pNext;
        } else {
            tail->pNext = l2;
            tail = l2;
            l2 = l2->pNext;
        }
    }

    // Attacca la coda residua
    tail->pNext = (l1 != NULL) ? l1 : l2;

    return head;
}
```
