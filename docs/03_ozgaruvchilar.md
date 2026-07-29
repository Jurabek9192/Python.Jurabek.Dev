# 03 — O'ZGARUVCHILAR

## O'zgaruvchi nima?

**O'zgaruvchi** — xotirada ma'lumotni saqlash uchun nom beriladigan "quti". Har safar bu nom ishlatilganda, Python xotiradagi tegishli ma'lumotni topib beradi.

```python
ism = "Kamola"
yosh = 23
print(ism)
print(yosh)
```

## Nomlash qoidalari

- Faqat harf, raqam va pastki chiziq (`_`) — raqamdan boshlanmaydi
- Katta-kichik harf farqlanadi
- Zaxira so'zlar (`print`, `if`, `for`...) ishlatilmaydi
- An'ana: `snake_case` (`mening_ismim`, `talaba_soni`)

```python
yosh = 20                 # to'g'ri
talaba_soni = 30            # to'g'ri
# 1son = 5                  # XATO — raqamdan boshlangan
```

## Dinamik tiplash

Python'da o'zgaruvchi turi oldindan e'lon qilinmaydi va umr davomida o'zgarishi mumkin:

```python
narsa = 10          # int
narsa = "o'n"         # endi str
narsa = 10.5           # endi float
```

## Bir nechta o'zgaruvchini birga yaratish

```python
ism, yosh, shahar = "Ali", 20, "Namangan"
a = b = c = 0          # barchasiga bitta qiymat
```

## O'zgaruvchini qayta yozish (reassignment)

```python
hisob = 100
hisob = hisob + 50        # 150
hisob += 50                 # 200 — qisqa yozuv
```

Qisqa operatorlar: `+=`, `-=`, `*=`, `/=`, `//=`, `**=`, `%=`

## O'zgaruvchi nomi — yaxshi amaliyot

```python
# yomon: nima ekanligi tushunarsiz
x = 25
y = "Ali"

# yaxshi: nomidan mazmuni ko'rinib turibdi
talaba_yoshi = 25
talaba_ismi = "Ali"
```

Kod boshqalar (va kelajakdagi o'zingiz) uchun tushunarli bo'lishi uchun, o'zgaruvchilarga **mazmunli** nom bering.

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. `ism`, `yosh`, `shahar` o'zgaruvchilarini yarating va bittalab chiqaring.
2. Ikkita songa o'zgaruvchi bering va ularning yig'indisini uchinchi o'zgaruvchida saqlab, chiqaring.
3. Bitta qatorda 3 ta o'zgaruvchi yarating (`a, b, c = 1, 2, 3`).
4. O'zgaruvchiga qiymat bering, so'ng uni qayta yozib (reassign), eski va yangi qiymatini chiqaring.
5. `+=` operatoridan foydalanib, hisoblagichni 1 dan 5 gacha qo'lda (5 marta yozib) oshiring.
6. Ikki o'zgaruvchining qiymatini almashtiring (`a, b = b, a`).
7. O'zingizning to'liq ma'lumotingiz (ism, familiya, yosh, shahar, kasb) uchun 5 ta o'zgaruvchi yarating va chiroyli chiqaring.
8. Bitta o'zgaruvchiga ketma-ket 3 xil turdagi (int, str, float) qiymat bering, har safar `print()` bilan tekshiring.

🟡 **O'rta (9-15)**

9. To'rtburchakning eni va bo'yi uchun o'zgaruvchilar yarating, yuzasini hisoblab, natijani ham o'zgaruvchiga saqlang, so'ng chiqaring.
10. Bank balansi o'zgaruvchisini yarating (100000 dan boshlab), unga 3 marta turli summalar (`+=` bilan) qo'shing, oxirgi balansni chiqaring.
11. Uchta o'zgaruvchi (`a`, `b`, `c`) qiymatlarini bir-biriga aylantiring: a->b, b->c, c->a (vaqtinchalik o'zgaruvchisiz, bir qatorda).
12. Harorat Celsius'da o'zgaruvchiga saqlansin, uni Fahrenheit'ga aylantiruvchi yangi o'zgaruvchi yarating (`C * 9/5 + 32`).
13. O'zgaruvchilar nomlash xatosini (masalan raqamdan boshlangan nom) qasddan yozing, xatolikni ko'ring va tuzating.
14. `narx` o'zgaruvchisini yarating, unga 15% chegirma qo'llang (`narx *= 0.85`) va yangi narxni chiqaring.
15. Uchta fan bahosi uchun o'zgaruvchi yarating va ularning o'rtachasini to'rtinchi o'zgaruvchida hisoblang.

🔴 **Qiyin (16-20)**

16. "Savat" tizimi: 3 ta mahsulot narxi uchun o'zgaruvchi yarating, ularning umumiy summasini hisoblang, so'ng 10% chegirma qo'llab yakuniy narxni chiqaring.
17. O'zgaruvchilar yordamida oddiy "counter" (hisoblagich) yasang — boshlang'ich qiymatdan boshlab, 5 marta turli miqdorda oshirib-pasaytirib, har safar joriy qiymatni chiqaring.
18. Uchta o'zgaruvchiga tasodifiy(o'zingiz o'ylab topgan) uch xil valyutadagi summalarni bering (USD, EUR, so'm), ularni bitta umumiy valyutaga (so'm) aylantirib, yig'indisini toping.
19. Ish haqi o'zgaruvchisini yarating, undan soliq (12%) va pensiya ushlab qolinishini (undan keyin yana bir necha foiz) hisoblang, sof (qo'lga tegadigan) summani chiqaring.
20. O'zingizning shaxsiy "profil" ma'lumotlaringiz (kamida 6 ta o'zgaruvchi: ism, familiya, yosh, shahar, kasb, maosh) asosida, chiroyli formatlangan (chiziqlar bilan ajratilgan) profil kartochka chiqaring.

---

**Oldingi mavzu:** [02 — print(), sintaksis va arifmetik amallar](./02_print_sintaksis_arifmetik.md)
**Keyingi mavzu:** [04 — String (matn)](./04_string.md)
