# Chapter 01: Introduction to Algorithms
Algoritma dan Struktur Data


## Simple Search & Binary Search
#### 1. Introdusction to Algorithms
Algoritma adalah sekumpulan instruksi untuk menyelesaikan suatu task atau tugas tertentu. Kita akan membahas sejumlah algoritma yang dipilih karena algoritma nya cepat dan mampu menyelesaikan problem yang cukup menarik. 
#### 2.binary search
Kita akan dihadapi pada suatu kasus dimana harus mencari kata yang diawalai dari huruf k dalam kamus. Pada kasus ini dapat kita pahami bahwa dalam kamus menyimpan sekumpulan kata dalam urutan alfabet, oleh sebab itu kata yang berawalan k tentu saja berada di tengah tidak mungkin diawal ataupun diakhir, jadi kita dapay mulai melakukan pencarian melalui bagian tengah kamus.

Kasus pencarian ini biasa kita kenal dengan istilah search problem atau masalah pencarian, salah satu solusi yang bisa kita gunakan ialah menggunakan binary search.
Binary search adalah algoritma dimana inputan dari algoritmanya dalah suatu list yang terdiri dari sejumlah elemen yang terurut. Ketika elemen yang dicari berada dalam list yang terurut makan binary search akan mengembalikan posisi dari kata tersebut, tetapi jika kata yang dicari tdk ditemukan maka binary search akan mengembalikan nilai null atau kosong.
#### 3.A simler search (problem) example
saya sedang memikirkan angka 1 sampai dengan 100, kemudian kalian harus menebak angka tersebut dengan jumlah tebakan sesedikit mungkin. Untuk tebakan yang diberikan saya akan beritahu apakah tebakannya terlalu kecil, terlalu besar atau benar.
- Simple search way.
  Algoritma ini dikenal dengan simple search yang mana merupakan metode pencarian sederhana di mana setiap elemen dalam daftar atau array diperiksa satu per satu secara berurutan hingga elemen yang dicari ditemukan atau sampai akhir dari kumpulan data. Ini adalah pendekatan langsung yang efektif untuk set data yang kecil, tetapi bisa menjadi tidak efisien untuk set data yang besar karena membutuhkan jumlah langkah yang proporsional dengan jumlah elemen dalam set data.
- Binary Search Performance Expalined
  Binary search adalah algoritma pencarian yang efisien untuk menemukan nilai tertentu dalam sebuah array yang telah diurutkan. Algoritma ini bekerja dengan membagi set data menjadi dua bagian dan memeriksa apakah nilai yang dicari berada di bagian kiri atau kanan. Proses ini terus berlanjut pada bagian yang sesuai dengan pencarian, mengurangi set data yang harus diperiksa menjadi setengah pada setiap iterasi. Hal ini memungkinkan pencarian dilakukan dengan cepat, terutama pada set data yang besar. Binary search biasanya menggunakan logaritma.
- Logarithms
  algoritma merupakan kebalikan dari pemangkatan.
    ```sh
    10^2 = 100 <-> log100 = 2
    10^3 = 1000 <-> log1000 = 3
    2^3 = 8 <-> log8 = 3
    2^4 = 16 <-> log16 = 4
    2^5 = 32 <-> log32 = 5
    ```
    
Ketika kamu mencari suatu elemen menggunakan simple search, kemungkinan terburuknya kamu harus melihat dan menghitung setiap elemen satu-satu, dengan kata lain jika kita memiliki 8 buah elemen kita harus melakukan pengecekan sebanyak 8 kali.

Sebaliknya jika kita menggunakan binary search dalam kondisi terburuk kita hanya perlu melakukan pencarian sebanyak log n. sebagai contoh ketika kita mencari list dari 8 elemen kita hanya perlu mencari log = 3, karena 2^3 = 8. Dengan kata lain jika jumlah list sebanyak 8 elemen kita hnya perlu melakukan pengecekan sebanyak 3 kali.Untuk list sebanyak 1.024 elemen, log 1.024 = 10 karena 2^10 = 1.024 jadi untuk list sebanyak 1.024, kita hanya perlu melakukan pengecekan sebanyak 10 kali.

