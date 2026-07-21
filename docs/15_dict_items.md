# LUG'AT ELEMENTLARI BILAN ISHLASH

Lug'at ishida ro'yxat, lug'at ichida lug'at?

Avvalgi darslarimizda lug'at bilan tanishdik va  lug'atdagi elemrntlarniga kalit bo'yicha murojaat qilishni o'rgandik. Lug'atlar katta yoki kichik bo'lishi mumkin. Ba'zida lug'atdagi barcha kalitlarni yoki qiymatlarni bilmasligimiz mumkin. Bunday holatda qanday yo'l tutamiz?

Ushbu darsimizda lug'at elementlarini turli usullar yordamida chiqarishni o'rganamiz.

#### .items() METODI

Ushbu metod yordamida lug'atvichidagi barcha kalit-qiymatvjuftlaiklarini ko'rishimiz mumkin.


```python
uy_0={
    'turi' : 'uchastka',
    'maydoni':20,
    'kengligi':50,
    'uzunligi':40,
    'qavat':1,
    "ta'miri":"o'rtacha",
    'xona':5
}

print(uy_0)
```

    {'turi': 'uchastka', 'maydoni': 20, 'kengligi': 50, 'uzunligi': 40, 'qavat': 1, "ta'miri": "o'rtacha", 'xona': 5}
    

Bu metodni to'g'ridan-to'g'ri emas, for tsikli yordamida chaqirish orqali lug'atdagi barcha elementlarni tushunarliroq ko'rishimiz mumkin.


```python
for kalit, qiymat in uy_0.items():
    print(f"Kalit : {kalit}")
    print(f"Qiymat : {qiymat}\n")
```

    Kalit : turi
    Qiymat : uchastka
    
    Kalit : maydoni
    Qiymat : 20
    
    Kalit : kengligi
    Qiymat : 50
    
    Kalit : uzunligi
    Qiymat : 40
    
    Kalit : qavat
    Qiymat : 1
    
    Kalit : ta'miri
    Qiymat : o'rtacha
    
    Kalit : xona
    Qiymat : 5
    
    

Yuqoridagi kodda, uy_0 lug'atidagi har bir kalit va qiymat juftligini konsolga chiqardik. E'tibor bering, for tsiklida biz bir emas ikkita o'zgaruvchi yaratib oldik (kalit va qiymat).

Bu usul ba'zi lug'atlardagi ma'lumotlarni chiroyli ko'rinishda chiqarish uchun juda qo'l keladi.


```python
mashinalar={
    'aziz' : 'nexia',
    'laziz' : 'matiz',
    'davron': 'damas',
    'shavkat':'spark',
    'abror':'matiz',
    'asror':'malibu', 
    'anvar':'muravey'
}

for k, q in mashinalar.items():
    print(f'{k.title()}ning mashinasi : {q.title()}.\n')
```

    Azizning mashinasi : Nexia.
    
    Lazizning mashinasi : Matiz.
    
    Davronning mashinasi : Damas.
    
    Shavkatning mashinasi : Spark.
    
    Abrorning mashinasi : Matiz.
    
    Asrorning mashinasi : Malibu.
    
    Anvarning mashinasi : Muravey.
    
    

#### .keys() METODI

Agar lug'atdagi kalit so'zlarni ko'rish talab qilinsa, **.keys()** metodidan foydalanishimiz mumkin.


```python
ichimliklar={
    'coca-cola':15000,
    'pepsi':15000,
    'gorilla':13000,
    'sharbat': 15000,
    'oddiy suv':3000,
    'millliy cola':13000
}

print(ichimliklar.keys())
```

    dict_keys(['coca-cola', 'pepsi', 'gorilla', 'sharbat', 'oddiy suv', 'millliy cola'])
    


```python
print('Mavjud ichimliklar :')
for suv in ichimliklar.keys():
    print(suv.title())
```

    Mavjud ichimliklar :
    Coca-Cola
    Pepsi
    Gorilla
    Sharbat
    Oddiy Suv
    Millliy Cola
    

Yuqoridagi kodimizda, for tsiklida .keys() metodini ishlatmasak ham huddi shu natija chiqadi.

for tsikli va if sharti yordamida lug'atdagi biror qiymatlarni alohida chiqarishimiz ham mumkin:


```python
olamiz=['coca-cola', 'pepsi', 'fanta', 'mors']

for ichimlik in ichimliklar:
    if ichimlik in olamiz:
        print(f"{ichimlik.title()} {ichimliklar[ichimlik]} so'm.")
```

    Coca-Cola 15000 so'm.
    Pepsi 15000 so'm.
    

Yuqoridagi kodga e'tibor bering. Biz avval olamiz degan ro'yxat yasab oldik (ichimliklar olyapmiz), keyin esa ichimliklar lug'atidagi har bir ishimlikni bizdagi olamiz ro'yxati bilan solishtirdik, Agar ichimlik bizdagi olamiz ro'yxatida bo'lsa, uning narxini konsolga chiqardik.

Quyidagi misolda esa aksincha, olamiz ro'yxatiddagi har bir elementni ichimliklar bilan solishtiramiz va ichimlik mavjuda bo'lmasa, do'konga murojaat qoldiramiz:


```python
for ichimlik in ichimliklar:
    if ichimlik not in olamiz:
        print(f"Iltimos, do'koningizga {ichimlik.title()} ham olib keling.")
```

    Iltimos, do'koningizga Gorilla ham olib keling.
    Iltimos, do'koningizga Sharbat ham olib keling.
    Iltimos, do'koningizga Oddiy Suv ham olib keling.
    Iltimos, do'koningizga Millliy Cola ham olib keling.
    

#### LUG'AT ELEMENTLARINI TARTIB BILAN CHIQARISH

