# Conditional operators (if,elif,else)

Pythonda şərtlərdən istifadə etmək sadədir. Məsələn tutalım ki, bir obyektiniz var və 18 yaşı tamam olmuş və ya ötmüş şəxsləri içəri almaq lazım olan kod parçası yazmaq lazımdır. Kodun strukturu bu şəkildə olacaq.

Şərtləri əmələ gətirən əsas keyword-lər bunlardır. `if`, `elif`, `else` **.**

else-dən və elif-dən istifadə etmək məcburi sayılmır. Bir şərt kodu təkcə if ilə əmələ gələ bilər.

else istifadə olunarsa həmişə şərt kodunun son elementi olmalıdır. else işlənmədiyi şərt kodu kaskadında ola bilər ki, situasiya heç bir şərtə uyğun olmasın. Ancaq else işlənərsə, else-dən yuxarıdakı situasiyalar doğru olmadığı halda mütləq else içindəki kod işə düşür.

```python
'''
Yaş üçün şərt qoyuruqsa bilməliyik ki,
Yaş 18 və 18-dən böyük olarsa girişə icazə verəcəyik.
Yaş 18-dən kiçik olarsa buna icazə verməyəcəyik.
'''

yas = int(input("Yasinizi daxil edin: "))

if yas>18: #yaş 18-dən böyük olarsa
    print("Daxil ola bilersiniz.")
elif yas==18: #yaş 18-ə bərabər olarsa
    print("Daxil ola bilersiniz.")
else: # digər halları əhatə edir, (bu halda 18-dən kiçik olacaq)
    print("Giris ucun yasiniz kifayet deyil")
```

Bəs yuxarıdakı kodu daha səmərəli yazmaq olmazdımı, olardı əlbətdə. Ancaq sırf elif keyword-ünün istifadəsini göstərmək üçün birinci növbədə o cür yazdım.

```python
'''
Yaş üçün şərt qoyuruqsa bilməliyik ki,
Yaş 18 və 18-dən böyük olarsa girişə icazə verəcəyik.
Yaş 18-dən kiçik olarsa buna icazə verməyəcəyik.
'''

yas = int(input("Yasinizi daxil edin: "))

if yas>=18: #yaşın 18-dən böyük və ya ona bərabər olduğu hallarda
    print("Daxil ola bilersiniz.")
else: #digər hallarda, (indiki nümunədə 18-dən kiçik olduğu hallar)
    print("Giris ucun yasiniz kifayet deyil")
```

Yeni başlayan şəxslər adətən `=` ilə `==` çaşdırırlar. `=` variable assignment zamanı istifadə olunur. `==` isə bərabərliyi yoxlamaq məqsədilə istifadə olunur. Məhz buna görə də, bu iki fərqli situasiyanı bir-biri ilə qarışdırmaq olmaz.

| şərtləndirmələr | mənaları                                                                   |
| --------------- | -------------------------------------------------------------------------- |
| x\<y            | x, y-dən kiçik olarsa True, olmazsa False cavabı verir.                    |
| x<=y            | x, y-dən kiçik, və ya y-ə bərabər olarsa True, olmazsa False cavabı verir. |
| x>y             | x, y-dən böyük olarsa True, olmazsa False cavabı verir.                    |
| x>=y            | x, y-dən böyük, və ya y-ə bərabər olarsa True, olmazsa False cavabı verir. |
| x==y            | x, y-ə bərabər olarsa True, olmazsa False cavabı verir.                    |
| x!=y            | x, y-ə bərabər olmazsa True, olarsa False cavabı verir.                    |

Xatırlıyırsınızsa operatorların prioritetləri haqqında danışmışdıq, şərt operatorları daha aşağı prioritetə sahibdirlər.

| Prioritet | Operator             |        |
| --------- | -------------------- | ------ |
| 1         | `+`, `-`             | unary  |
| 2         | `**`                 |        |
| 3         | `*`, `/`, `//`, `%`  |        |
| 4         | `+`, `-`             | binary |
| 5         | `<`, `<=`, `>`, `>=` |        |
| 6         | `==`, `!=`           |        |

Mürəkkəb şərt kaskadları.

```python
x = "1"

if x == 1:
    print("bir")
elif x == "1":
    if int(x) > 1:
        print("iki")
    elif int(x) < 1:
        print("uc")
    else:
        print("dord")
if int(x) == 1:
    print("five")
else:
    print("six")
    
'''
Ekrana çap olunan nəticə.

dord
bes
'''
```

Koda diqqətlə baxaq, birinci sətirdə x-ə string tipində 1 rəqəmi təyin etmişik.\
Üçüncü sətirdə x-in integer tipindəki 1-lə bərabər olması yoxlanılır string yox. Ona görə də üçüncü sətirdəki şərt ödənmədiyi üçün 5-ci sətirdəki `elif` şərti yoxlanılır, `x == "1"` x həqiqətən string tipində 1-ə bərabər olduğu üçün 6-11-ci sətirlər arasındakı kaskada keçid edirik. 6 və 8-ci sətirdəki şərtlər ödənmədiyinə görə 11-ci sətirdəki kod işə düşür və ekrana `dord` yazısı çıxır.

Bundan sonra isə 12-ci sətirdə `int()` type casting olunmuş 1 rəqəminin integer tipindəki 1 ilə eyniliyi yoxlanılır. Eyni olduğuna görə ekrana `bes` çap olunur. 14-cü sətirdəki else 12-ci sətirdəki if-in olduğuna görə mahiyyətini itirir və proqram başa çatır.



