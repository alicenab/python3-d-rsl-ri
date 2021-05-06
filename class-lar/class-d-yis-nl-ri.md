---
description: Class dəyişənləri nədir?
---

# Class dəyişənləri

Class dəyişənləri, class-ın aid olduğu bütün instance-lar üzrə işlədilə bilən dəyişənlərə deyilir.

İnstance dəyişənləri hər instance üçün müxtəlif idi. Ancaq Class dəyişənləri hər instance üçün eynidir.

Gəlin belə təsəvvür edək ki, şirkət hər il öz işçilərinin maaşını 12 faiz artırır. Biz bunu kod olaraq ifadə etmək üçün aşağıdaki kimi kod yaza bilərik:

```python
class Employee:

    raise_amount = 1.12
    
    def __init__(self, first, last, pay):
        self.first = first
        self.last = last
        self.pay = pay
        self.email = first + '.' + last + '@email.com'
        
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
        
    def apply_raise(self):
        self.pay = int(self.pay * raise_amount)
        
emp_1 = Employee('Mammad', 'Mammadov', 50000)
emp_2 = Employee('Mammad2', 'Mammadov2', 60000)


print(emp_1.pay)
emp_1.apply_raise()
print(emp_1.pay)
```

Əvvəlki bölmədə yazdığım koda, 3-cü, 14-15-ci sətirləri əlavə etdim. Riyazi baxımdan bir dəyəri 12 faiz artırmağın yolu həmin dəyəri 1.12-yə vurmaqdır. Həmin dəyərin bizə axırda `int` dəyərində geri dönməsi üçün bütün hesablamanı `int()` içinə aldım. Real mühitdə belə etməyin. Bu pis nəticələrə yol aça bilər.

Ancaq maraqlısı budur ki, yuxarıdaki kodu çalışdırdıqda python xəta verir:

```text
NameError: name 'raise_amount' is not defined.
```

 Bu xəta ona görə çıxır ki, class dəyişənini çağırmaq istədiyimizdə, həmin dəyişəni ya classın ya da instance-ın içindən çağırmalıyıq. 

15-ci sətirdə olduğu kimi `apply_raise` method-un içində `raise_amount` dəyişənini görmədiyi üçün, onu `Employee.raise_amount` \(vəya `self.raise_amount`\) olaraq dəyişdirmək lazımdır.

```python
class Employee:

    raise_amount = 1.12
    
    def __init__(self, first, last, pay):
        self.first = first
        self.last = last
        self.pay = pay
        self.email = first + '.' + last + '@email.com'
        
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
        
    def apply_raise(self):
        self.pay = int(self.pay * raise_amount)
        
emp_1 = Employee('Mammad', 'Mammadov', 50000)
emp_2 = Employee('Mammad2', 'Mammadov2', 60000)

print(Employee.raise_amount)    # 1.12
print(emp_1.raise_amount)  # 1.12
print(emp_2.raise_amount)  # 1.12
```

`emp_1` instance-ının özünün `raise_amount` adında attributu yoxdur. Ancaq `self` vasitəsi ilə o hansı class-a aid olduğunu bilir. Buna görə də özünün aid olduğu class-ın içindəki attributları axtarmağa başlıyır və `raise_amount`-nin `1.12`yə bərabər olduğunu görür.

Sizi maraqlı bir halla tanış etmək istəyirəm. Əgər siz `emp_1.raise_amount = 1.15` desəniz, məntiqi olaraq `emp_1`-in aid olduğu  class atributunun \(yəni `Employee.raise_amount`-nin da dəyişməsini gözləyərdiniz elə deyil?

Ancaq python3 belə işləmir. Əgər siz `emp_1.raise_amount` -ni `1.15` etsəniz, bu zaman python özü `emp_1` instance-ında `raise_amount`  adında əvvəl mövcud olmayan attribute yaradır. 

```python
class Employee:

    raise_amount = 1.12
    
     def __init__(self, first, last, pay):
        self.first = first
        self.last = last
        self.pay = pay
        self.email = first + '.' + last + '@email.com'
        
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
        
    def apply_raise(self):
        self.pay = int(self.pay * raise_amount)
        
emp_1 = Employee('Mammad', 'Mammadov', 50000)
emp_2 = Employee('Mammad2', 'Mammadov2', 60000)


print(emp_1.__dict__)
# {'ad': 'Ali', 'soyad': 'Mammadzada', 'maas': 50000}
emp_1.raise_amount = 1.15

print(Employee.raise_amount)    # 1.12
print(emp_1.raise_amount)  # 1.15
print(emp_2.raise_amount)  # 1.12

print(emp_1.__dict__) 
# {'artma_miqdari': 1.15, 'ad': 'Ali', 'soyad': 'Mammadzada', 'maas': 50000}
```

Nümunədən də gördüyünüz kimi, əvvəl  `emp_1`-in `namespace`-ində `raise_amount` yox idi. Ancaq sonradan yarandı. 

