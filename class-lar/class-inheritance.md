---
description: İrsilik
---

# Class Inheritance

## Inhertiance nədir?

İnheritance sözü Azərbaycan dilinə irsilik, törəmə kimi tərcümə olunur. 

İnheritance bizə `parent class`-dan method və `attribute`-ları irsi olaraq götürməyə imkan yaradır. Bu yolla biz `parent class`a heç bir zərər vermədən yeni `subclass`-lar yaradıb `subclass`-lara öz istədiyimiz funksionallıqları əlavə edə bilərik.

Aşağıdakı kod parçasına fikir verək, `Employee` adında bir `class`-ımız var. `inheritance`-ı məşq etmək üçün developer-lər və manager-lər `sublcass`-ı yaratmaq məntiqli olardı. Çünki həm developer-lər həm də manager-lər işçilərdir və onların sistemdə ad,soyad, email və maaşının qeydə alınmağı məntiqli səslənir.

```python
class Employee:
    raise_amt = 1.04

    def __init__(self, first, last, pay):
        self.first = first
        self.last = last
        self.email = first + '.' + last + '@email.com'
        self.pay = pay
    
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
    
    def apply_raise(self):
        self.pay = int(self.pay + self.raise_amt)

emp_1 = Employee('Corey', 'Schafer', 50000)
emp_2 = Employee('Test', 'Employee', 60000)

print(emp_1.email)
print(emp_2.email)
```

Output:

> Corey.Schafer@email.com   
> Test.Employee@email.com

Yuxarıdakı kodun 16-cı sətrindən etibarən dəyişiklik etməyə başladım.

Pythonda subclass yaratmaq çox sadədir. Birinci normal qaydada `class` keyword-ündən istifadə edib ondan sonra class-ın adını qoymaq lazımdır. Bundan sonra isə mötərizə içində yeni yaranan classın hansı class-dan method və attribute-ları inherit etməsini istədiyimizi demək lazımdır \(bax: aşağıdakı kodda sətir 16 və 19\). Fikir verirsinizsə, sətir 17 və 20-də pass keyword-ünü işlətmişəm. 

{% hint style="info" %}
The `pass` statement is used as a placeholder for future code.  
When the `pass` statement is executed, nothing happens, but you avoid getting an error when empty code is not allowed.  
Empty code is not allowed in loops, function definitions, class definitions, or in if statements.
{% endhint %}

Ancaq burada mənim `pass` işlətməyimin səbəbi başqadır. Mən faktiki olaraq `Developer` və `Manager` subclass-ları içində nəsə yazmasam belə, 22 və 23-cü sətirlərdə onlardan istifadə etmişəm. Bəs hər iki kod necə eyni nəticəni verib?

Ona görə ki, `Developer` və `Manager` sub class-ları hər ikisi `Employee` class-ının içindəki kodları özlərinə irsi olaraq götürüblər. Python kodu çalışdırıldığı zaman kod yuxarıdan aşağı oxunub gəlib çatır 22-ci sətirə. Görür ki `Developer` və `Manager` class-larından istifadə olunub. Baxır ki nə `Developer` class-ının içində nə də `Manager` class-ının içində `init` methodu yoxdur. Ona görə qalxır `Developer` və `Manager` class-larının parent classına yəni `Employee` classına.  Buna termin olaraq   
"`method resolution order`" deyilir.



```python
class Employee:
    raise_amt = 1.04

    def __init__(self, first, last, pay):
        self.first = first
        self.last = last
        self.email = first + '.' + last + '@email.com'
        self.pay = pay
    
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
    
    def apply_raise(self):
        self.pay = int(self.pay * self.raise_amt)

class Developer(Employee):
    pass

class Manager(Employee):
    pass

dev_1 = Developer('Corey', 'Schafer', 50000)
man_1 = Manager('Test', 'Employee', 60000)

print(dev_1.email)
print(man_1.email)
```

Output:

> Corey.Schafer@email.com   
> Test.Employee@email.com

`Method resolution order`-i görməyin bir yolu da python-un `help` method-undan istifadə etməkdir. Əgər yuxarıdaki kodun sonunda bunu yazsaq:

```python
print(help(Developer))
```

Bu nəticəni alarıq:

```python
Help on class Developer in module __main__:

class Developer(Employee)
 |  Developer(first, last, pay)
 |  
 |  Method resolution order:
 |      Developer
 |      Employee
 |      builtins.object
 |  
 |  Methods inherited from Employee:
 |  
 |  __init__(self, first, last, pay)
 |      Initialize self.  See help(type(self)) for accurate signature.
 |  
 |  apply_raise(self)
 |  
 |  fullname(self)
 |  
 |  ----------------------------------------------------------------------
 |  Data descriptors inherited from Employee:
 |  
 |  __dict__
 |      dictionary for instance variables (if defined)
 |  
 |  __weakref__
 |      list of weak references to the object (if defined)
 |  
 |  ----------------------------------------------------------------------
 |  Data and other attributes inherited from Employee:
 |
 |  raise_amt = 1.04
```

