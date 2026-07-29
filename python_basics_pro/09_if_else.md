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

## Mantiqiy operatorlar: and, or, not

```python
yosh = 25
maosh = 3000000

if yosh >= 18 and maosh >= 2000000:
    print("Kredit uchun mos")

if yosh < 18 or maosh < 1000000:
    print("Shartlarga javob bermaydi")
```

## Ternary (bir qatorli if/else)

```python
yosh = 20
holat = "katta" if yosh >= 18 else "kichik"
print(holat)
```

## Truthy va Falsy qiymatlar

```python
if []:            # bo'sh list -> False
    print("ishlamaydi")
if [1, 2]:          # bo'sh bo'lmagan -> True
    print("ishlaydi")
```

## Zamonaviy imkoniyat — match-case (Python 3.10+)

Ko'p `elif` zanjiri o'rniga, Python 3.10 dan boshlab `match-case` (boshqa tillardagi `switch`ga o'xshash) ishlatilishi mumkin:

```python
kun = "Dushanba"

match kun:
    case "Dushanba" | "Seshanba" | "Chorshanba" | "Payshanba" | "Juma":
        print("Ish kuni")
    case "Shanba" | "Yakshanba":
        print("Dam olish kuni")
    case _:
        print("Noma'lum kun")
```

`case _:` — "boshqa hech biriga mos kelmasa" degani (default holat).

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Foydalanuvchidan yosh so'rab, 18 dan katta yoki kichikligini aniqlang.
2. Sonning musbat, manfiy yoki nolga tengligini aniqlang (`elif`).
3. Sonning juft yoki toqligini aniqlang.
4. Bahoni (0-100) harf bahoga (A/B/C/D/F) aylantiring.
5. Uch sonning eng kattasini `if/elif/else` bilan toping.
6. Ternary operator yordamida sonning musbat/manfiyligini bitta qatorda aniqlang.
7. Foydalanuvchidan parol so'rab, u "12345" ga teng yoki emasligini tekshiring.
8. `and` operatoridan foydalanib, son 10 dan 20 gacha oraliqda ekanligini tekshiring.

🟡 **O'rta (9-15)**

9. Yilni kiritib, uning kabisa yili ekanligini tekshiring (4ga bo'linadi, 100ga bo'linmaydi, YOKI 400ga bo'linadi).
10. Uchburchakning uchta tomoni berilgan — haqiqiy uchburchak yasash mumkinligini tekshiring.
11. Taksi narxini hisoblang: boshlang'ich 5000 so'm + har km uchun 1500 so'm, agar masofa 10km dan oshsa 10% chegirma.
12. `match-case` yordamida foydalanuvchi kiritgan raqamga (1-7) qarab hafta kunini chiqaring.
13. Login va parolni tekshiruvchi tizim yozing — ikkalasi ham to'g'ri bo'lsagina "Xush kelibsiz" chiqsin.
14. Uchta o'zgaruvchidan (yomg'ir bor-yo'qligi, harorat, shamol) qarab, kiyim kiyish tavsiyasi bering.
15. Foydalanuvchi kiritgan uchta sondan qaysi biri eng katta, eng kichik va o'rtachasini aniqlang.

🔴 **Qiyin (16-20)**

16. Oddiy parol kuchini tekshiruvchi dastur yozing: kamida 8 belgi, kamida 1 katta harf, 1 kichik harf, 1 raqam bo'lishi kerak — har bir shartni alohida tekshirib, aniq qaysi shart bajarilmaganini ayting.
17. BMI (tana massasi indeksi) hisoblab, natijaga qarab "kam vazn/normal/ortiqcha vazn/semizlik" toifasini aniqlang.
18. Oddiy kalkulyator: foydalanuvchi ikkita son va amal belgisini (+,-,*,/) kiritadi, `match-case` yordamida mos amal bajariladi.
19. Uch xonali sonni kiritib, uning palindrom (masalan 121) ekanligini tekshiring.
20. Оddiy "svetofor" simulyatori — foydalanuvchi rangni kiritadi (qizil/sariq/yashil), tegishli harakatni ("to'xtang"/"tayyorlaning"/"yuring") chiqaring, boshqa rang kiritilsa xatolik xabarini bering.

---

**Oldingi mavzu:** [08 — For takrorlash operatori](./08_for_loop.md)
**Keyingi mavzu:** [10 — Bir nechta shartlarni tekshirish](./10_murakkab_shartlar.md)
