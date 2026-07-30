# 20 — MODULLAR

## Modul nima?

Har qanday `.py` fayli — bu modul, uni boshqa faylga `import` qilish mumkin.

```python
import math
print(math.sqrt(25))     # 5.0
```

## import qilish usullari — barchasi

```python
import math                        # butun modul
import math as m                     # qisqa nom bilan (alias)
from math import sqrt                  # faqat bitta funksiya
from math import sqrt, pi, floor          # bir nechtasi
from math import *                          # HAMMASINI (tavsiya etilmaydi!)
```

**Nega `from module import *` tavsiya etilmaydi?** Chunki qaysi funksiya qaysi moduldan kelganini bilish qiyinlashadi va nomlar to'qnashib qolishi mumkin.

## O'z modulingizni yaratish

**`matematika.py`:**
```python
def qoshish(a, b):
    return a + b

def ayirish(a, b):
    return a - b

PI = 3.14159
```

**`asosiy.py`:**
```python
import matematika
print(matematika.qoshish(5, 3))
print(matematika.PI)

from matematika import qoshish
print(qoshish(10, 5))
```

## Python'ning eng foydali o'rnatilgan modullari

### random — to'liq imkoniyatlar

```python
import random

print(random.randint(1, 100))         # 1 dan 100 gacha (ikkalasi ham kiradi)
print(random.random())                    # 0.0 - 1.0 orasida kasr
print(random.uniform(1.5, 5.5))              # ikki kasr son oralig'ida
print(random.choice(["a", "b", "c"]))            # ro'yxatdan bitta tasodifiy
print(random.choices(["a","b","c"], k=2))           # takrorlanishi mumkin bo'lgan 2 ta tanlov
print(random.sample(["a","b","c","d"], 2))            # takrorlanmaydigan 2 ta tanlov
royxat = [1, 2, 3, 4, 5]
random.shuffle(royxat)                                    # ro'yxatni joyida aralashtiradi
print(royxat)
```

### datetime — to'liq imkoniyatlar

```python
import datetime

hozir = datetime.datetime.now()
print(hozir)                                      # joriy sana+vaqt
print(hozir.year, hozir.month, hozir.day)             # qismlarga bo'lib olish
print(hozir.strftime("%d-%m-%Y %H:%M"))                  # chiroyli formatlash

bugun = datetime.date.today()
print(bugun)

farq = datetime.timedelta(days=7)
keyingi_hafta = bugun + farq
print(keyingi_hafta)
```

### os — fayl tizimi bilan ishlash

```python
import os

print(os.getcwd())              # joriy papka
print(os.listdir("."))             # joriy papkadagi fayllar ro'yxati
os.mkdir("yangi_papka")               # yangi papka yaratish
print(os.path.exists("bot.py"))          # fayl mavjudmi
print(os.path.join("papka", "fayl.txt"))    # yo'llarni to'g'ri birlashtirish
```

### sys — tizim bilan bog'liq

```python
import sys

print(sys.version)          # Python versiyasi
print(sys.argv)                # terminal orqali berilgan argumentlar
```

## if __name__ == "__main__":

```python
def test():
    print("test ishladi")

if __name__ == "__main__":     # faqat bu fayl to'g'ridan-to'g'ri ishga tushirilsa
    test()                          # boshqa fayl bu modulni import qilsa, bu qism ISHLAMAYDI
```

## Paket (package) — bir nechta modulni birlashtirish

```
mening_paketim/
├── __init__.py
├── matematika.py
└── matnlar.py
```

`__init__.py` — Python'ga "bu papka oddiy papka emas, paket" ekanligini bildiradi (bo'sh bo'lishi ham mumkin).

```python
from mening_paketim import matematika
from mening_paketim.matnlar import katta_qil
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. `math` modulidan foydalanib, sonning kvadrat ildizini toping.
2. `random.randint()` bilan 1-6 (zar) tasodifiy son generatsiya qiling.
3. `datetime` modulidan foydalanib, joriy sana va vaqtni chiqaring.
4. O'zingizning `salomlash.py` modulingizni yarating (bitta funksiya bilan) va uni boshqa fayldan import qiling.
5. `import math as m` yozib, qisqa nom bilan `m.pi` ni chiqaring.
6. `random.choice()` va `random.sample()` farqini sinab ko'ring.
7. `os.getcwd()` va `os.listdir()` bilan joriy papka haqida ma'lumot chiqaring.
8. `sys.version` yordamida qaysi Python versiyasida ishlayotganingizni tekshiring.

🟡 **O'rta (9-15)**

9. O'zingizning `geometriya.py` modulingizni yarating — ichida doira yuzi va perimetrini hisoblovchi 2 ta funksiya bo'lsin.
10. `random.shuffle()` bilan ro'yxatni aralashtiring.
11. "Tosh-qaychi-qog'oz" o'yinida kompyuter tanlovini `random.choice()` bilan generatsiya qiling.
12. `if __name__ == "__main__":` dan foydalanib, modulingizni ham mustaqil, ham import qilingan holda sinab ko'ring.
13. `datetime.timedelta` yordamida, bugungi sanaga 30 kun qo'shib, natijani chiqaring.
14. `os.path.exists()` bilan fayl mavjudligini tekshirib, mavjud bo'lmasa xabar bering.
15. 2 ta modulli (`matematik.py`, `matnlar.py`) kichik loyiha yarating, asosiy faylda ikkalasidan ham foydalaning.

🔴 **Qiyin (16-20)**

16. O'zingizning `validatsiya.py` modulingizni yarating — email va telefon raqamini tekshiruvchi funksiyalar bilan.
17. `random` va `datetime`ni birlashtirib, "kunlik tasodifiy vazifa generatori" yozing.
18. To'liq paket (papka + `__init__.py`) tuzilmasini yarating — ichida kamida 2 ta modul, har birida 2 tadan funksiya, va ularni `__init__.py` orqali qisqa import qilinadigan qiling.
19. `os` modulidan foydalanib, joriy papkadagi barcha `.py` fayllarni ro'yxatga olib, ularning umumiy sonini chiqaring.
20. To'liq "shaxsiy vositalar kutubxonasi" modulini yarating — kamida 5 ta turli funksiya (matematik, matn, sana bilan bog'liq) va uni asosiy dasturda sinovdan o'tkazing.

---

**Oldingi mavzu:** [19 — Moslashuvchan funksiya](./19_moslashuvchan_funksiya.md)
**Keyingi mavzu:** [21 — Funksiyalar. Lambda va so'ngso'z](./21_lambda_songsoz.md)
