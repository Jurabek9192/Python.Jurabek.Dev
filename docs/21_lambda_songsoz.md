# 21 — FUNKSIYALAR. LAMBDA VA SO'NGSO'Z

## Lambda — nomsiz, bir qatorlik funksiya

```python
kvadrat = lambda x: x ** 2
print(kvadrat(5))     # 25

qoshish = lambda a, b: a + b
print(qoshish(3, 5))     # 8

# standart qiymat bilan
salomlash = lambda ism, til="uz": f"Salom, {ism}!" if til == "uz" else f"Hello, {ism}!"
```

## Lambda ichida shart (ternary)

```python
juft_yoki_toq = lambda son: "juft" if son % 2 == 0 else "toq"
print(juft_yoki_toq(7))     # toq
```

## map() — har bir elementga funksiya qo'llash

```python
sonlar = [1, 2, 3, 4, 5]

kvadratlar = list(map(lambda x: x**2, sonlar))
print(kvadratlar)          # [1, 4, 9, 16, 25]

# oddiy funksiya bilan ham ishlaydi
def ikki_barobar(x):
    return x * 2
natija = list(map(ikki_barobar, sonlar))

# bir nechta ro'yxat bilan
a = [1, 2, 3]
b = [10, 20, 30]
yigindilar = list(map(lambda x, y: x + y, a, b))
print(yigindilar)     # [11, 22, 33]
```

## filter() — shartga mos elementlarni tanlash

```python
sonlar = list(range(1, 21))

juftlar = list(filter(lambda x: x % 2 == 0, sonlar))
print(juftlar)     # [2, 4, 6, ..., 20]

musbatlar = list(filter(lambda x: x > 0, [-5, 3, -2, 8, -1, 10]))
print(musbatlar)      # [3, 8, 10]
```

## reduce() — barcha elementlarni bitta qiymatga qisqartirish

```python
from functools import reduce

sonlar = [1, 2, 3, 4, 5]

yigindisi = reduce(lambda a, b: a + b, sonlar)
print(yigindisi)     # 15

kopaytmasi = reduce(lambda a, b: a * b, sonlar)
print(kopaytmasi)     # 120

# boshlang'ich qiymat bilan
natija = reduce(lambda a, b: a + b, sonlar, 100)
print(natija)     # 115
```

## sorted() — key=lambda bilan (eng ko'p ishlatiladigan kombinatsiya)

```python
talabalar = [("Ali", 85), ("Vali", 92), ("Guli", 78)]

saralangan = sorted(talabalar, key=lambda t: t[1])                # baho bo'yicha o'sish
print(saralangan)

saralangan2 = sorted(talabalar, key=lambda t: t[1], reverse=True)   # kamayish tartibida
print(saralangan2)

# bir nechta mezon bilan saralash
odamlar = [("Ali", 25, "Toshkent"), ("Vali", 20, "Toshkent"), ("Guli", 25, "Andijon")]
saralangan3 = sorted(odamlar, key=lambda o: (o[2], o[1]))     # avval shahar, keyin yosh
```

## map/filter vs list comprehension

```python
sonlar = [1, 2, 3, 4, 5]

kvadratlar_map = list(map(lambda x: x**2, sonlar))       # map bilan
kvadratlar_lc = [x**2 for x in sonlar]                       # list comprehension bilan (ko'proq tavsiya etiladi)

juftlar_filter = list(filter(lambda x: x % 2 == 0, sonlar))
juftlar_lc = [x for x in sonlar if x % 2 == 0]
```

**Amaliy qoida:** Ko'pchilik Python dasturchilari `map`/`filter` o'rniga list comprehension ishlatishni afzal ko'radi, chunki u o'qish oson. Lekin `reduce()`ning to'g'ridan-to'g'ri ekvivalenti yo'q, u o'ziga xos foydali vosita bo'lib qoladi. `sorted(..., key=lambda ...)` esa — juda ko'p ishlatiladigan, muhim naqsh.

## Funksiyalar haqida yakuniy tamoyillar

1. **Bitta funksiya — bitta vazifa** (Single Responsibility)
2. **Mazmunli nomlar** — `hisobla()` emas, `bmi_hisobla()`
3. **Kichik funksiyalar** — 20-30 qatordan oshsa, bo'lib tashlashni o'ylab ko'ring
4. **Docstring yozing** — boshqalar (va o'zingiz) tushunishi uchun
5. **Global o'zgaruvchidan saqlaning** — parametr va `return` orqali ishlang

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ikki sonni qo'shuvchi lambda funksiya yarating.
2. Sonni 2 baravar qaytaruvchi lambda yarating.
3. `map()` va lambda bilan ro'yxatning har bir elementini 10ga ko'paytiring.
4. `filter()` va lambda bilan ro'yxatdan faqat musbat sonlarni ajrating.
5. `reduce()` yordamida sonlar ro'yxatining ko'paytmasini toping.
6. Ism-familiyalar ro'yxatini familiya bo'yicha `sorted()` va lambda bilan saralang.
7. Lambda ichida ternary (`if/else`) ishlatib, son juft/toqligini aniqlang.
8. `sorted()` va `key=lambda` bilan so'zlar ro'yxatini uzunligiga qarab saralang.

🟡 **O'rta (9-15)**

9. Talabalar ro'yxatini (ism, baho) baho bo'yicha kamayish tartibida saralang.
10. `filter()` yordamida ro'yxatdan faqat 3 harfdan uzun so'zlarni ajrating.
11. `reduce()` yordamida sonlar ro'yxatidan eng kattasini toping (`max()` ishlatmasdan).
12. `map()` va `filter()`ni birlashtirib, avval juft sonlarni ajratib, so'ng ularni kvadratga oshiring.
13. `sorted()` da bir nechta mezon (masalan avval shahar, keyin yosh) bilan saralashni sinab ko'ring.
14. Ism-yosh juftliklaridan faqat 18 yoshdan katta bo'lganlarning ismlarini `filter()` va lambda bilan ajrating.
15. `reduce()` yordamida matnlar ro'yxatini bitta, bo'sh joy bilan birlashtirilgan gapga aylantiring.

🔴 **Qiyin (16-20)**

16. Mahsulotlar ro'yxatidan (nomi, narxi, miqdori) `filter()` bilan narxi 100,000dan yuqorilarini tanlang, `map()` bilan umumiy qiymatini hisoblang, `reduce()` bilan barcha umumiy qiymatlarning yig'indisini toping — barchasini bitta zanjirda bajaring.
17. Funksiyalar haqida o'rgangan barcha bilimingizni (oddiy funksiya, `*args`, `return`, lambda, map/filter/reduce) birlashtirib, "talabalar boshqaruv tizimi" yozing.
18. Matnlar ro'yxatidan `filter()` va lambda bilan faqat raqam bilan boshlanmaydiganlarini ajrating.
19. Ikki xil "saralash mezoni" bilan mahsulotlar ro'yxatini ikki xil tartibda chiqaring.
20. To'liq "mini-analitika" funksiyasini yozing — sonlar ro'yxatini qabul qilib, `filter`/`map`/`lambda`/`reduce` yordamida musbat, manfiy, juft, toq sonlar sonini va ularning yig'indisini alohida hisoblab, dictionary sifatida qaytarsin.

---

**Oldingi mavzu:** [20 — Modullar](./20_modullar.md)
**Keyingi mavzu:** [22 — "SON TOPISH" o'yini (amaliy loyiha)](./22_son_topish_oyini.md)
