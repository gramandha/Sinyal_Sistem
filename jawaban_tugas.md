# Pembahasan Konvolusi dan Sifat Sistem

## Soal 1 — Konvolusi Sinyal Diskrit

Diketahui:

$$
x[n]=\{4,2,3,1,2\}
$$

$$
h[n]=\{1,2\}
$$

Diasumsikan kedua sinyal dimulai dari \(n=0\).

### 1. Konvolusi

Rumus konvolusi diskrit:

$$
y[n]=x[n]*h[n]
$$

$$
y[n]=\sum_{k=-\infty}^{\infty}x[k]h[n-k]
$$

Hasil konvolusi:

$$
\boxed{y[n]=\{4,10,7,7,4,4\}}
$$

### Perhitungan

| \(n\) | Perhitungan   | \(y[n]\) |
| ----: | ------------- | -------: |
|     0 | \(4(1)\)      |        4 |
|     1 | \(4(2)+2(1)\) |       10 |
|     2 | \(2(2)+3(1)\) |        7 |
|     3 | \(3(2)+1(1)\) |        7 |
|     4 | \(1(2)+2(1)\) |        4 |
|     5 | \(2(2)\)      |        4 |

Jadi:

$$
\boxed{y[n]=\{4,10,7,7,4,4\}}
$$

### Grafik Sederhana

```text
x[n]

4 | ●
3 |     ●
2 |   ●       ●
1 |         ●
0 +-------------------
    0 1 2 3 4

h[n]

2 |     ●
1 | ●
0 +-------------
    0 1

y[n]

10|    ●
 9|
 8|
 7|        ●  ●
 6|
 5|
 4| ●              ●  ●
 3|
 2|
 1|
 0+-------------------------
    0  1  2  3  4  5
```

### 2. Sifat Sistem

Jika sistem didefinisikan menggunakan:

$$
y[n]=x[n]*h[n]
$$

maka sistem tersebut merupakan sistem **LTI (Linear Time-Invariant)**.

#### Linear

Sistem linear memenuhi prinsip superposisi:

$$
T\{ax_1[n]+bx_2[n]\}
=
aT\{x_1[n]\}+bT\{x_2[n]\}
$$

Karena konvolusi memenuhi sifat linear, maka:

$$
\boxed{\text{Linear}}
$$

#### Time Invariant

Untuk sistem LTI:

$$
x[n]\rightarrow y[n]
$$

Jika input digeser:

$$
x[n-n_0]
$$

maka output juga bergeser:

$$
y[n-n_0]
$$

Sehingga:

$$
\boxed{\text{Time Invariant}}
$$

#### LTI

Karena sistem linear dan time invariant:

$$
\boxed{\text{LTI}}
$$

#### Causal

Sistem LTI causal jika:

$$
h[n]=0,\qquad n<0
$$

Karena:

$$
h[n]=\{1,2\}
$$

dimulai dari \(n=0\), maka:

$$
\boxed{\text{Causal}}
$$

#### Memory

Output tidak hanya bergantung pada input saat ini, tetapi juga input sebelumnya.

Contohnya:

$$
y[n]=x[n]+2x[n-1]
$$

Terdapat \(x[n-1]\), sehingga sistem mempunyai memory.

$$
\boxed{\text{Dengan Memory}}
$$

#### BIBO Stability

Sistem LTI diskrit stabil BIBO jika:

$$
\sum_{n=-\infty}^{\infty}|h[n]|<\infty
$$

Untuk:

$$
h[n]=\{1,2\}
$$

diperoleh:

$$
|1|+|2|=3
$$

Karena:

$$
3<\infty
$$

maka:

$$
\boxed{\text{BIBO Stable}}
$$

### Kesimpulan Soal 1

| Sifat          | Hasil |
| -------------- | ----- |
| Linear         | Ya    |
| Time Invariant | Ya    |
| LTI            | Ya    |
| Causal         | Ya    |
| Memory         | Ya    |
| BIBO Stable    | Ya    |

