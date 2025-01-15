# Performans İyileştirmelerinde Dikkat Edilecek Noktalar

Yazar: Murat Öksüzer

Kurumsal web uygulamaları çok katmanlı uygulamalar ve geliştirilmelerinde değişik teknolojiler kullanılabiliyor. Bu 
sistemlerin performans iyileştirmelerinde hem her katmanda kullanılan teknoloji ve framework’lere hem de uygulamanın 
deploy edildiği ve çalıştırıldığı runtime ortamına özel optimizasyon noktalarına odaklanmak gerekir. Bu durumda bir 
sistemin “ince ayara” tabi tutulmasında dikkat edilecek bölümler ana hatları ile;

- İşletim sistemi ve veritabanı
- Java runtime
- Uygulama sunucusu
- Uygulamada kullanılan kütüphane, framework ve teknolojiler
- Uygulama kodunun kendisi

Bir sistemden arzu edilen verimi alabilmek için bütün bu kısımları “kutudan çıktıkları” ayarların dışında ihtiyaçlarımıza 
göre ayarlamamız gerekmektedir. Belirli bazı yerlerde de bu ayarlar birbirleri ile etkileşim de gösterebilmektedir. 
Örneğin, uygulama sunucusu düzeyinde sistemin ele alabileceği max concurrent HTTP isteği sayısını artırmamız aynı zamanda 
işletim sisteminin türüne göre max open file sayısında da değişikliğe gitmemizi gerektirebilir. Ya da veritabanı connection 
pool kabiliyetinden yararlanıyorsak max connection pool size’ını tek başına değiştirmemiz yeterli olmayacaktır. Arzu edilen 
miktarda DB connection’ı elde edebilmek için ayrıca DB tarafında, DB’nin türüne göre process, transaction veya thread 
sayılarını yöneten attribute’ları da gözden geçirmeliyiz.

Yakın bir zamanda bir müşterimizde kurumsal uygulamalarının performans optimizasyonu ile ilgili bir çalışma yürütmeye 
başladık. Başlangıç noktamız “veri erişim katmanı” ve bu katmanda kullanılan ORM teknolojisi Hibernate oldu. Hibernate 
odaklı “tuning” çalışmalarımız olumlu sonuç verdi ve sistemin isteklere cevap verebilirliğinde önemli ölçüde artış 
gerçekleşti.

Ancak kurumsal bir uygulamada optimizasyon sadece persistence ile sınırlı kalmıyor. Kısa bir süre sonra JMeter ile 
yürüttüğümüz load testlerimiz sırasında gelinen nokta uygulama sunucusunun da talep edilen yükü kaldırabilmesi için 
değişik kısımlarında “default” ayarlarının dışına çıkarak ince ayara tabi tutulması şeklinde oldu. Muhtemelen JRE ve 
işletim sistemi düzeyinde de ayarlamalara önümüzdeki günlerde ihtiyaç duyacağız.

Kullanılan teknolojiler, uygulama sunucuları ve runtime platformu farklılıklar gösterse de her performans optimizasyon 
çalışması için odaklanılması gereken bir takım ortak “ince ayar” noktalarından bahsedebiliriz. Bunların bir kısmı şu 
şekilde sıralanabilir;

- Connection pooling ayarları
- Thread pooling ayarları
- Max HTTP request count değeri
- Web isteklerinin ele alınmasındaki ayarlar, isteğin cache’lenmesi, sıkıştırılması vb.
- İşletim sistemindeki process, file thread yönetimi ile ilgili kısıtlar
- Loglama ile ilgili ayarlar
- Business veya mesajlaşma servislerindeki pooling mekanizmaları ve bunların ayarları
- Transaction altyapısındaki ayarlar, transaction timeout vs.

Yukarıda bahsettiğim kısımlar kullanılan teknolojilere göre daha spesifik noktalara dönüşebilir, eklemelerde yapılabilir. 
Ancak “performans hastalığı”nın tedavi sürecinin ilk ayağı olan teşhiste bize önemli ölçüde yol gösterici olacaklardır.
