---
title: "Heap Veri Yapısı"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "data-structures-2"
weight: 14
toc: true
---

Bu rehberde, heap veri yapısının ne olduğunu öğreneceksiniz. Ayrıca c# dilinde kuyruk implementasyonunu göreceksiniz.

Heap veri yapısı, yığın özelliğini karşılayan eksiksiz bir ikili ağaçtır. Verilen düğüm

- her zaman alt düğümlerinden daha büyük ve ana düğümdeki anahtar diğer tüm düğünler arasında en büyüktür. Bu duruma **max-heap** denir.

- her zaman alt düğümlerinden daha küçük ve ana düğümdeki anahtar diğer tüm düğünler arasında en küçüktür. Bu duruma **min-heap** denir.

<p align=center>
  <img src="../assets/max-heap.png" width=500px>
</p>

{{< alert icon="➡️" text="Max Heap" />}}

<p align=center>
  <img src="../assets/min-heap.png" width=500px>
</p>

{{< alert icon="➡️" text="Min Heap" />}}

Bu veri yapısı ayrıca **binary heap** olarak da adlandırılır.

&nbsp;
<hr>
&nbsp;

## Heap İşlemleri

Bir heap üzerinde gerçekleştirilen bazı önemli işlemler, algoritmaları ile birlikte aşağıda açıklanmıştır.

### Heapify

Heapify, ikili ağaçtan bir heap veri yapısı oluşturma işlemidir. Min-Heap veya Max-Heap oluşturmak için kullanılır.

1. Veri girişinden şöyle bir dizi alalım

<p align=center>
  <img src="../assets/heap-init-array.png" width=500px>
</p>

{{< alert icon="➡️" text="Başlangıç dizisi" />}}

2. Diziden tam bir ikili ağaç oluşturun

<p align=center>
  <img src="../assets/heap-complete-binary-tree.png" width=500px>
</p>

{{< alert icon="➡️" text="Eksiksiz İkili Ağaç" />}}

3. Dizini `n/2 - 1` ile verilen yaprak olmayan düğümün ilk dizininden başlayın.

<p align=center>
  <img src="../assets/heap-start-leaf-node.png" width=500px>
</p>

{{< alert icon="➡️" text="Alt düğümdeki ilk noktadan başla" />}}

4. `i` mevcut elemanını en büyük olarak ayarlayın.

5. Sol alt düğümün indeksi `2i+1` ve sağ alt düğümün indeksi `2i+2` veriliyor.

- Eğer sol alt düğüm **mevcut elemandan** büyükse(Yani eleman `i`. indekste ise), `leftChildIndex` değişkenini **en büyük** olarak ayarlayın.

- Eğer sağ alt düğüm **en büyükten** büyükse(Yani eleman `i`. indekste ise), `rightChildIndex` değişkenini **en büyük** olarak ayarlayın.

6. **En  büyük** ile **mevcut elemanın** yerlerini değiştirin.

<p align=center>
  <img src="../assets/heap-swap-necessary.png" width=500px>
</p>

{{< alert icon="➡️" text="Gerekliyse yer değiştirin" />}}

7. Alt ağaçlar da yığın haline gelene (Heapify) kadar 3-7 arasındaki adımları tekrarlayın.

```cs
Heapify(array, size, i)
  EnBuyuk = i
  leftChild = 2i + 1
  rightChild = 2i + 2
  
  if leftChild > array[largest]
    EnBuyuk = leftChildIndex
  if rightChild > array[largest]
    EnBuyuk = rightChildIndex

  array[i] ile array[largest] elemanlarını yer değiştir
```

Max Heap oluşturmak için:

```cs
  MaxHeap(array, size)
    ilk indeksten alt düğümler bitene kadar döngü
      heapify metodunu çalıştır
```

Min-Heap için, hem `leftChild` hem `rightChild` tüm düğümler için üst düğümden daha küçük olmalıdır.

&nbsp;
<hr>
&nbsp;

## Heap Yapısına Eleman Ekleme

Max-Heap yapısında eleman ekleme algoritması

```cs
If there is no node, 
  create a newNode.
else (a node is already present)
  insert the newNode at the end (last node from left to right)
  
heapify the array
```
1. Yeni elemanı ağacın sonuna yerleştirin.

<p align=center>
  <img src="../assets/heap-insert-end.png" width=500px>
</p>

2. Ağacı yığın haline getirin. (Heapify)

<p align=center>
  <img src="../assets/heap-heapify.png" width=500px>
</p>

