# Sifat-Sifat Sistem: BIBO, Kausalitas, Memory, dan LTI

## 1. Pendahuluan

Dalam mata kuliah **Sinyal dan Sistem**, suatu sistem menerima sinyal masukan (*input*) dan menghasilkan sinyal keluaran (*output*).

Secara umum:

$$
x(t) \rightarrow \boxed{\text{Sistem}} \rightarrow y(t)
$$

Sistem dapat dituliskan sebagai:

$$
y(t)=T\{x(t)\}
$$

Beberapa sifat penting sistem adalah:

1. **Stability** — kestabilan sistem
2. **Causality** — kausalitas sistem
3. **Memory** — sistem dengan atau tanpa memori
4. **Linearity** — linearitas
5. **Time Invariance** — invariansi terhadap waktu
6. **LTI** — Linear Time-Invariant

---

# 2. BIBO Stability

## 2.1 Pengertian

BIBO merupakan singkatan dari:

> **Bounded Input → Bounded Output**

Sistem dikatakan **BIBO stable** apabila setiap input yang terbatas menghasilkan output yang juga terbatas.

Jika:

$$
|x(t)| \leq M_x < \infty
$$

maka harus berlaku:

$$
|y(t)| \leq M_y < \infty
$$

### Intuisi

Jika input memiliki nilai yang terbatas, sistem tidak boleh menghasilkan output yang menuju tak hingga.

Contoh:

$$
-5 \leq x(t) \leq 5
$$

Jika output:

$$
-10 \leq y(t) \leq 10
$$

maka sistem stabil.

Namun jika:

$$
y(t)\rightarrow\infty
$$

maka sistem tidak stabil.

---

## 2.2 Contoh BIBO Stable

Diberikan:

$$
y(t)=2x(t)
$$

Misalkan:

$$
|x(t)|\leq M
$$

Maka:

$$
|y(t)|=|2x(t)|
$$

$$
|y(t)|\leq2M
$$

Karena $2M$ terbatas, maka sistem:

$$
\boxed{\text{BIBO Stable}}
$$

---

## 2.3 Contoh Tidak Stabil

Diberikan:

$$
y(t)=tx(t)
$$

Gunakan input terbatas:

$$
x(t)=1
$$

Maka:

$$
y(t)=t
$$

Ketika:

$$
t\rightarrow\infty
$$

maka:

$$
y(t)\rightarrow\infty
$$

Jadi sistem:

$$
\boxed{\text{Tidak BIBO Stable}}
$$

---

# 3. BIBO Stability pada Sistem LTI

Untuk sistem LTI kontinu:

$$
y(t)=x(t)*h(t)
$$

atau:

$$
y(t)=
\int_{-\infty}^{\infty}
x(\tau)h(t-\tau)d\tau
$$

Sistem LTI kontinu BIBO stable jika:

$$
\boxed{
\int_{-\infty}^{\infty}|h(t)|dt < \infty
}
$$

Artinya, **impulse response harus absolutely integrable**.

### Sistem LTI Diskrit

Untuk sistem diskrit:

$$
y[n]=x[n]*h[n]
$$

Syarat BIBO stability:

$$
\boxed{
\sum_{n=-\infty}^{\infty}|h[n]|<\infty
}
$$

---

# 4. Causality (Kausalitas)

## 4.1 Pengertian

Sistem disebut **causal** apabila output pada waktu tertentu hanya bergantung pada:

* input saat ini
* input masa lalu

dan tidak bergantung pada input masa depan.

Secara sederhana:

$$
\boxed{
\text{Output saat ini tidak membutuhkan input masa depan}
}
$$

---

## 4.2 Contoh Sistem Causal

Diberikan:

$$
y(t)=x(t)+x(t-1)
$$

Sistem membutuhkan:

* $x(t)$ → input saat ini
* $x(t-1)$ → input masa lalu

Tidak terdapat input masa depan.

Maka:

$$
\boxed{\text{Causal}}
$$

---

## 4.3 Contoh Sistem Non-Causal

Diberikan:

$$
y(t)=x(t+1)
$$

Output pada waktu $t$ membutuhkan:

$$
x(t+1)
$$

yang merupakan input masa depan.

Maka:

$$
\boxed{\text{Non-Causal}}
$$

---

## 4.4 Contoh dengan Integral

Diberikan:

$$
y(t)=
\int_{-\infty}^{t}x(\tau)d\tau
$$

Integral hanya menggunakan:

$$
\tau\leq t
$$

Sehingga sistem causal.

Sebaliknya:

$$
y(t)=
\int_t^{t+1}x(\tau)d\tau
$$

