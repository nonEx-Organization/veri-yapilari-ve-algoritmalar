---
title: "Bağlı Liste Tipleri"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "data-structures-2"
weight: 12
toc: true
---

Bu rehberde, bağlı listenin farklı türlerini öğreneceksiniz. Ayrıca c# dilinde kuyruk implementasyonunu göreceksiniz.

Bağlı listenin türlerini öğrenmeden önce [bağlı liste veri yapısı][linked-list] hakkında bilgi sahibi olduğunuzdan emin olun.

Bağlı listenin yaygın 3 türü vardır.

- [Tek Bağlı Liste][singly-linked-list]

- [Çift Bağlı Liste][doubly-linked-list]

- [Dairesel Bağlı Liste][circular-linked-list]

&nbsp;
<hr>
&nbsp;

## Tek Bağlı Liste

En yaygın olanıdır. Her bir düğümün verisi  ve sıradaki düğümün adresini taşıyan işaretcisi vardır.

<p align=center>
  <img src="../assets/singly-linked-list.png" width=100%  max-width=620px>
</p>

Her bir düğüm şu şekilde temsil edilir:

```cs
public class Node
{
    public int data;
    public Node next;
}
```

Üç elemanlı tek bağlı bir liste şu şekilde oluşturulabilir:

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

&nbsp;
<hr>
&nbsp;

## Çift Bağlı Liste

Çift bağlı listede önceki düğümü gösteren bir işaretçi ekliyoruz. Böylece ileri ve geri olmak üzere iki yönde de ilerleyebiliyoruz.

<p align=center>
  <img src="../assets/doubly-linked-list.png" width=100%  max-width=620px>
</p>

Her bir düğüm şu şekilde temsil edilir:

```cs
public class Node
{
    public int data;
    public Node next;
    public Node prev;
}
```

Üç elemanlı çift bağlı bir liste şu şekilde oluşturulabilir:

```cs
    //Düğümleri oluşturalım ve değer atayalım
    Node head;
    Node one = new Node { data = 1 };
    Node two = new Node { data = 2 };
    Node three = new Node { data = 3 };
    
    //Düğümleri bağlayalım
    one.next = two;
    one.prev = null;

    two.next = three;
    two.prev = one;

    three.next = null;
    three.prev = two;

    //baştaki düğümün adresini kaydedelim
    head = one;
```

&nbsp;
<hr>
&nbsp;

## Dairesel Bağlı Liste

Dairesel bağlı liste, son elemanın ilk elemana bağlı olduğu bağlı listenin bir varyasyonudur. Bu durum, dairesel bir döngü oluşturur.

<p align=center>
  <img src="../assets/circular-linked-list.png" width=100%  max-width=620px>
</p>

Dairesel bağlı bir liste, tek bağlı veya çift bağlı olabilir.

- Tek bağlı liste için, son elemanın işaretcisi ilk itemi gösterir.

- Çift bağlı liste için, ilk elemanın `prev` işaretcisi son elemanı gösterir.

Üç elemanlı dairesel tek bağlı bir liste şu şekilde oluşturulabilir:

```cs
    //Düğümleri oluşturalım ve değer atayalım
    Node head;
    Node one = new Node { data = 1 };
    Node two = new Node { data = 2 };
    Node three = new Node { data = 3 };
    
    //Düğümleri bağlayalım
    one.next = two;
    two.next = three;
    three.next = one;

    //baştaki düğümün adresini kaydedelim
    head = one;
```

<!--
LINKS
-->
[linked-list]:../linked-list
[singly-linked-list]:#tek-bağlı-liste
[doubly-linked-list]:#çift-bağlı-liste
[circular-linked-list]:#dairesel-bağlı-liste