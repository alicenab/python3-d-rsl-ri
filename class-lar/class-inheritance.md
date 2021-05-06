---
description: İrsilik
---

# Class Inheritance

## Inhertiance nədir?

İnheritance sözü Azərbaycan dilinə irsilik, törəmə kimi tərcümə olunur. 

İnheritance bizə `parent class`-dan method və `attribute`-ları irsi olaraq götürməyə imkan yaradır. Bu yolla biz `parent class`a heç bir zərər vermədən yeni `subclass`-lar yaradıb `subclass`-lara öz istədiyimiz funksionallıqları əlavə edə bilərik.

Aşağıdakı kod parçasına fikir verək, `Ishci` adında bir `class`-ımız var. `inheritance`-ı məşq etmək üçün developer-lər və manager-lər `sublcass`-ı yaratmaq məntiqli olardı. Çünki həm developer-lər həm də manager-lər işçilərdir və onların sistemdə ad,soyad, email və maaşının qeydə alınmağı məntiqli səslənir.

```python
class Ishci:
    artma_miqdari = 1.04

    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.email = ad + '.' + soyad + '@email.com'
        self.maas = maas
    
    def tamAd(self):
        return '{} {}'.format(self.ad, self.soyad)
    
    def maasi_artir(self):
        self.maas = int(self.maas + self.artma_miqdari)

ishci_1 = Ishci('Mammad', 'Mammadov', 50000)
ishci_2 = Ishci('Mammad2', 'Mammadov2', 60000)

print(ishci_1.email)
print(ishci_2.email)
```

Output:

> Mammad.Mammadov@email.com   
> Mammad2.Ishci@email.com

Yuxarıdakı kodun 16-cı sətrindən etibarən dəyişiklik etməyə başladım.

Pythonda subclass yaratmaq çox sadədir. Birinci normal qaydada `class` keyword-ündən istifadə edib ondan sonra class-ın adını qoymaq lazımdır. Bundan sonra isə mötərizə içində yeni yaranan classın hansı class-dan method və attribute-ları inherit etməsini istədiyimizi demək lazımdır \(bax: aşağıdakı kodda sətir 16 və 19\). Fikir verirsinizsə, sətir 17 və 20-də pass keyword-ünü işlətmişəm. 

{% hint style="info" %}
The `pass` statement is used as a placeholder for future code.  
When the `pass` statement is executed, nothing happens, but you avoid getting an error when empty code is not allowed.  
Empty code is not allowed in loops, function definitions, class definitions, or in if statements.
{% endhint %}

Ancaq burada mənim `pass` işlətməyimin səbəbi başqadır. Mən faktiki olaraq `Developer` və `Manager` subclass-ları içində nəsə yazmasam belə, 22 və 23-cü sətirlərdə onlardan istifadə etmişəm. Bəs hər iki kod necə eyni nəticəni verib?

Ona görə ki, `Developer` və `Manager` sub class-ları hər ikisi `Ishci` class-ının içindəki kodları özlərinə irsi olaraq götürüblər. Python kodu çalışdırıldığı zaman kod yuxarıdan aşağı oxunub gəlib çatır 22-ci sətirə. Görür ki `Developer` və `Manager` class-larından istifadə olunub. Baxır ki nə `Developer` class-ının içində nə də `Manager` class-ının içində `init` methodu yoxdur. Ona görə qalxır `Developer` və `Manager` class-larının parent classına yəni `Ishci` classına.  Buna termin olaraq   
"`method resolution order`" deyilir.



```python
class Ishci:
    artma_miqdari = 1.04

    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.email = ad + '.' + soyad + '@email.com'
        self.maas = maas
    
    def tamAd(self):
        return '{} {}'.format(self.ad, self.soyad)
    
    def maasi_artir(self):
        self.maas = int(self.maas * self.artma_miqdari)

class Developer(Ishci):
    pass

class Manager(Ishci):
    pass

proqramist_1 = Developer('Mammad', 'Mammadov', 50000)
menecer_1 = Manager('Mammad2', 'Mammadov2', 60000)

print(proqramist_1.email)
print(menecer_1.email)
```

