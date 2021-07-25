---
title: "Yığın"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "data-structures-1"
weight: 10
toc: true
---

Bu rehberde, yığın veri yapısı hakkında ve c# dilindeki implementasyonu hakkında bilgi edineceksiniz.

Yığın, LIFO prensibini takip eden doğrusal bir veri yapısıdır. 
Bu demektir ki yığından çıkarılacak ilk eleman, eklenen son elemandır.

Yığını üst üste birikmiş tabak yığını olarak düşünebilirsiniz.

<p align=center>
  <img src="../assets/stack-pile-of-plates.png"   height= 360px>
</p>


Burada yapabilecekleriniz:

- Üste tabak koymak

- Üstteki tabağı almak

Eğer alttaki bir tabağı almak isterseniz öncelikle üstteki tüm tabakları almak zorundasınız. Yığın veri yapısı da tam olarak bu şekilde çalışıyor.

&nbsp;
<hr>
&nbsp;

## Yığının LIFO Prensibi

Programlama terimlerine göre, yığının üstüne bir item koymak **push**, bir item almak ise **pop** olarak adlandırılır.

<p align=center>
  <img src="../assets/stack-push-pop.png" height= 360px>
</p>

Yukarıdaki resimde, item 3 son eklemesine rağmen ilk o çıkartılmıştır. **LIFO(Last In First Out) prensibi** tam olarak bu şekilde çalışır.

Bir yığını C, C++, Java, Python veya C# gibi herhangi bir programlama dilinde uygulayabiliriz, ancak belirtim hemen hemen aynıdır.

&nbsp;
<hr>
&nbsp;

## Yığının Basit İşlemleri

Yığın üzerinde farklı aksiyonlar gerçekleştirmemize izin veren bazı işlemler bulunmakta.

- **Push:** Yığının üstüne item ekler

- **Pop:** Yığının üstünden item çıkarır

- **IsEmpty:** Yığının boş olup olmadığını kontrol eder.

- **IsFull:** Yığının dolu olup olmadığını kontrol eder.

- **Peek:** Yığının en üstündeki itemin çıkarmadan değerine ulaşır.


## Yığın Veri Yapısının Çalışma Mantığı

İşlemlerimiz şu sırayı takip eder:

1\. Yığındaki en üstteki öğeyi takip etmek için `TOP` adlı bir işaretçi kullanılır.

2\. Yığın oluşturulduğunda değişkenin değerini -1'e eşitleriz. Böylece `TOP==-1` ile karşılaştırarak yığının doluluğunu kontrol edebiliriz.

3\.Yeni item eklediğimiz zaman,`TOP` değişkeninin değerini arttırırız ve yeni elemanı `TOP` olarak gösteririz.

4\. Eleman çıkarıldığında `TOP` değişkenini döndürürüz ve değerini azaltırız.

5\. Push işleminden önce, yığının zaten dolu olup olmadığı kontrol ederiz.

6\. Pop işleminden önce, yığının zaten boş olup olmadığını kontrol ederiz.

<p align=center>
  <img src="../assets/stack-operations.png" height= 360px>
</p>

&nbsp;
<hr>
&nbsp;

## C# Dilinde Yığın İmplementasyonu

Yaygın olarak yığın implementasyonunda diziler kullanılır ancak Listeler kullanılarak da implemente edilebilir.

```cs
class Program
    {
        static void Main(string[] args)
        {
            Stack stack = new Stack(5);
            stack.push(1);
            stack.push(2);
            stack.push(3);
            stack.push(4);
            stack.pop();
            Console.WriteLine("\nEleman çıkartıldıktan sonra dizi:");
            stack.printStack();
        }
    }
    class Stack
    {
        private readonly int[] arr;
        private int top; //üstteki elemanı gösterecek olan pointer değişkenimiz
        private int capacity; // yığın büyüklüğü

        // Yığın oluşturulur
        public Stack(int size)
        {
            arr = new int[size];
            capacity = size;
            top = -1;
        }

        //Ekleme işlemi
        public void push(int x)
        {
            if (isFull())
            {
                Console.WriteLine("YIĞIN DOLU");
                Environment.Exit(1);
            }

            Console.WriteLine("Eklenen sayı:\t" + x);
            arr[++top] = x;
        }

        // Silme İşlemi
        public int pop()
        {
            if (isEmpty())
            {
                Console.WriteLine("YIĞIN BOŞ");
                Environment.Exit(1);
            }
            return arr[top--];
        }

        //Yığın hacmini veren yardımcı fonksiyon
        public int size()
        {
            return top + 1;
        }

        // Yığın boş olup olmadığı kontrol edilir
        public Boolean isEmpty()
        {
            return top == -1;
        }

        // Yığın dolu olup olmadığı kontrol edilir
        public Boolean isFull()
        {
            return top == capacity - 1;
        }

        //Yığını yazdıran fonksiyon
        public void printStack()
        {
            for (int i = 0; i <= top; i++)
            {
                Console.WriteLine(arr[i]);
            }
        }
    }
```

&nbsp;
<hr>
&nbsp;

## Yığın Zaman Karmaşıklığı

Dizi bazlı yığın implementasyonu için, push ve pop işlemleri sabit yani `O(1)`  zaman alır.

&nbsp;
<hr>
&nbsp;

## Yığın Veri Yapısı Kullanımları

Yığın, uygulanması basit bir veri yapısı olmasına rağmen, çok güçlüdür. Yığının en yaygın kullanımları şunlardır:

- **Kelime ters çevirme -** Tüm harfleri yığına koyun ve hepsini dışarı atın. Yığının LIFO sıralamasından dolayı harfleri ters sırayla alacaksınız.

- **Derleyicilerde -** Derleyiciler, ifadeyi önek veya sonek formuna dönüştürerek `2 + 4 / 5 * (7 - 9)` gibi ifadelerin değerini hesaplamak için yığını kullanır.

- **Tarayıcılarda -** Tarayıcıdaki geri butonu daha önce ziyaret ettiğiniz tüm URL'leri yığına kaydeder.Her yeni bir sayfayı ziyaret ettiğinizde yığının en üstüne eklenir. Geri tuşuna bastığınızda geçerli URL yığından kaldırılır ve önceki URL'e erişim sağlanır.