# 18 — FUNKSIYA VA RO'YXAT

## Ro'yxatni funksiyaga uzatish

```python
def royxatni_korsat(elementlar):
    for element in elementlar:
        print(element)

mevalar = ["olma", "banan", "uzum"]
royxatni_korsat(mevalar)
```

## Funksiya ichida ro'yxatni o'zgartirish — muhim tushuncha (mutable vs immutable)

Listlar **mutable (o'zgaruvchan)** bo'lgani uchun, funksiya ichida o'zgartirilsa, bu o'zgarish **funksiyadan tashqarida ham** saqlanadi:

```python
def element_qoshish(royxat):
    royxat.append("yangi element")

mevalar = ["olma", "banan"]
element_qoshish(mevalar)
print(mevalar)     # ['olma', 'banan', 'yangi element'] — o'zgardi!
```

Bu — sonlar (`int`), string, tuple bilan farq qiladi, chunki ular **immutable (o'zgarmas)**:

```python
def songa_5_qoshish(son):
    son += 5

x = 10
songa_5_qoshish(x)
print(x)     # 10 — o'ZGARMADI!

def matnni_ozgartir(matn):
    matn += " qo'shimcha"

m = "salom"
matnni_ozgartir(m)
print(m)     # "salom" — o'ZGARMADI!
```

**Xulosa jadvali — qaysi turlar mutable, qaysilar immutable:**

| Mutable (o'zgaruvchan) | Immutable (o'zgarmas) |
|---|---|
| `list` | `int`, `float` |
| `dict` | `str` |
| `set` | `tuple` |
| | `bool` |

## Ro'yxatni o'zgartirmaslikni xohlasangiz — nusxa (copy) bering

```python
def yangi_royxat(royxat):
    nusxa = royxat.copy()      # yoki royxat[:] yoki list(royxat)
    nusxa.append("test")
    return nusxa

mevalar = ["olma", "banan"]
yangisi = yangi_royxat(mevalar)
print(mevalar)     # o'zgarmadi
print(yangisi)       # yangi element bilan
```

## Ro'yxatni filtrlab qaytarish

```python
def musbatlar(sonlar):
    return [x for x in sonlar if x > 0]

natija = musbatlar([-3, 5, -1, 8, 0, 2])
print(natija)     # [5, 8, 2]
```

## Funksiyaga list qabul qilib, statistikasini qaytarish

```python
def statistika(sonlar):
    return {
        "yigindi": sum(sonlar),
        "ortacha": sum(sonlar) / len(sonlar),
        "eng_katta": max(sonlar),
        "eng_kichik": min(sonlar),
        "soni": len(sonlar)
    }

print(statistika([4, 8, 15, 16, 23, 42]))
```

## Ro'yxat va *args farqi (eslatma keyingi mavzu uchun)

```python
def royxat_bilan(royxat):        # bitta argument — list
    return sum(royxat)

def args_bilan(*sonlar):            # istalgan sondagi alohida argumentlar
    return sum(sonlar)

print(royxat_bilan([1, 2, 3]))       # royxat sifatida beriladi
print(args_bilan(1, 2, 3))              # alohida-alohida beriladi
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ro'yxatni qabul qilib, uning barcha elementlarini chop etuvchi funksiya yozing.
2. Ro'yxatni qabul qilib, uning yig'indisini qaytaruvchi funksiya yozing (`sum()`siz, tsikl bilan).
3. Ro'yxatga element qo'shuvchi funksiya yozing va uni chaqirib, asl ro'yxat o'zgarganini tekshiring.
4. Ro'yxatni qabul qilib, faqat juft sonlarni qaytaruvchi funksiya yozing.
5. Ro'yxatni qabul qilib, uning uzunligini qaytaruvchi funksiya yozing (`len()`siz, tsikl bilan).
6. Ro'yxatni qabul qilib, uning nusxasini yaratib, nusxaga element qo'shuvchi funksiya yozing (asl o'zgarmasligini tekshiring).
7. `int`, `str`, `tuple` (immutable) va `list` (mutable) bilan bir xil "o'zgartirish" sinovini o'tkazib, farqni izohlab yozing.
8. Ro'yxatni qabul qilib, undagi eng katta qiymatni qaytaruvchi funksiya yozing.

🟡 **O'rta (9-15)**

9. Sonlar ro'yxatini qabul qilib, {yig'indi, o'rtacha, eng katta, eng kichik} dictionary qaytaruvchi funksiya yozing.
10. Ro'yxatni qabul qilib, undan takrorlanuvchi elementlarni olib tashlab qaytaruvchi funksiya yozing.
11. Ikki ro'yxatni qabul qilib, ularning umumiy elementlarini qaytaruvchi funksiya yozing.
12. Talabalar ro'yxatini (list-of-dict) qabul qilib, eng yuqori bahoga ega talabani qaytaruvchi funksiya yozing.
13. Ro'yxatni qabul qilib, uni ikkiga (juft va toq indeksli elementlar) bo'luvchi funksiya yozing.
14. Ro'yxat va son (chegara) qabul qilib, chegaradan katta elementlarni qaytaruvchi funksiya yozing.
15. Matnlar ro'yxatini qabul qilib, eng uzun so'zni qaytaruvchi funksiya yozing.

🔴 **Qiyin (16-20)**

16. Ro'yxatni qabul qilib, uni "sahifalarga" (masalan har biri 3 elementdan) bo'luvchi funksiya yozing.
17. Talabalar ro'yxati (ism, bir nechta baho) qabul qilinib, har birining o'rtacha bahosi qo'shilgan yangi ro'yxat qaytaruvchi funksiya yozing.
18. Ikki funksiya yozing: biri ro'yxatni o'zgartiradi (mutate), ikkinchisi yangi nusxa qaytaradi — ikkalasini chaqirib, farqini solishtiring va izohlang.
19. Mahsulotlar ro'yxatini (nomi, narxi, miqdori) qabul qilib, umumiy qiymati eng yuqori bo'lgan 3 ta mahsulotni qaytaruvchi funksiya yozing.
20. Rekursiv funksiya yozing — ro'yxatning yig'indisini rekursiya orqali hisoblang (`return royxat[0] + yigindi(royxat[1:])` mantig'ida).

---

**Oldingi mavzu:** [17 — Qiymat qaytaruvchi funksiya](./17_qiymat_qaytarish.md)
**Keyingi mavzu:** [19 — Moslashuvchan funksiya (*args, **kwargs)](./19_moslashuvchan_funksiya.md)