membutuhkan input masa depan.

Maka sistem non-causal.

---

# 5. Causality pada Sistem LTI

Untuk sistem LTI kontinu:

$$
y(t)=x(t)*h(t)
$$

Sistem LTI causal jika:

$$
\boxed{
h(t)=0,\quad t<0
}
$$

Untuk sistem diskrit:

$$
\boxed{
h[n]=0,\quad n<0
}
$$

### Contoh

Diberikan:

$$
h(t)=e^{-t}u(t)
$$

Karena:

$$
u(t)=0,\quad t<0
$$

maka:

$$
h(t)=0,\quad t<0
$$

Sehingga sistem causal.

---

# 6. Memory

## 6.1 Pengertian

Sistem disebut **memoryless** apabila output pada waktu tertentu hanya bergantung pada input pada waktu yang sama.

Untuk sistem kontinu:

$$
y(t)=f(x(t))
$$

Untuk sistem diskrit:

$$
y[n]=f(x[n])
$$

---

## 6.2 Contoh Memoryless

Diberikan:

$$
y(t)=3x(t)
$$

Output hanya bergantung pada $x(t)$.

Maka:

$$
\boxed{\text{Memoryless}}
$$

Contoh lainnya:

$$
y[n]=x^2[n]
$$

juga merupakan sistem memoryless.

---

# 7. Sistem dengan Memory

Sistem mempunyai **memory** apabila output membutuhkan nilai input selain pada waktu sekarang.

### Contoh 1

$$
y(t)=x(t-2)
$$

Membutuhkan input masa lalu.

Maka:

$$
\boxed{\text{With Memory}}
$$

### Contoh 2

$$
y[n]=x[n]+x[n-1]
$$

Membutuhkan:

$$
x[n]
$$

dan:

$$
x[n-1]
$$

Maka sistem mempunyai memory.

### Contoh 3

$$
y(t)=
\int_{-\infty}^{t}x(\tau)d\tau
$$

Sistem membutuhkan nilai input sebelumnya.

Maka sistem mempunyai memory.

---

# 8. Cara Cepat Menentukan Memory

Jika sistem hanya menggunakan:

$$
x(t)
$$

maka:

$$
\boxed{\text{Memoryless}}
$$

Jika terdapat:

$$
x(t-1)
$$

$$
x(t+1)
$$

atau operasi seperti integral dan delay, maka sistem memiliki memory.

> **Catatan:** Diferensiasi $dx(t)/dt$ juga dikategorikan sebagai sistem dengan memory dalam definisi sistem yang ketat karena nilai turunan di suatu titik bergantung pada perilaku sinyal di sekitar titik tersebut.

---

# 9. Linearity

Sistem disebut **linear** jika memenuhi prinsip **superposition**.

Prinsip superposisi terdiri dari:

1. **Homogeneity**
2. **Additivity**

Secara umum:

$$
\boxed{
T\{ax_1(t)+bx_2(t)\}
=
aT\{x_1(t)\}+bT\{x_2(t)\}
}
$$

---

## 9.1 Homogeneity

Jika:

$$
x(t)\rightarrow y(t)
$$

maka:

$$
ax(t)\rightarrow ay(t)
$$

---

## 9.2 Additivity

Jika:

$$
x_1(t)\rightarrow y_1(t)
$$

dan:

$$
x_2(t)\rightarrow y_2(t)
$$

maka:

$$
x_1(t)+x_2(t)
\rightarrow
y_1(t)+y_2(t)
$$

---

## 9.3 Contoh Sistem Linear

Diberikan:

$$
y(t)=3x(t)
$$

Maka:

$$
T\{ax_1+bx_2\}
=
3(ax_1+bx_2)
$$

$$
=3ax_1+3bx_2
$$

$$
=a(3x_1)+b(3x_2)
$$

Maka sistem linear.

---

## 9.4 Contoh Sistem Nonlinear

Diberikan:

$$
y(t)=x^2(t)
$$

Dengan:

$$
x(t)=ax_1(t)+bx_2(t)
$$

maka:

$$
y(t)
=
[ax_1+bx_2]^2
$$

$$
=
a^2x_1^2+2abx_1x_2+b^2x_2^2
$$

Tidak sama dengan:

$$
ax_1^2+bx_2^2
$$

Maka sistem:

$$
\boxed{\text{Nonlinear}}
$$

---

# 10. Time Invariance

Sistem disebut **time-invariant** apabila pergeseran waktu pada input hanya menyebabkan pergeseran waktu yang sama pada output.

Misalkan:

$$
x(t)\rightarrow y(t)
$$

Jika input digeser:

