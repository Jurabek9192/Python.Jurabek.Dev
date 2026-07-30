# 03 — O'ZGARUVCHILAR

## O'zgaruvchi nima?

**O'zgaruvchi** — xotirada ma'lumotni saqlash uchun nom beriladigan "quti". Texnik jihatdan, Python'da o'zgaruvchi aslida xotiradagi obyektga "yorliq (label)" bog'laydi — bu keyinroq listlar mavzusida muhim ahamiyat kasb etadi.

```python
ism = "Kamola"
yosh = 23
print(ism, yosh)
```

## Nomlash qoidalari (PEP8 standarti)

- Faqat harf, raqam va pastki chiziq (`_`) — raqamdan boshlanmaydi
- Katta-kichik harf farqlanadi
- Zaxira so'zlar (`print`, `if`, `for`, `class`...) ishlatilmaydi
- An'ana: `snake_case` (`mening_ismim`, `talaba_soni`) — o'zgaruvchi va funksiyalar uchun
- Doimiy qiymatlar (constants) uchun an'ana: `KATTA_HARFLAR` (masalan `PI = 3.14159`)

```python
yosh = 20                 # to'g'ri
talaba_soni = 30            # to'g'ri
MAX_BALL = 100                # doimiy qiymat konvensiyasi
# 1son = 5                  # XATO — raqamdan boshlangan
```

## Dinamik tiplash

Python'da o'zgaruvchi turi oldindan e'lon qilinmaydi va umr davomida o'zgarishi mumkin:

```python
narsa = 10          # int
print(type(narsa))    # <class 'int'>
narsa = "o'n"           # endi str
print(type(narsa))       # <class 'str'>
```

## Bir nechta o'zgaruvchini birga yaratish

```python
ism, yosh, shahar = "Ali", 20, "Namangan"      # unpacking
a = b = c = 0                                     # barchasiga bitta qiymat
```

## O'zgaruvchini qayta yozish va barcha qisqa operatorlar

```python
hisob = 100
hisob = hisob + 50        # 150 — to'liq yozuv
hisob += 50                 # 200 — qisqa yozuv (o'zi bilan bir xil)
hisob -= 20                   # 180
hisob *= 2                      # 360
hisob /= 3                        # 120.0
hisob //= 4                         # 30.0
hisob **= 2                           # 900.0
hisob %= 7                              # 4.0
```

## del — o'zgaruvchini o'chirish

```python
vaqtinchalik = "test"
del vaqtinchalik
# print(vaqtinchalik)     # XATOLIK! NameError — endi mavjud emas
```

## Ikki o'zgaruvchini almashtirish (swap)

```python
a, b = 5, 10
a, b = b, a          # Python'ga xos, juda qulay usul
print(a, b)             # 10 5
```

## isinstance() — turni tekshirish

```python
yosh = 25
print(isinstance(yosh, int))        # True
print(isinstance(yosh, (int, float)))  # True — bir nechta turni birga tekshirish
```

`isinstance()` — `type(x) == int` yozishdan ko'ra tavsiya etiladigan usul, chunki u meros (inheritance) bilan ham to'g'ri ishlaydi (Kitob 2'da chuqurroq o'rganiladi).

## O'zgaruvchi nomi — yaxshi amaliyot

```python
# yomon: nima ekanligi tushunarsiz
x = 25
y = "Ali"

# yaxshi: nomidan mazmuni ko'rinib turibdi
talaba_yoshi = 25
talaba_ismi = "Ali"
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. `ism`, `yosh`, `shahar` o'zgaruvchilarini yarating va bittalab chiqaring.
2. Ikkita songa o'zgaruvchi bering va ularning yig'indisini uchinchi o'zgaruvchida saqlab, chiqaring.
3. Bitta qatorda 3 ta o'zgaruvchi yarating (`a, b, c = 1, 2, 3`).
4. O'zgaruvchiga qiymat bering, so'ng uni qayta yozib (reassign), eski va yangi qiymatini chiqaring.
5. Barcha qisqa operatorlarni (`+=`, `-=`, `*=`, `/=`, `//=`, `**=`, `%=`) bitta o'zgaruvchida ketma-ket sinab ko'ring.
6. Ikki o'zgaruvchining qiymatini almashtiring (`a, b = b, a`).
7. O'zingizning to'liq ma'lumotingiz (ism, familiya, yosh, shahar, kasb) uchun 5 ta o'zgaruvchi yarating va chiroyli chiqaring.
8. `isinstance()` yordamida 3 ta turli o'zgaruvchining turini tekshiring.

🟡 **O'rta (9-15)**

9. To'rtburchakning eni va bo'yi uchun o'zgaruvchilar yarating, yuzasini hisoblab, natijani ham o'zgaruvchiga saqlang, so'ng chiqaring.
10. Bank balansi o'zgaruvchisini yarating (100000 dan boshlab), unga 3 marta turli summalar (`+=` bilan) qo'shing, oxirgi balansni chiqaring.
11. Uchta o'zgaruvchi (`a`, `b`, `c`) qiymatlarini bir-biriga aylantiring: a->b, b->c, c->a (vaqtinchalik o'zgaruvchisiz, bir qatorda).
12. Harorat Celsius'da o'zgaruvchiga saqlansin, uni Fahrenheit'ga aylantiruvchi yangi o'zgaruvchi yarating.
13. `del` yordamida vaqtinchalik o'zgaruvchini o'chirib, uni qayta chaqirishga urinib, chiqqan xatolikni ko'ring.
14. `narx` o'zgaruvchisini yarating, unga 15% chegirma qo'llang (`narx *= 0.85`) va yangi narxni chiqaring.
15. `MAX_BALL = 100` kabi katta harfli "doimiy qiymat" konvensiyasidan foydalanib, kamida 3 ta doimiy qiymat yarating.

🔴 **Qiyin (16-20)**

16. "Savat" tizimi: 3 ta mahsulot narxi uchun o'zgaruvchi yarating, ularning umumiy summasini hisoblang, so'ng 10% chegirma qo'llab yakuniy narxni chiqaring.
17. O'zgaruvchilar yordamida oddiy "counter" (hisoblagich) yasang — boshlang'ich qiymatdan boshlab, 5 marta turli miqdorda oshirib-pasaytirib, har safar joriy qiymatni chiqaring.
18. Uchta o'zgaruvchiga tasodifiy uch xil valyutadagi summalarni bering (USD, EUR, so'm), ularni bitta umumiy valyutaga (so'm) aylantirib, yig'indisini toping.
19. Ish haqi o'zgaruvchisini yarating, undan soliq (12%) va pensiya ushlab qolinishini hisoblang, sof summani chiqaring.
20. `isinstance()` va `type()` orasidagi farqni ko'rsatuvchi misol yozing — nima uchun `isinstance()` ko'proq tavsiya etilishini izohlang.

---

**Oldingi mavzu:** [02 — print(), sintaksis va arifmetik amallar](./02_print_sintaksis_arifmetik.md)
**Keyingi mavzu:** [04 — String (matn)](./04_string.md)