Output:

> Mammad.Mammadov@email.com   
> Mammad2.Ishci@email.com

`Method resolution order`-i görməyin bir yolu da python-un `help` method-undan istifadə etməkdir. Əgər yuxarıdaki kodun sonunda bunu yazsaq:

```python
print(help(Developer))
```

Bu nəticəni alarıq:

```python
Help on class Developer in module __main__:

class Developer(Ishci)
 |  Developer(ad, soyad, maas)
 |  
 |  Method resolution order:
 |      Developer
 |      Ishci
 |      builtins.object
 |  
 |  Methods inherited from Ishci:
 |  
 |  __init__(self, ad, soyad, maas)
 |      Initialize self.  See help(type(self)) for accurate signature.
 |  
 |  maasi_artir(self)
 |  
 |  tamAd(self)
 |  
 |  ----------------------------------------------------------------------
 |  Data descriptors inherited from Ishci:
 |  
 |  __dict__
 |      dictionary for instance variables (if defined)
 |  
 |  __weakref__
 |      list of weak references to the object (if defined)
 |  
 |  ----------------------------------------------------------------------
 |  Data and other attributes inherited from Ishci:
 |
 |  artma_miqdari = 1.04
```

Yuxarıdaki output-un 6-cı sətrindən görə bilərsiniz ki, `Developer` subclass-ının Method resolution orderi necədir. İlkin olaraq lazım olan şey `Developer` subclass-ında axtarılır, bundan sonra `Ishci`-də axtarılır. Əgər onda da tapılmazsa, `builtins.object`-də axtarılır.

Siz həmçinin 11-ci sətirdən etibarən `Ishci` class-ından inherit olunan method-ları, 30-cu sətirdən etibarən isə inherit olunan data və digər attribute-ları görə bilərsiniz.

İndi isə gəlin baxaq ki, hər bir subclass-a necə öz method və attribute-larını əlavə edə bilərik. Əsas kodun 2-ci sətrindən görə biləcəyiniz kimi, `Ishci` classında `artma_miqdari` = 1.04 \(yəni 4 faiz\) təyin olunub.

```python
    artma_miqdari = 1.04
```

Maaş artımı üçün yazdığımız funksiya isə bucürdür:

```python
    def maasi_artir(self):
        self.maas = int(self.maas * self.artma_miqdari)
```

Nümunə kimi göstərəsi olsaq, görərik ki, 

```python
# Yuxarıdakı kodlar çox yer tutmasın deyə kəsilib.

proqramist_1 = Developer('Mammad', 'Mammadov', 50000)
menecer_1 = Manager('Mammad2', 'Mammadov2', 60000)

print(proqramist_1.maas)
proqramist_1.maasi_artir()
print(proqramist_1.maas)

# Output:
# 50000
# 52000
```

proqramist_1 -in maaşı 4 faiz artaraq 52000-ə yüksəldi. apply\_raise funksiyasında \(50000 \* 1.04  = 52000\)

Ancaq mən istəyirəm ki, `Manager` subclass-ının maaş artımı başqa, `Developer` subclass-ınınki isə başqa olsun. Bu halda nə etməliyəm? Bu halda hər bir class-da həmin adda istədiyimiz dəyərdə attribute yaratmaq lazımdır.



```python
# Yuxarıdakı kodlar çox yer tutmasın deyə kəsilib.

class Developer(Ishci): 
    artma_miqdari = 1.06 # Developer subclass-ının özünə məxsus maaş artımı faizi.

class Manager(Ishci):
    artma_miqdari = 1.10 # Manager subclass-ının özünə məxsus maaş artımı faizi.

proqramist_1 = Developer('Mammad', 'Mammadov', 50000)
menecer_1 = Manager('Mammad2', 'Mammadov2', 60000)

print(proqramist_1.maas) # Maaş artırmadan maaşları ekrana çap edirəm.
print(menecer_1.maas) # 

proqramist_1.maasi_artir() # Həm proqramist_1 həm menecer_1 maaşlarını qaldırıram. maasi_artir() methodu
menecer_1.maasi_artir() # vasitəsiylə.

print(proqramist_1.maas) # Həm proqramist_1 həm menecer_1 Maaş artımından sonrakı maaşlarını ekrana çap
print(menecer_1.maas) # edirəm.
```