Min Heap için yukarıdaki algoritma, ana düğüm yeni düğümden her zaman küçük olacak şekilde değiştirilmiştir.

&nbsp;
<hr>
&nbsp;

## Heap Yapısından Eleman Silme

Max Heap yapısında eleman silme algoritması

```cs
If nodeToBeDeleted is the leafNode
  remove the node
Else swap nodeToBeDeleted with the lastLeafNode
  remove noteToBeDeleted
   
heapify the array
```

1. Silinecek elemanı seçin.

<p align=center>
  <img src="../assets/heap-select-deleted.png" width=500px>
</p>

2. Son eleman ile yer değiştirin.

<p align=center>
  <img src="../assets/heap-swap-last.png" width=500px>
</p>

3. Son elemanı silin.

<p align=center>
  <img src="../assets/heap-remove-last.png" width=500px>
</p>

4. Ağacı yığın haline getirin. (Heapify)

<p align=center>
  <img src="../assets/heap-heapify-1.png" width=500px>
</p>

Min Heap için yukarıdaki algoritma, alt düğümler yeni düğümden küçük olacak şekilde değiştirilmiştir.

&nbsp;
<hr>
&nbsp;

## Göz Atma - Peek (Max-Min)

Peek işlemi düğüm silmeden Max-Heap yapısından en büyük elemanı yada Min-Heap yapısından en küçük elemanı döndürür.

Max Heap ve Min Heap için

```cs
return AnaDugum
```

&nbsp;
<hr>
&nbsp;

## Çıkartma - Extract (Max-Min)

Çıkart-Max, Max Heap yapısından maksimum değeri çıkardıktan sonra döndürüyorken Çıkart-Min ise Min Heap yapısından minimum değeri çıkardıktan sonra bu değeri döndürür.

&nbsp;
<hr>
&nbsp;

## C# Dilinde Heap Implementasyonu


```cs
class Program
  {
      static void Main(string[] args)
      {
          List<int> array = new List<int>();
          int size = array.Count;

          Heap h = new Heap();
          h.insert(array, 3);
          h.insert(array, 4);
          h.insert(array, 9);
          h.insert(array, 5);
          h.insert(array, 2);

          Console.WriteLine("Öncelik Kuyruğu:\t");
          h.printArray(array);

          h.deleteNode(array, 4);
          Console.WriteLine("Eleman silindikten sonra kuyruk:\t");
          h.printArray(array);
      }
  }
public class Heap
{
    // Ağaç Yığınlaştırma
    public void heapify(List<int> hT, int i)
    {
        int size = hT.Count();
        // Kök, sağ ve sol düğümler arasından en büyüğünü bulma
        int largest = i;
        int l = 2 * i + 1;
        int r = 2 * i + 2;
        if (l < size && hT[l] > hT[largest])
            largest = l;
        if (r < size && hT[r] > hT[largest])
            largest = r;
            
        // Eğer kök en büyük değilse yer değiştir ve yığınlaştırmaya devam et
        if (largest != i)
        { //Swap İşlemi
            int temp = hT[largest];
            hT[largest] = hT[i];
            hT[i] = temp;

            heapify(hT, largest);
        }
    }

    // Öncelik Kuyruğuna eleman ekleme
    public void insert(List<int> hT, int newNum)
    {
        int size = hT.Count();
        if (size == 0) { // Eleman yoksa direkt ekle
            hT.Add(newNum);
        }
        else // Eleman varsa ekle ve yığın haline getir
        {
            hT.Add(newNum);
            for (int i = size / 2 - 1; i >= 0; i--)
            {
                heapify(hT, i);
            }
        }
    }

    // Öncelik Kuyruğundan eleman silme
    public void deleteNode(List<int> hT, int num)
    {
        int size = hT.Count();
        int i;
        for (i = 0; i < size; i++)// Aranan elemanı bulma
        {
            if (num == hT[i])
                break;
        }
        //Swap işlemi
        int temp = hT[i];
        hT[i] = hT[size - 1];
        hT[size - 1] = temp;

        hT.Remove(size - 1);
        for (int j = size / 2 - 1; j >= 0; j--)//kaldırma sonrası yığın haline getirme
        {
            heapify(hT, j);
        }
    }

    // Eleman Yazdırma
    public void printArray(List<int> array)
    {
        foreach (int element in array)
        {
            Console.Write(element + " ");
        }
        Console.Write("\n");
    }
}
```

&nbsp;
<hr>
&nbsp;

## Heap Veri Yapısı Kullanımları

- Öncelik Kuyruğu implementasyonunda

- Dijkstra Algoritmasında

- Heap Sıralamasında