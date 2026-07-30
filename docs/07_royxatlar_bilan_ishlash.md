# 07 — RO'YXATLAR BILAN ISHLASH (TUPLE VA SET)

## Tuple — o'zgarmas ro'yxat

```python
kordinata = (41.311, 69.240)
bosh = ()                  # bo'sh tuple
bitta = (5,)                  # DIQQAT: bitta elementli tuple uchun vergul SHART
notuple = (5)                    # bu oddiy int, tuple EMAS!

print(kordinata[0])          # 41.311
# kordinata[0] = 50             # XATOLIK! tuple o'zgarmas (immutable)
```

Nega tuple kerak? Ma'lumot tasodifan o'zgartirilib qo'yilmasligi kerak bo'lgan holatlar uchun (koordinatalar, doimiy sozlamalar), va u list'ga qaraganda tezroq va kam xotira ishlatadi.

## Tuple metodlari (faqat ikkitasi bor — o'zgarmas bo'lgani uchun)

```python
sonlar = (3, 5, 3, 8, 3, 1)

print(sonlar.count(3))        # 3 — nechta 3 borligi
print(sonlar.index(8))          # 3 — 8ning indeksi
print(len(sonlar))                 # 6
```

## Tuple unpacking (yechish)

```python
ism, yosh, shahar = ("Ali", 20, "Buxoro")
print(ism, yosh, shahar)

# * bilan qolganlarni listga yig'ish
sonlar = (1, 2, 3, 4, 5)
birinchi, *qolgani, oxirgi = sonlar
print(birinchi, qolgani, oxirgi)     # 1 [2, 3, 4] 5
```

## List <-> Tuple aylanishi

```python
mevalar_list = ["olma", "banan"]
mevalar_tuple = tuple(mevalar_list)     # listdan tuple
qayta_list = list(mevalar_tuple)          # tuple'dan list
```

## Set — noyob elementlar to'plami

```python
mevalar = {"olma", "banan", "olma"}      # takrorlanuvchi avtomatik olib tashlanadi
print(mevalar)                              # {'olma', 'banan'}

bosh_set = set()          # DIQQAT: {} EMAS! {} — bo'sh dictionary yaratadi
```

## Set — TO'LIQ METODLAR RO'YXATI

```python
mevalar = {"olma", "banan"}

mevalar.add("uzum")                # bitta element qo'shish
mevalar.update(["anor", "nok"])       # bir nechta element qo'shish (list, tuple, boshqa set)

mevalar.remove("banan")                  # o'chirish (mavjud bo'lmasa XATOLIK)
mevalar.discard("shaftoli")                 # o'chirish (mavjud bo'lmasa xatolik BERMAYDI)
elementi = mevalar.pop()                       # tasodifiy elementni o'chiradi va qaytaradi (tartib yo'q!)
mevalar.clear()                                   # barchasini tozalaydi
```

## Set matematikasi — to'liq

```python
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

print(a | b)             # union() bilan bir xil — birlashma: {1,2,3,4,5,6}
print(a & b)                # intersection() — kesishma: {3,4}
print(a - b)                   # difference() — farq: {1,2}
print(a ^ b)                      # symmetric_difference() — ikkalasida ham bo'lmagan: {1,2,5,6}

print(a.union(b))
print(a.intersection(b))
print(a.difference(b))
print(a.symmetric_difference(b))

print({1,2}.issubset(a))          # True — {1,2} — a ning qism to'plamimi
print(a.issuperset({1,2}))           # True — a, {1,2}ni o'z ichiga oladimi
print(a.isdisjoint({9,10}))             # True — umumiy elementi yo'qmi
```

## List, Tuple, Set — qачон qaysi biri?