Output:

> 50000  
> 60000  
> 53000  
> 66000

## Subclass-a parent class-da olmayan methodların verilməsi

Fərz edək ki, bizə lazımdır ki, hər bir developer-i yaradarkən onun adı, soyadı, maaşından əlavə həmçinin onun əsas istifadə etdiyi proqramlaşdırma dilini də təyin edək.

```python
proqramist_1 = Developer('Mammad', 'Mammadov', 50000)
```

Ancaq bu hal-hazırki kodda mümkün deyil çünki bundan qabaq `print(help(Developer))` yazaraq `Developer` subclass-ının 3 arqument götürdüyünü görmüşdük. 

```python
Help on class Developer in module __main__:

class Developer(Ishci)
 |  Developer(ad, soyad, maas)
 
 # Çox yer tutmaması üçün redaktə olunub.
```

Həmin 3 arqument isə `Ishci` parent class-ından törəyən arqumentlər idi. Hansı ki, kodun bu hissəsində qeyd olunub. 

```python
    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.email = ad + '.' + soyad + '@email.com'
        self.maas = maas
```

Əgər biz `Developer` subclass-ı üçün ayrıca developerin istifadə etdiyi proqramlaşdırma dilini də daxil etmək istəyiriksə, bunun üçün kodda bucür dəyişiklik etmək lazım gələcək. Biz yuxarıda göstərdiyim kodun hamısını koplayalıb `Developer` subclass-ının içinə də ata bilərik. Ancaq bu kodun təkrar istifadəsinə gətirib çıxaracaq. OOP isə əslində tamamilə təkrar kod istifadəsinin qarşısını almaq üçün istifadə olunur. Beləliklə yeni tam versiya kodumuz bu cür görsənəcək.

```python
class Ishci:
    artma_miqdari = 1.04

    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.email = ad + '.' + soyad + '@email.com'
        self.maas = maas
    
    def tamAd(self):
        return '{} {}'.format(self.ad, self.soyad)
    
    def maasi_artir(self):
        self.maas = int(self.maas * self.artma_miqdari)

class Developer(Ishci):
    artma_miqdari = 1.06

    def __init__(self, ad, soyad, maas, proqramlasdirma_dili):
        super().__init__(ad, soyad, maas)
        self.proqramlasdirma_dili = proqramlasdirma_dili

class Manager(Ishci):
    artma_miqdari = 1.10

proqramist_1 = Developer('Mammad', 'Mammadov', 50000, 'Python')
menecer_1 = Manager('Mammad2', 'Mammadov2', 60000)

print(proqramist_1.proqramlasdirma_dili)
```

Bizim taskımız bundan ibarət idi ki, proqramistləri təyin edəndə həmçinin həmin proqramistin istifadə etdiyi proqramlaşdırma dilini də təyin edə bilək. Bunu ümumi `Ishci` classı üçün kodlamağımız mənasız olardı, çünki bu `Ishci` class-ının `Developer` subclass-ından başqa bütün digər subclass-larında lazımsız `proqramlasdirma_dili` atributu yaradacaqdı. Bunun qarşısını almaq üçün bizə lazımdır ki, `Developer` subclass-ının içində init yaradaq. 

Xatırlayırsınzısa `method resolution order` haqqında danışanda qeyd etmişdim ki compiler subclass-ın init methodu olmadıqda onun parent class-ına keçir. 

Sətir 19-da görə bilərsiniz ki, `Developer` sublcass-ının içində yeni init methodu yaratmışıq və o `proqramlasdirma_dili` atributunu da istəyir. 

## super\(\) built-in keyword

