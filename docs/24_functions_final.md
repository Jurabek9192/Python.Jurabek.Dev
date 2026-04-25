# FUNKSIYALAR

Funksiyalar mavzusiga yakun yasaymiz.

#### lambda YOHUD NOMSIZ FUNKSIYA

Pythonning o'ziga xos xususiyatlaridan biri, nomsiz vaqtinchalik funksiyalar yaratish imkoniyati. Bunday funksiyalarni yaratishda def operatori o'rniga lambda operatori ishlatilgani uchun ham lambda funskiyalar deb ataladi. 

Nomsiz funksiyalar quyidagicha yaratiladi:


```python
lambda argument:ifoda
```




    <function __main__.<lambda>(argument)>



Lambda funksiyalari istalgan miqdordagi argumentlarga ega bo'lishi mumkin, ammo funksiya badanida faqat bitta ifoda mavjud bo'ladi. Ifoda bajariladi va qaytariladi (return operatori shart emas).

Nomsiz funksiyalar biror ifodani tezda hisoblab olishda qulay. Misol uchun quyidgai lambda funksiya ikkita argument qabul qiladi ( 
p
i
,
r
pi,r ), va aylana uzunligini qaytaradi: 


```python
import math
uzunlik=lambda pi, r: 2*pi*r
print(uzunlik(math.pi, 10))
```

    62.83185307179586
    

Kodni tahlil qilamiz, 1-qatorda math modulini chaqirib oldik. 2-qatorda lambda funksiyani yaratdik, funksiyamiz pi va r argumentlarini qabul qilib, 2*pi*r qiymatni qaytaradi. Funksiyaga nom bermadik, lekin unga uzunlik identifikatori orqali murojat qilishimiz mumkin. 3-qatorda funksiyamizga murojat qildik va natijani konsolga chiqardik.

Yana bir misol, topingchi quyidagi funksiyaning vazfiasi nima?


```python
product=lambda x, y : x**y
print(product(3, 2))
```

    9
    

 Shu yerda so'rashingiz mumkin, nima uchun lambda nomsiz deb ataladi, ahir unga hozirgina nomi bilan murojat qildikku?

Gap shundaki, lambda finksiyalarning asl mohiyati boshqa funskiyalar bilan birga ishlaganda ko'rinadi. Keling, tushunarli bo'lishi uchun oddiyroq misol ko'ramiz.

Quyidagi dasturda biz avval daraja degan funksiya yasadik, bu funskiyamiz n degan o'zgaruvchi qabul qilib oladi va funksiya ichidagi noma'lum x ning n-darajasini qaytaradi. Aslida daraja bu funksiya yasaydigan funksya bo'ldi. Xo'sh, undan qanday foydalanamiz? 4-5-qatorlarda esa daraja funksiyasidan yana 2 ta funksiya yasadik: kvadrat - kiritilgan sonning kvadratini hisoblaydi, kub - kiritilgan sonning kubini hisoblaydi.


```python
def daraja(n):
    return lambda x: x**n

kvadrat=daraja(2)
kub=daraja(3)

print(f"3-ning kvadrati {kvadrat(3)} ga , kubi {kub(3)} ga teng.")
```

    3-ning kvadrati 9 ga , kubi 27 ga teng.
    

Lambda funksiyalaridan argument sifatida boshqa funksyani qabul qiluvchi funksiyalar bilan ishlashda ham keng foydalaniladi. Misol uchun map() va filter() funksiyalari.

#### map() FUNKSIYASI

Bu funksiya argument sifatida ro'yxat (yoki lug'at) va boshqa bir funksiyani qabul qilib, ro'yxat elementlariga qabul qilingan funksya yordamida ishlov beradi. Tushunarli bo'lish uchun quyidagi misolni ko'ramiz.


```python
from math import sqrt 

sonlar=list(range(11))
ildizlar=list(map(sqrt, sonlar))
```

Yuqoridagi misolda avval 0 dan 10 gacha sonlar ro'yxatini tuzib oldik, keyin esa map funksiyasiga ro'yxat va sqrt funksiyasini uzatib, ro'yxatdagi barcha sonlarning ildizini hisoblab oldik. 

map() funksiyasi map obyekt qaytargani sababli, qaytgan obyektni ro'yxatga o'tkazib olish uchun list() funksiyasidan foyydalandik.

Yana bir misol ko'ramiz:


```python
sonlar=list(range(11))

def daraja2(x):
    """Berilgan sonning kvadratini qaytaruvchi funksiya."""
    return x*x

print(list(map(daraja2, sonlar)))
```

    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
    

Yuqoridagi misolda biz avval berilgan sonning kvadratini hisoblovchi funksiya yaratib oldik, undan keyin esa map yordamida sonlar ro'yxatidagi elementlarning kvadratini ham hisoblab oldik.

