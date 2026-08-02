# FAYLLAR BILAN ISHLASH

## Nega fayllar bilan ishlashni bilish kerak?

Hozirgacha dasturimiz ishga tushganda yaratilgan barcha ma'lumot (o'zgaruvchilar, list, dictionary) dastur to'xtashi bilan **yo'qolib ketardi**. Fayllar bilan ishlash — ma'lumotni **doimiy (persistent)** saqlash, ya'ni dastur yopilgandan keyin ham "eslab qolish" imkonini beradi. Telegram botingiz foydalanuvchilarni "eslab qolishi", o'yiningiz "eng yaxshi natija"ni saqlashi — barchasi shu mavzuga asoslanadi.

## Fayl ochish — open() funksiyasi

```python
fayl = open("salom.txt", "r")     # "r" — o'qish rejimi (read)
matn = fayl.read()
print(matn)
fayl.close()          # faylni YOPISH — juda muhim, aks holda xotira "band" bo'lib qoladi
```

## Fayl rejimlari — to'liq jadval

| Rejim | Ma'nosi |
|---|---|
| `"r"` | O'qish (read) — standart, fayl mavjud bo'lishi shart |
| `"w"` | Yozish (write) — fayl mavjud bo'lsa, **butunlay tozalanadi**! Mavjud bo'lmasa, yaratiladi |
| `"a"` | Qo'shish (append) — mavjud matnning **oxiriga** yozadi, tozalamaydi |
| `"x"` | Yangi fayl yaratish — agar fayl **allaqachon mavjud bo'lsa, xatolik** beradi |
| `"r+"` | O'qish VA yozish (fayl mavjud bo'lishi shart) |
| `"rb"`, `"wb"` | Binary (rasm, video, PDF kabi matn bo'lmagan fayllar) rejimida o'qish/yozish |

```python
fayl = open("yangi.txt", "w")       # bo'sh fayl yaratadi (yoki mavjudini tozalaydi)
fayl = open("log.txt", "a")             # mavjud matnga qo'shib boradi
```

## `with` operatori — TAVSIYA ETILADIGAN usul

`open()`/`close()` qo'lda yozish xavfli — agar orada xatolik yuz bersa, `close()` chaqirilmay qolishi mumkin. `with` operatori faylni **avtomatik yopadi**, hatto xatolik yuz bersa ham:

```python
with open("salom.txt", "r", encoding="utf-8") as fayl:
    matn = fayl.read()
    print(matn)
# bu yerga kelganda, fayl ALLAQACHON avtomatik yopilgan bo'ladi
```

**Qoida:** Fayllar bilan ishlaganda har doim `with` ishlating — bu Python jamiyatida standart, professional amaliyot hisoblanadi. `encoding="utf-8"` — o'zbekcha/ruscha (Ў, Қ, Ғ, apostrof) harflar to'g'ri o'qilishi/yozilishi uchun deyarli har doim kerak.

## O'qish metodlari — to'liq

```python
with open("matn.txt", "r", encoding="utf-8") as fayl:
    hammasi = fayl.read()              # BUTUN faylni bitta katta matn (str) sifatida o'qiydi

with open("matn.txt", "r", encoding="utf-8") as fayl:
    birinchi_qator = fayl.readline()      # faqat BITTA qatorni o'qiydi
    ikkinchi_qator = fayl.readline()         # keyingi chaqiruvda KEYINGI qatorni o'qiydi

with open("matn.txt", "r", encoding="utf-8") as fayl:
    barcha_qatorlar = fayl.readlines()      # BARCHA qatorlarni list ko'rinishida qaytaradi
    print(barcha_qatorlar)                     # ['Birinchi qator\n', 'Ikkinchi qator\n', ...]
```

### Fayl bo'ylab to'g'ridan-to'g'ri `for` bilan aylanish — eng samarali usul

```python
with open("matn.txt", "r", encoding="utf-8") as fayl:
    for qator in fayl:                # katta fayllar uchun ENG XOTIRA-TEJAMKOR usul
        print(qator.strip())              # .strip() — qator oxiridagi "\n" (yangi qator) belgisini olib tashlaydi
```

**Nega bu usul afzal?** `read()` butun faylni bir vaqtda xotiraga yuklaydi — agar fayl gigabaytlab bo'lsa, dastur "qulashi" mumkin. `for qator in fayl:` esa faylni **qator-baqator**, xotirani tejagan holda o'qiydi (bu Kitob 3'dagi generator tushunchasiga o'xshaydi).

## Yozish metodlari

```python
with open("natija.txt", "w", encoding="utf-8") as fayl:
    fayl.write("Birinchi qator\n")          # \n — yangi qatorga o'tish, QO'LDA yozish kerak!
    fayl.write("Ikkinchi qator\n")

with open("natija.txt", "w", encoding="utf-8") as fayl:
    qatorlar = ["Birinchi\n", "Ikkinchi\n", "Uchinchi\n"]
    fayl.writelines(qatorlar)             # list'dagi barcha qatorlarni birdaniga yozadi
```

**Diqqat:** `write()` avtomatik yangi qatorga o'tmaydi — `print()`dan farqli, `\n` ni o'zingiz qo'shishingiz kerak.

## Qo'shish rejimi (append) — mavjud faylni tozalamasdan yozish

```python
with open("log.txt", "a", encoding="utf-8") as fayl:
    fayl.write("Yangi voqea qayd etildi\n")     # fayl oxiriga qo'shiladi, eskisi o'chmaydi
```

Bu — log fayllar (dastur ishlagan voqealar tarixi) uchun ideal, chunki har safar dastur ishga tushganda oldingi loglar o'chib ketmasligi kerak.

## Fayl mavjudligini tekshirish — os.path

```python
import os

if os.path.exists("malumot.txt"):
    print("Fayl mavjud")
else:
    print("Fayl topilmadi")

print(os.path.isfile("malumot.txt"))        # bu FAYLmi (papka emas)
print(os.path.isdir("papka"))                  # bu PAPKAmi
print(os.path.getsize("malumot.txt"))             # fayl hajmi (baytlarda)
```

## Zamonaviy imkoniyat — pathlib moduli

`os.path` o'rniga, zamonaviy Python kodida ko'pincha **pathlib** ishlatiladi — u obyektga yo'naltirilgan, o'qish osonroq sintaksisga ega:

```python
from pathlib import Path

fayl_yoli = Path("malumot.txt")

print(fayl_yoli.exists())          # fayl mavjudmi
print(fayl_yoli.name)                 # "malumot.txt" — fayl nomi
print(fayl_yoli.suffix)                  # ".txt" — kengaytmasi
print(fayl_yoli.stem)                       # "malumot" — kengaytmasiz nomi

matn = fayl_yoli.read_text(encoding="utf-8")           # to'g'ridan-to'g'ri o'qish, open() shart emas
fayl_yoli.write_text("Yangi matn", encoding="utf-8")      # to'g'ridan-to'g'ri yozish
```

## Xatoliklarni boshqarish — fayllar bilan (Kitob'dagi try/except bilan bog'liq)

```python
try:
    with open("mavjud_bolmagan.txt", "r", encoding="utf-8") as fayl:
        matn = fayl.read()
except FileNotFoundError:
    print("Xato: bunday fayl topilmadi")
except PermissionError:
    print("Xato: faylni ochishga ruxsat yo'q")
```

## Papka bilan ishlash

```python
import os

os.mkdir("yangi_papka")               # bitta papka yaratish (agar mavjud bo'lsa, xatolik beradi)
os.makedirs("papka1/papka2", exist_ok=True)     # ichma-ich papkalar, mavjud bo'lsa xato bermaydi

print(os.listdir("."))            # joriy papkadagi barcha fayl/papkalar ro'yxati
os.remove("kerak_emas.txt")           # faylni o'chirish
os.rmdir("bosh_papka")                   # BO'SH papkani o'chirish
```

## Amaliy misol — talabalar ro'yxatini faylga saqlash va o'qish

```python
def talabalarni_saqlash(talabalar, fayl_nomi="talabalar.txt"):
    with open(fayl_nomi, "w", encoding="utf-8") as fayl:
        for ism, baho in talabalar:
            fayl.write(f"{ism},{baho}\n")

def talabalarni_oqish(fayl_nomi="talabalar.txt"):
    talabalar = []
    try:
        with open(fayl_nomi, "r", encoding="utf-8") as fayl:
            for qator in fayl:
                ism, baho = qator.strip().split(",")
                talabalar.append((ism, int(baho)))
    except FileNotFoundError:
        pass     # fayl hali mavjud bo'lmasa, bo'sh ro'yxat qaytariladi
    return talabalar

talabalarni_saqlash([("Ali", 85), ("Vali", 90), ("Guli", 78)])
print(talabalarni_oqish())     # [('Ali', 85), ('Vali', 90), ('Guli', 78)]
```

## Amaliy misol — oddiy "kunlik" (log) yozuvchi

```python
from datetime import datetime

def logga_yoz(xabar, fayl_nomi="dastur.log"):
    vaqt = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    with open(fayl_nomi, "a", encoding="utf-8") as fayl:
        fayl.write(f"[{vaqt}] {xabar}\n")

logga_yoz("Dastur ishga tushdi")
logga_yoz("Foydalanuvchi tizimga kirdi")
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. `with open()` yordamida yangi `.txt` fayl yaratib, ichiga o'z ismingizni yozing.
2. Yuqoridagi faylni `"r"` rejimida ochib, `.read()` bilan o'qib chiqing.
3. Faylga (`"w"` rejimida) 3 qatorlik matn yozing, har birida `\n` ishlatishni unutmang.
4. Yuqoridagi faylni `.readlines()` bilan o'qib, natijani (list) chiqaring.
5. `"a"` rejimida faylga yana bitta qator qo'shing va faylni to'liq o'qib, eski matn saqlanganini tekshiring.
6. `for qator in fayl:` yordamida faylni qator-baqator o'qing va har birini `.strip()` bilan tozalab chop eting.
7. `os.path.exists()` yordamida fayl mavjudligini tekshiring.
8. Mavjud bo'lmagan faylni o'qishga urinib, `FileNotFoundError`ni `try/except` bilan ushlang.

🟡 **O'rta (9-15)**

9. 5 ta ism-yosh juftligini faylga (har biri vergul bilan ajratilgan holda) yozing.
10. Yuqoridagi faylni o'qib, har qatorni `.split(",")` bilan bo'lib, dictionary'lar ro'yxatiga aylantiring.
11. `pathlib.Path` yordamida fayl nomi, kengaytmasi va mavjudligini tekshiring.
12. `os.listdir()` yordamida joriy papkadagi barcha fayllarni ro'yxatga oling va faqat `.txt` fayllarni ajrating.
13. Oddiy "kunlik" (log) funksiyasini yozing — har chaqirilganda joriy vaqt bilan faylga yangi qator qo'shsin.
14. `readline()` yordamida faylning faqat birinchi 3 qatorini (uch marta chaqirib) o'qing.
15. `writelines()` yordamida list'dagi barcha elementlarni bitta faylga yozing.

🔴 **Qiyin (16-20)**

16. To'liq "talabalar bazasi" funksiyalarini yozing: `talaba_qoshish()`, `talabalarni_royxat()`, `talaba_ochirish()` — barchasi faylda saqlansin.
17. Ikki faylni (masalan `talabalar.txt` va `baholar.txt`) o'qib, ma'lumotlarini birlashtirib, uchinchi faylga yozing.
18. Faylni o'qib, undagi so'zlar sonini, qatorlar sonini va belgilar sonini hisoblovchi "matn statistikasi" dasturini yozing.
19. `os.makedirs()` yordamida ichma-ich papka tuzilmasi yarating va unga fayl saqlang, so'ng `pathlib` bilan shu faylni topib o'qing.
20. To'liq "eslatmalar (notes) dasturi" yozing — foydalanuvchi menyudan yangi eslatma qo'shishi, barcha eslatmalarni ko'rishi, muayyanini o'chirishi mumkin bo'lsin, barcha ma'lumot doimiy faylda saqlansin (dastur qayta ishga tushirilganda ham yo'qolmasin).

---

**Bog'liq mavzular:** [11 — Xatolar bilan ishlash](./11_xatolar.md) • [JSON bilan ishlash](./json_bilan_ishlash.md)