Bəs 20-ci sətirdə yazdığımız super\(\) nə deməkdir?

`super()` bizə imkan verir ki, parent class-da olan init methodunun hamısını bir də kopyalamayaq. Onu kopyalamaq əvəzinə `super()` yazmaqla biz parent class-ındaki init methodunda nə təyin olunubsa hamısını işlədə bilirik. Parent class-dakı `init` methodunu çəkməyin bir neçə yolu var. Onların yazılış fərqlərini aşağıdakı tab-lara baxaraq görə bilərsiniz.

{% hint style="danger" %}
Nəzərinizə çatdırmaq istəyirəm ki, aşağıdakı kodların üçü də tamamilə eyni işi görür.
{% endhint %}

{% tabs %}
{% tab title="Kod parçası super\(\) ilə" %}
```python
class Developer(Ishci):
    artma_miqdari = 1.06

    def __init__(self, ad, soyad, maas, proqramlasdirma_dili):
        self.proqramlasdirma_dili = proqramlasdirma_dili
        
        super().__init__(ad, soyad, maas)
```
{% endtab %}

{% tab title="Kod parçası super\(\)-siz" %}
```python
class Developer(Ishci):
    artma_miqdari = 1.06

    def __init__(self, ad, soyad, maas, proqramlasdirma_dili):
        self.proqramlasdirma_dili = proqramlasdirma_dili
        
        
        self.ad = ad
        self.soyad = soyad
        self.email = ad + '.' + soyad + '@email.com'
        self.maas = maas   
```
{% endtab %}

{% tab title="Kod parçası class adı ilə" %}
```python
class Developer(Ishci):
    artma_miqdari = 1.06

    def __init__(self, ad, soyad, maas, proqramlasdirma_dili):
        self.proqramlasdirma_dili = proqramlasdirma_dili
        
        Ishci.__init__(self, ad, soyad, maas)
```
{% endtab %}
{% endtabs %}

İndi isə gəlin `Manager` subclass-ına elə dəyişikliklər edək ki, managerlərin digər işçilərdən kimi idarə etdiyi təyin edilə bilsin. `Developer` subclass-ında yazdığımız kimi `Manager` subclass-ında da `super()` işlətməliyik çünki Manager subclassına aid olan insanların da adı, soyadı və maaşı olacaq. Bundan başqa, Manager-in manage etdiyi insanları özündə saxlaması üçün, `add_emp` metodunu, özündəki siyahıdan çıxartması üçün  `remove_emp` methodunu, özündəki siyahını çap etməsi üçün isə `print_emp` methodunu yazaq. 

```python
# Kodun yuxarı hissəsi kəsilib.
class Manager(Ishci):
    artma_miqdari = 1.10
    # Aşağıda ishciler=None olmasının səbəbi budur ki, PEP8 standartına görə
    # arqument olaraq Mutable object daxil etmək məqsədəuyğun deyil.
    # Bunun yerinə ishciler variable-nı None-a bərabər edib if vasitəsi ilə
    # onu dictionary-ə çevirmək lazımdır.
        
    def __init__(self, ad, soyad, maas, ishciler=None):
        super().__init__(ad, soyad, maas) # Ishci classından atributlar inherit olur.
        if ishciler is None: 
            self.ishciler = []
        else:
            self.ishciler = ishciler

    # Əgər daxil edilən dəyər ishciler-də olmazsa, həmin dəyəri ishciler-ə əlavə et.
    def add_emp(self, emp):
        if emp not in self.ishciler:
            self.ishciler.append(emp)
    
    # Əgər daxil edilən dəyər ishciler-də mövcuddursa, onu ishciler-dən sil.
    def remove_emp(self, emp):
        if emp in self.ishciler:
            self.ishciler.remove(emp)

    # Bu method manager-in manage etdiyi şəxslərin siyahısını çıxardır.
    def print_emp(self):
        # İşçisi ekrana çıxacaq olan managerin tamAd-i çap olunur birinci növbədə.
        print('{} is managing these people'.format(self.tamAd())) 
        for emp in self.ishciler: # ishciler siyahısındakı hər bir employeenin 
            print('->', emp.tamAd()) # tamAd-ini ekrana çap edir.

proqramist_1 = Developer('Mammad', 'Mammadov', 50000, 'Python')
ishci_1 = Ishci('Shi', 'Fu', 50000)
menecer_1 = Manager('Sue', 'Smith', 60000)


menecer_1.add_emp(proqramist_1) # menecer_1-in manage etdiyi insan siyahısına proqramist_1-i əlavə edir.
menecer_1.add_emp(ishci_1) # menecer_1-in manage etdiyi insan siyahısına ishci_1-i əlavə edir.
menecer_1.print_emp()    # menecer_1-in manage etdiyi insan siyahısını ekrana çap edir.
menecer_1.remove_emp(proqramist_1) # proqramist_1-i menecer_1-in manage etdiyi insanlar siyahısından silir.
menecer_1.print_emp()       # menecer_1-in manage etdiyi insan siyahısını ekrana çap edir.
```

