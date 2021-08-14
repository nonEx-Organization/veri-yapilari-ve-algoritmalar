---
title: "Hash Tablosu"
description: ""
lead: "(Hash Table)"
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "data-structures-2"
weight: 13
toc: true
---

Bu rehberde, hash tablosunun ne olduğunu öğreneceksiniz. Ayrıca c# dilinde hash tablosu işlemlerinin çalışan örneklerini bulacaksınız.

Hash tablosu, elemanlarını anahtar-değer çiftlerinde saklayan veri yapısıdır.

- **Anahtar** - değerleri saklamak için kullanılan eşsiz tamsayı

- **Değer** - Anahtarla ilişkili veri

<p align=center>
  <img src="../assets/hash-table-key-value.png" width=220px>
</p>

{{< alert icon="➡️" text="Hash Tablosunda anahtar-değer çifti" />}}

&nbsp;
<hr>
&nbsp;

## Hashing (Hash Fonksiyonu)

Bir hash tablosunda, anahtarlar kullanılarak yeni bir dizin oluşturulur. O anahtara karşılık gelen eleman dizinde saklanır. Bu işleme **hashing** denir.

Anahtarımız `k` ve hash fonksiyonumuz `h(x)` olsun.

Burada `h(k)`, k ile bağlantılı elemanı saklamak için bize yeni bir indeks verecektir.

<p align=center>
  <img src="../assets/hash-table-representation.png" width=620px>
</p>

{{< alert icon="➡️" text="Hash Tablosunda anahtar-değer çifti" />}}

&nbsp;
<hr>
&nbsp;

## Hash Çakışması

Hash fonksiyonu çoklu anahtarlar için aynı indeksi oluşturduğunda **conflict**(çakışma) oluşacaktır. Bu durum **hash çakışması** olarak adlandırılır.

Aşağıdaki tekniklerden birini kullanarak hash çakışmasını çözebiliriz.

- Separate Chaining (Ayrı zincirleme)

- Open Addressing (Açık adresleme): Linear/Quadratic Probing and Double Hashing

&nbsp;
<hr>
&nbsp;

## 1. Separate Chaining (Ayrı zincirleme)

Zincirlemede, eğer hash fonksiyonu birçok eleman için aynı indeksi üretirse bu elemanlar çift bağlı liste kullanılarak aynı indekste saklanır.

<p align=center>
  <img src="../assets/hash-table-collision.png" width=620px>
</p>

&nbsp;
<hr>
&nbsp;

## 2. Open Addressing (Açık Adresleme)

Zincirlemenin aksine açık adresleme aynı indekse birçok elemanı saklamaz. Burada her yuva tek bir anahtarla doldurulur ya da null bırakılır.

Açık adreslemede kullanılan farklı teknikler şunlardır:

### Linear probing ( Doğrusal problama)

Doğrusal problamada çakışma sıradaki indeksin kontrol edilmesiyle çözülür.

`h(k, i) = (h′(k) + i) mod m``

- `i = {0, 1, …}`

- `h'(k)` ise yeni bir hash fonksiyonu

Eğer çakışma `h(k,0)`da meydana gelirse `h(k,1)` kontrol edilir. Bu durumda `ì` değişkeni doğrusal olarak artar.

Doğrusal problama ile ilgili sorun, bitişik yuvalardan oluşan bir kümenin doldurulmasıdır. Yeni bir eleman eklendiği zaman tüm kümenin gezilmesi gerekiyor. Hash tablosu üzerinde bu işlemleri gerçekleştirmek için gereken süreye eklenir.

### Quadratic probing ( İkinci Dereceden problama)

Dorğusal problamaya benzer çalışır ama aşağıdaki formül kullanılarak yuvalar arasındaki boşluk artırılır.

`h(k, i) = (h′(k) + c`<sub>`1`</sub>`i + c`<sub>`2`</sub>`i`<sup>`2`</sup> `)mod m`

- `c`<sub>`1`</sub>ve `c`<sub>`2`</sub> pozitif yardımcı sabitler

- `i = {0, 1, …}`

### Double Hashing (Çift Hashleme)

Eğer `h(k)` hash fonksiyonu çalışırken bir çakışma meydana gelirse başka bir hash fonksiynu sıradaki yuvayı bulmak için hesaplanır.

`h(k, i) = (h`<sub>`1`</sub>`(k) + ih`<sub>`2`</sub>`(k)) mod m`

&nbsp;
<hr>
&nbsp;

## İyi Hash Metodları

İyi bir hash fonksiyonu çakışmaları tamamen engellemeyebilir ancak çarpışma sayısını azaltabilir.

Şimdi ise iyi bir hash fonksiyonu bulmak için farklı yöntemlere bakacağız.

### 1. Division Method (Bölme Metodu)

Eğer `k `bir anahtarsa ​​ve `m` hash tablosunun boyutuysa, hash fonksiyonu `h()` şu şekilde hesaplanır:

`h(k) = k mod m`

Örneğin, hash tablosunun boyutu `10` ve `k = 112` olsun. `h(k) = 112` mod `10 = 2`. `m`'nin değeri 2'nin kuvvetleri olmamalıdır.
Nedeni ise `2`'nin kuvvetlerinin ikili sistemde `10, 100, 1000, …` olmasıdır.

### Multiplication Method (Çarpma Metodu)

`h(k) = ⌊m(kA mod 1)⌋`

- `kA mod 1`, kA kesirli kısmını verir

- `⌊ ⌋` taban değerini verir

- `A` herhangi bir sabittir. `A`'nın değeri 0 ile 1 arasındadır. Ancak, **Knuth** tarafından önerilen en uygun seçim ≈ `(√5-1)/2` olacaktır.

### Universal Hashing (Evrensel Hashing)

Evrensel hashing'de hash fonksiyonu anahtarlardan bağımsız olarak rastgele seçilir.

&nbsp;
<hr>
&nbsp;

# C# Dilinde Hash Table Implementasyonu

```cs
Hashtable ht = new Hashtable();

//Veriler ekleyip silelim
ht.Add(123, 432);
ht.Add(12, 2345);
ht.Add(15, 5643);
ht.Add(3, 321);
ht.Remove(12);

//Elemanları yazdır
foreach(DictionaryEntry item in ht)
{
    Console.WriteLine(item.Key + " : " + item.Value);
}
```
&nbsp;
<hr>
&nbsp;

# Hash Table Kullanımları

- Sabit zamanlı arama ve eklemede

- Kriptografik uygulamalarda

- Veri indekslemede