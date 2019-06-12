---
layout: post
title:  "NoSQL nedir? Nasıl kullanılıyor?"
excerpt: Herkese merhaba! Bu yazımda NoSQL'in ne olduğunu, ne olmadığını, ne amaçlarla kullanılabildiğini ve nasıl çalıştığını anlatacağım.
date:   2012-07-21 00:25:46 +0300
categories: Teknoloji
image: /assets/nosql.jpg
---
![NoSQL](/assets/nosql.jpg)

Blogumu takip edenler Microsoft dışında bir yazı gördüğü için şaşıracak belki ama bu yeni ve güzel teknolojiyi sizlerin de görmesini isterim. :) Zaten yazıyı sonuna kadar okuyanlar NoSQL'in SQL Server'a ya da MySQL'e bir alternatif olmadığını, onların eksik kalan kısımlarını tamamladığını görebilir.

**NoSQL nedir?**

2010 yılı başlarında web'in değişimiyle birlikte ortaya çıkmaya başlamış NoSQL kavramı "Not only SQL" kısaltmasından adını alıyor. "Not only SQL" derken ne demek istediklerinden bahsetmekte fayda var. İlişkisel veritabanlarında verilerimizi tabloların altında yer alan sütunlarda satır satır saklıyoruz. Bunları diğer tablolarla ilişkilendirip tanımlamalarımızı yapıyoruz. NoSQL'de ise tablo yok, ilişki yok desek yeridir. Verilerimizi ise Json ya da XML formatında döküman olarak saklıyoruz. Bir kolon açma ihtiyacınız olduğunda ise json ya da xml'e yeni bir alan eklemek yeterli oluyor. ID mi? O da ne? ID kavramı NoSQL'de var olsa da bizim için ID diye bir şey yok diyebiliriz. Var olan ID ler veritabanının motorları için. Join? O da yok. Büyük sorgular mı? Karmaşık sorgular mı? Hayır, NoSQL'de hiçbiri yok.

**Ne zaman ihtiyaç duyacağız?**

Bu konuyu bir örnekle açıklamak istersek bir haber sitesini düşünelim. Onlarca kategori, yüzlerce alt kategori, onbinlerce haber, yüzbinlerce tag mevcut. Bu bilgilerin sürekli güncellendiğini ve yenilerinin eklendiğini düşünürsek bu veritabanını yönetmenin ne kadar güç olduğunu az çok tahmin edebilirsiniz. NoSQL ise bu durumda bize fayda sağlıyor. Kısaca üç unsuru mevcut: Hız, işlevsellik ve ölçeklendirilme (scalability).

**Fire And Forget Prensibi**

NoSQL veritabanları Fire & Forget prensibi ile çalışır. Bu nedenle işkritik uygulamalarda tercih **edilmemelidir**. Çünkü bunun için hiç uygun değildir. **NoSQL %100 doğru verinin önemli olmadığı durumlarda tercih edilmelidir**. Bunun sebebini kısaca açıklamak gerekirse NoSQL ram üzerinde çalışır. 10 sunucunuzun olduğu bir sistem düşünün. 1.server'da yaptığınız bir update işleminin tüm sunucularda aktif olmasının ne kadar süreceğini asla bilemezsiniz. Bir banka uygulamasında hız kadar tutarlılık ne kadar önemliyse bir haber sitesi için tüm sunucuların aynı anda güncellenmesi gereksinimi hız ile kıyaslandığında bir o kadar düşük kalmaktadır.

**Kimler kullanıyor?** 

Türkiye'den örnek vermek gerekirse sahibinden.com bu teknolojiyi ilk kullananlardan birisi. Az önce banka örneğini verdikten sonra aranızda bu teknolojiden çekinenler olabilir. Ancak NoSQL e-ticaret alanında dahi kullanılabilir. Uzaktan bakıldığında e-ticaret sitelerinde fiyat güncellemelerinin ne kadar sürede yapıldığı önemli gibi dursa da aslında büyük web sitelerinin tamamı cache yapısına sahip olduğundan hali hazırdaki sistemlerde de değişikliklerin tüm sunucularda aktif olması birkaç dakikayı bulabilmekte. Ancak kullanıcılar için bir user tablosu açmak yerine NoSQL kullanmak kayıt olunduktan sonra login olunamayacağı manasına gelebilir. Bu sebeple tek başına kullanmanızı tavsiye etmemekteyim. Çoğunlukla startup şirketlere maliyet ve hız konusunda avantaj sağlıyor gibi görünse de aslında NoSQL Facebook, Twitter, Foursquare gibi devler tarafından da kullanılıyor. Foursquare'de birçok kontrol yapılmasına rağmen nasıl bu kadar hızlı check-in oluyor ya da başka check-in leri görüntülemeyi nasıl bu kadar hızlı yapıyorsunuz sandınız? :) Twitter'a bakacak olursak yazdığınız bir tweet'i search ettiğinizde neden hemen göremediğinizi sandınız? :)

