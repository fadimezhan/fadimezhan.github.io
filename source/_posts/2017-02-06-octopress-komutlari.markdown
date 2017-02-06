---
layout: post
title: "Octopress Komutları"
date: 2017-02-06 11:53:07 +0300
comments: true
sharing: true
categories: [Octopress, Blog, Post, Komut, Yayın]
published: true
footer: true
---

### Temada değişiklik yapmak için;
```sh ...
 rake preview #komutuyla https://localhost:4000 sayfasında yapılan değişiklikler kontrol edilebilir.Değişiklikler henüz görüntülenmemişse server yeniden açılmalıdır.
```

### Yapılan degişiklikleri web sayfasında yayınlamak için;
```sh ...
 git add .
 git commit -m "message"
 git push origin source
 rake generate
 rake deploy
```

### Post yayınlamak için;
```sh ...
 rake new_post["title"]    // source/_posts
```
ya da;
```sh ...
 rake new_page[Web/page.html] // source/Web/page.html
```
```sh ...
 git add .
 git commit -m "message"
 git push origin source
 rake generate
 rake deploy
```