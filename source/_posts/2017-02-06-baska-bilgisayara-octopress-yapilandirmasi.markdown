---
layout: post
title: "Baska Bilgisayara Octopress Yapılandırması"
date: 2017-02-06 17:21:15 +0300
comments: true
categories: 
---


Birden fazla bilgisayar kullananlar veya bilgisayarına format atanlar
için octopressi yeniden yapılandırmayı göstereceğim.


Octopress reposunda iki dal bulunur; master ve source. Source kısmı blog
yazılarımızı oluşturduğumuz dal, master kısmı ise tüm bloğu barındıran
daldır. Kurulum aşamasında master dalındaki dosyalar `_deploy` klasörü içinde oluşturulur. Alt çizgi içermesinin sebebi ise diğer dalları push ettiğinizde alt çizgi bulunan dosyaları çekmez. Böylece ``rake deploy`` komutunuzla master dalınız güncellenir.

<!-- More -->
öncelikle github sayfasından repomuzun url adresini kopyalıyoruz ve
 terminale geçiyoruz:

```sh
$ git clone -b source git@github.com:username/username.github.io.git octopress
```

Source dalımızdaki dosyaları bilgisayarımıza octopress klasörü içinde kopyaladı.Şimdi octopress dizinine geçip master dalımızdaki dosyaları _deploy dizini içine klonluyoruz:

```sh
$ cd octopress
$ git clone git@github.com:username/username.github.io.git _deploy
```


Şimdi dosyalarımızı yapılandırmak için gerekli komutları yazalım:

```sh
$ gem install bundler
$ rbenv rehash
$ bundle install
$ rake setup_github_pages
```

Son komuttan sonra url adresi isterse, github sayfasından kopyaladığımız repo url adresini yapıştırıyoruz.

Artık diğer bilgisayarınızdaki octopress bloğunuzun local kopyası oluştu. Eğer birden fazla bilgisayardan blog yazmak istiyorsanız pull-push işlemlerine dikkat etmeniz gerekecektir.

Blog yazınızı oluşturduğunuz bilgisayarda:

```sh
$ rake generate
$ git add .
$ git commit -am “Configuration for another computer.”
$ git push origin source  # source dalının (remote) güncellenmesi
$ rake deploy             # master dalının (remote) güncellenmesi
```

Daha sonra başka bilgisayarda son değişiklikleri bilgisayarınınza çekmeniz gerkecek:
```sh
$ cd octopress
$ git pull origin source  # source dalının (remote) güncellenmesi
$ cd ./_deploy
$ git pull origin master  # master dalının (remote) güncellenmesi
```

### Şimdi bloğumuza biraz içerik ekleyelim.

Yeni blog yazısı oluşturmak için ;
```sh
$ rake new_post[“title”]
```
blog yazıları ``source/_posts`` dizini altında depolanır.
 Yukarıdaki komutla jekyll isimlendirmesine göre, YYYY-MM-DD-post-title.markdown dosyası oluşturulur ve text editörde açtığınızda yaml frontmatter kod bloğunu görürsünüz. Bu kod bloğu sayfaların ve postların nasıl işleneceğini söyler.

Yeni sayfa oluşturmak için ;
```sh
$ rake new_page[super-awesome]  # /source/super-awesome/index.markdown  dosyası oluşturur.
```
ya da;

```sh
$ rake new_page[super-awesome/page.html]  # /source/super-awesome/page.html  dosyası oluşturur.
```

bazı komutlar ;

```sh
$ rake generate   # postları ve sayfaları public dizini içinde oluşturur.
$ rake watch      # değişiklikler için source/ ve sass/  dizinlerini izler
$ rake preview    # izler ve  http://localhost:4000  adresindeki web server’a bağlar
```

 Eğer postlarınızda yayınlamadan çalışmak istiyorsanız ``published: false`` kodunu yaml frontmatter kısmına ekleyin. Localhostunuzda ``rake preview`` komutuyla izleyebilirsiniz ama bu postunuz ``rake genereate`` yaptığınızda yayınlanmayacaktır.