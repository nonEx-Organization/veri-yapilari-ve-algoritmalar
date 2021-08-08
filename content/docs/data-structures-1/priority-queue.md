---
title: "Öncelik Kuyruğu"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "data-structures-1"
weight: 15
toc: true
---

Bu rehberde, öncelik kuyruk yapısının ne olduğunu öğreneceksiniz. Ayrıca c# dilinde kuyruk implementasyonunu göreceksiniz.

Öncelik kuyruğu, her elemanın bir öncelik değeriyle ilişkilendirildiği özel bir kuyruk türüdür. Elemanlar, öncelik değerlerine göre sunulur. Bu durum sayesinde yüksek öncelikli elemanların daha önce erişilebilir.

Fakat, aynı öncelikli elemanların oluşturulması durumunda elemanlara kuyruktaki sırasına göre erişilir.

<h4><b>Öncelik Değeri Atamak</b></h4>

Genelde, elemanın değeri üzerinden öncelik atanır.

Örneğin,

En büyük değere sahip eleman, kuyruğun en yüksek öncelikli elemanı olarak belirlenir. Ancak, diğer durumlarda en düşük değerli elamanı en yüksek öncelikli eleman olarak kabul edebiliriz.

Ayrıca ihtiyaçlarımıza göre öncelikleri de belirleyebiliriz.

<p align=center>
  <img src="../assets/priority-introduction.png" width= 320px>
</p>

{{< alert icon="➡️" text="En Yüksek Öncelikli Elemanı Çıkarmak" />}}

&nbsp;
<hr>
&nbsp;

## Öncelik Kuyruğu ile Normal Kuyruk Arasındaki Farklar

Normal bir kuyrukta **ilk giren ilk çıkar** kuralı uygulanırken, öncelik kuyruğunda elemanlar önceliklerine göre ayrılır. İlk çıkartılacak eleman en yüksek öncelikli elemandır

&nbsp;
<hr>
&nbsp;

## Öncelik Kuyruk İmplementasyonu

Öncelik kuyruğu bir dizi, bir bağlı liste, heap veri yapısı yada ikili arama ağaç yapısı ile implemente edilebilir. Bu veri yapıları arasından **heap veri yapısı** öncelik kuyruğu implementasyonunda verimlilik sağlar.

Burada, öncelik kuyruğunu implemente etmek için heap veri yapısı kullanacağız. Bir Max-Heap, aşağıdaki işlemleri implemente eder. Eğer bunlar hakkında daha fazla bilgi edinmek istiyorsanız [Heap veri yapısı][heap-data-structure] sayfasını ziyaret edin.

Öncelik kuyruğunun farklı uygulamalarının karşılaştırmalı bir analizi aşağıda verilmiştir.

| İşlemler | Göz atma(Peek) | Eleman Ekleme | Eleman Silme |
|------|------|------|------|
| Bağlı Liste | `O(1)` | `O(n)` | `O(1)` |
| İkili Yığın | `O(1)` | `O(log n)` | `O(log n)` |
| İkili Arama Ağacı | `O(1)` | `O(log n)` | `O(log n)` |

&nbsp;
<hr>
&nbsp;

## Öncelik Kuyruğu İşlemleri

Öncelik kuyruğunun temel işlemleri, elemanların eklenmesi, çıkarılması ve gözetlenmesidir.

{{< alert icon="📖" text="Öncelik kuyruğunu incelemeden önce, bu makaledeki öncelik sırasında ikili yığın kullanıldığından daha iyi anlaşılması için lütfen yığın veri yapısına bakın." />}}

&nbsp;
<hr>
&nbsp;

## 1. Öncelik Kuyruğuna Eleman Ekleme

Bir elemanın öncelik kuyruğuna eklenmesi aşağıdaki adımlarla yapılır.

- Ağacın sonuna yeni eleman eklenir.

<p align=center>
  <img src="../assets/priority-enqueue.png" width= 320px>
</p>

{{< alert icon="➡️" text="Ağacın sonuna yeni eleman eklemek" />}}

- Ağacı yığın haline getirin.

<p align=center>
  <img src="../assets/priority-heapify.png" width= 320px>
</p>

{{< alert icon="➡️" text="Yığınlaştırma sonrası Ağaç" />}}

Öncelik kuyruğuna eleman eklemenin algoritması

```bash
Eger düğüm yoksa
  düğüm oluştur
Eger düğüm varsa
  yeni düğümü en sona ekle(son düğüm soldan sağa doğru)

Diziyi yığın haline getir
```

&nbsp;
<hr>
&nbsp;

## 2. Öncelik Kuyruğundan Eleman Silme

Bir elemanın öncelik kuyruğundan silinmesi aşağıdaki adımlarla yapılır.

- Silinecek elemanı seçin.

<p align=center>
  <img src="../assets/priority-select-deleted.png" width= 320px>
</p>

{{< alert icon="➡️" text="Silinecek eleman seçilir" />}}

- En son eleman ile yer değiştir.

<p align=center>
  <img src="../assets/priority-swap-deleted.png" width= 320px>
</p>

{{< alert icon="➡️" text="Son uçtaki düğüm elemanıyla yer değiştirilir " />}}

- Son elemanı kaldır.

<p align=center>
  <img src="../assets/priority-dequeue.png" width= 320px>
</p>

{{< alert icon="➡️" text="Son eleman düğümü kaldırılır" />}}

- Ağacı yığın haline getir

<p align=center>
  <img src="../assets/priority-heapify-1.png" width= 320px>
</p>

{{< alert icon="➡️" text="Öncelik Kuyruğunun Yığın Hali" />}}

Öncelik kuyruğundan eleman silmenin algoritması

```bash
Eger SilinecekDugum cocuk dügüm ise
  düğümü sil
Degilse
  SilinecekDugum ile SonDugum`u yer degistir
  SilinecekDugum`u sil

Diziyi yığın haline getir
```

&nbsp;
<hr>
&nbsp;

## 3. Öncelik Kuyruğunu Gözetleme(Max-Min için Peek)

Peek işlemi max yığından en büyük değeri yada min yığından en küçük değeri düğüm silmeden geri döndürür.

Max Yığın ve Min Yığın için

`return AnaDugum`

&nbsp;
<hr>
&nbsp;

## 4. Öncelik Kuyruğundan Max-Min Elemanlarını Çıkarma

Çıkart-Max, max yığınından maksimum değeri çıkardıktan sonra döndürüyorken Çıkart-Min ise min yığınınından minimum değeri çıkardıktan sonra bu değeri döndürür.

&nbsp;
<hr>
&nbsp;

## C# Dilinde Öncelik Kuyruk Implementasyonu

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
        if (size == 0) // Eleman yoksa direkt ekle
        {
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

## Öncelik Kuyruk Kullanımları

Öncelik kuyruğunun kullanıldığı bazı uygulamalar şunlardır:

- [Dijkstra Algoritması][dijkstra-algorithm]

- Yığın Implementasyonunda

- Bir işletim sisteminde yük dengeleme ve kesinti işlemede

- Huffman kodlarında veri sıkıştırılmasında


<!--
LINKS
-->
[heap-data-structure]:../../data-structures-2/heap-data-structure
[dijkstra-algorithm]:../../greedy-algorithms/dijkstra-algorithm/


