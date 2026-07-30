# 06 — LIST (RO'YXAT)

## List nima?

Bitta o'zgaruvchida bir nechta qiymatni tartiblangan, o'zgaruvchan (mutable) holda saqlash imkonini beradi:

```python
mevalar = ["olma", "banan", "uzum"]
aralash = ["Ali", 25, True, 3.14]      # turli xil turlar birga bo'lishi mumkin
bosh = []                                  # bo'sh list
bosh2 = list()                               # bo'sh list yaratishning yana bir usuli
```

## Indeks va slicing

```python
mevalar = ["olma", "banan", "uzum", "anor"]

print(mevalar[0])          # olma
print(mevalar[-1])            # anor
print(mevalar[1:3])              # ['banan', 'uzum']
print(mevalar[::-1])                # teskari tartib
print(mevalar[::2])                    # har 2-elementdan
```

## List — TO'LIQ METODLAR RO'YXATI

### Element qo'shish

```python
mevalar = ["olma", "banan"]

mevalar.append("anor")            # oxiriga bitta element qo'shadi
print(mevalar)                        # ['olma', 'banan', 'anor']

mevalar.insert(1, "uzum")               # muayyan indeksga qo'yadi
print(mevalar)                             # ['olma', 'uzum', 'banan', 'anor']

mevalar.extend(["nok", "shaftoli"])           # boshqa listni oxiriga qo'shadi (har birini alohida)
print(mevalar)

# DIQQAT: append vs extend farqi
a = [1, 2]
a.append([3, 4])
print(a)          # [1, 2, [3, 4]] — butun list bitta element bo'lib qo'shildi

b = [1, 2]
b.extend([3, 4])
print(b)            # [1, 2, 3, 4] — har biri alohida qo'shildi
```

### Element o'chirish

```python
mevalar = ["olma", "banan", "uzum", "anor"]

mevalar.remove("banan")       # qiymat bo'yicha o'chiradi (birinchi topilganini)
print(mevalar)

oxirgisi = mevalar.pop()         # oxirgisini o'chiradi VA qaytaradi
print(oxirgisi, mevalar)

birinchisi = mevalar.pop(0)        # muayyan indeksdagini o'chiradi va qaytaradi
print(birinchisi, mevalar)

del mevalar[0]                        # indeks bo'yicha o'chirish (qaytarmaydi)

mevalar.clear()                          # BARCHA elementlarni o'chiradi
print(mevalar)                              # []
```

### Qidirish va sanash

```python
sonlar = [5, 3, 8, 1, 3, 9]

print(sonlar.index(8))          # 2 — 8ning birinchi indeksi (topilmasa XATOLIK)
print(sonlar.count(3))             # 2 — nechta 3 borligi
print(8 in sonlar)                    # True — mavjudligini tekshirish (eng tez usul)
```

### Saralash va tartiblash

```python
sonlar = [5, 3, 8, 1, 9]

sonlar.sort()                    # joyida saralaydi (o'sish tartibida), asl listni o'zgartiradi
print(sonlar)                        # [1, 3, 5, 8, 9]

sonlar.sort(reverse=True)               # kamayish tartibida
print(sonlar)                               # [9, 8, 5, 3, 1]

sonlar.reverse()                                # tartibni butunlay teskari qiladi (saralamaydi!)
print(sonlar)

yangi = sorted([3, 1, 2])                          # ASL listni o'zgartirmasdan, YANGI saralangan list qaytaradi
print(yangi)

# key parametri bilan murakkab saralash
talabalar = [("Ali", 85), ("Vali", 92), ("Guli", 78)]
saralangan = sorted(talabalar, key=lambda t: t[1])       # baho bo'yicha
print(saralangan)
```

### Nusxalash

```python
a = [1, 2, 3]
b = a                  # DIQQAT: bu nusxa EMAS — b va a bir xil listga ishora qiladi!
b.append(4)
print(a)                  # [1, 2, 3, 4] — a HAM o'zgardi!

c = a.copy()                  # haqiqiy nusxa (shallow copy)
c.append(5)
print(a, c)                       # a o'zgarmadi, c o'zgardi

d = list(a)                          # nusxalashning yana bir usuli
e = a[:]                                # nusxalashning uchinchi usuli (slicing orqali)
```

