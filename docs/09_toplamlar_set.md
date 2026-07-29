# TO'PLAMLAR (SET)

## Set nima?

**Set (to'plam)** — takrorlanuvchi elementlarni o'z ichiga olmaydigan, tartibsiz (unordered) ma'lumot to'plami. Jingalak qavs `{}` ichida yoziladi, lekin dictionary'dan farqli o'laroq faqat qiymatlardan iborat, kalit-qiymat juftligidan emas.

```python
mevalar = {"olma", "banan", "uzum", "olma"}   # "olma" ikki marta yozilgan
print(mevalar)
print(type(mevalar))
```

```
{'olma', 'banan', 'uzum'}
<class 'set'>
```

Diqqat qiling — natijada `"olma"` faqat bir marta qoldi. Set'ning eng asosiy vazifasi ham shu: **takrorlanuvchi qiymatlarni avtomatik olib tashlaydi.**

## Bo'sh set yaratish

```python
# DIQQAT: {} bo'sh dictionary yaratadi, bo'sh set EMAS!
notoplam = {}
print(type(notoplam))    # <class 'dict'>

toplam = set()             # bo'sh set to'g'ri yaratish usuli
print(type(toplam))        # <class 'set'>
```

## Listdan set yaratish — takrorlarni tozalash

Bu set'ning eng ko'p ishlatiladigan amaliy qo'llanilishi:

```python
sonlar = [1, 2, 2, 3, 4, 4, 4, 5]
noyob = set(sonlar)
print(noyob)                # {1, 2, 3, 4, 5}

# qaytadan listga aylantirish
tozalangan = list(noyob)
print(tozalangan)
```

## Elementlarni qo'shish va o'chirish

```python
mevalar = {"olma", "banan"}

mevalar.add("uzum")            # bitta element qo'shish
print(mevalar)

mevalar.update(["anor", "nok"]) # bir nechta element qo'shish
print(mevalar)

mevalar.remove("banan")         # o'chirish (mavjud bo'lmasa xatolik beradi)
mevalar.discard("shaftoli")     # o'chirish (mavjud bo'lmasa xatolik BERMAYDI)
print(mevalar)
```

## Set — indekslanmaydi!

Set tartibsiz to'plam bo'lgani uchun uning elementlariga indeks orqali murojaat qilib bo'lmaydi:

```python
mevalar = {"olma", "banan", "uzum"}
# print(mevalar[0])    # XATOLIK! TypeError: 'set' object is not subscriptable
```

Agar biror elementga alohida murojaat qilish zarur bo'lsa, avval uni listga aylantirish kerak.

## To'plamlar matematikasi

Set'ning eng kuchli tomoni — matematik to'plamlar nazariyasidagi amallarni to'g'ridan-to'g'ri bajara olishi:

```python
a = {1, 2, 3, 4, 5}
b = {4, 5, 6, 7, 8}

print(a | b)     # birlashma (union): {1,2,3,4,5,6,7,8}
print(a & b)     # kesishma (intersection): {4, 5}
print(a - b)     # farq (difference): {1,2,3} — faqat a'da bor
print(b - a)     # farq: {6,7,8} — faqat b'da bor
print(a ^ b)     # simmetrik farq: {1,2,3,6,7,8} — ikkalasida ham bo'lmagan
```

Yoki metod ko'rinishida:

```python
print(a.union(b))
print(a.intersection(b))
print(a.difference(b))
print(a.symmetric_difference(b))
```

## Amaliy misol: ikki sinf o'quvchilarini solishtirish

```python
tanlov_bo_limi = {"Ali", "Vali", "Guli", "Laylo"}
sport_bo_limi = {"Vali", "Bekzod", "Laylo", "Sardor"}

print("Ikkala to'garakka ham qatnashadi:", tanlov_bo_limi & sport_bo_limi)
print("Faqat tanlov bo'limida:", tanlov_bo_limi - sport_bo_limi)
print("Ikkalasidan birortasiga qatnashadi:", tanlov_bo_limi | sport_bo_limi)
```

```
Ikkala to'garakka ham qatnashadi: {'Vali', 'Laylo'}
Faqat tanlov bo'limida: {'Ali', 'Guli'}
Ikkalasidan birortasiga qatnashadi: {'Ali', 'Vali', 'Guli', 'Laylo', 'Bekzod', 'Sardor'}
```

## To'plamlarni solishtirish

```python
a = {1, 2, 3}
b = {1, 2, 3, 4, 5}

print(a.issubset(b))       # True — a, b'ning qism to'plamimi
print(b.issuperset(a))     # True — b, a'ni o'z ichiga oladimi
print(a.isdisjoint({9, 10})) # True — umumiy elementi yo'qmi
```

## `in` operatori — juda tez ishlaydi

Set'da elementni qidirish list'ga qaraganda ancha tezroq ishlaydi (katta hajmdagi ma'lumotlar bilan ishlaganda bu muhim bo'ladi):

```python
katta_toplam = set(range(1000000))
print(999999 in katta_toplam)   # deyarli bir zumda tekshiradi
```

## Qachon set, qachon list?

| Holat | Tanlov |
|---|---|
| Tartib muhim | **list** |
| Takrorlanuvchi qiymatlar bo'lishi kerak | **list** |
| Faqat noyob qiymatlar kerak | **set** |
| Tez-tez "mavjudligini tekshirish" kerak | **set** |
| Matematik to'plam amallari kerak | **set** |

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. Takrorlanuvchi elementlari bor list yarating va uni set'ga aylantirib, noyob qiymatlarni chiqaring.
2. Ikkita to'plam (sevimli ranglar) yaratib, ularning birlashmasi va kesishmasini toping.
3. Set'ga yangi element qo'shing va bittasini o'chiring, natijani chiqaring.

🟡 **O'rta daraja**

4. Ikki guruh talabalarining ismlari (set ko'rinishida) berilgan — ikkala guruhda ham bor talabalarni va faqat birinchi guruhda bor talabalarni toping.
5. Foydalanuvchidan matn kiritilsin va undagi noyob harflar sonini (takrorlanmagan) toping (`set()` yordamida).
6. Ikki listdagi umumiy elementlarni topib, natijani yana listga aylantirib chiqaring.

---

**Oldingi mavzu:** [08 — Lug'atlar (dictionary)](./08_lugatlar_dictionary.md)
**Keyingi mavzu:** [10 — Shartlar — if/else](./10_shartlar_if_else.md)
