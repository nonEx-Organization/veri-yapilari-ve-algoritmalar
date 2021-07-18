---
title: "Algoritma Nedir?"
description: ""
lead: ""
date: 2021-14-16
lastmod: 2021-10-06
draft: false
images: []
menu:
  docs:
    parent: "introduction"
weight: 1
toc: true
---

Bu derste, algoritmanın ne olduğunu örnekler ile öğreneceğiz.

Bilgisayar programlama terimlerinde, algoritma belirli bir problemin çözümü için iyi tanımlanmış bir talimat dizisidir. Sizden bir dizi girdi alır ve istenen sonucu verir. Örneğin,

İki sayıyı toplayan algoritma için:

1. Girdi olarak 2 sayı al
2. Artı (+) operatörü ile bu iki sayıyı topla
3. Sonucu ekrana göster

&nbsp;
<hr>
&nbsp;

## İyi Algoritmanın Özellikleri

+ Girdilerin ve çıktıların kesin olarak tanımlanması gerekir.
+ Algoritmanın her bir adımı net ve açık olmalıdır.
+ Algoritmalar, bir sorunu çözmenin birçok farklı yolu arasında en etkili olmalıdır.
+ Algoritma bilgisayar kodunu içermemelidir. Onun yerine başka bir programlama dili ile yazılabilir olmalıdır.

&nbsp;
<hr>
&nbsp;

## Algoritma Örnekleri
[İki sayıyı toplayan algoritma](#algoritma-1) 

[3 sayı arasından en büyüğünü bulan algoritma](#algoritma-2)

[İkinci dereceden denklemin tüm köklerini bulan algoritma](#algoritma-3)

[Faktöriyel algoritması](#algoritma-4)

[Asal sayı kontrolü algoritması](#algoritma-5)

[Fibonacci Serisi algoritması](#algoritma-6)

&nbsp;
<hr>
&nbsp;

## Algoritma 1

Kullanıcı tarafından girilen 2 sayıyı toplama

```bash
Adım 1: Başla
Adım 2: sayi1,sayi2 ve toplam değişkenlerini tanımla
Adım 3: sayi1 ve sayi2 değerlerini oku
Adım 4: sayi1 ve sayi2 yi topla ve sonucu toplama ata
        toplam <- sayi1 + sayi2
Adım 5: Ekrana toplamı yazdır
Adım 6: Dur
```
&nbsp;
<hr>
&nbsp;

## Algoritma 2

3 sayı arasından en büyüğünü bulma

```bash
Adım 1: Başla
Adım 2: a,b ve c sayılarını tanımla.
Adım 3: a,b ve c değişkenlerini oku.
Step 4: Eger a > b
            Eger a > c
                A sayısı en büyük yaz.
            Degilse
                C sayısı en büyük yaz.
        Degilse
            Eger b > c
                B sayısı en büyük yaz
            Degilse
                C sayısı en büyük yaz  
Adım 6: Dur
```
&nbsp;
<hr>
&nbsp;

## Algoritma 3

İkinci dereceden denklemin Kökünü bulun ax<sup>2</sup> + bx + c = 0


```bash
Adım 1: Başla
Adım 2: a,b,c,d,x1,x2,rp ve pi degiskenlerini tanımla.
Adım 3: diskriminant hesaplayın.
        D <- b2-4ac
Step 4: Eger D >= 0
            r1 ← (-b+√D)/2a
            r2 ← (-b-√D)/2a
            Kök olarak r1 ve r2 ekrana yaz
        Degilse
            Sanal ve reel parçayı hesapla
            rp ← -b/2a
            ip ← √(-D)/2a
            Kök olarak rp+j(ip) ve rp-j(ip) yaz  
Adım 5: Dur
```
&nbsp;
<hr>
&nbsp;

## Algoritma 4

Faktöriyel algoritması


```bash
Adım 1: Başla
Adım 2: n, faktoriyel ve i değişkenlerini tanımla.
Adım 3: Degiskenlere ilk değeri ver
          faktöriyel ← 1
          i ← 1
Adım 4: n değerini oku
Adım 5: i=n koşulu saglanana dek tekrar et
     5.1: faktöriyel ← faktöriyel*i
     5.2: i ← i+1
Adım 6: Ekrana faktöriyeli yazdır
Adım 7: Dur
```

&nbsp;
<hr>
&nbsp;

## Algoritma 5

Asal sayı kontrolü algoritması


```bash
Adım 1: Başla
Adım 2: n, durum ve i değişkenlerini tanımla.
Adım 3: Degiskenlere ilk değeri ver
          durum ← 1
          i ← 2
Adım 4: n değerini oku
Adım 5: i=(n/2) koşulu saglanana dek tekrar et
     5.1: Eger n/i kalanı 0a eşitse
              durum <- 0
              Adım 6ya git
     5.2: i ← i+1
Adım 6: Eger durum = 0
            Ekrana n sayısı asal değil yaz
        Degilse
            Ekrana n sayısı asal yaz
Adım 7: Dur
```

&nbsp;
<hr>
&nbsp;

## Algoritma 6

Fibonacci algoritması


```bash
Adım 1: Başla 
Adım 2: birinci_terim, ikinci_terim ve gecici değişkenlerini tanımla. 
Adım 3: Degiskenlere ilk değeri ver
        birinci_terim ← 0 
        ikinci_terim ← 1 
Adım 4: Ekrana birinci_terim ve ikinci_terimi yazdır
Adım 5: ikinci_terim <= 1000 koşulu saglanana dek tekrar et
     5.1: gecici ← ikinci_terim 
     5.2: ikinci_terim ← second_term + birinci_terim 
     5.3: birinci_terim ← gecici 
     5.4: Ekrana ikinci terimi yazdır
Adım 6: Dur
```

