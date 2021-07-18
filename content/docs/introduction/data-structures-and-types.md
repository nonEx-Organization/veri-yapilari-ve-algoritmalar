---
title: "Veri Yapıları ve Tipleri"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "introduction"
weight: 2
toc: true
---

Bu rehberde, veri yapılarını ve tiplerini öğreneceksiniz.

# Veri yapıları Nedir?

Veri yapısı, verileri depolamak ve düzenlemek için kullanılan bir depolamadır. Bir bilgisayarda veri düzenlemenin bir yoludur. Böylece verimli bir şekilde erişilebilir ve güncellenebilir.

İhtiyaçlarınıza ve projenize bağlı olarak, projeniz için doğru veri yapısını seçmek çok önemlidir. Örneğin, bellekte sırayla veri saklamak istiyorsanız Array veri yapısını kullanabilirsiniz.

> **Note:** Veri yapısı ve veri türleri biraz farklıdır. Veri yapısı, belirli bir sıraya göre düzenlenmiş veri türlerinin toplanmış halidir.

<img src="../introduction/array_.webp" width=700 height=280px>

<hr>
&nbsp;

## Veri Yapıları Tipleri

Basitce, veri yapıları iki kategoriye ayrılıyor:

- Doğrusal Veri yapıları
 
- Doğrusal Olmayan Veri yapıları

&nbsp; 
<hr>
&nbsp;

## Doğrusal Veri Yapıları

Doğrusal veri yapılarında elemanlar birbiri ardına sıralanır. Elemanlar belirli bir sıraya göre düzenlendiğinden uygulanması kolaydır.

Ancak, programın karışıklık düzeyi arttıkça, doğrusal veri yapıları operasyonel karmaşıklıktan dolayı en iyi seçim olmayabilir.

**Popüler doğrusal veri yapıları şunlardır:**

**1. Array Veri Yapısı**
    
  Bir dizide, bellekteki öğeler sürekli bellekte düzenlenir. Dizi içerisindeki tüm elementler aynı tiptir. Dizi içerisinde saklanabilecek öğelerin türü de programlama dili tarafından belirlenir.

<img src="../introduction/array_.webp" width=700 height=330px>
> Her elemanın bir dizinle temsil edildiği bir dizi

**2. Yığın Veri Yapısı**
    
  Yığın veri yapısında elementler LIFO prensibine göre depolanır. Bu demektir ki ilk çıkarılacak veri son eklenen veridir.

  Tıpkı son tabağın önce kaldırılacağı bir tabak yığını gibi çalışır.

<img src="../introduction/stack_dsa.webp" width=700 height=680px>

> Bir yığında, işlemler yalnızca bir uçtan gerçekleştirilebilir (burada üstte)

**3. Kuyruk Veri Yapısı**

  Kuyruk veri yapısı, Yığın'ın aksine ilk eklenen verinin ilk çıkarılacağı FIFO prensibi ile çalışır.

  Tıpkı sıradaki ilk kişinin bileti önce alacağı bilet gişesindeki bir insan kuyruğu gibi çalışır.

<img src="../introduction/queue_dsa.webp" width=700 height=380px>

> Kuyrukta ekleme ve silme işlemleri farklı uçlardan gerçekleşir.

**4. Bağlı Liste Veri Yapısı**

  Bağlı liste veri yapısında, veri öğeleri bir dizi düğüm aracılığıyla bağlanır. Her bir düğüm, kendine ait bir veriyi ve sıradaki düğümün adresini tutar.

<img src="../introduction/linked-list_dsa.webp" width=700 height=250px>

> Tek yönlü bağlı liste

&nbsp;
<hr>
&nbsp;

## Doğrusal Olmayan Veri Yapıları

Doğrusal veri yapılarının aksine, doğrusal olmayan veri yapılarındaki elementler herhangi bir sırada değildir. Bunun yerine, bir elementin bir veya daha fazla elemente bağlanacağı hiyerarşik bir şekilde düzenlenirler.

Doğrusal olmayan veri yapıları ayrıca grafik ve ağaç tabanlı veri yapılarına ayrılır.

**1.Graf Veri Yapısı**
  Grafik veri yapısında her bir düğüm köşe adını alır ve her bir köşe diğer köşelere kenarlar aracılığıyla bağlanır.

<img src="../introduction/graph_dsa.webp" width=390 height= 400px>

> Graf Veri Yapısı Örneği

**2.Ağaç Veri Yapısı**
  
  Bir grafiğe benzer şekilde, bir ağaç da bir köşeler ve kenarlar topluluğudur. Ancak ağaç veri yapısında iki köşe arasında yalnızca bir kenar olabilir.

<img src="../introduction/tree_dsa.webp" width=590 height= 400px>

> Ağaç Veri Yapısı Örneği

&nbsp;
<hr>
&nbsp;

## Doğrusal vs Doğrusal Olmayan Veri Yapıları

Artık doğrusal ve doğrusal olmayan veri yapıları hakkında bilgi sahibiyiz. Gelin, aralarındaki büyük farklılıkları inceleyelim.

| **Doğrusal Veri Yapıları** | **Doğrusal Olmayan Veri Yapıları** |
|------------------------|--------------------------------|
|Veriler birbiri ardına sıralı olarak düzenlenir.| Veriler sıralı olmayan düzende (hiyerarşik şekilde) düzenlenir.|
|Veriler tek bir katmanda bulunur.| Veriler farklı katmanlarda bulunur.|
|Tek seferde tüm elemanlar taranabilir. Yani, ilk elemandan başlarsak, tüm elemanları sırayla tek bir geçişte geçebiliriz.| Birden fazla çalıştırma gerektirir. Yani, ilk elemandan başlarsak, tüm elemanları tek bir geçişte geçmek mümkün olmayabilir.|
|Hafıza kullanımı verimli değil.| Farklı yapılar, ihtiyaca bağlı olarak belleği farklı verimli şekillerde kullanır.|
|Zaman karmaşıklığı veri büyüklüğüne bağlı olarak artar.| Zaman karmaşıklığı aynı kalır.|
| Örnek: Diziler,Yığın,Kuyruk | Örnek: Graf, Ağaç, Map |

&nbsp;
<hr>
&nbsp;


# Neden Veri Yapıları?
Veri yapıları hakkında bilgi sahibi olmanız, her bir veri yapısının çalışmasını anlamanıza yardımcı olur.Buna bağlı olarak projeniz için doğru veri yapılarını seçebilirsiniz.

Bu, bellek ve zaman açısından verimli kod yazmanıza yardımcı olur.