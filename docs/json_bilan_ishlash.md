# JSON BILAN ISHLASH

## JSON nima?

**JSON (JavaScript Object Notation)** — internetda va dasturlar orasida ma'lumot almashishning eng keng tarqalgan formati. U Python'ning dictionary va list strukturasiga juda o'xshaydi, shu sababli Python bilan ishlash uchun juda qulay. Deyarli barcha zamonaviy API'lar (ob-havo xizmatlari, ijtimoiy tarmoqlar, to'lov tizimlari) ma'lumotni aynan JSON formatida qaytaradi. Telegram botlar (aiogram), veb-saytlar, mobil ilovalar — barchasi orqasida JSON ishlaydi.

**Misol JSON matni:**
```json
{
    "ism": "Ali",
    "yosh": 20,
    "faol": true,
    "baholar": [85, 90, 78],
    "manzil": {
        "shahar": "Toshkent",
        "tuman": "Chilonzor"
    },
    "telefon": null
}
```

Diqqat qiling — bu Python'ning dictionary yozilishiga deyarli bir xil, faqat muhim farqlar bilan: JSON'da `True`/`False`/`None` o'rniga kichik harfli `true`/`false`/`null` yoziladi, va kalitlar har doim qo'shtirnoq ichida bo'lishi shart.

## Python va JSON turlarining mos kelishi

| Python | JSON |
|---|---|
| `dict` | object `{}` |
| `list`, `tuple` | array `[]` |
| `str` | string |
| `int`, `float` | number |
| `True` / `False` | `true` / `false` |
| `None` | `null` |

**Diqqat:** `tuple` JSON'ga aylantirilganda **list**ga aylanadi — JSON'da tuple tushunchasi umuman yo'q. Shuning uchun tuple'ni JSON'ga saqlab, qaytadan o'qisangiz, u endi list bo'lib qoladi.

## json moduli — Python'ning o'rnatilgan vositasi

```python
import json     # hech narsa o'rnatish shart emas, Python bilan birga keladi
```

## 1. dumps() — Python obyektini JSON MATNIGA aylantirish

```python
import json

talaba = {
    "ism": "Ali",
    "yosh": 20,
    "faol": True,
    "baholar": [85, 90, 78]
}

json_matni = json.dumps(talaba)
print(json_matni)
print(type(json_matni))     # <class 'str'> — bu ENDI oddiy matn!
```

```
{"ism": "Ali", "yosh": 20, "faol": true, "baholar": [85, 90, 78]}
```

`dumps()` — **"dump string"** degan ma'noni bildiradi (esda tut: oxirida **`s`** bor — demak **string** bilan ishlaydi).

### Chiroyli formatlash — indent va ensure_ascii

```python
json_matni = json.dumps(talaba, indent=4, ensure_ascii=False)
print(json_matni)
```

```
{
    "ism": "Ali",
    "yosh": 20,
    "faol": true,
    "baholar": [
        85,
        90,
        78
    ]
}
```

- **`indent=4`** — har bir daraja 4 bo'sh joy bilan suriladi, natija o'qish oson bo'ladi
- **`ensure_ascii=False`** — o'zbek/rus harflari (masalan "Farg'ona", "Тошкент") to'g'ri, o'qiladigan holda chiqadi. Agar bu parametrni yozmasangiz, kirill/o'ziga xos harflar `\u0442\u043e...` kabi kodlarga aylanib ketadi!

### sort_keys — kalitlarni alifbo tartibida chiqarish

```python
print(json.dumps(talaba, indent=2, sort_keys=True))     # kalitlar alifbo bo'yicha tartiblanadi
```

## 2. loads() — JSON MATNINI Python obyektiga aylantirish

```python
import json

json_matni = '{"ism": "Vali", "yosh": 22, "faol": false}'
malumot = json.loads(json_matni)

print(malumot)              # {'ism': 'Vali', 'yosh': 22, 'faol': False}
print(type(malumot))         # <class 'dict'>
print(malumot["ism"])         # Vali
```

`loads()` — **"load string"** (matndan yuklash). `dumps()`ning teskarisi.

## 3. dump() — Python obyektini JSON FAYLGA yozish

```python
import json

talabalar = [
    {"ism": "Ali", "yosh": 20},
    {"ism": "Vali", "yosh": 22}
]

with open("talabalar.json", "w", encoding="utf-8") as fayl:
    json.dump(talabalar, fayl, indent=4, ensure_ascii=False)
```

Diqqat qiling — `dumps()` dan farqli, bu yerda `json.dump()` (oxirida `s` YO'Q) ishlatilyapti, va natija o'zgaruvchiga emas, to'g'ridan-to'g'ri **faylga** yoziladi.

## 4. load() — JSON FAYLDAN o'qish

```python
import json

with open("talabalar.json", "r", encoding="utf-8") as fayl:
    talabalar = json.load(fayl)

print(talabalar)
print(type(talabalar))     # <class 'list'>

for talaba in talabalar:
    print(talaba["ism"])
```

## Eslab qolish formulasi — 4 funksiya

| Funksiya | Yo'nalish | Ishlaydi |
|---|---|---|
| `json.dumps()` | Python → JSON **matn** | xotirada (o'zgaruvchi bilan) |
| `json.loads()` | JSON matn → Python | xotirada |
| `json.dump()` | Python → JSON **fayl** | fayl bilan (`open()` kerak) |
| `json.load()` | JSON fayl → Python | fayl bilan (`open()` kerak) |

**Eslab qolish uchun oddiy qoida:** oxirida **`s`** bo'lgan funksiyalar (`dumps`, `loads`) — **string** (matn) bilan ishlaydi. `s` harfisiz versiyasi — **fayl** bilan ishlaydi.

## Xatoliklarni boshqarish

JSON bilan ishlaganda ikkita eng ko'p uchraydigan xatolik bor:

```python
import json

# 1. Fayl mavjud emas
try:
    with open("mavjud_bolmagan.json", "r", encoding="utf-8") as fayl:
        malumot = json.load(fayl)
except FileNotFoundError:
    print("Fayl topilmadi, bo'sh ro'yxat bilan boshlaymiz")
    malumot = []

# 2. Fayl ichidagi matn JSON formatida emas (buzilgan)
try:
    malumot = json.loads("{ism: Ali}")     # noto'g'ri format — kalit qo'shtirnoqsiz
except json.JSONDecodeError as xatolik:
    print(f"JSON formatida xatolik: {xatolik}")
```

## Amaliy naqsh — "yuklash, o'zgartirish, saqlash"

Bu naqsh — ma'lumotlarni doimiy saqlaydigan har qanday dastur (jumladan Telegram botlar)ning yuragi hisoblanadi:

```python
import json

FAYL_NOMI = "talabalar.json"

def talabalarni_yuklash():
    try:
        with open(FAYL_NOMI, "r", encoding="utf-8") as fayl:
            return json.load(fayl)
    except FileNotFoundError:
        return []     # fayl hali mavjud bo'lmasa, bo'sh ro'yxat bilan boshlaymiz

def talabalarni_saqlash(talabalar):
    with open(FAYL_NOMI, "w", encoding="utf-8") as fayl:
        json.dump(talabalar, fayl, indent=4, ensure_ascii=False)

# ishlatish:
talabalar = talabalarni_yuklash()
talabalar.append({"ism": "Yangi Talaba", "yosh": 19})
talabalarni_saqlash(talabalar)
```

## OOP bilan JSON — klass obyektlarini saqlash

**Muhim eslatma:** `json` moduli faqat oddiy Python turlarini (dict, list, str, int, float, bool, None) to'g'ridan-to'g'ri tushunadi. O'z klassingizning obyektini bevosita `json.dump()`ga bersangiz — xatolik chiqadi:

```python
class Talaba:
    def __init__(self, ism, yosh):
        self.ism = ism
        self.yosh = yosh

talaba = Talaba("Ali", 20)
# json.dumps(talaba)     # XATOLIK! TypeError: Object of type Talaba is not JSON serializable
```

**Yechim** — avval obyektni dictionary'ga aylantirish:

```python
class Talaba:
    def __init__(self, ism, yosh):
        self.ism = ism
        self.yosh = yosh

    def dictga_aylantir(self):
        return {"ism": self.ism, "yosh": self.yosh}

    @classmethod
    def dictdan_yaratish(cls, malumot):
        return cls(malumot["ism"], malumot["yosh"])

talabalar = [Talaba("Ali", 20), Talaba("Vali", 22)]

# saqlash
malumotlar = [t.dictga_aylantir() for t in talabalar]
with open("talabalar.json", "w", encoding="utf-8") as fayl:
    json.dump(malumotlar, fayl, indent=4, ensure_ascii=False)

# qayta o'qish va obyektlarga aylantirish
with open("talabalar.json", "r", encoding="utf-8") as fayl:
    yuklangan = [Talaba.dictdan_yaratish(m) for m in json.load(fayl)]
```

## Amaliy misol — sozlamalarni saqlash

```python
import json

sozlamalar = {
    "til": "uz",
    "mavzu": "qorong'i",
    "bildirishnomalar": True,
    "shrift_hajmi": 14
}

with open("sozlamalar.json", "w", encoding="utf-8") as fayl:
    json.dump(sozlamalar, fayl, indent=4, ensure_ascii=False)

with open("sozlamalar.json", "r", encoding="utf-8") as fayl:
    yuklangan_sozlamalar = json.load(fayl)

print(yuklangan_sozlamalar["til"])     # uz
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. O'zingiz haqingizda dictionary yarating (ism, yosh, shahar) va uni `json.dumps()` bilan oddiy matn ko'rinishida chop eting.
2. Xuddi shu dictionary'ni `indent=4` va `ensure_ascii=False` parametrlari bilan chiroyli formatda chop eting.
3. `json.loads()` yordamida qo'lda yozilgan JSON matnni (`'{"a": 1, "b": 2}'`) Python dictionary'ga aylantiring.
4. O'zingiz haqingizdagi dictionary'ni `talabam.json` fayliga `json.dump()` bilan saqlang.
5. Yuqoridagi faylni `json.load()` bilan qayta o'qib, ekranga chiqaring.
6. `dumps()` va `dump()` farqini — birini o'zgaruvchiga, birini faylga yozib — solishtiring va izohlab yozing.
7. `sort_keys=True` parametrini sinab, kalitlar alifbo tartibida chiqishini tekshiring.
8. Ichida list (masalan sevimli ranglar) bo'lgan dictionary yarating va uni JSON formatida chop eting.

🟡 **O'rta (9-15)**

9. 5 ta mahsulotdan iborat list (har biri nom, narx, miqdor dictionary'si) yarating va uni JSON faylga saqlang.
10. Yuqoridagi faylni qayta o'qib, barcha mahsulotlarning umumiy qiymatini (narx × miqdor yig'indisi) hisoblang.
11. `FileNotFoundError`ni `try/except` bilan ushlab, agar JSON fayl mavjud bo'lmasa, bo'sh list bilan boshlaydigan "xavfsiz yuklash" funksiyasini yozing.
12. Mavjud JSON faylni o'qib, undagi ma'lumotlarni filtrlab (masalan narxi 100,000dan yuqori mahsulotlar), yangi JSON faylga yozing.
13. "Yuklash, o'zgartirish, saqlash" naqshidan foydalanib, foydalanuvchidan yangi talaba ma'lumotini so'rab, mavjud JSON faylga qo'shing.
14. Ichma-ich (nested) JSON struktura yarating — masalan bitta talaba ichida "baholar" nomli dictionary (fan nomi -> baho).
15. `json.JSONDecodeError` xatoligini qasddan (noto'g'ri formatdagi matn bilan) keltirib chiqarib, uni `try/except` bilan ushlang.

🔴 **Qiyin (16-20)**

16. `Kitob` klassidan (nomi, muallif, yil) bir nechta obyekt yarating, ularni `dictga_aylantir()` metodi orqali JSON faylga saqlang.
17. Yuqoridagi faylni qayta o'qib, har bir dictionary'dan `classmethod` yordamida yangidan `Kitob` obyektlarini tiklang.
18. Telegram bot uchun "foydalanuvchilar bazasi" simulyatsiyasi yasang — har bir foydalanuvchi `telegram_id` kaliti bilan JSON faylda saqlansin, yangi foydalanuvchi qo'shilganda avvalgilar o'chib ketmasligini ta'minlang.
19. Ikki xil JSON faylni (masalan "talabalar.json" va "baholar.json") o'qib, ularni umumiy "ism" maydoni orqali birlashtirib, yangi, to'liq JSON fayl yarating.
20. To'liq "sozlamalar boshqaruvchisi" klassini yozing — `SozlamalarBoshqaruvchi` klassi JSON faylni avtomatik yuklaydi (agar mavjud bo'lmasa, standart sozlamalar bilan yaratadi), `.olish(kalit)` va `.ozgartir(kalit, qiymat)` metodlariga ega bo'lib, har o'zgarishda avtomatik saqlaydi.

---

**Bog'liq mavzu:** [12 — Dictionary bilan tanishuv](./12_dictionary.md)
