---
title: "Master Teoremi"
description: ""
lead: ""
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "introduction"
weight: 5
toc: true
---

Bu rehberde, master teoremin ne olduğunu ve tekrarlayan 
ilişkileri çözmek için nasıl kullanıldığını öğreneceksiniz.

Master teoremi, aşağıdaki formun tekrarlayan ilişkilerini çözmek için bir formüldür:

```bash
T(n) = aT(n/b) + f(n)

n = girdi sayısı

a = rekürsifteki alt problemlerin sayısı

n/b = Her alt problemin boyutu. Her alt problemin 
      aynı boyuta sahip olduğu varsayılır

f(n) = Problemi bölmenin maliyeti ve
      alt problemleri birleştirme maliyeti dahil
      rekürsif problemin dışında yapılan işin maliyeti
```

Asimptotik olarak pozitif bir fonksiyon, yeterince büyük bir `n` değeri için `f(n) > 0`'a sahip olduğu anlamına gelir.`

> Master teoremi, rekürsif ilişkilerin zaman karmaşıklığının basit ve hızlı bir şekilde hesaplanmasında kullanılır.

&nbsp;
<hr>
&nbsp;

## Master Teoremi

Eğer a ≥ 1 ve b > 1 sabit ise ve f(n) asimptotik olarak pozitif bir fonksiyon ise, o zaman  rekürsif bir ilişkinin zaman karmaşıklığı aşağıdaki şekilde verilir.

<pre>
T(n) = aT(n/b) + f(n)

T(n) aşağıdaki asimptotik sınırlara sahiptir:

    1. If f(n) = O(n<sup>log<sub>b</sub> a-ϵ</sup>) => T(n) = Θ(n<sup>log<sub>b</sub> a </sup>).  

    2. If f(n) = Θ(n<sup>log<sub>b</sub>a</sup>)) => T(n) = Θ(n<sup>log<sub>b</sub>a</sup> * log n).

    3. If f(n) = Ω(n<sup>log<sub>b</sub> a+ϵ</sup>)) => T(n) = Θ(f(n)).

</pre>

Yukarıdaki koşulların her biri şu şekilde yorumlanabilir:

1. Her düzeydeki alt problemleri çözmenin maliyeti belirli bir faktör kadar artarsa, `f(n)`'nin değeri n<sup>log<sub>b</sub>a</sup> 'dan polinomsal olarak daha küçük olacaktır. Bu durumda zaman karmaşıklığı n<sup>log<sub>b</sub>a</sup> olacaktır

2. Her düzeyde alt problemi çözmenin maliyeti hemen hemen eşitse, `f(n)`'nin değeri n<sup>log<sub>b</sub>a</sup> olacaktır. Bu durumda zaman karmaşıklığın<sup>log<sub>b</sub>a</sup> * log n olacaktır

3. Her seviyedeki alt problemleri çözmenin maliyeti belirli bir faktör kadar azalırsa, `f(n)`'nin değeri n<sup>log<sub>b</sub>a</sup>'dan polinomsal olarak daha büyük olacaktır. Bu durumda zaman karmaşıklığı `f(n)` olacaktır.

&nbsp;
<hr>
&nbsp;

## Master Teoremin Çözülmüş Örneği

```bash
  T(n) = 3T(n/2) + n2
  
  Buradan,

  a = 3
  n/b = n/2
  f(n) = n2

  logb a = log2 3 ≈ 1.58 < 2

  f(n) < nlogb a+ϵ , burada ϵ sabit bir sayıdır.

  3.Durum buraya uyuyor

  Sonuç olarak, T(n) = f(n) = Θ(n2) 

```

&nbsp;
<hr>
&nbsp;

## Master Teorem Sınırlamaları

Master Teorem aşağıdaki durumlarda kullanılamaz:

1. `T(n)` eğer tekdüze bir fonksiyon  değilse. Örnek: `T(n) = sin n`

2. `T(n)` eğer polinom fonksiyonu  değilse. Örnek: `f(n) =2`<sup>`n`</sup>

3. `a` eğer sabit bir sayı  değilse. Örnek: `a=2n`

4. `a < 1`