Yuxarıdaki output-un 6-cı sətrindən görə bilərsiniz ki, `Developer` subclass-ının Method resolution orderi necədir. İlkin olaraq lazım olan şey `Developer` subclass-ında axtarılır, bundan sonra `Employee`-də axtarılır. Əgər onda da tapılmazsa, `builtins.object`-də axtarılır.

Siz həmçinin 11-ci sətirdən etibarən `Employee` class-ından inherit olunan method-ları, 30-cu sətirdən etibarən isə inherit olunan data və digər attribute-ları görə bilərsiniz.

İndi isə gəlin baxaq ki, hər bir subclass-a necə öz method və attribute-larını əlavə edə bilərik. Əsas kodun 2-ci sətrindən görə biləcəyiniz kimi, `Employee` classında `raise_amt` = 1.04 \(yəni 4 faiz\) təyin olunub.

```python
    raise_amt = 1.04
```

Maaş artımı üçün yazdığımız funksiya isə bucürdür:

```python
    def apply_raise(self):
        self.pay = int(self.pay * self.raise_amt)
```

Nümunə kimi göstərəsi olsaq, görərik ki, 

```python
# Yuxarıdakı kodlar çox yer tutmasın deyə kəsilib.

dev_1 = Developer('Corey', 'Schafer', 50000)
man_1 = Manager('Test', 'Employee', 60000)

print(dev_1.pay)
dev_1.apply_raise()
print(dev_1.pay)

# Output:
# 50000
# 52000
```

dev1 -in maaşı 4 faiz artaraq 52000-ə yüksəldi. apply\_raise funksiyasında \(50000 \* 1.04  = 52000\)

Ancaq mən istəyirəm ki, `Manager` subclass-ının maaş artımı başqa, `Developer` subclass-ınınki isə başqa olsun. Bu halda nə etməliyəm? Bu halda hər bir class-da həmin adda istədiyimiz dəyərdə attribute yaratmaq lazımdır.



```python
# Yuxarıdakı kodlar çox yer tutmasın deyə kəsilib.

class Developer(Employee): 
    raise_amt = 1.06 # Developer subclass-ının özünə məxsus maaş artımı faizi.

class Manager(Employee):
    raise_amt = 1.10 # Manager subclass-ının özünə məxsus maaş artımı faizi.

dev_1 = Developer('Corey', 'Schafer', 50000)
man_1 = Manager('Test', 'Employee', 60000)

print(dev_1.pay) # Maaş artırmadan maaşları ekrana çap edirəm.
print(man_1.pay) # 

dev_1.apply_raise() # Həm dev_1 həm man_1 maaşlarını qaldırıram. apply_raise() methodu
man_1.apply_raise() # vasitəsiylə.

print(dev_1.pay) # Həm dev_1 həm man_1 Maaş artımından sonrakı maaşlarını ekrana çap
print(man_1.pay) # edirəm.
```

Output:

> 50000  
> 60000  
> 53000  
> 66000

## Subclass-a parent class-da olmayan methodların verilməsi

Fərz edək ki, bizə lazımdır ki, hər bir developer-i yaradarkən onun adı, soyadı, maaşından əlavə həmçinin onun əsas istifadə etdiyi proqramlaşdırma dilini də təyin edək.

```python
dev_1 = Developer('Corey', 'Schafer', 50000)
```

Ancaq bu hal-hazırki kodda mümkün deyil çünki bundan qabaq `print(help(Developer))` yazaraq `Developer` subclass-ının 3 arqument götürdüyünü görmüşdük. 

```python
Help on class Developer in module __main__:

class Developer(Employee)
 |  Developer(first, last, pay)
 
 # Çox yer tutmaması üçün redaktə olunub.
```

Həmin 3 arqument isə `Employee` parent class-ından törəyən arqumentlər idi. Hansı ki, kodun bu hissəsində qeyd olunub. 

```python
    def __init__(self, first, last, pay):
        self.first = first
        self.last = last
        self.email = first + '.' + last + '@email.com'
        self.pay = pay
```

