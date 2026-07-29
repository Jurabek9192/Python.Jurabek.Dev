# LUG'ATLAR (DICTIONARY)

## Dictionary nima?

**Dictionary (lug'at)** — ma'lumotlarni indeks (raqam) orqali emas, balki **kalit-qiymat (key-value)** juftliklari orqali saqlaydigan tur. Jingalak qavs `{}` ichida yoziladi.

```python
odam = {
    "ism": "Kamola",
    "yosh": 22,
    "shahar": "Andijon"
}
print(odam)
print(type(odam))
```

```
{'ism': 'Kamola', 'yosh': 22, 'shahar': 'Andijon'}
<class 'dict'>
```

Bu real hayotdagi lug'atga o'xshaydi — so'zni (kalit) qidirasiz va uning ma'nosini (qiymat) topasiz.

## Qiymatga murojaat qilish

List'dan farqli o'laroq, dictionary'da elementlarga **indeks emas, kalit orqali** murojaat qilinadi:

```python
odam = {"ism": "Kamola", "yosh": 22, "shahar": "Andijon"}

print(odam["ism"])       # Kamola
print(odam["yosh"])       # 22

# Agar kalit mavjud bo'lmasa, .get() xavfsizroq:
print(odam.get("kasb"))          # None (xatolik bermaydi)
print(odam.get("kasb", "Nomaʼlum"))  # standart qiymat bilan
```

**Diqqat:** `odam["kasb"]` — agar bunday kalit mavjud bo'lmasa, `KeyError` xatoligini beradi. Shu sabab mavjudligiga aniq ishonch bo'lmasa, `.get()` ishlatish tavsiya etiladi.

## Yangi qiymat qo'shish va o'zgartirish

```python
odam = {"ism": "Kamola", "yosh": 22}

odam["shahar"] = "Andijon"      # yangi kalit-qiymat qo'shildi
odam["yosh"] = 23                # mavjud qiymat o'zgartirildi

print(odam)
```

```
{'ism': 'Kamola', 'yosh': 23, 'shahar': 'Andijon'}
```

## Elementlarni o'chirish

```python
odam = {"ism": "Kamola", "yosh": 23, "shahar": "Andijon"}

del odam["shahar"]              # kalit orqali o'chirish
print(odam)                       # {'ism': 'Kamola', 'yosh': 23}

yosh = odam.pop("yosh")          # o'chiradi va qiymatini qaytaradi
print(yosh)                        # 23
print(odam)                        # {'ism': 'Kamola'}
```

## Muhim dictionary metodlari

```python
odam = {"ism": "Kamola", "yosh": 22, "shahar": "Andijon"}

print(odam.keys())      # dict_keys(['ism', 'yosh', 'shahar'])
print(odam.values())    # dict_values(['Kamola', 22, 'Andijon'])
print(odam.items())     # dict_items([('ism', 'Kamola'), ('yosh', 22), ('shahar', 'Andijon')])
```

Bu uchtasi ko'pincha tsikllar bilan birga ishlatiladi (`for` mavzusida chuqurroq ko'ramiz):

```python
for kalit in odam:
    print(kalit, "->", odam[kalit])

print("---")

for kalit, qiymat in odam.items():
    print(f"{kalit}: {qiymat}")
```

```
ism -> Kamola
yosh -> 22
shahar -> Andijon
---
ism: Kamola
yosh: 22
shahar: Andijon
```

## `in` operatori — kalit mavjudligini tekshirish

```python
odam = {"ism": "Kamola", "yosh": 22}

print("ism" in odam)         # True — DIQQAT: bu kalitlarni tekshiradi, qiymatlarni emas!
print("Kamola" in odam)       # False
print("Kamola" in odam.values())  # True — qiymatlar orasida tekshirish uchun .values()
```

## Ichma-ich lug'atlar (nested dictionary)

Real loyihalarda ko'pincha lug'at ichida lug'at bo'ladi — masalan bir nechta foydalanuvchi ma'lumotlarini saqlashda:

```python
talabalar = {
    "talaba1": {"ism": "Ali", "baho": 90},
    "talaba2": {"ism": "Vali", "baho": 85}
}

print(talabalar["talaba1"]["ism"])     # Ali
print(talabalar["talaba2"]["baho"])    # 85
```

## Dictionary bilan list birgalikda

```python
talabalar = [
    {"ism": "Ali", "baho": 90},
    {"ism": "Vali", "baho": 85},
    {"ism": "Guli", "baho": 95}
]

for talaba in talabalar:
    print(f"{talaba['ism']}: {talaba['baho']}")
```

Bu struktura — real hayotda API'lardan keladigan ma'lumotlarning (masalan JSON) eng tipik ko'rinishi bo'lib, siz keyinchalik Data Analytics bosqichida buni juda ko'p uchratasiz.

## `update()` — lug'atlarni birlashtirish

```python
odam = {"ism": "Kamola", "yosh": 22}
qoshimcha = {"shahar": "Andijon", "yosh": 23}   # yosh qayta yoziladi

odam.update(qoshimcha)
print(odam)
```

```
{'ism': 'Kamola', 'yosh': 23, 'shahar': 'Andijon'}
```

## Dictionary'ning muhim xususiyatlari

- Kalitlar **noyob (unique)** bo'lishi kerak — bir xil kalit ikki marta yozilsa, oxirgisi qoladi
- Kalit sifatida faqat **o'zgarmas (immutable)** turlar ishlatilishi mumkin: `str`, `int`, `tuple` — lekin `list` emas
- Python 3.7 versiyasidan boshlab dictionary elementlar qo'shilish tartibini saqlaydi

```python
# xato: list kalit sifatida ishlatilib bo'lmaydi
# malumot = {[1,2]: "qiymat"}   # TypeError

# to'g'ri: tuple kalit sifatida ishlatilishi mumkin
malumot = {(41.3, 69.2): "Toshkent"}
print(malumot)
```

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. O'zingiz haqingizda ism, yosh, shahar va kasbdan iborat dictionary yarating va har birini alohida chiqaring.
2. Yaratilgan dictionary'ga yangi kalit-qiymat qo'shing (masalan "hobbi") va bittasini o'zgartiring.
3. `.keys()`, `.values()`, `.items()` metodlarini sinab ko'ring va natijalarini chop eting.
4. Dictionary'da muayyan kalit mavjudligini `in` orqali tekshiring.

🟡 **O'rta daraja**

5. Mahsulot nomi va narxidan iborat dictionary yarating (kamida 5 ta mahsulot). Foydalanuvchidan mahsulot nomini so'rab, uning narxini `.get()` orqali xavfsiz chiqaring (mavjud bo'lmasa "Mahsulot topilmadi" deb yozing).
6. Talabalar ismi va baholaridan iborat dictionary yarating va eng yuqori bahoga ega talabani toping (`.items()` va tsikl yordamida).
7. Ikkita dictionary'ni `.update()` yordamida birlashtiring va natijani chiqaring.

🔴 **Murakkabroq**

8. Har biri ism, yosh va shahar kalitlariga ega bo'lgan 3 talabaning ma'lumotlarini o'z ichiga olgan list-of-dictionaries yarating. Shulardan 20 yoshdan katta bo'lganlarni ekranga chiqaring.

---

**Oldingi mavzu:** [07 — Kortejlar (tuple)](./07_kortejlar_tuple.md)
**Keyingi mavzu:** [09 — To'plamlar (set)](./09_toplamlar_set.md)
