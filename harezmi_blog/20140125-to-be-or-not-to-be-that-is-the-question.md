# To Be Or Not To Be, That Is The Question

Yazar: Muammer Yücel

William Shakespeare’in ölümsüz eseri *Hamlet*, yıllar boyunca oyuncularını belki kolayca hatırlayamayacağımız birçok 
filme ya da tiyatro oyununa konu olmuş, adlarını çoktan unuttuğumuz farklı yayınevleri tarafından defalarca basımı 
yapılmış fevkalade bir eserdir. Nedir *Hamlet*’i bu denli farklı ve ölümsüz yapan? Elbette ki oldukça ustalıkla 
kurgulanmış senaryosu.

*Hamlet*’ten bir alıntıyı [“Yazılım Projelerinde Gereksinim Analizi”](http://blog.harezmi.com.tr/yazilim-projelerinde-gereksinim-analizi/) adlı yazı dizimizin devamı niteliğinde olan bu 
yazımızın başlığı olarak kullanmamın bir sebebi var. Yazılım projeleri de tıpkı bir tiyatro oyunu gibi kurgulanır, 
tasarlanır ve sahneye konur. Bu sürecin belki de en önemli safhası, senaryoları gerektiği titizlikte hazırlamaktır. 
Senaryolar, hali hazırda (*as is*) var olan işleyişi analiz etmekte olduğu kadar ortaya konacak (*to be*) olan çözüm 
için de büyük öneme sahiptir. Bu nedenle senaryolar üzerinde mutabık kalmak, geliştirilecek olan ürün için harcanan efor 
ve zamanın boşa gitmemesi için oldukça önemlidir.

Senaryoları belirlerken yapılan en büyük yanlışlardan biri, ortaya konacak olan çözüme yoğunlaşmaktır. Bu durum, analistin 
mevcut işleyişteki ince noktaları gözden kaçırmasına sebep olabilir. Özellikle konuşkan paydaşlarla yapılan analiz 
çalışmalarında zamanın boşa geçtiği ve ilerleme kaydedilemediği algısı analisti sonuç odaklı düşünmeye itebilir. Bunun 
sonucunda da analist, söyleşiyi farklı noktalara yönlendirebilir. Bu anlar oldukça riskli dönüm noktalarıdır. Çünkü o an 
için önemsiz ve kapsam dışı olarak görülen bir detay, ilerleyen safhalarda hayati öneme sahip bir konunun temeli olabilir.

Bu tür durumlarda yapılması gereken, soğukkanlı davranmak ve sınırları net bir biçimde belirlemektir. Bunun için de 
yapılması gereken, eğer konunun farklı noktalara gittiği şeklinde bir algı oluşmuş ise, projenin başlangıcında ortaya 
koyduğumuz amaç ve kazanımları yeniden gündeme getirmek, konuşulanların bu kazanımlara olan etkisini masaya yatırmak 
olmalıdır.

Çoğu zaman geliştirilecek olan uygulamanın sunacağı kabiliyetlere odaklanmak, *business* açısından önemli olan adımları 
gözden kaçırmaya yol açabilir. Gözden kaçan bu noktalar aslında doğrudan uygulama ile ilgili olmasa da dolaylı olarak 
uygulamayı etkileyecek adımlar olabilir. Bu aşamalar net bir biçimde belirlenmez ise projenin ilerleyen aşamalarında bu 
boşluk yersiz ve yanlış varsayımlarla doldurulabilir. Bu da gereksinimleri karşılamaktan uzak bir ürünün ortaya çıkmasına 
sebep olur.

Bu bağlamda senaryoları *business* ve *product* senaryolar olmak üzere ikiye ayırabiliriz. *Business* senaryolar, işleyişi 
uçtan uca kapsayan tüm hikayedir. *Product* senaryolar ise hikayenin bütünü içerisinde uygulama tarafından gerçekleştirilecek
olan kısımlardır. Önceki yazılarımızda da değindiğimiz su sipariş sistemi üzerinden örnek verecek olursak; müşterinin 
telefon açması ile başlayan ve suyu alıp ödemeyi yapması ile sonlanan sürecin tümü bir *business* senaryodur. Bu senaryo, 
müşterinin çağrı merkezini araması ile başlar, çağrı merkezi müşterinin siparişini, teslimat ve ödeme bilgilerini alır ve 
dağıtıcıya iletir, dağıtıcı siparişi teslim eder ve ödemeyi tahsil eder. Kabaca tanımladığımız bu işleyiş detaylandırıldıkça 
bazı adımların geliştirilecek uygulama üzerinden yürüyeceği, bazı adımların ise manuel işletileceği ortaya çıkacaktır. 
*Product* senaryolarını açık ve net bir biçimde belirleyebilmek için öncelikle *business* senaryolar belirlenmelidir.

Senaryolar üzerinde çalışmaya ilk olarak normal işleyiş (*happy path*) üzerinden başlamak gereklidir. Özellikle teknik 
kişilerin bulunduğu çalışmalarda, belki de entelektüel seviyenin korunmaya çalışılmasından dolayı, konunun akışı normal 
işleyişten çok aykırı ve özel durumlara yönlenebilir. Bu gidişat bir süre sonra insanların kendilerini ana fikirden 
uzaklaşmış ve problemlere *workaround* çözümler arar hale gelmiş bir yerlerde gezinirken bulmalarına sebep olabilir. 
Bu nedenle normal durum senaryolarını tam olarak bitirmeden aykırı ve özel durumlara geçilmemelidir.

Normal durum senaryoları tamamlandıktan sonra alternatif işleyişler üzerine düşünülmelidir. Alternatif akışlar, normal 
işleyişe paralel olarak yürütülebilen ve sonunda aynı sonuca ulaştıran farklı yollardır. Örneğin müşterinin ödemeyi nakit 
yapması beklenirken promosyon kuponu kullanması gibi.

Alternatif adımlar da belirlendikten sonra aykırı durumlar ve *what-if* senaryoları üzerinde konuşulmalıdır. Aykırı durumlar,
normal işleyişi kesintiye uğratan adımlardır. Örneğin “Dağıtıcı müşterinin adresine gittiğinde adreste kimse yoksa ne yapmalı?” 
sorusunun cevabı bir aykırı durum senaryosudur.

Aykırı durum senaryoları da net bir biçimde ortaya konduktan sonra negatif senaryolar üzerinde çalışılmalıdır. Negatif 
senaryolar, normal akışta adımların art niyetle ya da bilmeyerek (!) farklı bir biçimde işletilmesi durumudur. Örneğin 
müşterinin aslında olmayan bir adres vermesi durumunun ele alınması.

Senaryolar üzerinde yukarıda belirttiğimiz detaylarda çalışıldıkça işleyiş evrilecek ve tıpkı bir heykeltıraşın eseri 
gibi zamanla mükemmelleşecektir. Böylece *business* ve *product* senaryolar arasındaki ayrım ve sınırlar da daha da 
belirgin bir hale gelecektir. Bundan sonraki adım, senaryoların detayların gözden kaçırılmasını önleyecek bir biçimde 
ifade edilmesidir. Bunun için *use-case* çizenekleri, metinsel bir şablon ya da aktivite diyagramları kullanılabilir. 
Bunlardan hangisini kullanmak daha iyidir gibi bir tartışmaya girmeyi oldukça gereksiz bulduğumu özellikle belirtmek 
isterim. Neticede bunların her biri bizim alet çantamız içindeki araçlarımızdır. Uygun olanını kullanmak da tamamen bize 
kalmış.
