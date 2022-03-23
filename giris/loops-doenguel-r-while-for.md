# Loops(döngülər) while,for

Təsəvvür edin ki, [conditional-operators-if-elif-else.md](conditional-operators-if-elif-else.md "mention") səhifəsində izah olunan formada yaş sorğulamalısınız. Lakin 1 şəxsdən yox, 100 şəxsdən. Bunun üçün 200 sətirə yaxın kod yazmağa ehtiyac yoxdur. Həmin kodu qısa formada da yazmaq mümkündür. Bunun üçün döngülərdən istifadə etmək lazımdır. Döngülər bizə təkrarlanan işləri görməyə kömək edirlər.

## While loop, (While döngüsü)

&#x20;Döngüsünün şərti ifadəsi aşağıdakı kimidir. Bir şərt uyğun olduğu halda while içindəki kod çalışmağa davam edir, o vaxta qədər ki, həmin şərt doğru olmasın.

```python
while şərti_ifadə:
    nəsə_et
```

Əgər şərt heçvaxt doğru olmazsa, döngü sonzuza qədər davam edir, buna **infinite loop** deyilir. Infinite loop-a misal olaraq aşağıdakı kodu göstərə bilərəm.

```python
while True:
    print("Ctrl+C bas")
```

Yuxarıdakı 2 sətirlik kod parçası, sonsuza qədər ekrana yazı yazacaq. Onu Ctrl+C klavyatura kombinasiyası ilə dayandırmaq mümkündür. Ctrl+C kombinasiyası proseslərə `KeyboardInterrupt` exception-u(gələcəkdə öyrənəcəyik) göndərərək prosesi dayanmağa məcbur edir.

Məsələn 5 nəfərin yaş məlumatını alıb müvafiq olaraq onlara cavab verən kod parçasına baxaq.

Prosesin 5 dəfə təkrarlanması üçün c adında bir sayğac (**counter**) tanıdıram və onu sıfıra bərabər edirəm ki, hər bir prosesdə `c`-ni bir vahid artıraraq 5-ə çatanda dayandıra bilim gələcəkdə. İkinci sətirdə döngü şərti verirəm ki, `c` 5-dən kiçik olduğu müddət ərzində döngü içindəki kodu işlət. Kod istifadəçidən yaş soruşur və əgər yaş 18-dən böyük və ya ona bərabər olarsa ekrana `icaze var` çap edir. Əgər bu şərt ödənməzsə `icaze yoxdur` çap edir. Buradakı ən vacib məsələ bütün prosesdən sonra 8-ci sətirdə counteri 1 vahid artırmağımızdır.

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

Məsələn yuxarıda yazdığım istifadəçidən 5 dəfə yaş soruşan kod nümunəsini for döngüsü vasitəsilə aşağıdakı kimi yazmaq mümkündür.

```python
for c in range(5):
    yas = input("yasinizi daxil edin: ")
    if int(yas)>=18:
        print("icaze var")
    else:
        print("icaze yoxdur")
    print(c)
```

Kod parçası işə düşdükdə range(5)-i görür və özü üçün 5 elementi olan **list** (siyahı) (gələcəkdə keçəcəyik) düzəldir. Komputerlər sıfırdan saymağa başladığına görə həmin siyahı bu cür olur

```
[0,1,2,3,4]
```

Yuxarıdakı kodun birinci sətrini bu cür başa düşmək olar. range(5)-in verdiyi siyahının elementi dəfə, döngü içindəki işi gör. Buna görə də birinci etapda c-nin dəyəri sıfır, ikincidə bir, üçüncüdə iki, dördüncüdə üç, beşincidə isə 4 olur.

Daha yaxşı başa düşülsün deyə 7-ci sətirdə c-nin hal-hazırki dəyərini ekrana çap etdirmişəm.

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

Yuxarıdakı kodu bu şəkildə də yazmaq mümkündür. İkisi də tamamilə eyni şeydir.

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
Ekrana çıxan nəticə.

0
2
4
6
8
""
```

**NOT**; range() funksiyası heçvaxt son ədədi siyahıya salmır.

Digər koddan fərqli olaraq yuxarıdakı kodda range() funksiyası içinə iki ədəd vermişəm. Onlardan birincisi siyahının başlandığı, digəri isə bitdiyi yerdir. range() funksiyasına üçüncü arqumenti də vermək mümkündür, üçüncü arqument range() funksiyasında başdan sona addım sayını təyin edir. Yəni normalda rəqəmlər bir-bir artırdısa, biz bunu dəyişə bilərik. Dolayısıyla yuxarıdakı nəticəni verən kodu daha qısa şəkildə aşağıdakı formada yazmaq mümkündür.

```python
for i in range(0,10,2):
    print(i)

''' 
Ekrana çıxan nəticə.

0
2
4
6
8
'''
```



