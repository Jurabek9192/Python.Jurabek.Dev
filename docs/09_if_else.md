# 09 — IF-ELSE

## Oddiy if

```python
yosh = 20
if yosh >= 18:
    print("Siz kattasiz")
```

## if / else

```python
yosh = 15
if yosh >= 18:
    print("Kattasiz")
else:
    print("Voyaga yetmagansiz")
```

## if / elif / else

```python
baho = 75
if baho >= 90:
    print("A'lo")
elif baho >= 70:
    print("Yaxshi")
elif baho >= 50:
    print("Qoniqarli")
else:
    print("Qoniqarsiz")
```

## Solishtirish operatorlari — to'liq jadval

| Operator | Ma'nosi |
|---|---|
| `==` | Teng |
| `!=` | Teng emas |
| `>` | Katta |
| `<` | Kichik |
| `>=` | Katta yoki teng |
| `<=` | Kichik yoki teng |
| `is` | Bir xil obyektmi (xotirada) |
| `is not` | Boshqa obyektmi |

```python
a = [1, 2, 3]
b = [1, 2, 3]
c = a

print(a == b)     # True — qiymatlari bir xil
print(a is b)       # False — bular xotirada IKKI XIL obyekt
print(a is c)          # True — c aynan a ning o'ziga ishora qiladi
```

## Mantiqiy operatorlar: and, or, not

```python
yosh = 25
maosh = 3000000

if yosh >= 18 and maosh >= 2000000:
    print("Kredit uchun mos")

if yosh < 18 or maosh < 1000000:
    print("Shartlarga javob bermaydi")

if not (yosh < 18):
    print("Kattasiz")
```

## Ternary (bir qatorli if/else)

```python
yosh = 20
holat = "katta" if yosh >= 18 else "kichik"
print(holat)

# ichma-ich ternary (ehtiyot bilan, murakkab bo'lsa oddiy if/else yaxshiroq)
baho = 85
daraja = "A'lo" if baho >= 90 else "Yaxshi" if baho >= 70 else "Past"
```

## Truthy va Falsy qiymatlar — to'liq ro'yxat

**Falsy** (False deb hisoblanadi): `0`, `0.0`, `""` (bo'sh string), `[]`, `{}`, `()`, `set()`, `None`, `False`

```python
if []:            # bo'sh list -> False
    print("ishlamaydi")
if [1, 2]:          # bo'sh bo'lmagan -> True
    print("ishlaydi")
if "":                # bo'sh string -> False
    print("ishlamaydi")
if 0:                    # nol -> False
    print("ishlamaydi")

# amaliy foydalanish
royxat = [1, 2, 3]
if royxat:                # len(royxat) > 0 o'rniga — qisqa va Pythonic
    print("Ro'yxat bo'sh emas")
```

## Zamonaviy imkoniyat — match-case (Python 3.10+)

```python
kun = "Dushanba"

match kun:
    case "Dushanba" | "Seshanba" | "Chorshanba" | "Payshanba" | "Juma":
        print("Ish kuni")
    case "Shanba" | "Yakshanba":
        print("Dam olish kuni")
    case _:
        print("Noma'lum kun")

# tuple destructuring bilan
buyruq = ("harakat", "yur", 5)
match buyruq:
    case ("harakat", "yur", masofa):
        print(f"{masofa} qadam yurish")
    case ("harakat", turi, _):
        print(f"Noma'lum harakat: {turi}")
```

## if — bir qatorda (oddiy holatlar uchun)

```python
yosh = 20
if yosh >= 18: print("Katta")     # ishlaydi, lekin ko'p qatorli koddan ko'ra kamroq tavsiya etiladi
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Foydalanuvchidan yosh so'rab, 18 dan katta yoki kichikligini aniqlang.
2. Sonning musbat, manfiy yoki nolga tengligini aniqlang (`elif`).
3. Sonning juft yoki toqligini aniqlang.
4. Bahoni (0-100) harf bahoga (A/B/C/D/F) aylantiring.
5. Uch sonning eng kattasini `if/elif/else` bilan toping.
6. Ternary operator yordamida sonning musbat/manfiyligini bitta qatorda aniqlang.
7. `is` va `==` operatorlari orasidagi farqni ikkita bir xil qiymatli, lekin har xil obyektli list bilan sinab ko'ring.
8. `and` operatoridan foydalanib, son 10 dan 20 gacha oraliqda ekanligini tekshiring.

🟡 **O'rta (9-15)**

9. Yilni kiritib, uning kabisa yili ekanligini tekshiring.
10. Uchburchakning uchta tomoni berilgan — haqiqiy uchburchak yasash mumkinligini tekshiring.
11. Taksi narxini hisoblang: boshlang'ich 5000 so'm + har km uchun 1500 so'm, agar masofa 10km dan oshsa 10% chegirma.
12. `match-case` yordamida foydalanuvchi kiritgan raqamga (1-7) qarab hafta kunini chiqaring.
13. Login va parolni tekshiruvchi tizim yozing — ikkalasi ham to'g'ri bo'lsagina "Xush kelibsiz" chiqsin.
14. Truthy/Falsy tushunchasidan foydalanib, bo'sh listni to'g'ridan-to'g'ri `if royxat:` bilan tekshiruvchi kod yozing.
15. Foydalanuvchi kiritgan uchta sondan qaysi biri eng katta, eng kichik va o'rtachasini aniqlang.

🔴 **Qiyin (16-20)**

16. Oddiy parol kuchini tekshiruvchi dastur yozing: kamida 8 belgi, kamida 1 katta harf, 1 kichik harf, 1 raqam bo'lishi kerak.
17. BMI hisoblab, natijaga qarab toifasini aniqlang.
18. `match-case` yordamida oddiy kalkulyator yozing — foydalanuvchi ikkita son va amal belgisini kiritadi.
19. Uch xonali sonni kiritib, uning palindrom ekanligini tekshiring.
20. `match-case` bilan tuple destructuring ishlatib, oddiy "buyruq tahlilchisi" yozing (masalan `("harakat", "yur", 5)` yoki `("harakat", "burил", 90)`).

---

**Oldingi mavzu:** [08 — For takrorlash operatori](./08_for_loop.md)
**Keyingi mavzu:** [10 — Bir nechta shartlarni tekshirish](./10_murakkab_shartlar.md)
