---
title: 'Office 365 nedir? Nasıl geçilir? Fayda sağlar mı?'
layout: post
tags:
  - exchange
  - ' google'
  - ' google apps'
  - ' lync'
  - ' microsoft'
  - ' office 365'
  - ' office for mac'
category: Teknoloji
---
![Office 365](/assets/OFFICE365LOGOORANGE_PAGE.PNG)

Küçük işletmelerden kamu kuruluşlarına, eğitim kurumlarından kurumsal şirketlere kadar herkes için bulut altyapısı sağlayan Office 365 ile biz de şirket olarak yaklaşık 6 ay önce tanıştık. Orta Ölçekli İşletme lisansı ile kullanmaya başladığımız Office 365 geçtiğimiz 6 ay içerisinde bize birçok konuda tecrübe kazandırdı.

**Office 365’e nasıl geçilir?**

Eğer her şey sıfırdan başlıyorsa işiniz çok kolay. Office 365’in web sitesine girin, hesabınızı oluşturun, alan adınızın DNS kayıtlarını Office 365’e yönlendirin ve ödemeyi yaptıktan sonra kullanmaya başlayın!

Fakat var olan bir sistemi Office 365’e taşıyacaksanız işiniz biraz daha uzun sürecek. Office 365 öncesi Google üzerinden çalışan bir şirket olarak öncelikle Office 365 ve Exchange server yönetimini tanıyabilmek adına rhinorunner.onmicrosoft.com uzantılı bir domain ile demo hesabı açtık ve burada denemeler gerçekleştirdik. 1 haftalık test sürecinin ardından gerçek bir hesap açıp, kullanıcı sayımız kadar lisans aldıktan sonra kullanıcıların Office 365 hesaplarını oluşturduk. Bu aşamada DNS yönlendirmeleri yapılmadığı için buradaki e-posta adreslerine geçici olarak yine onmicrosoft.com uzantılı bir subdomain üzerinden erişim sağladık. Geçiş için günün en boş saati olarak geceyarısını seçtik ve beklemeye başladık. Gece 01:00 itibariyle önce DNS yönlendirmesini yapıp ardından **Exchange yönetim merkezi** üzerindeki geçiş bölümünden Google kullandığımız için **IMAP** protokolü ile Google üzerindeki tüm posta kutularının içeriklerini taşımaya başladık. **Fakat bu aşamada bir sorun var:** geçiş süresi sandığımızdan çok daha uzun sürdü. Google tarafındaki tüm posta kutularının toplam boyutunun 100 GB‘ı aşması ve Exchange’in **aynı anda en fazla 3 hesabı senkronize etmesi** sebebiyle gece 01:00’de başlattığımız taşıma işlemi tam 1 gün 15 saat 31 dakika sürdü.

Bu işlem devam ederken biz de Google tarafında kullandığımız dağıtım gruplarını oluşturmaya başladık. Maalesef ki öncesinde Exchange Server kullanmıyorsanız bu taşımaları elle yapmalı ve altlarındaki kullanıcıları tek tek elle tanımlamalısınız. Google tarafında oluşturulmasının çok kolay olduğu catch-all hesabının oluşturulmasının da bir hayli sıkıntılı olduğunu söylemeden geçmek istemiyorum.

Google’dan Office 365’e geçmek istememizin en önemli sebeplerinden birisi de Lync kullanmak istememizdi. Bu sebeple ofisteki tüm bilgisayarlarda var olan Office 2010’u kaldırıp Office 365 üzerinden edindiğimiz lisans ile Office 2013 yükledik ve Outlook ayarlarını yapılandırdık.

**Fakat bu aşamada bir sorun daha var: Apple!**

Şirketin bir ajans olduğu ve tüm dizayn ekibinin Mac kullandığı bir ofiste zaten bu tarafta bir sıkıntı yaşamayı bekliyorduk. Fakat sıkıntı beklediğimizden ağır oldu. Apple kullanıcılarının da mail server ayarlarını yaptıktan sonra ertesi sabah sesler yükselmeye başladı. Bu seslerin sebebi de Mac’in Mail yazılımının senkronizasyon yapısıydı. Office 365 taşıması sonrası sunucudaki tüm mailları yeniden download etmeye başlayan Mac Mail, başlattığı senkronizasyon işlemi kuyruktan kaybolana kadar yeni bir senkronizasyon isteğini işlemeye başlamadığı için gönderilen maillar outbox’ta, gelen maillar ise sunucuda beklemede kaldı. Senkronizasyon bitene kadar Apple kullanan kullanıcılarınızdan portal.microsoftonline.com üzerindeki Outlook Online’ı kullanmalarını rica ederseniz geçici bir çözüm elde edebilirsiniz.

