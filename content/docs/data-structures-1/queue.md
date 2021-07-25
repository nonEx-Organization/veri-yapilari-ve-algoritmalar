---
title: "Kuyruk"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "data-structures-1"
weight: 11
toc: true
---

Bu rehberde, kuyruk yapısının ne olduğunu öğreneceksiniz. Ayrıca c# dilinde kuyruk implementasyonunu göreceksiniz.

Kuyruk, programlamada kullanışlı bir veri yapısıdır. Sinema salonunun önündeki bilet kuyruğuna benzer, kuyruğa ilk giren insan, bileti de ilk alacak kişidir.

Kuyruk, **FIFO(First In First Out)** kuralına uyar. Yani ilk giren eleman ilk çıkan elemandır.

<p align=center>
  <img src="../assets/queue.png"   width= 620px>
</p>

{{< alert icon="➡️" text="Kuyruk FIFO Temsili" />}}

Yukarıdaki resimde 1, 2'den önce kuyrukta tutulduğu için **FIFO** kuralından dolayı kuyruktan da ilk o çıkarılacaktır. 

Programlama terimlerine göre, kuyruğa yeni bir eleman eklemek **enqueue**, kuyruktan eleman çıkartmak ise **dequeue** olarak adlandırılır.

Bir kuyruğu C, C++, Java, Python veya C# gibi herhangi bir programlama dilinde uygulayabiliriz, ancak belirtim hemen hemen aynıdır.

&nbsp;
<hr>
&nbsp;

## Kuyruğun Basit İşlemleri

Kuyruk, aşağıdaki işlemlere izin veren bir veri yapısıdır:

- **Enqueue:** Kuyruğun sonuna bir eleman eklemek

- **Dequeue:** Kuyruğun önünden bir eleman çıkarmak

- **IsEmpty:** Kuyruğun boş olup olmadığını kontrol eder.

- **IsFull:** Kuyruğun dolu olup olmadığını kontrol eder.

- **Peek:** Kuyruğun en önündeki elemanı çıkarmadan değerine ulaşır.

&nbsp;
<hr>
&nbsp;

## Kuyruğun Çalışma Mantığı

İşlemlerimiz şu sırayı takip eder:

- `FRONT` ve `REAR` adında iki işaretci değişkenimiz bulunur.

- `FRONT` kuyruğun ilk elemanını izler.

- `REAR` kuyruğun son elemanını izler.

- Başlangıçta, `FRONT` ve `REAR` değişkenlerinin değeri -1 yapılır.

&nbsp;

### Enqueue İşlemi

- Kuyruğun dolu olup olmadığını kontrol ederiz.

- İlk eleman için, `FRONT` değerini 0 yaparız.

- `REAR` indeksini 1 artırırız.

- `REAR` ile işaret edilen indekse yeni elemanı ekleriz.

&nbsp;

### Dequeue İşlemi

- Kuyruğun boş olup olmadığını kontrol ederiz.

- `FRONT` ile işaret edilen indeksteki değer döndürülür.

- `FRONT` indeksini 1 artırırız.

- Son eleman için, `FRONT` ve `REAR` değerlerini -1 yaparız.

&nbsp;

<p align=center>
  <img src="../assets/queue-operations.png" width= 600px>
</p>

{{< alert icon="➡️" text="Enqueue ve Dequeue işlemleri" />}}
 
&nbsp;
<hr>
&nbsp;

## C# Dilinde Kuyruk Implementasyonu

Kuyrukları Java ve C/++'da uygulamak için genellikle dizileri kullanırız. C# dilini kullanacağımız için dizileri kullanacağız.

