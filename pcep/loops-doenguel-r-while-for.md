# Loops(döngülər) while,for

Təsəvvür edin ki, [conditional-operators-if-elif-else.md](conditional-operators-if-elif-else.md "mention") səhifəsində izah olunduğu formada yaş sorğulamalısınız. Lakin 1 şəxsdən yox, 100 şəxsdən. Bunun üçün 200 sətirə yaxın kod yazmağa ehtiyac yoxdur, həmin kodu qısa formada da yazmaq mümkündür. Bunun üçün döngülərdən istifadə etmək lazımdır. Döngülər bizə təkrarlanan işləri görməyə kömək edir.

## While loop, (While döngüsü)

Döngüsünün şərti ifadəsi aşağıdakı kimidir. Bir şərt uyğun olduğu halda, while içindəki kod həmin şərt doğru olmayana qədər çalışmağa davam edir.

```python
while şərti_ifadə:
    nəsə_et
```

Əgər şərt heçvaxt doğru olmazsa, döngü sonzuza qədər davam edir, buna **infinite loop** deyilir. Infinite loop-a misal olaraq aşağıdakı kodu göstərə bilərik:

```python
while True:
    print("Ctrl+C bas")
```

Yuxarıdakı 2 sətirlik kod parçası sonsuza qədər ekrana yazı yazacaq. Onu "Ctrl+C" klavyatura kombinasiyası ilə dayandırmaq mümkündür. "Ctrl+C" kombinasiyası proseslərə `KeyboardInterrupt` exception-u (gələcəkdə öyrənəcəyik) göndərərək prosesi dayanmağa məcbur edir.

Məsələn, 5 nəfərin yaş məlumatını alıb müvafiq olaraq onlara cavab verən kod parçasına baxaq.

Prosesin 5 dəfə təkrarlanması üçün c adında bir sayğac (**counter**) tanıdırıq və onu sıfıra bərabər edirik ki, hər bir prosesdə `c`-ni bir vahid artıraraq 5-ə çatdıqda gələcəkdə dayandıra bilək. İkinci sətirdə döngü şərti veririk ki, `c` 5-dən kiçik olduğu müddət ərzində döngü içindəki kodu işlət. Kod istifadəçidən yaş soruşur, əgər yaş 18-dən böyük və ya ona bərabər olarsa, ekrana `icaze var` çap edir. Bu şərt ödənmədikdə isə `icaze yoxdur` çap edir. Burada ən vacib məsələ bütün prosesdən sonra 8-ci sətirdə counter-i 1 vahid artırmağımızdır.

```python
c=0
while c<5:
    yas = input("yasinizi daxil edin: ")
    if int(yas)>=18:
        print("icaze var")
    else:
        print("icaze yoxdur")
    c+=1
```

Yuxarıdakı kod 5 dəfə istifadəçidən yaşını soruşur. Ekrana çıxartdığı yazı aşağıdakı kimidir.

```
yasinizi daxil edin: 16
icaze yoxdur
yasinizi daxil edin: 17
icaze yoxdur
yasinizi daxil edin: 18
icaze var
yasinizi daxil edin: 19
icaze var
yasinizi daxil edin: 20
icaze var
```

## For loop, (for döngüsü) və range() funksiyası

For bizə müəyyən bir siyahıdakı elementlərin hər biri üzrə işləmək imkanı verən döngü növüdür.

Məsələn, yuxarıda yazdığımız istifadəçidən 5 dəfə yaş soruşan kod nümunəsini for döngüsü vasitəsilə aşağıdakı kimi yazmaq mümkündür:

```python
for c in range(5):
    yas = input("yasinizi daxil edin: ")
    if int(yas)>=18:
        print("icaze var")
    else:
        print("icaze yoxdur")
    print(c)
```

Kod parçası işə düşdükdə range(5)-i görür və özü üçün 5 elementi olan **list** (siyahı) (gələcəkdə bundan bəhs edəcəyik) tərtib edir. Kompüterlər sıfırdan saymağa başladığına görə həmin siyahı bu cür olur:

```
[0,1,2,3,4]
```

Yuxarıdakı kodun birinci sətrini bu cür başa düşmək olar. range(5)-in verdiyi siyahının elementi dəfə döngü içindəki işi gör. Buna görə də birinci mərhələdə c-nin dəyəri sıfır, ikincidə bir, üçüncüdə iki, dördüncüdə üç, beşincidə isə 4 olur.

Aydın olması üçün 7-ci sətirdə c-nin hal-hazırki dəyərini ekrana çap etdirək.

```
yasinizi daxil edin: 16
icaze yoxdur
0
yasinizi daxil edin: 17
icaze yoxdur
1
yasinizi daxil edin: 18
icaze var
2
yasinizi daxil edin: 19
icaze var
3
yasinizi daxil edin: 20
icaze var
4
```

Yuxarıdakı kodu bu şəkildə də yazmaq mümkündür. İkisi də tamamilə eynidir.

```python
siyahi = [0,1,2,3,4]

for c in siyahi:
    yas = input("yasinizi daxil edin: ")
    if int(yas)>=18:
        print("icaze var")
    else:
        print("icaze yoxdur")
    print(c)
```

### range() funskiyasının əlavə imkanları

Tutalım ki, 1-dən 10-a qədər cüt ədədləri ekrana çap edən proqram yazmaq lazımdır.

```python
for i in range(0,10):
    if i%2==0: # ikiyə bölündükdə qalıqda 0 alınan ədəd cüt ədəddir.
        print(i)
        
""
Ekrana çıxan nəticə:

0
2
4
6
8
""
```

**NOT**; range() funksiyası heç vaxt son ədədi nəzərə almır.

Digər koddan fərqli olaraq yuxarıdakı kodda `range()` funksiyası içinə iki ədəd vermişik. Onlardan birincisi siyahının başlandığı, digəri isə bitdiyi yerdir. `range()` funksiyasına üçüncü arqumenti də vermək mümkündür, üçüncü arqument range() funksiyasında başdan sona addım sayını təyin edir. Yəni normalda rəqəmlər bir-bir artırdısa, biz bunu dəyişə bilərik. Dolayısıyla yuxarıdakı nəticəni verən kodu daha qısa şəkildə aşağıdakı formada yazmaq mümkündür:

```python
for i in range(0,10,2):
    print(i)

''' 
Ekrana çıxan nəticə:

0
2
4
6
8
'''
```

`range()` funksiyasında geri addımlamaq da mümkündür. Məsələn,

```
for i in range(10,0,-2):
    print(i)

''' 
Ekrana çıxan nəticə:

10
8
6
4
2
'''
```
