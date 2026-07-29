# LIST COMPREHENSION

## List comprehension nima?

**List comprehension** — yangi list yaratishning qisqa, "Python'ga xos" (Pythonic) usuli. U oddiy `for` tsikli orqali list yaratishning bir qatorlik ekvivalentidir.

```python
# oddiy usul
kvadratlar = []
for i in range(1, 6):
    kvadratlar.append(i ** 2)
print(kvadratlar)

# list comprehension
kvadratlar = [i ** 2 for i in range(1, 6)]
print(kvadratlar)
```

Ikkalasi ham bir xil natija beradi: `[1, 4, 9, 16, 25]`, lekin ikkinchisi qisqaroq va (o'rganib olgach) o'qish osonroq.

## Asosiy sintaksis

```
[ifoda for element in iterable]
```

```python
sonlar = [1, 2, 3, 4, 5]
ikki_barobar = [x * 2 for x in sonlar]
print(ikki_barobar)     # [2, 4, 6, 8, 10]
```

## Shart bilan list comprehension

```
[ifoda for element in iterable if shart]
```

```python
sonlar = range(1, 21)
juftlar = [x for x in sonlar if x % 2 == 0]
print(juftlar)
```

```
[2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
```

Bu quyidagi oddiy tsiklga teng:

```python
juftlar = []
for x in sonlar:
    if x % 2 == 0:
        juftlar.append(x)
```

## if/else bilan list comprehension (ternary)

Agar `if` shartsiz emas, balki har bir elementga qarab boshqa-boshqa qiymat berish kerak bo'lsa, ternary tuzilma ishlatiladi — bu holda `if/else` shartdan **oldin** yoziladi:

```python
sonlar = [1, 2, 3, 4, 5, 6, 7, 8]
natija = ["juft" if x % 2 == 0 else "toq" for x in sonlar]
print(natija)
```

```
['toq', 'juft', 'toq', 'juft', 'toq', 'juft', 'toq', 'juft']
```

**Farqni eslab qoling:**
- Filtrlash (ba'zi elementlarni tashlab ketish): `[x for x in royxat if shart]`
- Har bir elementni o'zgartirish: `[x if shart else boshqa for x in royxat]`

## String'lar bilan list comprehension

```python
sozlar = ["python", "dastur", "kod", "AI"]
katta_harflar = [soz.upper() for soz in sozlar]
print(katta_harflar)     # ['PYTHON', 'DASTUR', 'KOD', 'AI']

uzunliklar = [len(soz) for soz in sozlar]
print(uzunliklar)          # [6, 6, 3, 2]

uzun_sozlar = [soz for soz in sozlar if len(soz) > 3]
print(uzun_sozlar)          # ['python', 'dastur']
```

## Ichma-ich list comprehension

Matritsalar (list ichida list) bilan ishlashda foydali:

```python
matritsa = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

# barcha elementlarni bitta tekis listga yig'ish
tekis = [son for qator in matritsa for son in qator]
print(tekis)     # [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

Bu yerdagi tartib muhim — u ikkita ichma-ich `for` tsikliga teng:

```python
tekis = []
for qator in matritsa:
    for son in qator:
        tekis.append(son)
```

## Dictionary comprehension

Xuddi shu mantiq lug'atlar uchun ham ishlaydi:

```python
sonlar = [1, 2, 3, 4, 5]
kvadratlar_lugat = {x: x**2 for x in sonlar}
print(kvadratlar_lugat)
```

```
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

```python
odam = {"ism": "Ali", "yosh": 25, "shahar": "Buxoro"}
katta_kalitlar = {kalit.upper(): qiymat for kalit, qiymat in odam.items()}
print(katta_kalitlar)
```

## Set comprehension

```python
sonlar = [1, 2, 2, 3, 3, 3, 4]
noyob_kvadratlar = {x**2 for x in sonlar}
print(noyob_kvadratlar)     # {16, 1, 4, 9}
```

## Qachon list comprehension ishlatish, qachon oddiy for?

| Holat | Tavsiya |
|---|---|
| Oddiy, bir qatorlik mantiq (filtrlash, o'zgartirish) | **list comprehension** |
| Bir necha shart, murakkab mantiq | oddiy **for** tsikli |
| Har bir qadamda print, log yozish yoki boshqa "side effect" kerak | oddiy **for** tsikli |
| Yangi list/dict/set yaratish maqsad | **comprehension** |

**Amaliy maslahat:** Agar list comprehension bir qatordan uzunroq bo'lib, o'qish qiyinlashsa — bu signal, oddiy `for` tsikliga qaytish vaqti keldi degani. Aql bovar qilmas darajada murakkab comprehension yozish yaxshi amaliyot emas.

## Amaliy misol: talabalar orasidan o'tganlarini tanlash

```python
talabalar = [
    {"ism": "Ali", "baho": 85},
    {"ism": "Vali", "baho": 45},
    {"ism": "Guli", "baho": 92},
    {"ism": "Laylo", "baho": 38}
]

otganlar = [t["ism"] for t in talabalar if t["baho"] >= 60]
print(otganlar)     # ['Ali', 'Guli']
```

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. 1 dan 10 gacha sonlarning kublarini (`x**3`) list comprehension yordamida hosil qiling.
2. 1 dan 30 gacha sonlar orasidan 3 ga bo'linadiganlarini list comprehension bilan ajrating.
3. Berilgan so'zlar ro'yxatidagi har bir so'zning uzunligini list comprehension orqali toping.

🟡 **O'rta daraja**

4. 1 dan 20 gacha sonlarni "juft"/"toq" deb belgilovchi yangi list yarating (if/else ternary comprehension).
5. Berilgan matritsadagi barcha elementlarni 2 baravar oshirib, yangi (tekis) list hosil qiling.
6. Ism-yosh juftliklaridan (`[("Ali", 20), ("Vali", 17), ("Guli", 22)]`) faqat 18 yoshdan katta bo'lganlarning ismlarini ajrating.
7. Dictionary comprehension yordamida 1 dan 10 gacha sonlar va ularning kublaridan iborat lug'at yarating.

🔴 **Murakkabroq**

8. Berilgan gapdagi so'zlardan faqat unli harf bilan boshlanadiganlarini ajratib oling (list comprehension va `startswith` yoki indeks tekshiruvi orqali).
9. 5x5 ko'paytirish jadvalini ichma-ich list comprehension yordamida (matritsa ko'rinishida) hosil qiling.

---

**Oldingi mavzu:** [17 — Lambda funksiyalar](./17_lambda_funksiyalar.md)
**Keyingi mavzu:** [19 — Modullar va paketlar (asoslar)](./19_modullar_paketlar.md)
