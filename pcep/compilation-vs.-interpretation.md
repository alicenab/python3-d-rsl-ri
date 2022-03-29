# Compilation vs. interpretation

Yüksək səviyyəli dildə source code-u yazdıqdan sonra həmin kodun işləməsi üçün o, aşağı səviyyəli maşın dilinə tərcümə olunmalıdır.

Yüksək səviyyəli dildən maşın dilinə çevrilmənin iki əsas yolu mövcuddur:

**Compliation** - source code bir dəfə tərcümə olunur, kodda edilmiş hər dəyişiklik üçün kodu yenidən tərcümə etmək lazım gəlir. Bu zaman yazdığınız kod işlədilə bilən (məsələn, windows-da .exe faylları) fayl formatına çevrilir. Həmin tərcüməni edən alət **compiler** adlanır.

**Interpretation** - Proqram hər dəfə işə salınmaq istədikdə tərcümə olunmalıdır. Bu halda kodu istənilən şəxsə ötürə bilməzsiniz, gərək ötürdüyünüz şəxsdə də tərcümə etmək üçün alət olsun. Həmin alət **interpreter** adlanır.



| Metod        | Compliation                                                                                                                                                                                                                                                                                                                                                                    | Interpretation                                                                                                                                                                                                                                                                        |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Üstünlükləri | <ul><li>Compliation edilmiş proqramlar adətən daha sürətli işləyirlər;</li><li>Sadəcə kodu yazan şəxsin compiler istifadə etməsinə ehtiyac var, kodu təhvil alan şəxsin kompüterində compiler olmasına isə ehtiyac yoxdur;</li><li>Sizin yazdığınız kod compliation zamanı insanların çətin başa düşə bildiyi maşın dilinə çevrilir. Bu sizin kodun gizliliyini artırır.</li></ul> | <ul><li>Kodu yazıb bitirdiyiniz an onu işə sala bilərsiniz, əlavə tərcümə mərhələsinə ehtiyac yoxdur;</li><li>Sizin kodunuz yazdığınız formada kompüter yaddaşında saxlanılır. Müxtəlif arxitekturalı kompüterlər üçün müxtəlif təcrümələr etməyinizə ehtiyac qalmır.</li></ul> |
| Zəiflikləri  | <ul><li>Compliation vaxt aparan bir proses halına çevrilə bilər. Siz öz kodunuzu yazıb bitirdikdən dərhal sonra işlətməyə bilərsiniz;</li><li>Müştərinin sahib olduğu dəmir avadanlıq platformasına uyğun olaraq kodu compile etməlisiniz ki, kod həmin arxitekturalı kompüterdə işə düşə bilsin.</li></ul>                                                                    | <ul><li>Həm sizdə, həm də müştəridə interpreter olmalıdır ki, kodu işə sala bilsin;</li><li>Interpreter vasitəsilə işə düşən kodun compile olunan koddan sürətli işləməsini gözləməyin, çünki kompüterlə kod arasında əlavə proqram, yəni interpreter olur.</li></ul>                  |



Python interpreted dildir, yəni yuxarıdakı cədvəldə Interpretation haqqında danışılan üstün və zəif xüsusiyyətlərə sahibdir.

Python dilində kod yazmaq istəsəniz, sizin python interpreter-ə ehtiyacınız olacaq. Python interpreter-i pulsuz yükləmək mümkündür.\
\
Tarixi səbəblərdən işləmək üçün əlavə interpreter-ə ehtiyacı olan dillər həmçinin **skriptinq dilləri**, həmin dillərin source code-u isə **skriptlər** adlandırılıb.
