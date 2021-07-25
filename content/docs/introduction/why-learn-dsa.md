---
title: "Neden Öğrenmeliyiz"
description: ""
lead: ""
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "introduction"
weight: 3
toc: true
---

Bu rehberde, her programcının neden veri yapılarını ve algoritmaları öğrenmesi gerektiğini örnekler yardımıyla öğreneceğiz.

Bu makale, algoritma öğrenmeye yeni başlayan ve kariyerini/programlama becerilerini geliştirmenin ne kadar etkili olacağını merak edenler, ayrıca Google, Facebook ve Amazon gibi büyük şirketlerin neden algoritmaları optimize etmede son derece iyi programcıları işe aldığını merak edenler içindir.

## Algoritma Nedir?

Gayri resmi olarak, bir algoritma, bir sorunu çözmek için atılan adımlardan başka bir şey değildir. Aslında hepsi bir çözümdür.

Örneğin, faktöriyel hesaplayan problemin çözümü şöyle bir şeye benzeyebilir:

**Problem: n sayısının faktöriyelini hesaplama**

```bash
faktoriyel=1 degeri ile başlat
1den n sayısına kadar her v degeri icin:
    faktoriyel ile v çarp
faktoriyel n sayısının faktöriyel hesabını içerir
```
{{< alert icon="➡️" text="Bu algoritma türkçe yazılmıştır. Eğer bir programlama dili ile yazılsaydı, bunu kod olarak belirtirdik. C++'da faktöriyel hesabını yapan kod aşağıda." />}}

```cpp
int faktoriyel(int n) {
    int fakt = 1;
    for (int v = 1; v <= n; v++) {
        fakt = fakt * v;
    }
    return fakt;
}
```
<hr>
&nbsp;

Programlama tamamen algoritma ve veri yapılarından oluşur. Veri yapıları ile veri depolayabiliyorken, bu veriler kullanılarak problem çözmek için algoritma kullanılır.

Veri yapıları ve algoritmalar, standart problemlerin çözümlerini ayrıntılı olarak inceler ve her birini kullanmanın ne kadar verimli olduğu konusunda size bir fikir verir. Ayrıca Ayrıca size bir algoritmanın verimliliğini değerlendirme bilimini de öğretir. Bu size çeşitli seçeneklerden en iyisini seçme fırsatı sunar.

&nbsp;
<hr>
&nbsp;

## Kodunuzu Ölçeklenebilir Hale Getirmek için Veri Yapılarının ve Algoritmaların Kullanımı

### Zaman Kıymetlidir
Varsayalım ki Bob ve Alice ilk 10<sup>11</sup> doğal sayının toplamını bulma problemini çözmeye çalışıyor. Bob algoritmayı yazarken, Alice Donald Trump'ı eleştirmek kadar basit olduğunu kanıtlayarak uyguluyor.

**Algoritma (Bob)**

```bash
sum=0 yaparak değişkenine deger ata
1den 1011e(dahil) kadar her dogal n sayısı için:
    toplama n sayısını ekle
Ekrana toplam değişkenini yazdır
```
**Kod (Alice)**

```cpp
int findSum() {
    int sum = 0;
    for (int v = 1; v <= 100000000000; v++) {
        sum += v;
    }
    return sum;
}
```
{{< alert icon="➡️" text="Alice ve Bob, neredeyse hiç vakit kaybetmeden kendilerine ait bir şey inşa edebilecekleri için kendilerini çok mutlu hissediyorlar. Gelin, onların çalışma alanlarına gizlice girelim ve konuşmalarını dinleyelim." />}}

<pre>
<b>Alice:</b> Hadi kodu çalıştıralım ve toplamı bulalım.
<b>Bob:</b> Bir kaç dakika önce çalıştırdım ancak hala bir çıktı vermedi. Bunun problemi ne?
</pre>

Oops, bir şeyler ters gitti! Bilgisayar en belirleyici makinelerdir. Geri dönüp tekrar çalıştırmaya çalışmak yardımcı olmaz. Gelin, bu basit kodda neyin yanlış gittiğini analiz edelim.

Bir bilgisayar programı için en değerli kaynaklardan ikisi zaman ve bellektir.

Bilgisayarın kodu çalıştırması için geçen süre:

```bash
Çalıştırma Zamanı = Komut sayısı * her komutu çalıştırma zamanı
```

Komutların sayısı, kullandığınız koda bağlıdır ve her bir kodun yürütülmesi için geçen süre, bilgisayarınıza ve derleyicinize bağlıdır.

Bu durumda, yürütülen komutların toplam sayısı(biz buna **x** diyelim):
<pre>
x = 1 + (10<sup>11</sup> + 1) + (10<sup>11</sup>) + 1
|
x = 2 * 10<sup>11</sup> + 3
</pre>

