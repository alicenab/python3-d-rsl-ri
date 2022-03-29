# Lists

Aşağıdakı kod nümunəsinə baxaq

```python
meyvələr = ['alma', 'armud', 'heyva']
qiymətlər = [23,33,43]

print(meyvələr)
print(qiymətlər)

# Hər hansı siyahının uzunluğunu len() funksiyası ilə tapmaq mümkündür
print("Meyvələr list-inin uzunluğu: ", len(meyvələr),
      "\nƏdədlər list-inin uzunluğu: ", len(qiymətlər))

# List-in n-ci elementini onun həmin listdəki indeksini yazaraq əldə edə bilərik.
print(meyvələr[0], qiymətlər[2])
```

Listi birbaşa olaraq digər variable-a tanıtdığımız zaman, onun RAMdakı adresi referans götürüldüyü üçün (pointer məntiqi) hər iki list eyni olur.

```
list_1 = [1]
list_2 = list_1
list_1[0] = 2
print(list_2) #cavab 2
```

Aşağıdakı misalda iki list isə fərqli addressdir, çünki birbaşa özünü yox, bütün elementlərini kopyalamışıq:

```
list_1 = [1]
list_2 = list_1[:]
list_1[0] = 2
print(list_2) #cavab 1
```

List slicing dedikdə list-in öz istədiyimiz indeks aralığını təyin etmək başa düşülür

```
my_list = [10, 8, 6, 4, 2]
new_list = my_list[1:3]
print(new_list)
```

List slicing mənfi ədədlərlə də olur. Ancaq aşağıda son dəyər ilk dəyərdən böyük olduğu üçün ekrana empty list çıxacaq, ikinci printdə isə sol dəyər sağdan kiçik olduğu üçün ekrana nəticə çıxacaq:

```python
my_list = [10, 8, 6, 4, 2]
# indeks -  0, 1, 2, 3, 4
# indeks - -5,-4,-3,-2,-1
new_list = my_list[-1:-3]
print(new_list) # cavab: []

new_list = my_list[-3:-1]
print(new_list) # cavab: [6, 4]
```

Slicing-də sol tərəf göstərilməzsə, listin başlanğıcı, sağ tərəf göstərilmədikdə isə listin sonu nəzərdə tutulur. Heç bir tərəf göstərilməzsə, bütün list nəzərdə tutulur:

```python
my_list = [10, 8, 6, 4, 2]
print(my_list[3:])   # siyahının 3-cü indeksindən sonrakı dəyərləri əhatə edir
print(my_list[:3])   # siyahının 3-cü indeksindən əvvəlki və üçüncü indeksindəki dəyərləri əhatə edir.

del my_list[:]       # siyahının bütün indekslərindəki elementləri silir.
my_list.append(1)    # siyahıya sıfırıncı elementdən 1 dəyərini daxil edir.
print(my_list)

# .insert vasitəsilə siyahının istədiyimiz indeksinə istədiyimiz dəyəri daxil edə bilərik.
my_list.insert(0,0)  # sıfırıncı indeksə 0 dəyərini daxil et
my_list.insert(0,-1) # sıfırncı indeksə -1 dəyərini daxil et. (bundan qabaqki dəyərlər sağa sürüşür)
my_list.insert(3,2)  # üçüncü indeksə 2 dəyərini daxil et
print(my_list)       # [-1, 0, 1, 2]
 
del my_list          # my_list siyahısını silir.
print(my_list)

# Ekrana çıxacaq:
'''
[4, 2]
[10, 8, 6]
[1]
[-1, 0, 1, 2]
Traceback (most recent call last):
  File "c:\Users\alicenab\Desktop\test.py", line 16, in <module>
    print(my_list)
NameError: name 'my_list' is not defined
'''
```

in və not in açar sözləri hər hansı elementin siyahının içində olub-olmamasını təyin etmək üçün işlədilir. Məsələn:

```
my_list = [0, 1, 2, 3, 4]

print(5 not in my_list) # True
print(1 in my_list)     # True
```