Əgər biz `Developer` subclass-ı üçün ayrıca developerin istifadə etdiyi proqramlaşdırma dilini də daxil etmək istəyiriksə, bunun üçün kodda bucür dəyişiklik etmək lazım gələcək. Biz yuxarıda göstərdiyim kodun hamısını koplayalıb `Developer` subclass-ının içinə də ata bilərik. Ancaq bu kodun təkrar istifadəsinə gətirib çıxaracaq. OOP isə əslində tamamilə təkrar kod istifadəsinin qarşısını almaq üçün istifadə olunur. Beləliklə yeni tam versiya kodumuz bu cür görsənəcək.

```python
class Employee:
    raise_amt = 1.04

    def __init__(self, first, last, pay):
        self.first = first
        self.last = last
        self.email = first + '.' + last + '@email.com'
        self.pay = pay
    
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
    
    def apply_raise(self):
        self.pay = int(self.pay * self.raise_amt)

class Developer(Employee):
    raise_amt = 1.06

    def __init__(self, first, last, pay, prog_lang):
        super().__init__(first, last, pay)
        self.prog_lang = prog_lang

class Manager(Employee):
    raise_amt = 1.10

dev_1 = Developer('Corey', 'Schafer', 50000, 'Python')
man_1 = Manager('Test', 'Employee', 60000)

print(dev_1.prog_lang)
```

Bizim taskımız bundan ibarət idi ki, proqramistləri təyin edəndə həmçinin həmin proqramistin istifadə etdiyi proqramlaşdırma dilini də təyin edə bilək. Bunu ümumi `Employee` classı üçün kodlamağımız mənasız olardı, çünki bu `Employee` class-ının `Developer` subclass-ından başqa bütün digər subclass-larında lazımsız `prog_lang` atributu yaradacaqdı. Bunun qarşısını almaq üçün bizə lazımdır ki, `Developer` subclass-ının içində init yaradaq. 

Xatırlayırsınzısa `method resolution order` haqqında danışanda qeyd etmişdim ki compiler subclass-ın init methodu olmadıqda onun parent class-ına keçir. 

Sətir 19-da görə bilərsiniz ki, `Developer` sublcass-ının içində yeni init methodu yaratmışıq və o `prog_lang` atributunu da istəyir. 

## super\(\) built-in keyword

Bəs 20-ci sətirdə yazdığımız super\(\) nə deməkdir?

`super()` bizə imkan verir ki, parent class-da olan init methodunun hamısını bir də kopyalamayaq. Onu kopyalamaq əvəzinə `super()` yazmaqla biz parent class-ındaki init methodunda nə təyin olunubsa hamısını işlədə bilirik. Parent class-dakı `init` methodunu çəkməyin bir neçə yolu var. Onların yazılış fərqlərini aşağıdakı tab-lara baxaraq görə bilərsiniz.

{% hint style="danger" %}
Nəzərinizə çatdırmaq istəyirəm ki, aşağıdakı kodların üçü də tamamilə eyni işi görür.
{% endhint %}

{% tabs %}
{% tab title="Kod parçası super\(\) ilə" %}
```python
class Developer(Employee):
    raise_amt = 1.06

    def __init__(self, first, last, pay, prog_lang):
        self.prog_lang = prog_lang
        
        super().__init__(first, last, pay)
```
{% endtab %}

{% tab title="Kod parçası super\(\)-siz" %}
```python
class Developer(Employee):
    raise_amt = 1.06

    def __init__(self, first, last, pay, prog_lang):
        self.prog_lang = prog_lang
        
        
        self.first = first
        self.last = last
        self.email = first + '.' + last + '@email.com'
        self.pay = pay   
```
{% endtab %}

{% tab title="Kod parçası class adı ilə" %}
```python
class Developer(Employee):
    raise_amt = 1.06

    def __init__(self, first, last, pay, prog_lang):
        self.prog_lang = prog_lang
        
        Employee.__init__(self, first, last, pay)
```
{% endtab %}
{% endtabs %}

İndi isə gəlin `Manager` subclass-ına elə dəyişikliklər edək ki, managerlərin digər işçilərdən kimi idarə etdiyi təyin edilə bilsin. `Developer` subclass-ında yazdığımız kimi `Manager` subclass-ında da `super()` işlətməliyik çünki Manager subclassına aid olan insanların da adı, soyadı və maaşı olacaq. Bundan başqa, Manager-in manage etdiyi insanları özündə saxlaması üçün, `add_emp` metodunu, özündəki siyahıdan çıxartması üçün  `remove_emp` methodunu, özündəki siyahını çap etməsi üçün isə `print_emp` methodunu yazaq. 

