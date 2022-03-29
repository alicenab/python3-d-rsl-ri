# print() funksiyası

print() funksiyası özünə daxil edilmiş obyektləri insanın başa düşə biləcəyi formada çıxış cihazına (bu əsasən terminal olur) ötürən funksiyaya deyilir.

Mötərizənin içində vergüllə ayrılmış hər bir obyekt funksiyanın arqumentləri sayılır.

Gəlin aşağıdakı nümunəyə baxaq:

```python
print("Cut dirnaq icinde 'tek dirnaq' istifade etmek mumkundur")
print('Bunun "eksi" de dogrudur.')
print("Eyni dirnaqlari istifade etmek ucun \"escape character\"-dan (backslash) istifade etmek lazimdir.")
print("Backslash-in ozunu ekrana vermek ucun iki defe backlash '\\' istifade edilmelidir.")
print("Default olaraq ekrana cap olunan setrin sonu newline '\\n' ile bitir.")
print('Buna gore indiyedek butun printler yeni setirden basladi.')
print('bundan sonraki cumle ise yeni setirden baslamayacaq',end=' ')
print("Cunki end parametri ile setirin ne ile biteceyini deyisdirdik.")
print('sep vasitesi ile ekrana yazdiginiz bir nece seyin arasini bosluqdan basqa seylerle doldura bilersiniz')
print("meselen","bu","cumle","yeni","setirden","baslayacaq",sep='-')
print('printin', 'icinde', 'de','\nyeni', 'setirden', 'basla\tmaq', 'mumkundur',sep='__',end='!!!')
```

Ekrana çıxan nəticə.

```
Cut dirnaq icinde 'tek dirnaq' istifade etmek mumkundur
Bunun "eksi" de dogrudur.
Eyni dirnaqlari istifade etmek ucun "escape character"-dan (backslash) istifade etmek lazimdir.
Backslash-in ozunu ekrana vermek ucun iki defe backlash '\' istifade edilmelidir.
Default olaraq ekrana cap olunan setrin sonu newline '\n' ile bitir.
Buna gore indiyedek butun printler yeni setirden basladi.
bundan sonraki cumle ise yeni setirden baslamayacaq Cunki end parametri ile setirin ne ile biteceyini deyisdirdik.
sep vasitesi ile ekrana yazdiginiz bir nece seyin arasini bosluqdan basqa seylerle doldura bilersiniz
meselen-bu-cumle-yeni-setirden-baslayacaq
printin__icinde__de__
yeni__setirden__basla   maq__mumkundur!!!
```
