---
title: Aylarca kendi sunucunuzda bedava VPN kullanmak
date: 2021-02-05T21:07:32+03:00
author: omerify
layout: post
permalink: /2021/02/05/bedava-vpn-kullanmak/
categories:
  - Blog
tags:
  - bedava-vpn
  - digitalocean
  - hosting
  - indirim-kodlari
  - internet-yasaklari
  - outline
  - outline-vpn
  - vpn
  - vpn-kurulumu
  - vps
---

Size özel IP adresine sahip sunucularda 5 dakikada VPN kurarak dünya çapında bir çok noktadan çıkış kapısı açabilir ve istediğiniz sitelere erişim sağlayabilirsiniz. Üstelik bu hizmete oldukça ucuz veya bedava sahip olabilirsiniz.

<figure><img src="https://omerify.github.io/blog/assets/img/2021/02/omerify-Ekran-Resmi-outline-vpn-server-masaustu.png"/></figure> 

Twitter&#8217;ın Soylu ve Bahçeli&#8217;ye engel koymasından sonra internet yasakları yeniden gündeme geldi. Ben de **VPN** _(özel sanal ağ)_ servislerine göz gezdirmeye başladım. Hazır VPN servislerinin IP adresleri belli olduğu için engellemesinin kolay olduğunu biliyoruz. Yani aylık bir miktar ödeyerek size verilen hizmete ulaşmanız bile kolaylıkla engellenebiliyor. Bunun tek çaresi ise _kendi sunucunuzdan yararlanarak bir VPN bağlantı sağlamak._ **Kendinize özel bu IP adresiyle dünya çapında bir çok noktadan çıkış kapısı açabilir ve istediğiniz sitelere erişim sağlayabilirsiniz.**

Aslında bu hizmetin amacı kurumsal firmalara ekstra bir güvenlik katmanı sağlamak olsa da günümüzde hükümetler işlerine gelmeyen siteleri engellemekten tereddüt etmiyor. Son kullanıcılarda bu seçeneği oldukça sıklıkla kullanıyor.

Gelelim işin bedava tarafına. Bir çok yabancı **VPS** _(özel sanal sunucu)_ hizmeti veren firma ilk üyelik esnasında oldukça cömert davranıyor ve başlangıç için 20 dolardan 100 dolara kadar bedava kullanım hakkı tanıyorlar. Bedava kredileri kullanmak için süre kısıtlamasının olduğunu hatırlatmakta fayda var ki bu süre genelde 2 ay civarı.

Eğer benim için aylık 5 dolar önemli değil diyorsanız sorun yok. Bedava krediniz bittikten sonra kullanmaya devam edersiniz. Diğer türlü düşünüyorsanız aşağıdaki linklerden bedava kullanım hakkınız bittikçe sırayla dileğinizi seçerek başka servislere geçer 5 dakikalık basit bir kurulumla kendi VPN hizmetinizi kullanmaya devam edebilirsiniz.

(VPN kurulumunu promosyon kodlarının altına ekledim.)

### Bedava VPS promosyon kodları

  * **DigitalOcean:** Benim favori hosting firmam **Digital Ocean**&#8216;ın aşağıdaki **promosyon kodu**yla bedava **100 dolar**lık krediyi 2 ay boyunca kullanmanıza olanak sağlıyor. Ayrıca VPN yazılımıyla bir kaç tuşa basarak kolayca kendi VPN serverınızı kullanabilmek mümkün. Kişisel tavsiyem digitalocean&#8217;ı kullanmanız yönünde.  
    <a href="https://m.do.co/c/24f61f55683d" target="_blank" rel="noreferrer noopener"><strong>https://m.do.co/c/24f61f55683d</strong></a>

  * **UpCloud:** Finlandiya merkezli firma en yüksek hızlı SSD&#8217;leri kullanmasıyla meşhur. Kayıtta 3 günlük **25 Dolar** bedava kredi veriyor. Ama hesabınıza 10 dolar yükleyerek toplamda 35 dolarlık bir krediniz oluyor ve bu da 7 ay boyunca VPN kullanımı demek. Aylık 1 dolardan biraz fazlaya VPN kullanabilirsiniz. İkinci tercihiniz bu firma olabilir. (Kendi VPN servisim için bu siteyi kullanıyorum.)
    <a href="https://upcloud.com/signup/?promo=5P62V4" target="_blank" rel="noreferrer noopener"><strong>https://upcloud.com/signup/?promo=5P62V4</strong></a>

  * **Vultr:** Bir başka çok bilinen hosting firması. 50 dolar bedava kredi veriyor fakat bunu kullanmak için (yanılmıyorsam) 10 dolar yükleme yapmanızı istiyor.  
    <a href="https://www.vultr.com/promo/try50/" target="_blank" rel="noreferrer noopener nofollow">https://www.vultr.com/promo/try50/</a>

  * **Linode:** Yılların eskitemediği firma Linode, 2 ay boyunca kullanmanız için 100 dolar veriyor.  
    <a href="https://promo.linode.com/lan/" target="_blank" rel="noreferrer noopener nofollow">https://promo.linode.com/lan/</a>

