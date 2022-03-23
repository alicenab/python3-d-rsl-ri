# Break, continue

Python dilində bəzi açar sözlər var ki, onlar mühüm əhəmiyyət daşımırlar, kodun yazılışında ciddi fərq yaratmırlar, professional proqramistlər onları istifadə etmədən də iş görə bilərlər. Bu kimi açar sözlər **syntactic candy** və ya **syntactic sugar** adlanırlar.

break və continue işlənmə qaydası aşağıdakı kimidir.

**break** - dərhal döngünü sonlandırır. Proqram döngüdən sonrakı sətirləri icra etməyə başlayır

**continue** - döngünün həmin mərhələsini skip edir

Nümunə üçün daxil edilmiş sözdə qalın saitlərdən başqa hərfləri çap edən koda baxaq.

```python
soz = input("Soz daxil edin: ")

for herf in soz:
    if herf=='a':
        continue
    elif herf=='ı':
        continue
    elif herf=='o':
        continue
    elif herf=='u':
        continue
    else:
        print(herf,end='')

'''      
Ekranda çıxan nəticə.

Soz daxil edin: azerbaycan
zrbycn
'''
```

Yuxarıdaki nümunədə də göstərdiyim kimi, continue açar sözü öz işləndiyi yerdən çıxardır proqramı.

Aşağıdakı nümunədə doğru sayt adını daxil etmədikcə dayanmayan kod parçası görürsünüz. Kod break vasitəsilə döngüdən yalnız onda çıxır ki, daxil edilmiş sayt adı 3-cü sətirdəki şərti ödəsin. 5-ci sətirdəki `break` döngünü pozur.&#x20;

```python
while True:
    sayt = input("Sayt daxil edin: ")
    if sayt=="alicenab.com":
        print("Tapdiniz!")
        break
        
'''      
Ekranda çıxan nəticə.

Sayt daxil edin: example.com
Sayt daxil edin: test.com
Sayt daxil edin: alicenab.com
Tapdiniz!
'''  
```

### While-else, for-else

Digər bir sintaktik şəkər isə `while-else` və `for-else`-dir. Python dili sizə imkan verir ki, döngülərdən sonra else açar sözünü işlədək. Bu bir çox yeni başlayanlar üçün çətin gələ bilər. Sadə izahı aşağıdakı kimidir.

Əgər hər hansı döngüdə kod break olunmazsa, bu zaman else içindəki kod işə düşsün.

```python
i = 0
while i < 5:
    print(i)
    i += 1
else:
    print("else:", i)
```

Aşağıdakı kod parçasında i əvvəlcədən 111-ə bərabər edildiyi üçün 2-ci sətirin içini oxumur və 4-cü sətirin içinə keçir.

```python
i = 111
for i in range(200, 1):
    print(i)
else:
    print("else:", i)
```



