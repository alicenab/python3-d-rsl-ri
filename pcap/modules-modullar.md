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

### math modulu

#### riyazi funksiyalar

```python
from math import pi, radians, degrees, sin, cos, tan, asin

ad = 90
ar = radians(ad)
ad = degrees(ar)

print(ad == 90.)                    # True
print(ar == pi / 2.)                # True
print(sin(ar) / cos(ar) == tan(ar)) # True
print(asin(sin(ar)) == ar)          # True
```

Sadalananlardan başqa, math modulunun aşağıdakı metodları da mövcuddur:

pow() built-in funksiyadır və math-dan import edilməyə ehtiyacı yoxdur.

```
asin(x) → the arcsine of x;
acos(x) → the arccosine of x;
atan(x) → the arctangent of x.
sinh(x) → the hyperbolic sine;
cosh(x) → the hyperbolic cosine;
tanh(x) → the hyperbolic tangent;
asinh(x) → the hyperbolic arcsine;
acosh(x) → the hyperbolic arccosine;
atanh(x) → the hyperbolic arctangent.
e → a constant with a value that is an approximation of Euler's number (e)
exp(x) → finding the value of ex;
log(x) → the natural logarithm of x
log(x, b) → the logarithm of x to base b
log10(x) → the decimal logarithm of x (more precise than log(x, 10))
log2(x) → the binary logarithm of x (more precise than log(x, 2))
ceil(x) → the ceiling of x (the smallest integer greater than or equal to x)
floor(x) → the floor of x (the largest integer less than or equal to x)
trunc(x) → the value of x truncated to an integer (be careful - it's not an equivalent either of ceil or floor)
factorial(x) → returns x! (x has to be an integral and not a negative)
hypot(x, y) → returns the length of the hypotenuse of a right-angle triangle with the leg lengths equal to x and y (the same as sqrt(pow(x, 2) + pow(y, 2)) but more precise)
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

platform() funksiyası avadanlığın xüsusiyyətləri, əməliyyat sistemi və interpreter-in versiyası kimi bir neçə məlumatı ekrana çıxarır.

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

#Ekrana cap olunacaq:
#Linux-5.17.9-300.fc36.x86_64-x86_64-with-glibc2.35
```

#### machine() funksiyası

machine() əməliyyat sisteminin istifadə etdiyi prosessorun ümumi versiyasını ekrana çıxarır (x86\_64 vəya x86)

#### processor() funksiyası

processor() funksiyası mümkün olduğu halda prosessorun əsl tam adını qaytarır.

#### system() funksiyası

system() funksiyası əməliyyat sisteminin adını string olaraq qaytarır

#### version() funksiyası

version() funksiyası əməliyyat sisteminin versiyasını string olaraq qaytarır

```
from platform import machine
from platform import processor
from platform import system
from platform import version

print(machine())   #x86_64
print(processor()) #Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz
print(system())    #Linux
print(version())   #1 SMP Debian 4.4.6-1+rpi14 (2016-05-05)
```

#### python\_implementation() və python\_version\_tuple() funksiyaları

python\_implementation() funksiyası pythonun hansı implementasiyasından istifadə etdiyiniz haqqında məlumat verir.

python\_version\_tuple() funksiyası quraşdırılmış python-un əsas(major) versiyası, köməkçi(minor) versiyası və patch leveli haqqında məlumat verir. Məsələn:

```
from platform import python_implementation, python_version_tuple

print(python_implementation())       # CPython

for atr in python_version_tuple():
    print(atr,end=' ')               # 3 10 4
```





&#x20;