Binary search hanya bisa digunakan ketika list yang kita miliki sudah terurut. Sebagai contoh, daftar nama pada buku telfon ataupun daftar kata pada kamus, jadi kamu dapat menggunakan binary search untuk menemukannya.

#### 4.Binary Search In python
Kita akan mulai melihat bagaimana implementasi binary search dengan menggunakan bahasa pemograman python dimana kita akan menampung sekumpulan nilai didalam suatu list.
```sh
low = 0
High = len(list) -
```
Disini menjelaskan tentang konsep indexing dimana posisi pertama memiliki index 0, posisi kedua memiliki index 1 dan seterusnya. Disini akan terdapat suatu fungsi yaitu binary search dimana fungsi ini akan menerima dua parameter, parameter pertama berupa sorted list dan parameter kedua berisi item yang akan dicari dan bilamana item yang terdapat dalam list tadi maka fungsi tersebut akan mengembalikan posisi dari item tersebut didalam list nya,
untuk setiap tahapan pencarian kita akan memantau posisi dari listnya

```sh
mid = (low + high) /2
guess = list[mid]
```
dalam setiap literasinya kita akan memeriksa elemen yang berada pada posisi tengah, oleh karenyanya kita perlu mencari posisi tengahnya seperti pada, selanjutnya elemen yang mau kita periksa adalah list index ke mid yang kita tamping pada variable guess.
Disini nilai mid akan otomatis dibulatkan kebawah oleh python ketika hasil penjumlahan low dan high nya tidak berupa bilangan bulat. 
```sh
If guess < item:
    low = mid + 1
```
kalau guess nya lebih kecil dari item, maka nilai dari low indexnya bisa kita sesuaikan dengan mid + 1, tetapi jika guess nya lebih besar  maka kita perlu mengupdate high indexnya.
Full code:

```sh
def binary_search(list, item):
       low = 0
       high = len(list)-1
       
       while low <= high:
                mid = (low + high) // 2
                guess = list[mid]
                if guess == item:
                     return mid
                if guess > item:
                    high = mid – 1
                else:
                    low = mid + 1
        return None

my_list = [1,3,5,7,9]
print(binary_search(my_list, 3))
print(binary_search(my_list, -1))
```
## Running Time & Big O Notation
#### 1. Running Time 
Secara umum kita selalu dihadapkan pada kebutuhan untuk memilih algiritma yang paling efisien, dimana kita selalu berusaha untuk melakukan optimasi dalam hal waktu maupun ukuran. Berapakah banyak waktu yang bisa kita optimumkan dengan menerapkan binary search?

pada cara yang pertama yang mana kita menggunakan simple search, kita butuh untuk melakukan pengecekan satu-persatu. dengan kata lain jika kita memiliki 100 elemen, maka akan dibutuhkan 100 kali pengecekan dan bila terdapat 4 miliar elemen maka akan dibutuhkan sampai dengan 4 miliar kali pengecekan juga.maka jumlah pengecekan maksimumnya akan sama dengan jumlah elemen yang terdapat dalam list tersebut. ]ini sering diinisialkan sebagai 'linear time'.

jika kita menggunakan binary search, maka ketika kita dihadapkan dengan 100 items,itu akan membutukan paling puruk sebesar 7 kali pengecekan dan kalau kita dihadapkan 4 miliar items, maka paling banyak kita akan melakukan 32 kali pengecekan saja.

Binari search akan menerapkan yang namanya 'logaritmic time' atau sering dikenal dengan istilah log time.

run time for search  algorithms
| Simple Search | Binary Search |
| ------ | ------ |
| 100 items -> 100 tebakan| 100 items -> 7 tebakan |
| 4 miliar items -> 4 miliar tebakan | 4 miliar items -> 32 tebakan |
|O (n) -> linear time|O (log n) -> logaritmic time |