**Active Directory**

Bu konu hakkında birçok araştırma yapıp birçok kişiye danıştık ve sonuç olarak iç sistemimizde yer alan Active Directory’i Office 365 ile **bağlamamaya** karar verdik. Bunun nedeni ise tamamen online bir sisteme geçmek isterken Active Directory’nin bunu baltalayabilecek olması. Bir sorun olması ve Office 365’in Active Directory sunucunuza internet üzerinden erişememesi halinde kullanıcılarınız hiçbir şekilde sisteme giriş yapamıyor. Bu da olası bir internet kesintisinde cep telefonlarımızdan bile mail atamayacağımız ve mail alamayacağımız anlamına geliyor.

**Yaşanan diğer sorunlar**

Bahsedeceğim bu sorunlar ise geçiş aşamasında değil, 6 aylık kullanım sürecinde ortaya çıkan sorunlar.

1. **Office for Mac 2011**: Geçişin ardından kısa bir süre geçtikten sonra fark ettik ki kullanıcıların büyük bir hevesle kullanmaya çalıştığı özelliklerin bazıları Mac kullanıcılarında çalışmıyordu. Bunun sebebi ise kullanmaya çalıştıkları özelliğin Office 2013’te yeni gelen bir özellik olması, fakat Office for Mac 2011 üzerinde bulunmuyor olması. Bu özelliklere örnek vermek gerekirse Lync üzerinden canlı sunum paylaşmak, ekran paylaşmak, canlı anket oluşturmak gibi özelliklerin Office for Mac 2011’de bulunmadığını söyleyebilirim.
2. **Bağlantı sorunları**: Uzaktaki bir sunucu üzerinden çalışan Lync, bazı konularda bizi hayal kırıklığına uğrattı. Sesli görüşmelerde çok sıkıntı yaşamasak da TeamViewer üzerinden sorunsuz gerçekleştirdiğimiz ekran paylaşma özelliğini Lync üzerinden yapmak istediğimizde 100 Mbps’lik bağlantıda dahi görüntüde donma sorunları yaşadık.
**Güncelleme**: Bu sorunlar Eylül ayı itibariyle azaldı, geçen hafta yapılan Office güncellemesi ile birlikte önemsenmeyecek bir düzeye geldi. Fakat kullanıcılarımız artık bu özelliğin sorunlu olduğu önyargısına sahip oldukları için kullanım oranı oldukça düşük.
3. **SharePoint Online 2013**: Daha önce bir server farm üzerinde çalışan SharePoint 2010 kullanan biri olarak onda dahi performans anlamındaki verimin çok iyi olmadığına inanan biriyim. Fakat SharePoint Online 2013’ün de bundan çok farklı olduğunu söylemem mümkün değil. Özellikle hız konusunda sınıfta kalıyor.
4. **SkyDrive Pro**: Kişisel SkyDrive’a alışan kullanıcılara SkyDrive Pro’nun nasıl işlediğini anlatmak biraz fazla zor oldu ve sonuç olarak ne mi oldu? Herkes kişisel SkyDrive ya da Dropbox hesabını kullanmaya başladı.

Bu kadar kötümser olduktan sonra iyi yönlerinden de bahsetmenin vakti geldi. Öncelikle fiyat olarak Google ile kıyasladığınızda daha pahalı olmasına karşın daha fazla özelliği **daha stabil** şekilde sunarak Office 365 ilk başarısını elde ediyor. Google ile sağlayamadığımız anlık mail akışını da Exchange’in Outlook, Windows Phone Mail ve iPhone’un native mail uygulamasındaki mail push özelliğiyle Office 365 sayesinde sağlamış olduk. Uzaktan erişim için online arayüzü kullanmak istediğimizde de klavye kısayollarından tutun Lync’e kadar Outlook’a benzeyen ve sorunsuz çalışan bir sistem bulduk karşımızda. Office Online tarafı da gerek Word gerek Excel gerekse PowerPoint tarafında Windows sürümünü aratmadı ve Google Docs’a göre çok üstün bir performans sergiledi. Fakat en önemli fark **sorun çıktığında karşımızda bir muhatap bulabiliyor olmaktı.**