Pythonda lug'at elementlari siz (foydalanuvchi) kiritgan tartibda saqlanadi. Agar lug'at elementlarini alifbo tartibida chiqarish talab qilinsa, sorted() funksiyasidan foydalanamiz.


```python
print("Mavjud ichimliklar :")
for ichimlik in sorted(ichimliklar):
    print(ichimlik.title())
```

    Mavjud ichimliklar :
    Coca-Cola
    Gorilla
    Millliy Cola
    Oddiy Suv
    Pepsi
    Sharbat
    

#### .values() METODI

Agar lug'atdagi qiymatlarni chiqarish talab qilinsa .values() metodidan foydalanamiz.


```python
print(ichimliklar.values())
```

    dict_values([15000, 15000, 13000, 15000, 3000, 13000])
    


```python
print(f"Do'stlarim quyidagi mshinalarni minishadi :")
for mashina in mashinalar.values():
    print(mashina.title())
```

    Do'stlarim quyidagi mshinalarni minishadi :
    Nexia
    Matiz
    Damas
    Spark
    Matiz
    Malibu
    Muravey
    

Yuqooridagi usul bilan qiymatlarga murojaat qilganimizda barcha qiymatlar chiqib keladi. Agar biron qiymat ko'p takrorlangan bo'lsa natijada ham takrorlanadi:


```python
mashinalar['davron']='muravey'
mashinalar['akbar']='muravey'
mashinalar['mavlon']='muravey'

print("Do'stlarim minadigan mashinalar :")
for mashina in mashinalar.values():
    print(mashina.title())
```

    Do'stlarim minadigan mashinalar :
    Nexia
    Matiz
    Muravey
    Spark
    Matiz
    Malibu
    Muravey
    Muravey
    Muravey
    

Yuqoridagi natijaga e'tibor bersangiz muravey bir necha bor chiqib keldi
va bu modellar bir necha bor qayta-qayta konsolga chiqib keldi.

Buning oldini olish uchun set() funksiyasidan foydalanamiz:


```python
print("Do'stlarim minadigan mashinalar :")
for mashina in set(mashinalar.values()):
    print(mashina.title())
```

    Do'stlarim minadigan mashinalar :
    Spark
    Muravey
    Malibu
    Nexia
    Matiz
    

Pythonda set yana bir ma'lumot turi bo'lib, ro'yxat va lug'at kabi bir nechta elementlarni saqlashga mo'ljallangan. Lug'at va ro'yxatdan farqli ravishda, set ichidagi elementlar biror tartibda saqlanmaydi, va ularga indeks orqali murojat qilib bo'lmaydi. Shuningdek, set ichida bir hil elementlar bo'lmaydi.

#### Topshiriqlar

1. .items() metodi yordamida juftliklarni olish
Topshiriq: Berilgan student = {"name": "Malika", "age": 21, "faculty": "Matematika"} lug'atining barcha kalit va qiymat juftliklarini .items() metodi yordamida ekranga chiqaring.

2. for siklida .items() orqali iteratsiya qilish
Topshiriq: scores = {"math": 85, "physics": 90, "chemistry": 78} lug'atini for sikli va .items() yordamida aylanib, har bir fan va uning bahosini "Fan: [fan], Baho: [baho]" ko'rinishida chop eting.

3. Qiymatlar bo'yicha shart tekshirish
Topshiriq: prices = {"apple": 12000, "banana": 8000, "bread": 4000, "milk": 10000} lug'atidan .items() yordamida narxi 9000 so'mdan qimmat bo'lgan mahsulotlar nomini ekranga chiqaring.

4. Kalit va qiymatlarni alohida o'zgaruvchilarga ajratish
Topshiriq: person = {"first_name": "Jasur", "last_name": "Karimov", "age": 25} lug'atini .items() yordamida siklga qo'yib, har bir iteratsiyada kalit va qiymatni alohida o'zgaruvchilarga (key, value) qabul qilib chop eting.

5. .items() natijasini ro'yxatga (list) o'tkazish
Topshiriq: data = {"a": 1, "b": 2, "c": 3} lug'atining .items() natijasini list() yordamida ro'yxatga aylantiring va uning 0-indeksidagi elementni ekranga chiqaring.

6. Shartli ravishda qiymatni yangilash
Topshiriq: employees = {"Ali": 500, "Vali": 700, "Sardor": 450} lug'atidagi xodimlarning maoshini .items() orqali tekshirib, agar maoshi 600 dan kam bo'lsa, uni 10 foizga oshirilgan holda yangi lug'atga yozing.

7. Kalit uzunligini hisoblash
Topshiriq: colors = {"red": "#FF0000", "green": "#00FF00", "blue": "#0000FF"} lug'atidan .items() yordamida foydalanib, uzunligi 4 ta harfdan iborat bo'lgan kalitlar va ularning rang kodlarini chiqaring.

8. Ikki lug'at elementlarini solishtirish
Topshiriq: Berilgan dict1 = {"a": 10, "b": 20} va dict2 = {"a": 10, "b": 25} lug'atlarining .items() natijalarini solishtirib, qaysi juftliklar bir xil ekanligini aniqlang.

9. .items() yordamida qiymatlar yig'indisini topish
Topshiriq: expenses = {"food": 150000, "transport": 50000, "entertainment": 80000} lug'atidagi barcha qiymatlar (xarajatlar) yig'indisini .items() yordamida hisoblang.

10. Juftliklarni teskari o'girish (Invert Dictionary)
Topshiriq: original = {1: "one", 2: "two", 3: "three"} lug'atining .items() natijasidan foydalangan holda, kalit va qiymatlarning o'rnini almashtirib yangi lug'at hosil qiling.

