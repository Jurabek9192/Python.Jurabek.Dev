# 24 — REGEX (MATN ANDOZALARI)

## RegEx nima?

**Regular Expression (regex)** — matn ichida muayyan naqsh (pattern)ni qidirish uchun ishlatiladigan maxsus til. Python'da `re` moduli orqali ishlatiladi.

```python
import re

matn = "Mening ismim Ali, telefon: 901234567"
natija = re.search(r"\d{9}", matn)
print(natija.group())     # 901234567
```

## Asosiy belgilar — to'liq jadval

| Belgi | Ma'nosi |
|---|---|
| `\d` | Raqam (0-9) |
| `\D` | Raqam bo'lmagan belgi |
| `\w` | Harf/raqam/`_` |
| `\W` | Harf/raqam/`_` bo'lmagan belgi |
| `\s` | Bo'sh joy (probel, tab, yangi qator) |
| `\S` | Bo'sh joy bo'lmagan belgi |
| `.` | Istalgan bitta belgi (yangi qatordan tashqari) |
| `^` | Matn boshlanishi |
| `$` | Matn tugashi |
| `+` | 1 yoki ko'p marta |
| `*` | 0 yoki ko'p marta |
| `?` | 0 yoki 1 marta |
| `{n}` | Aniq n marta |
| `{n,m}` | n dan m gacha marta |
| `[abc]` | a, b yoki c dan biri |
| `[^abc]` | a, b, c DAN BOSHQA istalgan belgi |
| `[a-z]` | a dan z gacha istalgan harf |
| `\|` | YOKI (bir nechta variant) |
| `()` | Guruhlash |

## Asosiy funksiyalar — barchasi

```python
import re

matn = "Telefon: 901234567, ikkinchisi: 907654321"

re.search(naqsh, matn)        # BIRINCHI mosni topadi (istalgan joyda)
re.match(naqsh, matn)            # faqat matn BOSHIDAN mos kelsa topadi
re.fullmatch(naqsh, matn)           # BUTUN matn naqshga to'liq mos kelishi kerak
re.findall(naqsh, matn)                # BARCHA moslarni list qaytaradi
re.finditer(naqsh, matn)                  # barcha moslarni "iterator" sifatida (Match obyektlar bilan)
re.sub(naqsh, yangi, matn)                   # almashtiradi
re.sub(naqsh, yangi, matn, count=1)             # faqat birinchi marta almashtiradi
re.split(naqsh, matn)                              # naqsh bo'yicha bo'ladi

print(re.findall(r"\d{9}", matn))     # ['901234567', '907654321']
```

## Match obyekti — group(), start(), end()

```python
natija = re.search(r"\d{9}", matn)
if natija:
    print(natija.group())       # 901234567 — mos kelgan matn
    print(natija.start())          # boshlanish indeksi
    print(natija.end())               # tugash indeksi
```

## Guruhlash — qism-mosni ajratib olish

```python
matn = "Sana: 28-07-2026"
natija = re.search(r"(\d{2})-(\d{2})-(\d{4})", matn)

if natija:
    print(natija.group())      # 28-07-2026 (butun mos)
    print(natija.group(1))       # 28 (kun)
    print(natija.group(2))         # 07 (oy)
    print(natija.group(3))           # 2026 (yil)
    print(natija.groups())              # ('28', '07', '2026') — barchasi tuple sifatida
```

## Nomlangan guruhlar (named groups)

```python
natija = re.search(r"(?P<kun>\d{2})-(?P<oy>\d{2})-(?P<yil>\d{4})", matn)
print(natija.group("kun"))     # 28 — nom orqali murojaat, indeks emas
```

## re.IGNORECASE — katta-kichik harfga qaramasdan qidirish

```python
matn = "Salom, SALOM, salom!"
print(re.findall(r"salom", matn, re.IGNORECASE))     # ['Salom', 'SALOM', 'salom']
```

## Naqshni oldindan "kompilyatsiya" qilish (tezlik uchun)

Agar bir xil naqsh ko'p marta ishlatilsa, uni oldindan kompilyatsiya qilish tezroq ishlaydi:

```python
naqsh = re.compile(r"\d{9}")
print(naqsh.findall(matn))
print(naqsh.search(matn))
```

## Amaliy misol — email tekshirish

```python
def email_togrimi(email):
    naqsh = r"^[\w.-]+@[\w.-]+\.\w+$"
    return bool(re.match(naqsh, email))

print(email_togrimi("ali@mail.com"))      # True
print(email_togrimi("notogri-email"))       # False
```

## Amaliy misol — O'zbekiston telefon raqami

```python
def telefon_togrimi(raqam):
    naqsh = r"^\+998\d{9}$"
    return bool(re.match(naqsh, raqam))

print(telefon_togrimi("+998901234567"))     # True
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Berilgan matndan barcha raqamlarni `findall()` bilan ajrating.
2. `re.IGNORECASE` yordamida matnda "salom" so'zi (katta-kichik harfsiz) borligini tekshiring.
3. Matndagi barcha bo'sh joylarni pastki chiziq bilan almashtiring (`re.sub()`).
4. Berilgan matnni bo'sh joy bo'yicha `re.split()` bilan bo'ling.
5. Matnda faqat harflardan iborat so'zlarni toping (`\w+`).
6. Berilgan matndan barcha 3 xonali sonlarni toping.
7. `re.match()` va `re.search()` farqini bitta misolda solishtiring (matn o'rtasida joylashgan naqsh bilan).
8. Berilgan matndagi barcha katta harf bilan boshlangan so'zlarni toping.

🟡 **O'rta (9-15)**

9. Email manzillarini matn ichidan `findall()` bilan barchasini ajrating.
10. O'zbekiston telefon raqamini (`+998` bilan boshlanadigan) tekshiruvchi funksiya yozing.
11. Guruhlash (`()`) yordamida sanani kun/oy/yilga ajratib, `.group(1)`, `.group(2)`, `.group(3)` bilan chiqaring.
12. Nomlangan guruhlardan (`?P<nom>`) foydalanib, xuddi shu sanani nom orqali ajrating.
13. Parolni tekshiring — kamida 8 belgi, kamida 1 raqam borligini regex bilan tasdiqlang.
14. Matndagi barcha URL (http yoki https bilan boshlangan) manzillarni toping.
15. `re.compile()` yordamida naqshni oldindan tayyorlab, bir nechta matn ustida qayta ishlating.

🔴 **Qiyin (16-20)**

16. To'liq parol validatori: 8+ belgi, katta harf, kichik harf, raqam, maxsus belgi — barchasini alohida regex bilan tekshiring.
17. HTML matnidan barcha `<a href="...">` teglaridagi havolalarni ajrating.
18. Matn ichidan barcha IP manzillarni (masalan `192.168.1.1` formatida) toping.
19. `finditer()` yordamida matndagi barcha moslarning aniq boshlanish va tugash indekslarini chiqaring.
20. To'liq "matn tozalash" funksiyasini yozing — matndan barcha raqamlar, ortiqcha bo'sh joylar va maxsus belgilarni tozalab, faqat toza so'zlarni qoldiring.

---

**Oldingi mavzu:** [23 — "SO'Z TOPISH" o'yini](./23_soz_topish_oyini.md)
**Keyingi mavzu:** [25 — Python'ning eng so'nggi imkoniyatlari](./25_yangi_imkoniyatlar.md)
