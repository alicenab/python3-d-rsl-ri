# Python-dan ilk istifadə

Əgər siz, MacOS vəya hər hansı linux tipli əməliyyat sistemini istifadə edirsinizsə, çox böyük ehtimalla sizin kompüterinizdə artıq python3 mövcuddur. Terminala aşağıdakı əmri yazaraq yüklənib yüklənməməsini yoxlamaq mümkündür.

```
python3 -V
```

Əgər yüklənibsə python3-ün versiyası ekrana yazılacaq. Windows istifadə edən şəxslər isə ağlayaraq bu sadəliyi öz gündəliklərinə yaza bilərlər 😛

Əlbətdə ki, bu bir zarafatdır, windows istifadəçiləri aşağıdakı linkdən python3-ü öz kompüterlərinə yükləyib quraşdıra bilərlər.

{% embed url="https://www.python.org/ftp/python/3.10.3/python-3.10.3-amd64.exe" %}
(bu spesifik olaraq 3.10.3 versiyasının linkidir)
{% endembed %}

Python-da kod yazmağa başlamaq üçün üç şeyə ehtiyacınız var

1\) kodu yazdığınız **editor**-a (notepad, vim, notepad++, visual studio code və s.)

2\) yazdığınız kodu işə salmaq və işə düşmüş kod nəzarətdən çıxdıqda həmin prosesi bağlamaq üçün **console**(terminal)-a

3\) yazdığınız kodu addım-addım izləyib, hansı mərhələdə kodun necə davrandığını müşahidə etməyinizə kömək edən **debugger**-ə.

Python3-ü komputerə ilk quraşdırdığınız vaxt yuxarıdaki bəndlərdəki özəllikləri özündə birləşdirən **IDLE** adında bir alət də yüklənir.&#x20;

**IDLE** açılımı: Integrated Development and Learning Environment-dir.



Test üçün MacOS əməliyyat sistemində prosesin necə olduğunu göstərəcəm.

```
alicenab@Alis-MacBook-Pro ders % pwd
/Users/alicenab/Desktop/ders
alicenab@Alis-MacBook-Pro ders % vim ilk.py
alicenab@Alis-MacBook-Pro ders % cat ilk.py 
print("Salam dunya")
alicenab@Alis-MacBook-Pro ders % python3 ilk.py 
Salam dunya
```

1\) pwd əmri vasitəsilə hal-hazırda hansı qovluqda olduğumu öyrənmək istəyirəm\
2\) 1-ci sətirdəki əmrin cavabı ikinci sətirdə ekrana yazılır\
3\) vim text editoru vasitəsilə ilk.py adında fayl yaradıb içinə print("salam dunya") yazıram\
4\) cat əmri vasitəsilə ilk.py faylının içini ekrana çıxardıram\
5\) 5-ci sətirdə 4-cü sətirdəki əmrin nəticəsi görsənir\
6\) python3 ilk.py əmri vasitəsilə ilk.py source faylını python3 interpreterinə ötürürəm\
7\) 6-cı sətrin nəticəsi 7-ci sətirdə ekrana yazılır. Bu proqramın nəticəsidir.
