# 10 — BIR NECHTA SHARTLARNI TEKSHIRISH

## and, or, not — chuqurroq

```python
yosh = 25
maosh = 4000000
tajriba = 3

if yosh >= 18 and maosh >= 2000000 and tajriba >= 1:
    print("Kredit uchun to'liq mos")
```

## Qisqa tutashuv (short-circuit)

```python
royxat = []
if len(royxat) > 0 and royxat[0] == "olma":    # birinchi False bo'lsa, ikkinchisi tekshirilmaydi
    print("Bor")
else:
    print("Bo'sh yoki mos emas")
```

## Zanjirlangan solishtirish

```python
yosh = 25
if 18 <= yosh <= 65:      # matematik yozuvga o'xshash, Python'ga xos
    print("Ish yoshidagi odam")
```

## all() va any()

```python
baholar = [85, 90, 78, 92]
print(all(b >= 60 for b in baholar))    # True — hammasi 60dan yuqorimi
print(any(b >= 95 for b in baholar))     # False — kamida bittasi 95dan yuqorimi
```

## in va not in — shart sifatida

```python
kunlar = ["Dushanba", "Chorshanba", "Juma"]
bugun = "Chorshanba"
if bugun in kunlar:
    print("Bugun mashg'ulot bor")
```

## Ichma-ich shartlar vs and bilan soddalashtirish

```python
yosh = 20
guvohnoma = True

# ichma-ich (murakkabroq)
if yosh >= 18:
    if guvohnoma:
        print("Haydash mumkin")

# and bilan (soddaroq, tavsiya etiladi)
if yosh >= 18 and guvohnoma:
    print("Haydash mumkin")
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Yosh va fuqarolikni tekshirib, ikkalasi ham mos bo'lsa "Ovoz berish huquqi bor" deb chiqaring.
2. Zanjirlangan solishtirish (`10 <= x <= 20`) yordamida son oraliqda ekanligini tekshiring.
3. `all()` yordamida ro'yxatdagi barcha sonlar musbat ekanligini tekshiring.
4. `any()` yordamida ro'yxatda kamida bitta juft son borligini tekshiring.
5. `in` operatoridan foydalanib, kiritilgan kun "dam olish kuni" ro'yxatida borligini tekshiring.
6. Ikki shartni `or` bilan birlashtirib, harorat juda issiq YOKI juda sovuq ekanligini tekshiring.
7. Uch shartni (`and` bilan) birlashtirib, "malakali nomzod" mezonini tekshiring (yosh, tajriba, ta'lim).
8. `not` operatoridan foydalanib, sonning musbat emasligini tekshiring.

🟡 **O'rta (9-15)**

9. Kiyim tanlash tizimi: harorat va yomg'ir borligiga qarab tavsiya bering (ikkita shartni birlashtirib).
10. Uchta mezondan (yosh, maosh, staj) kamida ikkitasi bajarilsa "qisman mos" deb chiqaring (`sum()` va bool qiymatlar yig'indisidan foydalaning).
11. Parol kuchini tekshirish — barcha shartlarni alohida bool o'zgaruvchida saqlab, `all()` orqali tekshiring.
12. Talabalar ro'yxatidagi barcha baholar 60dan yuqori ekanligini `all()` bilan tekshiring, agar yo'q bo'lsa qaysi talaba past ekanligini toping.
13. Kirish nazorati: foydalanuvchi tizimga kirgan va (admin YOKI moderator) bo'lsa, boshqaruv paneliga ruxsat bering.
14. De Morgan qonunidan foydalanib (`not (A and B) == (not A) or (not B)`), bir xil natija beruvchi ikki xil shart yozing.
15. `in` va `not in` dan foydalanib, kiritilgan so'z taqiqlangan so'zlar ro'yxatida bor-yo'qligini tekshiring.

🔴 **Qiyin (16-20)**

16. Murakkab kredit tekshiruvi: yosh (21-60), maosh (3+ mln), kredit tarixi (bool) — barchasi bajarilsa "tasdiqlandi", aks holda qaysi shart(lar) bajarilmaganini alohida ayting.
17. `all()` va list comprehension'ni birlashtirib, ro'yxatdagi barcha so'zlar 3 harfdan uzun ekanligini tekshiring.
18. Ish vaqti tizimi: agar tizimga kirgan, roli mos VA ish vaqti (9-18) oralig'ida bo'lsa — "to'liq ruxsat", aks holda "faqat ko'rish" yoki "kirish yo'q" holatlarini ajrating (ichma-ich shartlar bilan).
19. Uchta talabaning uchtadan bahosi berilgan (9 ta son) — `all()` yordamida barcha talabalar barcha fanlardan o'tganligini (60+) tekshiring.
20. "Murakkab parol siyosati" — parol uzunligi, katta/kichik harf, raqam, maxsus belgi (`!@#$`) borligini alohida-alohida tekshirib, foydalanuvchiga aniq qaysi talablar bajarilmaganini ro'yxat qilib bering.

---

**Oldingi mavzu:** [09 — IF-ELSE](./09_if_else.md)
**Keyingi mavzu:** [11 — Xatolar bilan ishlash](./11_xatolar.md)
