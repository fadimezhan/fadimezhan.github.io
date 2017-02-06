---
layout: post
title: "Octopress Komutları"
date: 2017-02-06 11:53:07 +0300
comments: true
categories: octopress
---

## Temada değişiklik yapmak için;
```ssh
- rake preview #komutuyla https://localhost:4000 sayfasında yapılan değişiklikler kontrol
edilebilir.Değişiklikler henüz görüntülenmemişse server yeniden açılmalıdır.
```

## Yapılan degişiklikleri web sayfasında yayınlamak için;
```ssh
- git add .
- git commit -m "message"
- git push origin source
- rake generate
- rake deploy
```

## Yazı yaınlamak için;
```sh
- rake new_post["title"]    // source/_posts
```
ya da;
```sh
- rake new_page[Web/page.html] // source/Web/page.html
```
```sh
- git add .
- git commit -m "message"
- git push origin source
- rake generate
- rake deploy
```