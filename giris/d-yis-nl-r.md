# Variables (dəyişənlər)

Hər hansı dəyəri müəyyən adda komputerin RAM yaddaşında müəvvəqi olaraq yadda saxlamaq üçün dəyişənlərdən istifadə olunur. Dəyişənlər təyin olunarkən bərabərin sağ tərəfindəki vahid sol tərəfə təyin olunur. Məsələn&#x20;

```
a=3
print(a)
```

Yuxarıdakı misalda birinci növbədə `1` dəyərinə sahib olan integeri `a` adı verdiyim bir dəyişənə təyin etdim. Daha sonra isə onun adını çağıraraq içindəki dəyəri ekrana yazdım.&#x20;

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

Dəyişənlərin adları ingilis dilində olmaq məcburiyyətində deyil. Məsələn, aşağıdakı formada dəyişən adlandırmaları qanuna uyğundur

```
Adiós_Señora, sûr_la_mer, Einbahnstraße, переменная
```

Gəlin başqa bir misala baxaq

```
ad="Məmməd"
soyad="Məmmədov"
yas=22
print(ad, soyad, yas)
```

Yuxarıdakı misalda Məmməd adını ad dəyişəninə, Məmmədov soyadını soyad dəyişəninə, 22 ədədini isə yas dəyişəninə təyin etmişəm, bundan sonra isə print() funksiyası vasitəsilə əvvəlcədən təyin etdiyim dəyişənləri ekrana çap etmişəm. Nəticə aşağıdakı kimidir.

```
Məmməd Məmmədov 22
```



Dəyişənlərə yenidən dəyərlərin təyin olunması.

```
istenilen=4
istenilen=5+1
print(istenilen)     #ekrana 6 yazılacaq.
istenilen2=8
print(istenilen*istenilen2)    #ekrana 
```

Yuxarıdakı misalda 1-ci sətirdə `4` ədədi təyin olunmuş `istenilen` adlı dəyişənə 2-ci sətirdə `5+1` təyin olunmuşdur. Kompüter kodu sətir bə sətir oxuduğu üçün ikinci sətirdə baş verən təyinetmə birincini əvəzləyəcəkdir. Dolayısıyla 3-cü sətirin nəticəsi olaraq ekrana 5+1-in nəticəsi, yəni 6 çıxacaqdır.&#x20;

4-cü sətirdə `istenilen2` adlı dəyişənə 8 integerini təyin etmişəm. 5-ci sətirdə `print()` funksiyası vasitəsilə istenilen dəyişəninin `istenilen2` dəyişəni ilə hasilini ekrana çap etmişəm. Ekrana 6\*8, yəni 48 cavabı çıxmışdır.

Eyni vaxtda 1-dən çox dəyişənə dəyər təyin etmək mümkündür. Məsələn

```
x, y, z = 5, 10, 8
print(x,y,z) # ekrana 5, 10, 8 çap edir.
```











