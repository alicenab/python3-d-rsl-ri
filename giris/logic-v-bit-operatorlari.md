# Logic və bit operatorları

İndiyədək izah etdiyimiz şərtləndirmələr sadə şərtləndirmələrdir. Lakin real həyatda istifadə etdiyimiz şərtlər bu qədər sadə deyil. Məsələn:

_Əgər günortadan sonra hava yaxşı olsa, gəzməyə gedəcəm._

Burada şəxsin gəzməyə getməyi üçün iki şərt ödənməlidir: həm gün içindəki vaxt günortadan sonra olmalıdır, həm də hava yaxşı olmalıdır. Bəs biz bu cür situasiyaları kompüterlərə necə başa sala bilərik?

Bu kimi hallarda xüsusi logic operatorlardan istifadə olunur. Məsələn: and, or, not və s.

`and` logic operatorunun True cavabını qaytarması üçün and-in sağ və sol tərəfindəki şərtlərin hər ikisi True olmalıdır;

`or` logic operatoru yalnız hər iki tərəf False cavabını qaytardıqda False qaytarır;

`not` logic operatoru isə özünə verilən cavabın əksini qaytarır.

## Bitwise operators



* `&` (ampersand) - bitwise conjunction operatoru, sağ və sol tərəf 1 olmalıdır ki, cavab 1 versin;
* `|` (bar) - bitwise disjunction operatoru, iki tərəfdən ən az biri 1 olmalıdır ki, cavab 1 versin;
* `~` (tilde) - bitwise negation operatoru, sadəcə tərəflərdən biri 1 olmalıdır ki, cavab 1 versin;
* `^` (caret) - bitwise exclusive or (xor), verilmiş bitin əksini qaytarır.













