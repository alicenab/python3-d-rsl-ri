---
description: İrsilik
---

# Class Inheritance

```python
class Ishci:
    artma_miqdari = 1.12

    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.maas = maas
        self.email = ad + '.' + soyad + '@email.com'

    def tamAd(self):
        return '{} {}'.format(self.ad, self.soyad)

    def maasi_artir(self):
        self.pay = int(self.maas * self.artma_miqdari)


ishci_1 = Ishci('Ali', 'Mammadzada', 50000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 60000)

print(ishci_1.maas) # 50000
print(ishci_2.maas) # 60000
```

 Adından da göründüyü kimi, inheritance \(irsilik\) üst class-ın method və attribute-larını alt classa ötürür. Bu ona görə vacib birşeydir ki, inheritance vasitəsi ilə biz üst class-a aid method və attributları alt class-a ötürə, alt class-a əlavə üstünlüklər yarada biləcək method və attribut kimi dəyişikliklər əlavə edə, bütün bu vaxt ərzində isə üst class-a zərər verməyə bilərik.

Gəlin indiyə qədər üzərində işlədiyimiz `Ishci` class-ı üzərində işimizi davam edək. Gəlin fərz edək ki, Proqramçılar və Menecerlər kimi yeni iki işçi tipi yaratmaq tapşırığı almışıq. Məntiqi uyğunluğa görə, Proqramçılar və Menecerlər də həmçinin işçi olduğuna görə, İşçi classının özəlliklərini daşımalıdırlar.

Ümumi class yaratmaq ənənəmizə əsaslanaraq, yeni class yaradaq 



```python
class Ishci:
    artma_miqdari = 1.12

    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.maas = maas
        self.email = ad + '.' + soyad + '@email.com'

    def tamAd(self):
        return '{} {}'.format(self.ad, self.soyad)

    def maasi_artir(self):
        self.maas = int(self.maas * self.artma_miqdari)

class Proqramist(Ishci):
    pass

class Menecer(Ishci):
    pass

ishci_1 = Ishci('Ali', 'Mammadzada', 50000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 60000)

proqramist_1 = Proqramist('Ismayil', 'Aliyev', 70000)
menecer_1 = Menecer('Bayram', 'Camilli', 80000)

print(help(Proqramist))
```

Proqramist class-ının mötərizə içində "Ishci" classını göstərərək, Proqramist class-ının hansı class-dan inherit olunmasını təyin etmiş oldKodu ekrana aşağıdaki nəticəni çıxarır:

```text
Help on class Proqramist in module __main__:

class Proqramist(Ishci)
 |  Proqramist(ad, soyad, maas)
 |  
 |  Method resolution order:
 |      Proqramist
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
 |  artma_miqdari = 1.12

None

Process finished with exit code 0

```

Yuxarıdaki kodun 6-cı sətrində gördüyünüz `Method resolution order` python-un methodlar və attribute-lar üzrə axtarış sırasıdır. Gördüyünüz kimi, python method və attribute-ları  ilk növbədə `Proqramist` class-ının içində, sonra `Ishci` sonra isə, `builtin.object`-lərin içində axtarır.

Bizim halımızda axtarılan object `Ishci` class-ının içindədir. 11-18 sətirləri arasında `Ishci` class-ından inherit olunmuş method-lar və onlar haqqında qısa məlumatı görə bilərsiniz. `__dict__` və `__weakref__` həmişə ötürüldüyünü nəzərdə saxlayası olsaq, 30-32-ci sətirlərdə `Ishci` class-ından inherit olan data və attribute-ları görmək mümkündür.

```python
class Ishci:
    artma_miqdari = 1.12

    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.maas = maas
        self.email = ad + '.' + soyad + '@email.com'

    def tamAd(self):
        return '{} {}'.format(self.ad, self.soyad)

    def maasi_artir(self):
        self.maas = int(self.maas * self.artma_miqdari)

class Proqramist(Ishci):
    artma_miqdari = 1.21

class Menecer(Ishci):
    artma_miqdari = 1.41

ishci_1 = Ishci('Ali', 'Mammadzada', 10000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 10000)
proqramist_1 = Proqramist('Ismayil', 'Aliyev', 10000)
menecer_1 = Menecer('Bayram', 'Camilli', 10000)

# Maasi deyismeyen birinci isci:
print(ishci_1.maas)
# Maasi artan ikinci isci:
ishci_2.maasi_artir()
print(ishci_1.maas)
print(ishci_2.maas)
# Maasi artan proqramist:
proqramist_1.maasi_artir()
print(proqramist_1.maas)
# Maasi artan menecer:
menecer_1.maasi_artir()
print(menecer_1.maas)
```

Həmin kodun outputu:

`10000   
10000  
11200  
12100  
14100`



Gördüyünüz kimi, `ishci_1`-in \(əsas classımız\) maaşı dəyişmədi. Əsas classımızdan törəyən `proqramist_1` class-ının, menecer\_1 class-ının isə maaşı dəyişdi.

```python
class Ishci:

    artma_miqdari = 1.12
    
    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.maas = maas
        self.email = ad + '.' + soyad + '@email.com'
        
    def tamAd(self):
        return '{} {}'.format(self.ad, self.soyad)
        
    def maasi_artir(self):
        self.maas = int(self.maas * self.artma_miqdari)
        
class Proqramist(Ishci):
    artma_miqdari = 1.25
    
    def __init__(self, ad, soyad, maas, proq_dili):
        super().__init__(ad, soyad, maas)
        #Ishci.__init__(self, ad, soyad, maas)
        self.proq_dili = proq_dili

ishci_1 = Ishci('Ali', 'Mammadzada', 50000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 60000)

proqramist_1 = Proqramist('Ismayil', 'Aliyev', 70000)
proqramist_2 = Proqramist('Bayram', 'Camilli', 80000)
```

{% hint style="info" %}
Proqramlaşdırmada single class inheritance və multiple class inheritance var. Biz hal-hazırda asan olsun deyə nümunəmizi single class inheritance üzərindən başa saldığımız üçün, 21-ci sətirdəki kimi super\(\)-dən istifadə edəcəyik. Ancaq məlumat üçün deyim ki, 21 və 22-ci sətirdəki ifadələr tamamilə eynidir.
{% endhint %}

```python
class Ishci:

    artma_miqdari = 1.12
    
    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.maas = maas
        self.email = ad + '.' + soyad + '@email.com'
        
    def tamAd(self):
        return '{} {}'.format(self.ad, self.soyad)
        
    def maasi_artir(self):
        self.maas = int(self.maas * self.artma_miqdari)
        
class Proqramist(Ishci):
    artma_miqdari = 1.25
    
    def __init__(self, ad, soyad, maas, proq_dili):
        super().__init__(ad, soyad, maas)
        #Ishci.__init__(self, ad, soyad, maas)
        self.proq_dili = proq_dili

class Menecer(Ishci):

    def __init__(self, ad, soyad, maas, idaresinde=None):
        super().__init__(ad, soyad, maas)
        if idaresinde is None:
            self.idaresinde = []
        else:
            self.idaresinde = idaresinde
            
    def ishci_elavEt(self, emp):
        if emp not in self.idaresinde:
            self.idaresinde.append(emp)


ishci_1 = Ishci('Ali', 'Mammadzada', 50000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 60000)

proqramist_1 = Proqramist('Ismayil', 'Aliyev', 70000)
proqramist_2 = Proqramist('Bayram', 'Camilli', 80000)
```







