---
description: Data tiplərinin birindən digərinə çevrilməsi.
---

# Type casting

Type casting dedikdə python-da data tipinin dəyişilməsi başa düşülür. Məsələn.

```
a = 4
b = 2.0
c = '3'
print (a, b, c*a)
a = float(a) # 4 çevrilib 4.0 oldu
b = int(b)   # 2.0 çevrilib 2 oldu
c = int(c)   # string tipindəki 3 çevrilib integer tipindəki 3 oldu.
print(a, b, c*a)
```

Yuxarıdakı kod parçası ekrana aşağıdakı nəticəni çıxardacaq.

```
4 2.0 3333
4.0 2 12.0
```