#### 2. Big O Notation
 Big O Notation adalah suatu notasi spesial yang dapat memberitahukan kamu seberapa cepat suatu algoritma berjalan. dalam kehidupan sehari hari kita sering atau akan menggunakan algoritma dari orang lain, oleh sebab itu kita memerlukan big o notation untuk mengetahui seberapa cepat atau lambat algoritma tersebut sehingga kita dapat mengetahui algoritma mana yang paling efisien.
 
 pada bagian ini kita akan membahas bagaimana implementasi  big o notation yang dapat membantu kita dalam membandingkan running times dari beberapa algoritma yang digunakan.
 
#### 3.Algorithm running times grow at different rates 
 dalam kasus ini ada seseorang yang bernama BOB yang diminta untuk menuliskan suatu algoritma yang akan digunakan oleh NASA. Algoritma ini akan dijalankan suatu melakukan pendaratan roket  di bulan, dimana algoritma ini digunakan untuk suatu proses penghitungan terkait lokasi pendaratan. dan untuk kasus ini BOB hanya memiliki waktu 10 detik saja.
 
 disini BOB dihadapkan pada sebuah algoritma yaitu simple search dan binary search. Algoritma yang akan dipilih BOB ini harus cepat dan tepat. disatu sisi, kita tau bahwa binary search jauh lebih cepat jika dibandingkan dengan  simple search. tetapi disisi lain simple search  jauh lebih mudah untuk diimplementasikan. Artinya suatu BOB menuliskan algoritma simple seacrh ini, maka sangat kecil kemungkinan  untuk melakukan kesalahan atau menghasilkan bug dalam code programnya, dan tentunya BOB tidak menginginkan adanya bug pada code program untuk mendaratkan roket di bulan.
 
 disini kita melakukan pengecekan suatu elemen  dibutuhkan waktu 1 milisecond, kemudian BOB mulai melakukan kalkulasi  terhadap 100 elemen. dengan simple search, maka BOB harus melakukan pemeriksaan terhadap 100 elemens, sehingga dibutuhkan waktu sekitar 100 milisecond. Sedangkan kalau BOB menggunakan binary search, maka BOB hanya akan  perlu melakukan pengecekan 7 elemen  sehingga dibutuhkan waktu hanya 7 milisecond saja.
 
 secara sealistis jumlah elemen yang harus dicari berkisar 1 miliar elemen. artinya jika BOB menjalankan 1 miliar elemen menggunakan binary search, maka  BOB akan membutuhkan waktu  30 milisecond (log2 1.000.000.000 adalah 30). dan dari kasus sebelumnya bisa kita lihat bahwa binary search 15 kali lebih cepat dari simple search. karena pada kasus sebelumnya  simple search  membutuhkan waktu 100 milisecond  untuk 100 elemen sedangkan binary search membutuhkan waktu  7 milisecond. oleh karenanya kalau binary search  membutuhkan 30  milisecond  berarti simple search membutuhkan  waktu 15 kalilipatnya yaitu 450 milisecond. artinya nilai ini masih dibawah threshold yaitu 10 detik. dengan alasan inilah akhirnya BOB memutuskan menggunakan simple search]. jadi pertanyaannya apakah BOB mengambil keputusan yang tepat?
 
 disini  BOB telah melakukan kesalahan besar. disini kita perhatikan jika kita menggunakan simple search untuk  melakukan pencarian pada  1  miliar items  maka akan dibutuhkan 1 miliar milisecond, atau 11 hari. yang jadi permasalahannya adalah bahwa run time atau binary search  dan simple search tidak berkembang dengan rate yang sama (kecepatan tidak sama).
 
 seiring dengan seiring meningkatnya jumlah items peningkatan jumlah waktu bisa dibilang kecil juka dibandingkan simple search yang terbilang cukup besar. artinya binary search akan membutuhkan waktu yang jauh lebih sedikit  bila dibandingkan simple search. atau dengan kata lain binary search jauh lebih cepat dengan simple search. 
 
 oleh karenanya tidaklah cukup untuk mengetahui suatu algoritma akan berjalan, kita butuh  mencari tahu bagaimana running timesnya akan meningkat  seiring peningkatan ukurannya. oleh karenanya big o notation ini menjadi lebih relevan ketika kita membandingkan antar algoritma.
 
