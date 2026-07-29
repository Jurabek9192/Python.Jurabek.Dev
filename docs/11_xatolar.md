# 11 — XATOLAR BILAN ISHLASH

## "Dasturchi xato qiladi. Yaxshi dasturchi ko'p xato qiladi."

Xatolik — dasturlashning tabiiy qismi. Muhimi — xatolikni qanday boshqarishni bilish.

## try/except asoslari

```python
try:
    son = int(input("Son kiriting: "))
    print(100 / son)
except:
    print("Xatolik yuz berdi")
```

## Muayyan xatolik turlarini ushlash

```python
try:
    son = int(input("Son: "))
    print(100 / son)
except ValueError:
    print("Noto'g'ri son kiritildi")
except ZeroDivisionError:
    print("Nolga bo'lib bo'lmaydi")
```

## Keng tarqalgan xatoliklar

| Xatolik | Sabab |
|---|---|
| `ValueError` | Noto'g'ri qiymat (`int("abc")`) |
| `ZeroDivisionError` | Nolga bo'lish |
| `TypeError` | Mos kelmaydigan turlar |
| `IndexError` | Mavjud bo'lmagan indeks |
| `KeyError` | Mavjud bo'lmagan dictionary kaliti |
| `FileNotFoundError` | Fayl topilmadi |

## Xatolik xabarini olish

```python
try:
    son = int("abc")
except ValueError as xatolik:
    print(f"Xatolik: {xatolik}")
```

## finally — har doim bajariladi

```python
try:
    fayl = open("test.txt")
except FileNotFoundError:
    print("Fayl topilmadi")
finally:
    print("Tekshiruv yakunlandi")
```

## Xavfsiz kiritish funksiyasi

```python
def son_kiritish(xabar):
    while True:
        try:
            return int(input(xabar))
        except ValueError:
            print("Xato! Faqat son kiriting.")
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Foydalanuvchidan son so'rab, uni 10ga bo'ling — `ValueError` va `ZeroDivisionError` ni alohida ushlang.
2. Listdan foydalanuvchi kiritgan indeks bo'yicha element chiqaring, `IndexError` ni ushlang.
3. Dictionary'dan kalit bo'yicha qiymat oling, `KeyError` ni ushlang.
4. `try/except` bilan matnni songa aylantiring, xato bo'lsa tushunarli xabar chiqaring.
5. `as` orqali xatolik xabarini olib, uni chiqaring.
6. `finally` blokidan foydalanib, "Tekshiruv tugadi" degan xabar har doim chiqishini ta'minlang.
7. Mavjud bo'lmagan faylni ochishga urinib, `FileNotFoundError` ni ushlang.
8. Ikki sonni bo'luvchi dasturga xatolikni boshqarishni qo'shing.

🟡 **O'rta (9-15)**

9. Xavfsiz son kiritish funksiyasini yozing — foydalanuvchi to'g'ri son kiritmagunicha qayta so'raydigan.
10. Ikkita sonni bo'lishda barcha mumkin bo'lgan xatoliklarni (`ValueError`, `ZeroDivisionError`) alohida ushlab, har biriga aniq xabar bering.
11. Foydalanuvchidan yosh so'rang — manfiy son kiritilsa, o'zingiz `raise ValueError(...)` orqali xatolik chiqaring va uni `except` bilan ushlang.
12. Ro'yxatdan indeks bo'yicha element olishda, agar indeks noto'g'ri bo'lsa, foydalanuvchidan qaytadan so'rovchi (tsikl bilan) dastur yozing.
13. Mavjud bo'lmagan faylni qayta-qayta so'rab, mavjud fayl nomi kiritilguncha davom etuvchi dastur yozing.
14. `except Exception as e` yordamida barcha kutilmagan xatoliklarni ushlab, xabarini chiqaring.
15. Kalkulyator dasturiga (ikkita son va amal) barcha mumkin bo'lgan xatoliklarni (noto'g'ri son, nolga bo'lish, noto'g'ri amal belgisi) qo'shing.

🔴 **Qiyin (16-20)**

16. Bank tizimi simulyatori: pul yechishda agar summa balansdan katta bo'lsa, o'zingiz yaratgan xabar bilan `ValueError` chiqaring va uni ushlang.
17. JSON yoki CSV faylni o'qishga urinib (Kitob 2'dagi bilim bilan), fayl mavjud bo'lmasa yoki format xato bo'lsa, ikkalasini alohida ushlang.
18. Ichma-ich `try/except` yozing — tashqi blok fayl ochishni, ichki blok fayl ichidagi ma'lumotni songa aylantirishni tekshirsin.
19. Foydalanuvchidan matematik ifoda (masalan "5+3") kiritilib, uni `eval()` orqali hisoblovchi, lekin xato ifoda kiritilganda chiroyli xabar beruvchi dastur yozing (eslatma: `eval()` faqat ishonchli, o'z kiritilgan ma'lumot bilan ishlatiladi).
20. To'liq "xavfsiz kalkulyator" yarating — foydalanuvchi son yoki amal xato kiritsa, dastur to'xtamasdan, tushunarli xabar bilan qayta so'rasin (`while True` + `try/except` birgalikda).

---

**Oldingi mavzu:** [10 — Bir nechta shartlarni tekshirish](./10_murakkab_shartlar.md)
**Keyingi mavzu:** [12 — Dictionary bilan tanishuv](./12_dictionary.md)
