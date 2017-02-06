---
layout: post
title: "Ruby On Rails"
date: 2017-02-06 16:53:45 +0300
comments: true
categories: [Ruby, Ruby on rails, model, controller, view, blog, web site]
---

Ruby on Rails, Ruby dilinde yazılmış, açık kaynak kodlu ve web uygulaması
geliştirmek için gereken tüm bileşenlere sahip frameworktür. İki tane felsefeyi esas alır;

 - **Don't repeat yourself(DRY):** Aynı işlemi yapan kodları tekrarlamayı
     en aza indirmeyi savunur. Örneğin partial işlemi ile belli bir işi yapan
    kod parçası farklı yerlerde kullanılabilir.
 - **Convention over configuration(COC):** Uygulama hazırlanırken sürekli yapılan rutin işleri, ruby on rails frameworkü tarafından daha kolay ve hızlı oluşturur.

Ruby on Rails MVC(Model,View,Controller) mimarisini kullanır.

 - **Model:** Veritabanı ile ilişkiyi sağlar.Tüm verileri bulundurur.
 - **Controller:** Kullanıcının isteklerine göre işlemleri yapar ve modelden gelen verileri işler.
 - **View:** Kullanıcının görüntüleyeceği arayüzü içerir.

Şimdi proje oluşturma işlemlerine bakalım:
<!-- More -->
```
$ rails new blog      //blog isimli proje oluşturur.
$ bundle install      //içindeki gemlleri yükler ya da günceller.
$ cd blod             //oluşturulan klasörün içine girer.
$ rails server        //serverı açar.
```

Son komutla http://localhost:3000 adresinde serverı açar ve sizi sabit welcome sayfası karşılar.

```
$rails generate controller welcome index
```
Burada welcome isminde controller ve index isminde action(olay) oluşturuyoruz.  **app/views/welcome/index.html.erb** sayfası içindeki kodlar kullanıcının görüntüleyeceği kodları içeriyor.Bu içeriği şöyle değiştirelim.

```
<h1>Hello,Rails</h1>
```

 localhostu açtığımızda hala aynı sayfa bizi karşılıyor. Bu yüzden **config/routes.rb** içinden  #root 'welcome#index' kısmının başındaki # işareti kaldırıp, tekrar localimizi açalım. Artık yazdığımız html sayfası görüntüleniyor.

Şimdiye kadar controller,action ve view oluşturmayı öğrendik.

Artık blogumuza biraz içerik katalım.Bunun için resource oluşturuyouz. Bununla oluşturma,yoketme, güncelleme,okuma gibi kısımlar ekleniyor.
**config/routes.rb** sayfasına kodumuzu ekleyelim.

```
get 'welcome/index'
resources :articles
root 'welcome#index'
```
http://localhost:3000/articles/new  sayfası oluşturuldu ama routing hatası veriyor. Controller oluşturulması gerekiyor.

```
$ bin/rails generate controller articles
```

Şimdide bilinmeyen action hatası veriyor. Bunun için **app/controllers/articles_controller.rb** sayfasına kodlarımızı ekleyelim.

```
class ArticlesController < ApplicationController
  def new
  end
end
```

**app/views/articles/new.html.erb** sayfasını oluşturup içine kodlarımızı yazalım.
```
<h1>New Article</h1>
```
Artık http://localhost:3000/articles/new adresinde görüntüleyebiliriz.
