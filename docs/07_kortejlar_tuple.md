# KORTEJLAR (TUPLE)

## Tuple nima?

**Tuple (kortej)** — listga juda o'xshash, lekin bitta muhim farq bilan: tuple yaratilgandan keyin **o'zgartirib bo'lmaydi** (immutable). Doira qavs `()` ichida yoziladi.

```python
kordinata = (41.311, 69.240)
print(kordinata)
print(type(kordinata))
```

```
(41.311, 69.24)
<class 'tuple'>
```

## Nega tuple kerak, agar list bor bo'lsa?

1. **Xavfsizlik** — ma'lumot tasodifan o'zgartirilib qo'yilishining oldini oladi (masalan geografik koordinatalar, oy nomlari kabi o'zgarmasligi kerak bo'lgan qiymatlar)
2. **Tezlik** — tuple listga qaraganda xotirada kamroq joy egallaydi va tezroq ishlaydi
3. **Dictionary kaliti sifatida** — tuple'ni lug'at kaliti qilib ishlatish mumkin, listni esa yo'q (buni Lug'atlar mavzusida ko'ramiz)

## Yaratish usullari

```python
bosh1 = (1, 2, 3)
bosh2 = 1, 2, 3          # qavssiz ham yozish mumkin
bosh3 = tuple([1, 2, 3])  # listdan tuple yasash

# bitta elementli tuple — DIQQAT, vergul shart!
bitta = (5,)               # bu tuple
notuple = (5)                # bu oddiy int, tuple EMAS!
print(type(bitta))          # <class 'tuple'>
print(type(notuple))        # <class 'int'>
```

## Indekslash va kesish

Tuple ustida list'dagi kabi indeks va slicing ishlaydi:

```python
mevalar = ("olma", "banan", "uzum", "anor")

print(mevalar[0])       # olma
print(mevalar[-1])      # anor
print(mevalar[1:3])     # ('banan', 'uzum')
```

## Tuple o'zgarmasligi (immutability)

```python
mevalar = ("olma", "banan")
# mevalar[0] = "shaftoli"    # XATOLIK! TypeError: 'tuple' object does not support item assignment
```

Agar tuple ichidagi qiymatlarni o'zgartirish zarur bo'lsa, uni avval listga aylantirish kerak:

```python
mevalar = ("olma", "banan")
royxat = list(mevalar)
royxat[0] = "shaftoli"
mevalar = tuple(royxat)
print(mevalar)
```

```
('shaftoli', 'banan')
```

## Tuple metodlari

Tuple o'zgarmas bo'lgani uchun list'dagidek ko'p metodlarga ega emas — faqat ikkitasi bor:

```python
sonlar = (3, 5, 3, 8, 3, 1)

print(sonlar.count(3))    # 3 — nechta 3 borligi
print(sonlar.index(8))    # 3 — 8 ning indeksi
print(len(sonlar))         # 6 — uzunligi
```

## Tuple'ni "yechish" (unpacking)

Bu Python'ning eng qulay xususiyatlaridan biri — tuple elementlarini bir vaqtda bir nechta o'zgaruvchiga ajratib olish:

```python
kordinata = (41.311, 69.240)
kenglik, uzunlik = kordinata

print(kenglik)     # 41.311
print(uzunlik)      # 69.24
```

```python
odam = ("Sardor", 25, "Toshkent")
ism, yosh, shahar = odam
print(f"{ism} {yosh} yoshda, {shahar}da yashaydi")
```

`*` belgisi bilan qolgan qiymatlarni bitta listga yig'ish ham mumkin:

```python
sonlar = (1, 2, 3, 4, 5)
birinchi, *qolgani, oxirgi = sonlar
print(birinchi)     # 1
print(qolgani)        # [2, 3, 4]
print(oxirgi)          # 5
```

## Funksiyadan bir nechta qiymat qaytarish

Tuple'ning eng amaliy qo'llanilishlaridan biri — funksiya bir nechta natijani birdan qaytarishi kerak bo'lganda:

```python
def minmax(sonlar):
    return min(sonlar), max(sonlar)   # bu aslida tuple qaytaryapti

kichik, katta = minmax([5, 2, 9, 1, 7])
print(f"Eng kichik: {kichik}, eng katta: {katta}")
```

```
Eng kichik: 1, eng katta: 9
```

## List va Tuple qachon qaysi birini ishlatish kerak?

| Holat | Tanlov |
|---|---|
| Ma'lumot doim o'zgarib turadi (qo'shiladi, o'chiriladi) | **list** |
| Ma'lumot o'zgarmasligi kerak (konstantalar, koordinatalar) | **tuple** |
| Lug'atga kalit sifatida ishlatish kerak | **tuple** |
| Funksiyadan bir nechta qiymat qaytarish | **tuple** |
| Katta hajmdagi ma'lumot, tezlik muhim | **tuple** |

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. O'zingizning ism, yosh va shahringizdan iborat tuple yarating va uni unpacking orqali 3 ta o'zgaruvchiga ajrating.
2. Haftaning 7 kunidan iborat tuple yarating va uning uzunligini chiqaring.
3. Tuple ichida bitta elementni o'zgartirishga urinib ko'ring va chiqqan xatolikni o'qib, nima uchun bunday bo'lganini tushuntiring (izoh sifatida yozing).

🟡 **O'rta daraja**

4. Ikkita son qabul qilib, ularning yig'indisi va ko'paytmasini tuple ko'rinishida qaytaruvchi funksiya yozing, so'ng natijani ikkita alohida o'zgaruvchiga unpacking qiling.
5. Talabalar ismi va bahosidan iborat tuple'lar ro'yxatini yarating (masalan `[("Ali", 90), ("Vali", 75)]`) va eng yuqori baholi talabani toping.
6. `*` operatoridan foydalanib, 5 ta sondan iborat tuple'ning birinchi, oxirgi va o'rtadagilarini alohida o'zgaruvchilarga ajrating.

---

**Oldingi mavzu:** [06 — Ro'yxatlar (list)](./06_royxatlar_list.md)
**Keyingi mavzu:** [08 — Lug'atlar (dictionary)](./08_lugatlar_dictionary.md)
