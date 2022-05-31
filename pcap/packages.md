---
description: >-
  Modullar öz içlərində funksiyaları saxladığı kimi, package-lər də öz içlərində
  modulları saxlayırlar.
---

# Packages

&#x20;Python modulu müəyyən sıraya görə axtarır. Həmin sıranı əyani şəkildə görmək üçün kiçik kod parçası yazmaq mümkündür:

```
import sys

for p in sys.path:
    print(p)

'''
/home/alicenab/Desktop/test
/usr/lib64/python310.zip
/usr/lib64/python3.10
/usr/lib64/python3.10/lib-dynload
/usr/lib64/python3.10/site-packages
/usr/lib/python3.10/site-packages
'''
```

Sıranın ən yuxarısındakı element birinci path elementi adlanır, python zip tipli faylları da adi qovluqlar kimi emal edə bilir. Məhz bu səbəbdən 8-ci sətirdə python310.zip faylını görmək mümkündür.

Kodun daxilində döngüdən əvvəl `sys.path.append('/home/alicenab/Desktop/test2')` yazaraq `test2` qovluğunu ümumi siyahının sonuna əlavə edə bilərik. Əgər öz qovluğumuzu ümumi siyahının əvvəlinə əlavə etmək istəyiriksə, koda aşağıdakı sətri əlavə etmək lazım olacaq.

`sys.path.insert(0,'/home/alicenab/Desktop/test2')`

#### modullar və packagelər

python pathdakı hər bir fayl adını modul adı kimi başa düşür. Yəni pathdakı hər hansı faylı modul kimi koda import etmək mümkündür.&#x20;

Pathdakı hər bir qovluq package olaraq başa düşülə bilər. Tək şərt ondan ibarətdir ki həmin qovluğun içində `__init__.py` faylı olmalıdır.

Package-lər özündə modulları cəmləşdirirlər. Packageləri də modullar kimi kod içində import etmək mümkündür. package-ləri import edərkən `from` açar sözündən istifadə olunur.&#x20;

Aşağıdakı qovluq strukturuna nəzər yetirsək görərik ki, `yeniPackage` adında qovluq və onunla eyni səviyyədə yerləşən `main.py` adında fayl, `yeniPackage` qovluğunun içində isə iki ədəd fayl mövcuddur.

```
.
├── main.py
└── yeniPackage
    ├── __init__.py
    └── yeniModul.py
```

`yeniModul.py` faylının içindəki kod:

```
def yeniModulunFunksiyasi():
    print("Men yeni modulun funksiyasiyam.")
```

`main.py` faylının içindəki kodu iki cür yazmaq olar. Birinici üsulda faylın içindəki bütün funksiyalar hal-hazırda olduğumuz faylın içinə kopyalanacağı üçün bu resursların qeyri səmərəli işlənməsinə gətirib çıxarır. Birinci üsulda import etdiyimiz modul içindəki funksiyanı çağırarkən nöqtədən istifadə etməliyik. Məsələn: `yeniModul.yeniModulunFunksiyasi()`

İkinci üsul vasitəsilə konkret bir ad import etdiyimizə görə konflikt vermək ehtimalı mövcuddur. Bu səbəbdən `as` açar sözü də işlədə bilərdik:

{% tabs %}
{% tab title="Birinci üsul" %}
```python
from yeniPackage import yeniModul

yeniModul.yeniModulunFunksiyasi()
```
{% endtab %}

{% tab title="İkinci üsul" %}
```python
from yeniPackage.yeniModul import yeniModulunFunksiyasi
#from yeniPackage.yeniModul import yeniModulunFunksiyasi as yMF

yeniModulunFunksiyasi()
#yMF()
```
{% endtab %}
{% endtabs %}

`main.py` faylı icra olunduqda ekrana aşağıdakı yazı çıxır:

```
Men yeni modulun funksiyasiyam.
Men yeni modulun funksiyasiyam.
```











