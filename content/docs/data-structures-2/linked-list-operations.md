---
title: "Bağlı Liste İşlemleri"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "data-structures-2"
weight: 11
toc: true
---

Bu rehberde, bağlı liste üzerindeki farklı işlemleri öğreneceksiniz. Ayrıca c# dilinde kuyruk implementasyonunu göreceksiniz.

Bağlı listeler üzerinde farklı işlemler yapmamızı sağlayan çeşitli bağlı liste işlemleri vardır.

İşte bu makalede ele alacağımız temel bağlantılı liste işlemlerinin bir listesi.

- [Traversal][traversal] - Bağlı listedeki her elemana erişme

- [Ekleme][insertion] - Bağlı listeye yeni bir düğüm ekleme

- [Silme][deletion] - Bağlı listedeki bir düğümü kaldırma

- [Arama][search] - Bağlı listede düğüm arama

- [Sıralama][sort] - Bağıl listenin düğümlerini sıralama

Yukarıdaki bağlı liste işlemlerine detaylıca girmeden önce [bağıl liste][linked-list] hakkında bilgi sahibi olduğunuzdan emin olun.

### Bağlı Liste Hakkında Hatırlanması Gerekenler

- Bağlı listenin ilk düğümünü `head` olarak işaretlenir.

- Bağlı listenin son düğümünde `next` işaretçisi `null`'dır. Eğer sıradaki düğümün `next == null` ise bağlı listenin sonuna ulaşılır.

Tüm örneklerde, bağlı listenin aşağıdaki gibi düğüm yapısına sahip üç düğüm olduğunu varsayacağız:

`1 ---> 2 ---> 3`

```cs
public class Node
{
    public int data;
    public Node next;
}
```
&nbsp;
<hr>
&nbsp;

## Bağlı Listede Gezinme

Bağlı listenin içeriğini göstermek oldukça basit. `Temp` işaretcisini `head`'ten başlatıp bir sonrakine taşımaya devam ediyoruz ve içeriğini gösteriyoruz.

`Temp` işaretçimiz `null` olduğunda bağlı listenin sonuna geldiğimizi anlıyoruz ve while döngüsünden çıkıyoruz.

```cs
Node temp = head;
Console.WriteLine('Bağlı Liste Elemanları\n')

while(temp != null) {
  Console.WriteLine(temp +' --> ');
  temp = temp.next;
}
```
Programın çıktısı aşağıdaki gibi olacaktır:
```cs
Bağlı Liste Elemanları
 1 ---> 2 ---> 3 --->
```
&nbsp;
<hr>
&nbsp;

## Bağlı Listeye Eleman Ekleme

Bağlı listenin başına, ortasına yada sonuna eleman ekleyebilirsiniz.

### Başa Ekleme

- Yeni bir düğüm oluştur.

- Data değişkenine istediğiniz değerini atayın.

- Yeni düğümün next işaretçisini `head`'i gösterecek şekilde güncelleyin.

- `head` işaretçisinde oluşturduğunuz düğümü gösterin.

```cs
Node newNode = new Node { data = 5 };
newNode.next = head;
head = newNode;
```

### Sona Ekleme

- Yeni bir düğüm oluştur.

- Data değişkenine istediğiniz değerini atayın.

- Son düğüme kadar gidin.

- Son düğümün next işaretçisini oluşturduğunuz düğümü gösterecek şekilde güncelleyin.

```cs
Node newNode = new Node { data = 5 };
newNode.next = null;
Node temp = head;

while(temp != null) {
  temp = temp.next;
}

temp.next = newNode;
```

### Ortaya Ekleme

- Yeni bir düğüm oluştur.

- Data değişkenine istediğiniz değerini atayın.

- Istenilen indekse kadar düğümler arasında gezinin.

- `next` işaretçilerini yeni düğüm aralarında olacak şekilde güncelleyin.

```cs
Node newNode = new Node { data = 5 };
newNode.next = null;
Node temp = head;

for(int i=2; i < position; i++) {
  if(temp.next != null) {
    temp = temp.next;
  }
}
newNode.next = temp.next;
temp.next = newNode;
```

&nbsp;
<hr>
&nbsp;

## Bağlı listeden Eleman Silme

Bağlı listenin başından, ortasından yada sonundan eleman silebilirsiniz.

### Baştan Silme

- `Head` işaretçisini ikinci düğüm olarak güncelleyin.

```cs
head = head.next;
```

### Soldan Silme

- Sondan ikinci elemana kadar gezinin.

- `next` işaretçisini `null` olarak belirtin.

```cs
Node temp = head;
while(temp.next.next != null){
  temp = temp.next;
}
temp.next = null;
```

### Ortadan Silme

- Silinecek elemandan öncesine kadar gezinin.

- Düğümü zincirden çıkarmak için `next` işaretçileri değiştirin.

```cs
for(int i=2; i< position; i++) {
  if(temp.next != null) {
    temp = temp.next;
  }
}
temp.next = temp.next.next;

```

&nbsp;
<hr>
&nbsp;

## Bağlı Listede Eleman Arama

Aşağıdaki adımları kullanarak  bağlı listedeki bir öğeyi bir döngü yardımıyla arayabilirsiniz.
`Item` elemanını bağlı liste üzerinde arayalım.

- `head` işaretcisini `current` düğüm olarak belirtiyoruz.

- `current` işaretcisi `null` olana dek devam ediyoruz çünkü bağlı listedeki son elemanın işaretcisi `null`'dır.

