# SHARTLAR — IF / ELSE

## Nega shartlar kerak?

Hayotda biz doimiy ravishda shartlarga asoslangan qarorlar qabul qilamiz: *"Agar yomg'ir yog'sa, soyabon olaman, aks holda olmayman"*. Dasturlash ham xuddi shunday — kod ma'lum shart bajarilganda bir narsa qilishi, aks holda boshqa narsa qilishi kerak bo'ladi. Buning uchun **shartli operatorlar (if/else)** ishlatiladi.

## Bool turi — shartlarning asosi

Har qanday shart, oxir-oqibat, `True` yoki `False` qiymatiga tugaydi:

```python
print(5 > 3)      # True
print(5 == 10)     # False
print(10 != 5)     # True
```

## Solishtirish operatorlari

| Operator | Ma'nosi |
|---|---|
| `==` | Teng |
| `!=` | Teng emas |
| `>` | Katta |
| `<` | Kichik |
| `>=` | Katta yoki teng |
| `<=` | Kichik yoki teng |

**Eng ko'p uchraydigan xato:** `=` (tenglashtirish) bilan `==` (solishtirish)ni chalkashtirish. `=` qiymat beradi, `==` esa ikki qiymatni solishtiradi.

```python
yosh = 18        # bu tenglashtirish — yosh o'zgaruvchisiga 18 qiymati beriladi
print(yosh == 18) # bu solishtirish — True qaytaradi
```

## Oddiy `if`

```python
yosh = 20

if yosh >= 18:
    print("Siz kattasiz")
```

```
Siz kattasiz
```

**Diqqat qiling:**
- `if` shartidan keyin ikki nuqta (`:`) qo'yiladi
- Shart bajarilganda ishlaydigan kod **4 ta bo'sh joy (indentatsiya)** bilan ichkariga suriladi
- Python'da indentatsiya — bu shunchaki chiroylik emas, balki **majburiy sintaksis qoidasi**

## `if / else`

```python
yosh = 15

if yosh >= 18:
    print("Siz kattasiz")
else:
    print("Siz voyaga yetmagansiz")
```

```
Siz voyaga yetmagansiz
```

## `if / elif / else`

Bir nechta shartni ketma-ket tekshirish kerak bo'lganda `elif` (else if qisqartmasi) ishlatiladi:

```python
baho = 75

if baho >= 90:
    print("A - A'lo")
elif baho >= 70:
    print("B - Yaxshi")
elif baho >= 50:
    print("C - Qoniqarli")
else:
    print("D - Qoniqarsiz")
```

```
B - Yaxshi
```

**Muhim tushuncha:** Python shartlarni **yuqoridan pastga qarab**, birinchi `True` bo'lgan shartni topguncha tekshiradi va qolganlarini tekshirmay o'tkazib yuboradi. Shu sababli shartlar tartibi juda muhim — yuqoridagi misolda agar `baho >= 70` shartini birinchi qo'ysak, `baho >= 90` bo'lgan holatlar ham noto'g'ri "B" deb chiqib ketardi.

## Mantiqiy operatorlar: `and`, `or`, `not`

Bir nechta shartni birlashtirish uchun ishlatiladi:

```python
yosh = 25
maosh = 3000000

if yosh >= 18 and maosh >= 2000000:
    print("Kredit olish uchun mos keladi")
```

| Operator | Ma'nosi | Misol |
|---|---|---|
| `and` | Ikkalasi ham to'g'ri bo'lsa `True` | `(5>3) and (2>1)` → `True` |
| `or` | Kamida bittasi to'g'ri bo'lsa `True` | `(5>3) or (1>2)` → `True` |
| `not` | Qiymatni teskarisiga aylantiradi | `not (5>3)` → `False` |

```python
harorat = -5

if harorat < 0 or harorat > 40:
    print("Ob-havo noqulay")
else:
    print("Ob-havo normal")
```

## Ichma-ich shartlar (nested if)

Shart ichida yana shart bo'lishi mumkin:

```python
yosh = 20
haydovchilik_guvohnomasi = True

if yosh >= 18:
    if haydovchilik_guvohnomasi:
        print("Mashina haydashingiz mumkin")
    else:
        print("Avval guvohnoma oling")
else:
    print("Yoshingiz yetarli emas")
```

Bu yerda `and` operatoridan foydalanib, kodni tekisroq qilish mumkin edi:

```python
if yosh >= 18 and haydovchilik_guvohnomasi:
    print("Mashina haydashingiz mumkin")
else:
    print("Shart bajarilmadi")
```

