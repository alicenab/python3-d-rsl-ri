# Tuple and dictionary

Sequence types və mutability haqqında, for ilə içində iterate edə bildiyimiz hər bir data tipi sequental data type sayılır. Məsələn listlər. Listlər həm də mutable data type-dır. Yəni proqram işlədiyi müddətdə içi dəyişə bilər. Tuple-lar adətən o zaman istifadə olunurlar ki, hər hansı bir listiniz və s. var onu proqram içində dəyişməsini istəmirsiz. Onu tuple() vasitəsilə tuple-a çevirirsiniz.

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

## Dictionary (lüğətlər)

Dictonary tipinin tuple tipindən fərqi ondadır ki, python 3.6 versiyasından etibarən, dictionary mutable tipdir. Yəni onun hansısa elementini proqramın gedişatı zamanı dəyişdirmək mümkündür. Dictionary-lər key və value-lardan ibarət olurlar. Məsələn aşağıdakı nümunəyə baxaq.

Tuple immutable (dəyişilməz) olduğu üçün aşağıdakı onu aşağıdakı kimi dəyişdirmək xəta çıxardacaq:

```
luget_1 = {'masin':'car', 'reng':'color', 'telefon':'telephone'}

print(luget_1)
print(luget_1.keys())
print(luget_1.values())

# lugetin key-inin silinmesi onunla bagli olan value-nun da silinmesine getirib cixarir.

del luget_1['reng']
print(luget_1)

# lugetin son elementini popitem() vasitesile silmek mumkundur.

luget_1.popitem()
print(luget_1)

# update vasitesile lugeti update etmek mumkundur
luget_1.update({'ses':'voice'})
print(luget_1)

luget_2 = luget_1.copy()
luget_2.clear()

print()
print(luget_1)
print(luget_2)
```

Yuxarıdakı kod parçası ekrana aşağıdakı nəticələri çap edəcəkdir.

```
{'masin': 'car', 'reng': 'color', 'telefon': 'telephone'}
dict_keys(['masin', 'reng', 'telefon'])
dict_values(['car', 'color', 'telephone'])
{'masin': 'car', 'telefon': 'telephone'}
{'masin': 'car'}
{'masin': 'car', 'ses': 'voice'}

{'masin': 'car', 'ses': 'voice'}
{}
```

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

# lüğətin spesifik elementini listlərdə olduğu kimi indekslər vasitəsilə olmasa da,
# key-lər vasitəsilə tapmaq olar. Məsələn:
print(nümunə_1['kitab']) # ekrana book çıxardacaq.
print(nümunə_4['1']['ad']) # ekrana Ali çıxardacaq.

print("\nKeylər:   " + str(nümunə_3.keys()))   #  
print("Valuelar: " + str(nümunə_3.values())) # 
print("İtemlər:  " + str(nümunə_3.items()))  #

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
book
Ali
Keylər:   dict_keys(['Ali', 'Mammad', 'Aziz', 'Orxan'])
Valuelar: dict_values([1234, 12345, 123456, 'test'])
İtemlər:  dict_items([('Ali', 1234), ('Mammad', 12345), ('Aziz', 123456), ('Orxan', 'test')])

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

Başqa bir nümunəyə baxaq:

```python
example = {'maşın':'car', 'test':'test', 'kitab':'book'}
# Lüğətin içindəki hər hansı dəyəri aşağıdakı formada dəyişmək mümkündür.
example['maşın'] = 'car2'
example['qələm'] = 'pen'
# Update metodu da həmin işə yararlıdır.
example.update({"kitab": "book2"})
example.update({"telefon": "telephone"})
print(example) # {'maşın': 'car2', 'test': 'test', 'kitab': 'book2', 'qələm': 'pen', 'telefon': 'telephone'}

# popitem vasitəsilə lüğətin son elementini silmək mümkündür
example.popitem()
print(example) # {'maşın': 'car2', 'test': 'test', 'kitab': 'book2', 'qələm': 'pen'}

# lüğətin spesifik elementini isə del açar sözü ilə silmək mümkündür
del example['maşın']
print(example) # {'test': 'test', 'kitab': 'book2', 'qələm': 'pen'}

example.clear()

# lüğətin içindəki itemləri clear() metodu vasitəsilə silmək mümkündür:
print(example) # {}
```







