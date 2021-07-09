# Typo Fixer

Veri giriş operatörlerinin yazdığı İngilizce dilindeki metinleri kontrol ederek, bu metinler içindeki yazım
hatalarını bulan ve düzelten, ayrıca veri giriş operatörlerinin hatalı veri girme oranları ile yazım hatası bulma
algoritmasının başarı oranlarını da hesaplayarak raporlayabilen bir uygulama geliştirilmesi istenmektedir. 
Veri giriş operatörleri ve metinler ile ilgili bilgilerin dosyalardan (girdi01.txt gibi) alındığı varsayılmaktadır. 
İngilizce sözlük olarak, words.txt dosyası kullanılmaktadır.

Veri giriş operatörlerini temsil etmek için, DataEntryOperator isimli bir sınıf.
DataEntryOperator sınıfı; ilgili operatörün sicil numarasını tutan int tipinde ID, adı ve soyadını tutan String tipinde adSoyad ve operatörün çalıştığı birimi tutan String tipinde departman isimli değişkenlere sahiptir. DataEntryOperator sınıfı için; parametresiz “constructor” metot, tüm değişkenleri kullanan “constructor” metot ve “toString” metodlarını içermektedir.
Metinleri temsil etmek için Text isimli sınıf. Text sınıfı; metni yazan kişiyi temsil etmek için DataEntryOperator tipinde yazar, metin içeriğini tutmak için String tipinde content isimli değişkenlere sahiptir.

NOT: Metinlerin İngilizce dilinde olduğu varsayılmıştır.

    girdi01.txt dosyası içeriği:
    110,Ali Cetin,MuhendislikFakultesi
    Imagine a mechanical turtle that walks around the room under the
    control of a Java application. The turtle holds a pen in one of
    two positions, up or down. The default position is up.
    
    girdi02.txt dosyası içeriği:
    221,Ayse Demir,TipFakultesi
    PubMed comprises more than 28 million citations for biomedical
    literature from MEDLINE, life science journals, and online books.
    Citations may include links to full-text content from PubMed
    Central and publisher web sites.
Dosyanın ilk satırında, veri giriş operatörüne ilişkin bilgiler yer almaktadır. İkinci satırdan dosyanın
sonuna kadar ise bu kişinin yazdığı metin içeriği bulunmaktadır.
Uygulama, işlenecek girdi dosyalarını bunların isimlerini içeren bir meta dosyadan almaktadır.

    Örnek meta dosya içeriği:
    girdi01.txt
    girdi02.txt
    girdi03.txt
    girdi04.txt
    girdi05.txt
    
Her bir girdi dosyası okunurken, ilgili DataEntryOperator ve Text nesneleri oluşturulmuştur. 
Text nesneleri Text tipindeki tek boyutlu bir dizi içinde biriktirilmektedir.
Oluşturulan her Text nesnesinin içeriğinin (content) yazım hataları açısından incelenmesi ve içeriğin hataları giderecek şekilde güncellenmesi gerçekleştirilmektedir.
Sonuçların tutulması için kullanılmak üzere iki boyutlu bir dizi tanımlanmıştır. Bu dizinin bir boyutu metinler içindir ve bu boyuttaki indeksler ile Text tipindeki 
tek boyutlu dizinin ilgili nesnesinin indeksi uyumludur. İki boyutlu dizideki diğer boyut ise sırası ile ilgili metindeki toplam kelime sayısı, 
doğru yazılmış olan kelime sayısı, düzeltilen kelime sayısı, hatalı olup düzeltilememiş olan kelime sayısı, operatörün doğru yazım oranı 
(doğru kelime sayısı / toplam kelime sayısı) ile algoritmanın başarı oranı (düzeltilen kelime sayısı / (düzeltilen kelime sayısı + hatalı olup düzeltilememiş kelime sayısı)) 
bilgileri içindir. İşlem bittiğinde iki boyutlu dizi tüm metinlere ilişkin istenen hesaplanmış değerleri saklamış olacaktır.

    İki boyutlu dizi kullanılarak aşağıdaki işlemler gerçekleştirilmiştir:
    1) Tüm veri giriş operatörleri için okunan tüm metinlerdeki, toplam kelime sayısı, doğru yazılmış toplam kelime sayısı, düzeltilen toplam kelime sayısı yazdırılmaktadır.
    2) Mühendislik fakültesinde çalışan veri giriş operatörlerinin doğru yazım oranı ortalamasının yazdırılması, 
    Tıp fakültesinde çalışan veri giriş operatörlerinin hatalı yazım oranı ortalamasının yazdırılması gibi spesifik işlemler yapılmaktadır.
    3) Okunan tüm metinler için algoritmanın başarı oranı ortalaması yazdırılmaktadır.
