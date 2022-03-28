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

| `x = x & y`  | `x`` ``&=`` ``y`  |
| ------------ | ----------------- |
| `x = x \| y` | `x`` ``\|=`` ``y` |
| `x = x ^ y`  | `x`` ``^=`` ``y`  |





