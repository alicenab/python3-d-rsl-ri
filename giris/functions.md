# Functions (funksiyalar)





Funksiyalar sizin funksiya daxilində yazdığınız kodu icra edib cavabını qaytaran kod parçlarıdır. Yaradılış məqsədi kod təkrarının qarşısını almaqdır. Standart funksiya istifadəsi aşağıdakı şəkildədir:

```
nəticə = funksiyanın_adı(funksiyanın_arqumenti)
```

Funksiyanı yaratmaq üçün lazım olan minimal kod aşağıdakı kimidir:

```
def funksiyanın_adı():
    pass
```

python interpreteri işə düşdükdə pass kəliməsini gördükdə başa düşür ki, heçnə icra etmək lazım deyil və olduğu kimi davam edir. Yuxarıdakı misal o zaman proqramistlər tərəfindən istifadə olunur ki, hansısa funksiya yazmağa qərar versələr də onun hansı işlər görəcəyini hələ dəqiqləşdirmirlər. Funksiya yaratmaq fikri ağıldan çıxmasın deyə yuxarıdaki kimi qeyd edirlər.

Funksiyanın arqumenti olmaya da bilər, bir arqumenti də ola bilər, 1-dən çox arqumenti də ola bilər. Funksiya daxilində işlənmiş dəyişənlər funksiyanın lokal dəyişənləri (local variables) adlanırlar. Funksiyanın xaricində işlədilmiş dəyişənlər isə (0 indentation level) global variable adlanırlar. Funksiyalar adətən return açar sözü vasitəsilə nəticəni geri qaytarırlar. Çox söz deyib heç bir məna verməyən insanlar kimi, içində return açar sözü olmayan funksiyalar  return açar sözü işlənmiş hər bir funksiyanı 5-ci sətirdəki kimi hansısa variable-a təyin etmək mümkündür. Aşağıdakı kodu ətraflı nəzərdən keçirək.

1-ci sətirdə topla adında funksiya yaratmışam və qeyd etmişəm ki default olaraq bu funksiya 2 arqument qəbul edəcək və funksiyaya daxil olan arqumentləri müvəqqəti olaraq sag və sol adlandırmaq olar.

2-ci sətirdə topla funksiyasına daxil edilmiş sag və sol adındakı arqumentləri toplayaraq funksiya daxilində cavab adında bir variable-a təyin etmişəm.

3-cü sətirdə cavab variable-ını return etmişəm. Yəni funksiya öz işini tamamladıqdan sonra cavab dəyişənini geri qaytaracaq.

5-ci sətirdə nəticə adlı global variable-a topla(3,7) tanıtmışam. 6-cı sətirdə isə nəticə dəyişənini ekrana çap etdirmişəm.

```
def topla(sag,sol):
    cavab = sag+sol
    return cavab

nəticə = topla(3,7)
print(nəticə) #ekrana 10 çap ediləcək.
```

Funksiyalar default arqument qəbul edə bilərlər. Bu arqumentlərdən birinin daxil olunmaq istənilmədiyi vaxtlarda köməyə çatır. Məsələn:

```python
def topla(sag,sol=3):
    cavab = sag+sol
    return cavab

nəticə = topla(3)
print(nəticə) #ekrana 6 çap edəcək.

nəticə = topla(3,3)
print(nəticə) #ekrana 6 çap edəcək.
```

Default arqumentləri kodlaşdırarkən diqqət etmək lazımdır ki, default arqumentlər həmişə digər arqumentlərdən sonda, yəni sağ tərəfdə yazılmalıdır. Default arqumentdən sonra adi arqument gəlməsi kodda xətaya səbəb olur.

```python
def add_numbers(a, b=2, c):
    print(a + b + c)

add_numbers(a=1, c=3)
```

1-ci sətirdə default argumentdən sonra non default argument gəlməyi syntax error sayılır.

**Variable shadowing**, öz içində təyin olunmasa belə funksiyalar global variable-ları tanıyırlar. Əgər global variable ilə eyni adda funksiya daxilində də variable olarsa, funksiya daxilindəki variable dəyəri əsas götürülür. bu variable shadowing adlanir.

```
def my_function():
    #var = 2
    print("Do I know that variable?", var)


var = 1
my_function()
print(var)

'''
Do I know that variable? 1
1
'''
```

funksiya daxilindən kənardakı dəyişənə təsir etmək üçün global sözündən istifadə etmək lazımdır.

```
def my_function():
    global var
    var = 2
    print("Do I know that variable?", var)

var = 1
my_function()
print(var)
```

Global səviyyədə (0 indentation) funksiya daxilindəki variable-ı çağırmaq istəyəndə typeerror verir.

Özü özünü çağıran funksiyalara rekursiv funksiyalar deyilir

```
```











