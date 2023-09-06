Pilih lebih dari satu : Quiz: Apa tujuan dari Market Basket Analysis?
Apa tujuan dari Market Basket Analysis?
JAWABAN

Untuk menemukan pola unik dari sebuah dataset transaksi
Mengenali pelanggan secara lebih personal
Membuat paket produk yang bisa meningkatkan penjualan
Menyusun produk pada rak atau website yang berhubungan erat
Menemukan jarak terpendek dengan para customer

**Tujuan dari Market Basket Analysis** adalah:

-  Untuk menemukan pola unik dari sebuah dataset transaksi.
-  Membuat paket produk yang bisa meningkatkan penjualan.
-  Menyusun produk pada rak atau website yang berhubungan erat.



```
#Menggunakan library arules
library(arules)

#Membaca transaksi dari file data_transaksi.txt
transaksi <- read.transactions(file="https://storage.googleapis.com/dqlab-dataset/data_transaksi.txt", format="single", sep="\t", cols=c(1,2), skip=1)

#Menampilkan data transaksi dengan print dan inspect 
inspect(transaksi)

#Menghasilkan model Market Basket Analysis
mba <- apriori(transaksi,parameter = list(supp = 0.1, confidence = 0.5))

#Menampilkan paket produk
inspect(subset(mba, lift>1))
```

Kode yang Anda berikan adalah contoh penggunaan library arules dalam bahasa pemrograman R untuk melakukan analisis Market Basket Analysis. Saya akan menjelaskan setiap langkah yang Anda lakukan dalam kode tersebut:

**Menggunakan Library arules**: Anda mengimpor library arules, yang digunakan untuk melakukan analisis aturan asosiasi, termasuk Market Basket Analysis.

**Membaca Transaksi dari File**: Anda membaca data transaksi dari file "data_transaksi.txt" yang tersimpan di lokasi yang diberikan dalam URL. Anda mengatur format file sebagai "single" dan menentukan bahwa kolom 1 dan 2 dari file ini akan digunakan sebagai transaksi. Anda juga melewati baris pertama yang berisi header dengan skip=1.

**Menampilkan Data Transaksi**: Anda menggunakan fungsi inspect untuk menampilkan data transaksi yang telah dibaca. Ini membantu Anda memeriksa apakah data transaksi telah dibaca dengan benar.

**Menghasilkan Model Market Basket Analysis**: Anda membuat model Market Basket Analysis menggunakan fungsi apriori. Anda mengatur parameter supp (support) sebesar 0.1 (10%) dan confidence sebesar 0.5 (50%). Ini berarti Anda hanya akan mempertimbangkan aturan yang memiliki tingkat support minimal 10% dan tingkat confidence minimal 50%.

**Menampilkan Paket Produk**: Anda menggunakan fungsi inspect lagi untuk menampilkan aturan-aturan yang telah dihasilkan oleh model Market Basket Analysis. Anda menggunakan subset untuk hanya menampilkan aturan-aturan yang memiliki nilai "lift" lebih dari 1. Lift adalah salah satu metrik penting dalam Market Basket Analysis yang mengukur sejauh mana dua produk berkaitan satu sama lain.

Dengan demikian, kode ini membantu Anda melakukan analisis Market Basket Analysis pada data transaksi yang telah dibaca, dan menampilkan aturan-aturan asosiasi yang relevan berdasarkan tingkat support, confidence, dan lift yang telah Anda tentukan.



Berikut adalah kode yang setara dalam bahasa pemrograman Python menggunakan library mlxtend untuk melakukan analisis Market Basket Analysis:

```
# Menggunakan library mlxtend
from mlxtend.frequent_patterns import apriori
from mlxtend.frequent_patterns import association_rules

# Membaca transaksi dari file data_transaksi.txt
import pandas as pd
df = pd.read_csv("https://storage.googleapis.com/dqlab-dataset/data_transaksi.txt", sep="\t", header=None, skiprows=1, usecols=[0, 1])

# Menampilkan data transaksi
print(df)

# Menghasilkan model Market Basket Analysis
frequent_itemsets = apriori(df, min_support=0.1, use_colnames=True)
rules = association_rules(frequent_itemsets, metric="lift", min_threshold=1)

# Menampilkan aturan asosiasi
print(rules)
```

Dalam kode Python ini, kita menggunakan library mlxtend untuk melakukan analisis Market Basket Analysis. Kami membaca data transaksi dari file "data_transaksi.txt" menggunakan Pandas, lalu menghasilkan model Market Basket Analysis dengan menghitung itemset yang sering muncul (frequent itemsets) dan aturan asosiasi (association rules) berdasarkan tingkat support dan lift yang telah ditentukan.

