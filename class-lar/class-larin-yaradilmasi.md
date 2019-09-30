# Class-ların yaradılması

Nəyə görə class-ları işlədirik? Class-lar bizə data və funksiyaları məntiqi şəkildə qruplaşdırmağa imkan verir. Mən onları müvafiq olaraq attribute və method adlandıracağam. 

Method - class içində təyin etdiyimiz funksiyalar method adlanır.  
Attribute - classa aid olan dəyişənlər attribute adlanır  
Instance - class-dan törəyən object

Tutaq ki, şirkətdəki işçiləri əks etdirən bir tətbiq yazmalıyıq. Hər işçinin adı, emaili və görə bildiyi işlər var. Hər işçini ayrı ayrı kodlamaq həm kod sətiri həm də vaxt baxımından əziyyət olardı. Buna görə işçi adında bir qəlib yaradıb, hər işçini o qəlibə uyğun kodlamaq daha sərfəlidir. Bu halda hər bir işçinin öz methodu və attribute-u olacaq.

İşçi adında bir class yaratmaq üçün aşağıdaki kodu yazmaq kifayətdir.

```python
class Ishci:
    pass
```

{% hint style="info" %}
Python-dan istifadə edərkən, əgər boş bir class və ya funksiyadan istifadə edirsinizsə, içi boş qalmasın deyə `pass` sözünü istifadə edirik. Çünki içi boş class-lar error verirlər.
{% endhint %}

Instance nədir?

Yuxarıdaki misalda Işçi üçün class yaratmışdıq. Hər işçini bu qəlibə oturtduqca, işçi, qəlibin instance-ı olur. Daha texniki dildə desək

```python
class Ishci:
    pass

# Burada ishci_1 ve ishci_2 Ishci class-inin instance-lardir.
ishci_1 = Ishci() 
ishci_2 = Ishci()

print(ishci_1) # <__main__.ishci object at 0x1013775f8>
print(ishci_2) # <__main__.ishci object at 0x101377668>
```



Gördüyünüz kimi, hər instance-ın özünə aid yaddaşda yeri var və tipi object-dir. Python-da instance dəyişənləri və class dəyişənləri var.

`ishchi_1` də təyin etdiyimiz instance dəyişənləri heç vaxt `inshci_2`nin instance dəyişənləri ilə toqquşmur yaddaşdaki yeri fərqli olduğuna görə.

Gəlin `ishci_1` və `ishci_2` yə bəzi instance dəyişənləri təyin edək.

 

```text
class Ishci:
    pass
    
ishci_1 = Ishci()
ishci_2 = Ishci()

print(ishci_1) # <__main__.ishci object at 0x1013775f8>
print(ishci_2) # <__main__.ishci object at 0x101377668>

ishci_1.ad = 'Ali'
ishci_1.soyad = 'Mammadzada'
ishci_1.email = 'ali.mammadzada@email.com'
ishci_1.maas = 50000

ishci_2.ad = 'Serxan'
ishci_2.soyad = 'Ismayilov'
ishci_2.email = 'serxan.ismayilov@email.com'
ishci_2.maas = 60000

print(ishci_1) # ali@example.com
print(ishci_2) # serxan@example.com
```

İki işçinin informasiyasını əl vasitəsi ilə daxil etmək çətin və uzun olur, hər dəfə instance yaradılanda bu məlumatın avtomatik daxil olunmasını təmin etmək gözəl fikir olardı. Bunun üçün əsas class-ımızın içində `__init__` method-unu istifadə etməliyik.

Əgər əvvəlcədən başqa dil bilirdinizsə, sizə asan olması üçün `__init__`in bir constructor olduğunu deməliyəm. Əgər python sizin öyrəndiyiniz ilk dildirsə, `__init__` -i aşağıda izah etdiyim kimi anlaya bilərsiniz.

`__init__` initialize \(initial=ilkin\) sözünün qısaltmasıdır.   
Əgər bir classda `__init__` metodunu istifadə etsək, həmin classın bütün instance-ları `__init__` metodunun içindəki attribute-lara sahib olacaq.

`__init__` instace təyin edən zaman class-ın içində işə düşən ilk method-dur.