---

# Soal 2 — Konvolusi Diskrit

Diketahui:

$$
x[n]=
\begin{cases}
1, & 0\leq n\leq2\\
0, & \text{lainnya}
\end{cases}
$$

Sehingga:

$$
x[n]=\{1,1,1\}
$$

Sedangkan:

$$
h[n]=
\begin{cases}
2, & 1\leq n\leq2\\
0, & \text{lainnya}
\end{cases}
$$

Jika ditulis mulai dari \(n=0\):

$$
h[n]=\{0,2,2\}
$$

## 1. Konvolusi

Rumus:

$$
y[n]=\sum_k x[k]h[n-k]
$$

Hasilnya:

$$
\boxed{y[n]=\{0,2,4,4,2\}}
$$

### Perhitungan

| \(n\) | Perhitungan        | \(y[n]\) |
| ----: | ------------------ | -------: |
|     0 | \(1(0)\)           |        0 |
|     1 | \(1(2)+1(0)\)      |        2 |
|     2 | \(1(2)+1(2)+1(0)\) |        4 |
|     3 | \(1(0)+1(2)+1(2)\) |        4 |
|     4 | \(1(0)+1(0)+1(2)\) |        2 |

Jadi:

$$
\boxed{y[n]=\{0,2,4,4,2\}}
$$

## 2. Sifat Sistem

### Linear

Konvolusi merupakan operasi linear.

$$
\boxed{\text{Linear}}
$$

### Time Invariant

Konvolusi tidak berubah sifatnya terhadap pergeseran waktu.

$$
\boxed{\text{Time Invariant}}
$$

### LTI

Karena linear dan time invariant:

$$
\boxed{\text{LTI}}
$$

### Causal

Karena:

$$
h[n]=0,\qquad n<0
$$

maka:

$$
\boxed{\text{Causal}}
$$

### Memory

Output bergantung pada lebih dari satu nilai input.

$$
\boxed{\text{Dengan Memory}}
$$

### BIBO Stability

$$
\sum |h[n]|=0+2+2=4
$$

Karena:

$$
4<\infty
$$

maka:

$$
\boxed{\text{BIBO Stable}}
$$

### Kesimpulan Soal 2

| Sifat          | Hasil |
| -------------- | ----- |
| Linear         | Ya    |
| Time Invariant | Ya    |
| LTI            | Ya    |
| Causal         | Ya    |
| Memory         | Ya    |
| BIBO Stable    | Ya    |

---

# Soal 3 — Konvolusi Sinyal Kontinu

Sebagai contoh digunakan:

$$
x(t)=
\begin{cases}
1, & 0\leq t\leq2\\
0, & \text{lainnya}
\end{cases}
$$

dan:

$$
h(t)=
\begin{cases}
1, & 0\leq t\leq1\\
0, & \text{lainnya}
\end{cases}
$$

## 1. Rumus Konvolusi

Konvolusi kontinu:

$$
y(t)=x(t)*h(t)
$$

$$
\boxed{
y(t)=\int_{-\infty}^{\infty}x(\tau)h(t-\tau)d\tau
}
$$

Konsepnya adalah:

1. Balik salah satu sinyal.
2. Geser sinyal.
3. Tentukan daerah overlap.
4. Kalikan kedua sinyal.
5. Integralkan daerah overlap.

---

## 2. Menentukan Daerah Overlap

Sinyal \(x(t)\) aktif pada:

$$
0\leq t\leq2
$$

Sinyal \(h(t)\) aktif pada:

$$
0\leq t\leq1
$$

Ketika digeser, panjang daerah overlap berubah.

### Interval 1 — \(t<0\)

Tidak terjadi overlap.

$$
\boxed{y(t)=0}
$$

### Interval 2 — \(0\leq t<1\)

Panjang overlap:

$$
t
$$

Karena amplitudo kedua sinyal adalah 1:

$$
y(t)=t
$$