**Amaliy maslahat:** Iloji boricha ichma-ich shartlarni kamaytiring — kod chuqurlashgan sari o'qish qiyinlashadi. `and`/`or` operatorlari orqali shartlarni bitta qatorga tekislash odatda yaxshiroq amaliyot hisoblanadi.

## Bir qatorli if/else (ternary operator)

Qisqa shartlarni bitta qatorda yozish mumkin:

```python
yosh = 20
holat = "katta" if yosh >= 18 else "kichik"
print(holat)
```

```
katta
```

Bu quyidagiga teng:

```python
if yosh >= 18:
    holat = "katta"
else:
    holat = "kichik"
```

Ternary operator faqat oddiy, qisqa shartlar uchun tavsiya etiladi — murakkab mantiq bo'lsa, oddiy `if/else` o'qish uchun qulayroq bo'ladi.

## "Truthy" va "Falsy" qiymatlar

Python'da `if` shartiga faqat `True`/`False` emas, boshqa qiymatlar ham berilishi mumkin — Python ularni avtomatik `bool`ga aylantiradi:

**Falsy** (shart `False` deb hisoblanadigan qiymatlar):
```python
if 0: print("ishlamaydi")           # 0 — falsy
if "": print("ishlamaydi")           # bo'sh string — falsy
if []: print("ishlamaydi")            # bo'sh list — falsy
if None: print("ishlamaydi")          # None — falsy
```

**Truthy** (deyarli hamma boshqa narsa):
```python
if 5: print("ishlaydi")               # har qanday nol bo'lmagan son
if "salom": print("ishlaydi")          # bo'sh bo'lmagan string
if [1, 2]: print("ishlaydi")            # bo'sh bo'lmagan list
```

Bu amaliyotda juda foydali, masalan listning bo'sh emasligini tekshirish uchun `len(royxat) > 0` o'rniga to'g'ridan-to'g'ri `if royxat:` yozish mumkin.

## Amaliy misol: login tekshiruvchi

```python
togri_login = "admin"
togri_parol = "12345"

kiritilgan_login = input("Login: ")
kiritilgan_parol = input("Parol: ")

if kiritilgan_login == togri_login and kiritilgan_parol == togri_parol:
    print("Tizimga xush kelibsiz!")
elif kiritilgan_login != togri_login:
    print("Login noto'g'ri")
else:
    print("Parol noto'g'ri")
```

**Muhim eslatma:** Real hayotda parollar solishtirilganda katta-kichik harflar farqi muammo tug'diradi. Buni oldini olish uchun ko'pincha `.lower()` metodi ishlatiladi (login uchun, parol uchun emas — parol har doim aniq mos kelishi kerak):

```python
if kiritilgan_login.lower() == togri_login.lower():
    ...
```

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. Foydalanuvchidan yosh so'rab, 18 yoshdan katta yoki kichikligini aniqlang.
2. Foydalanuvchidan son kiritib, uning musbat, manfiy yoki nolga tengligini aniqlovchi dastur yozing (`elif` dan foydalaning).
3. Foydalanuvchidan sonni kiritib, u juft yoki toqligini aniqlang.
4. Foydalanuvchidan bahoni (0-100) so'rab, harf baho (A/B/C/D/F) ga aylantiruvchi dastur yozing.
5. Uch sonning eng kattasini `if/elif/else` yordamida (`max()` dan foydalanmasdan) toping.

🟡 **O'rta daraja**

6. Foydalanuvchidan yil kiritib, u kabisa yili (leap year) yoki yo'qligini aniqlang. (Qoida: 4 ga bo'linadigan, lekin 100 ga bo'linmaydigan, YOKI 400 ga bo'linadigan yillar kabisa yili hisoblanadi.)
7. Uchburchakning uchta tomoni berilgan — bu qiymatlar bilan haqiqiy uchburchak yasash mumkinligini tekshiring (har bir tomon boshqa ikki tomon yig'indisidan kichik bo'lishi kerak).
8. Taksi narxini hisoblovchi dastur: boshlang'ich narx 5000 so'm, har km uchun 1500 so'm, agar masofa 10 km dan oshsa 10% chegirma beriladi.

🔴 **Murakkabroq**

9. Oddiy parol kuchini tekshiruvchi dastur yozing: parol kamida 8 belgidan iborat bo'lishi, kamida bitta katta harf, bitta kichik harf va bitta raqamdan iborat bo'lishi kerak. Har bir shart bajarilmasa, aniq qaysi talab bajarilmaganini chiqaring.

---

**Oldingi mavzu:** [09 — To'plamlar (set)](./09_toplamlar_set.md)
**Keyingi mavzu:** [11 — Mantiqiy operatorlar va murakkab shartlar](./11_mantiqiy_operatorlar.md)
