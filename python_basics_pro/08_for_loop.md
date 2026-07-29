# 08 — FOR TAKRORLASH OPERATORI

## Asosiy sintaksis

```python
mevalar = ["olma", "banan", "uzum"]
for meva in mevalar:
    print(meva)
```

## range() bilan ishlash

```python
for i in range(5):           # 0,1,2,3,4
    print(i)

for i in range(2, 8):          # 2,3,4,5,6,7
    print(i)

for i in range(0, 10, 2):        # 0,2,4,6,8 (qadam bilan)
    print(i)
```

## enumerate() — indeks bilan birga

```python
mevalar = ["olma", "banan", "uzum"]
for indeks, meva in enumerate(mevalar, start=1):
    print(f"{indeks}. {meva}")
```

## String va dictionary bo'ylab

```python
for harf in "Python":
    print(harf)

odam = {"ism": "Ali", "yosh": 20}
for kalit, qiymat in odam.items():
    print(kalit, "->", qiymat)
```

## Ichma-ich for tsikllari

```python
for i in range(1, 4):
    for j in range(1, 4):
        print(f"{i}x{j}={i*j}", end="  ")
    print()
```

## break va continue

```python
for son in range(1, 20):
    if son == 10:
        break             # tsikl to'xtaydi
    if son % 2 == 0:
        continue            # keyingisiga o'tadi
    print(son)
```

## Zamonaviy imkoniyat — itertools moduli (kirish)

Katta va murakkab tsikllar uchun `itertools` moduli juda foydali vositalar taqdim etadi:

```python
from itertools import combinations

ismlar = ["Ali", "Vali", "Guli"]
for juftlik in combinations(ismlar, 2):     # barcha 2 talik kombinatsiyalar
    print(juftlik)
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. `range()` yordamida 1 dan 20 gacha sonlarni chiqaring.
2. 1 dan 50 gacha 5 ga bo'linadigan sonlarni chiqaring.
3. Listdagi har bir elementni, indeksi bilan birga (`enumerate`) chiqaring.
4. 1 dan 10 gacha sonlarning yig'indisini `for` orqali hisoblang.
5. Berilgan so'zdagi unli harflarni sanab chiqing.
6. 5 marta foydalanuvchidan ism so'rab, har birini salomlashtiring.
7. `for` yordamida 1 dan N gacha (foydalanuvchi kiritgan) sonlarni chiqaring.
8. Ko'paytirish jadvalini (masalan 5 uchun, 1 dan 10 gacha) chiqaring.

🟡 **O'rta (9-15)**

9. Ichma-ich `for` yordamida to'liq ko'paytirish jadvalini (1 dan 10 gacha, hammasi) chiqaring.
10. Yulduzchalardan uchburchak shaklini chizing (ichma-ich for bilan).
11. 1 dan 100 gacha tub sonlarni topib chiqaring.
12. Ikkita ro'yxatni (mahsulot va narx) `zip()` va `for` bilan birlashtirib, "Non - 3000 so'm" formatida chiqaring.
13. `break` yordamida, foydalanuvchi kiritgan sonlar ro'yxatidan birinchi manfiy sonni topib, tsiklni to'xtating.
14. `continue` yordamida 1-30 oralig'ida faqat 7 ga bo'linmaydigan sonlarni chiqaring.
15. `for...else` tuzilmasidan foydalanib, ro'yxatda toq son yo'qligini tekshiring.

🔴 **Qiyin (16-20)**

16. Fibonachchi ketma-ketligining dastlabki 15 ta hadini `for` tsikli yordamida chiqaring.
17. 2 o'lchamli matritsa (list ichida list) berilgan — uning barcha elementlari yig'indisini va har bir qator yig'indisini alohida hisoblang.
18. Berilgan sonning tub ko'paytuvchilarga ajralishini (`for` va `while` kombinatsiyasi bilan) toping.
19. "Yulduzcha piramida" chizing — pastga qarab kamayadigan uchburchak (5 qatordan boshlab 1 tagacha).
20. `itertools.combinations` yordamida 4 ta talabadan 2 talikdan barcha mumkin bo'lgan juftliklarni (masalan sport o'yini uchun jamoalar) hosil qiling.

---

**Oldingi mavzu:** [07 — Ro'yxatlar bilan ishlash](./07_royxatlar_bilan_ishlash.md)
**Keyingi mavzu:** [09 — IF-ELSE](./09_if_else.md)
