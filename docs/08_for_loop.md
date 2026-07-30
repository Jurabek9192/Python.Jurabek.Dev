# 08 — FOR TAKRORLASH OPERATORI

## Asosiy sintaksis

```python
mevalar = ["olma", "banan", "uzum"]
for meva in mevalar:
    print(meva)
```

## range() — to'liq imkoniyatlar

```python
for i in range(5):              # 0,1,2,3,4 — bitta argument: tugash
    print(i)

for i in range(2, 8):              # 2,3,4,5,6,7 — boshlanish, tugash
    print(i)

for i in range(0, 10, 2):             # 0,2,4,6,8 — boshlanish, tugash, qadam
    print(i)

for i in range(10, 0, -1):               # 10,9,8,...,1 — manfiy qadam bilan teskari
    print(i)

print(list(range(5)))                       # range obyektini listga aylantirish: [0,1,2,3,4]
print(len(range(1, 100)))                      # range uzunligini bilish (aylanmasdan!)
```

## enumerate() — indeks bilan birga aylanish

```python
mevalar = ["olma", "banan", "uzum"]

for indeks, meva in enumerate(mevalar):              # standart, 0 dan boshlanadi
    print(indeks, meva)

for indeks, meva in enumerate(mevalar, start=1):        # 1 dan boshlash
    print(f"{indeks}. {meva}")
```

## zip() — bir nechta ro'yxat bo'ylab birgalikda aylanish

```python
ismlar = ["Ali", "Vali", "Guli"]
yoshlar = [20, 22, 19]
shaharlar = ["Toshkent", "Andijon", "Namangan"]

for ism, yosh, shahar in zip(ismlar, yoshlar, shaharlar):     # istalgan sonda list birlashadi
    print(f"{ism}, {yosh}, {shahar}")
```

## String va dictionary bo'ylab

```python
for harf in "Python":
    print(harf)

odam = {"ism": "Ali", "yosh": 20}
for kalit in odam:                    # standart holatda faqat kalitlar bo'ylab aylanadi
    print(kalit)
for kalit, qiymat in odam.items():        # kalit VA qiymat birga
    print(kalit, "->", qiymat)
for qiymat in odam.values():                 # faqat qiymatlar
    print(qiymat)
```

## Ichma-ich for tsikllari

```python
for i in range(1, 4):
    for j in range(1, 4):
        print(f"{i}x{j}={i*j}", end="  ")
    print()
```

## break, continue, else

```python
for son in range(1, 20):
    if son == 10:
        break               # tsikl to'liq to'xtaydi
    if son % 2 == 0:
        continue                # keyingi elementga o'tadi
    print(son)

# for...else — break bo'lmasdan tabiiy tugasa ishga tushadi
for son in [2, 4, 6, 8]:
    if son % 2 != 0:
        print("Toq son topildi!")
        break
else:
    print("Barcha sonlar juft ekan")     # break ishlamagani uchun bu chiqadi
```

## Reversed() — teskari tartibda aylanish

```python
for son in reversed(range(1, 6)):     # 5,4,3,2,1
    print(son)

for harf in reversed("Python"):          # n,o,h,t,y,P
    print(harf)
```

## sorted() — for bilan birga

```python
sonlar = [5, 2, 8, 1]
for son in sorted(sonlar):                # asl ro'yxatni o'zgartirmasdan, saralangan holda aylanish
    print(son)

for son in sorted(sonlar, reverse=True):     # kamayish tartibida
    print(son)
```

## Zamonaviy imkoniyat — itertools moduli

```python
from itertools import combinations, permutations, product

ismlar = ["Ali", "Vali", "Guli"]

for juftlik in combinations(ismlar, 2):        # barcha 2talik kombinatsiyalar (tartib muhim emas)
    print(juftlik)

for juftlik in permutations(ismlar, 2):           # barcha 2talik joylashtirishlar (tartib muhim)
    print(juftlik)

for kombinatsiya in product([1,2], ["a","b"]):       # barcha mumkin bo'lgan juftliklar (dekart ko'paytmasi)
    print(kombinatsiya)
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. `range()` yordamida 1 dan 20 gacha sonlarni chiqaring.
2. 1 dan 50 gacha 5 ga bo'linadigan sonlarni chiqaring.
3. Listdagi har bir elementni, indeksi bilan birga (`enumerate`) chiqaring.
4. 1 dan 10 gacha sonlarning yig'indisini `for` orqali hisoblang.
5. Berilgan so'zdagi unli harflarni sanab chiqing.
6. `zip()` yordamida ikkita listni (ism, yosh) birlashtirib chiqaring.
7. `reversed()` yordamida 10 dan 1 gacha sonlarni chiqaring.
8. Ko'paytirish jadvalini (masalan 5 uchun, 1 dan 10 gacha) chiqaring.

🟡 **O'rta (9-15)**

9. Ichma-ich `for` yordamida to'liq ko'paytirish jadvalini (1 dan 10 gacha, hammasi) chiqaring.
10. `sorted()` bilan `for` tsiklini birlashtirib, ro'yxatni saralangan holda, lekin asl ro'yxatga tegmasdan chiqaring.
11. 1 dan 100 gacha tub sonlarni topib chiqaring.
12. `zip()` yordamida uchta ro'yxatni (mahsulot, narx, miqdor) birlashtirib chek formatida chiqaring.
13. `break` yordamida, foydalanuvchi kiritgan sonlar ro'yxatidan birinchi manfiy sonni topib, tsiklni to'xtating.
14. `for...else` tuzilmasidan foydalanib, ro'yxatda toq son yo'qligini tekshiring.
15. `itertools.combinations` yordamida 4 ta talabadan 2 talikdan barcha mumkin bo'lgan juftliklarni hosil qiling.

🔴 **Qiyin (16-20)**

16. Fibonachchi ketma-ketligining dastlabki 15 ta hadini `for` tsikli yordamida chiqaring.
17. 2 o'lchamli matritsa berilgan — uning barcha elementlari yig'indisini va har bir qator yig'indisini alohida hisoblang.
18. Berilgan sonning tub ko'paytuvchilarga ajralishini `for` va `while` kombinatsiyasi bilan toping.
19. `itertools.permutations` yordamida 3 ta harfdan (masalan "A","B","C") yasaladigan barcha joylashtirishlarni chiqaring.
20. `itertools.product` yordamida, 3 xil o'lcham va 2 xil rangdan yasaladigan barcha mahsulot variantlarini (masalan futbolka) hosil qiling.

---

**Oldingi mavzu:** [07 — Ro'yxatlar bilan ishlash](./07_royxatlar_bilan_ishlash.md)
**Keyingi mavzu:** [09 — IF-ELSE](./09_if_else.md)
