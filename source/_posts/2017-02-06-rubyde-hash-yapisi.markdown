---
layout: post
title: "Ruby'de Hash Yapısı"
date: 2017-02-06 17:42:34 +0300
comments: true
categories: [Hash, Ruby, Anahtar, Programlama, Kod]
---

Hash, bir anahtar ve o anahtara ait değerden oluşan, sözlük benzeri bir yapıdır. Arraylere benzer ama arraylar integer ve onun indexinden oluşurken, hash yapısında istediğin tipi kullanabilirsin.
Yapısı şöyledir:
hash={"anahtar"=>"değer"}

Hash yapısı kolayca oluşturulabilir;
<!-- More -->
```rb
kelimeler={"hello"=>"merhaba","yes"=>"evet"} #(1)
kelimeler={hello:"merhaba", yes:"evet"}      #(2)
kelimeler={:hello=>"merhaba",:yes"evet"}     #(3)
```

Aynı yapı farklı syntax özellikleriyle yukarıdaki gibi yazılabilir.

Anahtardan değeri görüntülemek için;
```rb
kelimeler[hello]   #merhaba (1 ve 2 için)
kelimeler[:hello]  #merhaba (3 için)
```
Tüm anahtarları ya da değerleri görüntülemek için;
```rb
kelimeler.keys     #hello,yes
kelimeler.values   #merhaba,evet
```

Hash yapısını method olarak da oluşturabilirsiniz.
```rb
kelimeler=Hash.new
kelimeler["hello"]="merhaba  #metoda değer ekleme
```

Hashlere default değer verebilirsiniz.
Default değer vermezseniz, hash içinde bulunmayan değerler nil döndürür.
```rb
kelimeler=Hash.new(0)
```
ya da
```rb
kelimeler.default=0
```

### Hashlerle Kullanabiliceğimiz Metodlar
Tüm anahtar-değerleri silmek için;
```rb
h={a => "a", b =>"b"}
h.clear              #{}
```
Anahtar birden fazla değere sahip olabilir. Bu değerleri görüntülemek için dizi dönüren assoc metodu;
```rb
h={"renkler"=>["mavi","yeşil","mor"], harfler=>["a","b"]}
h.assoc("harfler")     #{"harfler",["a","b"]}
h.assoc("yok")         #nil
```
Hash'e parametre göndererek işleme sokabiliriz;
```rb
hash = Hash.new{|h,k|h[k]=k.to_i*2}
hash.default(10)  #20
```
Herhangi bir değeri silmek için;
```rb
h={"a" => 200, "b" =>100}
h.delete(a)
```
Koşullu olarak silmek için;
```rb
h={"a" => 200, "b" =>100}
h.delete_if{|key,value| value>150}    #{"b"=>100}
```

Hash içindekileri döngüde kullanmak için;
```rb
h={"a" => 200}
h.each{|key,value|puts "#{key} is #{value}"}  #a is 200
```
flatten metodu iç içe bulunan dizileri tek bir diziye dönüştürür;
```rb
a =  {1=> "one", 2 => [2,"two"], 3 => "three"}
a.flatten #[1, "one", 2, [2, "two"], 3, "three"]
```