$$
x(t-t_0)
$$

maka output harus menjadi:

$$
y(t-t_0)
$$

Secara matematis:

$$
\boxed{
T\{x(t-t_0)\}=y(t-t_0)
}
$$

---

## 10.1 Contoh Time-Invariant

Diberikan:

$$
y(t)=2x(t)
$$

Jika input digeser:

$$
x(t-t_0)
$$

maka:

$$
y_1(t)=2x(t-t_0)
$$

Output awal:

$$
y(t)=2x(t)
$$

Jika digeser:

$$
y(t-t_0)=2x(t-t_0)
$$

Karena:

$$
y_1(t)=y(t-t_0)
$$

maka sistem time-invariant.

---

## 10.2 Contoh Time-Varying

Diberikan:

$$
y(t)=tx(t)
$$

Input digeser:

$$
x(t-t_0)
$$

maka:

$$
y_1(t)=tx(t-t_0)
$$

Output awal yang digeser:

$$
y(t-t_0)
=
(t-t_0)x(t-t_0)
$$

Karena:

$$
tx(t-t_0)
\neq
(t-t_0)x(t-t_0)
$$

maka sistem:

$$
\boxed{\text{Time-Varying}}
$$

---

# 11. LTI System

LTI adalah singkatan dari:

> **Linear Time-Invariant**

Sistem LTI memiliki dua sifat:

1. **Linear**
2. **Time-Invariant**

Dengan demikian:

$$
\boxed{
LTI = Linear + Time\ Invariant
}
$$

Sistem LTI sangat penting dalam analisis sinyal dan sistem karena karakteristik sistem dapat direpresentasikan menggunakan **impulse response**.

---

# 12. Impulse Response

Impulse response adalah output sistem ketika input yang diberikan berupa impulse.

Untuk sistem kontinu:

$$
x(t)=\delta(t)
$$

maka:

$$
y(t)=h(t)
$$

Sehingga:

$$
\boxed{
h(t)=T\{\delta(t)\}
}
$$

Untuk sistem diskrit:

$$
\boxed{
h[n]=T\{\delta[n]\}
}
$$

---

# 13. Konvolusi pada Sistem LTI

Salah satu sifat penting sistem LTI adalah output dapat diperoleh melalui operasi **konvolusi**.

Untuk sistem kontinu:

$$
\boxed{
y(t)=x(t)*h(t)
}
$$

atau:

$$
\boxed{
y(t)=
\int_{-\infty}^{\infty}
x(\tau)h(t-\tau)d\tau
}
$$

Untuk sistem diskrit:

$$
\boxed{
y[n]=
\sum_{k=-\infty}^{\infty}
x[k]h[n-k]
}
$$

Dengan demikian:

$$
\boxed{
Input + Impulse\ Response
\rightarrow Output
}
$$

---

# 14. Contoh Analisis Sistem

Diberikan:

$$
\boxed{
y(t)=2x(t)+x(t-1)
}
$$

## 14.1 Linearity

Uji:

$$
T\{ax_1+bx_2\}
$$

Hasilnya:

$$
2(ax_1+bx_2)
+
(ax_1(t-1)+bx_2(t-1))
$$

$$
=
a[2x_1+x_1(t-1)]
+
b[2x_2+x_2(t-1)]
$$

Maka sistem:

$$
\boxed{\text{Linear}}
$$

---

## 14.2 Time Invariance

Input digeser:

$$
x(t-t_0)
$$

Output:

$$
y_1(t)
=
2x(t-t_0)+x(t-t_0-1)
$$

Output awal digeser:

$$
y(t-t_0)
=
2x(t-t_0)+x(t-t_0-1)
$$

Karena:

$$
y_1(t)=y(t-t_0)
$$

maka sistem:

$$
\boxed{\text{Time-Invariant}}
$$

---

## 14.3 Causality

Sistem membutuhkan:

$$
x(t)
$$

dan:

$$
x(t-1)
$$

Keduanya adalah input sekarang dan masa lalu.

Maka:

$$
\boxed{\text{Causal}}
$$

---

## 14.4 Memory

Karena terdapat:

$$
x(t-1)
$$

maka sistem membutuhkan input masa lalu.

Maka:

$$
\boxed{\text{With Memory}}
$$

---

## 14.5 Kesimpulan

| Sifat          | Hasil                               |
| -------------- | ----------------------------------- |
| Linear         | Ya                                  |
| Time-Invariant | Ya                                  |
| LTI            | Ya                                  |
| Causal         | Ya                                  |
| Memoryless     | Tidak                               |
| BIBO           | Perlu dianalisis berdasarkan $h(t)$ |

