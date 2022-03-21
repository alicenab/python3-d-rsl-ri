# ➕ riyazi hesablamalar

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

Pythonda həmçinin `4.` və `.3` kimi yazaraq da float rəqəmin və ya ədədin float tipində olduğunu başa düşmək mümkündür. `4.` `4.0` kimi, `.3` isə `0.3` kimi başa düşülür.



Python3.6-cı versiyasından etibarən böyük ədədlərin oxuna bilənliyini artırmaq məqsədilə ədədləri tanıdarkən \_ işarəsindən istifadə edilməsinə icazə verilir. Məsələn

```
print(1_234_567_89) # ekrana 123456789 cixardacaq
```

Octal (8-lik say sistemi) və Hexadecimal (16-lıq say sistemi)ndə olan ədədləri qeyd edərkən qarşısında müvafiq olaraq 0o (sıfır o) vəya 0x (sıfır x) qeyd etmək lazımdır. Məsələn

```
print(0x123) #ekrana 291 çıxardır
print(0o123) #ekrana 83 çıxardır
```









