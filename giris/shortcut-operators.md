# Shortcut operators

Xatırlıyırsınızsa, aritmetik operatorları sadalamışdıq. (bax.  [sad-riyazi-hesablamalar.md](sad-riyazi-hesablamalar.md "mention"))

Bəzi hesablamalar zamanı bu operatorları qısa şəkildə yazmaq da mümkündür. Məsələn

```python
yas=17
print(yas) # ekrana 17 çıxır
yas = yas + 1
print(yas) # erkana 18 çıxır
yas += 1
print(yas) # ekrana 19 çıxır
```

Python proqramlaşdırma dilində `yas=yas+1` ilə `yas+=1` eyni cür başa düşülür. Digər operatorlar da həmçinin bu  cür istifadə oluna bilərlər. Məsələn aşağıdakı yazılışlar düzgündür.

`i = i + 2 * j` ⇒ `i`` ``+=`` ``2 * j`

`var = var / 2` ⇒ `var`` ``/=`` ``2`

`rem = rem % 10` ⇒ `rem`` ``%=`` ``10`

`j = j - (i + var + rem)` ⇒ `j`` ``-=`` ``(i + var + rem)`

`x = x ** 2` ⇒ `x`` ``**=`` ``2`







