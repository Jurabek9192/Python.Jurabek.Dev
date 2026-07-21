# NESTING

Lug'at ichida ro'yxat, ro'yxat ichida lug'at?

#### NESTING

Ba'zida dasturlash jarayonida lug;atning ichida ro'yxatlar yoki boshqa lug;atni, yoki aksincha ro'yxat ichida lug'atni saqlash ham qo'l kelishi mumkin. Bu ingliz tilida **Nesting** deyiladi. Nesting Pythondagi foydali qususiyatlardan biri.

Keling, bunga bir nechta misollar ko'ramiz.

#### LUG'ATLAR RO'YXATI

Biz avvalgi darsimizda lug'atlar bilan tanishib ularni mashinalar lu'ati sifatida saqlashni ko'rgan edik.

Agar bizdan bunday qo'stlar va mashinalar ro'yxati ko'p bo'lsa bunda biz har bir do'st va mashinaning o'zi uchun alohida lug'at qilishimiz tabiiy, lekin bu luga'atlar bilan ishlash qiyinchilik tug'dirishi mumin. Shunday xolatda barcha lug'atlarni (mashinalarni) bitta ro'yxatga joylab, ular ustida turli amallar bajarish mumkin.

Keling quyidagi misolni ko'ramiz, bazamizda bir necha mashinalar bor. Har bir mashina alohida lug'at shaklida.


```python
car0 = {
        'model':'lacetti',
        'rang':'oq',
        'yil':2018,
        'narh':13000,
        'km':50000,
        'korobka':'avtomat'
        }

car1 = {
        'model':'nexia 3',
        'rang':'qora',
        'yil':2015,
        'narh':9000,
        'km':89000,
        'korobka':'mexanika'
        }

car2 = {
        'model':'gentra',
        'rang':'qizil',
        'yil':2019,
        'narh':15000,
        'km':20000,
        'korobka':'mexanika'
        }
```

Agar biz har bir lug'atga alohida murojaat qiladigan bo'lsak, lug'atlarning nomlarni yodlab qolishimiz talab qilinar edi:


```python
car=car0
print(f"{car['model'].title()},\
      {car['rang']} rang,\
        {car['yil']}-yil, {car['narh']}$")

car=car1
print(f"{car['model'].title()},\
      {car['rang']} rang,\
        {car['yil']}-yil, {car['narh']}$")

car=car2
print(f"{car['model'].title()},\
      {car['rang']} rang,\
        {car['yil']}-yil, {car['narh']}$")
```

    Lacetti,      oq rang,        2018-yil, 13000$
    Nexia 3,      qora rang,        2015-yil, 9000$
    Gentra,      qizil rang,        2019-yil, 15000$
    

Keling barcha avtolarni bitta ro'yxatga joylaymiz va for tsikli yordamida birma-bir konsolga chiqaramiz:


```python
cars = [car0, car1, car2]
for car in cars:
    print(f"{car['model'].title()}, "
          f"{car['rang']} rang, "
          f"{car['yil']}-yil, {car['narh']}$")
```

    Lacetti, oq rang, 2018-yil, 13000$
    Nexia 3, qora rang, 2015-yil, 9000$
    Gentra, qizil rang, 2019-yil, 15000$
    

E'tibor bering ishimiz bir muncha yengillashdi kodimiz ham qisqardi. Natija esa bir xil.

Endi biz ro'yxat ichidagi istalgan lug'atga indeks bo'yicha murojaat qilishimiz mumkin (bunda lug'atning nomini yodlab qolishimiz shart emas).


```python
print(cars[0])
```

    {'model': 'lacetti', 'rang': 'oq', 'yil': 2018, 'narh': 13000, 'km': 50000, 'korobka': 'avtomat'}
    

Biror lug'atdagi elementga murojaat qilish uchun esa quyidagi usuldan foydalanishimiz mumkin:


```python
print(cars[0]['model'])
```

    lacetti
    


```python
print(f"{cars[2]['rang'].title()}\n"
      f"{cars[2]['model'].title()}")
```

    Qizil
    Gentra
    

for tsikli yordamida biz bo'sh lug'atlar yo'rxatini ham yaratib olishimiz mumkin:


```python
malibus=[]

for n in range(10):
    new_car={
        'model' : 'malibu',
        'rang': None,
        'yil': 2020,
        'narh': None,
        'km':0,
        'korobka': 'avto'
    }

    malibus.append(new_car)
```

Yuqoridagi misolda biz 10 ta Malibu mashinasidan iborat ro'yxat tuzdik. E'tibor qiling, 'rang' kalitiga qiymat bermadik va None deb qoldirdik. Endi ishlab chiqqarish jarayonida mashinalarga turli ranglarni berishimiz mumkin. Misol uchun birinchi 3 ta mashinaga qizil rang beramiz.


```python
for malibu in malibus[:3]:
    malibu['rang']='qizil'
```

Keyingi 3 tasiga esa qora:


```python
for malibu in malibus[3:6]:
    malibu['rang']='qora'
```