Google tarafında yaşadığımız sorunları çözmek adına harcadığımız çabayı düşündüğümde içimden her ne olursa olsun Office 365’i seçmek geliyor. Yaşadığınız bir sorunun Office 365 tarafındaki çözüm süreci şu şekilde işliyor: Microsoft, öncelikle yardım ve topluluk sayfalarını araştırmanızı istese de Office 365 yönetim merkezi üzerinde **hizmet istekleri** adlı bir bölüm sunuyor. Çözemediğiniz, anlam veremediğiniz bir sorun yaşadığınızda burada açacağınız **Türkçe** Hizmet İsteği ile karşınızda bir muhatap bulabiliyorsunuz. Google tarafında bu süreç önce yardım kanallarına bakmak, eğer çözüm bulamıyorsanız Google’a İngilizce bir e-mail gönderip günlerce yanıt beklemek, sonunda da manasız bir cevap alıp yerinize oturmak şeklindeydi. Eğer bir Google Partner aracılığıyla Google Apps kullanıcısı olmuşsanız bu durumda o danışmanlık şirketine de ulaşabilirdiniz fakat çoğu senaryoda bu da ücretli bakım işlemleri ile sonuçlanmaktaydı. Aşağıya eklediğim screenshot üzerinde Office 365 üzerindeki hizmet isteği sayfasını ve sağ tarafta bulunan **yüz gülümsetici** uyarıyı görebilirsiniz.

![Office 365 Hizmet İsteği](/assets/OFFICE365_HIZMETISTEGI.JPG "Office 365 Hizmet İsteği")

Fakat burada önemli bir detay söz konusu, belirtilen destek hattı numarası **cep telefonları ile aranamıyor**. Türkiye için 00800 448 824 556 olan destek hattı numarasını cep telefonunuzdan aramak istediğinizde yanlış bir numara çevirdiğiniz uyarısını alıyorsunuz.

**Fakat merak etmeyin**, eğer bir hizmet isteği kaydı oluşturursanız **Microsoft Customer Support** ekibindeki Frontline Destek Mühendisleri sizi şaşırtacak kadar kısa bir süre içerisinde telefonla size dönüş yapıyor, bilgisayarınıza uzaktan bağlantı gerçekleştiriyor, telefonda Türkçe destek sağlayarak yardımcı olmaya çalışıyor, yeri geliyor saatlerce uğraşıyor ama sorununuz çözülmeden ortadan kaybolmuyorlar. Hatta bu yazıyı yazmama sebep olan durum da SRX1223896575ID numaralı kaydım için **Microsoft Frontline Destek Mühendisi Ümit Engin Yükselen**‘in bana yaptığı hızlı geri dönüş (20 dk) üzerine oldu. Geçtiğimiz 2 gün boyunca defalarca arayıp, defalarca e-mail üzerinden iletişime geçip, defalarca da uzaktan bağlantı gerçekleştirerek yaşadığımız 2 sorun için çözüm odaklı çalışarak bizlere yardımcı oldu. Kendisine ilgisi için bir teşekkürü borç bilirim.

**Sonuç olarak, Office 365 fayda sağlar mı?**

Eğer IT tarafında bir mail sunucusunun yükünü üzerinizde tutmak istemiyor, bunun en profesyönel şekilde yönetilmesini istiyorsanız, aynı zamanda stabil, hızlı ve çeşitlilik barındıran bir hizmet bekliyorsanız, **Office 365’i kesinlikle tavsiye ederim**. Her geçen gün hizmet kalitesinin daha da arttığını söylemekte fayda var. Fakat şu anki planlarınız sistemin detaylı değil ucuz olması yönünde ilerliyorsa bu durumda tavsiyem **Google Apps** olacaktır. Şunu da unutmamak gerekir ki bugün kullanacağınız Google Apps’ten ileride Office 365’e geçmek istemeniz halinde bu geçiş zorlu bir süreç oluşturacak. Bu yüzden daha düşük fiyatlı Office 365 paketlerini incelemekte de fayda var. Emin olun Office 365, ödediğiniz her kuruşun hakkını verecek bir performans sergiliyor. Özellikle de Google’da neredeyse hiç sahip olamayacağınız destek hizmetlerinde.