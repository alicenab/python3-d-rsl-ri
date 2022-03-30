# Python-dan ilk istifadə

Əgər siz, MacOS vəya hər hansı linux tipli əməliyyat sistemini istifadə edirsinizsə, çox böyük ehtimalla sizin kompüterinizdə artıq python3 mövcuddur. Terminala aşağıdakı əmri yazaraq yüklənib-yüklənməməsini yoxlamaq mümkündür.

```
python3 -V
```

Yükləndiyi halda python3-ün versiyası ekrana yazılacaq.

Windows istifadə edən şəxslər isə ağlayaraq bu sadəliyi öz gündəliklərinə yaza bilərlər.😛

Əlbətdə ki, bu bir zarafatdır, windows istifadəçiləri aşağıdakı linkdən python3-ü öz kompüterlərinə yükləyib quraşdıra bilərlər.

{% embed url="https://www.python.org/ftp/python/3.10.3/python-3.10.3-amd64.exe" %}
(bu spesifik olaraq 3.10.3 versiyasının linkidir.)
{% endembed %}

Python-da kod yazmağa başlamaq üçün iki şeyə ehtiyacınız var:

1\) Kodu yazdığınız **editor**-a (notepad, vim, notepad++, visual studio code və s.);

2\) yazdığınız kodu işə salmaq və işə düşmüş kod nəzarətdən çıxdıqda həmin prosesi bağlamaq üçün **console**(terminal)-a.

Əlavə olaraq, yazdığınız kodu addım-addım izləyib, hansı mərhələdə kodun necə davrandığını müşahidə etməyinizə kömək edən **debugger**-dən istifadə edə bilərsiniz.

Python3-ü Windows əməliyyat sisteminə quraşdırdığınız vaxt yuxarıda sadalanan bəndlərdəki özəllikləri və debuggeri özündə birləşdirən **IDLE** adında bir alət də yüklənir.

**IDLE** Integrated Development and Learning Environment sözlərinin birləşməsidir.

Test üçün MacOS əməliyyat sistemində prosesin necə olduğuna baxaq.

```
pwd
/Users/alicenab/Desktop/ders
vim ilk.py
cat ilk.py 
print("Salam dunya")
python3 ilk.py 
Salam dunya
```

1\) pwd əmri vasitəsilə hal-hazırda hansı qovluqda olduğumuzu öyrənmək istəyirik;\
2\) 1-ci sətirdəki əmrin cavabı ikinci sətirdə ekrana yazılır;\
3\) vim text editoru vasitəsilə ilk.py adında fayl yaradıb içinə print("salam dunya") yazırıq;\
4\) cat əmri vasitəsilə ilk.py faylının içini ekrana çıxardırıq;\
5\) 5-ci sətirdə 4-cü sətirdəki əmrin nəticəsi görünür;\
6\) python3 ilk.py əmri vasitəsilə ilk.py source faylını python3 interpreterinə ötürürük;\
7\) 6-cı sətrin nəticəsi 7-ci sətirdə ekrana yazılır. Bu proqramın nəticəsidir.
