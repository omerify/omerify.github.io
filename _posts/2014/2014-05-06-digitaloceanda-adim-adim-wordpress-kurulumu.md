---
author: "Ömer Serdar Ören"
title: "DigitalOcean’da Adım Adım WordPress Kurulumu"
date: "2014-05-06"
categories:
  - "blog"
tags:
  - "digital-ocean"
  - "kurulum"
  - "vps"
  - "wordpress"
  - "nasil-yapilir"
  - "yazilar"
share-img: /assets/img/2014/05/ekran-resmi-digitalocean-ana-ekran.png
thumbnail-img: /assets/img/2014/05/ekran-resmi-digitalocean-ana-ekran.png
---

| **12.05.2016 Güncelleme:  ÖNEMLİ NOT** |
|:--:|
| Digitalocean’da kurulum oneclick application bölümünden kolayca yapılabilir. PHP 7 ye geçilmesi aşağıdaki bazı bölümleri geçersiz kılmaktadır. Boşu boşuna bütün yazıyı okumanıza gerek yok! Zamanım olmadığı için yazıyı güncelleyemedim, umarım en kısa zamanda başarabilirim. Güncel kaynaklara bakmanızı öneririm. |

---

![](/assets/img/2014/05/digitalocean-logo1.png)

Bu yazıyı da benim gibi acemiler için hazırladım. Çok karışık olmayacak şekilde Türkçe kaynak olmasını istedim.  
Fiyatları ile herkesin gözünü dolduran firma, eminim tüm meraklı gözlerin gözetimi altındadır. Dün elime geçen bir kupon sayesinde digital ocean firmasını deneme fırsatı buldum. 10$’lık da bir kredi yükledim ve bir süre idare edebilecek VPS hizmeti satın almış oldum. Ama bir sorun vardı! Daha önce hiç VPS kullanmamıştım. Yani kendi sunucumu kendim yönetmek zorunda kalmamış ve garip siyah ekranlı terminallere ‘command’lar yazmamıştım. Daha önce almış olduğum hosting hizmetlerini wordpress kurmak ve blogumu ayakta tutabilmek için satın almıştım. Her wordpress kullanan gibi yerli yabancı bir çok hosting firması kullanmak zorunda kalmıştım. Ne kadar zor olabilir ki diye düşünürken, kullanımının basitliğiyle övünen firmanın developer’lar için olduğunu, aldıktan sonra kavradım. Çünkü cpanel yok, ftp kullanıcı adı şifre, mysql adres yok, yok oğlu yok! Bende yarım yamalak İngilizcemle internette araştırmaya koyuldum ve bir kaç saatlik uğraştan sonra nihayet kurdum. ( Hoş, sonra sildim ama olsun☺ ) Bu fiyatlara bu özellikleri kaçıramazdım. Sizde benim gibi düşünüyorsanız buradan buyrun…

**Not:** <a href="https://m.do.co/c/24f61f55683d" target="_blank" rel="noreferrer noopener">https://m.do.co/c/24f61f55683d</a> referans linkine tıklayarak üye olursanız, 10$ hediye çekine **bedava** sahip olursunuz. Bu da iki aylık bedava hosting demek!

## Adım 1 — DigitalOcean’a kayıt

<a href="https://m.do.co/c/24f61f55683d" target="_blank" rel="noreferrer noopener">Buraya</a> tıklayarak digitalocean’a gidiyor ve üye oluyoruz. Üye olmak için **eposta** adresi ve **şifrenizi** girmeniz yeterli. Eposta adresine gelen onaylama linkine tıkladığınızda üyeliğiniz tamamlamış oluyorsunuz, bu kadar basit. Digital ocean hesabınıza girdiğinizde ise aşağıdaki gibi bir ekranla karşılaşıyorsunuz.

![](/assets/img/2014/05/ekran-resmi-digitalocean-ana-ekran.png)

Daha sonra buradaki ‘**Update Billing**’ bölümüne tıklayarak ödeme yönteminizi (Kredi kartı ya da Paypal) belirliyorsunuz. Ben 10$ ödeyerek başladım. Eğer acemiyseniz size de aynısını tavsiye ederim.

## Adım 2 — Droplet oluşturmak

Ödemenizi yaptıktan sonra hemen logonun altında ‘**create**’ butonuna tıklıyorsunuz ve aşağıdaki ekran sizi karşılıyor.

![](/assets/img/2014/05/ekran-resmi-digitalocean-droplet-olusturma.png)

**“deneme”** yazan yere boşluk olmayacak şekilde istediğinizi yazabilirsiniz. Örneğin: benimblogumcom  
**Select size:** Bu bölüm VPS’inizin genişliği ile alakalı. Başlangıç için aylık 5$ olan seçeneği işaretliyoruz.  
**Select Region:** Makinanızın nerede olacağını seçmeniz gerekiyor. Türkiye şartlarında en uygunu **Amsterdam**, **Frankfurt** ya da **London** olacaktır.

