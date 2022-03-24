---
description: >-
  Bu yazıda integer və float ədədlər üzərində praktiki sadə hesablama
  əməliyyatları ilə tanış olacaqsınız.
---

# sadə riyazi hesablamalar

Hesablamalar zamanı iki şeyə diqqət yetirmək lazımdır:

1\) Əgər sağ və sol tərəfdəki dəyərlər integer tipində olarsa, nəticə də integer tipində olacaq. Əgər sağ və ya sol tərəfdən biri və ya hər ikisi float tipində olarsa, bu zaman nəticə də float tipində olacaq. Bundan sonra bunu məqalədə integer və float qaydası adlandıracağıq.

2\) Sıfırı istənilən ədədə bölə bilərik, lakin bunun əksi mümkün deyil. İstənilən ədədi sıfıra bölsək, bu zaman xəta baş verəcək. Bu, integer division və remainder division-a da aiddir.



**Unary** və **binary** operatorlar nədir

Aydındır ki `+` və `-` işarələri toplama və çıxma hesablamaları üçün istifadə olunduqda binary operator;

Bir ədədin xüsusiyyəti (indiki halda müsbət və ya mənfi olduğunu) göstərmək üçün istifadə edildikdə isə **unary** operator adlandırılırlar;&#x20;

Hesablama məqsədilə (sağında və solunda dəyər olduqda) işlədildikdə isə **binary** operator adlandırılırlar.

Bu qayda digər işarələrə də aiddir. Gələcəkdə həmin işarələrin başqa hansı məqsədlərlə istifadə olunmasını öyrənəcəyik.





`+`, toplama üçündür,

integer və float qaydasına tabedir.

\
`-`, çıxma üçündür,

integer və float qaydasına tabedir.

\
`*`, **multiplication operator** adlanır, vurma üçündür&#x20;,

integer və float qaydasına tabedir.



\
`/`, **divisional** operator adlanır, sol tərəf dividend, sağ tərəf isə divisor adlanır.

İstənilən halda hər bir bölmə əməliyyatının nəticəsi float tipində olur. Sıfıra bölmə zamanı xəta baş verir.

\
`//`, **integer divisional** operator adlanır. Digər adı **floor divisional**dır. Nəticə olaraq aldığı dəyər **quotient** adlanır, integer və float qaydasına riayət edir. Sıfıra bölmə zamanı xəta baş verir. Normal bölmə əməliyyatından iki xüsusiyyətinə görə fərqlənir:

1\) Bölmə hesablamaları zamanı qalıq hissəni silir, əsas cavabı nəticə kimi təqdim edir;\
2\) cavabı yuvarlaqlaşdırır, yuvarlaqlaşdırma zamanı ən aşağı dəyərli integerə çatmağa yönəlir.

Dolayısıyla aşağıdakı kodun nəticəsi `-2.0` olacaq. Çünki əsl cavab -1.5 olsa da, // standart olaraq bütün cavabları yuvarlaqlaşdırdığı üçün, həm də yuvarlaqlaşdırma zamanı aşağı dəyərə yönəldiyi üçün nəticə `-1.5` dən daha aşağı olan `-2.0` götürüləcək.

```python
print(6. // -4)
```



\
`%`, **remainder (modulo)** operatoru adlanır. Bölmə əməliyyatından alınan qalığı hesablamaq üçündür. Sıfıra bölmə zamanı xəta baş verir.

Aşağıdakı kodun hesablanma qaydası izah olunmuşdur. 

```
print(14 % 4)
```

* `14 // 4` cavab `3` →  **quotient**;
* `3 * 4` cavab `12` →  **quotient** və **divisor** hasili;
* `14 - 12` cavab `2` →  **remainder**-i əldə etdik.

Qeyd. `0%3` kimi hesablamaların cavabı 3-dür.





\
`**`**exponentiation (power) operator** adlanır, sol tərəfindəki arqument (ədəd) **base**, sağ tərəfindəki arqument isə **exponent** adlanır.

integer və float qaydasına riayət edir. **base** hissə integer tipində olmaya bilər, **exponent** hissə mütləq integer olmalıdır.

Mürəkkəb formullarda sağdan sola hesablanan tək operatordur. Məsələn:

```
print(2 ** 2 ** 3)
```

Hesablamanı soldan sağa apardığımız halda ilk olaraq göstərilən formada davam etməli idik.

* `2 ** 2` → `4`; `4 ** 3` → `64`
* `2 ** 3` → `8`; `2 ** 8` → `256`

Ancaq python-da hesablama göstərilən ikinci üsulla hesablanır və nəticə 256 olur.



Mürəkkəb hesablamalar zamanı bəzən hansı hesablamanın birinci icra ediləcəyini bilməmək səhv nəticələrə gətirib çıxara bilər. Xatırlayırsınızsa, riyaziyyatda həm toplamanın, həm də  vurmanın olduğu hesablamalarda ilkin olaraq vurma, daha sonra toplama əməliyyatnını icra olunması qaydası öyrədilir.&#x20;

| Priority | Operator            | Tipi   |
| -------- | ------------------- | ------ |
| 1        | `+`, `-`            | unary  |
| 2        | `**`                |        |
| 3        | `*`, `/`, `//`, `%` |        |
| 4        | `+`, `-`            | binary |

Hesablamalar zamanı əlavə mötərizələrdən də istifadə oluna bilər. Məsələn:

```
print((5 * ((25 % 13) + 100) / (2 * 13)) // 2)
```

Cavab `10.0` olacaqdır.
