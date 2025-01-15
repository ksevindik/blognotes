# Nasıl Profesyonel Yazılımcı Olunur?

Yazar: Murat Öksüzer

![](images/clean_code_01.jpeg)

Herkese merhabalar. Bu yazımızda [Robert C. Martin](http://en.wikipedia.org/wiki/Robert_Cecil_Martin)‘in, nam-ı diğer Bob Amca’nın, profesyonellik adına biz yazılımcılara 
sunduğu altın öğütlerden bahsedeceğiz.

Kısaca profesyonellikten bahsedelim. İşini ciddiye alan, yaptığı iş ile gurur duyan, neye ihtiyacı olduğunu bilen ve bu 
ihtiyaçlardan taviz vermeyenler profesyonel olarak nitelenirler. Yazılım dünyasında da durum böyledir. Bu vasıfları 
taşıyanlara profesyonel, usta veya ilkeli yazılımcı denir.

Etrafımıza baktığımızda içinde yazılım bulunan cihazların günden güne arttığını görmekteyiz. Böyle bir ortamda ilkesiz 
olarak yazılım geliştirmek ciddi maddi zararlara neden olabileceği gibi can kayıpları ile sonuçlanan felaketlerle de 
karşılaşılabilir.

Peki nasıl profesyonel yazılımcı olunur? Takip edilmesi gereken ilkeler nelerdir?

### 1 – Çöp kod teslim etme! – *We will not ship shit!*
Hangi koşullar altında olursa olsun. Patronunuz ne kadar ısrarcı olursa olsun, çöp kod teslimi yapmamalısınız. Kodun kötü 
durumda olduğunu, tamamlanabilmesi için biraz daha zaman gerektiğini söyleyecek tek kişi sizsiniz.

### 2 – Daima hazır ol!
Her an projenin deploy edilebilir ve çalıştırılabilir durumda olduğundan emin ol. Sürüm hazır değil, kalite kontrolde 
bekliyor vb. gecikmelere veda etme zamanı. Sürüm yayınlandıktan sonra kararlı duruma getirmeye çalışma. Her zaman kararlı 
bir sürümün bulunsun. Derlenmeyen veya çalışmayan kodun repositörde yeri yoktur.

### 3 – İstikrarını koru! – *Stable Productivity*
Üretkenliğin, uğraştığın kodun azlığıyla veya fazlalığıyla değişmemeli. Yeni bir özelliği implement etme hızın belli bir 
sabitin altına inmemeli. Bunu yapabilmen için de kodu keşmekeş içine sokmadan sürekli olarak temiz tutmak durumundasın.

### 4 – Esneklik – *Inexpensive Adaptability*
Sisteme yeni bir özellik eklemek veya çıkarmak, sistemin baştan sona tekrardan tasarlanmasını gerektirmemeli. Müşterinin 
fikir değiştirme olasılığı oldukça yüksek olduğundan sistem en baştan modüler bir yapıda tasarlanmalıdır. Kullanılan 
veritabanı birkaç gün içerisinde değiştirilebilir olmalı. Hatta ilişkisel veritabanından NoSQL veritabanına geçiş ihtimali 
bile düşünülmelidir.

Web sadece bir I/O bileşenidir. Web olmadığı zamanlarda da uygulamalar olduğu gibi gelecekte de webin değişeceği 
öngörülebilir. Uygulama herhangi bir I/O channela uyarlanabilir şekilde tasarlanmalıdır.

### 5 – Gelişimi Sürekli Kıl – *Continuous Improvement*
Yeni bir kütüphane veya dil çıktığında mümkün olduğunca kullanmaya bak. Kodu bulduğundan daha temiz bırak.

### 6 – Koda Dokunmaktan Korkma – *Fearless Competence*
Kodda değişiklik yapmaktan korkma. Hatalı gördüğün yeri düzelt. Bozmadığından emin olmak için değişik disiplinlerden 
faydalanabilirsin, *Test Driven Development* gibi.

### 7 – Yüksek Kaliteyi Hedefle – *Extreme Quality*
Yapabileceğinin en iyisini yap. Yazabileceğin en temiz kodu yaz, yapabileceğin en dürüst tahminlerde bulun, 
tasarlayabileceğin en esnek, uyarlanabilir mimariyi tasarla.

Bob Amca’nın öğütleri önümüzdeki yazılarda devam edecek. Bir sonraki paylaşımda buluşmak üzere...