Oxirgi 4 ta avtoni qora lekin karobkasini mexanika qilamiz:


```python
for malibu in malibus[6:]:
    malibu['rang']='qora'
    malibu['korobka']='mexanika'
```

Keling endi mashinalarning korobkasidan kelib chiqqan holda narx belgilaymiz:


```python
for malibu in malibus:
    if malibu['korobka']=='aavto':
        malibu['narh']=40000
    else:
        malibu['narh']=35000
        
```

Endi mashinalarni konsolga chiqarib ko'raylik:


```python
print(malibus)
```

    [{'model': 'malibu', 'rang': 'qizil', 'yil': 2020, 'narh': 35000, 'km': 0, 'korobka': 'avto'}, {'model': 'malibu', 'rang': 'qizil', 'yil': 2020, 'narh': 35000, 'km': 0, 'korobka': 'avto'}, {'model': 'malibu', 'rang': 'qizil', 'yil': 2020, 'narh': 35000, 'km': 0, 'korobka': 'avto'}, {'model': 'malibu', 'rang': 'qora', 'yil': 2020, 'narh': 35000, 'km': 0, 'korobka': 'avto'}, {'model': 'malibu', 'rang': 'qora', 'yil': 2020, 'narh': 35000, 'km': 0, 'korobka': 'avto'}, {'model': 'malibu', 'rang': 'qora', 'yil': 2020, 'narh': 35000, 'km': 0, 'korobka': 'avto'}, {'model': 'malibu', 'rang': 'qora', 'yil': 2020, 'narh': 35000, 'km': 0, 'korobka': 'mexanika'}, {'model': 'malibu', 'rang': 'qora', 'yil': 2020, 'narh': 35000, 'km': 0, 'korobka': 'mexanika'}, {'model': 'malibu', 'rang': 'qora', 'yil': 2020, 'narh': 35000, 'km': 0, 'korobka': 'mexanika'}, {'model': 'malibu', 'rang': 'qora', 'yil': 2020, 'narh': 35000, 'km': 0, 'korobka': 'mexanika'}]
    

#### LUG'AT ICHIDA RO'YXAT

Bir kalitga bir nechta qiymatlar berish talab qilinganda, qiymatlarni ro'yxat ko'rinishida yozish o'rinlidir. Misol uchun, bir tashkilotda bir nechta dasturchilar ishlaydi va har bir dasturchi turli dasturlash tillarini biladi. Keling dasturshilar lug'atini tuzamiz va har bir dasturchi haqidagi ma'lumotni chiqaramiz:


```python
dasturchilar={
    'ali':['python', 'c++'],
    'vali':['html', 'css', 'js'],
    'hasan':['php', 'sql'],
    'husan':['python', 'php'],
    'maryam':['c++', 'c#'],
    'lola':['python', 'golang'],
    'shahlo':['c++', 'c#']
}

for ism, tillar in dasturchilar.items():
    print(f"\n{ism.title()} quyidagi tillarni biladi:")
    for til in tillar:
        print(til.title())
```

    
    Ali quyidagi tillarni biladi:
    Python
    C++
    
    Vali quyidagi tillarni biladi:
    Html
    Css
    Js
    
    Hasan quyidagi tillarni biladi:
    Php
    Sql
    
    Husan quyidagi tillarni biladi:
    Python
    Php
    
    Maryam quyidagi tillarni biladi:
    C++
    C#
    
    Lola quyidagi tillarni biladi:
    Python
    Golang
    
    Shahlo quyidagi tillarni biladi:
    C++
    C#
    

Pythondagi print() funktsiyasi har bir matndan so'ng yangi qator tashlaydi. Buning oldini olish uchun quyidagi usuldan foydalanish mumkin: print(string, end = '')


```python
for ism, tillar in dasturchilar.items():
    print(f"\n{ism.title()} quyidagi tillarni biladi:")
    for til in tillar:
        print(til.title(), end="  ")
```

    
    Ali quyidagi tillarni biladi:
    Python  C++  
    Vali quyidagi tillarni biladi:
    Html  Css  Js  
    Hasan quyidagi tillarni biladi:
    Php  Sql  
    Husan quyidagi tillarni biladi:
    Python  Php  
    Maryam quyidagi tillarni biladi:
    C++  C#  
    Lola quyidagi tillarni biladi:
    Python  Golang  
    Shahlo quyidagi tillarni biladi:
    C++  C#  

#### LUG'AT ICHIDA LUG'AT 

Bunday qilish tavsiya qilinmaydi ammo istisno holatlarda lug'at ichida lug'at qiymatlarni lug'at ko'rinishida saqlash mumkin. Misol uchun ish joyingizdagi hamkasblaringiz haqidagi ma'lumotlarni saqlashda, hamkasbingizning ismi kalit u haqidagi ma'lumootlarni esa lug'at ko'rinishida berlishi mumkin.


