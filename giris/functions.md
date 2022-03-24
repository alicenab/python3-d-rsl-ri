# Functions

```
def add_numbers(a, b=2, c):
    print(a + b + c)

add_numbers(a=1, c=3)
```

1-ci sətirdə default argumentdən sonra non default argument gəlməyi syntax error sayılır.

variable shadowing, öz içində təyin olunmasa belə funksiyalar global variable-ları tanıyırlar. Əgər global variable ilə eyni adda funksiya daxilində də variable olarsa, funksiya daxilindəki variable dəyəri əsas götürülür. bu variable shadowing adlanir.

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



