# 12 — DICTIONARY BILAN TANISHUV

## Dictionary nima?

Kalit-qiymat (key-value) juftliklaridan iborat ma'lumot turi:

```python
odam = {"ism": "Kamola", "yosh": 22, "shahar": "Andijon"}
print(odam["ism"])       # Kamola
```

## Qiymatga xavfsiz murojaat

```python
print(odam.get("kasb"))                    # None — xatolik bermaydi
print(odam.get("kasb", "Noma'lum"))          # standart qiymat bilan
```

## Qo'shish, o'zgartirish, o'chirish

```python
odam["shahar"] = "Farg'ona"       # o'zgartirish
odam["kasb"] = "dasturchi"           # qo'shish
del odam["yosh"]                        # o'chirish
```

## keys(), values(), items()

```python
for kalit, qiymat in odam.items():
    print(f"{kalit}: {qiymat}")
```

## `in` operatori

```python
print("ism" in odam)         # True — kalitlarni tekshiradi
```

## Zamonaviy imkoniyat — dictionary birlashtirish operatori `|` (Python 3.9+)

```python
a = {"x": 1, "y": 2}
b = {"y": 3, "z": 4}

birlashgan = a | b       # {'x': 1, 'y': 3, 'z': 4}
print(birlashgan)
```

## Dictionary comprehension

```python
kvadratlar = {x: x**2 for x in range(1, 6)}
print(kvadratlar)     # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. O'zingiz haqingizda (ism, yosh, shahar) dictionary yarating va har birini chiqaring.
2. Dictionary'ga yangi kalit-qiymat qo'shing.
3. Mavjud qiymatni o'zgartiring.
4. Bitta kalit-qiymatni o'chiring (`del`).
5. `.keys()`, `.values()`, `.items()` ni sinab ko'ring.
6. `in` operatori bilan kalit mavjudligini tekshiring.
7. `.get()` yordamida mavjud bo'lmagan kalit uchun standart qiymat chiqaring.
8. Dictionary comprehension bilan 1-10 gacha sonlar va ularning kublaridan lug'at yasang.

🟡 **O'rta (9-15)**

9. Mahsulot nomi va narxidan iborat dictionary yarating (5 ta), foydalanuvchi nomni kiritsa narxini chiqaring.
10. Ikkita dictionary'ni `|` operatori bilan birlashtiring.
11. Talabalar ismi va bahosidan iborat dictionary yaratib, eng yuqori bahoni topuvchi dastur yozing.
12. Dictionary'dagi barcha qiymatlarning yig'indisini (`sum(d.values())`) hisoblang.
13. Foydalanuvchidan bir nechta ism-yosh juftligini kiritib olib, dictionary'ga to'ldiring.
14. Berilgan matndagi har bir so'zning necha marta uchraganini dictionary orqali hisoblang (so'z sanash).
15. Dictionary comprehension bilan, mavjud dictionary'dagi barcha qiymatlarni 2 barobar oshiring.

🔴 **Qiyin (16-20)**

16. Telefon kitobi: ism-raqam juftliklarini dictionary'da saqlang, qo'shish/o'chirish/qidirish funksiyalarini yozing.
17. Ovoz berish tizimi: nomzodlar va ovozlar sonini dictionary'da saqlang, eng ko'p ovoz olganini toping.
18. Ikki dictionary'ni solishtirib, faqat bittasida bor kalitlarni toping.
19. Talabalar bahosidan iborat dictionary'ni qiymat (baho) bo'yicha kamayish tartibida saralab chiqaring (`sorted()` va `.items()` bilan).
20. Inventarizatsiya tizimi: mahsulot nomi kalit, {narx, miqdor} ichki dictionary qiymat bo'lsin (nested), umumiy inventar qiymatini hisoblang.

---

**Oldingi mavzu:** [11 — Xatolar bilan ishlash](./11_xatolar.md)
**Keyingi mavzu:** [13 — Nesting (ichma-ich tuzilmalar)](./13_nesting.md)