| Ma'lumot turi | O'zgaruvchanmi | Tartibli | Takrorlanish | Tezlik (qidirish) |
|---|---|---|---|---|
| `list` | Ha | Ha | Ruxsat | O'rtacha |
| `tuple` | Yo'q | Ha | Ruxsat | O'rtacha, lekin tezroq |
| `set` | Ha | Yo'q | Ruxsat etilmaydi | Juda tez |

## Ro'yxatlar bilan ko'proq amaliy ishlash

```python
sonlar = [3, 1, 4, 1, 5, 9, 2, 6]

print(sum(sonlar))            # yig'indi
print(sorted(sonlar))            # yangi saralangan list
print(list(set(sonlar)))            # takrorsiz elementlar

ismlar = ["Ali", "Vali"]
yoshlar = [20, 22]
for ism, yosh in zip(ismlar, yoshlar):     # zip — ikki ro'yxatni birlashtirish
    print(f"{ism}: {yosh}")

lugat = dict(zip(ismlar, yoshlar))            # zip + dict — juda foydali kombinatsiya
print(lugat)          # {'Ali': 20, 'Vali': 22}
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ism, yosh, shahardan iborat tuple yarating va uni 3 ta o'zgaruvchiga unpacking qiling.
2. Bitta elementli tuple to'g'ri yarating (`(5,)`) va uning turini tekshiring.
3. Takrorlanuvchi elementli list'dan set yasang va noyob elementlarni chiqaring.
4. `.add()`, `.remove()`, `.discard()` metodlarini set ustida sinab ko'ring.
5. Ikkita set'ning birlashmasi (`|`), kesishmasi (`&`), farqi (`-`) ni toping.
6. `zip()` yordamida ikkita ro'yxatni (ism va yosh) birlashtirib chiqaring.
7. `zip()` va `dict()`ni birlashtirib, ikkita listdan dictionary yasang.
8. `sorted()` funksiyasi bilan ro'yxatni saralab, asl ro'yxat o'zgarmaganini tekshiring.

🟡 **O'rta (9-15)**

9. Ikki guruh talabalarining ismlaridan (set) ikkalasida ham bor va faqat bittasida bor talabalarni toping.
10. Funksiya yozing — u ikkita son qabul qilib, ularning yig'indisi va ko'paytmasini tuple ko'rinishida qaytarsin.
11. `symmetric_difference()` (`^`) metodini amaliy misolda (masalan ikki do'kon mahsulotlari) sinab ko'ring.
12. `issubset()` va `issuperset()` metodlarini amaliy misolda sinab ko'ring.
13. Matndagi noyob (takrorlanmagan) harflar sonini `set()` yordamida hisoblang.
14. `*` operatoridan foydalanib, 5 elementli tuple'ning birinchi, oxirgi va o'rtadagi elementlarini alohida ajrating.
15. Talabalar ismi va bahosidan iborat tuple'lar ro'yxatini yarating va eng yuqori baholini toping.

🔴 **Qiyin (16-20)**

16. Uchta do'kon uchun mahsulot to'plamlarini (set) yarating va barcha uchta do'konda ham bor mahsulotlarni (`&` bilan uchtasini) toping.
17. Katta ro'yxatdagi (100+ element) eng ko'p uchraydigan 3 ta elementni (`set` va `.count()` yordamida) toping.
18. Ikki ro'yxatni (mahsulot nomi va narxi) `zip()` bilan birlashtirib, `dict()` yordamida to'liq lug'atga aylantiring.
19. `isdisjoint()` metodidan foydalanib, ikki sinf o'quvchilari orasida umuman umumiy o'quvchi yo'qligini tekshiring.
20. Talabalar ma'lumotlarini (ism, 3 ta baho) tuple sifatida saqlab, har birining o'rtacha bahosini hisoblab, eng yaxshi 3 talabani `sorted()` va `key=lambda` bilan chiqaring.

---

**Oldingi mavzu:** [06 — List (ro'yxat)](./06_list.md)
**Keyingi mavzu:** [08 — For takrorlash operatori](./08_for_loop.md)
