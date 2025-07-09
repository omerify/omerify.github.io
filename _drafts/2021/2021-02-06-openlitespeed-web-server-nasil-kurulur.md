---
title: OpenLiteSpeed web server nasıl kurulur?
date: 2021-02-06T19:38:26+03:00
author: omerify
layout: post
permalink: /2021/02/06/openlitespeed-web-server-nasil-kurulur/
categories:
  - Blog
tags:
  - openlitespeed
  - openlitespeed-kurulumu
  - server
  - server-kurulumu
  - sunucu
  - sunucu-kurulumu
  - vps
---

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/ekran-resmi-openlitespeed-web-server-anasayfa-web-gorunumu.JPG" /><figcaption><a href="https://openlitespeed.org/" target="_blank" rel="noreferrer noopener nofollow">openlitespeed.org</a></figcaption></figure>

Son yıllarda **Openlitespeed** web sunucusu <a href="https://openlitespeed.org/benchmarks/wp-http2/" target="_blank" rel="noreferrer noopener nofollow">benchmark</a> sonuçlarıyla wordpress severlerin yeni gözdesi haline geldi. Ucuz ve kısıtlı imkanlarla blogunu kendi VPS&#8217;lerinde sunmak için oldukça etkili. Ayrıca açık kaynaklı oluşuyla artan bir kullanıcı kitlesine sahip. Ben de bu blogu <a href="https://m.do.co/c/24f61f55683d" target="_blank" rel="noreferrer noopener">DigitalOcean</a> üzerinde **openlitespeed** kullanarak sizlere sunuyorum.

Başka bir proje için <a href="https://upcloud.com/signup/?promo=5P62V4" target="_blank" rel="noreferrer noopener">UpCloud</a> firmasında yeni bir site kurmam gerekti ve DigitalOcean&#8217;da otomatik gerçekleşen kurulumu kendim yapmak zorunda kaldım. Bu arada tecrübelerimi size aktararak kendi openlitespeed serverını kurmak isteyenlere de yardımcı kaynak oluşturmaya karar verdim.

Bu yazıda en basit haliyle **Ubuntu 20.04** üzerine **OpenLiteSpeed** sunucu kurulumunu anlatmaya çalışacağım.

**Kurulum Aşamaları:**

  1. _**Bir VPS satın alma**_
  2. _**Güvenlik duvarı (firewall) kurallarını yapılandırma**_
  3. _**OpenLiteSpeed ​​sunucusunu yükleme**_
  4. _**Yönetici paneli şifresini ayarlama**_
  5. _**Alan adını yapılandırma**_
  6. _**SSL sertifikasının alınması ve etkinleştirilmesi**_
  7. _**Yönetici paneli için HTTPS&#8217;yi etkinleştirme**_
  8. _**Siteniz için HTTPS&#8217;yi etkinleştirme**_

<hr />

**Önemli not:** Benim gibi amatörseniz her aşamayı sırasıyla takip edip, dikkatle okuyarak ve yazdığınız her şeyi iki defa kontrol ederek yapmanızda fayda var. Bu işlemleri uygulamak için temel Linux, terminal/komut bilgisi olursa işlemleri daha rahat uygulayabilirsiniz. Tüm aşamalar benim tarafımdan yapılmış ve resimleri eklenmiştir. Sorularınız için yorum bölümünü kullanabilirsiniz. Elimden gelen yardımı yapmaya çalışırım.

<hr />

#### 1- Herhangi bir firmadan VPS kiralayarak başlayabilirsiniz.

Daha önce yazdığım gibi hızı ve kalitesi nedeniyle sunucu kurulumu için <a href="https://upcloud.com/signup/?promo=5P62V4" target="_blank" rel="noreferrer noopener">UpCloud</a> firmasını kullanıyorum. Ama <a href="https://m.do.co/c/24f61f55683d" target="_blank" rel="noreferrer noopener">DigitalOcean</a> gibi birçok <a href="https://openlitespeed.org/#install" target="_blank" rel="noreferrer noopener nofollow">firma</a> bu işi bir tıkla yapmanızı sağlıyor. Eğer baştan gözünüz kesmiyorsa hiç başlamayın derim.

Sunucu kurulup ayağa kalktıktan sonra terminale aşağıdaki iki komutu yazarak tüm sistemi güncelleyin.

<pre><code>sudo apt update
sudo apt full-upgrade</code></pre>

Bu işlem sırasında yes/no diye soran her yere -y- harfini yazarak geçin. Sonra sistemi yeniden başlatın.

<pre><code>sudo reboot</code></pre>

<hr />

#### 2- Güvenlik duvarı (firewall) kurallarını yapılandırma:

OpenLiteSpeed, standart olmayan bağlantı noktaları kullanıyor. Bu yüzden yönetici paneline ve sunucunun varsayılan sayfasına erişebilmek için **8088** ve **7080** numaralı bağlantı noktalarına gelen trafik engeli kaldırmanız gerekiyor. Çünkü güvenlik gerekçesiyle portlar (bağlantı noktaları) Ubuntu&#8217;da kapalı olarak geliyor.

Ufw güvenlik duvarının aşağıdaki komutla kurulup kurulmadığını kontrol edin. Ubuntu&#8217;da genelde vardır ama kontrol etmekte fayda var.

<pre><code>sudo apt install ufw</code></pre>

Ardından aşağıdaki bağlantı noktalarına izin verin, diğer bağlantıları reddetmek için varsayılan kuralı ayarlayın ve güvenlik duvarını etkinleştirin.

<pre><code>sudo ufw allow 22,53,80,443,7080,8088/tcp
sudo ufw default reject
sudo ufw enable</code></pre>

Güvenlik duvarınızı gerekli bağlantı noktalarına ve hizmetlere izin verecek şekilde yapılandırdıktan sonra, OpenLiteSpeed&#8217;in yüklemesine devam edebilirsiniz. Bu arada aşağıdaki komutla firewall izinlerinin durumunu kontrol edebilirsiniz.

<pre><code>sudo ufw status</code></pre>

<hr />

#### 3- OpenLiteSpeed ​​sunucusunu yükleme

Sunucu kurulumu için OpenLiteSpeed tarafından bize verilen depoyu kullanarak işleme başlayabiliriz. Bunun için aşağıdaki komutu yazın.

<pre><code>wget -O - http://rpms.litespeedtech.com/debian/enable_lst_debian_repo.sh | sudo bash
sudo apt update</code></pre>

Depo eklendikten sonra, OpenLitespeed sunucusu aşağıdaki komutlar kullanılarak kurulabilir. OpenLiteSpeed&#8217;de PHP işleyicisi için en son sürümünü kullanacağım &#8211; lsphp74

<pre><code>sudo apt install openlitespeed lsphp74</code></pre>

OpenLiteSpeed ve bunun için bir PHP derleyici kurduk. Ancak yine de sunucumuza normal işlemler için hangi PHP&#8217;yi kullanılması gerektiğini bildirmemiz gerekiyor. Bunu yapmak için, az önce kurduğumuz PHP işleyicisine bağlantı oluşturmamız gerekiyor.

<pre><code>sudo ln -sf /usr/local/lsws/lsphp74/bin/lsphp /usr/local/lsws/fcgi-bin/lsphp5</code></pre>

Şu ana kadar yaptıklarımızla sunucunun hata vermeden kurulmuş olması lazım. Bundan sonra güvenlik için ince ayarlara başlayabiliriz.

<hr />

#### 4- Yönetici paneli şifresini ayarlama

Openlitespeed diğer sunucu kontrol yazılımları gibi bir admin paneline sahip. Bu panele ulaşmak için ise tabi ki kullanıcı adı ve şifre lazım. Kullanıcı adı ve şifreyi belirlemek için aşağıdaki komutu kullanın.

<pre><code>sudo /usr/local/lsws/admin/misc/admpass.sh</code></pre>

Kullanıcı adını ve şifrenizi (2 defa) girmeniz istenecek. Kendi istediğiniz username ve passwordu seçebilirsiniz. Eğer kullanıcı adı seçmezseniz default olarak &#8216;admin&#8217; olur.

Eğer aşağıdaki yazıyla karşılaşırsanız buraya kadar her şey tamam demektir.

<pre><code>Administrator's username/password is updated successfully!</code></pre>


<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-ols-openlitespeed-server-kurulum-1.JPG" /></figure>
  <caption>Buraya kadar olan kısmın terminal görüntüsü</caption>

Artık nihayet sunucunuza web üzerinden erişim sağlama vakti geldi. Admin paneline aşağıdaki gibi IP adresiniz ve sonuna &#8216;:8088&#8217; ekleyerek girebilirsiniz.

<pre><code>http:&#47;&#47;&lt;sunucu-ip-adresi&gt;:8088 </code></pre>

Adrese gittiğinizde karşınıza aşağıdaki gibi bir sayfa çıkması lazım.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-ekran-resmi-ols-openliteserver-hosgeldin-mesaji.JPG" /></figure>

Admin paneline gitmek için ise aşağıdaki adrese gitmeniz gerekiyor:

<pre><code>http:&#47;&#47;&lt;sunucu-ip-adresi&gt;:7080 </code></pre>

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-admin-giris-ekrani.JPG" /></figure>

Daha önce belirlediğiniz kullanıcı adı ve şifreyle giriş yaptıktan sonra karşınıza admin panelinin ana sayfası çıkacak.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-admin-ilk-giris-ekrani.JPG" /></figure>

Bu bölüme kadar her şey tamamsa bir sonraki bölüme geçebilirsiniz.

