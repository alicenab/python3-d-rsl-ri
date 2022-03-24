# Lists

Listlər pointer məntiqi ilə işləyir. Aşağıdakı misalda iki list eyni addressdir:

```
list_1 = [1]
list_2 = list_1
list_1[0] = 2
print(list_2)
```

Aşağıdakı misalda iki list isə fərqli addressdir:

```
list_1 = [1]
list_2 = list_1[:]
list_1[0] = 2
print(list_2)
```

List slicing - başlanğıc dəyərdən son dəyər -1-ə kimi.

```
my_list = [10, 8, 6, 4, 2]
new_list = my_list[1:3]
print(new_list)
```

List slicing mənfi ədədlərlə də olur. Ancaq aşağıda son dəyər ilk dəyərdən böyük olduğu üçün ekrana empty list çıxacaq:

```
my_list = [10, 8, 6, 4, 2]
new_list = my_list[-1:-3]
print(new_list)
```

Slicing-də sol tərəf göstərilməzsə, listin başlanğıcı, sağ tərəf göstərilmədikdə isə listin sonu nəzərdə tutulur. Heç bir tərəf göstərilməzsə, bütün list nəzərdə tutulur:

```python
my_list = [10, 8, 6, 4, 2]
print(my_list[3:])
print(my_list[:3])

del my_list[:]
my_list.append(1)
print(my_list)

del my_list
print(my_list)

# Ekrana çıxacaq:
'''
[4, 2]
[10, 8, 6]
[1]
Traceback (most recent call last):
  File "kod.py", line 10, in <module>
    print(my_list)
NameError: name 'my_list' is not defined

'''
```

in və not in açar sözləri.

```
my_list = [0, 1, 2, 3, 4]

print(5 not in my_list)
print(1 in my_list)
```

