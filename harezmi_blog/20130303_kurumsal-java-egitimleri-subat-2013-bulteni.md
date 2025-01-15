# Kurumsal Java Eğitimleri Şubat 2013 Bülteni

### Performans İyileştirmelerinde Dikkat Edilecek Noktalar

Performans, kurumsal Java uygulamalarının en baş ağrıtıcı konularındandır. Donald Knuth’un “We should forget about small 
efficiencies, say about 97% of the time: premature optimization is the root of all evil” vecizesi bir yana, uygulamalarımız
işletime alındığında karşı karşıya kalabileceğimiz performans darboğazlarını nasıl aşacağımızla ilgili kafamızdaki yöntemin
net adımlardan oluşması, optimizasyon için nereye bakacağımızı bilmemiz performans iyileştirme çalışmalarının verimli 
olması için şarttır. Bu [yazımızda](http://blog.harezmi.com.tr/performans-iyilestirmelerinde-dikkat-edilecek-noktalar/) bir sistemin “ince ayara” tabi tutulmasında dikkat edilecek bölümleri ana hatları ile 
inceliyoruz.

### Spring JavaConfig ve Döngüsel Bağımlılıklar

Aslında en doğrusu döngüsel bağımlılıklardan tamamen kaçınmak. Ancak zaman zaman karşımıza doğrudan veya dolaylı olarak 
java nesneleri arasında döngüsel bağımlılık ihtiyacı çıkabiliyor. Bu [yazımızda](http://blog.harezmi.com.tr/spring-javaconfig-ve-dongusel-bagimliliklar/) Spring Application Framework içerisinde 
döngüsel bağımlılıkların nasıl ele alındığını incelemeye başlıyoruz. Devam yazılarımızda ise Spring 3 ile gelen Java 
tabanlı konfigürasyon yönetiminde döngüsel bağımlılıkların yönetimini ve Java tabanlı konfigürasyonun döngüsel 
bağımlılıklarla ilgili kısıtlarını ve bunların nasıl aşılabileceğini incelemeye devam edeceğiz.

### Hibernate: Field Level mı? Getter Level Mı?

Herhangi bir framework, bir işi yapabilmek için birden fazla yol sunduğunda hangi yolun daha iyi olduğu ile ilgili 
geliştiriciler arasında hiçbir zaman kesin bir görüş birliğine varılması mümkün değildir. Aslında bu beklenmemelidir de
çünkü muhtemelen bu alternatifler diğer yolların yetersiz kaldığı bir takım durumlar düşünülerek eklenmiştir. JPA veya 
Hibernate ile çalışırken temel tartışma konularından birisi de entity sınıfların persistent alanlarına hangi erişim 
yönetiminin kullanılması uygulamamız için daha doğru olur sorusudur. Bu [yazımızda](http://blog.harezmi.com.tr/hibernate-field-level-mi-getter-level-mi/) iki yönetimi de inceliyoruz, artı ve
eksilerini değerlendiriyoruz.

Bir sonraki bültenimizde görüşmek üzere…


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
