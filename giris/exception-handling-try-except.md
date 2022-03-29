# Exception handling (try-except)

Böyük ehtimalla indiyədək hansısa proqramı istifadə etdikdə qarşılaşdığınız xətaya baxıb demisiniz ki, "bu nə deməkdir". Adətən kodda hər hansı bir xəta olduqda proqram fəaliyyətini dayandıraraq ekrana istifadəçi tərəfindən başa düşülməsi çətin olan texniki bir xəta verir.

Proqramist kimi koddakı xətalardan yayınmaq yerinə onları tapıb aradan qaldırmaq daha faydalıdır. Xəta baş verən anda proqramın özünün necə aparması haqqında bu səhifədə, yəni [exception-handling-try-except.md](exception-handling-try-except.md "mention") səhifəsində danışacam. Ən sadə try-except kod kaskadı aşağıdakı kimidir.

```python
try:
	print("Bu hissədə normal kodlar olur")
except:
	print("Try içindəki kodda xəta baş verərsə except içindəki kod işə düşür")

# Ekrana çıxan nəticə:
# Bu hissədə normal kodlar olur
```

Proqramçı spesifik olaraq hansısa xəta tipi baş verdiyi zaman proqramın özünü necə aparmasını kodlaşdıra bilər. Bunun üçün python bir neçə xəta tipini əvvəlcədən tanıdıb. Onlardan bəziləri aşağıdakılardır:&#x20;

**`ZeroDivisionError`**` ``-` `/`, `//`, və `%` hesablama operatorları tərəfindən sıfıra bölmə halı aşkarlandığı halda yaranır.\
**`TypeError`**` ``-` Data tiplər bir birinə uyğun olmadığı halda yaranır. Məsələn int() tipindəki məlumatın str() tipi ilə birləşdirilməyə çalışılması.\
**`AttributeError`**` ``-` Olmayan bir metodu işlətməyə çalışdığımız zaman baş verir. Məsələn listlərin depend() metodu olmadığı halda, `my_list.depend(3)` yazsaq.\
**`NameError`**` ``-` Müraciət olunmağa çalışan variable tapılmadığı halında baş verir.



Python bəzən proqramçının buraxdığı səhvləri görmür. Məsələn, aşağıdakı kod parçasında 6-cı sətirdə print() yerinə prin() yazılmasına baxmayaraq istifadəçi kod işə düşdükdən sonra sıfırdan kiçik ədəd daxil etməzsə kod heç vaxt 5-ci sətirdəki şərtə uyğun gəlmədiyi üçün python 6-cı sətirdəki səhvi tapmayacaq:

```python
temperatur = float(input('Temperaturu daxil edin:'))

if temperatur > 0:
    print("Above zero")
elif temperatur < 0:
    prin("Below zero")
else:
    print("Zero")
```

Proqramı debug etmək onun icrasını addım-addım izləyərək səhvlərin tapılmasına deyilir. İDE-lər (məsələn, visual studio code, pycharm, İDLE və s.) özləri debug alətlərinə sahib olurlar. Lakin uzun müddətdir işlədilən başqa bir debug metodu da var. Buna **print debugging** deyilir.&#x20;

Print debugging dedikdə proqramçının kodun müxtəlif hissələrində variable-ları print edərək kodun icrası zamanı variable-ların vəziyyətinə nəzarət etməsi başa düşülür.



