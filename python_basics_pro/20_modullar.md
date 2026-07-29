# 20 — MODULLAR

## Modul nima?

Har qanday `.py` fayli — bu modul, uni boshqa faylga `import` qilish mumkin.

```python
import math
print(math.sqrt(25))     # 5.0
```

## import qilish usullari

```python
import math                    # butun modul
import math as m                 # qisqa nom bilan
from math import sqrt              # faqat bitta funksiya
from math import sqrt, pi, floor     # bir nechtasi
```

## O'z modulingizni yaratish

**`matematika.py`:**
```python
def qoshish(a, b):
    return a + b

PI = 3.14159
```

**`asosiy.py`:**
```python
import matematika
print(matematika.qoshish(5, 3))
```

## Eng foydali o'rnatilgan modullar

```python
import random
print(random.randint(1, 100))         # tasodifiy son
print(random.choice(["a", "b", "c"]))    # ro'yxatdan tasodifiy

import datetime
print(datetime.datetime.now())            # joriy vaqt

import os
print(os.getcwd())                           # joriy papka
```

## if __name__ == "__main__":

```python
def test():
    print("test ishladi")

if __name__ == "__main__":     # faqat to'g'ridan-to'g'ri ishga tushirilsa
    test()
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. `math` modulidan foydalanib, sonning kvadrat ildizini toping.
2. `random.randint()` bilan 1-6 (zar) tasodifiy son generatsiya qiling.
3. `datetime` modulidan foydalanib, joriy sana va vaqtni chiqaring.
4. O'zingizning `salomlash.py` modulingizni yarating (bitta funksiya bilan) va uni boshqa fayldan import qiling.
5. `import math as m` yozib, qisqa nom bilan `m.pi` ni chiqaring.
6. `from math import sqrt, pow` yozib, ikkalasini alohida ishlatib ko'ring.
7. `random.choice()` bilan ro'yxatdan tasodifiy element tanlang.
8. `os.getcwd()` bilan joriy papka yo'lini chiqaring.

🟡 **O'rta (9-15)**

9. O'zingizning `geometriya.py` modulingizni yarating — ichida doira yuzi va perimetrini hisoblovchi 2 ta funksiya bo'lsin.
10. `random.shuffle()` bilan ro'yxatni aralashtiring.
11. "Tosh-qaychi-qog'oz" o'yinida kompyuter tanlovini `random.choice()` bilan generatsiya qiling.
12. `if __name__ == "__main__":` dan foydalanib, modulingizni ham mustaqil, ham import qilingan holda sinab ko'ring.
13. `datetime` yordamida, ikkita sana orasidagi kunlar farqini hisoblang.
14. `os.listdir()` bilan joriy papkadagi barcha fayllarni ro'yxatga oling.
15. 2 ta modulli (`matematik.py`, `matnlar.py`) kichik loyiha yarating, asosiy faylda ikkalasidan ham foydalaning.

🔴 **Qiyin (16-20)**

16. O'zingizning `validatsiya.py` modulingizni yarating — email va telefon raqamini tekshiruvchi funksiyalar bilan.
17. `random` va `datetime`ni birlashtirib, "kunlik tasodifiy vazifa generatori" yozing (bugungi sana + tasodifiy tanlangan vazifa).
18. Paket (papka + `__init__.py`) tuzilmasini yarating — ichida kamida 2 ta modul, har birida 2 tadan funksiya.
19. `os` modulidan foydalanib, joriy papkadagi barcha `.py` fayllarni ro'yxatga olib, ularning umumiy sonini chiqaring.
20. To'liq "shaxsiy vositalar kutubxonasi" modulini yarating — kamida 5 ta turli funksiya (matematik, matn, sana bilan bog'liq) va uni asosiy dasturda sinovdan o'tkazing.

---

**Oldingi mavzu:** [19 — Moslashuvchan funksiya](./19_moslashuvchan_funksiya.md)
**Keyingi mavzu:** [21 — Funksiyalar. Lambda va so'ngso'z](./21_lambda_songsoz.md)
