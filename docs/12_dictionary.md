# 12 — DICTIONARY BILAN TANISHUV

## Dictionary nima?

Kalit-qiymat (key-value) juftliklaridan iborat, tartiblangan (Python 3.7+), o'zgaruvchan ma'lumot turi:

```python
odam = {"ism": "Kamola", "yosh": 22, "shahar": "Andijon"}
bosh = {}                # bo'sh dictionary
bosh2 = dict()              # bo'sh dictionary yaratishning yana bir usuli
```

## Qiymatga murojaat qilish

```python
print(odam["ism"])                    # Kamola — mavjud bo'lmasa XATOLIK (KeyError)
print(odam.get("kasb"))                  # None — xatolik bermaydi
print(odam.get("kasb", "Noma'lum"))         # standart qiymat bilan
```

## Dictionary — TO'LIQ METODLAR RO'YXATI

### Qo'shish, o'zgartirish, o'chirish

```python
odam = {"ism": "Kamola", "yosh": 22}

odam["shahar"] = "Andijon"             # yangi kalit qo'shish
odam["yosh"] = 23                         # mavjudni o'zgartirish

odam.setdefault("kasb", "talaba")            # agar kalit yo'q bo'lsa, qo'shadi; bor bo'lsa tegmaydi
print(odam)

yosh = odam.pop("yosh")                         # o'chiradi VA qaytaradi
print(yosh)

yosh2 = odam.pop("mavjud_emas", "yoq")             # mavjud bo'lmasa, standart qiymat qaytaradi (xatolik bermaydi)

oxirgi = odam.popitem()                               # oxirgi qo'shilgan juftlikni o'chiradi va qaytaradi

del odam["shahar"]                                       # kalit bo'yicha o'chirish

odam.clear()                                                # barchasini tozalash
```

### Ko'rish metodlari

```python
odam = {"ism": "Kamola", "yosh": 22, "shahar": "Andijon"}

print(odam.keys())          # dict_keys(['ism', 'yosh', 'shahar'])
print(odam.values())           # dict_values(['Kamola', 22, 'Andijon'])
print(odam.items())               # dict_items([('ism', 'Kamola'), ...])

for kalit, qiymat in odam.items():
    print(f"{kalit}: {qiymat}")
```

### Nusxalash va birlashtirish

```python
odam = {"ism": "Kamola", "yosh": 22}

nusxa = odam.copy()          # haqiqiy nusxa (shallow copy)

odam.update({"shahar": "Farg'ona", "yosh": 23})     # bir nechta qiymatni birdaniga yangilash/qo'shish
print(odam)

# Zamonaviy — | operatori (Python 3.9+)
a = {"x": 1, "y": 2}
b = {"y": 3, "z": 4}
birlashgan = a | b            # {'x': 1, 'y': 3, 'z': 4}
a |= b                           # a ni to'g'ridan-to'g'ri yangilaydi (update() bilan bir xil)
```

### fromkeys() — bir nechta kalitni bir xil qiymat bilan yaratish

```python
kalitlar = ["a", "b", "c"]
yangi = dict.fromkeys(kalitlar, 0)     # {'a': 0, 'b': 0, 'c': 0}
print(yangi)
```

## `in` operatori

```python
print("ism" in odam)              # True — kalitlarni tekshiradi
print("Kamola" in odam.values())     # True — qiymatlar orasida tekshirish uchun .values()
```

## Dictionary comprehension

```python
kvadratlar = {x: x**2 for x in range(1, 6)}
print(kvadratlar)          # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# shart bilan
juft_kvadratlar = {x: x**2 for x in range(1, 11) if x % 2 == 0}

# mavjud dictionary asosida
narxlar = {"olma": 5000, "banan": 8000}
chegirmali = {mahsulot: narx * 0.9 for mahsulot, narx in narxlar.items()}
```

## Dictionary'ni saralash

```python
baholar = {"Ali": 85, "Vali": 92, "Guli": 78}

# qiymat bo'yicha saralash
saralangan = dict(sorted(baholar.items(), key=lambda item: item[1], reverse=True))
print(saralangan)

# kalit bo'yicha saralash
alifbo_boyicha = dict(sorted(baholar.items()))
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. O'zingiz haqingizda (ism, yosh, shahar) dictionary yarating va har birini chiqaring.
2. Dictionary'ga yangi kalit-qiymat qo'shing.
3. Mavjud qiymatni o'zgartiring.
4. Bitta kalit-qiymatni o'chiring (`del` va `.pop()` ikkalasini ham sinab ko'ring).
5. `.keys()`, `.values()`, `.items()` ni sinab ko'ring.
6. `in` operatori bilan kalit mavjudligini tekshiring.
7. `.get()` yordamida mavjud bo'lmagan kalit uchun standart qiymat chiqaring.
8. Dictionary comprehension bilan 1-10 gacha sonlar va ularning kublaridan lug'at yasang.

🟡 **O'rta (9-15)**

9. `.setdefault()` metodini sinab, u qanday ishlashini (mavjud/mavjud bo'lmagan holatlarda) izohlab bering.
10. Ikkita dictionary'ni `.update()` va `|` operatori bilan alohida-alohida birlashtiring, natijalarini solishtiring.
11. `dict.fromkeys()` yordamida 5 ta fan nomidan iborat, barchasi 0 baho bilan boshlanadigan dictionary yarating.
12. Talabalar ismi va bahosidan iborat dictionary yaratib, `sorted()` va `key=lambda` bilan baho bo'yicha saralang.
13. Dictionary'dagi barcha qiymatlarning yig'indisini (`sum(d.values())`) hisoblang.
14. Berilgan matndagi har bir so'zning necha marta uchraganini dictionary orqali hisoblang (so'z sanash).
15. Dictionary comprehension bilan, mavjud dictionary'dagi barcha qiymatlarni 2 barobar oshiring.

🔴 **Qiyin (16-20)**

16. Telefon kitobi: ism-raqam juftliklarini dictionary'da saqlang, qo'shish/o'chirish/qidirish funksiyalarini yozing.
17. Ovoz berish tizimi: nomzodlar va ovozlar sonini dictionary'da saqlang, eng ko'p ovoz olganini `max()` va `key=` bilan toping.
18. `.popitem()` metodini sinab, u dictionary'dan qaysi elementni o'chirishini (Python 3.7+da) tekshiring.
19. Talabalar bahosidan iborat dictionary'ni ham kalit, ham qiymat bo'yicha (ikki xil) saralab chiqaring.
20. Inventarizatsiya tizimi: mahsulot nomi kalit, {narx, miqdor} ichki dictionary qiymat bo'lsin (nested), umumiy inventar qiymatini hisoblang.

---

**Oldingi mavzu:** [11 — Xatolar bilan ishlash](./11_xatolar.md)
**Keyingi mavzu:** [13 — Nesting (ichma-ich tuzilmalar)](./13_nesting.md)