```python
hamkasblar={
    'ali':{
        'familiya':'valiyev',
        't_yil':1995,
        'ma\'lumot': 'oliy',
        'tillar':['python', 'c++']
    },
    'vali':{
        'familiya':'aliyev',
        't_yil': 2001,
        'ma\'lumot': 'oliy',
        'tillar': ['html', 'css', 'js']
    },
    'hasan':{
        'familiya': 'husanov',
        't_yil': 1999,
        'ma\'lumot': 'oliy',
        'tillar':['python', 'php']
    }
}
```

Hamkasblar to'g'risidagi ma'lumotlarni esa quyidagicah ko'rish mumkin:


```python
for ism, info in hamkasblar.items():
    print(f"\n{ism.title()} {info['familiya'].title()}, "
          f"{info['t_yil']}-yilda tug'ilgan."
          f"Ma'lumot : {info["ma'lumot"]}.\n"
          "Quyidagi dasturlash tillarini biladi :")
    for til in info['tillar']:
        print(til.upper())
```

    
    Ali Valiyev, 1995-yilda tug'ilgan.Ma'lumot : oliy.
    Quyidagi dasturlash tillarini biladi :
    PYTHON
    C++
    
    Vali Aliyev, 2001-yilda tug'ilgan.Ma'lumot : oliy.
    Quyidagi dasturlash tillarini biladi :
    HTML
    CSS
    JS
    
    Hasan Husanov, 1999-yilda tug'ilgan.Ma'lumot : ['python', 'php'].
    Quyidagi dasturlash tillarini biladi :
    


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    Cell In[27], line 6
          1 for ism, info in hamkasblar.items():
          2     print(f"\n{ism.title()} {info['familiya'].title()}, "
          3           f"{info['t_yil']}-yilda tug'ilgan."
          4           f"Ma'lumot : {info["ma'lumot"]}.\n"
          5           "Quyidagi dasturlash tillarini biladi :")
    ----> 6     for til in info['tillar']:
          7         print(til.upper())
    

    KeyError: 'tillar'


Lug'at ichidagi lug'atlar bir hil tuzilishga ega bo'lgani ishingizni ancha yengillashtiradi, aks holda kodingiz murakkablashib ketishi mumkin.


#### Topshiriqlar

1. Ichma-ich lug'at yaratish (Nested Dictionary)
Topshiriq: students nomli lug'at yarating. Unda ikkita talabaning ismi kalit sifatida kelsin, qiymati esa ularning yoshi va kursi ko'rsatilgan ichki lug'atlardan iborat bo'lsin.

2. Ichma-ich lug'at elementiga murojaat qilish
Topshiriq: Berilgan school = {"class_a": {"teacher": "Anvar", "students_count": 25}, "class_b": {"teacher": "Dilshod", "students_count": 22}} lug'atidan class_a ning o'qituvchisi (teacher) nomini ekranga chiqaring.

3. Ichma-ich lug'atga yangi element qo'shish
Topshiriq: Yuqoridagi school lug'atidagi class_b ichki lug'atiga "room": 405 kalit-qiymat juftligini qo'shing.

4. Lug'at ichidagi ro'yxat (Dictionary with a List)
Topshiriq: programmer = {"name": "Zafar", "skills": ["Python", "SQL", "Docker"], "experience": 3} lug'atidan foydalanib, dasturchining ko'nikmalari ro'yxatidan ikkinchi elementni ekranga chiqaring.

5. Ro'yxat ichidagi lug'atlar (List of Dictionaries)
Topshiriq: Har biri mahsulot nomi va narxini o'z ichiga olgan 3 ta lug'atdan iborat products ro'yxatini tuzing va ularning barchasini for sikli yordamida ekranga chiqaring.

6. Ichma-ich ro'yxatdagi qiymatni o'zgartirish
Topshiriq: Berilgan team = {"leader": {"name": "Jasur", "active": True}, "members": [{"name": "Ali"}, {"name": "Vali"}]} lug'atida birinchi a'zoning (members ro'yxatining 0-indeksi) ismini "Sardor" deb o'zgartiring.

7. Sikl yordamida ichma-ich lug'atni aylanish
Topshiriq: employees = {"hr": {"name": "Malika", "salary": 500}, "it": {"name": "Timur", "salary": 900}} lug'atining tashqi kalitlari va ichki lug'atdagi ism va oyliklarni for sikli yordamida chop eting.

8. Ichma-ich tuzilmadagi shartli tekshiruv
Topshiriq: Talabalar ro'yxatini saqlovchi ichma-ich lug'at tuzing va bahosi 85 dan yuqori bo'lgan talabalarning ismini shart operatori yordamida ajratib oling.

9. Ichma-ich ro'yxatga element qo'shish .append()
Topshiriq: company = {"department": "Development", "staff": ["Aziz", "Bekzod"]} lug'atidagi staff ro'yxatiga .append() yordamida yangi xodimning ismini qo'shing.

10. Uch bosqichli ichma-ich lug'at (Deeply Nested Dictionary)
Topshiriq: Mamlakat, uning poytaxti va poytaxtdagi tuman haqidagi ma'lumotlarni o'z ichiga olgan uch darajali ichma-ich lug'at tuzing va eng ichki elementdagi qiymatga murojaat qiling.