![](/assets/img/2014/05/ekran-resmi-digitalocean-droplet-olusturma-app-secimi.png)

**Select Image:** Sayfanın altında bulunan bu bölüme geldiğinizde “**Applications**” sekmesini tıklayın ve “_WordPress on 14.04_” yazan bölümü seçin. Son olarak en alttaki “**Create Droplet**” butonunu tıkladığınızda 2. adımda bitmiş olacaktır. Bu işlem sonucunda kayıt olduğunuz email adresine “_root_”, “_password_” ve “_IP adresi_” bilgilerini içeren bir eposta gelecektir.

## Adım 3 — Alan adını kurulum için kullanmak

Bu adımda bir alan adınızın olduğunu varsayıyorum. (Alan adı olmadan da yapmak mümkün) Kontrol panelizde sol tarafta bulunan “**DNS**” linkine tıklayın. Karşınıza gelecek ekranda daha önceden sahip olduğunuz alanadını girin, oluşturduğunuz droplet ismini seçin ve “**create domain**” butonuna tıklayın.

![](/assets/img/2014/05/ekran-resmi-digitalocean-dns-ayarlari.png)

Oluşturduğunuz droplet ismini seçerken sizin VPS’inizin IP adresini de gösterecektir. İşte bu IP adresini, domaini satın aldığınız firmadan, A records’ları olarak değiştirin. (Hem www hem de www’siz için A records’ları değiştirmeyi unutmayın) Unutmadan IP adresini size gönderilen epostada da bulabilirsiniz. (Size gönderilen IP adresi unique yani sadece sizin sitenize özel.) Ben A records falan bilmem diyorsanız. Name Server’larınızı (DNS) aşağıdaki gibi de yapabilirsiniz.

  1. ns1.digitalocean.com
  2. ns2.digitalocean.com
  3. ns2.digitalocean.com

Tarayıcı penceresinden alan adınıza girdiğinizde karşınıza şifre soran kutu çıkacaktır ve wordpress’in kurulumuna geçemeyeceksiniz. Bu nokta size gönderilen “root” olan kullanıcı adı ve “şifre” işe yaramaz. Alan adınız ve wordpress kurumunuzu şimdilik unutun ve diğer adıma geçin.

## Adım 4 — .htaccess şifresini almak

Sırada benim gibi kişilerin hiç aşina olmadığı bir durum söz konusu.

  * Kontrol paneli ana ekranda sol menüden “Droplet” seçeneğini seçin.
  * Oluşturduğunuz dropletin üstünü tıklayın.
  * Access butonuna tıklayın.
  * Hemen aşağıda mavi bir “console access” butonu olacak. Ona tıklayın.

Karşınıza aşağıdaki gibi bir ekran çıkacak. Login yazan yere “**root**” yazın ve “enter” layın. Sonra şifre soracak. Şifre bölümüne epostada gelen şifreyi yazın. Yazarken hiç bir yazı görünmeyecektir. Hata yok, siz yazmaya devam edin ve “Enter”a basın. (Eğer yazısız simsiyah bir ekran görürseniz, siyah bölümün üstüne fare ile tıklarken, klavyeden herhangi bir tuşa basın. Düzelecektir.)

![](/assets/img/2014/05/digitalocean-konsol-ekrani1.png)

Kullanıcı adı(root) ve şifrenizi doğru girerseniz ekranda çeşitli yazılar çıkacaktır. Daha sonra sizden email ile gönderilen root şifresini değiştirmeniz istenecek. İlk önce size gönderilen root şifresi ve daha sonra iki defa kendi belirleyeceğiniz karmaşık bir şifre girin. Daha sonra çıkan ekranda&nbsp;.htaccess satırının altında kullanıcı adı olarak “admin” ve bir “şifre” olacak. Bu şifreyi not edin.

## Adım 5 — Wordpress sitesini açmak

Şimdi tekrar alan adınızı yazarak websitenizi açın. Bu siyah ekrandan aldığınız kullanıcı adı yani **admin** ve **şifreyi** girerek bildiğimiz WordPress kurulumunuza başlayabilirsiniz. Kurulum gayet basit ve adımları devam ettirerek gerçekleştirebilirsiniz. Dolayısıyla anlatmaya gerek duymuyorum.

## Adım 6 — .htaccess şifresini silmek

Güvenlik nedeniyle **wordpress** ve **root** şifrenizden farklı olarak her çıkış yapıp tekrar girmeye çalıştığınızda bu şifre (.htaccess -siyah konsoldan aldığınız-) sorulacaktır. Bu özelliği kaldırmak için. FTP ile kendi server’ımıza ulaşmamız lazım. Bunun için ben Filezilla kullanıyorum. IP adresi ve şifrenizi girin diğer ayarların aşağıdaki resimde olduğu gibi olmasını sağlayın. Giriş yaptıktan sonra onaylamak için uyarı çıkacaktır. Kabul edin.

