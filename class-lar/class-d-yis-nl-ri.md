---
description: Class dəyişənləri nədir?
---

# Class dəyişənləri

Class dəyişənləri, class-ın aid olduğu bütün instance-lar üzrə paylanan dəyişənlərə deyilir.

İnstance dəyişənləri hər instance üçün müxtəlif idi. Ancaq Class dəyişənləri hər instance üçün eynidir.

Gəlin belə təsəvvür edək ki, şirkət hər il öz işçilərinin maaşını 12 faiz artırır. Biz bunu kod olaraq ifadə etmək üçün aşağıdaki kimi kod yaza bilərik:

```python
class Ishci:

    maas_artimi = 1.12
    
    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.maas = maas
        self.email = ad + '.' + soyad + '@email.com'
        
    def tamAd(self):
        return '{} {}'.format(self.ad, self.soyad)
        
    def maas_artimi():
        self.pay = int(self.pay * maas_artimi)
        
ishci_1 = Ishci('Ali', 'Mammadzada', 50000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 60000)
```

Əvvəlki bölmədə yazdığım koda, 3-cü, 14-15-ci sətirləri əlavə edirəm. Riyazi baxımdan bir dəyəri 12 faiz artırmağın yolu həmin dəyəri 1.12-yə vurmaqdır. Həmin dəyərin bizə axırda `int` dəyərində geri dönməsi üçün bütün hesablamanı `int()` içinə aldım.

Ancaq maraqlısı budur ki, yuxarıdaki kodu çalışdırdıqda python xəta verir:

```text
NameError: name 'maas_artimi' is not defined.
```

 Bu xəta ona görə çıxır ki, class dəyişənini çağırmaq istədiyimizdə, həmin dəyişəni ya classın ya da instance-ın içindən çağırmalıyıq. 

15-ci sətirdə olduğu kimi `maas_artimi` method-un içində `maas_artimi` dəyişənini görmədiyi üçün, onu `Ishci.maas_artimi` \(vəya `self.maas_artimi`\) olaraq dəyişdirmək lazımdır.

```python
class Ishci:

    maas_artimi = 1.12
    
    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.maas = maas
        self.email = ad + '.' + soyad + '@email.com'
        
    def tamAd(self):
        return '{} {}'.format(self.ad, self.soyad)
        
    def maas_artimi():
        self.pay = int(self.pay * self.maas_artimi)
        
ishci_1 = Ishci('Ali', 'Mammadzada', 50000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 60000)

print(Ishci.maas_artimi)    # 1.12
print(ishci_1.maas_artimi)  # 1.12
print(ishci_2.maas_artimi)  # 1.12
```

`ishci_1` instance-ının özünün `maas_artimi` adında attributu yoxdur. Ancaq `self` vasitəsi ilə o hansı class-a aid olduğunu bilir. Buna görə də özünün aid olduğu class-ın içindəki attributları axtarmağa başlıyır və `maas_artimi`-nin `1.12`yə bərabər olduğunu görür.

Sizi maraqlı bir halla tanış etmək istəyirəm. əgər siz `ishci_1.maas_artimi = 1.15` desəniz, məntiqi olaraq `ishci_1`-in aid olduğu  class atributunun \(yəni `Ishci.maas_artimi`-nin da dəyişməsini gözləyərdiniz elə deyil?

Ancaq python belə işləmir. Əgər siz `ishci_1.maas_artimi`-ni `1.15` etsəniz, bu zaman python özü `ishci_1` instance-ında `maas_artimi` adında əvvəl mövcud olmayan attribute yaradır. 

```python
class Ishci:

    maas_artimi = 1.12
    
    def __init__(self, ad, soyad, maas):
        self.ad = ad
        self.soyad = soyad
        self.maas = maas
        self.email = ad + '.' + soyad + '@email.com'
        
    def tamAd(self):
        return '{} {}'.format(self.ad, self.soyad)
        
    def maas_artimi():
        self.pay = int(self.pay * self.maas_artimi)
        
ishci_1 = Ishci('Ali', 'Mammadzada', 50000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 60000)


print(ishci_1.__dict__)
# {'ad': 'Ali', 'soyad': 'Mammadzada', 'maas': 50000}
ishci_1.maas_artimi = 1.15

print(Ishci.maas_artimi)    # 1.12
print(ishci_1.maas_artimi)  # 1.15
print(ishci_2.maas_artimi)  # 1.12

print(ishci_1.__dict__) 
# {'maas_artimi': 1.15, 'ad': 'Ali', 'soyad': 'Mammadzada', 'maas': 50000}
```

Nümunədən də gördüyünüz kimi, əvvəl  `ishci_1`-in `namespace`-ində `maas_artimi` yox idi. Ancaq sonradan yarandı.

