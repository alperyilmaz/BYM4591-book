# Bash Döngüler

%%%% TODO terminal tiplerini, shell ve terminal konseptlerini anlatan bir ek kısım yapılabilir, orada da sh, bash, tcsh, zsh tarif edilebilir, aşağıdaki parantez içinde de atıf olmalı : 

%%%% TODO bu kaynak kullanılmalı: http://askubuntu.com/questions/506510/what-is-the-difference-between-terminal-console-shell-and-command-line

Bash terminalinde sadece `komut dosyaadı` şeklinde kullanım yoktur. Programlama dillerinde olduğu gibi oldukça karmaşık işlemler `if` , `for` veya `while` kullanarak mantıksal bir akış içinde gerçekleştirilebilir. Bu yüzden Bash için basit bir programa dili diyebiliriz.

Programlama dillerinde sıklıkla kullanılan döngüler (ing. loop) bir takım komutların veya işlemlerin belirli sayıda veya belirli bir koşul doğru oluncaya kadar tekrar edilmesi için kullanılır. Linux sistemlerinde kurulu olan terminal programları da (sh, bash, tcsh, zsh, vb.) döngü kullanabilmektedirler.

Kitapta kullanılan terminal bash temelli olduğu için bu bölümde bash döngüleri anlatılacaktır. Temel olarak `for` ve `while` döngüleri olmak üzere iki tür döngü tipi vardır. `for` döngülerinde belirli sayıda tekrar, `while` döngülerinde ise belirli bir koşul doğrulanana kadar tekrar olmaktadır. Eğer koşul hiç doğrulanmazsa sonsuz döngü oluşturmak da mümkündür. 

## for döngüsü

Bash tarafından kabul edilen iki tür `for` döngüsü vardır. Birincisi C programlama dili tarzında olan döngüler, ikincisi ise liste elemanları üzerinden giden döngülerdir. C dili tarzı for döngüsü aşağıdaki şekildedir:

    $ for ((IFADE1 ; IFADE2 ; IFADE3))
    do
    KOMUT1
    KOMUT2
    done

Birinci ifadede başlangıç koşulu, ikinci ifadede döngüye devam koşulu, üçüncü ifadede ise sayım koşulu bulunmaktadır. `do` ve `done` satırları arasındaki komutlar, ki birden fazla olabilir, istenen miktarda tekrar tekrar çalıştırılır. Örnek olarak 1'den 10'a kadar olan sayıları sırasıyla ekrana bastırmak için aşağıdaki şekilde bir `for` döngüsü çalıştırılabilir.

    $ for ((i=1 ; i<=10; i++))
    do
    echo $i
    done

Bu örnekte, i adlı bir değişken kullanılmış ve başlangıç olarak 1 değeri atanmış, değeri 10'dan küçük eşit oluncaya kadar döngü devam etmiş ve döngünün her tekrarında i'nin değeri bir arttırılmıştır. `i++` ifadesi `i=i+1` ifadesinin kısaltılmış halidir. Farkedildiği üzere, döngü içinde hem `i` hem de `$i` şeklinde ifadeler vardır. Atama, karşılaştırma işlemlerinde değişkenin adı sade şekilde kullanılırken, değişkenin içeriğine erişim istendiğinde $ işareti ile birlikte kullanılmaktadır. Bu Bash'e ait bir durumdur, diğer programa dillerinde değişkenler hep $ işareti ile veya hep sade olarak kullanılabilmektedir.

> Yukarıdaki örnek 4 satırdan oluşmaktadır ve terminal for döngüsünün başladığını, komutun sonlandırılmadığını bildiğinden, ilk satırın sonunda enter tuşuna basıldığında satırı çalıştırmayacak ve bir sonraki satıra geçecektir. Bu sefer $ işareti yerine satırın devam ettiğini gösteren > işareti olacaktır.

0'dan 10'a kadar çift sayıları ekranda görüntülemek için aşağıdaki döngü kullanılabilir:

    $ for ((index=0 ; index<=10; index=index+2))
    do
    echo $index çift sayıdır
    done

C tipi for döngülerinde birden fazla değişken kullanılabilmektedir:

    $ for ((index=0,j=1 ; index<=10; index=index+2,j++))
    do
    echo "$j"inci sayı : $index
    done

> Değişken adını çift tırnak içine almak karışıklıkları önlemek içindir. Yukarıdaki örnekte çift tırnak kullanılmasa `echo $jinci sayı` yazıldığında boş değerler ekrana basılacaktır çünkü `jinci` adında bir değişkenin değerine erişim sağlanmaya çalışılıyor sanılacaktır.

Yukarıda örnekleri verilen döngüler tek satırda da yazılabilmektedir. Tek satırda yazıldığında çubuk (|) karakteri ile çıktısı başka komutlara gönderilebilir.

    $ for ((i=1 ; i<=10; i++)); do echo $i; done
    
    $ for ((i=1 ; i<=10; i++)); do echo $i; done | wc -l