## `in`, `len`, `+`, `*` operatorlari

```python
mevalar = ["olma", "banan"]

print(len(mevalar))          # 2
print("olma" in mevalar)        # True

a = [1, 2, 3]
b = [4, 5, 6]
print(a + b)                       # [1, 2, 3, 4, 5, 6] — birlashtirish
print(a * 3)                          # [1, 2, 3, 1, 2, 3, 1, 2, 3] — takrorlash
```

## List comprehension — zamonaviy va qulay

```python
kvadratlar = [x**2 for x in range(1, 6)]
print(kvadratlar)          # [1, 4, 9, 16, 25]

juftlar = [x for x in range(1, 21) if x % 2 == 0]      # shart bilan
print(juftlar)

natija = ["juft" if x % 2 == 0 else "toq" for x in range(1, 6)]   # if/else bilan
print(natija)

# ichma-ich list comprehension
matritsa = [[i*j for j in range(1, 4)] for i in range(1, 4)]
print(matritsa)
```

## Foydali o'rnatilgan funksiyalar list bilan

```python
sonlar = [5, 3, 8, 1, 9]

print(sum(sonlar))          # 26
print(len(sonlar))             # 5
print(max(sonlar))                # 9
print(min(sonlar))                   # 1
print(any(x > 5 for x in sonlar))       # True — kamida bittasi shartga mos
print(all(x > 0 for x in sonlar))          # True — barchasi shartga mos
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. 5 ta shahar nomidan iborat list yarating va chiqaring.
2. Listning birinchi va oxirgi elementini chiqaring.
3. `.append()`, `.insert()`, `.extend()` metodlarini bittalab sinab, farqini tushuntiring.
4. `.remove()`, `.pop()`, `del` bilan ro'yxatdan elementlarni o'chiring.
5. Listning uzunligini (`len()`) chiqaring.
6. `.sort()` va `sorted()` farqini sinab ko'ring (asl list o'zgaradimi yo'qmi).
7. `.index()` va `.count()` metodlarini sinab ko'ring.
8. List comprehension yordamida 1-10 gacha sonlarning kvadratlarini hosil qiling.

🟡 **O'rta (9-15)**

9. `.copy()` va oddiy `=` orqali "nusxalash" farqini sinab, natijasini izohlang.
10. Ro'yxatdagi barcha juft sonlarni yangi ro'yxatga yig'ing (list comprehension bilan).
11. Ikkita ro'yxatni birlashtiring (`+`) va takrorlanuvchi elementlarni olib tashlang (`set()` orqali).
12. 5 ta mahsulot narxidan iborat list yarating, umumiy summani `sum()` bilan hisoblang.
13. `key=lambda` parametri bilan, talabalar ro'yxatini (ism, baho) baho bo'yicha saralang.
14. `any()` va `all()` funksiyalarini ro'yxat ustida amaliy misolda sinab ko'ring.
15. List comprehension yordamida 1-50 gacha 3 yoki 5 ga bo'linadigan sonlarni ajrating.

🔴 **Qiyin (16-20)**

16. 3x3 matritsa (ichma-ich list comprehension) yarating va uning barcha elementlari yig'indisini hisoblang.
17. Ro'yxatdagi eng ko'p uchraydigan elementni (moda) `.count()` yordamida toping.
18. `.pop(0)` va `.pop()` ishlatilishidagi tezlik farqi haqida (katta ro'yxatlarda `.pop(0)` sekinroq) qisqa izlanish qiling va yozib qo'ying.
19. Ro'yxatni "sahifalash" — 10 elementli ro'yxatni har biri 3 tadan iborat kichik ro'yxatlarga bo'ling (slicing yordamida).
20. Talabalar ro'yxati (ism, baho) berilgan — `sorted()`, `key`, `reverse=True` yordamida TOP-3 talabani chiqaring.

---

**Oldingi mavzu:** [05 — Sonlar](./05_sonlar.md)
**Keyingi mavzu:** [07 — Ro'yxatlar bilan ishlash (Tuple, Set)](./07_royxatlar_bilan_ishlash.md)
