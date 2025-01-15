# Kurumsal Java Eğitimleri Kasım 2013 Bülteni

Herkese Merhabalar,

Bu ayki bültenimize ilk olarak Hibernate ile başlamak istiyorum. Hibernate kullanılan projelerin yaşadığı en büyük sorun
hepimizin bildiği gibi `LazyInitializationException`’dır. `Session` kapandıktan sonra, initialize edilmemiş bir proxy 
nesnenin kendisine veya bir `entity`’nin initialize edilmemiş bir ilişkisine erişilmeye çalışıldığı vakit ortaya çıkan
bu hatadan kurtulmak için uygulama geliştiriciler değişik yollar izlemektedirler. Maalesef bu yollardan bazıları da 
uygulamanın kod kalitesini düşürücü niteliktedir. Hibernate 4 ile gelen bir yeni özellik sayesinde bu hataya güle güle 
demek mümkün. Detayları [buradaki yazımızdan](http://blog.harezmi.com.tr/hibernates-new-feature-for-overcoming-frustrating-lazyinitializationexceptions/) öğrenebilirsiniz.

İkinci konumuz da yine Hibernate ile ilgili. Geçen ay ilk bölümünü yayımladığımız **Hibernate’de Sınıf İlişkileri** 
başlıklı yazı dizisinin yeni bölümüne [buradan](http://blog.harezmi.com.tr/hibernatede-sinif-iliskileri-2/) ulaşabilirsiniz. Bu ayki bölümde `M:1` ilişkileri inceliyoruz.

Harezmi Bilişim Çözümleri olarak üzerinde çalıştığımız konulardan birisi de model güdümlü yazılım geliştirmedir. Model
güdümlü yazılım geliştirmenin temel problem noktalarından birisi de model-kod, kod-model senkronizasyonunun nasıl 
sağlanacağıdır. Bununla ilgili olarak Eclipse platformunun sunduğu `JDT` isimli bir teknolojiyi sizinle paylaşmak 
istiyoruz. `JDT` sayesinde kodunuzun içerisinde yaptığınız herhangi bir değişikliğin model tarafından algılanabilmesi 
ve takip edilebilmesi mümkün hale geliyor. `JDT` hakkındaki yazımıza [buradan](http://blog.harezmi.com.tr/eclipse-java-development-tools-jdt/) ulaşabilirsiniz.

Bu kadar teknik konudan sonra biraz da proje/süreç yönetimi ve gereksinim analizi gibi konularla ilgili konuşalım. 
Gereksinim analizi nedir? Nerede ve nasıl başlar? Kapsamı ne olmalıdır? Bize ne gibi bir çıktı verir? Yazılım sürecimizin 
diğer safhaları ile ilişkisi nasıl olmalıdır? Yeni başlayan bir yazı dizimiz ile bu konulardaki deneyimlerimizi sizinle 
paylaşacağız. Bu ay ilk olarak proje, process gibi çok sık kullandığımız temel kavramlar aslında tam olarak ne anlama 
geliyor, bu kavramların zihnimizde canlandırdığı veya canlandırması gereken temel imgeler nelerdir, bunları inceliyoruz.
Yazımızın devamına [buradan](http://blog.harezmi.com.tr/yazilim-projelerinde-gereksinim-analizi/) erişebilirsiniz.


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