C tipi for döngülerine ek olarak liste şeklinde for döngüleri vardır, genel olarak çalışma şekli aşağıdaki gibidir:

    $ for DEGISKEN in LISTE
    do
    KOMUT1
    KOMUT2
    done

> Bash komutlarında değişken isimlerinde Türkçe karakter kullanımı hatalara neden olabilir

Bu tip döngüde, LISTE uzunluğu kadar döngü tekrar edecektir ve DEGISKEN'in değeri sırasıyla LISTE elemanları olacaktır. Liste elemanları aralarında boşluk bırakılarak yazılabilir. 1 ile 10 arasındaki sayıları liste şeklindeki döngü ile ekrana yazdırmak için aşağıdaki komut kullanılabilir (tek satır şekli de verilmiştir):

    $ for i in 1 2 3 4 5 6 7 8 9 10
    do 
    echo $i 
    done
    
    $ for i in 1 2 3 4 5 6 7 8 9 10; do echo $i; done

Liste rastgele sırada, istenen içerikte serbest olarak sağlanabilir. Sıralı bir liste olması halinde Bash tarafından sağlanan özel ifadeler ile, `{başlangıç..bitiş..adım}` gibi, listeler otomatik olarak oluşturulabilir:

    $ for i in {1..10}
    do 
    echo $i 
    done
    
    $ for i in {1..10}; do echo $i; done

Yukarıdaki örnekte 1 ile 10 arasındaki sayıları üretmek için özel Bash ifadesi kullanılmıştır. Aşağıdaki örneklerde aralık üretmek için kullanılan ifadenin farklı kullanımları özetlenmiştir.

<<[Şekil 3.1 Bash aralıklarının farklı kullanımları](code/bash-aralik.txt)

%%%% TODO 2. 3. 4. orneklerde sorun var

Liste tarzındaki for döngülerinde çok büyük bir üstünlük vardır. Liste, elle girilebilir, özel ifadeler ile otomatik olarak üretilebilir veya başka bir komutun çıktısından elde edilebilir. İstenildiği kadar karmaşık, çubuk karakteri ile (|) ile birbirine bağlanmış komutlar içeren bir ifadenin çıktısı liste olarak kullanılabilir. Komutun çıktısının liste olarak algılanması için özel tek tırnak işareti `` ` `` arasında veya `$( )` yapısı içinde olması gereklidir.

```bash
$ for DEGISKEN in `komut` 
do 
echo $DEGISKEN 
done

$ for DEGISKEN in `komut`; do echo $DEGISKEN; done
```

Veya 

```bash
$ for DEGISKEN in $(komut)
do 
echo $DEGISKEN 
done