Output:

> Sue Smith is managing these people   
> -&gt; Mammad Mammadov  
> -&gt; Shi Fu  
> Sue Smith is managing these people   
> -&gt; Shi Fu

Yuxarıdakı misalda kod parçalarının nə etdiyini comment şəklində izah etmişəm.

## isinstance\(\) və issubclass\(\)

Bu methodların ikisi də cavab olaraq `True` vəya `False` qaytarır.

`isinstance(man1, Manager)` dediyimizdə, əgər man\_1 Manager-in instance-ı olarsa True, olmazsa False qaytaracaq.  
`issubclass(Manager, Ishci)` dediyimizdə, əgər Manager classı Ishci classının subclass-ıdırsa True, deyilsə False qaytaracaq.

```python
print(isinstance(menecer_1, Manager))        # True
print(isinstance(menecer_1, Ishci))       # True
print(isinstance(menecer_1, Developer))      # False
print(issubclass(Developer, Ishci))   # True
print(issubclass(Manager, Ishci))     # True
print(issubclass(Manager, Developer))    # False
```

Son olaraq ümumi kod parçasını atıram ki, kimdəsə çətinlik varsa baxa bilsin:

```python
class Ishci:
    artma_miqdari = 1.04

    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.email = ad + '.' + soyad + '@email.com'
        self.maas = maas
    
    def tamAd(self):
        return '{} {}'.format(self.ad, self.soyad)
    
    def maasi_artir(self):
        self.maas = int(self.maas * self.artma_miqdari)

class Developer(Ishci):
    artma_miqdari = 1.06

    def __init__(self, ad, soyad, maas, proqramlasdirma_dili):
        super().__init__(ad, soyad, maas)
        self.proqramlasdirma_dili = proqramlasdirma_dili

class Manager(Ishci):
    artma_miqdari = 1.10
    
    def __init__(self, ad, soyad, maas, ishciler=None):
        super().__init__(ad, soyad, maas)
        if ishciler is None:
            self.ishciler = []
        else:
            self.ishciler = ishciler

    def add_emp(self, emp):
        if emp not in self.ishciler:
            self.ishciler.append(emp)

    def remove_emp(self, emp):
        if emp in self.ishciler:
            self.ishciler.remove(emp)

    def print_emp(self):
        print('{} is managing these people'.format(self.tamAd()))
        for emp in self.ishciler:
            print('->', emp.tamAd())

proqramist_1 = Developer('Mammad', 'Mammadov', 50000, 'Python')
ishci_1 = Ishci('Shi', 'Fu', 50000)
menecer_1 = Manager('Sue', 'Smith', 60000)


print(isinstance(menecer_1, Manager))   # True
print(isinstance(menecer_1, Ishci))  # True
print(isinstance(menecer_1, Developer)) # False
print(issubclass(Developer, Ishci))  # True
print(issubclass(Manager, Ishci))  # True
print(issubclass(Manager, Developer)) # False


```

Hörmətlə.

