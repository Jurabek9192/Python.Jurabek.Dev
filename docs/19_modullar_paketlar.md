# MODULLAR VA PAKETLAR (ASOSLAR)

## Modul nima?

**Modul** — Python kodi yozilgan `.py` fayl. Har qanday Python fayli — bu modul, va uni boshqa fayllarga **import** qilish (chaqirib olish) mumkin. Bu kodni bo'laklarga bo'lib, qayta ishlatish imkonini beradi.

## Nega modullar kerak?

Butun loyihani bitta ulkan faylga yozish o'rniga, kodni mantiqiy qismlarga bo'lib, alohida fayllarga joylashtiramiz:

- `matematika.py` — matematik funksiyalar
- `foydalanuvchi.py` — foydalanuvchi bilan bog'liq funksiyalar
- `asosiy.py` — dasturning bosh fayli, boshqalarini chaqiradi

Bu kodni tartibli, boshqarish oson va jamoada ishlash uchun qulay qiladi.

## Python'ning o'rnatilgan modullari (standard library)

Python o'zi bilan birga juda ko'p tayyor modullarni olib keladi. Ulardan foydalanish uchun `import` kalit so'zi ishlatiladi:

```python
import math

print(math.sqrt(25))     # 5.0
print(math.pi)             # 3.141592653589793
print(math.floor(4.7))    # 4
```

## import qilishning turli usullari

```python
# 1. Butun modulni import qilish
import math
print(math.sqrt(16))

# 2. Modulga qisqa nom (alias) berish
import math as m
print(m.sqrt(16))

# 3. Faqat kerakli funksiyani import qilish
from math import sqrt
print(sqrt(16))           # endi math. yozish shart emas

# 4. Bir nechta funksiyani import qilish
from math import sqrt, pi, floor
print(sqrt(16), pi, floor(4.7))

# 5. Hammasini import qilish (TAVSIYA ETILMAYDI)
from math import *
print(sqrt(16))
```

**Muhim eslatma:** `from module import *` odatda tavsiya etilmaydi, chunki qaysi funksiya qaysi moduldan kelganini aniqlash qiyinlashadi va nomlar to'qnashishi mumkin. Har doim aniq import qilish (`import math` yoki `from math import sqrt`) yaxshiroq amaliyot hisoblanadi.

## Ko'p ishlatiladigan o'rnatilgan modullar

### random — tasodifiy qiymatlar

```python
import random

print(random.randint(1, 100))       # 1 dan 100 gacha tasodifiy son
print(random.choice(["olma", "banan", "uzum"]))  # ro'yxatdan tasodifiy tanlov
print(random.random())               # 0 va 1 orasida tasodifiy kasr son

royxat = [1, 2, 3, 4, 5]
random.shuffle(royxat)                # ro'yxatni aralashtiradi
print(royxat)
```

### datetime — sana va vaqt

```python
from datetime import datetime

hozir = datetime.now()
print(hozir)                          # 2026-07-28 14:23:10.123456
print(hozir.year)                     # 2026
print(hozir.strftime("%d-%m-%Y"))     # 28-07-2026
```

### os — operatsion tizim bilan ishlash

```python
import os

print(os.getcwd())          # joriy papkani ko'rsatadi
print(os.listdir("."))       # joriy papkadagi fayllar ro'yxati
```

## O'zingizning modulingizni yaratish

Ikkita faylni tasavvur qiling:

**`matematika.py`** (modul fayli):
```python
def qoshish(a, b):
    return a + b

def ayirish(a, b):
    return a - b

PI = 3.14159
```

**`asosiy.py`** (asosiy fayl, xuddi shu papkada):
```python
import matematika

print(matematika.qoshish(5, 3))       # 8
print(matematika.ayirish(10, 4))       # 6
print(matematika.PI)                    # 3.14159
```

Yoki aniqroq import:

```python
from matematika import qoshish, PI

print(qoshish(5, 3))
print(PI)
```

## `if __name__ == "__main__":` nima uchun kerak?

Bu Python'da juda ko'p uchraydigan naqsh. Har bir modul, agar to'g'ridan-to'g'ri ishga tushirilsa, `__name__` o'zgaruvchisiga `"__main__"` qiymatini oladi. Lekin agar u boshqa fayl tomonidan import qilingan bo'lsa, `__name__` modul nomiga teng bo'ladi.

**`matematika.py`:**
```python
def qoshish(a, b):
    return a + b

if __name__ == "__main__":
    # bu qism faqat matematika.py to'g'ridan-to'g'ri ishga tushirilganda ishlaydi
    # boshqa fayl uni import qilganda ISHLAMAYDI
    print("Test:", qoshish(2, 3))
```

Bu, masalan, har bir modulni mustaqil test qilish, lekin boshqa fayllarga import qilinganda ortiqcha kod ishlab ketmasligi uchun ishlatiladi.

## Paket (package) nima?

**Paket** — ichida bir nechta modul (`.py` fayllar) va `__init__.py` fayli bo'lgan papka. Paket — bu modullarni yanada kattaroq guruhlarga birlashtirish usuli.

```
mening_loyiham/
│
├── matematika/
│   ├── __init__.py
│   ├── asosiy_amallar.py
│   └── geometriya.py
│
└── asosiy.py
```

```python
# asosiy.py ichida
from matematika import asosiy_amallar
from matematika.geometriya import doira_yuzi
```

`__init__.py` fayli — Python'ga bu papka oddiy papka emas, balki paket ekanligini bildiradi (ba'zan bo'sh bo'lishi ham mumkin).

## pip — tashqi kutubxonalarni o'rnatish

Python'ning o'rnatilgan modullaridan tashqari, minglab **tashqi kutubxonalar** mavjud (masalan `requests`, `pandas`, `numpy`). Ularni o'rnatish uchun `pip` (Python'ning paket menejeri) ishlatiladi:

```bash
pip install requests
```

O'rnatilgandan keyin, oddiy modul kabi import qilinadi:

```python
import requests
```

Bu mavzuni Kitob 3'da (venv va pip — muhit boshqaruvi) chuqurroq ko'ramiz.

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. `math` modulidan foydalanib, foydalanuvchi kiritgan sonning kvadrat ildizini toping.
2. `random` modulidan foydalanib, 1 dan 6 gacha (zar) tasodifiy son generatsiya qiluvchi dastur yozing.
3. `datetime` modulidan foydalanib, joriy sana va vaqtni chiqaring.

🟡 **O'rta daraja**

4. O'zingizning `geometriya.py` nomli modulingizni yarating — unda doira yuzi va perimetrini hisoblovchi ikkita funksiya bo'lsin. Boshqa faylda uni import qilib ishlatib ko'ring.
5. `random.choice()` yordamida "tosh-qaychi-qog'oz" o'yinida kompyuter tanlovini tasodifiy generatsiya qiling.
6. `os` modulidan foydalanib, joriy papkadagi barcha `.py` fayllarni ro'yxatga oling (`os.listdir()` va `.endswith()` dan foydalaning).

🔴 **Murakkabroq**

7. `__init__.py` bilan oddiy paket tuzilmasini yarating: ichida kamida 2 ta modul (`matematik.py`, `matn.py`) bo'lsin, har birida kamida 2 tadan funksiya. Asosiy faylda ikkalasidan ham foydalaning.

---

**Oldingi mavzu:** [18 — List comprehension](./18_list_comprehension.md)
**Keyingi mavzu:** [20 — Yakuniy loyiha](./20_yakuniy_loyiha.md)
