---
title: "Çift uçlu kuyruk"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "data-structures-1"
weight: 17
toc: true
---

Bu rehberde, çift uçlu kuyruk yapısının ne olduğunu öğreneceksiniz. Ayrıca c# dilinde kuyruk implementasyonunu göreceksiniz.

**Deque** yada diğer adıyla çift uçlu kuyruk, eleman eklemenin önden yada arkadan gerçekleştirilebildiği bir tür [kuyruk][queue] tipidir. Bundan dolayı FIFO(İlk giren ilk çıkar) kuralına uymaz.

<p align=center>
  <img src="../assets/deque-representation.png" width= 620px>
</p>

{{< alert icon="➡️" text="Deque Temsili" />}}

&nbsp;
<hr>
&nbsp;

## Deque Çeşitleri

- Giriş Kısıtlamalı Deque

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Bu deque yapısında, veri girişi tek taraftan kısıtlanmıştır ancak iki taraftan da silmeye izin verir.

- Çıkış Kısıtlamalı Deque

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Bu deque yapısında, veri çıkışı tek taraftan kısıtlanmıştır ancak iki taraftan da veri eklemeye izin verir.


&nbsp;
<hr>
&nbsp;

## Deque İşlemleri

Aşağıda deque yapısının [dairesel dizi][circular-queue] implementasyonu bulunmakta. Bu dairesel dizide eğer dizi doluysa başlangıçtan başlarız.

Ancak doğrusal dizi implementasyonunda eğer dizi dolu ise daha fazla eleman eklenemez. Aşağıdaki her bir işlem için, eğer dizi dolu ise "taşma mesajı" fırlatılır.

Aşağıdaki işlemler yapılmadan önce bu adımlar takip edilir.

1. N boyutunda bir dizi(Deque) oluşturun.

2. Birinci indekste 2 işaretçiyi oluşturun ve `front = -1` ve `rear = 0` değerlerini atayın.

<p align=center>
  <img src="../assets/deque-init-array.png" width= 370px>
</p>

{{< alert icon="➡️" text="Deque yapısı için diziyi  ve işaretçi değişkenleri oluştur" />}}


### 1. Öne ekleme

1.`front` indeksi kontrol edilir.

<p align=center>
  <img src="../assets/deque-check-front.png" width= 370px>
</p>

2. Eğer `front < 1` ise `front = n - 1` yaparak tekrar oluşturuyoruz.(Son Indeks)

<p align=center>
  <img src="../assets/deque-shift-front.png" width= 370px>
</p>

{{< alert icon="➡️" text="front degiskenini sona dogru kaydır" />}}

3. Yukarıdaki koşul sağlanmıyorsa, `front`'u bir azaltın.

4. `dizi[front]` indeksine 5 değerini ekleyin.

<p align=center>
  <img src="../assets/deque-enqueue-front.png" width= 370px>
</p>

{{< alert icon="➡️" text="front degiskenini sona dogru kaydır" />}}


### 2. Arkaya ekleme

1. Dizi dolu mu kontrol edilir.

<p align=center>
  <img src="../assets/deque-check-full.png" width= 370px>
</p>

2. Eğer deque doluysa, `rear = 0` yaparak tekrar oluşturuyoruz.

3. Yukarıdaki koşul sağlanmıyorsa, `rear`'ı bir azaltın.

<p align=center>
  <img src="../assets/deque-inc-rear.png" width= 370px>
</p>

4. `dizi[rear]` indeksine 5 değerini ekleyin.

<p align=center>
  <img src="../assets/deque-enqueue-rear.png" width= 370px>
</p>


### 3. Önden Silme

1. Dizi boş mu kontrol edilir.

<p align=center>
  <img src="../assets/deque-check-empty.png" width= 370px>
</p>

2. Eğer deque boşsa(yani `front = -1`), silme işlemi gerçekleştirilemez.

3. Eğer deque sadece bir elemana sahipse(yani `front = rear`),`front = -1` ve `rear = -1` değerleri atanır.

4. Eğer `front` sonda ise(yani `front = n - 1`), `front = 0` ataması yapılır.

5. Yukarıdaki koşullar gerçekleşmediyse, `front = front + 1` ataması yapılır.

<p align=center>
  <img src="../assets/deque-inc-front.png" width= 370px>
</p>


### 4. Arkadan Silme

1. Dizi boş mu kontrol edilir.

