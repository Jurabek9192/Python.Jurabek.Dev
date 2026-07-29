# 07 — RO'YXATLAR BILAN ISHLASH (TUPLE VA SET)

## Tuple — o'zgarmas ro'yxat

```python
kordinata = (41.311, 69.240)
print(kordinata[0])       # 41.311
# kordinata[0] = 50        # XATOLIK! tuple o'zgarmas
```

Nega tuple kerak? Ma'lumot tasodifan o'zgartirilib qo'yilmasligi kerak bo'lgan holatlar uchun (masalan koordinatalar, doimiy sozlamalar).

## Tuple unpacking

```python
ism, yosh, shahar = ("Ali", 20, "Buxoro")
print(ism, yosh, shahar)
```

## Set — noyob elementlar to'plami

```python
mevalar = {"olma", "banan", "olma"}    # takrorlanuvchi avtomatik olib tashlanadi
print(mevalar)      # {'olma', 'banan'}
```

## Set matematikasi

```python
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

print(a | b)     # birlashma: {1,2,3,4,5,6}
print(a & b)      # kesishma: {3,4}
print(a - b)       # farq: {1,2}
```

## List, Tuple, Set — qачон qaysi biri?

| Ma'lumot turi | O'zgaruvchanmi | Tartibli | Takrorlanish |
|---|---|---|---|
| `list` | Ha | Ha | Ruxsat |
| `tuple` | Yo'q | Ha | Ruxsat |
| `set` | Ha | Yo'q | Ruxsat etilmaydi |

## Ro'yxatlar bilan ko'proq amaliy ishlash

```python
sonlar = [3, 1, 4, 1, 5, 9, 2, 6]

print(sum(sonlar))          # yig'indi
print(sorted(sonlar))          # yangi saralangan list (asl o'zgarmaydi)
print(list(set(sonlar)))          # takrorsiz elementlar

# zip — ikki ro'yxatni birlashtirish
ismlar = ["Ali", "Vali"]
yoshlar = [20, 22]
for ism, yosh in zip(ismlar, yoshlar):
    print(f"{ism}: {yosh}")
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ism, yosh, shahardan iborat tuple yarating va uni 3 ta o'zgaruvchiga unpacking qiling.
2. Bitta elementli tuple to'g'ri yarating (`(5,)`) va uning turini tekshiring.
3. Takrorlanuvchi elementli list'dan set yasang va noyob elementlarni chiqaring.
4. Ikkita set'ning birlashmasini va kesishmasini toping.
5. `zip()` yordamida ikkita ro'yxatni (ism va yosh) birlashtirib chiqaring.
6. `sorted()` funksiyasi bilan ro'yxatni saralab, asl ro'yxat o'zgarmaganini tekshiring.
7. Haftaning 7 kunidan iborat tuple yarating.
8. Set'ga yangi element qo'shing (`.add()`) va bittasini o'chiring (`.discard()`).

🟡 **O'rta (9-15)**

9. Ikki guruh talabalarining ismlaridan (set) ikkalasida ham bor va faqat bittasida bor talabalarni toping.
10. Funksiya yozing — u ikkita son qabul qilib, ularning yig'indisi va ko'paytmasini tuple ko'rinishida qaytarsin.
11. Ro'yxatdagi barcha noyob elementlarni sanoq bilan (har biri nechta marta uchraganini) chiqaring.
12. `zip()` yordamida uchta ro'yxatni (ism, yosh, shahar) birlashtirib, har biri uchun to'liq gap tuzing.
13. Matndagi noyob (takrorlanmagan) harflar sonini `set()` yordamida hisoblang.
14. Ikki ro'yxatni solishtirib, ular orasidagi farqni (faqat bittasida bor elementlarni) `set` operatorlari bilan toping.
15. Talabalar ismi va bahosidan iborat tuple'lar ro'yxatini yarating va eng yuqori baholini toping.

🔴 **Qiyin (16-20)**

16. Uchta do'kon uchun mahsulot to'plamlarini (set) yarating va barcha uchta do'konda ham bor mahsulotlarni toping.
17. `*` operatoridan foydalanib, 5 elementli tuple'ning birinchi, oxirgi va o'rtadagi elementlarini alohida ajrating.
18. Katta ro'yxatdagi (100+ element) eng ko'p uchraydigan 3 ta elementni (`set` va `.count()` yordamida) toping.
19. Ikki ro'yxatni (mahsulot nomi va narxi) `zip()` bilan birlashtirib, dictionary'ga aylantiring (`dict(zip(...))`).
20. Talabalar ma'lumotlarini (ism, 3 ta baho) tuple sifatida saqlab, har birining o'rtacha bahosini hisoblab, eng yaxshi 3 talabani chiqaring.

---

**Oldingi mavzu:** [06 — List (ro'yxat)](./06_list.md)
**Keyingi mavzu:** [08 — For takrorlash operatori](./08_for_loop.md)