### Interval 3 — \(1\leq t<2\)

Seluruh \(h(t)\) berada di dalam \(x(t)\).

Panjang overlap:

$$
1
$$

Sehingga:

$$
y(t)=1
$$

### Interval 4 — \(2\leq t<3\)

Overlap mulai berkurang.

Panjang overlap:

$$
3-t
$$

Sehingga:

$$
y(t)=3-t
$$

### Interval 5 — \(t\geq3\)

Tidak terjadi overlap.

$$
y(t)=0
$$

## 3. Hasil Konvolusi

$$
\boxed{
y(t)=
\begin{cases}
0, & t<0\\
t, & 0\leq t<1\\
1, & 1\leq t<2\\
3-t, & 2\leq t<3\\
0, & t\geq3
\end{cases}
}
$$

Bentuknya adalah **trapesium**.

```text
y(t)

1 |       ┌─────────┐
  |      /           \
  |     /             \
0 |────┘               └────
      0    1    2    3
```

---

# Soal 4 — Konvolusi Sinyal Kontinu

Diketahui:

$$
h(t)=
\begin{cases}
4, & 1\leq t\leq3\\
0, & \text{lainnya}
\end{cases}
$$

dan:

$$
x(t)=
\begin{cases}
2, & 0\leq t\leq2\\
0, & \text{lainnya}
\end{cases}
$$

> **Catatan:** Karena sinyalnya kontinu, notasi yang tepat adalah \(x(t)\), \(h(t)\), dan \(y(t)\), bukan \(x[n]\), \(h[n]\), dan \(y[n]\).

## 1. Rumus Konvolusi

$$
y(t)=x(t)*h(t)
$$

$$
y(t)=
\int_{-\infty}^{\infty}
x(\tau)h(t-\tau)d\tau
$$

Kedua sinyal mempunyai amplitudo:

$$
A_x=2
$$

$$
A_h=4
$$

Sehingga hasil perkalian amplitudo:

$$
A_xA_h=2\times4=8
$$

---

## 2. Menentukan Daerah Overlap

Sinyal \(x(t)\) aktif pada:

$$
0\leq t\leq2
$$

Sinyal \(h(t)\) aktif pada:

$$
1\leq t\leq3
$$

Support hasil konvolusi berada dari:

$$
0+1=1
$$

hingga:

$$
2+3=5
$$

Jadi:

$$
1\leq t\leq5
$$

---

## 3. Interval Pertama

Untuk:

$$
1\leq t\leq3
$$

panjang overlap bertambah dari 0 hingga 2.

Panjang overlap:

$$
L=t-1
$$

Karena amplitudo hasil perkalian adalah 8:

$$
y(t)=8(t-1)
$$

---

## 4. Interval Kedua

Untuk:

$$
3\leq t\leq5
$$

panjang overlap mulai berkurang.

Panjang overlap:

$$
L=5-t
$$

Maka:

$$
y(t)=8(5-t)
$$

---

## 5. Hasil Konvolusi

$$
\boxed{
y(t)=
\begin{cases}
0, & t<1\\
8(t-1), & 1\leq t\leq3\\
8(5-t), & 3\leq t\leq5\\
0, & t>5
\end{cases}
}
$$

Pada \(t=3\):

$$
y(3)=8(3-1)
$$

$$
\boxed{y(3)=16}
$$

Jadi nilai maksimum konvolusi adalah:

$$
\boxed{y_{\max}=16}
$$

### Grafik

```text
x(t)

2 |     ┌──────────┐
  |     │          │
0 |─────┘          └─────
       0          2


h(t)

4 |          ┌──────────┐
  |          │          │
0 |──────────┘          └─────
            1          3


y(t)

16|              ●
  |             / \
  |            /   \
  |           /     \
0 |──────────┘       └────────
             1  3    5
```

Bentuk \(y(t)\) adalah **segitiga**.

---

# Analisis Sifat Sistem Soal 4

## 1. Linear

