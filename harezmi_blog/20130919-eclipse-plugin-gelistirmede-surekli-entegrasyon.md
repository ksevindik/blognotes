# Eclipse Plugin Geliştirmede Sürekli Entegrasyon

Yazar: Murat Öksüzer

Merhaba arkadaşlar. Bu yazımızda Eclipse Plugin projelerinin build edilmesi, update site üretimi gibi işlerin 
otomatikleştirilmesinden bahsedeceğiz.

Eclipse pluginleri update site’lar aracılığıyla dağıtılmaktadır. Update site’lar değişik “feature”‘lardan meydana 
gelebilirler. Bu feature’lar da bir veya birden fazla “plugin”‘in bir araya gelmesiyle oluşmaktadır.

Bir Eclipse Plugin projesi kendine has proje yapısına sahiptir ve default br projede maven, ant vb. bir build script 
bulunmamaktadır. Projeler Eclipse PDE (Plugin Development Environment) apisi tarafından build edilmektedir. Sürekli 
entegrasyon işine girebilmek için bu projeleri build eden araçlara ve scriptlere ihtiyaç var. Biz de build aracı olarak 
Maven’ı seçtik, işe koyulduk ve projelerimizi “mavenize” ettik. Yani projelere pom.xml dosyası ekledik. Mavenize ederken 
proje yapısını değiştirmemek gerekiyor çünkü geliştirme yaparkan build işlemi PDE apisi tarafından yapılıyor ve klasör 
yapısı değişikliği bu işlemi kötü yönde etkileyebiliyor.

Eclipse Plugin projelerini maven ile build etme denince akla gelen ilk seçenek Tycho olmakta. Tycho, eclipse plug-in, 
feature, update site, RCP application ve OSGi bundle projelerini build etmek üzere geliştirilmiş bir Maven 3 pluginidir. 
Bu plugin, projelerin kendi metadatalarını (plugin.xml, feature.xml, manifest.mf vb.) kullanmakta ve pom.xml dosyası 
içerisinde konfigüre edilmekte. Maven’ın modüler build özelliğinden yararlanmakta. Parent bir proje oluşturup, build 
edeceğimiz projeleri bu projeye modül olarak tanımladıktan ve modüllere de parent projeyi tanıttıktan sonra projelerimizi 
derleyebiliyoruz.

Kulağa çok hoş gelen bu özelliklerini öğrendikten sonra biz de bu plugini kullanmak istedik. Fakat henüz tam 
olgunlaşmadığını, exceptionlarla boğuşmaya başlayınca anladık. Biz de kendi yolumuzu bulmaya koyulduk.

Öncelikle, projelerin maven ile build ediliyor hale gelmesi gerekiyor. Bunun için Maven’ın compile sırasında ihtiyaç 
duyduğu dependencyleri pom.xml içerisinde tanımlamalıyız. Bunun için build path’de bulunan “Plugin Dependencies”, 
“Referenced Liblaries” vb bölümlerinde bulunan harici tüm kütüphanelerin maven artifact olarak pom.xml’e eklenmesi 
ihtiyacı doğuyor.

Plugin Dependencies genelde org.eclipse ile başlayan eclipse pluginlerinden ibarettir. Bunlar “eclipse/plugins” 
klasörünün altında bulunuyor. Bu pluginlerin isimlendirmesi aşağıdaki gibidir:

```console
pluginid_version.jar
```

Bunu maven’ın anlayacağı bir artifact yapısına çevirmek istediğimizde aşağıdaki gibi bir klasör yapısı altında 
konumlandırmamız gerekmektedir(alt çizgi tireye dönüşüyor):

```console
pluginid/version/pluginid-version.jar
```

“eclipse/plugins” klasörü altında bulunan tüm jarları bu şekilde mavenize ettik. Group id olarak kullanılacak olan bir 
klasör içinde konumlandırdık:

```console
com/organizationname/pluginid/version/pluginid-version.jar
```

Bu yapıyı arşivleyip Artifactory repositorimize artifact bundle olarak yükledik. Bu şekilde, aşağıdaki gibi bir dependency 
elementiyle projemize gerekli pluginleri ekleyebiliyor hale geldik:

```xml
<dependency>
    <groupId>com.organizationname</groupId>
    <artifactId>pluginid</artifactId>
    <version>version</version>
</dependency>
```

