# O'ZGARUVCHILAR VA MA'LUMOT TURLARI

## O'zgaruvchi nima?

**O'zgaruvchi (variable)** — kompyuter xotirasida biror ma'lumotni saqlab turadigan, nom berilgan "quti" hisoblanadi. Har safar bu nomni ishlatganimizda, Python xotiradagi tegishli ma'lumotni oladi.

```python
ism = "Aziz"
yosh = 15
print(ism)
print(yosh)
```

```
Aziz
15
```

Bu yerda `ism` va `yosh` — o'zgaruvchilar, `=` esa **tenglashtirish (assignment) operatori** bo'lib, o'ngdagi qiymatni chapdagi o'zgaruvchiga yuklaydi.

## O'zgaruvchi nomlash qoidalari

- Faqat harflar, raqamlar va pastki chiziq (`_`) dan iborat bo'lishi mumkin
- Raqamdan boshlanishi **mumkin emas** (`1ism` — xato, `ism1` — to'g'ri)
- Katta-kichik harflar farqlanadi (`Ism` va `ism` — ikki xil o'zgaruvchi)
- Python'ning zaxira so'zlaridan foydalanib bo'lmaydi (`print`, `if`, `for` va h.k.)
- An'anaviy ravishda **snake_case** uslubi qo'llaniladi: `mening_ismim`, `talaba_soni`

```python
# to'g'ri nomlar
yosh = 20
talaba_soni = 30
_vaqtinchalik = "test"

# noto'g'ri nomlar (xatolik beradi)
# 1son = 5
# mening-ismim = "Vali"
```

## Ma'lumot turlari (Data Types)

Python'da har bir qiymatning o'z **turi** bor. Asosiy turlar:

| Tur | Nomi | Misol |
|---|---|---|
| `int` | Butun son | `5`, `-12`, `1000` |
| `float` | Kasr son | `3.14`, `-0.5` |
| `str` | Matn (string) | `"salom"`, `'Toshkent'` |
| `bool` | Mantiqiy (True/False) | `True`, `False` |
| `list` | Ro'yxat | `[1, 2, 3]` |
| `tuple` | Kortej | `(1, 2, 3)` |
| `dict` | Lug'at | `{"kalit": "qiymat"}` |
| `NoneType` | Bo'sh qiymat | `None` |

Turini bilish uchun `type()` funksiyasidan foydalaniladi:

```python
son = 10
kasr = 3.14
matn = "Salom"
mantiqiy = True

print(type(son))
print(type(kasr))
print(type(matn))
print(type(mantiqiy))
```

```
<class 'int'>
<class 'float'>
<class 'str'>
<class 'bool'>
```

## Dinamik tiplash (Dynamic Typing)

Python'da o'zgaruvchining turini oldindan e'lon qilish shart emas — Python buni avtomatik aniqlaydi. Bundan tashqari, bitta o'zgaruvchi umrida turli xil turdagi qiymatlarni qabul qilishi mumkin:

```python
narsa = 10          # int
print(type(narsa))
narsa = "o'n"        # endi str
print(type(narsa))
narsa = 10.0         # endi float
print(type(narsa))
```

```
<class 'int'>
<class 'str'>
<class 'float'>
```

Bu C++ yoki Java kabi **statik tiplangan** tillardan farqli xususiyat — u yerda o'zgaruvchi turi e'lon qilingandan keyin o'zgarmaydi.

## Turlarni bir-biriga aylantirish (Type Casting)

Ba'zan bir turdagi ma'lumotni boshqasiga aylantirish kerak bo'ladi. Bu uchun `int()`, `float()`, `str()`, `bool()` funksiyalaridan foydalaniladi.

```python
son_matn = "25"
son = int(son_matn)     # matnni songa aylantirish
print(son + 5)
```

```
30
```

```python
son = 10
matn = str(son)         # sonni matnga aylantirish
print("Mening yoshim " + matn)
```

```
Mening yoshim 10
```

**Diqqat:** Agar matn ichida son bo'lmasa, `int()` funksiyasi xatolik beradi:

```python
son = int("yigirma")   # ValueError xatoligi beradi
```

## input() funksiyasi va turlar

`input()` funksiyasi foydalanuvchidan qanday ma'lumot kiritilishidan qat'iy nazar, **har doim `str` (matn) turida** qaytaradi. Shu sababli sonlar bilan ishlash uchun uni albatta aylantirish kerak.

```python
yosh = input("Necha yoshdasiz? ")
print(type(yosh))          # <class 'str'> — hatto 15 kiritilsa ham!

yosh = int(yosh)
print(type(yosh))          # endi <class 'int'>
print(yosh + 5)             # endi matematik amal bajarish mumkin
```

## None turi

`None` — Python'da "qiymat yo'q" yoki "bo'sh" degan maxsus tur. U `0` ham, `""` (bo'sh matn) ham emas — bu butunlay alohida tushuncha.

```python
natija = None
print(natija)
print(type(natija))
```

```
None
<class 'NoneType'>
```

`None` ko'pincha o'zgaruvchini "hali qiymati yo'q" holatda e'lon qilishda yoki funksiya hech narsa qaytarmaganda ishlatiladi.

## Bir qatorda bir nechta o'zgaruvchi

```python
ism, yosh, shahar = "Laylo", 22, "Samarqand"
print(ism, yosh, shahar)

# barchasiga bitta qiymat
a = b = c = 0
print(a, b, c)
```

```
Laylo 22 Samarqand
0 0 0
```

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. `ism`, `yosh`, `shahar` nomli o'zgaruvchilar yarating va ularni bitta `print()` qatorida chiqaring.
2. Ikkita sonni o'zgaruvchilarga yozing va ularning yig'indisini hisoblovchi dastur yozing.
3. `input()` orqali foydalanuvchi ismini so'rang va "Salom, [ism]!" deb chiqaring.
4. Har bir asosiy ma'lumot turi (`int`, `float`, `str`, `bool`) uchun bittadan o'zgaruvchi yarating va `type()` orqali turlarini ekranga chiqaring.
5. Bitta o'zgaruvchiga ketma-ket 3 xil turdagi qiymat bering va har safar uning turini chop eting.

🟡 **O'rta daraja**

6. Foydalanuvchidan ikkita son (matn ko'rinishida) kiritishni so'rang, ularni `int()` ga aylantirib, yig'indisi, ayirmasi, ko'paytmasi va bo'linmasini chiqaring.
7. Foydalanuvchidan tug'ilgan yilini so'rang va joriy yildan ayirib, yoshini hisoblab chiqaruvchi dastur yozing.
8. Nega `"5" + "5"` natijasi `"55"` bo'ladi-yu, `5 + 5` natijasi `10` bo'ladi? Buni tushuntirib, kod orqali isbotlang.

---