```python
# Kodun yuxarı hissəsi kəsilib.
class Manager(Employee):
    raise_amt = 1.10
    # Aşağıda employees=None olmasının səbəbi budur ki, PEP8 standartına görə
    # arqument olaraq Mutable object daxil etmək məqsədəuyğun deyil.
    # Bunun yerinə employees variable-nı None-a bərabər edib if vasitəsi ilə
    # onu dictionary-ə çevirmək lazımdır.
        
    def __init__(self, first, last, pay, employees=None):
        super().__init__(first, last, pay) # Employee classından atributlar inherit olur.
        if employees is None: 
            self.employees = []
        else:
            self.employees = employees

    # Əgər daxil edilən dəyər employees-də olmazsa, həmin dəyəri employees-ə əlavə et.
    def add_emp(self, emp):
        if emp not in self.employees:
            self.employees.append(emp)
    
    # Əgər daxil edilən dəyər employees-də mövcuddursa, onu employees-dən sil.
    def remove_emp(self, emp):
        if emp in self.employees:
            self.employees.remove(emp)

    # Bu method manager-in manage etdiyi şəxslərin siyahısını çıxardır.
    def print_emp(self):
        # İşçisi ekrana çıxacaq olan managerin fullname-i çap olunur birinci növbədə.
        print('{} is managing these people'.format(self.fullname())) 
        for emp in self.employees: # employees siyahısındakı hər bir employeenin 
            print('->', emp.fullname()) # fullname-ini ekrana çap edir.

dev_1 = Developer('Corey', 'Schafer', 50000, 'Python')
emp_1 = Employee('Shi', 'Fu', 50000)
man_1 = Manager('Sue', 'Smith', 60000)


man_1.add_emp(dev_1) # man_1-in manage etdiyi insan siyahısına dev_1-i əlavə edir.
man_1.add_emp(emp_1) # man_1-in manage etdiyi insan siyahısına emp_1-i əlavə edir.
man_1.print_emp()    # man_1-in manage etdiyi insan siyahısını ekrana çap edir.
man_1.remove_emp(dev_1) # dev_1-i man_1-in manage etdiyi insanlar siyahısından silir.
man_1.print_emp()       # man_1-in manage etdiyi insan siyahısını ekrana çap edir.
```

Output:

> Sue Smith is managing these people   
> -&gt; Corey Schafer  
> -&gt; Shi Fu  
> Sue Smith is managing these people   
> -&gt; Shi Fu

Yuxarıdakı misalda kod parçalarının nə etdiyini comment şəklində izah etmişəm.

## isinstance\(\) və issubclass\(\)

Bu methodların ikisi də cavab olaraq `True` vəya `False` qaytarır.

`isinstance(man1, Manager)` dediyimizdə, əgər man\_1 Manager-in instance-ı olarsa True, olmazsa False qaytaracaq.  
`issubclass(Manager, Employee)` dediyimizdə, əgər Manager classı Employee classının subclass-ıdırsa True, deyilsə False qaytaracaq.

```python
print(isinstance(man_1, Manager))        # True
print(isinstance(man_1, Employee))       # True
print(isinstance(man_1, Developer))      # False
print(issubclass(Developer, Employee))   # True
print(issubclass(Manager, Employee))     # True
print(issubclass(Manager, Developer))    # False
```

Son olaraq ümumi kod parçasını atıram ki, kimdəsə çətinlik varsa baxa bilsin:

```python
class Employee:
    raise_amt = 1.04

    def __init__(self, first, last, pay):
        self.first = first
        self.last = last
        self.email = first + '.' + last + '@email.com'
        self.pay = pay
    
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
    
    def apply_raise(self):
        self.pay = int(self.pay * self.raise_amt)

class Developer(Employee):
    raise_amt = 1.06

    def __init__(self, first, last, pay, prog_lang):
        super().__init__(first, last, pay)
        self.prog_lang = prog_lang

class Manager(Employee):
    raise_amt = 1.10
    
    def __init__(self, first, last, pay, employees=None):
        super().__init__(first, last, pay)
        if employees is None:
            self.employees = []
        else:
            self.employees = employees

    def add_emp(self, emp):
        if emp not in self.employees:
            self.employees.append(emp)

    def remove_emp(self, emp):
        if emp in self.employees:
            self.employees.remove(emp)

    def print_emp(self):
        print('{} is managing these people'.format(self.fullname()))
        for emp in self.employees:
            print('->', emp.fullname())

dev_1 = Developer('Corey', 'Schafer', 50000, 'Python')
emp_1 = Employee('Shi', 'Fu', 50000)
man_1 = Manager('Sue', 'Smith', 60000)


print(isinstance(man_1, Manager))   # True
print(isinstance(man_1, Employee))  # True
print(isinstance(man_1, Developer)) # False
print(issubclass(Developer, Employee))  # True
print(issubclass(Manager, Employee))  # True
print(issubclass(Manager, Developer)) # False


```

Hörmətlə.