```cs
class Program
    {
        static void Main(string[] args)
        {
            Queue q = new Queue();
            q.deQueue();

            // 5 eleman ekleyelim
            q.enQueue(1);
            q.enQueue(2);
            q.enQueue(3);
            q.enQueue(4);
            q.enQueue(5);

            // 6.eleman kuyruk doluluğundan eklenemeyecek
            q.enQueue(6);

            // İlk gireni yani 1 sayısını çıkaracağız
            q.deQueue();

            // Artık 4 elemanımız var
            q.display();
        }
    }
public class Queue
    {
        static int SIZE = 5;
        int[] items = new int[SIZE];
        int front, rear;
        public Queue()
        {
            front = -1;
            rear = -1;
        }
        // Kuyruk dolu olup olmadığı kontrol edilir
        public bool isFull()
        {
            return (front == 0 && rear == SIZE - 1);
        }
        // Kuyruk boş olup olmadığı kontrol edilir
        public bool isEmpty()
        {
            return (front == -1);
        }
        //Ekleme İşlemi
        public void enQueue(int element)
        {
            if (isFull())
                Console.WriteLine("Kuyruk maksimum kapasiteye ulaştı");
            else {
                if (front == -1) //Eğer kuyruk tamamen boş ise
                    front = 0;
                rear++;
                items[rear] = element;
                Console.WriteLine("Kuyruğa eklenen sayı:\t" + element);
            }
        }
        public int deQueue()
        {
            int element;
            if (isEmpty()) {
                Console.WriteLine("Kuyrukta veri bulunmamakta");
                return (-1);
            }
            else {
                element = items[front];
                if (front >= rear){
                    front = -1;
                    rear = -1;
                }
                else {
                    front++;
                }
                Console.WriteLine("Kuyruktan silinen sayı:\t" + element);
                return (element);
            }
        }
        public void display()
        {
            if (isEmpty()){
                Console.WriteLine("Kuyrukta veri bulunmamakta");
            }
            else {
                Console.WriteLine("Kuyruk:\n");
                for (int i = front; i <= rear; i++)
                    Console.WriteLine(items[i] + "  ");
            }
        }
    }
```
 
&nbsp;
<hr>
&nbsp;

## Kuyruk Sınırlamaları

Aşağıdaki resimde göreceğiniz gibi, biraz kuyruğa ekleme ve kuyruktan çıkarma işleminden sonra, kuyruğun boyutu azaltıldı.

<p align=center>
  <img src="../assets/queue-limitations.png" width= 600px/>
</p>

{{< alert icon="➡️" text="Kuyruk sınırlamaları" />}}

Ve 0 ve 1 indekslerini yalnızca kuyruk sıfırlandığında ekleyebiliriz.

`REAR` son indekse ulaştıktan sonra, boş alanlara (0. ve 1. indeks) fazladan eleman depolayabilirsek, boş alanlardan yararlanabiliriz. Bu yapı, [dairesel kuyruk][circular-queue] adı verilen değiştirilmiş bir kuyruk tarafından gerçekleştirilir.

&nbsp;
<hr>
&nbsp;

## Karmaşıklık Analizi

Bir dizi kullanan bir kuyruğa alma ve kuyruğa alma işlemlerinin karmaşıklığı `O(1)`'dir.

&nbsp;
<hr>
&nbsp;

## Kuyruk Kullanımları

- CPU ve Disk Zamanlaması

- İki işlem arasında asenkron olarak veri transfer edilirken kuyruk senkronizasyon için kullanılır. Örnek: IO Buffers, pipes, file IO vb.

- Gerçek zamanlı sistemlerde kesintilerin bakımında

- Çağrı Merkezi telefon sistemleri, arayan kişileri sırayla tutmak için kuyrukları kullanır.

&nbsp;
<hr>
&nbsp;

# Önerilen Yazılar

- [Kuyruk Tipleri][queue-types]

- [Dairesel Kuyruk][circular-queue]

- [Deque Veri Yapısı][deque]

- [Öncelik Kuyruğu][priority-queue]

<!--
LINKS
-->

[circular-queue]: ../circular-queue
[queue-types]:    ../types-of-queue
[deque]:          ../deque
[priority-queue]: ../priority-queue
