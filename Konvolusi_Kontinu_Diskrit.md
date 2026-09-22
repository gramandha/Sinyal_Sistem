# Konvolusi Sinyal Kontinu dan Diskrit

## 1. Pendahuluan

Konvolusi merupakan operasi matematika yang digunakan untuk menentukan respons keluaran suatu sistem berdasarkan sinyal masukan dan karakteristik sistem.

Pada sistem **Linear Time-Invariant (LTI)**, output dapat dihitung menggunakan konvolusi antara input dan impulse response.

Secara umum:

$$
y=x*h
$$

Keterangan:

* $x$ : sinyal input
* $h$ : impulse response sistem
* $y$ : sinyal output
* $*$ : operasi konvolusi

Konvolusi dibedakan menjadi:

1. Konvolusi sinyal kontinu.
2. Konvolusi sinyal diskrit.

---

# 2. Konvolusi Sinyal Kontinu

## 2.1 Pengertian

Konvolusi kontinu digunakan pada sinyal yang didefinisikan untuk setiap nilai waktu $t$.

Rumus konvolusi kontinu:

$$
\boxed{
y(t)=x(t)*h(t)
}
$$

Secara matematis:

$$
\boxed{
y(t)=
\int_{-\infty}^{\infty}
x(\tau)h(t-\tau)d\tau
}
$$

Keterangan:

* $t$ : waktu output.
* $\tau$ : variabel integrasi.
* $x(\tau)$ : sinyal input.
* $h(t-\tau)$ : impulse response yang dibalik dan digeser.

## 2.2 Makna Rumus

Rumus:

$$
y(t)=
\int_{-\infty}^{\infty}
x(\tau)h(t-\tau)d\tau
$$

menunjukkan bahwa:

1. Sinyal input $x(\tau)$ dikalikan dengan $h(t-\tau)$.
2. Hasil perkalian diintegralkan terhadap $\tau$.
3. Nilai integral merupakan output sistem pada waktu $t$.

---

# 3. Metode Flip and Shift

Konvolusi kontinu dapat dihitung menggunakan metode **flip and shift**.

## Langkah 1: Tentukan $h(\tau)$

Ambil impulse response sebagai fungsi terhadap variabel $\tau$.

## Langkah 2: Balik Sinyal

Lakukan pembalikan waktu:

$$
h(\tau)\rightarrow h(-\tau)
$$

## Langkah 3: Geser Sinyal

Geser sebesar $t$:

$$
h(-\tau)\rightarrow h(t-\tau)
$$

## Langkah 4: Kalikan

Kalikan kedua sinyal:

$$
x(\tau)h(t-\tau)
$$

## Langkah 5: Integralkan

$$
y(t)=
\int_{-\infty}^{\infty}
x(\tau)h(t-\tau)d\tau
$$

### Ringkasan

$$
\boxed{
\text{Flip}
\rightarrow
\text{Shift}
\rightarrow
\text{Multiply}
\rightarrow
\text{Integrate}
}
$$

---

# 4. Contoh Konvolusi Kontinu

Diberikan impulse response:

$$
h(t) = 
\begin{cases}
4, & 1 \le t \le 3 \\
0, & \text{lainnya}
\end{cases}
$$

dan input:

$$
x(t) = 
\begin{cases}
2, & 0 \le t \le 2 \\
0, & \text{lainnya}
\end{cases}
$$

Tentukan:

$$
y(t)=x(t)*h(t)
$$

## 4.1 Tuliskan Rumus

$$
y(t)=
\int_{-\infty}^{\infty}
x(\tau)h(t-\tau)d\tau
$$

Karena $x(\tau)=1$ pada $0<\tau<3$, maka:

$$
0<\tau<3
$$

Sementara itu, $h(t-\tau)=1$ jika:

$$
0<t-\tau<2
$$

Sehingga:

$$
t-2<\tau<t
$$

Jadi, kita mencari daerah overlap antara:

$$
0<\tau<3
$$

dan:

$$
t-2<\tau<t
$$

## 4.2 Menentukan Batas Integral

Batas integrasi ditentukan oleh daerah yang saling overlap.

### Kasus 1: $t<0$

Tidak ada overlap.

$$
y(t)=0
$$

### Kasus 2: $0<t<2$

Daerah overlap memiliki panjang $t$.

$$
y(t)=
\int_0^t1\,d\tau
$$

$$
y(t)=t
$$

### Kasus 3: $2<t<3$

Daerah overlap memiliki panjang $2$.

