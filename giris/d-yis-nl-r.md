# Dəyişənlər

Hər hansı dəyəri müəyyən adda komputerin RAM yaddaşında müəvvəqi olaraq yadda saxlamaq üçün dəyişənlərdən istifadə olunur. Məsələn&#x20;

```
a=3
print(a)
```

Yuxarıdakı misalda birinci növbədə 1 dəyərinə sahib olan integeri komputerin RAM yaddaşında müəyyən bir bölgədə yadda saxladım və ona a adını verdim. Daha sonra isə onun adını çağıraraq içindəki dəyəri ekrana yazdım.&#x20;

Dəyişənlər yazdığımız kodları daha oxunaqlı və sadə formaya salmaq üçün istifadə olunurlar.



Təsəvvür edin ki, böyük bir restoranda təşkilatçısınız, hər dəfə müxtəlif sayda qonaqlarınız olur, məsəlçün 100-200 arası.

hər bir masanın ölçüsünü masanı reserv edən insanların sayına görə təşkil eliyirsiz, məsələn Əvəz adlı şəxsin tanışları üçün 6 nəfərlik, Əbülfəz adlı şəxsin tanışları üçün 4 nəfərlik, Əziz adlı şəxsin tanışları üçün isə 10 nəfərlik masalar təşkil etmək lazım olur. Həmin masalar qonaqlar gələnə kimi reserv olunurlar, qonaqlar getdikdən sonra boş olurlar, məclis bitdikdə isə hamısı boş olur.

Komputer yaddaşını sadə dildə sizə bu cür izah edə bilərəm.



```
python3 kod.py
```

Komputerdə bu əmri çalışdırdıqda əməliyyat sistemi sizin proqramın icra olunması üçün komputerin RAM-ında bir adresi götürür ki, növbəti nə gəlsə bu adresdən sonra gəlsin. Bunu dolmaqda olan bir vedrə kimi təsəvvür edə bilərsiz, sizin proqram həmişə vedrənin ən yuxarısındaki adresdən başlayır və üzü yuxarı vedrəni(RAM)ı doldurmağa başlayır.





`a=3` dedikdə komputer 3 rəqəminin komputerin ram yaddaşında tutacağı yeri hesablıyır və yaddaşda 3 rəqəminin tutacağı yeri reserv edir, gələcəkdə kimsə 3-ə müraciət etmək istəsə sadəcə masanın adını bilməsi bəs edir ki masada oturan şəxsləri görə bilsin.&#x20;

Masada oturan şəxslərin işi bitdikdən sonra onlar dəyişə bilərlər. Proqram icra olunub bitdikdən sonra isə ümumiyyətlə RAMda proqramın tutduğu yer təmizlənir. Loru dildə desək məclislərin hamısı bitir.&#x20;



Dəyişənlər adlandırılan zaman bir neçə nüans nəzərə alınmalıdır, Məsələn, dəyişənlər adlandırılarkən aşağıdakıları etmək olmaz

1\) Dəyişənlər adlandırılarkən boşluqdan istifadə etmək olmaz, məsələn,

`menim adim`, `telebenin yasi` kimi adlandırmalar etmək səhvdir.

2\) Dəyişənlər adlandırılarkən rəqəmdən başlamaq olmaz. Məsələn, `10telebe`, `2defe` kimi adlar səhvdir.&#x20;

3\) Dəyişənlər adlandırılarkən aşağıdakı sözlərdən istifadə etmək olmaz çünki onlar Python dilinin işləməsi üçün rezerv olunmuş xüsusi sözlərdir.

```
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

