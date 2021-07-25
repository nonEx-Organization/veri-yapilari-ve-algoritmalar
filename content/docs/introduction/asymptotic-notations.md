---
title: "Asimptotik Analiz: Big O Notasyonu ve Dahası"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "introduction"
weight: 4
toc: true
---

Bu rehberde, asimptotik notasyonların ne olduğunu öğreneceksiniz.
Ayrıca Big-O notasyonu, Teta notasyonu ve Omega notasyonunu da öğreneceksiniz.

Bir algoritmanın verimliliği zamana,depolamaya ve algoritmayı çalıştırmak için gerekli diğer kaynaklara bağlıdır. **Verimlilik** asimptotik notasyonların yardımı ile hesaplanır.

Farklı türdeki girdiler için algoritma aynı performansı gösteremeyebilir.
Girdi sayısının artması ile performans değişecektir.

Girdi boyutunun sırasının değişmesi ile algoritmanın performansındaki değişimin incelenmesi **asimptotik analiz** olarak tanımlanır.

&nbsp;
<hr>
&nbsp;

## Asimptotik Notasyonlar

Asimptotik gösterimler, girdi belirli bir değere veya sınırlayıcı bir değere yöneldiğinde bir algoritmanın çalışma süresini tanımlamak için kullanılan matematiksel gösterimlerdir.

Örneğin, **Bubble Sort**(Balon sıralaması)'da eğer girdi dizisi zaten sıralı ise algoritma tarafından geçen süre doğrusaldır, yani en iyi durumdur.(**Best case**)

Ancak, giriş dizisi ters durumda olduğunda, algoritma elemanları sıralamak için maksimum süreyi alır, yani en kötü durumdur.(**worst case**)

Girdi dizisi gerek sıralanmış gerek tam ters sırada olsun, ortalama süre alır. Bu süreler asimptotik gösterimler kullanılarak gösterilir.

Ana 3 tane asimptotik notasyon bulunmaktadır:

- [Big-O Notasyonu](#big-o-notasyonu-o-notasyonu)

- [Omega Notasyonu](#omega-notasyonu-ω-notasyonu)

- [Teta Notasyonu](#teta-notasyonu-θ-notasyonu)

&nbsp;
<hr>
&nbsp;

## Big O Notasyonu (O Notasyonu)

Big-O notasyonu, bir algoritmanın çalışma süresinin üst sınırını temsil eder. Bu bize bir algoritmanın en kötü durum karmaşıklığını verir.

<img src="../assets/big-o-notation.webp" width=700 height=680px>

{{< alert icon="➡️" text="Big-O, bir fonksiyonun üst sınırını verir" />}}


```bash
O(g(n)) = { f(n): c ve n0 pozitif sabitleri var
          tüm n ≥ n0 ve 0 ≤ f(n) ≤ cg(n) olacak şekilde }
```
Yukarıdaki ifadede yeterince büyük `n` sayısı için, `0` ile `cg(n)` arasında olacak şekilde pozitif bir c sabiti varsa, `O(g(n))` kümesine ait bir `f(n)` fonksiyonu olarak tanımlanabilir.

Herhangi bir `n` değeri için, bir algoritmanın çalışma süresi `O(g(n))` tarafından sağlanan süreyi geçmez.

&nbsp;
<hr>
&nbsp;

## Omega Notasyonu (Ω Notasyonu)

Omega notasyonu, bir algoritmanın çalışma süresinin alt sınırını temsil eder. Böylece, bir algoritmanın en iyi durum(**best case**) karmaşıklığını sağlar.

<img src="../assets/omega-notation.webp" width=700 height=680px>

{{< alert icon="➡️" text="Omega, bir fonksiyonun alt sınırını verir" />}}

```bash
Ω(g(n)) = { f(n): c ve n0 pozitif sabitleri var
          tüm n ≥ n0 ve 0 ≤ cg(n) ≤ f(n) olacak şekilde }
```
Yukarıdaki ifade, yeterince büyük `n` için, `cg(n)`'nin üzerinde olacak şekilde pozitif bir `c` sabiti varsa, `Ω(g(n))` kümesine ait bir `f(n)` fonksiyonu olarak tanımlanabilir.

For any value of `n`, the minimum time required by the algorithm is given by `Omega Ω(g(n))`.

&nbsp;
<hr>
&nbsp;

## Teta Notasyonu (Θ Notasyonu)

Teta notasyonu, fonksiyonu yukarıdan ve aşağıdan çevreler. Bir algoritmanın çalışma süresinin üst ve alt sınırını temsil ettiğinden, bir algoritmanın ortalama durum karmaşıklığını analiz etmek için kullanılır.

<img src="../assets/theta-notation.webp" width=700 height=680px>

{{< alert icon="➡️" text="Teta, fonksiyonu sabit faktörler içinde sınırlar" />}}

```bash
Θ(g(n)) = { f(n): c ve n0 pozitif sabitleri var
          tüm n ≥ n0 ve 0 ≤ c1g(n) ≤ f(n) ≤ c2g(n) olacak şekilde }
```
Yukarıdaki ifade, yeterince büyük `n` için `c`<sub>`1`</sub>`g(n)` ve `c2g(n)` arasında sıkıştırılabilecek şekilde `c1` ve `c2` pozitif sabitleri varsa, `Θ(g(n))` kümesine ait `f(n)` işlevi olarak tanımlanabilir.

Bir `f(n)` fonksiyonu, tüm `n ≥ n0` için `c`<sub>`1`</sub>`g(n)` ve `c`<sub>`2`</sub>`g(n)` arasında herhangi bir yerde bulunuyorsa, o zaman `f(n)`'nin asimptotik olarak sıkı bağlı olduğu söylenir.