![](/assets/img/2014/05/digitalocean-filezilla-ftp-ayar1.png)

Gereken ayarı değiştirmek için aşağıdaki dosya yolunu takip edin. (Notepad++ gibi bir program yardımıyla açıp düzenleyebilirsiniz.)

<pre>/etc/apache2/apache2.conf</pre>

Dosyada aşağıdaki satırları bulun.

<pre>DirectoryMatch ^.*/wp-admin
    AuthType Basic
    AuthName "Please login to your droplet via SSH for login details."
    AuthUserFile /etc/apache2/.htpasswd
    Require valid-user
DirectoryMatch</pre>

ve o satırları başına # işareti ekleyerek etkisiz hale getirin.

<pre>#DirectoryMatch ^.*/wp-admin
#    AuthType Basic
#    AuthName "Please login to your droplet via SSH for login details."
#    AuthUserFile /etc/apache2/.htpasswd
#    Require valid-user
#DirectoryMatch</pre>

Ve artık defalarca girmeniz gereken şifreden kurtuldunuz.

**Not**: Bu şifre sadece **wp-admin** klasörünüze girerken sorulur. Ziyaretçilerinizin siteye erişimini engellemez. Güvenlik benim için önemli diyorsanız şifreyi kaldırmak zorunda değilsiniz.

## Adım 7 — Wordpress’i Türkçe yapmak ve Upload limiti arttırmak

Bu aşamaya kadar gelmişseniz bir kaç sorunla karşılaşacaksınız demektir. Kurduğunuz wordpress, otomatik kurulum nedeniyle İngilizce olarak kurulacaktır. Türkçeleştirmek için wordpress admin panelinde boşuna ayarları kurcalamayın.

**(WordPress’in yeni sürümünde kurarken dil seçimini zaten yapıyorsunuz. Kurulum zaten Türkçeyse bu bölümü atlayın.)**

Türkçeleştirmek için FTP yöntemi ile wordpress dosyarınıza ulaşmanız lazım. Bunun için FTP ile bağlandıktan sonra,

<pre>/var/www/</pre>

Dizini içinde wordpress kurulumunuzun dosyaları olur. Bu dizinin içindeki wp-config.php dosyasını alın ve aşağıdaki satırı bulun.

<pre>define('WPLANG', '');</pre>

Bu satırı aşağıdaki gibi değiştirin.

<pre>define('WPLANG', 'tr_TR');</pre>

WordPress admin panelinize geldiğinizde sizden dil ayarları için güncellemenizi isteyecek. Güncelleme işi bittikten sonra artık Türkçe olarak kullanabilirsiniz.

## Upload Limitini Arttırmak

Son olarak her şey tamam gibi gözüküyor ama veri tabanınızı yüklerken sorun çıkıyor. Hatta görsel ve diğer dosyalarınız yüklenmiyor. İşte bunun nedeni sistem kendiliğin 2 MB’lık dosya yükleme limiti ile geliyor. Bu ayarı değiştirmek için FTP ile bağlandıktan sonra aşağıdaki dosyayı bulup ufak bir ayar yapmanız gerekli.

<pre>/etc/php5/apache2/php.ini</pre>

yolunu takip ederek php.ini dosyasını bulun. Dosyayı Notepad++ gibi bir programla açın. Aşağıdaki satırları bulun ve istediğiniz limite getirin. (**Bu satırlar ayrı yerlerdedir.**)

<pre>upload_max_filesize = 64M</pre>
<pre>post_max_size = 64M</pre>
<pre>max_execution_time = 300</pre>

Burada örnek olarak 64 MB’a yükselttim. Siz isterseniz 500 MB’da yapabilirsiniz. Bu işlemi yaptıkran sonra, daha önce bahsettiğim siyah konsol ekranına gelin ve giriş yaptıktan sonra aşağıdaki satırları yazıp enter tuşuna basın.

<pre>sudo service apache2 restart</pre>

Ve artık dosya yükleme limitini değiştirdiniz.

Bu yazıya gösterilen ilgiden dolayı digitalocean VPS’leriniz için bakım ve güncelleme işlemlerinizi nasıl yapacağınız anlatacak ve yine basit bir dille anlatılmış bir yazı hazırlığına başladım. Umarım yararlı olur.

**ÖNEMLİ NOT: Tüm dosya değişikliklerinde dosyayı değiştirmeden önce bir kopyasını alırsanız, sorun olduğunda tekrar kolayca başa dönebileceğinizi unutmayın.**

Bu uzun yazıyı okuyup wordpress’i kurmuşsanız gerçekten tebrik ederim. Olabildiğince açıklayıcı ve kısa olmaya çalıştım. Benim gibi acemilere yardımcı olabilirsem ne mutlu bana…

**_Dediğim gibi bende acemiyim ama yardım edebileceğim bir konu olursa aşağıya yorum yorum yaparak sorularınızı ya da yaşadığınız problemleri yazabilirsiniz._**
