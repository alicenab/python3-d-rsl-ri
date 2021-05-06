# Class-ların yaradılması

Nəyə görə class-ları işlədirik? Class-lar bizə data və funksiyaları məntiqi şəkildə qruplaşdırmağa imkan verir. Mən onları müvafiq olaraq attribute və method adlandıracağam. 

Method - class içində təyin etdiyimiz funksiyalar method adlanır.  
Attribute - classa aid olan dəyişənlər attribute adlanır  
Instance - class-dan törəyən object

Tutaq ki, şirkətdəki işçiləri əks etdirən bir tətbiq yazmalıyıq. Hər işçinin adı, emaili və görə bildiyi işlər var. Hər işçini ayrı ayrı kodlamaq həm kod sətiri həm də vaxt baxımından əziyyət olardı. Buna görə işçi adında bir qəlib yaradıb, hər işçini o qəlibə uyğun kodlamaq daha sərfəlidir. Bu halda hər bir işçinin öz methodu və attribute-u olacaq.

İşçi adında bir class yaratmaq üçün aşağıdaki kodu yazmaq kifayətdir.

```python
class Employee:
    pass
```

{% hint style="info" %}
Python-dan istifadə edərkən, əgər boş bir class və ya funksiyadan istifadə edirsinizsə, içi boş qalmasın deyə `pass` sözünü istifadə edirik. Çünki içi boş class-lar error verirlər.
{% endhint %}

Instance nədir?

Yuxarıdaki misalda işçi üçün class yaratmışdıq. Hər işçini bu qəlibə oturtduqca, işçi, qəlibin instance-ı olur. Daha texniki dildə desək:

```python
class Employee:
    pass

# Burada emp_1 ve emp_2 Employee class-inin instance-lardir.
emp_1 = Employee() 
emp_2 = Employee()

print(emp_1) # <__main__.Employee object at 0x1013775f8>
print(emp_2) # <__main__.Employee object at 0x101377668>
```



Gördüyünüz kimi, hər instance-ın özünə aid yaddaşda yeri var və tipi object-dir. Python-da instance dəyişənləri və class dəyişənləri var.

`emp_1` də təyin etdiyimiz instance dəyişənləri heç vaxt `emp_2`nin instance dəyişənləri ilə toqquşmur yaddaşdaki yeri fərqli olduğuna görə.

Gəlin `emp_1` və `emp_2` yə bəzi instance dəyişənləri təyin edək.

 

```python
class Employee:
    pass
    
emp_1 = Employee()
emp_2 = Employee()

print(emp_1) # <__main__.Employee object at 0x1013775f8>
print(emp_2) # <__main__.Employee object at 0x101377668>

emp_1.first = 'Mammad'
emp_1.last = 'Mammadov'
emp_1.email = 'Mammad.Mammadov@email.com'
emp_1.pay = 50000

emp_2.first = 'Mammad2'
emp_2.last = 'Mammadov2'
emp_2.email = 'Mammad2.Mammadov2@email.com'
emp_2.pay = 60000

print(emp_1.email) # Mammad.Mammadov@email.com
print(emp_2.email) # sarkhan.ismayilov@email.com
```

İki işçinin informasiyasını əl vasitəsi ilə daxil etmək çətin və uzun olur, hər dəfə instance yaradılanda bu məlumatın avtomatik daxil olunmasını təmin etmək gözəl fikir olardı. Bunun üçün əsas class-ımızın içində `__init__` method-unu istifadə etməliyik.

Əgər əvvəlcədən başqa dil bilirdinizsə, sizə asan olması üçün `__init__`in bir constructor olduğunu deməliyəm. Əgər python sizin öyrəndiyiniz ilk dildirsə, `__init__` -i aşağıda izah etdiyim kimi anlaya bilərsiniz.

`__init__` initialize \(initial=ilkin\) sözünün qısaltmasıdır.   
Əgər bir classda `__init__` metodunu istifadə etsək, həmin classın bütün instance-ları `__init__` metodunun içindəki attribute-lara sahib olacaq.

`__init__` instace təyin edən zaman class-ın içində işə düşən ilk method-dur.

