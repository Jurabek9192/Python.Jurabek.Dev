# 24 — REGEX (MATN ANDOZALARI)

## RegEx nima?

**Regular Expression (regex)** — matn ichida muayyan naqsh (pattern)ni qidirish uchun ishlatiladigan maxsus til. Python'da `re` moduli orqali ishlatiladi.

```python
import re

matn = "Mening ismim Ali, telefon: 901234567"
natija = re.search(r"\d{9}", matn)
print(natija.group())     # 901234567
```

## Asosiy belgilar

| Belgi | Ma'nosi |
|---|---|
| `\d` | Raqam |
| `\w` | Harf/raqam/`_` |
| `\s` | Bo'sh joy |
| `.` | Istalgan belgi |
| `+` | 1 yoki ko'p marta |
| `*` | 0 yoki ko'p marta |
| `?` | 0 yoki 1 marta |
| `^` | Boshlanish |
| `$` | Tugash |
| `[abc]` | a, b yoki c |

## Asosiy funksiyalar

```python
re.search(naqsh, matn)      # birinchi mosni topadi
re.findall(naqsh, matn)       # barcha moslarni list qaytaradi
re.sub(naqsh, yangi, matn)      # almashtiradi
re.split(naqsh, matn)             # naqsh bo'yicha bo'ladi
```

## Amaliy misol — email tekshirish

```python
def email_togrimi(email):
    naqsh = r"^[\w.-]+@[\w.-]+\.\w+$"
    return bool(re.match(naqsh, email))

print(email_togrimi("ali@mail.com"))     # True
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Berilgan matndan barcha raqamlarni `findall()` bilan ajrating.
2. Matnda "salom" so'zi (katta-kichik harfsiz) borligini tekshiring.
3. Matndagi barcha bo'sh joylarni pastki chiziq bilan almashtiring.
4. Berilgan matnni bo'sh joy bo'yicha `re.split()` bilan bo'ling.
5. Matnda faqat harflardan iborat so'zlarni toping (`\w+`).
6. Berilgan matndan barcha 3 xonali sonlarni ajrating.
7. Matnda `@` belgisi borligini tekshiring (oddiy email tekshiruvi).
8. Berilgan matndagi barcha katta harf bilan boshlangan so'zlarni toping.

🟡 **O'rta (9-15)**

9. Email manzillarini matn ichidan `findall()` bilan barchasini ajrating.
10. O'zbekiston telefon raqamini (`+998` bilan boshlanadigan) tekshiruvchi funksiya yozing.
11. Berilgan matndan sana formatidagi (kun-oy-yil) yozuvlarni toping.
12. Parolni tekshiring — kamida 8 belgi, kamida 1 raqam borligini regex bilan tasdiqlang.
13. Matndagi barcha URL (http yoki https bilan boshlangan) manzillarni toping.
14. Berilgan matnni gaplarga (`.`, `!`, `?` bo'yicha) bo'ling.
15. Matn ichidagi barcha takrorlangan bo'sh joylarni (2 va undan ko'p probel) bitta probelga almashtiring.

🔴 **Qiyin (16-20)**

16. To'liq parol validatori: 8+ belgi, katta harf, kichik harf, raqam, maxsus belgi — barchasini alohida regex bilan tekshiring.
17. HTML matnidan barcha `<a href="...">` teglaridagi havolalarni ajrating.
18. Matn ichidan barcha IP manzillarni (masalan `192.168.1.1` formatida) toping.
19. Berilgan CSV qatoridagi (vergul bilan ajratilgan, lekin qiymat ichida vergul bo'lishi mumkin) qiymatlarni to'g'ri ajratuvchi regex yozing.
20. To'liq "matn tozalash" funksiyasini yozing — matndan barcha raqamlar, ortiqcha bo'sh joylar va maxsus belgilarni tozalab, faqat toza so'zlarni qoldiring.

---

**Oldingi mavzu:** [23 — "SO'Z TOPISH" o'yini](./23_soz_topish_oyini.md)
**Keyingi mavzu:** [25 — Python'ning eng so'nggi imkoniyatlari](./25_yangi_imkoniyatlar.md)
