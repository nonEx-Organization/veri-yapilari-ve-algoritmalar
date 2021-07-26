---
title: "Kuyruk Tipleri"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "data-structures-1"
weight: 12
toc: true
---

Bu rehberde, farklı kuyruk türlerini illüstrasyonlarla birlikte öğreneceksiniz.

Kuyruk, programlamada kullanışlı bir veri yapısıdır. Sinema salonunun önündeki bilet kuyruğuna benzer, kuyruğa ilk giren insan, bileti de ilk alacak kişidir.

Kuyruk tipleri 4'e ayrılır:

- [Basit Kuyruk](#basit-kuyruk)

- [Dairesel Kuyruk](#dairesel-kuyruk)

- [Öncelik Kuyruğu](#öncelik-kuyruğu)

- [Çift Uçlu Kuyruk](#çift-uçlu-kuyruk)

&nbsp;
<hr>
&nbsp;

## Basit Kuyruk

Basit kuyrukta yerleştirme arkada, çıkarma ise önde gerçekleşir. FIFO (İlk Giren İlk Çıkar) kuralına sıkı sıkıya bağlıdır.

<p align=center>
  <img src="../assets/simple-queue.png" width=620px>
</p>

{{< alert icon="➡️" text="Basit Kuyruk Temsili" />}}

Daha fazlasını öğrenmek için [kuyruk veri yapısını][queue-page] ziyaret edin.

&nbsp;
<hr>
&nbsp;

## Dairesel Kuyruk

Dairesel kuyrukta son eleman ilk elemanı göstererek dairesel bir bağlantı oluşturur.

<p align=center>
  <img src="../assets/circular-queue.png" width=620px>
</p>

{{< alert icon="➡️" text="Dairesel Kuyruk Temsili" />}}

Basit bir kuyruğa göre dairesel bir kuyruğun ana avantajı, daha iyi bellek kullanımıdır. Son pozisyon dolu ve ilk pozisyon boşsa, ilk pozisyona bir eleman ekleyebiliriz. Bu işlem basit bir kuyrukta mümkün değildir.

Daha fazlasını öğrenmek için [dairesel kuyruk veri yapısını][circular-queue-page] ziyaret edin.

&nbsp;
<hr>
&nbsp;

## Öncelik Kuyruğu

Öncelik sırası, her öğenin bir öncelik ile ilişkilendirildiği ve önceliğine göre sunulduğu özel bir kuyruk türüdür. Eğer aynı önceliğe sahip elemanlar varsa, kuyruktaki sıralarına göre servis edilir.

<p align=center>
  <img src="../assets/priority-queue.png" width=620px>
</p>

{{< alert icon="➡️" text="Öncelik Kuyruğu Temsili" />}}

Eleman ekleme, değerlerin gelişine bağlı olarak gerçekleşir. Eleman çıkarmada ise önceliğe göre gerçekleşir.

Daha fazlasını öğrenmek için [öncelik kuyruğu veri yapısını][priority-queue-page] ziyaret edin.

&nbsp;
<hr>
&nbsp;

## Çift Uçlu Kuyruk

Çift uçlu kuyrukta elemanların eklenmesi ve çıkarılması önden veya arkadan yapılabilir.
Bu durum, FIFO (İlk Giren İlk Çıkar) kuralına bağlı olmadığını gösterir.

<p align=center>
  <img src="../assets/double-ended-queue.png" width=620px>
</p>

{{< alert icon="➡️" text="Çift Uçlu Kuyruk Temsili" />}}

Daha fazlasını öğrenmek için [çift uçlu kuyruk veri yapısını][deque-queue-page] ziyaret edin.

<!--
LINKS
-->
[queue-page]:../queue
[circular-queue-page]:../circular-queue
[priority-queue-page]:../priority-queue
[deque-queue-page]:../deque