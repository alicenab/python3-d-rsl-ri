# Exceptions

Kod parçası işə düşdüyü zaman xətalar yaratması həm müştəri həm proqramistin istəyincə olmur. Gözlənilməz hallara qarşı əvvəlcədən halların nəzərə alınması daha məqsədəuyğundur. Məsələn, tutalım ki, elə bir proqram təminatı yazmısınız ki,&#x20;

Qarşılaşa biləcəyimiz error tiplərindən bəzilərini aşağıda sadalamağa çalışmışam.

`ZeroDivisionError`, `ValueError`, `TypeError`, `AttributeError`, `SyntaxError`

```python
try:
    value = int(input('Enter a natural number: '))
    print('The reciprocal of', value, 'is', 1/value)        
except ValueError:
    print('I do not know what to do.')    
except ZeroDivisionError:
    print('Division by zero is not allowed in our Universe.') 
```



Başqa bir nümunəyə diqqət edək. kodda bilərək `print()` yerinə `prin()` yazılıb ancaq python kodu işə düşdüyü zaman həmin hissəni oxumadığı üçün bu səhvi görmür. `0` daxil etsək ekrana Zero çap olunur.

```
temperature = float(input('Enter current temperature:'))

if temperature > 0:
    print("Above zero")
elif temperature < 0:
    prin("Below zero")
else:
    print("Zero")
```