$$
y(t)=
\int_{t-2}^{t}1\,d\tau
$$

$$
y(t)=2
$$

### Kasus 4: $3<t<5$

Daerah overlap memiliki panjang $5-t$.

$$
y(t)=
\int_{t-2}^{3}1\,d\tau
$$

$$
y(t)=5-t
$$

### Kasus 5: $t>5$

Tidak ada overlap.

$$
y(t)=0
$$

## 4.3 Hasil Akhir

$$
\boxed{
y(t)=
\begin{cases}
0, & t<0\\
t, & 0\leq t<2\\
2, & 2\leq t<3\\
5-t, & 3\leq t<5\\
0, & t\geq5
\end{cases}
}
$$

Bentuk output berupa trapesium.

```text
y(t)

  2 |       ┌──────────┐
    |      /            \
    |     /              \
    |    /                \
  0 |───┘                  └──────
       0    2      3       5      t
```

---

# 5. Konvolusi Sinyal Diskrit

## 5.1 Pengertian

Konvolusi diskrit digunakan untuk sinyal yang didefinisikan pada indeks diskrit $n$.

Rumus konvolusi diskrit:

$$
\boxed{
y[n]=x[n]*h[n]
}
$$

Secara matematis:

$$
\boxed{
y[n]=
\sum_{k=-\infty}^{\infty}
x[k]h[n-k]
}
$$

Keterangan:

* $n$ : indeks output.
* $k$ : indeks penjumlahan.
* $x[k]$ : sinyal input.
* $h[n-k]$ : impulse response yang dibalik dan digeser.

## 5.2 Perbedaan dengan Konvolusi Kontinu

| Kontinu     | Diskrit     |
| ----------- | ----------- |
| $y(t)$      | $y[n]$      |
| Integral    | Penjumlahan |
| $\tau$      | $k$         |
| $h(t-\tau)$ | $h[n-k]$    |

---

# 6. Metode Flip and Shift Diskrit

Langkah-langkah konvolusi diskrit:

1. Tentukan $x[k]$ dan $h[k]$.
2. Balik impulse response menjadi $h[-k]$.
3. Geser menjadi $h[n-k]$.
4. Kalikan $x[k]h[n-k]$.
5. Jumlahkan seluruh hasil perkalian.

$$
\boxed{
\text{Flip}
\rightarrow
\text{Shift}
\rightarrow
\text{Multiply}
\rightarrow
\text{Sum}
}
$$

---

# 7. Contoh Konvolusi Diskrit

Diberikan:

$$
x[n]=[1,2,3]
$$

dan:

$$
h[n]=[1,1]
$$

Tentukan:

$$
y[n]=x[n]*h[n]
$$

## 7.1 Rumus

$$
y[n]=
\sum_kx[k]h[n-k]
$$

## 7.2 Perhitungan

### Untuk $n=0$

$$
y[0]=x[0]h[0]
$$

$$
y[0]=1(1)=1
$$

### Untuk $n=1$

$$
y[1]=x[0]h[1]+x[1]h[0]
$$

$$
y[1]=1(1)+2(1)=3
$$

### Untuk $n=2$

$$
y[2]=x[1]h[1]+x[2]h[0]
$$

$$
y[2]=2(1)+3(1)=5
$$

### Untuk $n=3$

$$
y[3]=x[2]h[1]
$$

$$
y[3]=3(1)=3
$$

## 7.3 Hasil Akhir

$$
\boxed{
y[n]=[1,3,5,3]
}
$$

---

# 8. Konvolusi Diskrit Menggunakan Tabel

Konvolusi diskrit dapat dihitung dengan perkalian bergeser.

Diberikan:

$$
x[n]=[1,2,3]
$$

$$
h[n]=[1,1]
$$

Susun perkalian:

```text
          1    2    3
               1    2    3
          ----------------
          1    3    5    3
```

Maka:

$$
y[n]=[1,3,5,3]
$$

---

# 9. Hubungan Konvolusi dengan Sistem LTI

Sistem LTI merupakan sistem yang memenuhi:

1. Linear.
2. Time-Invariant.

Sistem LTI dapat direpresentasikan menggunakan impulse response.

Jika input sistem adalah:

$$
x(t)
$$

dan impulse response:

$$
h(t)
$$

maka output:

$$
\boxed{
y(t)=x(t)*h(t)
}
$$

Untuk sistem diskrit:

$$
\boxed{
y[n]=x[n]*h[n]
}
$$

