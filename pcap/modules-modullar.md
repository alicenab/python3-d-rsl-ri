# Modules (modullar)

İstifadə olunan bütün kodlar proqramistlər tərəfindən inkişaf etdirilirlər. Bəzi kodlar çox sadə olsa da, bəziləri çox mürəkkəbdir və bütün işi bir nəfərin görməsi proyektin bitməsi üçün verilmiş olan vaxtdan daha çoxunu tələb edir. Real həyatdan bir nümunə götürək, konsert tədbirinin təşkil olunması üçün lazım olan hərşeyi bir şəxsin təmin etməsi absürddür. Adətən lazım olan işlər komandalar və ya şəxslər arasında bölüşdürülür və hərə bir işi görür. Bunun nəticəsi olaraq bir nəfər tərəfindən çox uzun müddətdə başa çata biləcək iş birneçə şəxs tərəfindən qısa müddətdə başa çatır.

Eyni məntiq proqramlaşdırmada da istifadə olunur. Proqram modullara bölünür. İşin bölünməsi isə **decomposition** adlanır.&#x20;

Modulun tərifi rəsmi dokumentasiyaya əsasən belədir: Module it is **a file containing Python definitions and statements.** which can be later imported and used when necessary.

Sonra lazım olduğunda import edilə bilərək istifadə olunan, içində python kodu saxlayan fayl python modulu adlanır.

Əgər əvvəl mövcud olan modulu istifadə edirsinizsə, vəya çətin bir işi görmək üçün əvvəl mövcud olmuş bir modulun üzərində dəyişikliklər edirsinizsə, siz modulun istifadəçisi sayılırsınız. Ya özünüz ya da digər proqramistlərin həyatını asanlaşdırmaq üçün tamamilə yeni bir modul yazmısınızsa, siz modulun (**supplier**) dəstəkləyicisi sayılırsınız.

Hər bir kitabın hissələri, paraqrafları və s. olduğu kimi, python modullarının da özünün classları, obyektləri, metodları və funksiyaları mövcuddur. Pythonun öz üstündə gələn modulları vardır, bundan əlavə olaraq gələcək səhifələrdə hansısa modulun necə internetdən yüklənməli olduğunu öyrənəcəyik.

Mövcud olan modulu koda daxil etmək üçün `import` açar sözündən istifadə olunur. Eyni vaxtda bir və ya bir neçə modulu import etmək mümkündür. `import` açar sözündən sonra import etmək istədiyimiz **modulun adı**nı yazmaq lazımdır. Məsələn.

```
import math
import sys
```

vəya

```
import math, sys
```

Göstərilmiş nümunələrdə `math` və `sys` modul adlarıdır.

### Namespace nədir?

Təsəvvür edin ki 3 dostunuz var və onların üçünün də Məhəmməd adında dostu var. 3 dostunuzun söhbətinə ortadan daxil olsanız və eşitsəniz ki, Məhəmməd haqqında danışırlar, soruşarsınız ki, hansı Məhəmməddən danışırsınız?

Namespace-ləri virtual mühit adlandırmaq olar, yəni dolayısıyla desək, math modulunun içində pi  mövcuddur, ancaq siz özünüz myMath adında modul yaradıb onun içində başqa bir pi varlığını yarada bilərsiz.



Kod yazarkən necə bilmək lazımdır ki, mən hansı pi-ni işlədirəm? Çox sadə. pi-dən əvvəl onun hansı moduldan gəldiyini göstərərək. Məsəlçün:

```python
import math
print(math.pi) # ekrana çıxır: 3.141592653589793
```

Eyni vaxtda müxtəlif namespace-lərin eyni adlı entity-sini istifadə etmək olarmı? Bəli olar:

```python
import math

def sin(x):
    if 2 * x == pi:
        return 0.99999999
    else:
        return None

pi = 3.14

print(sin(pi/2))            # buradadakı sin və pi 3 və 9-cu sətirdən gəlir
print(math.sin(math.pi/2))  # buradakı sin və pi 1-ci sətirdə import olunmuş math-dan gəlir.
```

Sırf istədiyiniz entity-ləri də import edə bilərsiniz. Bunun üçün from açar sözü istifadə olunmalıdır. Hərfi tərcüməsi bucürdür "x modulundan y entity-sini import et". Lakin burda diqqətli olunması lazım olan məqamlar var. Bu halda siz birbaşa kodun yazıldığı faylın namespace-inə dəyişəni gətirdiyiniz üçün həmin dəyişən sonradan modifikasiya oluna bilər. Çünki həmin dəyişəni çağırmaq üçün gəldiyi modulu göstərməyə ehtiyac qalmır:

```python
from math import pi, sin
print(pi) # 3.141592653589793

pi = 4
print(pi) # 4
print(math.pi)#from sözü ilə import olunan entitylər modul adıyla çağırılmamalıdır
#6-cı sətir xəta verəcək.
```

Yuxarıda göstərilmiş misalın daha aqresiv forması aşağıdakı nümunədir. `*` işarəsi vasitəsilə bütün entity-ləri hazırki namespace-ə gətirmək etibarlı metod deyil və bundan yayınmaq lazımdır:

```python
from math import *
print(pi) # 3.141592653589793

pi = 4
print(pi) # 4
```