```python
class Employee:
    def __init__(self, first, last, pay):
        self.ifirst = first
        self.ilast = last
        self.ipay = pay
        self.iemail = first+ '.' + last + '@email.com'
    
emp_1 = Employee('Mammad', 'Mammadov', 50000)
emp_2 = Employee('Mammad2', 'Mammadov2', 60000)

print(emp_1.iemail) # Mammad.Mammadov@email.com
print(emp_2.iemail) # Mammad2.Mammadov2@email.com
```

Gördüyünüz kimi 21 sətirlik bir koddan 9 sətirlik bir koda düşdük.

ad, soyad, maas və email bizim class-ımızın attribute-ları idi. Ancaq biz class-a həmçinin bəzi funksionallıqları da əlavə etmək istəyirik. Deməli class-a method yazacayıq. Tutaq ki, işçilərin ad və soyadlarını \(yəni fullname-i\) göstərən bir method-a ehtiyacımız var. Praktiki olaraq bunu çox sadə şəkildə bu cür həll edə bilərik:

```python
class Employee:
    def __init__(self, first, last, pay):
        self.ifirst = first
        self.ilast = last
        self.ipay = pay
        self.iemail = first + '.' + last + '@email.com'
    
emp_1 = Employee('Mammad', 'Mammadov', 50000)
emp_2 = Employee('Mammad2', 'Mammadov2', 60000)

print('{} {}'.format(emp_1.ifirst, emp_1.ilast) # Mammad.Mammadov@email.com
print('{} {}'.format(emp_2.ifirst, emp_2.ilast) # Mammad2.Mammadov2@email.com
```

Ancaq hər dəfə işçinin tam adı lazım olduqca yuxarıdaki kodun 11-12-ci sətirlərindəki kimi uzun kod yazmaq çətin olacaq. Bu problemi həll etmək üçün Ishci class-ının içində bir method yazmaq mümkündür. Ancaq `__init__` methodu əvvəl işləyib attribute-ları təyin etdiyi üçün, artıq yeni method-da ad, soyad, maas yazmaq lazım deyil.

{% hint style="info" %}
`ifirst` `ilast` `ipay` `iemail` məsələsini anladığınıza görə, normal qaydada təyin edirəm.
{% endhint %}

```python
class Employee:
    def __init__(self, first, last, pay):
        self.ifirst = first
        self.ilast = last
        self.ipay = pay
        self.iemail = first + '.' + last + '@email.com'
        
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
        
emp_1 = Employee('Mammad', 'Mammadov', 50000)
emp_2 = Employee('Mammad2', 'Mammadov2', 60000)

print(emp_1.fullname()) # Mammad Mamamadov
print(emp_2.fullname()) # Mammad2 Mammadov2
```

 8-ci sətiri belə fikirləşin 

```python
    def fullname()
```

Əgər yuxarıdakı nümunədəki kimi siz `self`-i yazmadan instance yaratmağa çalışsanız, Həmin dəyəri print edərkən Python sizə TypeError verəcək:

`fullname() takes 0 positional arguments but 1 was given`

Axı biz `fullname()` method-unda nə `self` arqumentini nə də başqa bir argumenti təyin etməmişik? necə olur ki errorda deyir `1 was given`? 

Bu ona görədir ki, class-ın içində bir method yazığımızda, həmin method biz yazsaq da yazmasaq da avtomatik olaraq instance-ı ilk arqument kimi qəbul edir.  

Yəni `print(emp_1.fullname())` yazdığımızda, `emp_1` dəyərini avtomatik olaraq `fullname(emp_1)` -a atır. Ona görə də `self` yazmaq mütləqdir.

Başqa bir deyişlə, `emp_1.fullname()` yazdığımızda, python yazdığımızı `Employee.fullname(emp_1)` -ə çevirir. `emp_1`-i isə `self`ə class-ın içindəki method-da self yazmadığımızda  Aşağıdaki erroru verir:`fullname() takes 0 positional arguments but 1 was given`

{% hint style="info" %}
`self` class içindəki method içindəki bir  argument-dir, `self` bir keyword deyil. Siz başqa bir ad da istifadə edə bilərsiniz. Ancaq kodun oxunabilirliyini artırmaq məqsədi ilə `self` istifadə etmək məsləhət görülür. 
{% endhint %}