<hr />

#### 5- Alan adını yapılandırma

Buraya kadar yaptıklarımızla herhangi biri kendi alan adıyla sadece sizin IP adresinizi kullanarak sunucunuzu kullanabilir. Bizim yapmak isteğim şey ise kendi alan adımızı barındırmak. Bunun için bir kaç basit ayar var.

Sol kenar çubuğu menünüzdeki **_Listeners_**&#8216;e gidin ve ardından **_Actions_** altında **_View_** simgesini tıklayın.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-listeners-bolumu-1.JPG" /></figure>

Sonra karşınıza çıkan sayfada ön tanımlı _**Virtual Host Mapping**_ bölümünde yine **_Action_** yazan yerin altındaki **_Edit_** simgesine tıklayın.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-listeners-bolumu-2.JPG" /></figure>

Karşınıza çıkan sayfada **_Domains_** sekmesine kendi alan adınızı yazın. Diğer kısımlara dokunmayın. Ayrıca (?) olan yerlere tıklayarak açıklamaları okuyabilirsiniz.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-listeners-bolumu-5-2-domain-test.JPG" /></figure>

Alan adınızı yazdıktan sonra üstteki resimde okta gösterilen yerdeki **_Save_** simgesini tıklayın. Ve karşınıza **_Graceful Restart_** uyarısı çıkan bir mesaj çıkacak. Bunun için aşağıdaki görselde okla gösterilen yeşil butona tıklamanız yeterli.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-listeners-bolumu-6-domain-graceful-restart.JPG" /></figure>

Bu noktada OpenLiteSpeed ​​sunucusunu bir bulut sunucuya kurduk. Ancak site yine de 8088 numaralı bağlantı noktasını kullanıyor ve güvenli olmayan HTTP kullanıyor. SSL sertifikaları almak ve HTTPS&#8217;yi etkinleştirmek için bir sonraki bölüme geçebilirsiniz.

<hr />

#### 6- SSL sertifikasının alınması ve etkinleştirilmesi

SSL sertifikaları, web sitenizin Let&#8217;s Encrypt gibi bilinen güvenilir bir sertifika sağlayıcı tarafından doğrulanmasına olanak tanır. Certbot adlı kullanımı kolay bir istemci ile ücretsiz olarak almak mümkündür. Bir çok sitede zaten bu şekilde yapıyor.

Başlamadan önce hatırlatmakta fayda var. Alan adınızı sunucunuzun IP adresine yönlendirmiş olmanız gerekiyor. Alan adı kayıt kuruluşunuzda **A record**&#8216;u sunucunuzun IP adresi olarak değiştirerek bu adımı tamamlayabilirsiniz. Benim örneğimde; **test.omerify.com** -> **121.121.12311.211** gibi.

İlk olarak certbot&#8217;u sunucumuza kuruyoruz.

<pre><code>sudo apt install certbot</code></pre>

Ardından aşağıdaki komutu kullanarak sertifikaları alın. **<Alan-adınız>** kısmını OpenLiteSpeed ​​sunucunuzu işaret eden geçerli bir alan adıyla değiştirin.

<pre><code>sudo certbot certonly --standalone -d &lt;alan-adınız&gt;</code></pre>

Örnek:

<pre><code>sudo certbot certonly --standalone -d test.omerify.com</code></pre>

Girdiğiniz bu komut, sertifikayı ayarlamanıza yardımcı olacak birkaç soru sorarak etkileşimli bir yükleme komut dosyası başlatır. Sorulara uygun cevaplar yazmanız gerekecek. Ayrıca sertifika kurulumu için e-posta adresi vermeniz gerekiyor. Tarihi geçmeden önce yenilemek için falan uyarı gönderiyorlar.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-lets-encrypt-ssl-sertifika-alimi.JPG" /></figure>

Buraya kadar olan kısım tamamsa admin paneli için HTTPS sertifikasını etkinleştirmeye geçebiliriz.

<hr />

#### 7- Yönetici paneli için HTTPS&#8217;yi etkinleştirme

Kontrol panelinize giriş yapın. Sol menüdeki _**WebAdmin Settings**_ ardından **_Listeners_** sekmesini tıklayın. Ardından **_Actions_** yazısının altındaki **_View_** simgesini tıklayın.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-webadmin-ssl-aktif-yapma.JPG" /></figure>

Ardından, **Listeners** ayarlarında iken **SSL** sekmesine gidin ve ilk satırdaki _**SSL Private Key & Certificate**_ bölümünde sağda **_Edit_** simgesini tıklayın.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-webadmin-ssl-aktif-yapma-2.JPG" /></figure>

