# Cloudflare Worker 2 V'siz ve Alt

Bu, Cloudflare Worker platformunu temel alan bir komut dosyasıdır. Orijinal sürüme dayalı olarak, VLESS yapılandırma bilgilerini görüntüleyecek ve abonelik içeriğine dönüştürecek şekilde değiştirildi. Bu betiği kullanarak VLESS yapılandırma bilgilerini çevrimiçi yapılandırmayı kullanarak Clash veya Singbox gibi araçlara kolayca dönüştürebilirsiniz.

-   Temel dağıtım video eğitimi:<https://www.youtube.com/watch?v=LeT4jQUh8ok>
-   Hızlı dağıtım video eğitimi:<https://www.youtube.com/watch?v=59THrmJhmAw>**_En iyi öneri!!!_**
-   Perspektifi kullanma konusunda ileri düzey eğitim:<https://www.youtube.com/watch?v=s91zjpw3-P8>

Telegram iletişim grubu:[@CMLiussss](https://t.me/CMLiussss)

# Sorumluluk reddi beyanı

Bu sorumluluk reddi beyanı GitHub'daki "edgetunnel" projesi (bundan sonra "proje" olarak anılacaktır) için geçerlidir, proje bağlantısı şöyledir:<https://github.com/cmliu/edgetunnel>

### kullanmak

Bu proje yalnızca öğrenme, araştırma ve güvenlik testi amacıyla tasarlanmış ve geliştirilmiştir. Güvenlik araştırmacılarına, akademisyenlere ve teknoloji meraklılarına ağ iletişim teknolojisini anlama ve uygulama konusunda bir araç sağlamayı amaçlamaktadır.

### yasallık

Kullanıcılar bu projeyi indirirken ve kullanırken yerel yasa ve düzenlemelere uymalıdır. Kullanıcılar, eylemlerinin kendi bölgelerindeki yasalara, düzenlemelere ve diğer geçerli gereksinimlere uygun olmasını sağlamaktan sorumludur.

### Sorumluluk reddi beyanı

1.  Bu projenin yazarı olarak ben (bundan sonra "Yazar" olarak anılacaktır), bu projenin yalnızca yasal, etik ve eğitim amaçlı kullanılması gerektiğini vurgularım.
2.  Yazar, bu projenin herhangi bir şekilde yasa dışı kullanımını teşvik etmez, desteklemez veya teşvik etmez. Bu projenin yasadışı veya etik olmayan faaliyetler için kullanıldığı tespit edilirse yazar bu tür davranışları şiddetle kınayacaktır.
3.  Yazar, bu projeyi kullanan herhangi bir kişi veya grubun gerçekleştirdiği yasa dışı faaliyetlerden sorumlu değildir. Bu projenin kullanımından doğacak her türlü sonuç kullanıcının kendisi tarafından karşılanacaktır.
4.  Bu projenin kullanımından doğabilecek doğrudan veya dolaylı hiçbir zarardan yazar sorumlu değildir.
5.  Kullanıcılar bu projeyi kullanarak bu sorumluluk reddi beyanının tüm şartlarını anladıklarını ve kabul ettiklerini belirtmiş olurlar. Kullanıcı bu şartları kabul etmiyorsa projeyi kullanmayı derhal bırakmalıdır.

Yazar, bu sorumluluk reddini herhangi bir zamanda önceden bildirimde bulunmaksızın güncelleme hakkını saklı tutar. Sorumluluk reddi beyanının en son sürümü projenin GitHub sayfasında yayınlanacaktır.

## risk uyarısı

-   Abonelik hizmetine yanlış düğüm yapılandırmaları göndererek düğüm yapılandırma bilgilerinin sızmasını önleyin.
-   Alternatif olarak, kendiniz dağıtmayı da seçebilirsiniz[WorkerVless2sub Abonelik Oluşturma Hizmeti](https://github.com/cmliu/WorkerVless2sub)Böylece abonelik oluşturucunun avantajlarından yararlanabilirsiniz.

## İşçi dağıtım yöntemi[Video öğretici](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=83s)

1.  Cloudflare Worker'ı dağıtın:
    -   Cloudflare Worker konsolunda yeni bir Worker oluşturun.
    -   İrade[işçi.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)İçeriği Worker düzenleyicisine yapıştırın.
    -   7\. satırı değiştir`userID`Kendinize göre değiştirin**UUID**。

2.  Abonelik içeriğine erişin:
    -   erişim`https://[YOUR-WORKERS-URL]/[UUID]`Abonelik içeriği mevcuttur.
    -   Örneğin`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`Bu sizin evrensel uyarlanabilir abonelik adresinizdir.
    -   Örneğin`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`Base64 abonelik formatı; PassWall, SSR+ vb. için uygundur.
    -   Örneğin`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`OpenClash vb. için uygun Clash abonelik formatı.
    -   Örneğin`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`singbox abonelik formatı, singbox vb. için uygundur.

3.  Çalışanlara özel bir alan adı bağlayın:
    -   İşçi konsolunda`触发器`sekme, aşağıya tıklayın`添加自定义域`。
    -   CloudFlare alan adı çözümleme hizmetine aktardığınız ikincil alan adını girin, örneğin:`vless.google.com`Tıkladıktan sonra`添加自定义域`, sertifikanın geçerli olmasını bekleyin.
    -   **Eğer acemiyseniz, daha fazla bakmanıza gerek kalmadan hemen şimdi yola çıkabilirsiniz! ! !**

<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>

4.  Kendininkini kullan`优选域名`/`优选IP`Şunun için abonelikler:
    -   Kendi tercih ettiğiniz alan adını veya kendi tercih ettiğiniz IP'yi kullanmak istiyorsanız, şu adrese başvurabilirsiniz:[WorkerVless2sub GitHub deposu](https://github.com/cmliu/WorkerVless2sub)içindeki dağıtım talimatlarına göre kendiniz oluşturun.
    -   Açık[işçi.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js) 文件，在第 12 行找到 `sub`değişkeni seçin ve konuşlandırılan abonelik oluşturucunuzun adresine göre değiştirin. Örneğin`let sub = 'sub.cmliussss.workers.dev';`, https gibi protokol bilgilerini ve simgeleri eklememeye dikkat edin.
    -   Kendi abonelik adresinizi kullanıyorsanız abonelik oluşturucuya sormayı unutmayın.`sub`alan adı ve`[YOUR-WORKER-URL]`Alan adı aynı üst düzey alan adına ait değil, aksi takdirde bir istisna oluşacaktır. Yapabilirsiniz`sub`Değişkene,workers.dev'e atanan alan adı atanır.

</details>

## Sayfa yükleme dağıtım yöntemi**En iyi öneri!!!**[Video öğretici](https://www.youtube.com/watch?v=59THrmJhmAw)

1.  Cloudflare Sayfalarını Dağıtın:
    -   indirmek[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)dosyanızı açın ve Yıldız'a tıklayın!!!
    -   Cloudflare Sayfaları konsolunda seçin`上传资产`Son olarak projenize bir isim verin ve tıklayın.`创建项目`ve ardından indirilenleri yükleyin[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)Dosyadan sonra tıklayın`部署站点`。
    -   Dağıtım tamamlandıktan sonra tıklayın`继续处理站点` 后，选择 `设置`>`环境变量`>**yapmak**Üretim için değişkenleri tanımlayın >`添加变量`.
        Değişken adını girin**UUID**değer UUID'nizdir, ardından tıklayın`保存`Bu kadar.
    -   geri dönmek`部署`sekmesinde sağ alt köşedeki simgesine tıklayın`创建新部署`Daha sonra yeniden yükleyin[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)Dosyadan sonra tıklayın`保存并部署`Bu kadar.

2.  Abonelik içeriğine erişin:
    -   erişim`https://[YOUR-PAGES-URL]/[YOUR-UUID]`Abonelik içeriği mevcuttur.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`Bu sizin evrensel uyarlanabilir abonelik adresinizdir.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`Base64 abonelik formatı; PassWall, SSR+ vb. için uygundur.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`OpenClash vb. için uygun Clash abonelik formatı.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`singbox abonelik formatı, singbox vb. için uygundur.

<details>
<summary><code><strong>「 我自己有域名！我要绑定自己的域名！我已经熟练的掌握域名解析！ 」</strong></code></summary>
   
3. 给 Pages绑定 CNAME自定义域：[视频教程](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
   - 在 Pages控制台的 `自定义域`选项卡，下方点击 `设置自定义域`。
   - 填入你的自定义次级域名，注意不要使用你的根域名，例如：
     您分配到的域名是 `fuck.cloudns.biz`，则添加自定义域填入 `lizi.fuck.cloudns.biz`即可；
   - 按照 Cloudflare 的要求将返回你的域名DNS服务商，添加 该自定义域 `lizi`的 CNAME记录 `edgetunnel.pages.dev` 后，点击 `激活域`即可。
   - **如果你是小白，那么你的 pages 绑定`自定义域`之后即可直接起飞，不用再往下看了！！！**
   - 
</details>
<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>
   
4. 使用自己的`优选域名`/`优选IP`的订阅内容：
   - 如果你想使用自己的优选域名或者是自己的优选IP，可以参考 [WorkerVless2sub GitHub 仓库](https://github.com/cmliu/WorkerVless2sub) 中的部署说明自行搭建。
   - 在 Pages控制台的 `设置`选项卡，选择 `环境变量`> `制作`> `编辑变量`> `添加变量`；
   - 变量名设置为`SUB`，对应的值为你部署的订阅生成器地址。例如 `sub.cmliussss.workers.dev`，后点击 **保存**。
   - 之后在 Pages控制台的 `部署`选项卡，选择 `所有部署`> `最新部署最右的 ...`> `重试部署`，即可。
   - 注意，如果您使用了自己的订阅地址，要求订阅生成器的 `SUB`域名 和 `[YOUR-PAGES-URL]`的域名 不同属一个顶级域名，否则会出现异常。您可以在 `SUB` 变量赋值为 Pages.dev 分配到的域名。

</details>

## Sayfalar GitHub dağıtım yöntemi[Video öğretici](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=560s)

1.  Cloudflare Sayfalarını Dağıtın:
    -   Bu projeyi Github'da çatallayın ve Yıldız'a tıklayın!!!
    -   Cloudflare Sayfaları konsolunda seçin`连接到 Git`Bundan sonra seçin`edgetunnel`Öğeden sonra tıklayın`开始设置`。
    -   var olmak`设置构建和部署`Sayfanın alt kısmında`环境变量（高级）`daha sonra birleştir`添加变量`Değişken adını girin**UUID**değer UUID'nizdir, ardından tıklayın`保存并部署`Bu kadar.

2.  Abonelik içeriğine erişin:
    -   erişim`https://[YOUR-PAGES-URL]/[YOUR-UUID]`Abonelik içeriği mevcuttur.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`Bu sizin evrensel uyarlanabilir abonelik adresinizdir.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`Base64 abonelik formatı; PassWall, SSR+ vb. için uygundur.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`OpenClash vb. için uygun Clash abonelik formatı.
    -   Örneğin`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`singbox abonelik formatı, singbox vb. için uygundur.

3.  CNAME özel alan adını Sayfalara bağlayın:[Video öğretici](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
    -   Sayfalar konsolunda`自定义域`sekme, aşağıya tıklayın`设置自定义域`。
    -   Özel ikincil alan adınızı girin, kök alan adınızı kullanmamaya dikkat edin, örneğin:
        Size atanan alan adı`fuck.cloudns.biz`, ardından doldurulacak özel bir alan ekleyin`lizi.fuck.cloudns.biz`Bu kadar;
    -   Cloudflare gereksinimlerine göre alan adı DNS servis sağlayıcınız iade edilecek ve özel alan adı eklenecektir.`lizi`CNAME kaydı`edgetunnel.pages.dev`Bundan sonra tıklayın`激活域`Bu kadar.
    -   **Eğer acemiyseniz, sayfalarınız bağlayıcıdır`自定义域`Bundan sonra doğrudan yola çıkabilirsiniz, daha fazla bakmanıza gerek yok! ! !**

<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>

4.  Kendininkini kullan`优选域名`/`优选IP`Şunun için abonelikler:
    -   Kendi tercih ettiğiniz alan adını veya kendi tercih ettiğiniz IP'yi kullanmak istiyorsanız, şu adrese başvurabilirsiniz:[WorkerVless2sub GitHub deposu](https://github.com/cmliu/WorkerVless2sub)içindeki dağıtım talimatlarına göre kendiniz oluşturun.
    -   Sayfalar konsolunda`设置`sekme, seç`环境变量`>`制作`>`编辑变量`>`添加变量`；
    -   Değişken adı şu şekilde ayarlandı:`SUB`karşılık gelen değer, dağıttığınız abonelik oluşturucunun adresidir. Örneğin`sub.cmliussss.workers.dev`, ardından tıklayın**kale**。
    -   Daha sonra Sayfalar konsolunda`部署`sekme, seç`所有部署`>`最新部署最右的 ...`>`重试部署`, bu kadar.
    -   Kendi abonelik adresinizi kullanıyorsanız abonelik oluşturucuya sormayı unutmayın.`SUB`alan adı ve`[YOUR-PAGES-URL]`Alan adı aynı üst düzey alan adına ait değil, aksi takdirde bir istisna oluşacaktır. Yapabilirsiniz`SUB`Değişkene Pages.dev'e atanan alan adı atanır.

</details>

### Değişken açıklaması

| değişken ismi    | Örnek                                                                                                                                                          | Açıklama                                                                                                                                                                           | YT                                                           |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| UUID             | 90SD4AH-141A-43SS-991B-08263SVISES10                                                                                                                           | Powershell -Çıkış Yok -Komut "[rehber]&#x3A;:YeniGuid()"                                                                                                                           | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=72s)   |
| PROXY IP         | proxyip.fxxk.dedyn.io                                                                                                                                          | CloudFlareCDN sitesine erişim için proxy düğümü olarak alternatif (ProxyIP'ler arasında kullanılan birden fazla ProxyIP'yi destekler)`,`veya aralık olarak satır besleme)          | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=166s)  |
| ÇORAP5           | kullanıcı:[password@127.0.0.1](mailto:password@127.0.0.1):1080                                                                                                 | CloudFlareCDN sitelerine erişim için SOCKS5 proxy'si olarak tercih edilir                                                                                                          | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=826s)  |
| ALT              | sub.cmliussss.workers.dev                                                                                                                                      | Yerleşik alan adı ve IP düğümü bilgileriyle birlikte abonelik oluşturucu adresi                                                                                                    | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1193s) |
| subapi           | api.v1.mk                                                                                                                                                      | Clash, singbox vb. abonelik dönüşümü arka ucu                                                                                                                                      | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1446s) |
| ALT YAPILANDIRMA | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/cmliu/ACL4SSR/main/Clash/config/ACL4SSR_Online_Full_MultiMode.ini) | Clash, singbox vb. Abonelik dönüşüm profilleri                                                                                                                                     | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1605s) |
| RPROXYIP         | YANLIŞ                                                                                                                                                         | Abone tarafından atanan ProxyIP'nin alınmasını zorlamak için true olarak ayarlayın (abone desteği gerektirir)                                                                      | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1816s) |
| 02               | <https://t.me/CMLiussss>                                                                                                                                       | Ana sayfa 302 atlaması (URL'ler arasında kullanılan birden fazla URL'yi destekler)`,`Veya satır sonunu aralayıcı olarak kullanın, eğer bu konuda yeniyseniz kullanmayın)           |                                                              |
| URL'si           | <https://t.me/CMLiussss>                                                                                                                                       | Ana sayfa gizleme (URL'ler arasında kullanılan birden fazla URL'yi destekler)`,`Veya aralıklı satır kesintileri, rastgele ayarlar dolandırıcılığı önlemeyi kolayca tetikleyebilir) |                                                              |

## Yıldız yıldızlar yükseliyor

[![Stargazers over time](https://starchart.cc/cmliu/edgetunnel.svg?variant=adaptive)](https://starchart.cc/cmliu/edgetunnel)

## Uyarlanmış uyarlanabilir abonelik içeriği

-   [v2rayN](https://github.com/2dust/v2rayN)
-   Clash.meta（[çatışma eşiğinde devrim](https://github.com/clash-verge-rev/clash-verge-rev)，[Nyanpasu'da çatışma](https://github.com/keiko233/clash-nyanpasu)，~[çatışma eşiği](https://github.com/zzzgydi/clash-verge/tree/main)~，ClashX Metası）
-   şarkı kutusu (SFI)

# minnettar

[zizifn](https://github.com/zizifn/edgetunnel)、[Sterilize edin ve yok edin](https://github.com/3Kmfi6HP/EDtunnel)、[Stanley-bebek](https://github.com/Stanley-baby)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config)、[Shegs1999](https://github.com/SHIJS1999/cloudflare-worker-vless-ip)