Bir bilgisayarın saniyede **y** = 10<sup>8</sup> komut işleyebildiğini varsayalım.(Bu durum bilgisayarınızın özelliklerine göre değişir.). Yukarıdaki kodu çalıştıracak süre:

```bash
Kodu çalıştıracak süre: x/y (16 dakikadan daha fazla)
```
Algoritmayı, Alice ve Bob'un bu kodu her çalıştırdıklarında 16 dakika beklemek zorunda kalmayacak şekilde optimize etmek mümkün müdür?

Doğru yöntemi zaten tahmin ettiğinize eminim. N'e kadar olan sayıların toplamını şu formülle hesaplayabiliriz:

```bash
Toplam = N * (N + 1) / 2
```
Bunu koda dönüştürdüğümüzde buna benzer bir görüntü oluşacaktır:

```c
int topla(int N) {
    return N * (N + 1) / 2;
}

```
Bu kod yalnızca bir komutta yürütülür ve değeri ne olursa olsun görevi yerine getirir. Gerekirse evrendeki toplam atom sayısından büyük olsun. Sonucu kısa sürede bulacaktır.

Bu durumda problemi çözmek için geçen süre 1/y'dir (10 nanosaniyedir). Bu arada, bir hidrojen bombasının füzyon reaksiyonu 40-50 ns sürer, bu da kodunuzu çalıştırdığınız anda birisi bilgisayarınıza hidrojen bombası atsa bile programınızın başarıyla tamamlanacağı anlamına gelir.

{{< alert icon="➡️" >}}
**Note:** Bilgisayarlar çarpma ve bölme için bir kaç komut işler. Basitlik olması açısından sadece 1 tanesini söyledim.
{{< /alert >}}

&nbsp;
<hr>
&nbsp;

## Ölçeklenebilirlik ve Daha Fazlası

Ölçeklenebilirlik, ölçek artı yetenektir. Bu, daha büyük boyuttaki problemi ele almak için bir algoritmanın/sistemin kalitesi anlamına gelir.

50 kişilik bir sınıf kurma problemini düşünün. En basit çözümlerden bir oda kiralayın, bir kaç tebeşir ile karatahta edinin ve problem çözüldü.

**Ama ya sorunun boyutu artarsa? Ya öğrenci sayısı 200'e çıkarsa?**

Çözümümüz hala geçerli ancak artık daha fazla kaynak gerekiyor. Bu durumda muhtemelen daha büyük bir oda(Tahmini Tiyatro Alanı), bir projektör ve dijital bir kaleme ihtiyacınız olacak.

**Ya öğrenci sayısı 1000'e çıkarsa?**

Sorunun boyutu arttığında çözüm başarısız olur veya çok fazla kaynak kullanılır. Bu, çözümünüzün ölçeklenebilir olmadığı anlamına gelir.

**O zaman ölçeklenebilirlik çözüm nedir?**

