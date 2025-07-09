---
title: Raspberry Pi Öğreniyorum
date: 2021-01-24T13:53:47+03:00
author: omerify
layout: post
permalink: /2021/01/24/raspberry-pi-ogreniyorum/
categories:
  - Blog
tags:
  - bilgisayar
  - diy
  - kendin-yap
  - mikro-bilgisayar
  - raspberry
  - raspberry-pi
---

Eğer yeteri kadar azminiz, yazılım veya donanım konusunda bir şeyler üretmeye merakınız varsa, Raspberry Pi sizin için biçilmiş kaftan. Her yaştan ve meslekten insana hitap ediyor.

![](https://omerify.github.io/blog/assets/img/2021/01/raspberry-pi-RPi-Logo-Stacked-Reg-SCREEN.png)

Tüketim çılgınlığının verdiği huzursuzluk yüzünden amatör bir ruhla kendin yap (**DIY**) kültüründen nasiplenmek amacıyla yaklaşık iki sene önce çok isteyerek aldığım **Raspberry Pi 3 Model B** cihazını, ilk karşılaşmamızdan sonra tozlu raflara kaldırdım ve eski alışkanlıklar yüzünden de uzun bir süre yüzüne dahi bakamadım.

Geçen ay <a href="https://www.raspberrypi.org/" target="_blank" rel="noreferrer noopener nofollow">Raspberry Pi</a>nin logosunun olduğu kutu dikkatimi çekti ve kendisine bir daha masamda yer vermeye başladım. Boş zamanlarımda bu sefer öğreneceğimi kendime yüksek sesle telkin ederek tekrar hayatıma sokmaya karar verdim. Bu yazıyı ve (umarım) daha sonrakileri hazırlamamın nedeni de verdiğim bu karar. Çünkü öğrenmenin bir diğer yöntemi de öğretmek, paylaşımda bulunmak ve başkalarıyla tartışmak. Belki de en önemlisi bu bilgilerden benim gibi acemilerin ve beceriksizlerin de yararlanmasını sağlayacak Türkçe kaynak oluşturmak. Faydalı olmasını umarak.

Alışılmış dışına çıkarak eğer bir Raspberry Pi alacaksanız ve nelerle karşılaşacağınızı bilmiyorsanız, ilk önce bu uğraştan neden vazgeçmeniz gerektiğini anlatmak istiyorum. Çünkü bu maceraya atılacak kişilerin karşılaşacakları zorlukları bilmeleri gerekiyor. Aksi takdirde paranızı ve zamanınızı boşuna harcamış olacaksınız. Aşağıdaki maddelere rağmen hala gözünüz kesiyorsa bir dakika bile durmayın ve yapmanız gerekeni yapın.

**Not:** Burada bahsettiğim Linux masaüstü kullanım deneyimi Raspberry Pi üzerinde geçerlidir. Kendi PC&#8217;nize kurabileceğiniz kullanımı kolay ve oldukça akıcı **Ubuntu**, **MX Linux**, **Debian**, **Manjaro** gibi **GNU/Linux** dağıtımları mevcut ve bu yazıların konusu dışında.

### Raspberry Pi kullanmanın zorlukları:

**1-** **Raspberry Pi**&#8216;yi kullanmaya başladığınız zaman **klasik PC** kullanımda olan _hazıra konma, hız ve tüketim odaklı alışkanlıklarınızı unutmanız gerekiyor_. Çünkü cihazı alıp <a href="https://www.raspberrypi.org/software/" target="_blank" rel="noreferrer noopener nofollow">Raspberry Pi işletim sistemini</a> kurmak ve bu işletim sisteminden verim almak için az da olsa **komut satırı**, **linux** ve **programlama** bilginizin olması gerekiyor. Cihazı ilk defa çalıştırdığım zamanları hatırlıyorum. Bana 2000&#8217;li yılların başından beri uzak olan **MSDOS**&#8216;da format çekerken kullandığım terminal ekranını hatırlatması çok ekşi gelmişti. İsteğiniz programları yüklemek, işletim sistemini güncellemek, linux&#8217;dan faydalanmak için mimarisini keşfetmek ilk bir kaç saatten sonra oldukça yorucu geliyor.

**2-** Kullanmaya başladıktan sonra kendi tarayacısında (chromium kullanıyor) _internette içerik tüketmek, video izlemek, sayfalar arası gezinmek tam bir işkence halini alıyor_ ve &#8216;_**Neden kendime bunu yapıyorum?**_&#8216; diye soruyorsunuz. Zaten kısıtlı işlemci ve grafik gücü hali hazırda yararlandığınız bir çok program için oldukça yetersiz. Hele ki yüksek kaliteli içerikleri ve yüksek GB&#8217;lik dosyalar ise imkansız.

**3-** **Özgür yazılım, açık kaynak, geliştirme ortamları** vs. kulağa hoş gelse de oldukça emek isteyen şeyler. _İşinize yarayacak araçları bulmak benim gibi konuya uzak olanlar için oldukça çetrefilli bir süreç._ Bir keresinde bir program kurmak için bir kaç satır &#8216;**şey**&#8216; yazdım ve kuruldu (sanıyorum) ama programı çalıştırmayı bırakın nereye kurulduğunu bile bulamadım. İnternette içeriklerin hemen hemen hepsi İngilizce ve kullanmak için teknik dökümanları incelemek gerekiyor ve nedense her aşamada sorunlar çıkıyor. Sorunları çözmek için gereken her şey yine İngilizce. Bazı Türkçe dökümanlar ve videolar var ama oldukça yetersiz. Eğitim videolarındaki arkadaşlar mühendislik eğitimi veya bilgisayar eğitimi almış olacaklar ki, çok basit olarak geçtikleri şeyler sıradan bir kullanıcının algı sınırlarını aşabiliyor ve bir yerden sonra artık yeter deyip kapatabiliyorsunuz. Videolarda yaptıkları ilgi çekici şeyleri yapmaya çalışırken, size hiç bir anlam ifade etmeyen hata mesajları şevkinizi çabucak kırıyor.

**4-** Bir süre sonra Linux kullanmanın anahtarının PC&#8217;deki masaüstü görüntü arayüzünde olduğu gibi bir şeyleri tıklayıp keyfine bakmak olmadığını anlıyorsunuz. Linux&#8217;un kendi mimarisi içinde bir takım dosyalarda daha önce görmediğiniz şekillerde yazılmış kodlarla cebelleşmeniz gerekebiliyor. Ve yanınızda size yardım edebilecek biri yoksa ve mecbur değilseniz en son aşamada kutusuna koyup tozlu raflara hapsetmekten başka bir seçenek kalmıyor. Ve bir süre sonra anlıyorsunuz ki rafa kaldırdığınız şey avuç içinize sığan yeşil bir devre yığını değil, yaratıcılığınız olmuş. Bu yüzden süreç boyunca devam etmek için merakınızı ve azminizi diri tutmanız gerekecek.

<hr />

### Neden Raspberry Pi kullanmalıyım?

Tüm bu olumsuzluklara rağmen neden tekrar öğrenmeyi kafaya koyduğumu sorabilirsiniz. İşte bu noktada bir şeyler üretme iç güdüsü temel motivasyonum olarak öne çıkıyor. Kullandığım bu blogun barındırıldığı **sunucular, cep telefonları, modemler, routerlar, kameralar, TV&#8217;ler, web uygulamaları, hava gözlem istasyonları, astronomik ölçüm donanımları, eşyanın interneti cihazları, yapay zeka destekli donanımlar ve daha bir çok ürünün altında yatan teknoloji**den bahsediyorum. _Raspberry Pi_ de bunlara imkan veren altyapıyı kullanıyor ve kendi **istediğiniz şeyleri üretmek için çok uygun donanım, ekosistem ve topluluğa sahip.** Youtube&#8217;da Raspberry Pi ile yapılan şeyleri aramayı deneyebilirsiniz, karşınızı binlerce proje videosu çıkacak.

**Toparlamak gerekirse;** eğer yeteri kadar **azminiz, yazılım veya donanım konusunda bir şeyler üretmeye merakınız varsa**, _Raspberry Pi sizin için biçilmiş kaftan_. Her yaştan ve meslekten insana hitap ediyor. Burada Raspberry Pi&#8217;nin tarihçesini ve özelliklerini anlatacak değilim ama dileyenler <a href="https://tr.wikipedia.org/wiki/Raspberry_Pi" target="_blank" rel="noreferrer noopener nofollow">Wikipedi</a> sayfasından veya <a href="https://www.raspberrypi.org/about/" target="_blank" rel="noreferrer noopener nofollow">resmi sitesinden</a> bilgi alabilir.

<hr />

### Kullandığım donanımlar

  * <a href="https://www.raspberrypi.org/products/raspberry-pi-3-model-b/" target="_blank" rel="noreferrer noopener nofollow">Raspberry Pi Model 3 B</a>
  * <a href="https://www.raspberrypi.org/products/raspberry-pi-zero/" target="_blank" rel="noreferrer noopener nofollow">Raspberry Pi Zero</a>
  * <a href="https://www.raspberrypi.org/products/raspberry-pi-zero-w/" target="_blank" rel="noreferrer noopener nofollow">Raspberry Pi Zero W</a>
  * <a href="https://www.raspberrypi.org/products/sense-hat/" target="_blank" rel="noreferrer noopener nofollow">Sense Hat</a>
  * <a href="https://www.raspberrypi.org/products/camera-module-v2/" target="_blank" rel="noreferrer noopener nofollow">Camera Module V2</a>

Şu an için kullandığım donanımları bir fikir oluşturması açısından ekledim. Ayrıca daha sonraki yazılarda projeler için yine bu donanımları kullanarak bir şey yapmaya çalışacağım. Eğer siz ilk defa alıyorsanız ve bütçeniz el veriyorsa, çıkan en son versiyon Raspberry Pi&#8217;yi almanızı öneririm. 2018 yılında aldığımda fiyatlar oldukça makuldu fakat bu yazıyı hazırladığım günlerde &#8216;**şahlanan ekonominin**&#8216;de etkisiyle uçuşa geçmiş. Örnek vermek gerekirse **Sense HAT**&#8216;i ben aldığımda **150 TL** civarındaydı, 2021 Şubat&#8217;ta **350 TL** seviyesine kadar gelmiş.

Bu arada **Raspberry Pi&#8217;yi kullanmak için monitör, klavye, fare, sd kart ve 5V/2A&#8217;lik micro usb güç beslemesi** (en iyi performansı orjinal adaptörü veriyor.) gibi ekipmanlarınızın olması gerektiğini de hatırlatmakta fayda var. **Raspberry Pi Zero** alacaksanız, uygun micro USB, USB çoklayıcı ve mini HDMI adaptörlerini de aldığınızda emin olun. <a href="https://www.robotistan.com/" target="_blank" rel="noreferrer noopener nofollow">Robotistan</a> ve <a href="https://market.samm.com/" target="_blank" rel="noreferrer noopener nofollow">SAMM Market</a> (TR Resmi Raspberry Pi satıcısı) Türkiye&#8217;de en çok bilinenlerden ikisi.

**ssh** üzerinden kablosuz ve monitörsüz bağlanmak da mümkün ama başlangıçta evinizdeki bilgisayarın donanımlarından faydalanabilirsiniz.

Bu ilk yazı konu ile ilgili olarak önsöz niteliğinde ve temel bilgilendirme tadında oldu. Merak ettikleriniz için aşağıda yorum bölümü açık. Bundan sonrakiler için ise takipte kalmaya devam edin.
