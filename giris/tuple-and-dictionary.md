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





