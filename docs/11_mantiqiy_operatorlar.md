# MANTIQIY OPERATORLAR VA MURAKKAB SHARTLAR

## Takrorlash: and, or, not

Oldingi mavzuda `and`, `or`, `not` operatorlari bilan tanishgan edik. Bu mavzuda ularni chuqurroq, murakkabroq holatlarda qanday ishlashini ko'ramiz.

## Haqiqat jadvali (Truth Table)

| A | B | A and B | A or B |
|---|---|---|---|
| True | True | True | True |
| True | False | False | True |
| False | True | False | True |
| False | False | False | False |

```python
print(True and True)    # True
print(True and False)   # False
print(False or True)    # True
print(False or False)   # False
print(not True)          # False
```

## Qisqa tutashuv (Short-circuit evaluation)

Python `and`/`or` operatorlarini "aqlli" tarzda baholaydi — agar natija birinchi qismdanoq aniq bo'lsa, ikkinchisini tekshirmaydi:

```python
# and: birinchi False bo'lsa, ikkinchisi tekshirilmaydi
def tekshir():
    print("tekshirildi")
    return True

print(False and tekshir())   # False — "tekshirildi" chop etilmaydi!
print(True or tekshir())      # True — "tekshirildi" chop etilmaydi!
```

Bu nafaqat tezlik uchun, balki xatoликларнинг oldini olish uchun ham foydali:

```python
royxat = []

if len(royxat) > 0 and royxat[0] == "olma":
    print("Birinchi element olma")
else:
    print("Ro'yxat bo'sh yoki birinchi element olma emas")
```

Agar `and` o'rniga tartib teskari bo'lganida (`royxat[0] == "olma" and len(royxat) > 0`), bo'sh list uchun `royxat[0]` xatolik berardi. Short-circuit tufayli bunday tekshiruvlarni xavfsiz yozish mumkin.

## Bir nechta shartni birlashtirish

```python
yosh = 25
maosh = 4000000
ish_tajribasi = 3

if yosh >= 18 and maosh >= 2000000 and ish_tajribasi >= 1:
    print("Kredit uchun to'liq mos")
```

Murakkab shartlarda qavslardan foydalanish o'qishni osonlashtiradi:

```python
if (yosh >= 18 and yosh <= 65) and (maosh >= 2000000 or ish_tajribasi >= 5):
    print("Shartlarga javob beradi")
```

## `in` va `not in` operatorlari shart sifatida

```python
ruxsat_etilgan_kunlar = ["Dushanba", "Chorshanba", "Juma"]
bugun = "Chorshanba"

if bugun in ruxsat_etilgan_kunlar:
    print("Bugun mashg'ulot bor")
else:
    print("Bugun dam olish kuni")
```

## Zanjirlangan solishtirish (Chained comparison)

Python'ning qulay xususiyatlaridan biri — matematikadagi kabi zanjirli solishtirish:

```python
yosh = 25

# odatiy usul
if yosh >= 18 and yosh <= 65:
    print("Ish yoshidagi odam")

# Python'ga xos qisqa usul — xuddi shu ma'noni beradi
if 18 <= yosh <= 65:
    print("Ish yoshidagi odam")
```

## `all()` va `any()` funksiyalari

Bir nechta shartni ro'yxat ko'rinishida tekshirish kerak bo'lganda juda foydali:

```python
baholar = [85, 90, 78, 92]

print(all(baho >= 60 for baho in baholar))   # True — hammasi 60 dan yuqorimi
print(any(baho >= 95 for baho in baholar))    # False — kamida bittasi 95 dan yuqorimi
```

`all()` — barcha elementlar `True` bo'lsagina `True` qaytaradi.
`any()` — kamida bitta element `True` bo'lsa `True` qaytaradi.

```python
shartlar = [yosh >= 18, maosh >= 2000000, ish_tajribasi >= 1]

if all(shartlar):
    print("Barcha shartlar bajarildi")
```

## De Morgan qonunlari (mantiqiy transformatsiya)

Ba'zan shartni soddalashtirish kerak bo'ladi. Bu qonunlar foydali:

```python
# not (A and B) == (not A) or (not B)
# not (A or B) == (not A) and (not B)

yosh = 15
haydovchilik_bor = False

# quyidagi ikkita shart bir xil natija beradi:
if not (yosh >= 18 and haydovchilik_bor):
    print("Haydash mumkin emas")

if yosh < 18 or not haydovchilik_bor:
    print("Haydash mumkin emas")
```

## Amaliy misol: kirish nazorati tizimi

```python
foydalanuvchi_roli = "admin"
tizimga_kirgan = True
ish_vaqti = 14   # soat 24 formatda

if tizimga_kirgan and (foydalanuvchi_roli == "admin" or foydalanuvchi_roli == "moderator"):
    if 9 <= ish_vaqti <= 18:
        print("Boshqaruv paneliga kirish ruxsat etildi")
    else:
        print("Ish vaqtidan tashqarida, faqat ko'rish rejimida")
else:
    print("Kirish taqiqlangan")
```

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. Foydalanuvchidan yosh va fuqarolik (Uzbekiston/boshqa) so'rab, agar yoshi 18dan katta VA fuqaroligi Uzbekiston bo'lsa, "Ovoz berish huquqingiz bor" deb chiqaring.
2. Sonlar ro'yxati berilgan — `all()` yordamida barcha sonlar musbat ekanligini tekshiring.
3. Sonlar ro'yxati berilgan — `any()` yordamida ro'yxatda kamida bitta juft son borligini tekshiring.
4. Zanjirlangan solishtirish (`10 <= x <= 20`) yordamida sonning berilgan oraliqda ekanligini tekshiruvchi dastur yozing.

🟡 **O'rta daraja**

5. Kiyim tanlash tizimi: harorat va yomg'ir bor-yo'qligiga qarab (ikkita input) qanday kiyim kiyish tavsiyasini beruvchi dastur yozing (masalan harorat past va yomg'ir bor — "issiq kiyim va soyabon").
6. Uch xil shartdan (yosh, maosh, ish staji) kamida ikkitasi bajarilsa "qisman mos" deb chiqaruvchi dastur yozing (`sum()` va `bool` yig'indisidan foydalanishga harakat qiling).
7. Parol kuchini tekshirish dasturini (oldingi mavzudagi) `all()` funksiyasi yordamida qayta yozing — har bir shart alohida bool o'zgaruvchida saqlansin.

---

**Oldingi mavzu:** [10 — Shartlar (if/else)](./10_shartlar_if_else.md)
**Keyingi mavzu:** [12 — while tsikli](./12_while_tsikli.md)