Endi keling huddi shu misolni lambda yordamida yozamiz:


```python
kvadratlar=list(map(lambda x: x*x, sonlar))
print(kvadratlar)
```

    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
    

Yuqoridagi misolda, endi daraja degan funksiyani yaratib o'tirmasdan, to'g'ridan-to'g'ri map() ni ichiga darajani hisoblovchi lambda funksiya uzatdik.

map() funksiyasi bo'lmaganida biz bunday dasturlarni for yordamida yozishimiz kerak bo'lar edi:


```python
kvadratlar=[]
for son in sonlar:
    kvadratlar.append(son*son)
```

map() funksiyasiga bir nechta ro'yxatlar ham uzatish mumkin:


```python
a=[4, 5, 6, 7]
b=[7, 8, 9]
a_plus_b=list(map(lambda x, y : x+y, a, b))
print(a_plus_b)
```

    [11, 13, 15]
    

map() istalgan ko'rinishdagi ma'lumot turlari bilan ishlaydi:


```python
ismlar=['hasan', 'husan', 'olim', 'umid']
print(list(map(lambda matn: matn.upper(), ismlar)))
```

    ['HASAN', 'HUSAN', 'OLIM', 'UMID']
    

#### filter() FUNKSIYA

Bu funksiya ham argument sifatida ro'yxat va boshqa funskiyani qabul qilib oladi va berilgan ro'yxat elementlarini berilgan funksiya yordamida saralaydi. Bunda argument sifatida uzatilgan funksiya mantiqiy qiymat qaytarishi kerak (True yoki False).

Keling bunga ham bir misol ko'ramiz: tasodifiy sonlar ro'yxatidan juft sonalrni ajratib oluvchi dastur yozamiz. Dasturimiz 3 qismdan iborat:

Avvalo, random modulidagi sample() funksiyasi yordamida 0-99 oralig'idagi 10 ta tasodifiy sonlar ro'yxatini tuzib oldik

Berilgan son juft (True) yoki juft emas (False) ekanligini qaytaruvchi funksiya yozdik

filter() fuksiyasiga yangi yaratgan juftmi funksiyasi va tasodifiy sonlar ro'yxatini uzatib, yangi juft_sonlar ro'yxatini shakllantridik


```python
import random as rand

sonlar=rand.sample(range(100), 10)

def juftmi(x):
    """x juft bo'lsa True, aks holda False qaytaradi."""
    return x%2==0

juft_sonlar=list(filter(juftmi, sonlar))
print(sonlar)
print(juft_sonlar)
```

    [87, 78, 33, 26, 57, 94, 1, 30, 23, 91]
    [78, 26, 94, 30]
    

Keling endi shu dasturni lambda yordamida yozamiz:


```python
sonlar=rand.sample(range(100), 10)
juft_sonlar=list(filter(lambda son: son%2==0, sonlar))

print(sonlar)
print(juft_sonlar)

```

    [10, 57, 89, 35, 79, 68, 99, 39, 30, 41]
    [10, 68, 30]
    

Kurib turganingizdek, lambda funksiya yordamida dastur bir muncha qisqaroq chiqadi. Agar juftmi funksiyasi kelajakda shart bo'lmasa, alohida funksiya yaratib o'tirmasdan, bir marttalik lambda funksiyasidan foydalangan afzal.

Keling endi filter() funksiyasi yordamida matnlarni saralashga ham misollar ko'raylik.

Quyidagi dastur mevalar ro'yxatidan b harfiga boshlanuvchi mevalarni ajratib oladi. Bu yerda biz matnlarga tegishli bo'lgan .startswith() metodidan foydalandik. Bu metod, berilgan matn shu harfdan boshlanadimi yoki yo'q tekshiradi va True yoki False qiymat qaytaradi.


```python
mevalar=['olma', 'anor', 'anjir', 'shaftoli', 'o\'rik', 'tarvuz', 'banan']

mevalar_b=list(filter(lambda meva: meva.startswith('b'), mevalar))

print(mevalar_b)
```

    ['banan']
    

Quyidagi dastur esa mevalar ro'yxatidan nomi 5 yoki undan kam harfdan iborat mevalarni saralab oladi.


```python
mevalar2=list(filter(lambda meva: len(meva)<5, mevalar))
print(mevalar)
print(mevalar2)
```

    ['olma', 'anor', 'anjir', 'shaftoli', "o'rik", 'tarvuz', 'banan']
    ['olma', 'anor']
    

Topingchi, quyidagi kod qanday vazifani bajaradi?


```python
mevalarr=list(filter(lambda meva: (meva.startswith('a') and meva.endswith('r')), mevalar))
print(mevalarr)
```