Sistem yang menggunakan konvolusi:

$$
y(t)=x(t)*h(t)
$$

memenuhi prinsip superposisi.

$$
\boxed{\text{Linear}}
$$

---

## 2. Time Invariant

Jika input digeser:

$$
x(t-t_0)
$$

maka output juga mengalami pergeseran:

$$
y(t-t_0)
$$

Sehingga:

$$
\boxed{\text{Time Invariant}}
$$

---

## 3. LTI

Karena sistem:

* Linear
* Time Invariant

maka:

$$
\boxed{\text{LTI}}
$$

---

## 4. Causal

Sistem LTI kontinu causal jika:

$$
h(t)=0,\qquad t<0
$$

Diketahui:

$$
h(t)=4,\qquad 1\leq t\leq3
$$

dan:

$$
h(t)=0,\qquad t<1
$$

Maka:

$$
\boxed{\text{Causal}}
$$

---

## 5. Memory

Sistem mempunyai memory apabila output bergantung pada input selain \(x(t)\) pada waktu yang sama.

Konvolusi:

$$
y(t)=\int x(\tau)h(t-\tau)d\tau
$$

menggunakan nilai input pada berbagai \(\tau\).

Maka:

$$
\boxed{\text{Dengan Memory}}
$$

---

## 6. BIBO Stability

Sistem LTI kontinu stabil BIBO jika:

$$
\int_{-\infty}^{\infty}|h(t)|dt<\infty
$$

Untuk sistem ini:

$$
h(t)=4,\qquad 1\leq t\leq3
$$

sehingga:

$$
\int_1^3|4|dt
=
4(3-1)
$$

$$
=8
$$

Karena:

$$
8<\infty
$$

maka:

$$
\boxed{\text{BIBO Stable}}
$$

---

# Ringkasan Keseluruhan

| Soal   | Linear | Time Invariant | LTI | Causal | Memory | BIBO Stable |
| ------ | ------ | -------------- | --- | ------ | ------ | ----------- |
| Soal 1 | Ya     | Ya             | Ya  | Ya     | Ya     | Ya          |
| Soal 2 | Ya     | Ya             | Ya  | Ya     | Ya     | Ya          |
| Soal 3 | Ya*    | Ya*            | Ya* | Ya*    | Ya*    | Ya*         |
| Soal 4 | Ya     | Ya             | Ya  | Ya     | Ya     | Ya          |

> **Catatan:** Untuk Soal 3, sifat sistem bergantung pada sistem yang dimaksud. Jika sistem didefinisikan sebagai sistem LTI dengan impulse response \(h(t)\), maka sifat-sifat tersebut dapat dianalisis dari \(h(t)\).

## Rumus Penting

### Konvolusi Diskrit

$$
\boxed{
y[n]=\sum_{k=-\infty}^{\infty}x[k]h[n-k]
}
$$

### Konvolusi Kontinu

$$
\boxed{
y(t)=\int_{-\infty}^{\infty}x(\tau)h(t-\tau)d\tau
}
$$

### Syarat Causal LTI

Diskrit:

$$
\boxed{h[n]=0,\quad n<0}
$$

Kontinu:

$$
\boxed{h(t)=0,\quad t<0}
$$

### Syarat BIBO Stable

Diskrit:

$$
\boxed{
\sum_{n=-\infty}^{\infty}|h[n]|<\infty
}
$$

Kontinu:

$$
\boxed{
\int_{-\infty}^{\infty}|h(t)|dt<\infty
}
$$

### Hubungan LTI

$$
\boxed{
\text{LTI}=\text{Linear}+\text{Time Invariant}
}
$$

dan karakteristik sistem LTI ditentukan oleh **impulse response**:

$$
\boxed{h(t)=T\{\delta(t)\}}
$$

atau:

$$
\boxed{h[n]=T\{\delta[n]\}}
$$

Kemudian output sistem diperoleh melalui konvolusi:

$$
\boxed{y=x*h}
$$