### as açar sözü

Modullar import edilərkən qarışıqlığın qarşısını almaq üçün aliaslardan istifadə edilə bilər. Bunun üçün as açar sözündən istifadə etmək lazımdır. Hərfi tərcüməsi belədir: "x modulunu y adıyla import et". Məsələn, aşağıdakı misalda math modulu riyaziyyat adıyla import edilmişdir:

```python
import math as riyaziyyat

pi = riyaziyyat.pi

print(pi)
```

Entitylərə də alias təyin etmək mümkündür. Məsələn, aşağıdakı kodda math moduluna aid olan pi və sin entityləri uyğun olaraq myPI və mySIN adlarıyla import edilmişdir:

```python
from math import pi as myPI, sin as mySIN

print(myPI, mySIN(myPI/2)) # 3.141592653589793 1.0
```

### dir() funksiyası

dir() funksiyası vasitəsilə modul içindəki bütün entity-lərin adına baxmaq mümkündür. Məsələn:

```
import math
print(dir(math))

# ['__doc__', '__loader__', '__name__', '__package__', '__spec__', 'acos', 'acosh', 'asin', 'asinh', 'atan', 'atan2', 'atanh', 'ceil', 'comb', 'copysign', 'cos', 'cosh', 'degrees', 'dist', 'e', 'erf', 'erfc', 'exp', 'expm1', 'fabs', 'factorial', 'floor', 'fmod', 'frexp', 'fsum', 'gamma', 'gcd', 'hypot', 'inf', 'isclose', 'isfinite', 'isinf', 'isnan', 'isqrt', 'lcm', 'ldexp', 'lgamma', 'log', 'log10', 'log1p', 'log2', 'modf', 'nan', 'nextafter', 'perm', 'pi', 'pow', 'prod', 'radians', 'remainder', 'sin', 'sinh', 'sqrt', 'tan', 'tanh', 'tau', 'trunc', 'ulp']
```

### random modulu

Random modulu təsadüfi ədədlərin yaradılması üçün istifadə edilir.

#### random() funksiyası.

random modulunun random() funksiyası (0.0 <= x < 1.0) arasında təsadüfi float ədəd qaytarır.

random modulu hər hansı bir seed-i input kimi qəbul edərək həmin seed əsasında random bir dəyər qaytarır. Adətən hər proqram işə düşdükdə yeni ədəd yaranması üçün vaxt-dan seed kimi istifadə olunur.&#x20;

#### seed() funksiyası.

Yuxarıda qeyd olunduğu kimi, əgər seed() funksiyası heç bir arqumentsiz işlədilərsə, hazırki vaxta görə seed təyin olunur. Bundan əlavə olaraq seed() funksiyasına hansısa integer arqument kimi daxil edilə bilər. Məsələn aşağıdakı nümunəyə baxaq:

```python
from random import random, seed

seed(0)

for i in range(5):
    print(random())
    
'''
Ekrana çap olunan nəticə:
0.8444218515250481
0.7579544029403025
0.420571580830845
0.25891675029296335
0.5112747213686085
'''
```

Yuxarıda göstərilmiş kodu siz də öz komputerinizdə işlədin, komputerinizin float ədədləri hesablama gücündən asılı olaraq ya eyni ya da mənim nəticəmə çox bənzər bir nəticə əldə edəcəksiniz.

#### randint() və randrange() funksiyaları

Əgər təsadüfi integer ədəd əldə etmək istəyirsinizsə, bu funksiyalar köməyə çatacaq. Aralarında iki fərq var. randrange() heç vaxt yüksək dəyəri random ədəd kimi geri qaytarmır.&#x20;

```python
from random import randrange, randint

tesadufi_1 = randint(1,10)   # 1 və 10 nəticələrə daxil ola bilər.
tesadufi_2 = randrange(1,10) # 10 nəticələrə daxil ola bilməz

for i in range(10):
    tesadufi_3 = randrange(1,10,3) # 1,4,7 qaytaracaq.
    tesadufi_4 = randrange(0, 1, 1) # həmişə 0 qaytaracaq
    print(tesadufi_3, tesadufi_4)
```

#### choice() və sample() funksiyaları

Bu funksiyalar əldə olan siyahıdan təsadüfi verilənləri seçmək üçün istifadə olunur. choice() funksiyası vasitəsilə empty olmuyan bir siyahıdan təsadüfi bir elementi seçmək mümkündür. sample() funksiyası vasitəsilə isə empty olmayan funksidan istədiyimiz qədər təsadüfi element seçə bilərik. Məsələn:

```
from random import sample
from secrets import choice


my_list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

print(choice(my_list))    # 5
print(sample(my_list, 10))#[3, 5, 2, 1, 4, 6, 7, 8, 9, 10]
```

### platform modulu

#### platform() funksiyası



```
from platform import platform

# Alias true olduqda daha umumi informasiya vermeye calisir.
# terse true olduqda minimum informasiya vermeye calisir.

print(platform(aliased=True, terse=True))
print(platform(aliased=True, terse=False))
print(platform(aliased=False, terse=True))
print(platform(aliased=False, terse=False))
print()
# 0 ve 1 parametrlerini de funksiyaya oturmek mumkundur.
print(platform())
print(platform(1))
print(platform(0, 1))
```





