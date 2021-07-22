---
title: "Böl ve Fethet Algoritması"
description: ""
lead: ""
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "introduction"
weight: 6
toc: true
---

Bu rehberde, **böl ve fethet** algoritmasının nasıl çalıştığını öğreneceksiniz. Ayrıca yinelemeli bir problemi çözmek için böl ve fethet yaklaşımını diğer yaklaşımlarla karşılaştıracağız.

Böl ve Fethet algoritmasının büyük problemleri çözerkenki stratejisi şudur:

1. Problemi daha küçük problemlere ayırın.

2. Küçük problemleri çözün.

3. Bunları birleştirerek istenen çıktıyı elde edin.

Böl ve Fethet algoritmasında **özyineleme** kullanılır. Farklı programlama dillerinde özyinelemeyi öğrenmek için:

- [Java'da özyineleme][java-recursive]

- [Python'da özyineleme][python-recursive]

- [C++'da özyineleme][cpp-recursive]

&nbsp;
<hr>
&nbsp;

## Böl ve Fethet Algoritması Nasıl Çalışır?

İşte ilgili adımlar:

1. **Böl:**  Verilen problemi özyineleme kullanarak daha küçük probleme bölün

2. **Fethet:** Daha küçük problemleri özyineleme ile çözün. Eğer yeteri kadar küçükse, direkt çözün.

3. **Birleştir:** Asıl problemi çözmek için özyinelemeli sürecin parçası olan alt problemlerin çözümlerini birleştirin.

Bu kavramı bir örnek yardımıyla anlayalım.

Burada, böl ve yönet yaklaşımını kullanarak bir diziyi sıralayacağız.(*Yani [Birleştirme sıralaması][merge-sort] ile*)

1. Verilen dizi şöyle olsun:

<p align="center">
  <img src="../assets/divide-and-conquer-array.webp" height=100>
</p>

> Birleştirme sırası için verilen dizi

2. Diziyi iki yarıma **bölün**.

<p align="center">
  <img src="../assets/divide-and-conquer-array-divided.webp" height=200>
</p>

> İki alt parçaya bölün

3. Tek elaman kalana dek diziyi özyinelemeli şekilde alt parçalara bölmeye devam edin.

<p align="center">
  <img src="../assets/divide-and-conquer-array-divided-recursive.webp" height=300>
</p>

> Diziyi daha küçük parçalara bölün

4. Şimdi, sıralanmış şekilde tüm elemanları birleştirin. Burada, **fethet** ve **birleştir** adımları sırayla gerçekleşir.

<p align="center">
  <img src="../assets/divide-and-conquer-combine.webp" height=300>
</p>

> küçük parçaları birleştirin

&nbsp;
<hr>
&nbsp;

## Zaman Karmaşıklığı

Böl ve yönet algoritmasının karmaşıklığı, [master teoremi][master-theorem] kullanılarak hesaplanır.


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
Özyinelemeli bir problemin zaman karmaşıklığını bulmak için bir örnek alalım.
Bir birleştirme sıralaması için denklem şu şekilde yazılabilir:

```bash
  T(n) = aT(n/b) + f(n)
       = 2T(n/2) + O(n)
   
  a = 2 (her seferinde bir problem 2 alt probleme bölünür)
  n/b = n/2 (her alt problemin boyutu girdinin yarısıdır)
  f(n) = Problemi bölmek ve alt problemleri birleştirmek icin geçen süre
  T(n/2) = O(n log n) (Bunu anlamak için, master teoremine bakın)

  Öyleyse, T(n) = 2T(n log n) + O(n)
            ≈ O(n log n)

```

&nbsp;
<hr>
&nbsp;

## Böl ve Fethet vs Dinamik Yaklaşım

Böl ve fethet yaklaşımı, bir problemi daha küçük alt problemlere böler; bu alt problemler özyinemeli şekilde çözülür. Her alt problemin sonucu ileride ulaşılmak üzere saklanmaz. Buna karşılık, dinamik bir yaklaşımda, her bir alt problemin sonucu ileride ulaşılmak üzere saklanır.

Aynı alt problem birden çok kez çözülmediğinde böl ve yönet yaklaşımını kullanın. Bir alt problemin sonucu gelecekte birden çok kez kullanılacaksa dinamik yaklaşımı kullanın.

Bunu bir örnekle açıklayalım. Fibonacci serisini bulmaya çalıştığımızı varsayalım.

**Böl ve Fethet Yaklaşımı**

```c
  fib(n)
    If n < 2, return 1
    Else , return f(n - 1) + f(n -2)
```

**Dinamik Yaklaşım**
```c
  mem = []
  fib(n)
    If n in mem: return mem[n] 
    else,     
        If n < 2, f = 1
        else , f = f(n - 1) + f(n -2)
        mem[n] = f
        return f
```
Dinamik yaklaşımda, `mem` değişkeni her bir alt problemin sonucunu tutuyor.

&nbsp;
<hr>
&nbsp;

## Böl ve Fethet Algoritmasının Avantajları

- Saf halde iki matrisin çarpımındaki zaman karmaşıklığı `O(n`<sup>`3`</sup>`)` iken böl ve fethet algoritması kullanılarak(Bknz. **Strassen'in Matris Çarpımı**) bulunan karmaşıklık `O(n`<sup>`2.8074`</sup>`)` olarak hesaplanır. Bu yaklaşım aynı zamanda *Hanoi Kulesi* gibi diğer sorunları da basitleştirir.

- Bu yaklaşım, çok işlemli sistemler için uygundur.

- Bellek önbelleklerini verimli bir şekilde kullanır.

&nbsp;
<hr>
&nbsp;

## Böl Ve Fethet Kullanımları

- [İkili Arama][binary-search]

- [Birleştirme sıralaması][merge-sort]

- [Hızlı sıralama][quick-sort]

- Strassen's matrix çarpımı

- Karatsuba algoritması


<!-- REFERENCED LINKS -->
[java-recursive]:https://www.programiz.com/java-programming/recursion
[python-recursive]:https://www.programiz.com/python-programming/recursion
[cpp-recursive]:https://www.programiz.com/cpp-programming/recursion
[merge-sort]:../../sorting-search-algorithm/merge-sort
[master-theorem]:../master-theorem
[quick-sort]:../../sorting-search-algorithm/quick-sort
[binary-search]:../../sorting-search-algorithm/binary-search