#### 4.Big O Notation Explained
 Big O Notation ini mengekspresikan bagaimana kecepatan suatu algoritma. Sebagai contoh kita dihadapkan pada suatu list, simple search butuh melakukan pengecekan setiap elemennya, oleh karenanya ini akan membutuhkan sejumlah n operation, sehingga penulisan Big O Notationnya adalah O(n) atau linear time. Big O notation tidak mengekspresikan kecepatan suatu algoritma dalam satuan second atau detik, Big O Notatin memungkinkan kita untuk membandingkan kita suatu notasi untuk membandingkan jumlah operasi. dimana Big O akan mengekspresikan bagaimana suatu algoritma berkembang dari suatu algoritma.
 
 Binary search membutuhkan Log n operation untuk memeriksa list dengan ukuran n. oleh karenanya running time untuk binary search ketika diekspresikan dengan Big o Notation adalah O(Log n). secara umum Big o notation dituliskan dengan  O(n). 
 
#### 5.Big O Estabilishes a worst-case run time 
semisal kita mengimplementasikan simple searsch untuk mencari seseorang pada buku telfon kita.pada kasus ini kita mencari adit,  yang mana menempati urutan pertama pada buku telfon yang kita miliki. sehingga kita tidak perlu mengecek satu satu dari pertama sampai terakhir. karena telah menemukan adit. maka pertanyaannya  apakah algoritmanya masih dibilang O(n) time atau justru O(1) time? karena disini kita telah menemukan orang yang dicari pada operasi pertama. 

kasus pencarian adit ini tetap harus dinotasikan sebagai O(n) time. kita memang menemukannya pada pencarian pertama, tetapi perlu diingat ini merupakan base case scenarionya, dan yang perlu digaris bawahi disini adalah scenario terburuk. kondisi terburuknya adalah kita harus mengecek setiap entri dari buku telfon kita. dengan ini maka dapat disimpulkan bahwa simple search itu tidak akan mungkin lebih lamban dari O(n) time.

#### 6.Some common Big O run times
Berikut adalah daftar Big O Notation yang umum untuk ditemui, dan disini diurutkan dari Big O yang tercepat sampai Big O yang terlama.
- O(log n), sering dikenal sebagai log time.contoh: Binary search.
- O(n), sering dikenal sebagai linear time. contoh: Simple search.
- O(n*log n). contoh:quicksort.
- O(n^2). contoh: selection sort.
- O(n!). contoh: traveling sales person.

jika kita butuh untuk menggambarkan 16 boxis lagi dimana kita dihadapkan pada pilihan 5 jenis algoritma. semisal untuk menjalankan 10 operation kita membutuhkan waktu 1 detik, atau dengan kata lain ditiap detiknya bisa menjalankan 10 operation. kalau kita memilih algoritma pertama O(log n) maka akan dibutuhkan 4 operation untuk menggambar 16 boxis.(log 16 = 4) maka kita membutuhkan waktu 0,4 detik. Bagaimana jika kita diminta untuk menggambarkan 1.024 boxis? maka kita dapat kalkulasikan log 1.024 = 10,  berarti kita hanya butuh 1 detik.

untuk algoritma kedua menggunakan O(n) time. yang mana akan dibutuhkan 16 operation untuk menggambar 16 boxis, dan akan dibutuhkan 1.024 operasion untuk menggambar 1.024 boxis.Berapa waktu yang dibutuhkan dalam detik?

sebagai ilustrasi jika boxisnya 16 maka O(log n) dibutuhkan 0,4 detik, O(n) dibutuhkan 1,6 detik, O(n*log n) dibutuhkan 6,4 detik, O(n^2) dibutuhkan 25,6 detik, dan O(n!) dibutuhkan 60.301 tahun. dan berbedaan ini akan semakin ekstream seirim jumlah yang akan ditambahkan. 

#### 7.Rangkuman 
kecepatan algoritma tidak diukur dalam satuan detik tapi  berdasarkan pertumbuhan dari jumlah operasinya. run time dari algoritma itu diekspresikan dengan menggunakan Big O Notation. dan O(log n) lebih cepat jika dibandingkan dengan O(n), semua itu akan semakin signifikan bersama dengan meningkatnya jumlah items.