```python
class Ishci:
    def __init__(self, ad, soyad, maas):
        self.iad = ad
        self.isoyad = soyad
        self.imaas = maas
        self.iemail = ad + '.' + soyad + '@email.com'
    
ishci_1 = Ishci('Ali', 'Mammadzada', 50000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 60000)

print(ishci_1.iemail) # Ali.Mammadzada@email.com
print(ishci_2.iemail) # Serxan.Ismayilov@email.com
```

Gördüyünüz kimi 21 sətirlik bir koddan 9 sətirlik bir koda düşdük.

ad, soyad, maas və email bizim class-ımızın attribute-ları idi. Ancaq biz class-a həmçinin bəzi funksionallıqları da əlavə etmək istəyirik. Deməli class-a method yazacayıq. Tutaq ki, işçilərin ad və soyadlarını \(yəni fullname-i\) göstərən bir method-a ehtiyacımız var. Praktiki olaraq bunu çox sadə şəkildə bu cür həll edə bilərik:

```python
class Ishci:
    def __init__(self, ad, soyad, maas):
        self.iad = ad
        self.isoyad = soyad
        self.imaas = maas
        self.iemail = ad + '.' + soyad + '@email.com'
    
ishci_1 = Ishci('Ali', 'Mammadzada', 50000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 60000)

print('{} {}'.format(ishci_1.iad, ishci_1.isoyad) # Ali Mammadzada
print('{} {}'.format(ishci_1.iad, ishci_2.isoyad) # Serxan Ismayilov
```

Ancaq hər dəfə işçinin tam adı lazım olduqca yuxarıdaki kodun 11-12-ci sətirlərindəki kimi uzun kod yazmaq çətin olacaq. Bu problemi həll etmək üçün Ishci class-ının içində bir method yazmaq mümkündür. Ancaq `__init__` methodu əvvəl işləyib attribute-ları təyin etdiyi üçün, artıq yeni method-da ad, soyad, maas yazmaq lazım deyil.

{% hint style="info" %}
`iad` `isoyad` `imaas` `iemail` məsələsini anladığınıza görə, normal qaydada təyin edirəm.
{% endhint %}

```python
class Ishci:
    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.maas = maas
        self.email = ad + '.' + soyad + '@email.com'
        
    def tamAd(self):
        return '{} {}'.format(self.ad, self.soyad)
        
ishci_1 = Ishci('Ali', 'Mammadzada', 50000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 60000)

print(ishci_1.tamAd())
print(ishci_2.tamAd()) 
```

 8-ci sətiri belə fikirləşin 

```python
    def tamAd()
```

Əgər yuxarıdakı nümunədəki kimi siz `self`-i yazmadan instance yaratmağa çalışsanız, Həmin dəyəri print edərkən Python sizə TypeError verəcək:

`tamAd() takes 0 positional arguments but 1 was given`

Axı biz `tamAd()` method-unda nə `self` arqumentini nə də başqa bir argumenti təyin etməmişik? necə olur ki errorda deyir `1 was given`? 

Bu ona görədir ki, class-ın içində bir method yazığımızda, həmin method biz yazsaq da yazmasaq da avtomatik olaraq instance-ı ilk arqument kimi qəbul edir.  

Yəni `print(ishci_1.tamAd())` yazdığımızda, `ishci_1` dəyərini avtomatik olaraq `tamAd(ishci_1)` -a atır. Ona görə də `self` yazmaq mütləqdir.

Başqa bir deyişlə, `ishci_1.tamAd()` yazdığımızda, python yazdığımızı `Ishci.tamAd(ishci_1)` -ə çevirir. `ishci_1`-i isə `self`ə class-ın içindəki method-da self yazmadığımızda  Aşağıdaki erroru verir:`tamAd() takes 0 positional arguments but 1 was given`

{% hint style="info" %}
`self` class içindəki method içindəki bir  argument-dir, `self` bir keyword deyil. Siz başqa bir ad da istifadə edə bilərsiniz. Ancaq kodun oxunabilirliyini artırmaq məqsədi ilə `self` istifadə etmək məsləhət görülür. 
{% endhint %}