<hr />

### 5 dakikada Outline VPN kurulumu

Açık kaynak Outline VPN yazılımını indirmek için: <a href="https://getoutline.org/" target="_blank" rel="noreferrer noopener nofollow">https://getoutline.org/</a>

<iframe width="560" height="315" src="https://www.youtube.com/embed/wtIvjwzIoXo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**VPN kurulumu hakkında notlar:**

  * Gizli kalmanız suç işleyebilirsiniz anlamına gelmiyor. Gizlilik ve güvenlik bir haktır. Hakkınıza sahip çıkın diye VPN var.
  * VPN sunucu kurulumu 5 dakika aldığı için ben gerektiği zaman yeni sunucu kuruyor ve kullanmadığım zamanlar sunucuyu siliyorum. Çünkü yukarıdaki siteler sunuculardan aylık değil çalıştığı saat başı ücret alıyor. Yani haftada bir kaç saat kullanacaksanız tüm hafta sunucuyu ayakta tutmanız gerekmiyor. Bu da para ile hizmet alsanız bile ayda 1 dolardan daha az maliyet getiriyor.  
    Aylık 5 dolarlık bir VPS&#8217;in saatlik ücreti genelde 0.007 dolar. Ayda 30 saat çalışsa, size maliyeti 0.21 dolar. Çeyrek dolar bile değil. Hem de süper hızlı ve premium network bağlantıları var.
  * Bu arada her defasında tekrar mı sunucu kuracağım diye endişelenmeyin. Bir kaç defa yaptığınızda alışacaksınız ve ne kadar basit olduğunu göreceksiniz. Yazılım üzerinde zaten DigitalOcean kurulumu oldukça basit. Sunucuyu silerken dikkat etmeniz gereken nokta Outline yazılımı üzerinden değil, Hizmet aldığınız site üzerinde sunucuyu (delete, destroy vs.) silmeniz gerekiyor.
  * Eğer VPN bağlantınızın daha hızlı olmasını istiyorsanız Avrupa&#8217;daki lokasyonları seçmeniz mantıklı olacaktır. Mesafeden dolayı ABD merkezli sunucular Avrupa&#8217;ya kıyasla daha yavaştır.
  * VPN kurulumunu yaptıktan sonra kullanmanız gereken anahtarı (**key**) yabancılara vermeyin. İnternette kamuya açık bir şekilde paylaşmayın. Çok iyi tanıdığınız kişilerden başkasına vermeyin.
  * **Bir servisi kullanıp bedava hakkınızı tükettikten sonra diğerine üye olun.** Hepsine aynı anda üye olmayın. Çünkü bazı sitelerin üye olduktan sonra bedava kredilerin kullanım süresi var.
  * Bazı siteler sizden bedava kullanım için bir miktar (5 veya 10 dolar) yükleme yapmanızı isteyebilir. 50 dolar bedava kullanım için oldukça makul bir teklif. Kabul etmek sizin elinizde.
  * 5 dolarlık bir VPN server işinizi görecektir. Çoğu kullanıcı için daha pahalı olanları seçmenize gerek yok. Böylece bedava kullanım süreleriniz de artacaktır. Süre kısıtlaması olmadan 25 dolarlık bir krediyle 5 ay boyunca bedava VPN kullanmak mümkün.
