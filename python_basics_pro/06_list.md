# 06 — LIST (RO'YXAT)

## List nima?

Bitta o'zgaruvchida bir nechta qiymatni tartiblangan holda saqlash imkonini beradi:

```python
mevalar = ["olma", "banan", "uzum"]
print(mevalar)
print(type(mevalar))
```

## Indeks va slicing

```python
mevalar = ["olma", "banan", "uzum", "anor"]

print(mevalar[0])        # olma
print(mevalar[-1])         # anor
print(mevalar[1:3])          # ['banan', 'uzum']
```

## List o'zgaruvchan (mutable)

```python
mevalar = ["olma", "banan"]
mevalar[0] = "shaftoli"
print(mevalar)     # ['shaftoli', 'banan']
```

## Element qo'shish va o'chirish

```python
mevalar = ["olma", "banan"]
mevalar.append("anor")           # oxiriga qo'shish
mevalar.insert(1, "uzum")          # muayyan o'ringa qo'shish
mevalar.remove("banan")              # qiymat bo'yicha o'chirish
oxirgisi = mevalar.pop()               # oxirgisini o'chirish va qaytarish
```

## Foydali metodlar

```python
sonlar = [5, 3, 8, 1]
print(len(sonlar))         # 4
sonlar.sort()                 # o'sish tartibida
sonlar.sort(reverse=True)       # kamayish tartibida
print(sonlar.count(3))            # nechta 3 bor
print("olma" in mevalar)             # mavjudlikni tekshirish
```

## List comprehension — zamonaviy va qulay

```python
kvadratlar = [x**2 for x in range(1, 6)]
print(kvadratlar)     # [1, 4, 9, 16, 25]

juftlar = [x for x in range(1, 21) if x % 2 == 0]
print(juftlar)
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. 5 ta shahar nomidan iborat list yarating va chiqaring.
2. Listning birinchi va oxirgi elementini chiqaring.
3. Listga yangi element qo'shing (`append`).
4. Listdan bitta elementni o'chiring (`remove`).
5. Listning uzunligini (`len()`) chiqaring.
6. Sonlar ro'yxatini o'sish tartibida saralang.
7. Listda muayyan element borligini `in` orqali tekshiring.
8. List comprehension yordamida 1-10 gacha sonlarning kvadratlarini hosil qiling.

🟡 **O'rta (9-15)**

9. Sonlar ro'yxatidan eng katta va eng kichik qiymatni `max()`/`min()`siz, o'zingiz solishtirib toping.
10. Ro'yxatdagi barcha juft sonlarni yangi ro'yxatga yig'ing (list comprehension bilan).
11. Ikkita ro'yxatni birlashtiring (`+`) va takrorlanuvchi elementlarni olib tashlang (`set()` orqali).
12. 5 ta mahsulot narxidan iborat list yarating, umumiy summani `sum()` bilan hisoblang.
13. Ro'yxatni teskari tartibga o'giring (`.reverse()` yoki `[::-1]`).
14. Talabalar ismi va bahosidan iborat ichma-ich list yarating (masalan `[["Ali", 85], ["Vali", 90]]`), eng yuqori baholi talabani toping.
15. List comprehension yordamida 1-50 gacha 3 yoki 5 ga bo'linadigan sonlarni ajrating.

🔴 **Qiyin (16-20)**

16. 3x3 matritsa (ichma-ich list) yarating va uning barcha elementlari yig'indisini hisoblang.
17. Ro'yxatdagi eng ko'p uchraydigan elementni (moda) toping (`.count()` yordamida).
18. Ikki ro'yxatni solishtirib, ikkalasida ham bor elementlarni topuvchi dastur yozing (`set()` ishlatmasdan, faqat list metodlari bilan).
19. Ro'yxatni "sahifalash" — 10 elementli ro'yxatni har biri 3 tadan iborat kichik ro'yxatlarga bo'ling (slicing yordamida, qo'lda).
20. Talabalar ro'yxati (ism, baho) berilgan — baho bo'yicha kamayish tartibida saralab, TOP-3 talabani chiqaring (`sorted()` va `key=lambda` dan foydalaning).

---

**Oldingi mavzu:** [05 — Sonlar](./05_sonlar.md)
**Keyingi mavzu:** [07 — Ro'yxatlar bilan ishlash](./07_royxatlar_bilan_ishlash.md)
