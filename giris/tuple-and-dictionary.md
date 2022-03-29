# Tuple and dictionary

Sequence types və mutability haqqında.

For ilə içində iterate edə bildiyimiz hər bir data tipi sequental data type sayılır. Məsələn, listlər. Listlər eyni zamanda mutable data type-dır. Yəni proqram işlədiyi müddətdə içi dəyişə bilər.

Proqram işlədiyi müddətdə içi dəyişə bilməyən tiplər də mövcuddur. Onlara immutable tiplər deyilir. Məsələn, tuple. Tuple-ı pythonda iki cür tanıda bilərik:

```
tuple_1 = (1, 2, 4, 8)
tuple_2 = 1., .5, .25, .125

print(tuple_1) # (1, 2, 4, 8)
print(tuple_2) # (1.0, 0.5, 0.25, 0.125)
```

Tuple-ın hər bir elementi başqa data tipinə aid ola bilər.

Tuple-ları tanımladarkən mütləq vergül işarəsindən istifadə etmək lazımdır. Tək elementi olan tuple-lar aşağıdakı formada təyin olunurlar. Nümunədən də göründüyü kimi 2-ci sətirdə vergül istifadə etmədiyim üçün 5-ci sətrin nəticəsi olaraq 9-cu sətirdə int tipi görsənib:

```python
test_1 = (1, )
test_2 = (1)

print(type(test_1))
print(type(test_2))

'''
<class 'tuple'>
<class 'int'>
'''
```

Tuple immutable (dəyişilməz) olduğu üçün aşağıdakı onu aşağıdakı kimi dəyişdirmək xəta çıxardacaq:

```
my_tuple.append(123)
del my_tuple[2]
my_tuple[1] = -5
```

Habelə, tuple-lar üzərində `+`,`*`,`len()`,`in`, `not in` əməliyyatları etmək mümkündür:

```python
my_tuple = (1, 10, 100)

t1 = my_tuple + (1000, 10000)
t2 = my_tuple * 3
t3 = t1 + t2

print(len(t2))              # 9
print(t1)                   # (1, 10, 100, 1000, 10000)
print(t2)                   # (1, 10, 100, 1, 10, 100, 1, 10, 100)
print(t3)                   # (1, 10, 100, 1000, 10000, 1, 10, 100, 1, 10, 100, 1, 10, 100)
print(10 in my_tuple)       # True
print(-10 not in my_tuple)  # True
```

## Dictionaries (lüğətlər)

Dəyərləri saxlaya biləcəyimiz digər bir data tipi isə lüğətlərdir. Python 3.6 versiyasından etibarən lüğətlər ordered (sequential) və mutable data tipləri sayılırlar. Lüğətlər {} fiqurlu mötərizələr vasitəsilə tanıdılır, key (açar) və value (dəyər)lərdən ibarət olurlar. Məsələn:

```python
nümunə_1 = {'maşın':'car', 'test':'test', 'kitab':'book'} # standart dictionary tanıtımı
nümunə_2 = {} # boş dictionary bu cür tanıdılır
nümunə_3 = {'Ali':1234, 'Mammad':12345, 'Aziz':123456, 'Orxan':'test'} # dictionary içində bir neçə fərqli data tipi ola bilər
nümunə_4 = {            # mürəkkkəb dictionary-ni alt-alta yazmaq daha rahatdır.
            '1':{'ad':'Ali', 'soyad':'aliyev'},
            '2':{'ad':'Mammad','soyad':'Mammadov'}
            }
# hər bir lüğətin necə çap olunduğuna baxaq
print(nümunə_1, nümunə_2, nümunə_3, nümunə_4)

print("\nnümunə_1 variable:")
for açarsöz in nümunə_1.keys():
    print(açarsöz + '->' + nümunə_1[açarsöz])

print("\nnümunə_4 variable:")
for açarsöz,dəyər in nümunə_4.items():
    for dəyər2 in dəyər.keys():
        print(açarsöz, dəyər2, dəyər[dəyər2])
```

Yuxarıdakı kod ekrana aşağıdakı nəticəni çap edəcək:

```python
{'maşın': 'car', 'test': 'test', 'kitab': 'book'} {} {'Ali': 1234, 'Mammad': 12345, 'Aziz': 123456, 'Orxan': 'test'} {'1': {'ad': 'Ali', 'soyad': 'aliyev'}, '2': {'ad': 'Mammad', 'soyad': 'Mammadov'}}

nümunə_1 variable:
maşın->car
test->test
kitab->book

nümunə_4 variable:
1 ad Ali
1 soyad aliyev
2 ad Mammad
2 soyad Mammadov
```

