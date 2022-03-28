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