---

# 15. Contoh Analisis Kedua

Diberikan:

$$
\boxed{
y(t)=tx(t)
}
$$

| Sifat          | Hasil | Alasan                       |
| -------------- | ----- | ---------------------------- |
| Linear         | Ya    | Memenuhi superposisi         |
| Time-Invariant | Tidak | Mengandung $t$               |
| LTI            | Tidak | Tidak time-invariant         |
| Causal         | Ya    | Hanya menggunakan $x(t)$     |
| Memoryless     | Ya    | Hanya bergantung pada $x(t)$ |

---

# 16. Contoh Analisis Ketiga

Diberikan:

$$
\boxed{
y(t)=x(t+2)
}
$$

| Sifat          | Hasil | Alasan                                          |
| -------------- | ----- | ----------------------------------------------- |
| Linear         | Ya    | Memenuhi superposisi                            |
| Time-Invariant | Ya    | Pergeseran input menghasilkan pergeseran output |
| LTI            | Ya    | Linear dan time-invariant                       |
| Causal         | Tidak | Membutuhkan input masa depan                    |
| Memoryless     | Tidak | Menggunakan $x(t+2)$                            |

---

# 17. Ringkasan Konsep

| Sifat              | Pertanyaan                                            |
| ------------------ | ----------------------------------------------------- |
| **BIBO Stability** | Apakah input terbatas menghasilkan output terbatas?   |
| **Causality**      | Apakah output membutuhkan input masa depan?           |
| **Memory**         | Apakah output membutuhkan input selain saat sekarang? |
| **Linearity**      | Apakah sistem memenuhi superposisi?                   |
| **Time-Invariant** | Apakah sistem tidak berubah ketika waktu digeser?     |
| **LTI**            | Apakah sistem linear dan time-invariant?              |

---

# 18. Cara Cepat Menganalisis Sistem

Diberikan:

$$
y(t)=T\{x(t)\}
$$

Gunakan langkah berikut.

### Langkah 1 — Cek Memory

Apakah output hanya menggunakan:

$$
x(t)
$$

Jika ya → **Memoryless**

Jika menggunakan $x(t-1)$, $x(t+1)$, integral, delay, dan sebagainya → **With Memory**

---

### Langkah 2 — Cek Causality

Apakah terdapat input masa depan?

Contoh:

$$
x(t+a),\quad a>0
$$

Jika ada → **Non-Causal**

Jika tidak → **Causal**

---

### Langkah 3 — Cek Linearity

Uji:

$$
T\{ax_1+bx_2\}
$$

Bandingkan dengan:

$$
aT\{x_1\}+bT\{x_2\}
$$

Jika sama → **Linear**

Jika berbeda → **Nonlinear**

---

### Langkah 4 — Cek Time Invariance

Bandingkan:

$$
T\{x(t-t_0)\}
$$

dengan:

$$
y(t-t_0)
$$

Jika sama → **Time-Invariant**

Jika berbeda → **Time-Varying**

---

### Langkah 5 — Jika LTI

Cari impulse response:

$$
h(t)=T\{\delta(t)\}
$$

Kemudian gunakan:

$$
y(t)=x(t)*h(t)
$$

---

# 19. Peta Konsep

```text
                         SISTEM
                            |
       +--------------------+--------------------+
       |                    |                    |
   Stability            Causality             Memory
       |                    |                    |
      BIBO             Causal /              Memoryless /
                       Non-Causal               Memory
       |
       |
   +---+-------------------+
   |                       |
Linearity            Time Invariance
   |                       |
   +-----------+-----------+
               |
              LTI
               |
               v
        Impulse Response
               |
               v
           h(t) / h[n]
               |
               v
          Konvolusi
               |
               v
           y(t) / y[n]
```

# 20. Inti yang Harus Diingat

> **BIBO** → *Bounded Input menghasilkan Bounded Output.*

> **Causal** → *Tidak menggunakan input masa depan.*

> **Memoryless** → *Output hanya bergantung pada input saat ini.*

> **Linear** → *Memenuhi prinsip superposisi.*

> **Time-Invariant** → *Pergeseran input menghasilkan pergeseran output yang sama.*

> **LTI** → *Linear + Time-Invariant.*

> **LTI → Konvolusi**

$$
\boxed{
y(t)=x(t)*h(t)
}
$$

Untuk sistem LTI kontinu:

$$
\boxed{
\text{BIBO Stable}
\iff
\int_{-\infty}^{\infty}|h(t)|dt<\infty
}
$$

dan:

$$
\boxed{
\text{Causal}
\iff
h(t)=0,\quad t<0
}
$$