**MongoDB nedir? Niye MongoDB kullanayım?**

NoSQL için birçok alternatifiniz mevcut. NoSQL'e deliler gibi karşı olan Oracle'dan tutun da Google'a kadar. Ancak içlerinden en çok kullanılanı ve öğrenilmesi en kolay olanı MongoDB. MongoDB alışılması en kolay olan döküman odaklı veritabanı olarak bilinmekte. Özelliklerinden bahsetmek gerekirse aşağıdaki maddeleri yazabiliriz:

1.  Open Source
2.  Raw, schema, relation içermez
3.  Çok derin where içeren sorgularda sorun yaşatabilir
4.  Collection ile veriler gruplandırılabilir. Örneğin haberler adında bir collection'ın altında galeriler gibi bir haber grubu açılabilir.
5.  Sorgularda Regex kullanımı imkanı sunar
6.  Cloud mimariler için uygun bir yapısı mevcuttur

Birkaç sorgu gösterecek olursak şu örnekleri verebiliriz:

> db.news.remove() // news isimli collection'ı tamamen siler.
> 
> db.news.find({'post_date': '2012-07-21'}) // 21.07.2012 tarihinde yazılmış olan haberleri listeler. 
> 
> db.news.find({'post_date': '2012-07-21'}, {'is_active': true}) // 21.07.2012 tarihinde yazılmış olan aktif haberleri listeler.

**Scaling and Sharding**

Scaling konusunda da NoSQL yine öne çıkmakta. Bundan yıllar önce Google'ın kullanmaya başladığı mapping algoritmaları, Amazon Web Services, Heroku (Facebook), Google App Engine gibi düşük kalitedeki çok sayıda sunucuda çalışır. Bu sebeple NoSQL scalability konusunda öne çıkar. Sharding ise aynı verinin birçok lokasyonda bulunması anlamına geliyor. Fire & Forget'ten az önce bahsettik. Böylece read & write işlemleri daha sağlıklı çalışıyor.

**Durability Eleştirileri**

Şahsen bu eleştirilere cevap verecek olursam çoğunu anlamsız bulmaktayım. Az önce MangoDB'nin verileri ram'de sakladığından bahsetmiştik. Bu durum olası bir hatada (Örneğin MangoDB'nin bellekteki veriyi diske yazamadan sunucunun resetlenmesi gibi) veri kaybına yol açabilmektedir. Ancak amaç doğrultusunda bankacılık gibi kritik verilerin bulunduğu yerlerin değil içeriklerin önemli olduğu yerlerin kullanması gerektiğinden bahsediyoruz. Bir haber sitesindeki bir yazının yayınlanamaması kimsenin ölmesine ya da maddi zarara uygulamasına sebep olmayacaktır. Sırf bu sebepten MangoDB'yi çöpe atmak pek de mantıklı bir hamle olmayacaktır. Hele ki bu durumun önüne geçmek için onlarca çözüm varken.. En basit çözümden bahsedecek olursak kayıt ekranında bunun sunucudan check edilene kadar local olarak saklanması. MangoDB'nin önerdiği çözüm ise replication yapmak ve bu konuda haklılar. Kritik işlerinizi tek sunucuda hallediyorsanız hatayı MangoDB'de değil biraz da kendinizde aramalısınız. MangoDB değil de RDBMS kullanırken bilgiler diske yazılamadan sunucu yanarsa ne olacak? Canlı örneğini 9 Eylül 2009'da İstanbul'u sel bastığında Vodafone'da gördük. Datacenter'a dolan sular sunucuları sular altında bıraktı. Bu durumda RDBMS kullansanız ne olacak? 11 Eylül sonrasında kaç tane şirketin data kaybı yüzünden battığını/batmanın eşiğine geldiğini araştırmanızı tavsiye ederim. Belki de fiziksel bir sorun sebebiyle bilgiler diske yazılmış gibi görünüyor ancak yazılamıyor? Bu gibi durumlarda bir e-ticaret sitesinden bahsediyorsak alternatif çözümünüz tüm ürün bilgilerinizi, ürünlere yapılan yorum bilgilerinizi vb. MangoDB'de saklayıp; sipariş, sanal pos gibi bilgileri SQL'de saklamak olacaktır. Zaten adı üzerinde değil miydi: Not Only SQL :)

Son olarak Foursquare'in neden MangoDB kullandığını [http://nosql.mypopescu.com/post/6658269854/mongodb-at-foursquare-practical-data-storage](http://nosql.mypopescu.com/post/6658269854/mongodb-at-foursquare-practical-data-storage) adresinden inceleyebileceğinizi belirtip yazımı burada sonlandırıyorum.

Faydalı olması dileğiyle,
Mert