Dengan demikian:

```text
Input x(t)
     |
     v
  Sistem LTI
     |
     v
Output y(t)

y(t) = x(t) * h(t)
```

---

# 10. Interpretasi Fisik Konvolusi

Konvolusi dapat dipahami sebagai proses menjumlahkan kontribusi seluruh bagian input terhadap output sistem.

Setiap bagian kecil input menghasilkan respons sistem.

Respons tersebut kemudian dijumlahkan untuk mendapatkan output.

Secara sederhana:

$$
\boxed{
\text{Input}
+
\text{Karakteristik Sistem}
\rightarrow
\text{Output}
}
$$

---

# 11. Hubungan Konvolusi dengan Impulse

Sinyal kontinu dapat direpresentasikan menggunakan impulse:

$$
x(t)=
\int_{-\infty}^{\infty}
x(\tau)\delta(t-\tau)d\tau
$$

Untuk sistem LTI:

$$
\delta(t-\tau)
\rightarrow
h(t-\tau)
$$

Maka:

$$
y(t)=
\int_{-\infty}^{\infty}
x(\tau)h(t-\tau)d\tau
$$

Sehingga:

$$
\boxed{
y(t)=x(t)*h(t)
}
$$

Untuk sistem diskrit:

$$
x[n]=
\sum_{k=-\infty}^{\infty}
x[k]\delta[n-k]
$$

Maka:

$$
y[n]=
\sum_{k=-\infty}^{\infty}
x[k]h[n-k]
$$

---

# 12. Sifat-Sifat Konvolusi

## 12.1 Komutatif

$$
\boxed{
x*h=h*x
}
$$

Untuk sistem kontinu:

$$
x(t)*h(t)=h(t)*x(t)
$$

## 12.2 Asosiatif

$$
\boxed{
(x*h)*g=x*(h*g)
}
$$

## 12.3 Distributif

$$
\boxed{
x*(h_1+h_2)
=
x*h_1+x*h_2
}
$$

## 12.4 Konvolusi dengan Impulse

$$
\boxed{
x(t)*\delta(t)=x(t)
}
$$

Untuk diskrit:

$$
\boxed{
x[n]*\delta[n]=x[n]
}
$$

---

# 13. Konvolusi dan Filtering

Konvolusi merupakan dasar proses filtering.

Untuk sistem diskrit:

$$
y[n]=x[n]*h[n]
$$

dengan:

* $x[n]$ : sinyal asli.
* $h[n]$ : koefisien filter.
* $y[n]$ : sinyal hasil filtering.

Contoh filter moving average:

$$
h[n]=\frac{1}{3}[1,1,1]
$$

Maka:

$$
y[n]=
x[n]*
\frac{1}{3}[1,1,1]
$$

Filter moving average menghitung rata-rata beberapa sampel sehingga dapat mengurangi perubahan cepat atau noise.

---

# 14. Perbandingan Konvolusi Kontinu dan Diskrit

| Aspek            | Kontinu                          | Diskrit                    |
| ---------------- | -------------------------------- | -------------------------- |
| Input            | $x(t)$                           | $x[n]$                     |
| Impulse response | $h(t)$                           | $h[n]$                     |
| Output           | $y(t)$                           | $y[n]$                     |
| Operasi          | Integral                         | Penjumlahan                |
| Variabel         | $\tau$                           | $k$                        |
| Rumus            | $\int x(\tau)h(t-\tau)d\tau$     | $\sum x[k]h[n-k]$          |
| Metode           | Flip, shift, multiply, integrate | Flip, shift, multiply, sum |

---

# 15. Ringkasan

Konvolusi merupakan operasi yang digunakan untuk menentukan output sistem berdasarkan input dan impulse response.

### Konvolusi Kontinu

$$
\boxed{
y(t)=
\int_{-\infty}^{\infty}
x(\tau)h(t-\tau)d\tau
}
$$

### Konvolusi Diskrit

$$
\boxed{
y[n]=
\sum_{k=-\infty}^{\infty}
x[k]h[n-k]
}
$$

### Perbedaan Utama

* Sinyal kontinu menggunakan integral.
* Sinyal diskrit menggunakan penjumlahan.
* Keduanya menggunakan konsep flip and shift.
* Pada sistem LTI, konvolusi digunakan untuk menghitung output.

### Inti Konsep

$$\boxed{\text{Konvolusi} = \text{Flip} + \text{Shift} + \text{Perkalian} + \text{Integral atau Penjumlahan}}$$
