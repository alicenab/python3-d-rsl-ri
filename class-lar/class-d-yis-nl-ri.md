---
description: Class dəyişənləri nədir?
---

# Class dəyişənləri

Class dəyişənləri, class-ın aid olduğu bütün instance-lar üzrə paylanan dəyişənlərə deyilir.

İnstance dəyişənləri hər instance üçün müxtəlif idi. Ancaq Class dəyişənləri hər instance üçün eynidir.

Gəlin belə təsəvvür edək ki, şirkət hər il öz işçilərinin maaşını 10 faiz artırır. Biz bunu kod olaraq ifadə etmək üçün aşağıdaki kimi kod yaza bilərik:

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