Let&#8217;s Encrypt&#8217;den aldığımız sertifikaları bu alanlara ekleyeceğiz. Bunun için aşağıdaki resimde olduğu gibi her satıra gelen sertifika yollarını doldurun.

  * Private Key File:&nbsp;  
    `/etc/letsencrypt/live/<alan-adınız>/privkey.pem`
  * Certificate File:&nbsp;  
    `/etc/letsencrypt/live/<alan-adınız>/fullchain.pem`
  * Chained Certificate:&nbsp;`Yes`
  * CA Certificate Path:&nbsp;  
    `/etc/letsencrypt/live/<alan-adınız>/fullchain.pem`
  * CA Certificate File:&nbsp;  
    `/etc/letsencrypt/live/<alan-adınız>/fullchain.pem`


<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-webadmin-ssl-aktif-yapma-3.JPG" /></figure>

Her şey ayarlandıktan sonra, sağdaki **_Save_** simgesine tıklayarak yeni ayarları kaydedin ve hemen üstteki yeşil düğmeyle _**Graceful Restart**_ yapın.

Daha sonra, yönetici panelini yeni bir tarayıcı sekmesinde açarak değişikliklerin başarıyla uygulandığını test edin.

<pre><code>https:&#47;&#47;&lt;alan-adınız&gt;:7080</code></pre>

Browser&#8217;da alan adınızın yanında kilit düğmesi sorunsuz çalışıyorsa her şey tamam demektir. Bir sonraki bölüme geçebilirsiniz.

<hr />

#### 8- Siteniz için HTTPS&#8217;yi etkinleştirme

Arka planda sunucu kurulumunu hallettik. Fakat son kullanıcı sitenize girmek için hala site adresinizin sonuna 8088 port numarasını eklemek zorunda. Sadece alan adınızı girerek sitenize ulaşılması için SSL için standart olan **443** portunun kullanılması gerekiyor.

Bunun içinde bir üsteki adımlara benzer ama farklı yerlerde küçük bir ayar daha yapmamız gerekir. Kontrol panelinizin sol kısmındaki **_Listeners_** sekmesini tıklayın.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-listeners-bolumu-1.JPG" /></figure>

Ardından çıkan pencerede **_Address Settings_** kısmındaki **_Edit_** simgesine tıklayın.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/openlitespeed-default-listener-general.jpg" /></figure>

Çıkan ayarları aşağıdaki gibi değiştirin

  * Port 8088&#8217;i 443 olarak değiştirin
  * Secure bölümünde Yes&#8217;i seçin

Ardından sağ taraftaki **_Save_** simgesine tıklayın ve yaptığını ayarları kaydedin. Sonra da yeşil kutuya tıkayın ve **_Graceful Restart_** yapın.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-listeners-web-ssl-aktif-yapma-1.JPG" /></figure>

Aynı sayfada SSL sekmesini seçin ve bir önceki adımda anlattığım gibi sertifika bilgilerini girin.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-webadmin-ssl-aktif-yapma-5.JPG" /></figure>

<ul>
  <li>
    Private Key File:&nbsp;<br /><code>/etc/letsencrypt/live/&lt;alan-adınız&gt;/privkey.pem</code>
  </li>
  <li>
    Certificate File:&nbsp;<br /><code>/etc/letsencrypt/live/&lt;alan-adınız&gt;/fullchain.pem</code>
  </li>
  <li>
    Chained Certificate:&nbsp;<code>Yes</code>
  </li>
  <li>
    CA Certificate Path:&nbsp;<br /><code>/etc/letsencrypt/live/&lt;alan-adınız&gt;/fullchain.pem</code>
  </li>
  <li>
    CA Certificate File:&nbsp;<br /><code>/etc/letsencrypt/live/&lt;alan-adınız&gt;/fullchain.pem</code>
  </li>
</ul>

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-webadmin-ssl-aktif-yapma-6.JPG" /></figure>

Üsteki sertifika bilgilerini doğru girdikten sonra sonra bir defa **_Graceful Restart_** atın. Eğer her şeyi doğru yaptıysanız alan adınızı adres satırına yazdığınızda aşağıdaki gibi bir sayfayla karşılamanız lazım.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-openlitespeed-server-kurulum-basarili.JPG" /></figure>

Artık web sitemizi OpenLiteSpeed kullanarak hazır hale getirdik.

Bilginiz olması açısından OpenLiteSpeed `/usr/local/lsws` dizini altında çalışır.

Kurulumla gelen örnek sitenin dizini `/usr/local/lsws/Example/html/`

Aynı sunucu altında bir çok sanal alan oluşturarak bir çok farklı siteyi barındırmanız mümkün. Ama kurulum için şimdilik bu kadar yeter. OpenLiteSpeed&#8217;i öğrendikçe sizlerle paylaşmaya devam edeceğim. Ve umuyorum ki en kısa zamanda, hazır hale gelmiş bu sunucuya manuel olarak WordPress kurmayı deneyeceğim. Takip etmeye devam edin.
