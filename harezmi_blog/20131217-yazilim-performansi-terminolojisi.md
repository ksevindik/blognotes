# Yazılım Performansı Terminolojisi

Yazar: Murat Öksüzer

![](images/sw_perf.jpeg)

Performans denilince aklımıza gelen sadece “hız” mıdır? A programı B programından hızlıysa her zaman A mı tercih 
edilmelidir? Bu yazımızda bu sorulara cevaplandırmada yardımcı olması amacıyla yazılım performansını ölçerken 
kullandığımız anahtar kelimelerden bahsedeceğiz.

**Response Time**: (tepki süresi) Sistemin dışarıdan aldığı bir isteği işleyip cevap verene kadar geçen süreye denir. 
Örnek olarak “topla” tuşuna basmanız ile hesap makinesinin girilen değerleri toplayıp ekranda göstermesi arasında geçen 
süre verilebilir.

**Responsiveness**: (duyarlılık) Sistemin bir kullanıcı isteğine ne kadar çabuk tepki verdiği ile alakalıdır. Kullanıcı 
memnuniyeti açısından önemlidir çünkü kullanıcı isteğinin alındığını ve işleme başlandığını bilmek ister. Tuşa bastıktan 
sonra ekranda bir değişiklik görmeyen kullanıcı hayal kırıklığına uğrayabilir. Kullanıcı “Rapor üret” tuşuna bastığında 
ekranda gösterilecek bir ilerleme çubuğu response time‘ı yani rapor üretme süresini değiştirmese de responsiveness‘ı 
arttıracaktır.

**Latency**: (gecikme süresi) Sistemin gelen çağrıya hiçbir iş yapmadan anında cevap verse bile cevabın bize ulaşmasına 
kadar geçen minimum süredir. Önümüzdeki bilgisayarda bu süre sıfıra yakındır fakat uzak sistemlerde isteğin karşı tarafa 
gidip hiçbir işle oyalanmadan tekrar geri gelmesi bile saniyeler alabilir. Bu nedenle uzak sistemlere yapılan çağrıların 
en aza indirilmesi önerilir.

**Throughput**: (iş/zaman) Birim zamanda yapılan iş miktarı. Kurumsal uygulamalarda saniyede yapılan transaction sayısıyla 
ölçülmektedir (*transactions per second*, tps).

Yazılım performansından bahsederken ya response time’dan ya da throughput’tan bahsedilmektedir. Kullanıcı bakış açısıyla 
bakıldığında ise responsiveness daha önemli olabilmektedir. Bu nedenle daha kötü response time veya throughput pahasına 
da olsa responsiveness’ı arttırmak, yazılımınızın performansını arttırabilir.

**Load**: (yük) Bir sistemin ne kadar yük altında olduğunu anlatmak için kullanılır. Sisteme o anda bağlı olan kullanıcı 
sayısı ile ölçülebilir. Load genelde diğer ölçülerle, mesela response time ile beraber kullanılmaktadır. Örneğin 
“Sistem 100 kullanıcılı iken response time 0.5 saniye, 200 kullanıcılı iken 2 saniyedir.” denilebilir.

**Efficiency**: (verimlilik) Kısaca birim kaynakla üretilen performans (*performans / kaynak*) şeklinde tarif edebiliriz. 
2 işlemci ile 30 tps performans elde edilen bir sistem, 4 işlemci ile 40 tps performans elde edilen sistemden daha 
verimlidir denilebilir.

**Capacity**: (kapasite) Sistemin istenilen şekilde çalışmaya devam edebildiği maksimum load veya throughput’a denir.

**Scalability**: (ölçeklenebilirlik) Sisteme eklenen ek kaynakların performansı nasıl etkilediğinin ölçüsüdür. Eklediğiniz 
donanımla orantılı olarak performans artışı sağlayan sistemler ölçeklenebilir (*scalable*) sistemlerdir. Tek bir sunucunun 
gücünü arttırmaya *vertical scalability*, sisteme birden fazla sunucu eklemeye ise *horizontal scalability* denir.

Kurumsal uygulamalar tasarlarken kapasiteden hatta verimlilikten daha çok ölçeklenebilirliğe dikkat edilmesi tavsiye 
edilmektedir. Performansa ihtiyaç duyduğunuzda scalability ile istediğinizi daha ucuza elde edebilirsiniz. Scalable bir 
sistemde çoğu kez yeni donanım almak, yeni yazılımcı almak veya yazılımı upgrade etmekten daha ucuza gelmektedir.

Bu yazımızda yazılım performansı denince akla gelen terimlere aşina olmaya çalıştık. 

Bir sonraki paylaşımda buluşmak üzere...
