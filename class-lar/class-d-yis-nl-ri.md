---
description: Class dəyişənləri nədir?
---

# Class dəyişənləri

Class dəyişənləri, class-ın aid olduğu bütün instance-lar üzrə paylanan dəyişənlərə deyilir.

İnstance dəyişənləri hər instance üçün müxtəlif idi. Ancaq Class dəyişənləri hər instance üçün eynidir.

Gəlin belə təsəvvür edək ki, şirkət hər il öz işçilərinin maaşını 12 faiz artırır. Biz bunu kod olaraq ifadə etmək üçün aşağıdaki kimi kod yaza bilərik:

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
        
    def maas_artimi():
        self.pay = int(self.pay * artma_miqdari)
        
ishci_1 = Ishci('Ali', 'Mammadzada', 50000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 60000)
```

Əvvəlki bölmədə yazdığım koda, 3-cü, 14-15-ci sətirləri əlavə etdim. Riyazi baxımdan bir dəyəri 12 faiz artırmağın yolu həmin dəyəri 1.12-yə vurmaqdır. Həmin dəyərin bizə axırda `int` dəyərində geri dönməsi üçün bütün hesablamanı `int()` içinə aldım.

Ancaq maraqlısı budur ki, yuxarıdaki kodu çalışdırdıqda python xəta verir:

```text
NameError: name 'artma_miqdari' is not defined.
```

 Bu xəta ona görə çıxır ki, class dəyişənini çağırmaq istədiyimizdə, həmin dəyişəni ya classın ya da instance-ın içindən çağırmalıyıq. 

15-ci sətirdə olduğu kimi `maas_artimi` method-un içində `artma_miqdari` dəyişənini görmədiyi üçün, onu `Ishci.artma_miqdari` \(vəya `self.artma_miqdari`\) olaraq dəyişdirmək lazımdır.

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
        
    def maas_artimi():
        self.maas = int(self.pay * self.artma_miqdari)
        
ishci_1 = Ishci('Ali', 'Mammadzada', 50000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 60000)

print(Ishci.artma_miqdari)    # 1.12
print(ishci_1.artma_miqdari)  # 1.12
print(ishci_2.artma_miqdari)  # 1.12
```

`ishci_1` instance-ının özünün `artma_miqdari` adında attributu yoxdur. Ancaq `self` vasitəsi ilə o hansı class-a aid olduğunu bilir. Buna görə də özünün aid olduğu class-ın içindəki attributları axtarmağa başlıyır və `artma_miqdari`-nin `1.12`yə bərabər olduğunu görür.

Sizi maraqlı bir halla tanış etmək istəyirəm. Əgər siz `ishci_1.artma_miqdari = 1.15` desəniz, məntiqi olaraq `ishci_1`-in aid olduğu  class atributunun \(yəni `Ishci.maas_artimi`-nin da dəyişməsini gözləyərdiniz elə deyil?



Ancaq python belə işləmir. Əgər siz `ishci_1.artim_miqdari`-ni `1.15` etsəniz, bu zaman python özü `ishci_1` instance-ında `artim_miqdari` adında əvvəl mövcud olmayan attribute yaradır. 

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
        
    def maas_artimi():
        self.maas = int(self.maas * self.artma_miqdari)
        
ishci_1 = Ishci('Ali', 'Mammadzada', 50000)
ishci_2 = Ishci('Serxan', 'Ismayilov', 60000)


print(ishci_1.__dict__)
# {'ad': 'Ali', 'soyad': 'Mammadzada', 'maas': 50000}
ishci_1.artma_miqdari = 1.15

print(Ishci.artma_miqdari)    # 1.12
print(ishci_1.artma_miqdari)  # 1.15
print(ishci_2.artma_miqdari)  # 1.12

print(ishci_1.__dict__) 
# {'artma_miqdari': 1.15, 'ad': 'Ali', 'soyad': 'Mammadzada', 'maas': 50000}
```

Nümunədən də gördüyünüz kimi, əvvəl  `ishci_1`-in `namespace`-ində `artma_miqdari` yox idi. Ancaq sonradan yarandı. Əgər yuxarıdaki kodun 15-ci sətrində `self.maas_artimi` yox `Ishci.maas_artimi` yazsaydıq, onda `ishci_1`ə etdiyimiz dəyişiklik bütün `Ishci` class-ına tətbiq ediləcəkdi.

