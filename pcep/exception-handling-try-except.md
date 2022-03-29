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

Yuxarıda izah elədiyim xəta tipləri işlənmiş bir kod parçasına nəzər yetirək. Əgər istifadəçi sıfır daxil edərsə bu həm ValueError-un həm də ZeroDivisionError-un yaranmasına səbəb olacaq. Lakin kodun yazılışında ValueError birinci gəldiyi üçün istifadəçi sıfır daxil edərsə ekrana `Bad input...` yazısı çıxacaq:

```python
try:
    value = int(input("Enter a value: "))
    print(value/value)
except ValueError:
    print("Bad input...")
except ZeroDivisionError:
    print("Very bad input...")
except:
    print("Booo!")
```

Bir sətirdə eyni vaxtda iki xəta üçün də eyni kod yazmaq mümkündür. Məsələn aşağıdakı misala baxaq:

```python
while True:
    try:
        number = int(input("integer tipində bir dəyər daxil edin: "))
        print(5/number)
        break
    except (ValueError, ZeroDivisionError):
        print("Yalnış dəyər daxil olunub, və ya sıfıra bölmə xətası yaranıb.")
    except:
        print("Üzr istəyirik, bilinməyən bir xəta baş verdi.")
```



Proqramı debug etmək onun icrasını addım-addım izləyərək səhvlərin tapılmasına deyilir. İDE-lər (məsələn, visual studio code, pycharm, İDLE və s.) özləri debug alətlərinə sahib olurlar. Lakin uzun müddətdir işlədilən başqa bir debug metodu da var. Buna **print debugging** deyilir.&#x20;

Print debugging dedikdə proqramçının kodun müxtəlif hissələrində variable-ları print edərək kodun icrası zamanı variable-ların vəziyyətinə nəzarət etməsi başa düşülür.



