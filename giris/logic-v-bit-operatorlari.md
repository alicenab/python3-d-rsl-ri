# Logic və bit operatorları

İndiyədək izah etdiyimiz şərtləndirmələr sadə şərtləndirmələrdir. Lakin real həyatda istifadə etdiyimiz şərtlər bu qədər sadə deyil. Məsələn:

_Əgər günortadan sonra hava yaxşı olsa, gəzməyə gedəcəm._

Burada şəxsin gəzməyə getməyi üçün iki şərt ödənməlidir: həm gün içindəki vaxt günortadan sonra olmalıdır, həm də hava yaxşı olmalıdır. Bəs biz bu cür situasiyaları kompüterlərə necə başa sala bilərik?

Bu kimi hallarda xüsusi logic operatorlardan istifadə olunur. Məsələn: and, or, not və s.

`and` logic operatorunun True cavabını qaytarması üçün and-in sağ və sol tərəfindəki şərtlərin hər ikisi True olmalıdır;

`or` logic operatoru yalnız hər iki tərəf False cavabını qaytardıqda False qaytarır;

`not` logic operatoru isə özünə verilən cavabın əksini qaytarır.

## Bitwise operators

Bitwise operatorları haqqında oxuyarkən fikirləşə bilərsiniz ki, real həyatda bu mənə harda lazım ola bilər?&#x20;

Təsəvvür edin ki, böyük bir kod yazmısınız və həmin kodun nəticəsi 63 fərqli şərtin doğru və ya yanlış olduğu barədə məlumatı RAM yaddaşda aşağıdakı şəkildə yadda saxlayır. Bu tipli hesablamalara ən çox linux əməliyyat sisteminin kodlarında rastlaşmışam. Əgər sizə son 5 bit üzərində işləmək səlahiyyəti verilsəydi və digər bitlərə dəyişiklik icazəsi verilməsəydi, aşağı səviyyədə bitwise operatorları vasitəsilə bu kimi əməliyyatları etmək daha rahat olardı.

```
11001001010010001001010100111111010101010101101010010010101010
```

* `&` (ampersand) - bitwise conjunction operatoru, sağ və sol tərəf 1 olmalıdır ki, cavab 1 versin;
* `|` (bar) - bitwise disjunction operatoru, iki tərəfdən ən az biri 1 olmalıdır ki, cavab 1 versin;
* `~` (tilde) - bitwise negation operatoru, sadəcə tərəflərdən biri 1 olmalıdır ki, cavab 1 versin;
* `^` (caret) - bitwise exclusive or (xor), verilmiş bitin əksini qaytarır.

Digər hesablama operatorlarında olduğu kimi, bu operatorlar da shortcutla istifadə edilə bilərlər.

|  `x = x & y` |  `x`` ``&=`` ``y` |
| :----------: | :---------------: |
| `x = x \| y` | `x`` ``\|=`` ``y` |
|  `x = x ^ y` |  `x`` ``^=`` ``y` |

## Bitshift operatorları

Hərşeyi başa düşmək üçün aşağıdakı kod nümunəmə baxmaq mümkündür.

```python
i = 15               #b'00000000000000000000000000001111' - original deyer
j = 22               #b'00000000000000000000000000010110' - original deyer

my_conj = i&j        #b'00000000000000000000000000000110' - her ikisinin 1 olanlari
my_xor = i^j         #b'00000000000000000000000000011001' - her ikisinin 1 olmayani
my_disj = i|j        #b'00000000000000000000000000011111' - her ikisinin 0 olmayani
my_neg1 = ~i         #b'11111111111111111111111111110000' - i-nin tersi, 2nin complementi
my_neg2 = ~j         #b'11111111111111111111111111101001' - j-nin tersi, 2nin complementi

left_shift = i<<2    #b'00000000000000000000000000111100' - 2 dəfə sola sürüşür, soldakı 2 rəqəm sağa keçir.
right_shift = i>>2   #b'00000000000000000000000000000011' - 2 dəfə sağa sürüşür, yox olanların yerinə 0 yazılır

print("i: ", i,
      "\nj: ", j,
      "\nmy_conj: ", my_conj,
      "\nmy_xor: ", my_xor,
      "\nmy_disj: ", my_disj,
      "\nmy_neg1: ", my_neg1,
      "\nmy_neg2: ", my_neg2,
      "\nleft_shift: ", left_shift,
      "\nright_shift", right_shift
        )
```

Right shift və left shiftləri bu formada daha sürətli hesablamaq olar:&#x20;

```python
var=32
var = var>>4
print(var) # cavab 2. 32/2^4=32/16=2

var = 32
var = var << 4
print(var) #cavab 512. 32*2^4=32*16=512
```

