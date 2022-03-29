# easy level string manipulation

Yeni başlayanlar üçün rahat olsun deyə stringlərlə iş üzrə çox sadə izah verməyə çalışacam

iki fərqli stringi bir birinə birləşdirmək (**concatinte**) üçün `+` işarəsindən istifadə edə bilərsiniz. Məsələn

```
a='Salam'
b='necesiniz?'
print(a+b)
```

Yuxarıdakı kod ekrana `Salamnecesiniz?` çıxardacaq. arada boşluq olması üçün yuxarıdakı kodun üçüncü sətrini aşağıdakı ilə dəyişmək lazımdır.

```
print(a+' '+b)
```

`+` işarəsinin **concatination** (birləşdirici) funksiyasını yerinə yetirməsi üçün, + işarəsinin sağ və sol tərəfləri string olmalıdır.

## String replication

Bir stringi X qədər çoxaltmağa string replication deyilir. Bu aşağıdakı formada icra olunur.

```
print('a'*3)    # ekrana aaa çıxardır
print('ab'*3)   # ekrana ababab çıxardır
print('abc'*0)  # ekrana boş string çıxardır
print('b'*-1)   # ekrana boş string çıxardır
```







