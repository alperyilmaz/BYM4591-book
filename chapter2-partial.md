# GNU/Linux Komutları

Terminalde kullanılabilecek komutların tamamı oldukça uzun bir liste oluşturabilir. Kitapta verilen komutlar buradaki örneklerin ve problemlerin çözülmesi için gerekli olan komutlardır. Listenin tamamı aşağıdaki kaynaklarda bulunabilir:

* [ss64.com](http://ss64.com/bash/)
* Terminalde **`compgen -acbk`** komutu çalıştırılabilecek bütün komutları listeler.
* [Linux Complete Command Reference](http://www.amazon.com/Linux-Complete-Command-Reference-Purcell/dp/0672311046/ref=pd_sim_sbs_14_2?ie=UTF8&refRID=0JBHXM2MMTRM2TXDF3JX) adlı kitap
* [Linux in a Nutshell](http://www.amazon.com/Linux-Nutshell-Ellen-Siever/dp/0596154488) adlı kitap

Yukarıdaki kaynaklara ek olarak, [ExplainShell](http://explainshell.com/) adlı websayfasını kullanarak, kitaptaki komutların veya başka kaynaklarda karşılaştığınız komutların açıklamalarını görebilirsiniz. 

Ayrıca, bu kitapta verilen komutların fazla sayıda opsiyonları (veya argümanları) bulunmaktadır. Bu kitapta sadece Veri Analizi ve Görüntüleme dersi için yeterli olanları gösterilecektir. Bütün opsiyonları görmek için **`man komut`** ile komuta ait detaylı bilgilere ulaşılabilir.

> ### Başlamadan Önce
>
> Aşağıdaki komutlardaki örneklerin ve bölüm sonlarındaki soruların yapılabilmesi için kitapla beraber hazırlanmış arşiv dosyası aşağıdaki komutlar yardımıyla indirilip açılmalıdır.
>
>    curl -L  https://goo.gl/i4wD9H > veri-analizi-bundle.tar.gz
>    tar xzf veri-analizi-bundle.tar.gz


## man komutu

İngilizce orijinal tarifi: "an interface to the on-line reference manuals"

Komutların farklı fonksiyonlarını ve görevlerini görüntüler. Örneğin **`ls`** komutunun kullanımını öğrenmek için **`man ls`** yazıp enter tuşuna basıldığında aşağıdaki ekran görülür. Aşağı ve yukarı ok tuşları ile interaktif olarak doküman okunabilir ve açılan dosyadan q tuşu ile çıkış yapılır.

<<[Şekil 2.1 ls komutunun man komutu ile açıklanması](code/man-ls.txt)

## ls komutu

İngilizce orijinal tarifi: "list directory contents"

Geçerli dizindeki dosyaların alfabetik olarak sıralanmış listesini gösterir. Nokta (.) karakteri ile başlayan dosya isimlerini ilk sıraya koyar. Birçok opsiyonu olmakla birlikte, en çok kullanılan opsiyonlar şunlardır:

* **`ls -a`** (all) : Geçerli dizindeki tüm dosyaların listesini gösterir. Gizli dosya ve dizinleri de gösterir.
* **`ls -l`** (long) : Geçerli dizindeki tüm dosyaları ayrıntılarıyla gösterir. (izin - kullanıcı - boyut - tarih - dosya adı)
* **`ls -t`** (time) : Geçerli dizindeki dosyaları yüklenme tarihlerine göre sondan başa doğru sıralayarak gösterir.
* **`ls -S`** (size) : Geçerli dizindeki dosyaları boyutlarına göre büyükten küçüğe doğru sıralayarak gösterir.
* **`ls -r`** (reverse) : Sıralama düzenini tersine çevirerek gösterir. Eğer başka bir seçenekle kullanılmamışsa alfabetik sıralamanın tersine göre.
* **`ls -R`** (recursive) : Tüm dosyaları alt dizinleri ve içerikleri ile birlikte gösterir.
* **`ls -h`** (human readable) : Tüm dosyaları insan okunabilir şekilde gösterir. Ama tek başına işlevi yoktur. Dosya boyutunu gösteren seçenekler ile birlikte kullanılmalıdır.

Seçenekler birleştirilerek de kullanılabilirler. Örnek; ls -lrt dosyaları tarihlerine göre baştan sona doğru ve ayrıntılarıyla gösterir.

<<[Şekil 2.2 ls komutunun farklı opsiyonları/argümanları](code/ls-ornek.txt)

## cd komutu

Klasör değiştirerek, dizinler arası gezinmeyi sağlayan komuttur. Göreceli veya mutlak olarak klasör belirtmek mümkündür. Göreceli klasör belirtmek o anda çalışılan klasöre göre konum belirleyerek, mutlak konum belirleme ise kökten (İng. root) (/) başlayarak gidilmek istenen yer belirterek gerçekleşmektedir.

* **`cd <klasör.adı>`** : \<klasör.adı\> isimli klasörün içine girmeyi sağlar.
* **`cd ~`** : Hangi klasörde olunursa olunsun kullanıcının home klasörüne gitmeyi sağlar.
* **`cd ..`** : İşlem yapılan klasörün bir üst klasörüne geri dönmeyi sağlar.
* **`cd ../..`** : İşlem yapılan klasörün iki üst klasörüne gitmeyi sağlar.
* **`cd -`** : İşlem yapılan klasörden bir önce girilen klasöre gitmeyi sağlar.

> Terminalde sadece `cd` yazarak Enter tuşuna basıldığında `cd ~` şeklinde çalışır ve kullanıcının home klasörüne geçiş yapılır.


<<[Şekil 2.3 cd komutunun farklı kullanımları](code/cd-ornek.txt)

%%%% TODO cd example is not clear

> [Boşluk karakteri](#bosluk-karakteri) içeren dosya ve klasör isimlerine dair dikkat edilmesi gereken durum hakkında ilgili bölümü okuyunuz.

>### Sorular
>* `find-file` adlı klasör içinde cd ve ls komutları yardımıyla `image.jpg` dosyasını bulunuz.

## mkdir komutu

İngilizce orijinal tarifi: "make directories"

Geçerli dizinde klasör açmayı sağlayan komuttur.

* **`mkdir <klasör.adı>`** : Geçerli dizin içine \<klasör.adı\> isimli klasörün açılmasını sağlar.
* **`mkdir -p <klasör.adı1>/<klasör.adı2>/<klasör.adı3>`** : Geçerli klasör içine \<klasör.adı1\> isimli klasör, alt klasörü olarak \<klasör.adı2\> isimli bir klasör ve onun da alt klasörü olarak \<klasör.adı3\> isimli klasör açar. Komutun çalışabilmesi için klasör sayılarında bir sınırlama yoktur.

! **`mkdir`** komutu ile olmayan bir klasöre alt klasör açılmak istendiğinde hata mesajı ile karşılaşılabilir.Ancak **`mkdir -p`**komutu ile yeni bir klasöre alt klasör açılabilir.
[kaynak](http://docplayer.biz.tr/60171-Linux-server-temel-komutlar.html)

<<[Şekil 2.4 mkdir komutunun kullanımı](code/mkdir-ornek.txt)

## pwd komutu

İngilizce orijinal tarifi: "print name of current/working directory"

İçinde bulunulan klasörün mutlak konumunu ekranda gösterir.

<<[Şekil 2.5 pwd komutunun kullanımı](code/pwd-ornek.txt)

## touch komutu

Geçerli dizinde boş bir dosya açmayı sağlayan komuttur.

* **`touch <dosya.adı>`** : Geçerli dizin içine \<dosya.adı\> isimli boş bir dosya oluşturur.

>### Sorular
>* `touch` komutu yardımıyla, `test.png`, `test.mp3`,`test.doc` adlı dosyalar oluşturulursa, bunlar sırasıyla resim, müzik ve Word dökümanı mı olurlar?
>* `mkdir` ve `touch` komutlarını kullanarak `genomes` adlı klasör oluşturup içinde aşağıda gösterilen klasör ve dosya yapısını oluşturunuz. 

![genomes adlı klasör yapısı](images/genomes-folder.png)

> Doğru klasör yapısı oluşturulduğunda `genomes` klasörü içinde `find` komutunun çıktısı aşağıdaki gibi olmalıdır:

<<[genomes klasörü içeriği - find komutu çıktısı](code/genomes-folder.txt)

## rm komutu

İngilizce orijinal tarifi: "remove files or directories"

Geçerli dizinde bulunan dosyaları veya klasörleri silmeyi sağlar. 

* **`rm <dosya.adı>`** : Geçerli dizin içindeki \<dosya.adı\> isimli dosyanın silinmesini sağlar.
* **`rm -r <klasör.adı>`** : Klasörleri altdizin ve içerisinde bulunan dosyalar ile birlikte siler. Komut bazı durumlarda çalışmadan önce onay ister ve onaylamak için y tuşuna basılmalıdır.

<<[Şekil 2.6 rm komutunun kullanımı](code/rm-ornek.txt)

> Terminalde, "çöp kutusu" kavramı olmadığından dosyalar geri dönüşüme gitmeden silinir.

## cp komutu

İngilizce orijinal tarifi: "copy files and directories"

Geçerli klasör içinde bulunan bir dosyanın, başka bir klasöre veya başka bir dosyanın üzerine kopyalanmasını sağlar. 

* **`cp <kaynak.dosya.adı> <hedef.dosya.adı>`** : Geçerli klasördeki \<kaynak.dosya.adı\> isimli dosyanın \<hedef.dosya.adı\> isimli dosya olarak kaydedilmesini sağlar.
* **`cp -i <kaynak.dosya.adı> <hedef.dosya.adı>`** : Var olan bir dosya üzerine yazma durumlarında interaktif şekilde onay istenmesini sağlar. 
* **`cp -p`** : Kopyalanacak olan dosyanın kopyalama sırasında [dosya ve klasör izinleri](#dosya-klasor-izin) kısmında anlatılan izin ve özelliklerini değiştirmeden kopyalanmasını sağlar.
* **`cp -r`** : Klasörleri alt dizinleri ve dosyaları ile birlikte kopyalar.
* **`cp -u`** : Güncelleme olduğunda dosya ve klasörleri değiştirmeden kopyalar.

Kopyalanan dosya aynı klasör içine değil, farklı bir klasör içine kopyalanmak isteniyorsa; hedef klasörün ismi ~/\<hedef.klasör.adı\> şeklinde yazılmalıdır. Komutu kullanmak için kopyalanacak dosyanın bulunduğu klasör içinde olmaya gerek yoktur. Herhangi bir klasörden her klasöre kopyalama yapılabilir.

<<[Şekil 2.7 cp komutunun kullanımı](code/cp-ornek.txt)

%%%% TODO: cp komutu örneği geliştirilmeli, PATH (relative and absolute) kavramı bahsedilmeli

##  mv komutu

İngilizce orijinal tarifi: "move (rename) files"

Dosyaların aynı isimle ya da ismi değiştirilerek farklı bir klasör içine taşınmasını sağlar.

* **`mv <dosya.adı> <hedef.klasör.adı>`** : Geçerli dizin içindeki dosya hedef klasöre kopyalanıp geçerli dizindeki kopyası silinir, böylelikle dosya hedef klasöre taşınmış olur. Bu işlem aynı klasör içinde gerçekleştirilirse dosya ismi değiştirilmiş olur. 

<<[Şekil 2.8 mv komutunun kullanımı](code/mv-ornek.txt)

%%%% TODO mv example was not clear.. mv-ornek.txt has been updated by gamzebagımsız, can be improved further..

> [Boşluk karakteri](#bosluk-karakteri) içeren dosya ve klasör isimlerine dair dikkat edilmesi gereken durum hakkında ilgili bölümü okuyunuz.

>### Sorular
>* Sayı1000 isimli dosyanın sayılar adlı **kopyasını** oluşturun.
>* `sayılar` dosyasını `depo` isimli yeni bir klasör açarak içine taşıyın.
>* `depo` klasörünü `depo2` klasörü olarak içindeki sayılar dosyası ile birlikte taşıyın.
>* `touch` komutu egzersizinde oluşturmuş olduğunuz `genomes` adlı klasörün içeriklerini, mkdir, touch, cp, mv komutlarını kullanarak aşağıdaki hale getiriniz.

![Ulaşılması gereken klasör yapısı](images/genomes-folder2.png)

> Yukarıdaki soruda, `fish` klasörü altında bulunan `penguen.fa` dosyasının `birds` adlı klasörün altına taşınması için `fish` klasörü içinde olmak şart değildir. Herhangi bir klasörde iken uygun `mv` komutu ile taşıma gerçekleştirilebilir. Taşınacak dosyanın bulunduğu klasör veya hedef klasör mutlak veya göreceli olarak belirtilebilir. Aşağıdaki örnekte üç farklı geçerli dizinde bulunurken `mv` komutunun nasıl yazılacağı gösterilmiştir.

<<[Şekil 2.8a mv komutunun geçerli dizine göre değişmesi](code/mv-path.txt)

> universiteler.tar.gz adlı arşiv dosyasının içeriği ÖSYM'nin [2015 tarihli kılavuzuna](http://dokuman.osym.gov.tr/pdfdokuman/2015/OSYS/OSYS2015YerlestirmeMinMaxTablo-423072015.pdf) göre hazırlanmıştır. Her bir üniversite ve içerdiği fakülteler klasör olarak, bölümler de dosya olarak gösterilmiştir. Arşiv dosyasını açtıktan sonra aşağıdaki soruları cevaplayınız:
>
>* YTU altında "Tip Fakultesi" açınız.
>* YTU Tip Fakultesi altına Dahiliye ve Cildiye bölümleri açınız.
>* YTU'den "Iktisadi ve Idari Bilimler Fakultesi"ni kaldırınız.
>* YTU'ye Isik Univ. "Guzel Sanatlar Fakultesi"ni bölümleriyle beraber kopyalayınız.
>* IPEK UNIVERSITESI, Insan ve  Toplum Bilimleri Fakultesi altındaki bütün ingilizce bölümleri kapatınız.

%%%% TODO we need more questions for cp, mv, mkdir

> Uzun klasör isimlerini yazarken ilk birkaç harften sonra Tab tuşuna basıldığında klasör veya dosya adı tamamlanacaktır.

## seq komutu

İngilizce orijinal tarifi: "print a sequence of numbers"

Belli artımlarla sayı oluşturulup ekranda görüntülenmesini sağlar. Üç farklı kullanım seçeneği vardır. Bunlar:

* **`seq <sayı>`** : 1'den başlayarak, belirtilen sayıya kadar olan ardışık sayıları ekrana basar.
* **`seq <sayı1> <sayı2>`** : Sayı1'den başlayarak sayı2'ye kadar olan ardışık sayıları ekrana basar.
* **`seq <sayı1> <artım.miktarı> <sayı2>`** : sayı1'den başlayarak sayı2'ye kadar, belirtilen artım miktarı kadar artan sayıları ekrana basar.
* **`seq -w`** : Sayıların eşit genişlikte olmasını sağlar. Böylelikle, üretilen sayılar alfabetik sıralama için uygun hale gelir ve sayısal sıralamaya gerek kalmaz.

<<[Şekil 2.9 seq komutunun kullanımı](code/seq-ornek.txt)

## shuf komutu

İngilizce orijinal tarifi: "generate random permutations"

Rastgele sıralama yapılmasını sağlar.

* **`shuf <dosya.adı>`** : Geçerli dizindeki \<dosya.adı\> isimli dosya içinde bulunan bilgilerin sıralamasını, rastgele permutasyonlar şeklinde gerçekleştirir.

> Aşağıdaki örnekte de görüldüğü gibi, **`shuf`** komutu ve birçok komut, hem bir dosya üzerinde çalıştırılabilir hem de çubuk ile başka bir komutun çıktısı üzerinde çalıştırılabilir.

<<[Şekil 2.10 shuf komutunun kullanımı](code/shuf-ornek.txt)

>### Sorular
>* 1-100 arası 5'e bölünebilen sayıları ekranda görüntüleyin.
>* 1-50 arası 3'e bölünebilen rakamları ekranda görüntüleyin.

## cat komutu

İngilizce orijinal tarifi: "concatenate files and print on the standard output"

Dosyaların görüntülenmesini sağlar. Komutun `tac` şeklinde, tersten çalıştırılarak dosyanın sondan başa doğru görüntülenmesi de mümkündür.

* **`cat <dosya.adı>`** : Geçerli dizinde bulunan dosyaların içinin ekranda görüntülenmesini sağlar.

<<[Şekil 2.11 cat ve tac komutlarının kullanımı](code/cat-ornek.txt)

## head komutu

İngilizce orijinal tarifi: "output the first part of files"

Dosya içeriğinin başından ne kadar uzunlukta görüntüleneceğini belirler.

* **`head <dosya.adı>`** : Geçerli dizinde bulunan dosya.adı isimli dosyanın ilk 10 satırının görüntülenmesini sağlar.
* **`head -numara <dosya.adı>`** : Geçerli dizinde bulunan dosya.adı isimli dosyanın baştan itibaren, belirtilen sayıda satırının görüntülenmesini sağlar.
* **`head -n -<sayı> <dosya.adı>`** : Geçerli dizinde bulunan dosya.adı isimli dosyanın son `sayı` kadar satırı hariç bütün satırların görüntülenmesini sağlar.

## tail komutu

İngilizce orijinal tarifi: "output the last part of files"

Dosya içeriğinin sonundan kaç satır görüntüleneceğini belirler. Satırları tersten değil olması gereken sırada görüntüler.

* **`tail <dosya.adı>`** : Geçerli dizinde bulunan dosya.adı isimli dosyanın son 10 satırının görüntülenmesini sağlar.
* **`tail -numara <dosya.adı>`** : Geçerli dizinde bulunan dosya.adı isimli dosyanın sondan itibaren, belirtilen sayıda satırının görüntülenmesini sağlar.
* **`tail -n +<sayı> <dosya.adı>`** : Geçerli dizinde bulunan dosya.adı isimli dosyanın `sayı`. satırından itibaren görüntülenmesini sağlar.

<<[Şekil 2.12 head ve tail komutlarının kullanımı](code/head-tail-ornek.txt)

![Şekil 2.13 head ve tail komutlarının farklı kullanımları](images/head-tail.png)

>### Sorular
>* 20'den başlayarak sıralı 55. sayıyı ekranda görüntüleyin.
>* İlk 175 sayının son 10 tanesini ekranda görüntüleyin.
>* 7'ye bölünebilen ilk 15 sayının rastgele seçilmiş 5 tanesini ekranda görüntüleyin.
>* sayı1000 dosyasından 850-860 arasındaki sayıları ekranda görüntüleyin. (850 ve 860 dahil.)
>* sayı1000 dosyasının en ortasında bulunan iki sayıyı ekranda görüntüleyin.
>* sayı1000 dosyasındaki ilk çift sayıdan sonraki 24. sayıyı ekranda görüntüleyin.
>* harfler dosyasındaki 15. satırdaki harfi bulunuz.



## less komutu

Geçerli dizinde bulunan dosyaların interaktif şekilde görüntülenmesini sağlar. Ok tuşları ile ekran kaydırılabilir, > tuşu ile dosya sonuna, < tuşuyla dosyanın başına gidilebilir. Ayrıca, dosya içinde arama yapmak da mümkündür. Açılan ekrandan q tuşuna basılarak çıkış yapılır.

* **`less <dosya.adı>`** : Geçerli klasördeki \<dosya.adı\> isimli dosya içinde yazılı olanları farklı bir bölümde görüntüler. 
* **`less -N <dosya.adı>`** : Dosya içeriğini satırlara numara vererek görüntüler. 
* **`less -R <dosya.adı>`** : Dosya içinde bulunan özel karakterlerin görüntülenmesini sağlar. Terminalde var olan renklerin korunması için kullanılabilir.

## echo komutu

İstenilen yazıların ekrana basılmasını sağlar.

* **`echo "yazı"`** : Yazı ifadesinin ekrana basılmasını sağlar. 

<<[Şekil 2.14 echo komutunun kullanımı](code/echo-ornek.txt)

## rev komutu

İngilizce orijinal tarifi: "reverse lines of a file or files"

Dosya veya girdi içeriğindeki karakterleri ters sırada ekrana yazar.

* **`rev <dosya.adı>`** : Geçerli klasörde bulunan \<dosya.adı\> isimli dosyanın içindeki satırların karakterlerini kendi içinde ters sırada ekranda görüntüler.

<<[Şekil 2.15 rev komutunun kullanımı](code/rev-ornek.txt)

## Dosya türleri ve uzantıları (uyguluma)

Birinci bölümde açıklanan [dosya türleri](#dosya-turleri) konusunu uygulamalı olarak anlamaya çalışalım. `seq 1 10` komutu yardımıyla .png, .doc, .xls, .csv, ve .txt dosyaları oluşturunuz.

<<[Şekil 2.15n Farklı türlerde dosya oluşturulması](code/dosya-turleri.txt)

Klasörünüzde önceden bulunan `real.doc` dosyası ile yeni oluşturduğunuz `fake.doc` adlı dosyayı hem Linux terminalinde hem de Windows işletim sisteminde karşılaştırınız (bunu xls, png, csv dosyaları için de tekrar ediniz)

Klasörünüzde bulunan `real.svg` dosyası [scalable vector graphics](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics) adlı bir resim formatı olup, düzyazı (plain text) karakterleri kullanılarak resim çizdirme komutlarının özel bir [XML formatı](https://en.wikipedia.org/wiki/XML) haline getirilmesiyle ortaya çıkar. Kısacası, doc, xls veya png gibi dosya türleri binary format olabildiği gibi, plain text formatında olan dosyalar ile de resim veya diğer tür formatlar türetilebilir.

> Dosyaları Windows'ta açabilmek için winscp adlı program yardımıyla dosyaları uzaktaki makineden (remote) çalıştığınız makineye (local) taşımanız gerekmektedir. Winscp programının kurulumu için Ek-1'deki winscp hakkındaki bölüme bakınız.

> Binary format dosyaların ekrana yazdırılması sırasında çıkan karakterler terminalin işleyişini bozabilir. Bu tür durumlarda `reset` yazarak `enter` tuşuna basınız.

## tr komutu

İngilizce orijinal tarifi: "translate or delete characters"

Dosya içindeki veya girdideki karakterlerin başka karakterlere dönüştürülmesini sağlar. Diğer komutlar gibi **`tr <dosya.adı>`** şeklinde çalışmaz. Genellikle `cat` komutu ile birlikte işlev gösterir.

* **`cat <dosya.adı> | tr <değiştirilecek.karakterler> <hedef.karakterler>`** : Geçerli klasörde bulunan \<dosya.adı\> isimli dosyanın içinde bulunan değiştirilecek karakterlerin hedef karakterlere dönüştürülmesini sağlar.
* **`cat <dosya.adı> | tr -d "karakterler"`** : Geçerli klasörde bulunan \<dosya.adı\> isimli dosyanın içinde bulunan belirtilen karakterlerin silinmesini sağlar.

Boşluk, enter ve tab gibi özel karakterlerin de değiştirilmesi mümkündür. Boşluk için `""`, enter için `\n` ve tab için `\t` şeklinde ifadeler kullanılmalıdır.

<<[Şekil 2.16 tr komutunun kullanımı](code/tr-ornek.txt)

> "ABCDEFGHJKLMNOPRSTUVYZ" şeklindeki karakter listesi [A-Z] şeklinde yazılabilir. Ayrıca, tr komutunda [:alpha:] , [:alnum:] gibi belirli karakter dizilerinin kısa gösterimleri kullanılabilir. Listenin tamamı için tr komutunun kullanma talimatını okuyunuz.

>### Sorular
>* 'fark' kelimesinden 'pile' kelimesine kadar dört kademede olarak her kademede bir harf değiştirerek anlamlı kelimeler oluşturun. Örnek olarak kal kelimesinden sek kelimesine inmek şu şekilde gerçekleşir: kal - sal - sel - sek.
>* 'Yarın' kelimesini değiştirerek 'kadın' kelimesi olarak ekranda görüntüleyin.
>* AGTCAGCTACGACTACGACTACGACTAGCATCAA dizisinin ters eşleniğini (reverse complement) hesaplayınız.

## Kriptoloji ve Kriptoanaliz

Kriptoloji sayesinde herhangi bir mesaj belirli bir algoritma ile farklı bir hale dönüştürülüp güvenli olmayan kanaldan iletilebilir hale getirilmektedir. Bu tür dönüştürülmüş mesajlar üçüncü kişiler tarafından ele geçirilse çözümlenmesi gerekir (kriptoanaliz) ve kullanılan algoritmaya göre bu işlem basit veya çok zor olabilmektedir. 

Oldukça eski ve ilkel bir yöntem olan [Sezar şifresi](https://en.wikipedia.org/wiki/Caesar_cipher), her bir karakterin alfabetik olarak belirli ve sabit sayıda kaydırılması ile yapılmaktadır. Eğer, üç harf kaydırma kullanılacak olursa "Zebra" kelimesi "Cheud" şekline dönüşmektedir. [ROT13 adlı şifreleme](https://en.wikipedia.org/wiki/ROT13), Sezar şefrelemesinin özel bir hali olup her karakter alfabetik olarak 13 karakter ilerletilmektedir. ROT13 kullanıldığında "Zebra" kelimesi "Mroen" şeklinde yazılmaktadır. 




Info from Krypton Level 1 -> Level 2 and Krypton Level 2 -> Level 3

[Frequency Analysis](http://www.cryptool-online.org/index.php?option=com_content&view=article&id=96&Itemid=117&lang=en)

[N-Gram Analysis](http://www.cryptool-online.org/index.php?option=com_content&view=article&id=94&Itemid=112&lang=en)


## column komutu

İngilizce orijinal tarifi: "columnate lists"

Dosyaların veya girdinin ekranda sütunlar halinde düzenli görüntülenmesini sağlar.

* **`column <dosya.adı>`** : Geçerli dizin içinde bulunan \<dosya.adı\> isimli dosya içindeki sütunları tab ile birleştirerek aynı satırda görüntüler.
* **`column -t <dosya.adı>`** : Geçerli dizin içinde bulunan \<dosya.adı\> isimli dosyanın kolonlarının tab ile ayrıldığını kabul ederek düzenleme yapar.
* **`column -s 'ayıraç.türü' <dosya.adı>`** : Geçerli dizin içinde bulunan \<dosya.adı\> isimli dosyanın kolonlarının belirtilen ayıraç.türü ile ayrıldığını kabul ederek düzenleme yapar. Örneğin; **`column -s ','`** komutunda, virgül (,) ile ayrılmış kolonları düzenler. 

<<[Şekil 2.17 column komutunun kullanımı](code/column-ornek.txt)

>### Sorular
>* Movies ve ratings dosyalarını düzgün olarak ekranda görüntüleyin.

%%%% TODO: uzun satırlar wrap yapılıp satır numarası açılabilir.

## sort komutu

İngilizce orijinal tarifi: "sort lines of text files"

Geçerli dizinde bulunan bir dosyanın içeriğinin alfabetik olarak sıralanmasını sağlar.

* **`sort <dosya.adı>`** : Klasörde bulunan \<dosya.adı\> isimli dosyanın sıralanması sağlar.
* **`sort -r <dosya.adı>`** : Sıralamanın tersine çevrilmesi sağlar.
* **`sort -n <dosya.adı>`** : Sıralamanın sayısal değerlere göre yapılması sağlar.
* **`sort -k<kolon.numarası> <dosya.adı>`** : Sıralamanın belirlenen kolona göre yapılması sağlar.
* **`sort -u <dosya.adı>`** : Sıralamayı yaparken birden fazla olan modellerin bir kere gösterilmesini sağlar.


<<[Şekil 2.18 sort komutunun kullanımı](code/sort-ornek1.txt)

<<[Şekil 2.18 sort komutunun kullanımı (devamı)](code/sort-ornek2.txt)

> Kitaptaki örneklerde çıktının daha düzgün görünmesi için `column -t` komutu eklenmektedir. Çıktının düzeni önemli değilse `column -t` komutunun kullanılmasına gerek yoktur. 

<<[Şekil 2.19 seq ve sort komutlarının birlikte farklı kullanımları](code/seq-sort-ornek.txt)

%%%% TODO double sort example

>### Sorular
>* Sayı50 dosyasını alfabetik olarak sıralayın.
>* Sayı50 dosyasını sayısal olarak sıralayın ve ilk 15 tanesini ekranda görüntüleyin.
>* Sayı50 dosyasının alfabetik sıralamaya göre son 25 tanesi hariç ekranda görüntüleyin.
>* english_words adlı dosyadaki kelimeleri kafiye oluşturacak şekilde sıralayın.
>* emma ve oliver_twist kitaplarında en çok görünen 5 kelimeyi ayrı ayrı bulun.
>* emma ve oliver_twist kitaplarında en çok bulunan 150. kelimeleri bulun. 

%%%% TODO: kitap1 ve kitap2 emma_sayım ve oliver_twist_sayım dosyaları mı olacak? Yoksa emma ve oliver_twist kitapları şeklinde mi olacak? (şu an ikinci duruma göre ayarlandı)