Plugin projeleri için örnek bir pom.xml aşağıdaki gibidir:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
<modelVersion>4.0.0</modelVersion>
<groupId>com.organizationname</groupId>
<artifactId>plugin_id</artifactId>
<version>1.0</version>

    <parent>
        <groupId>com.organizationname</groupId>
        <artifactId>parent-project</artifactId>
        <version>1.0.0</version>
        <relativePath>../parent-project</relativePath>
    </parent>

    <dependencies>
    <!-- buraya gerekli dependencyler gelecek -->
    </dependencies>
    <build>
        <sourceDirectory>src</sourceDirectory>
        <resources>
            <resource>
                <directory>.</directory>
                <includes>
                    <!-- buraya plugin jarında bulunması gereken dosyalar listelenmelidir.
                    klasik yoldan üretilmiş bir jar'ın içeriğine bakılarak hangilerinin gerekli olduğu çıkarılabilir.-->
                    <include>plugin.xml</include>
                    <include>about.ini</include>
                    <include>icons/**</include>
                    <include>*.jar</include>
                    <include>lib/**</include>
                </includes>
            </resource>
       </resources>
       <plugins>
           <plugin>
               <artifactId>maven-compiler-plugin</artifactId>
               <version>3.1</version>
               <configuration>
                   <archive>
                        <manifestFile>META-INF/MANIFEST.MF</manifestFile>
                   </archive>
                   <source>1.6</source>
                   <target>1.6</target>
               </configuration>
           </plugin>
           <plugin>
               <artifactId>maven-jar-plugin</artifactId>
               <version>2.3.2</version>
               <configuration>
                   <archive>
                       <manifestFile>META-INF/MANIFEST.MF</manifestFile>
                   </archive>
                   <source>1.6</source>
                   <target>1.6</target>
               </configuration>
           </plugin>
       </plugins>
    </build>
</project>
```

Pluginlerimizi bu şekilde maven ile build edilebiliyor hale getirdik. Feature projelerimizi de build sonucu çıkan 
artifactin feature.xml dosyasını içerecek şekilde konfigüre ettik. Feature projeleri için örnek bir pom.xml aşağıdaki 
gibidir.

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
<modelVersion>4.0.0</modelVersion>
<groupId>com.organizationname</groupId>
<artifactId>feature_id</artifactId>
<version>1.0.0</version>

    <parent>
        <groupId>com.organizationname</groupId>
        <artifactId>parent-project</artifactId>
        <version>1.0.0</version>
        <relativePath>../parent-project</relativePath>
    </parent>

    <build>
        <resources>
            <resource>
                <directory>.</directory>
                <includes>
                    <include>feature.xml</include>
                </includes>
            </resource>
        </resources>
        <plugins>
            <plugin>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.1</version>
                <configuration>
                    <archive>
                        <addMavenDescriptor>false</addMavenDescriptor>
                    </archive>
                    <source>1.6</source>
                    <target>1.6</target>
                </configuration>
            </plugin>
            <plugin>
                <artifactId>maven-jar-plugin</artifactId>
                <version>2.3.2</version>
                <configuration>
                    <archive>
                        <addMavenDescriptor>false</addMavenDescriptor>
                    </archive>
                    <source>1.6</source>
                    <target>1.6</target>
                </configuration>
            </plugin>
       </plugins>
    </build>
</project>
```

Update Site oluşturabilmek için ayrı bir program yazmamız gerekti. Bu program (p2_repository_generator olarak isimlendirelim), 
plugin ve feature projelerimizin maven ile “clean package” goal’u ile build edilmesinden sonra “target” klasörleri altında 
oluşan jar dosyalarını topluyor ve update site klasör yapısında yeniden konumlandırıyor. Ayrıca site.xml dosyasını da 
üretiyor:

```console
updatesite/features/feature-artifact-jars
updatesite/plugins/plugin-artifact-jars
updatesite/site.xml
```

Bu klasör yapısındaki update site, Eclipse tarafından kullanılmaya hazırdır. Fakat şart olmamakla birlikte güncel p2 
repository’leri ekstra metadata dosyaları (artifacts.jar ve content.jar) beklemektedir. Bunları üretmek için de Eclipse’in 
komut satırı uygulaması olan “UpdateSite Publisher”‘ı kullandık (org.eclipse.equinox.p2.publisher.UpdateSitePublisher). 
Bu uygulama input olarak içinde site.xml ve gerekli jarlar bulunan bir klasör alıyor ve ortaya artifacts.jar ve content.jar 
içeren bir p2 repository çıkarıyor. Yukarıda ürettiğimiz update site klasörünü source input olarak verdik:

```shell
$eclipse -application org.eclipse.equinox.p2.publisher.UpdateSitePublisher -metadataRepository file:/path_to_output_directory  -artifactRepository file:/path_to_output_directory   -source /path_to_updatesite  -configs gtk.linux.x86 -compress -publishArtifacts
```

Çıktı şu yapıdadır :

```console
path_to_output_directory/features/feature-artifact-jars
path_to_output_directory/plugins/plugin-artifact-jars
path_to_output_directory/artifacts.jar
path_to_output_directory/content.jar
```

site.xml dosyamızı da bu klasöre attığımız zaman eksiksiz bir plugin update site oluşturmuş oluyoruz.

p2_repository_generator programımıza içerden bu komut satırı uygulamasını çağırma özelliği ekledik.

Sürekli entegrasyon aracı olarak Jenkins’i kullandık. Biri plugin ve feature projelerini build etmekle sorumlu, diğeri 
de p2_repository_generator programını çalıştıran scripti çalıştırmakla sorumlu iki job tanımladık. p2_repository_generator 
jobu, diğer job build ettiğinde tetiklenecek şekilde ayarlamamızı yaptık.