# Kurumsal Java Eğitimleri Ocak 2012

## ThreadLocal Değişkenler ve Güvenlik, Spring 3.1, Tasarım Örüntülerinde Ortaklık/Değişkenlik Analizi

Herkese Merhaba,

2012 yılına hızlı bir giriş yaptık, ilk ayın sonuna geldik bile. 2011 yılında yoğun talep gören 
[“Kurumsal Java Teknolojileri”](http://www.java-egitimleri.com/) eğitimlerimize bu yıl da devam ediyoruz. Abraham 
Lincoln’ün şu ünlü sözünü sanırım çoğumuz biliriz; “Bir ağacı kesmem için bana altı saat verirsen, ilk dört saatimi 
baltayı bilemeye harcarım.” Eğer bugünlerde “Enterprise Java” teknolojileri ile uygulama geliştirmeye çalışıyorsanız 
uygulama mimarisinden kullanılacak teknolojilere, analiz ve tasarım sürecinden geliştirme ortamına kadar pek çok konu 
hakkında bilgi ve deneyim sahibi olmanız, değişik teknolojileri bir araya getirmeniz gerekmektedir. Size sunduğumuz 
eğitimlerle hem Spring, Spring Security, Hibernate, AspectJ gibi teknolojileri hızlı biçimde kullanır hale gelmenize, 
hem de nesne yönelimli programlama, tasarım örüntüleri, kurumsal uygulama mimarisi, geliştirme ortamı gibi konularda
bilgi ve deneyim sahibi olmanıza yardımcı oluyoruz.

### Spring 3.1 ve Getirdiği Yenilikler

Geçtiğimiz günlerde Spring Application Framework’ün 3.1 sürümü yayımlandı. Bu sürüm Kurumsal Java teknolojileri ile 
uğraşanlar tarafından uzun süredir merakla beklenmekteydi. Peki bu sürümle Spring kullanıcıları araç setlerine ne tür 
kabiliyetler kazandılar?

Spring 3.1’in getirdiği en önemli yenilik “bean definition profile” oldu. Bu kabiliyet ile Spring ApplicationContext’i 
farklı ortamlar için farklı bean konfigürasyonları çok daha kolay biçimde yapılabiliyor.  
Spring 2.x serisi ile başlayan XML tabanlı bean konfigürasyon yöntemine alternatif olarak, Java kodu yazarak bean 
konfigürasyon yapılmasının sağlanması 3.1 sürümünde en üst noktaya taşınıyor.  
Diğer önemli bir yenilik ise “cache abstraction”. Bulut mimarilerinin yaygınlaştığı ve dağıtık cache kabiliyetlerinin 
önemli hale geldiği bu dönemde farklı cache teknolojilerinin uygulama düzeyinde ortak bir API ile soyutlanması sanırım 
oldukça işimize yarayacak.  
Bütün bunların yanında Servlet 3.0 ve Hibernate 4.x ile uyumlu hale gelmesi, MVC ve REST modüllerindeki iyileştirmeler 
de Spring 3.1 deki diğer dikkat çeken özellikler olarak karşımıza çıkıyor.

### Ortaklık/Değişkenlik Analizi ve Tasarım Örüntüleri

Gang Of Four’un *Design Patterns: Elements of Reusable Object-Oriented Software* [kitabında](http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612) kaliteli bir tasarıma ulaşmak
için dikkat edilmesi gereken temel noktalar şu şekilde özetlenebilir.

- Composition’ı inheritance’a tercih et.
- Değişen ne var ise onu bul ve encapsule et.

Ancak sistem içerisinde neyin değişip, neyin sabit kaldığının tespit edilmesi, bunların nasıl encapsule edileceği ile 
ilgili kitaptan detaylı bilgi edinmek maalesef mümkün olmuyor. Kitaptaki bu yöntem eksikliği çoğu okuyucunun zihnine 
daha önceden yerleştirilmiş nesne=veri + metot klasik yaklaşımı ile birleşince nesne modellerimiz güdük kalıyor. Okullarda 
“encapsulation” hep verinin encapsule edilmesi olarak öğretilir. Veri değişir ve bunlar nesnenin attribute’ları olarak 
ifade edilir. Oysa değişen sadece veri olmayabilir. Davranış veya sınıf da olabilir. Tasarım örüntülerinin pek çoğunda 
da verinin dışında davranış ve sınıf encapsulation’ını görmekteyiz. İşte ortaklık/değişkenlik analizi sayesinde sistemin 
genelinde her türden değişken ve ortak yapıları tespit etmemiz ve tasarımımızı çok daha esnek bir hale getirmemiz mümkün.

İki gün süren Nesne Yönelimli Analiz, Tasarım ve Tasarım Örüntüleri eğitimimizde de uygulamalı olarak GOF örüntülerini 
incelemenin yanı sıra, ortaklık ve değişkenlik analizi üzerinde de ayrıntılı biçimde duruyoruz.

### ThreadLocal Değişkenler Kullananlar Dikkat!

Bu ay size bahsetmek istediğim diğer bir konu ise *ThreadLocal* değişkenlerle ilgili. Kurumsal Java teknolojileri ile
uygulama geliştirenler, özellikle Spring, Hibernate gibi frameworkleri kullananlar uygulama genelinde “contextual bilgi”
paylaşımı için *ThreadLocal* değişkenlerin ne kadar önemli bir araç olduğunu bilirler. Ancak *ThreadLocal* değişkenleri 
dikkatsiz biçimde kullanmamız, uygulama ve veri güvenliği noktasında bizi bazı güvenlik açıkları ile karşı karşıya 
bırakabilir. TÜBİTAK Bilgi Güvenliği Kapısı’nda yayımlanan [makalemde](http://www.bilgiguvenligi.gov.tr/yazilim-guvenligi/threadlocal-kullaniminin-yol-acabilecegi-guvenlik-problemleri-ve-alinabilecek-onlemler.html) *ThreadLocal* kullanımının yol açabileceği güvenlik 
problemlerinden ve bunların nasıl önüne geçilebileceğinden bahsediyorum.

Bir sonraki ay görüşmek üzere, herkese bol Java’lı günler…


Kenan Sevindik

**Kurumsal Java Eğitimleri**
- Spring Application Framework
- Spring Security ile Web Uygulama Güvenliği
- Spring MVC ve Web Servisleri
- Spring AOP ve AspectJ ile Aspect Oriented Programlama
- Hibernate ile Java Persistence
- J2EE Teknolojilerine Giriş
- Java ile Nesne Yönelimli Programlama
- Nesne Yönelimli Analiz, Tasarım ve Tasarım Örüntüleri

On-site kurum içi eğitimlerin yanı sıra, kurum dışında da eğitimler düzenliyoruz. Her türlü konuda bilgi almak, size özel
bir eğitim programı oluşturmak veya kurumsal uygulama geliştirme ile ilgili danışmanlık ve koçluk hizmetlerimiz için bizimle
[irtibata](http://www.harezmi.com.tr/#contact) geçebilirsiniz.

*“Kurumsal Java Eğitimleri”* bir **[Harezmi](http://www.harezmi.com.tr/) Bilişim Çözümleri A.Ş.** hizmetidir.
