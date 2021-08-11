---
title: "Dairesel Kuyruk"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "data-structures-1"
weight: 13
toc: true
---

Bu rehberde, kuyruk yapısının ne olduğunu öğreneceksiniz. Ayrıca c# dilinde kuyruk implementasyonunu göreceksiniz.

Dairesel bir sıra, son öğenin ilk öğeye bağlandığı [normal bir kuyruğun][queue-page] genişletilmiş versiyonudur.Böylece daire benzeri bir yapı oluşturur.

<p align=center>
  <img src="../assets/circular-representation.png"   width= 320px>
</p>

{{< alert icon="➡️" text="Dairesel Kuyruk Temsili" />}}

Dairesel Kuyruk, normal kuyruktaki büyük sınırlamanın önüne geçer. Normal bir kuyrukta ekleme ve çıkartma işlemlerinden sonra kullanılmayan boş alanlar olacaktır.

<p align=center>
  <img src="../assets/why-circular-queue.png" width= 320px>
</p>

{{< alert icon="➡️" text="Normal Kuyruğun Sınırlandırılması" />}}

Buradaki 0. ve 1. indeksler ancak kuyruk sıfırlandıktan sonra(tüm elemanlar silindikten sonra) kullanılabilir olacaklar. Bu durum da kuyruğun asıl boyutunu azaltır.

&nbsp;
<hr>
&nbsp;

## Dairesel Kuyruk Çalışma Mantığı

Dairesel Kuyruk, dairesel artış süreciyle çalışır. Yani işaretçi değişkenimizi arttırmaya çalıştığımızda kuyruğun sonuna ulaşırsak kuyruğun başından başlarız.

Burada dairesel artış, kuyruk boyutu ile modulü ile gerçekleştirilir. Yani,

`if REAR + 1 == 5 (taşma!), REAR = (REAR + 1) % 5 = 0 (kuyruk başlangıcı)`

&nbsp;
<hr>
&nbsp;

## Dairesel Kuyruk İşlemleri

İşlemlerimiz şu sırayı takip eder:

- `FRONT` ve `REAR` adında iki işaretci değişkenimiz bulunur.

- `FRONT` kuyruğun ilk elemanını izler.

- `REAR` kuyruğun son elemanını izler.

- Başlangıçta, `FRONT` ve `REAR` değişkenlerinin değeri -1 yapılır.

&nbsp;

### Enqueue İşlemi

- Kuyruğun dolu olup olmadığını kontrol ederiz.

- İlk eleman için, `FRONT` değerini 0 yaparız.

- `REAR` indeksini dairesel olarak 1 artırırız.(Eğer `REAR` değişkeni sona ulaşırsa artmaya kuyruğun başından başlayacaktır.)

- `REAR` ile işaret edilen indekse yeni elemanı ekleriz.

&nbsp;

### Dequeue İşlemi

- Kuyruğun boş olup olmadığını kontrol ederiz.

- `FRONT` ile işaret edilen indeksteki değer döndürülür.

- `FRONT` indeksini dairesel olarak 1 artırırız.

- Son eleman için, `FRONT` ve `REAR` değerlerini -1 yaparız.

&nbsp;

Yine de, dolu bir kuyruk kontrolünde ek durumlar vardır:

- Durum 1: `FRONT` = 0 && `REAR == SIZE - 1`

- Durum 2: `FRONT = REAR + 1`

İkinci durumda  `REAR` değişkeni dairesel artış nedeniyle 0'dan başladığında ve değeri `FRONT` değişkenin değerinden sadece 1 eksik olduğunda kuyruğun dolu olduğu anlaşılır.

<p align=center>
  <img src="../assets/circular-queue-operations.png" width= 320px>
</p>

&nbsp;
<hr>
&nbsp;

## C# Dilinde Kuyruk Implementasyonu

Kuyrukları uygulamak için genellikle dizileri kullanılır. Ancak list yapılarını kullanarak da implementasyonunu gerçekleştirebiliriz.

```cs
class Program
    {
        static void Main(string[] args)
        {
            CQueue q = new CQueue();
            // Başarısız çünkü front = -1
            q.deQueue();

            q.enQueue(1);
            q.enQueue(2);
            q.enQueue(3);
            q.enQueue(4);
            q.enQueue(5);

            // Eleman çıkarma başarısız çünkü front == 0 && rear == SIZE - 1
            q.enQueue(6);

            q.deQueue();
            q.enQueue(7);

            q.display();

            // Eleman çıkarma başarısız çünkü front == rear + 1
            q.enQueue(8);
        }
    }
public class CQueue
    {
        static int SIZE = 5; // Dairesel Kuyruk genişliği
        static int front, rear;
        int[] items = new int[SIZE];

        public CQueue()
        {
            front = -1;
            rear = -1;
        }

        // Kuyruğun dolu olup olmadığı kontrol edilir
        public bool isFull()
        {
            if (front == 0 && rear == SIZE - 1){ // Önden ve arkadan dolu
                return true;
            }
            if (front == rear + 1){
                return true;
            }
            return false;
        }

        // Kuyruğun boş olup olmadığı kontrol edilir
        public bool isEmpty()
        {
            return front == -1 ? true : false;
        }

        // Kuyruğa eleman ekleme
        public void enQueue(int element)
        {
            if (!isFull()) // Dolu değilse
            {
                if (front == -1)
                    front = 0;
                rear = (rear + 1) % SIZE;
                items[rear] = element;
                Console.WriteLine("Kuyruğa eklenen eleman:\t" + element);
            }
        }

        // Kuyruğa eleman çıkarma
        public int deQueue()
        {
            int element;
            if (!isEmpty()){ //Boş değilse
                element = items[front];
                if (front == rear){
                    front = -1;
                    rear = -1;
                }
                else{
                    front = (front + 1) % SIZE;
                }
                return (element);
            }
            else return -1;
        }

        public void display()
        {
            int i;
            if (!isEmpty()) //Boş değilse
            {
                for (i = front; i != rear; i = (i + 1) % SIZE)
                    Console.WriteLine(items[i] + " ");
            }
        }
    }
```

&nbsp;
<hr>
&nbsp;

## Dairesel Kuyruk Karmaşıklık Analizi

Bir dizi kullanan dairesel kuyruk yapısı için kuyruğa alma ve kuyruğa alma işlemlerinin karmaşıklığı `O(1)`'dir.

&nbsp;
<hr>
&nbsp;

## Dairesel Kuyruk Kullanımları

- CPU Zamanlaması

- Hafıza Yönetimi

- Trafik Yönetimi

<!--
LINKS
-->
[queue-page]:../queue