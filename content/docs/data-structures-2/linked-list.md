---
title: "Bağlı Liste"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "data-structures-2"
weight: 10
toc: true
---


Bu rehberde, bağlı liste yapısının ne olduğunu öğreneceksiniz. Ayrıca c# dilinde kuyruk implementasyonunu göreceksiniz.

Bağlı liste, birbirine bağlı düğüm kümesini içeren doğrusal bir veri yapısıdır. Her bir düğüm kendi **verisini** ve kendisinden sonraki düğümün **adresini** tutar. Örneğin,

<p align=center>
  <img src="../assets/linked-list.png" width=100%  max-width=620px>
</p>

{{< alert icon="➡️" text="Bağlı Liste Veri Yapısı" />}}

Bir yerden başlamak zorundayız. Bu yüzden ilk düğümün adresine `HEAD` adında özel bir ad veriyoruz. Ayrıca bağlı listedeki son düğüm olarak da tanımlanabilir çünkü bu düğümün sıradaki adresi `NULL`'dır.

Bağlı Liste veri yapısının birkaç türü bulunmaktadır. Bu rehberde **tekli bağlı liste** üzerine yoğunlaşacağız. Bunlar: **tekli**, **çoklu** ve **dairesel** bağlı listedir. Diğer türler hakkında daha fazla bilgi öğrenmek için, [bağıl liste türlerini][types-of-linked-list] ziyaret edin.

{{< alert icon="➡️" >}}
**Not:** Daha önce hazine avı oyunu oynadıysanız her bir ipucu sıradaki ipucu hakkında bilgi içerir. Bağlı liste tam olarak bu şekilde çalışır.
{{< /alert >}}

&nbsp;
<hr>
&nbsp;

## Bağlı Liste Hakkında

Gelin, beraber bağlı listedeki her bir düğümün nasıl temsil edildiğini görelim. Her düğüm şunları içerir:

- Bir veri

- Diğer düğümün adresi

Bir yapı içinde hem veriyi hem de sonraki düğüm adresini şu şekilde temsil edebiliriz:

```cs
public class Node
{
    public int data;
    public Node next;
}
```

Bağlı bir liste düğümünün yapısını anlamak, onu kavramanın anahtarıdır.

Her bir düğümün bir verisi ve başka bir düğümün adresi vardır.
Bunun nasıl çalıştığını anlamak için üç öğeli basit bir bağlı Liste oluşturalım.

```cs
    //Düğümleri oluşturalım ve değer atayalım
    Node head;
    Node one = new Node { data = 1 };
    Node two = new Node { data = 2 };
    Node three = new Node { data = 3 };
    
    //Düğümleri bağlayalım
    one.next = two;
    two.next = three;
    three.next = null;
    
    //baştaki düğümün adresini kaydedelim
    head = one;
```
Sadece birkaç adımda, üç düğümlü basit bir bağlı liste oluşturduk.

<p align=center>
  <img src="../assets/linked-list-representation.png" width=100%  max-width=720px>
</p>

Bağlı listenin gücü, zinciri kırma ve ona yeniden katılma özelliğinden gelir. Örneğin, 1.düğüm ile 2.düğüm arasında veri değeri 4 olan düğüm koymak isterseniz, adımlar şöyle olacaktır:

- Yeni bir Node sınıfı oluşturun.

- Data değişkenine 4 değerini atayın.

- Next işaretcisini 2.düğümü gösterecek şekilde güncelleyin.

- 1.düğümün next işaretçisini oluşturduğunuz düğümü gösterecek şekilde güncelleyin.

Bir dizide benzer bir şey yapmak, sonraki tüm öğelerin konumlarını değiştirmeyi gerektirirdi.

Python,Java ve C# dillerinde aşağıda gösterildiği gibi sınıflar kullanılarak implemente edilebilir.

&nbsp;
<hr>
&nbsp;
 
## Bağlı Liste Faydaları

Listeler, C, C++, Python, Java ve C# gibi her programlama dilinde uygulanmasıyla popüler ve verimli veri yapılarından biridir.

Bunun dışında bağlı listeler, işaretçilerin nasıl çalıştığını öğrenmenin harika bir yoludur. Bağlı listeleri nasıl değiştireceğiniz konusunda pratik yaparak kendinizi grafikler ve ağaçlar gibi daha gelişmiş veri yapılarını öğrenmeye hazırlayabilirsiniz.

&nbsp;
<hr>
&nbsp;
 
## C# Dilinde Bağlı Liste İmplementasyonu

```cs
class Program
{
    static void Main(string[] args)
    {
        //Düğümleri oluşturup verilerini atayalım
        LinkedList linkedList = new LinkedList();
        linkedList.head = new Node(1);
        Node second = new Node(2);
        Node third = new Node(3);

        //Düğümleri bağlayalım
        linkedList.head.next = second;
        second.next = third;

        //Düğümleri yazdıralım
        while (linkedList.head != null)
        {
            Console.WriteLine(linkedList.head.data + " ");
            linkedList.head = linkedList.head.next;
        }
    }
}

public class LinkedList
{
    public Node head;
}

public class Node
{
    public Node(int value)
    {
        data = value;
        next = null;
    }
    public int data;
    public Node next;
}
```

&nbsp;
<hr>
&nbsp;
 
## Bağlı Liste Karmaşıklığı

Zaman Karmaşıklığı

|&nbsp;| En Kötü Durum | Ortalama Durum |
|------|---------------|----------------|
|Arama |      O(n)     |       O(n)     |
|Ekleme|      O(1)     |       O(1)     |
|Silme |      O(1)     |       O(1)     |

Uzay Karmaşıklığı: `O(n)`

&nbsp;
<hr>
&nbsp;
 
## Bağlı Liste Kullanımları

- Dinamik bellek ayırma

- Yığın ve Kuyruk implementasyonlarında

- Yazılımlardaki **geri alma** özelliğinde

- Hash tabloları ve Graflarda


<!--
LINKS
-->
[types-of-linked-list]:../types-of-linked-list