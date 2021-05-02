# Mathod-lar\(regular, class, static\)

Bundan əvvəlki dərsimizdə ən son bu səviyyədə qalmışdıq, gəlin davam edək. t

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
        
    def maas_artimi(self):
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

Bir daha yaddaşımızı təzələyək:

Class içində istifadə təyin etdiyimiz funksiyaları method adlandırmışdıq.

Məntiqi uyğunluğa görə, içində `self` yazdığımız methodlar, instance-lara aid olurdu. və `self` methodu ilə dəyişdirdiyimiz dəyişənlər yalnız həmin instance-a aid olurdu. Bəs class dəyişənlərinə necə təsir edə bilərik?

Blirik ki, məsələn 14-cü sətirdəki method-un self attribute-u, 

Bunun yolu `class method`larından istifadə etməkdir. 