[Khanacademy](https://khanacademy.org) gibi bir site düşünün. Milyonlarca öğrenci aynı anda videoları görebilir, cevapları okuyabilir ve bunun için daha fazla kaynağa gerek yoktur. Böylece çözümümüz, kaynak sıkıntısı altında daha büyük boyuttaki sorunları da çözebilir.

ilk N doğal sayının toplamını bulmak için ilk çözümümüzü hatırlıyorsanız, bu ölçeklenebilir değildi. Çünkü problemin boyutuna göre doğrusal büyüme gerektiriyordu.Bu tür **algoritmalar doğrusal olarak ölçeklenebilir algoritmalar** olarak adlandırılır.

İkinci çözümümüz çok ölçeklenebilirdi ve daha büyük boyutlu bir sorunu çözmek için daha fazla zaman kullanılmasını gerektirmiyordu. Bu tür algoritmalar **sabit zamanlı algoritmalar** olarak adlandırılır.

&nbsp;
<hr>
&nbsp;

## Hafıza Pahalıdır

Hafıza her zaman bolluk içerisinde bulunmaz. Çok fazla veri depolamanızı veya üretmenizi gerektiren kod/sistem ile uğraşırken, algoritmanızın mümkün olan her yerde bellek kullanımını koruması çok önemlidir. 

Örneğin: **Kişiler**le ilgili verileri kaydederken, yaşlarını değil, yalnızca doğum tarihlerini kaydederek hafızadan tasarruf edebilirsiniz. Doğum tarihini ve mevcut tarihi kullanarak her zaman hesaplayabilirsiniz.

&nbsp;
<hr>
&nbsp;

## Algoritma Verimliliği Örnekleri

Aşağıda, öğrenme algoritmalarının ve veri yapılarının yapmanıza olanak sağladığı bazı örnekler verilmiştir:

## Örnek 1: Yaş Grup Problemi

Belirli bir yaş grubundaki insanları bulmak gibi sorunlar, ikili arama algoritmasının biraz değiştirilmiş versiyonuyla kolayca çözülebilir.(*Verilerin sıralı olduğunu varsayıyoruz*)

Bu saf algoritma tüm kişileri teker teker inceler ve verilen yaş grubuna girip girmediğini kontrol eder, doğrusal olarak ölçeklenebilir. Oysa ikili arama, logaritmik olarak ölçeklenebilir bir algoritma olduğunu iddia ediyor. Bu, sorunun boyutunun karesi alınırsa, onu çözmek için geçen sürenin yalnızca **iki katına** çıkacağı anlamına gelir.

Diyelim ki 1000 kişilik bir grup için belirli bir yaştaki tüm insanları bulmak 1 saniye sürüyor. Daha sonra bu 1 milyon kişilik grup için,

- İkili arama algoritması ile sadece 2 saniyede problem çözülebiliyorken
- Bu saf algoritma ile 1 milyon saniyede çözülebilir.(12 gün civarı)

Bir sayının karekökünü bulmak için aynı ikili arama algoritması kullanılır.

&nbsp;
<hr>
&nbsp;

## Örnek 2: Rubik Küpü Problemi

Bir Rubik küpünün çözümünü bulmak için bir program yazdığınızı hayal edin.

Bu sevimli bulmacanın can sıkıcı bir şekilde 43,252,003,274,489,856,000 pozisyonu var ve bunlar sadece pozisyon! Yanlış pozisyonlara ulaşmak için kaç yol izleyebileceğinizi hayal edin.

Neyse ki, bu sorunu çözmenin yolu [graf veri yapısı](./data-structures-and-types.md) ile gösterilebilir. [Dijkstra algoritması](https://www.programiz.com/dsa/dijkstra-algorithm) olarak bilinen ve bu problemi doğrusal zamanda çözmenizi sağlayan bir grafik algoritması vardır. Evet, doğru duydunuz. Bu durum, minimum sayıda durumda çözülmüş konuma ulaşmanıza izin verdiği anlamına gelir.

&nbsp;
<hr>
&nbsp;

## Örnek 3: DNA Problemi

DNA, genetik bilgiyi taşıyan bir moleküldür. Roma karakterleri A(Adenin), C(Sitozin), T(Timin)  ve G(Guanin) ile temsil edilen daha küçük birimlerden oluşurlar.

Biyoinformatik alanında çalıştığınızı düşünün. Bir DNA zincirinde belirli bir kalıbın oluşumunu bulma görevi size verildi.

Bilgisayar bilimi akademisinde ünlü bir problemdir. En basit çözümü ise aşağıdaki ile orantılı zaman alır

```bash
(DNA zincirindeki karakter sayısı) * (Desendeki karakter sayısı)
```

Tipik bir DNA zinciri milyonlarca birim içerir. Eh! Endişelenme. KMP Algoritması, aşağıdaki ile orantılı zaman alır


```bash
(DNA zincirindeki karakter sayısı) + (Desendeki karakter sayısı)
```
Artı(+) ile değiştirilen Çarpı(*) operatörü, yanında bir çok değişikliği de getirir.

Desenin 100 karakter olduğunu düşünürsek, algoritmanız artık 100 kat daha hızlı. Deseniniz 1000 karakterden oluşsaydı, KMP algoritması neredeyse 1000 kat daha hızlı olurdu. Yani, eğer desenin oluşumunu 1 saniyede bulabildiyseniz, şimdi sadece 1 ms sürecektir. 1 zinciri eşleştirmek yerine, aynı uzunlukta 1000 zinciri aynı anda eşleştirebilirsiniz.

Ve bunun gibi sonsuz örnekler...

&nbsp;
<hr>
&nbsp;

## Son Söz

Genel olarak yazılım geliştirme, günlük olarak yeni teknolojileri öğrenmeyi içerir. Bu teknolojilerin çoğunu, projelerinizden birinde kullanırken öğrenirsiniz. Ancak, algoritmalarda durum böyle değildir.

Algoritmaları iyi bilmiyorsanız, şu anda yazdığınız kodu optimize edip edemeyeceğinizi belirleyemezsiniz. Bunları önceden bilmeniz ve mümkün olan, kritik olan her yerde uygulamanız beklenir.

Özellikle algoritmaların ölçeklenebilirliği hakkında konuştuk. Bir yazılım sistemi, bu tür bir çok algoritmadan oluşur. Bunlardan herhangi birini optimize etmek daha iyi bir sistem geliştirmek demektir.

Ancak, bir sistemi ölçeklenebilir hale getirmenin tek yolunun bu olmadığını unutmamak önemlidir. Örneğin, dağıtılmış bilgi işlem olarak bilinen bir teknik, bir programın bağımsız bölümlerinin birden çok makinede birlikte çalışmasına izin vererek onu daha da ölçeklenebilir hale getirir. 

{{< alert icon="➡️" text="Bknz. Distributed Systems" />}}