```
Parameter specification:
 confidence minval smax arem  aval originalSupport maxtime support minlen
        0.5    0.1    1 none FALSE            TRUE       5     0.1      1
 maxlen target   ext
     10  rules FALSE

Algorithmic control:
 filter tree heap memopt load sort verbose
    0.1 TRUE TRUE  FALSE TRUE    2    TRUE

Absolute minimum support count: 1 

set item appearances ...[0 item(s)] done [0.00s].
set transactions ...[4 item(s), 10 transaction(s)] done [0.00s].
sorting and recoding items ... [4 item(s)] done [0.00s].
creating transaction tree ... done [0.00s].
checking subsets of size 1 2 3 done [0.00s].
writing ... [16 rule(s)] done [0.00s].
creating S4 object  ... done [0.00s].

> #Menampilkan paket produk
> inspect(subset(mba, lift>1))
    lhs                     rhs        support confidence lift    
[1] {Pet Food}           => {Sirup}    0.4     0.8000000  1.333333
[2] {Sirup}              => {Pet Food} 0.4     0.6666667  1.333333
[3] {Gula,Pet Food}      => {Sirup}    0.1     1.0000000  1.666667
[4] {Pet Food,Teh Celup} => {Sirup}    0.2     0.6666667  1.111111
```

Pesan ini merupakan keluaran dari proses analisis Market Basket Analysis yang telah Anda jalankan. Di bawah ini, saya akan menjelaskan hasil dari analisis tersebut dalam bahasa Indonesia:

Hasil analisis menunjukkan aturan-aturan asosiasi yang ditemukan berdasarkan parameter-parameter yang Anda atur sebelumnya:
```
Aturan: {Pet Food} => {Sirup}

Support: 0.4
Confidence: 0.8000000
Lift: 1.333333


Aturan: {Sirup} => {Pet Food}

Support: 0.4
Confidence: 0.6666667
Lift: 1.333333



Aturan: {Gula, Pet Food} => {Sirup}

Support: 0.1
Confidence: 1.0000000
Lift: 1.666667



Aturan: {Pet Food, Teh Celup} => {Sirup}

Support: 0.2
Confidence: 0.6666667
Lift: 1.111111
```

Dalam konteks analisis Market Basket, aturan-asosiasi ini mengindikasikan hubungan antara item yang dibeli bersama-sama dalam transaksi. Nilai Support mengukur seberapa sering kombinasi item tersebut muncul dalam transaksi, Confidence mengukur seberapa sering item yang satu muncul jika item lainnya ada, dan Lift mengukur seberapa kuatnya hubungan antara item-item tersebut dibandingkan dengan kemunculan acak.

Misalnya, aturan pertama menunjukkan bahwa jika pelanggan membeli "Pet Food," maka mereka juga memiliki 80% kemungkinan untuk membeli "Sirup." Lift sekitar 1.33 mengindikasikan bahwa hubungan antara keduanya lebih kuat daripada hubungan acak.

Ini adalah hasil yang berguna untuk mengidentifikasi pola pembelian pelanggan dan dapat digunakan untuk perencanaan stok, rekomendasi produk, dan strategi pemasaran yang lebih baik.



## **Kesimpulan**
Algoritma apriori adalah salah satu algoritma yang merupakan penerapan praktis dari Market Basket Analysis (MBA). Algoritma ini digunakan untuk menganalisa banyaknya kombinasi produk yang terjadi di dalam transaksi ritel, yang akan sulit dan lama jika dilakukan secara manual.

Secara teknis, algoritma apriori akan mencari tingkat asosiasi antar item di dalam banyak kombinasi kelompok data secara otomatis. Kombinasi ini juga bisa disusun dengan suatu aturan (rule) asosiasi "Jika membeli ini produk A maka akan membeli produk B", sehingga algoritma ini dikategorikan sebagai Association Rules di ranah machine learning.

Dengan menemukan paket produk yang asosiasinya kuat, Anda sebagai seorang data scientist dapat menyarankan kepada bisnis dapat melakukan berbagai action item seperti membuat paket produk dengan penawaran khusus, mendekatkan produk-produk tersebut saling berdekatan dalam satu rak, mengeluarkan rekomendasi produk di sistem e-commerce, mengurangi masalah stok, dan lain-lain.

Setelah mengerti hal fundamental penggunaan ini, saatnya kita masuk Item, Itemset and Rules. Klik tombol Next untuk melanjutkan.