$ for DEGISKEN in $(komut); do echo $DEGISKEN; done
```

Bu iki kullanımdan `$( )` formatı daha çok tavsiye edilen kullanımdır. Bunun en önemli sebebi de iç içe komut çıktılarının bağlanmasını mümkün kılmasıdır; `$( komut1 $(komut2) )`

> Özel tek tırnak işareti Türkçe klavyede Alt Gr ve , tuş kombinasyonu ile elde edilebilir.

Aşağıdaki örnekte, `ogrenci-not-donem1` dosyasının ilk sütunu `cut -f1` komutu ile elde edilmiş, ilk satır `sed 1d` ile silinmiş ve elde edilen öğrenci numarası listesi teker teker for döngüsü içinde `grep` komutu ile başka bir dosyada aratılmıştır.

<<[Şekil 3.2 for döngüsündeki listenin bir başka komutun çıktısından elde edilmesi](code/for-liste.txt)

Liste tarzındaki for döngülerinde dosya listesi oluşturmak da oldukça kolaydır. [Jokerler](#jokerler) kısmında anlatılan özellikler kullanılarak dosya listeleri oluşturulabilir. Örnek olarak, geçerli klasördeki bütün png dosyaları için bir döngü oluşturmak istendiğinde aşağıdaki ifade kullanılabilir.

    $ for dosya in *.png; do komut $dosya; done

%%%% TODO dosyayı çalıştırma, ./dosyaadı ve sh dosyaadı gibi formları anlatan, # ile comment yapılan dosya 

%%%% TODO for döngüleri için örnekler

## while döngüsü

Belirlenen bir koşul doğru olduğu sürece çalışan döngü tipidir. Temel olarak aşağıdaki şekilde kullanılmaktadır:

%%% türkçe karakterler kırmızı göründüğü için code fence kullanıldı

```bash
while [ koşul ]
do
komut1
komut2
done
```

`while` döngüleri de istenildiğinde tek satır halinde yazılabilir ve çalıştırılabilirler.

    $ while [ koşul ] ; do komut1; komut2; done


`for` döngüsünde olduğu gibi, `do` ve `done` arasındaki komut(lar) koşul doğru olduğu sürece çalıştırılır. Köşeli parantez ,`[ ]` , arasındaki ifadeler "koşul ifadeleri" (ing. conditional expressions) olarak adlandırılır ve sayı, yazı ve durum karşılaştırmaları için kullanılır. Koşul ifadeleri sadece `while` için değil, `if` ifadesi için de kullanılmaktadır. Koşul doğru ise döngü çalıştırılır, yanlış ise döngüden çıkılır. Aşağıdaki örnekte 1'den 5'e kadar olan sayılar ekrana yazdırılmaktadır. `sayac` adlı değişkene ilk değer atandıktan sonra döngü başlatılır, değerinin 5'ten küçük eşit olduğu kontrol edilir. Ayrıca döngü içinde `sayac` değişkeninin değeri artırılır.

    $ sayac=1
    $ while [ $sayac -le 5 ] 
    do   
    printf "Sayaç değeri: $sayac\n"
    ((sayac++)) 
    done

Koşul ifadeleri için [daha detaylı liste](http://www.gnu.org/software/bash/manual/html_node/Bash-Conditional-Expressions.html), mantıksal [VE](http://bash.cyberciti.biz/guide/Logical_AND), [VEYA](http://bash.cyberciti.biz/guide/Logical_OR) ve [DEĞİL](http://bash.cyberciti.biz/guide/Logical_Not_!) ile ilgili örnekler; [sayısal](http://bash.cyberciti.biz/guide/Numeric_comparison), [yazı](http://bash.cyberciti.biz/guide/String_comparison) ve [dosya/klasör özellikleri karşılaştırmaları](http://bash.cyberciti.biz/guide/File_attributes_comparisons) [örnekleri](http://bash.cyberciti.biz/guide/Conditional_expression) ilgili linklerde bulunabilir.

Aşağıdaki örnek ise döngü adımlarında sayaçtan eksiltme yaparak geriye doğru sayımı göstermektedir. 

    $ sayac=5
    $ while [ $sayac -gt 0 ] 
    do   
    printf "Sayaç değeri: $sayac\n"
    ((sayac--)) 
    done

`while` döngüsünün satır okuma özelliği sayesinde oldukça kullanışlı döngüler kurulabilir. Okunan satır istenen bir değişkene aktarılır ve döngü içinde değişken içeriği istenildiği gibi kullanılabilir:

```bash
while read SATIR
do
komut $SATIR
done
```

Satır okuma, var olan bir dosyadan veya başka bir komutun çıktısı üzerinden yapılabilir. Bu özelliğinden dolayı, satır okuma tarzında olan döngüler çubuk (|) ile karmaşık komut ifadeleri ile birleştirilip kullanılabilir.

    $ cat DOSYA | while read SATIR; do komut $SATIR; done

Bütün satır bütün olarak okunabileceği gibi, satır içerikleri parçalara ayrılıp da kullanılabilir. Aşağıdaki örnekte final notu 50'den yüksek öğrenciler seçilip final notuna göre sıralandırılmış, sadece öğrenci numarası ve harf notu sütunları seçilmiş ve her iki içerik de `while read` yapısı ile iki farklı değişkene atanmıştır. Döngü içinde de her iki değişkenin değeri ekrana istenen şekilde yazdırılmıştır.

<<[Şekil 3.3 while read yapısının çoklu komutlara dahil edilmesi](code/while-read.txt)

Döngüler bölümünün girişinde belirtildiği gibi Bash aslında bir programlama dili olarak da kullanılmaktadır. Programlamanın temeli sayılan `if .. then` kalıpları,`for` veya `while` döngüleri sayesinde oldukça uzun ve karmaşık komutlar gerekli koşullar sağlandığında çalıştırılabilir ve belirli koşullarda belirli işlemlerin yapılması sağlanabilir. Aşağıdaki örnekte `while` döngüsü ve `if` koşulu bir arada kullanılmıştır.

```bash
while [ koşul ]
do
 komut1      #Koşul doğru olduğu sürece iptal koşuluna kadar çalıştırılır
 komut2
 if (iptal-koşulu)
 then
  break      #while döngüsünden çıkılır
 fi
 komut3      #iptal koşulu yoksa çalıştırılır
done
```

%%%% TODO xargs should also be mentioned

%%%% TODO parallel should be mentioned as well

%%%% TODO bu bölüm sonuna döngü ile yapılabilen örnekler eklenmeli, bir websayfasından sırasıyla pdf indirmek gibi, pubmed id listesini kullanarak abstract extraction gibi. Ayrıca, bu bölüm sonuna veya başka bir bölime martin krzywinski'nin handoutundaki sql ve commandline karşılaştırılması (yıldız şeması) eklenmeli (muhtemelen sqllite konusunun sonuna) ayrıca CpG islands örneği de eklenmeli

%%%% TODO some links to use http://www.thegeekstuff.com/2011/07/bash-for-loop-examples/ and https://www.garron.me/en/articles/bash-for-loop-examples.html

%%%% TODO pubmed orneği: head pubmed_result.txt | while read PMID; do curl -s "http://www.ncbi.nlm.nih.gov/pubmed/"$PMID"?report=abstract&format=text" | egrep -v "^<.+>$"; sleep 1;done