<p align=center>
  <img src="../assets/deque-check-empty.png" width= 370px>
</p>

2. Eğer deque boşsa(yani `front = -1`), silme işlemi gerçekleştirilemez.

3. Eğer deque sadece bir elemana sahipse(yani `front = rear`),`front = -1` ve `rear = -1` değerleri atanır.

4. Eğer `rear` sonda ise(yani `rear = 0`), `rear = n - 1` ataması yapılır.

5. Yukarıdaki koşullar gerçekleşmediyse, `rear = rear - 1` ataması yapılır.

<p align=center>
  <img src="../assets/deque-decrease-rear.png" width= 370px>
</p>


### 5. Boşluk Kontrolü

Bu işlem deque yapısının boş olup olmadığını kontrol eder. Eğer `front = -1` ise deque boştur.

### 6. Doluluk Kontrolü

Bu işlem deque yapısının dolu olup olmadığını kontrol eder. Eğer `front = 0` ve `rear = n - 1` ise deque doludur.

&nbsp;
<hr>
&nbsp;

## C# Dilinde Deque Implementasyonu

 ```cs
 class Program
    {
        static void Main(string[] args)
        {
            Deque dq = new Deque(4);
            dq.insertToRear(12);
            dq.insertToRear(14);

            Console.WriteLine("Sondaki eleman:\t" + dq.getRear());
            dq.deleteFromRear();
            Console.WriteLine("Silindikten sonra sondaki eleman: " + dq.getRear());

            dq.insertToFront(13);
            Console.WriteLine("Öndeki eleman:\t" + dq.getFront());
            dq.deleteFromFront();

            System.out.println("Silindikten sonra baştaki eleman: " + +dq.getFront());
        }
    }
  public class Deque
    {
        const int MAX = 100;// Dizi boyutu
        int[] arr;
        int front;
        int rear;
        int size;

        public Deque(int size) {
            arr = new int[MAX];
            front = -1;
            rear = 0;
            this.size = size;
        }
        
        //Deque doluluk kontrolü
        public bool isFull() => ((front == 0 && rear == size - 1) || front == rear + 1);
        
        //Deque boşluk kontrolü
        public bool isEmpty() => (front == -1);

        //Önden Eleman Ekleme
        public void insertToFront(int value)
        {
            if (!isFull()) { // dolu değilse
                if (front == -1) { // dizi boş ise
                    front = 0;
                    rear = 0;
                }
                else if (front == 0)// front eğer 1'den küçükse
                    front = size - 1;
                else 
                    front = front - 1;

                arr[front] = value;
            }
        }

        //Sondan Eleman Ekleme
        public void insertToRear(int value)
        {
            if (!isFull()) { // dolu değilse
                if (front == -1) { // dizi boş ise
                    front = 0;
                    rear = 0;
                }
                else if (rear == size - 1)
                    rear = 0;
                else
                    rear = rear + 1;

                arr[rear] = value;
            }
        }

        //Önden Eleman Silme
        public void deleteFromFront()
        {
            if (!isEmpty()) {
                if (front == rear) { //sadece bir eleman varsa
                    front = -1;
                    rear = -1;
                }
                else if (front == size - 1) // front sonda
                    front = 0;
                else
                    front = front + 1;
            }

        }

        //Sondan Eleman Silme
        public void deleteFromRear()
        {
            if (!isEmpty()){
                if (front == rear) // Bir elemana sahipse
                {
                    front = -1;
                    rear = -1;
                }
                else if (rear == 0) //rear sonda ise
                    rear = size - 1;
                else 
                    rear = rear - 1;
            }
        }

        //front işaretçi değeri elde etme
        public int getFront() => isEmpty() ? -1 : arr[front];

        //rear işaretçi değerini elde etme
        public int getRear() => (isEmpty() || rear < 0) ? -1 : arr[rear];

    }
 
 ```

&nbsp;
<hr>
&nbsp;

## Zaman Karmaşıklığı

Yukarıdaki tüm işlemlerin zaman karışıklığı sabit olarak `O(1)`dir

&nbsp;
<hr>
&nbsp;

## Deque Veri Yapısının Kullanımları

- Yazılımdaki geri alma işlemlerinde

- Tarayıcılardaki geçmişi saklamada

- [Yığın][stack] ve [kuyruk][queue] implementasyonlarında

<!--
LINKS
-->

[queue]:../queue
[stack]:../stack  
[circular-queue]: ../circular-queue