- Her bir adımda, düğümün verisinin `item` ile eşleşip eşleşmediğini kontrol ediyoruz. Eğer eşleşirse `true`, eşleşmezse `false` döndürüyoruz.

```cs
bool searchNode(Node head_ref, int key) {
  Node current = head_ref;

  while (current != null) {
    if (current.data == key) 
      return true;
    current = current.next;
  }
  return false;
}
```

&nbsp;
<hr>
&nbsp;

## Bağlı Listede Eleman Sıralama

Aşağıda, bağlı bir listenin öğelerini küçükten büyüğe doğru sıralamak için basit bir sıralama algoritması olan [balon sıralaması][bubble-sort] kullanacağız. Sırasıyla:

1. `head` işaretcisini `current` düğüm olarak belirtin ve `ìndex` adında başka bir düğümü sonra kullanmak üzere oluşturun.

2. `head` eğer `null` ise işlemi sonlandırılır.

3. Yukarıdaki koşul gerçekleşmediyse son düğüme kadar döngüyü çalıştırın.

4. Her bir adımda 5. ve 6. adımları takip edin.

5. `current` düğümünün sıradaki adresini `index`e kaydedin

6. Mevcut düğüm verisinin bir sonraki düğümden daha büyük olup olmadığını kontrol edin. Eğer büyükse, `current` ile `index` yer değiştirin.

Çalışma mantığını daha iyi anlamak için [balon sıralama][bubble-sort] makalesine bakın.

```cs
public void sortLinkedList(Node head_ref) {
  Node current = head_ref, index = null;
  int temp;

  if (head_ref == null) {
    return;
  } else {
    while (current != null) {
      // index mevcut düğümün next'ini gösteriyor
      index = current.next;
      while (index != null) {
        if (current.data > index.data) { // bubble sort
          temp = current.data;
          current.data = index.data;
          indexdata = temp;
        }
    	  index = index.next;
      }
      current = current.next;
    }
  }
}
```
&nbsp;
<hr>
&nbsp;

## C# Dilinde Bağlı Liste Implementasyonu

```cs
class Program
    {
        static void Main(string[] args)
        {
            LinkedList llist = new LinkedList();
            llist.insertToTail(1);
            llist.insertToHead(2);
            llist.insertToHead(3);
            llist.insertToTail(4);
            llist.insertAfter(llist.head.next, 5);
            Console.WriteLine("\nEleman Silindikten sonra Liste:");
            llist.removeNode(3);
            llist.printList();
            llist.sort(llist.head);
            Console.WriteLine("\nSıralanmış Liste: ");
            llist.printList();
        }
    }
public class LinkedList
    {
        public Node head;

        //Başa ekleme 
        public void insertToHead(int new_data)
        {
            Node new_node = new Node(new_data);
            new_node.next = head;
            head = new_node;
        }

        //Ortaya ekleme
        public void insertAfter(Node prev_node, int new_data)
        {
            if (prev_node != null) { // Öncesinde düğüm varsa
                Node new_node = new Node(new_data);
                new_node.next = prev_node.next;
                prev_node.next = new_node;
            }
        }

        //Sona Ekleme
        public void insertToTail(int new_data)
        {
            Node new_node = new Node(new_data);

            if (head == null) { //Eğer liste boş ise head olarak belirt
                head = new Node(new_data);
                return;
            }
            new_node.next = null;

            Node last = head;
            while (last.next != null)//Sona kadar gezinir
                last = last.next;

            last.next = new_node;
            return;
        }

        // Düğüm Silme
        public void removeNode(int position)
        {
            if (head == null)//Liste boş ise sonlandır
                return;

            Node temp = head;
            if (position == 0){ // 0.indeks ise baştan siler
                head = temp.next;
                return;
            }
            // Silinecek düğüm aranır
            for (int i = 0; temp != null && i < position - 1; i++)
                temp = temp.next;

            // Eğer düğüm bulunamamışsa
            if (temp == null || temp.next == null)
                return;

            // düğümü sil
            Node next = temp.next.next;
            temp.next = next;
        }

        //Düğüm arama
        public bool search(Node head, int key)
        {
            Node current = head;
            while (current != null)//Sona kadar gider ve key degerini kontrol eder
            {
                if (current.data == key)
                    return true;
                current = current.next;
            }
            return false;
        }

        //Bubble sort ile sıralama
        public void sort(Node head)
        {
            Node current = head;
            Node index = null;
            int temp;

            if (head == null) { //Liste boş ise sonlandır
                return;
            }
            else {
                while (current != null) {
                    // index mevcut düğümün sıradakini temsil eder
                    index = current.next;

                    while (index != null) {
                        if (current.data > index.data) {//bubble sort
                            temp = current.data;
                            current.data = index.data;
                            index.data = temp;
                        }
                        index = index.next;
                    }
                    current = current.next;
                }
            }
        }

        // Listeyi Yazdırma
        public void printList()
        {
            Node tnode = head;
            while (tnode != null) {
                Console.WriteLine(tnode.data + " ");
                tnode = tnode.next;
            }
        }
    }

    //Düğüm Sınıfı
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

<!--
LINKS
-->
[linked-list]:../linked-list
[traversal]:#bağlı-listede-gezinme
[insertion]:#bağlı-listeye-eleman-ekleme
[deletion]:#bağlı-listeden-eleman-silme
[search]:#bağlı-listede-eleman-arama
[sort]:#bağlı-listede-eleman-sıralama
[bubble-sort]:../../sorting-search-algorithm/bubble-sort