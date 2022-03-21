# ➕ sadə data tiplər

Python-da riyazi hesablamaları aparmaq üçün rəqəm və ədədləri əsasən üç data tipində təyin edirlər. integer, float və complex.

Complex ali riyaziyyatda istifadə olunduğu üçün bu haqqda danışmayacam.

integer və float data tiplərini bir-birindən fərqləndirən əsas xüsusiyyət integerin tam ədədlər üçün istifadə olunması, float data tipinin isə rasional ədədlər üçün istifadə olunmasıdır. Ədədlərin mənfi olduğunu bildirmək üçün qarşısına - işarəsi əlavə edilə bilər. Müsbət ədədlərin qarşısına + işarəsi əlavə etmək zəruri deyil, ancaq əlavə edilərsə də kod xətası olaraq qəbul edilmir.

Məsələn 23.1 (iyirmi üç tam onda bir) ədədini float tipində yadda saxlanılır. 23 (iyirmi üç) ədədi isə integer tipində yadda saxlanılır. Əgər əvvəlcədən float tipində olan bir ədəd integerə çevrilərsə python onu yuvarlaqlaşdırmır, nöqtədən sonrakı rəqəmləri silir. Məsələn.

```
print(int(23.1), int(23.4), int(-23.5), int(23.9))
```

Ekrana çıxan nəticə

```
23 23 -23 23
```

Pythonda həmçinin `4.` və `.3` kimi yazaraq da float rəqəmin və ya ədədin float tipində olduğunu başa düşmək mümkündür. `4.` `4.0` kimi, `.3` isə `0.3` kimi başa düşülür. Məntiqli olaraq əgər pythondan soruşsanız ki `4.0` `4`-ə bərabərdirmi, deyəcək ki bərabərdir. Məlumat üçün deyirəm ki,  bu bəzi proqramlaşdırma dillərində belə deyil.

```
print(4. == 4)    #ekrana True çıxardacaq.
```



Python3.6-cı versiyasından etibarən böyük ədədlərin oxuna bilənliyini artırmaq məqsədilə ədədləri tanıdarkən \_ işarəsindən istifadə edilməsinə icazə verilir. Məsələn

```
print(1_234_567_89) # ekrana 123456789 cixardacaq
```

Octal (8-lik say sistemi) və Hexadecimal (16-lıq say sistemi)ndə olan ədədləri qeyd edərkən qarşısında müvafiq olaraq 0o (sıfır o) vəya 0x (sıfır x) qeyd etmək lazımdır. Məsələn

```
print(0x123) #ekrana 291 çıxardır
print(0o123) #ekrana 83 çıxardır
```

print() funksiyası ekrana həmişə daha oxunaqlı yazı çap etdiyi üçün,  böyük ədədləri (məsələn, 3.14 vurulsun 10 üstü 20) göstərərkən E hərfindən istifadə edir. Böyük ədədlər təyin edilərkən 10 üstü olan rəqəmlər (exponent value) integer tipində olmalıdır. Lakin vurulduğu ədəd (base value) rasional ola bilər. Məsələn

```
print(3.14*10**20)  #ekrana 3.14e+20 çıxardır
```

Digər proqramlaşdırma dillərində olduğu kimi python-da da bir şeyin doğruluğunu yoxlamaq məqsədilə **boolean** dan istifadə olunur. `True` və ya `False`

Həmin dəyişənlər **case-sensitive**-dir. Yəni TRUE vəya false yazsanız başqa yerə müraciət etmiş sayılacaqsınız.

Komputerlər hərşeyi rəqəmsal olaraq yadda saxladıqları üçün, True 1 rəqəmi ilə, False isə 0 rəqəmi ilə ifadə olunur. Dolayısıyla rəqəmsal hesablama zamanı True False-dan böyükdür.

```
print(True>False) # Ekrana True çıxardacaq.
```

Əlavə olaraq pythonda yoxluğu bildirən bir data tipi də mövcuddur. Bu `None` adlanır. Birşeyin olub olamamsını None ilə yoxlamaq mümkündür. Həmçinin bir müvəqqəti olaraq hansısa dəyişəni təyin etmək lazımdırsa və ona hansı dəyəri təyin edəcəyinizi bilmirsinizsə, həmin dəyişənə `None` dəyərini təyin edə bilərsiniz.