## Multidimentional lists (Çoxölçülü siyahılar)

Hər hansı elementinin içində list saxlayan listlərə çoxölçülü listlər deyilir. Məsələn.

```python
# 2 elementi, hər elementinin isə özlüyündə 3 elementi olan çoxölçülü siyahı
my_list = [[1,2,3],[4,5,6]]
print(my_list)

# siyahının ilkin 2 elementi üzrə dəyərlərin ekrana çap olunması
for i in my_list:
    print(i)

# siyahının dərin elementlərinin ekrana çap olunması
for i in my_list:
    for j in i:
        print(j,end=' ')
    print()
```

Təsəvvür edin ki, 8-in 8-ə ölçüsündə şahmat taxtasını kodlaşdırmaq istəyirsiniz. İçində 8 ədəd simvol olan stringi ekrana yeni sətirdən 8 dəfə çap etsəniz hansısa nəticəni əldə edə bilərsiniz. Ancaq daha qısa yollar da var. Məsələn 8 ədəd X hərfini ekrana aşağıdakı kimi çap etmək mümkündür.&#x20;

```python
setir = []

for i in range(8):
    setir.append("X")

print(setir)
# Ekrana cap edecek:
# ['X', 'X', 'X', 'X', 'X', 'X', 'X', 'X']
```

Bu kimi situasiyalar üçün list comprehension deyilən bir metoddan istifadə olunur ki, kod daha effektiv olsun. Məsələn, aşağıdakı kod yuxarıdakı ilə eyni əhəmiyyət kəsb edir:

```python
setir = ['X' for i in range(8)]
print(setir)

# Ekrana çap edəcək:
# ['X', 'X', 'X', 'X', 'X', 'X', 'X', 'X']
```

Bu məntiqlə şahmat taxtasına şah fiqurlarını aşağıdakı formada əlavə etmək mümkündür:

```python
masa = [['x' for i in range(8)] for j in range(8)]
sah = 'S'

masa[0][3] = sah
masa[7][3] = sah

for setir in masa:
    print(setir)

'''
Ekrana çap olunacaq:

['x', 'x', 'x', 'S', 'x', 'x', 'x', 'x']
['x', 'x', 'x', 'x', 'x', 'x', 'x', 'x']
['x', 'x', 'x', 'x', 'x', 'x', 'x', 'x']
['x', 'x', 'x', 'x', 'x', 'x', 'x', 'x']
['x', 'x', 'x', 'x', 'x', 'x', 'x', 'x']
['x', 'x', 'x', 'x', 'x', 'x', 'x', 'x']
['x', 'x', 'x', 'x', 'x', 'x', 'x', 'x']
['x', 'x', 'x', 'S', 'x', 'x', 'x', 'x']
'''
```

Başqa bir nümunəyə baxaq. Aşağıdakı kodun birinci sətrində 10-a dək olan rəqəmlərin kvadratlarından ibarət olan list kvadratlar adındakı dəyişənə tanımlanır. 3-cü sətirdə isə kvadratlar listinin içindəki hansı element ikiyə bölündükdə qalıqda sıfır qalarsa, həmin elementlər tek\_kvadratlar adındakı dəyişənə tanımlanır:

```python
kvadratlar = [x ** 2 for x in range(10)]
print(kvadratlar)
tək_kvadratlar = [x for x in kvadratlar if x % 2 != 0 ]
print(tək_kvadratlar)
```

Üçölçülü siyahıya misal:

```
kubik = [[['x' for x in range(3)] for y in range(3)] for z in range(3)]
print(kubik)
# Ekrana aşağıdakı nəticəni çap edəcək:
# [[['x', 'x', 'x'], ['x', 'x', 'x'], ['x', 'x', 'x']], [['x', 'x', 'x'], ['x', 'x', 'x'], ['x', 'x', 'x']], [['x', 'x', 'x'], ['x', 'x', 'x'], ['x', 'x', 'x']]]
```



