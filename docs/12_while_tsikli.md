# WHILE TSIKLI

## Tsikl (loop) nima?

**Tsikl** — bir xil amalni bir necha marta takrorlash uchun ishlatiladigan struktura. Agar tsikllar bo'lmaganida, 100 marta biror ishni bajarish uchun kodni 100 marta qo'lda yozishimizga to'g'ri kelardi.

## while tsiklining sintaksisi

`while` tsikli shart **True** bo'lgan ekan ishlashda davom etadi:

```python
son = 1

while son <= 5:
    print(son)
    son += 1
```

```
1
2
3
4
5
```

Bu yerdagi jarayonni tahlil qilaylik:
1. `son = 1` — boshlang'ich qiymat
2. `son <= 5` shart tekshiriladi — `True`, shuning uchun tanadagi kod ishlaydi
3. `print(son)` va `son += 1` bajariladi
4. Shart yana tekshiriladi — bu `son` 6 bo'lguncha davom etadi
5. `son <= 5` `False` bo'lgach, tsikl to'xtaydi

## Cheksiz tsikl xatosi (Infinite Loop)

**Eng ko'p uchraydigan xato** — o'zgaruvchini yangilashni unutish, natijada shart hech qachon `False` bo'lmaydi:

```python
# XATO KOD — ISHGA TUSHIRMANG!
son = 1
while son <= 5:
    print(son)
    # son += 1 yozilmagan — dastur abadiy ishlayveradi!
```

Agar shunday holat yuz bersa, terminalda **Ctrl+C** tugmalarini bosib dasturni to'xtatish mumkin. Har doim `while` yozganingizda, shart qachon `False` bo'lishini o'ylab ko'ring.

## Sanoqchi (counter) namunasi

```python
sanoq = 0

while sanoq < 3:
    ism = input("Ismingizni kiriting: ")
    print(f"Salom, {ism}!")
    sanoq += 1

print("Barcha kishilar bilan salomlashildi")
```

## while ... else

Python'ning kamdan-kam ishlatiladigan, lekin foydali xususiyati — `while` tsikli `break` orqali emas, tabiiy tugasa, `else` bloki ishga tushadi:

```python
son = 1
while son <= 3:
    print(son)
    son += 1
else:
    print("Tsikl muvaffaqiyatli tugadi")
```

## `break` — tsiklni majburan to'xtatish

```python
son = 1
while True:        # qasddan cheksiz tsikl
    print(son)
    if son == 5:
        break        # shartga yetganda tsikldan chiqib ketamiz
    son += 1
```

```
1
2
3
4
5
```

`while True:` bilan `break` birgalikda ko'p ishlatiladigan naqsh — bu ayniqsa foydalanuvchi kiritgan ma'lumotni tekshirishda qulay:

```python
while True:
    parol = input("Parolni kiriting (chiqish uchun 'stop' yozing): ")
    if parol == "stop":
        print("Dastur to'xtatildi")
        break
    if len(parol) < 8:
        print("Parol juda qisqa, qayta urinib ko'ring")
        continue
    print("Parol qabul qilindi")
    break
```

## `continue` — joriy iteratsiyani o'tkazib yuborish

`continue` joriy aylanishni to'xtatib, keyingi aylanishga o'tadi (butun tsiklni emas, faqat shu bosqichni):

```python
son = 0
while son < 10:
    son += 1
    if son % 2 == 0:
        continue          # juft sonlarni o'tkazib yuboradi
    print(son)              # faqat toq sonlar chop etiladi
```

```
1
3
5
7
9
```

## Amaliy misol: taxminlash o'yini

```python
import random

maxfiy_son = random.randint(1, 100)
urinishlar = 0

while True:
    taxmin = int(input("1 dan 100 gacha son taxmin qiling: "))
    urinishlar += 1

    if taxmin < maxfiy_son:
        print("Kattaroq son kiriting")
    elif taxmin > maxfiy_son:
        print("Kichikroq son kiriting")
    else:
        print(f"Tabriklaymiz! Siz {urinishlar} ta urinishda topdingiz")
        break
```

## Amaliy misol: menyu tizimi

```python
while True:
    print("\n1 - Qo'shish")
    print("2 - Ko'rish")
    print("3 - Chiqish")
    tanlov = input("Tanlovingiz: ")

    if tanlov == "1":
        print("Element qo'shildi")
    elif tanlov == "2":
        print("Elementlar ko'rsatilmoqda")
    elif tanlov == "3":
        print("Dastur yopildi")
        break
    else:
        print("Noto'g'ri tanlov, qaytadan urining")
```

## while va for — qachon qaysi birini ishlatish

- **`while`** — takrorlanish sonini oldindan bilmaganimizda ishlatiladi (masalan: foydalanuvchi to'g'ri ma'lumot kiritguncha, yoki shart bajarilguncha)
- **`for`** — takrorlanish sonini yoki elementlar to'plamini oldindan bilganimizda ishlatiladi (keyingi mavzuda ko'ramiz)

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. `while` yordamida 1 dan 10 gacha sonlarni ekranga chiqaring.
2. `while` yordamida 10 dan 1 gacha (kamayish tartibida) sonlarni chiqaring.
3. Foydalanuvchi "stop" so'zini kiritmaguncha, uning kiritgan har bir so'zini takrorlab chiqaruvchi dastur yozing.
4. 1 dan 100 gacha bo'lgan barcha juft sonlarning yig'indisini `while` yordamida hisoblang.

🟡 **O'rta daraja**

5. Foydalanuvchidan parol so'rang — agar parol "python123" ga teng bo'lmasa, "Noto'g'ri parol, qayta urinib ko'ring" deb qayta so'rayverning, to'g'ri kiritilganda "Xush kelibsiz!" deb chiqaring.
6. Sonning faktorialini `while` tsikli yordamida hisoblovchi dastur yozing (masalan 5! = 5×4×3×2×1 = 120).
7. Yuqoridagi "taxminlash o'yini" dasturini o'zingiz qayta yozing va unga "3 martadan ko'p noto'g'ri taxmin qilinsa o'yin tugaydi" shartini qo'shing.

🔴 **Murakkabroq**

8. Oddiy ATM simulyatori yozing: boshlang'ich balans 1,000,000 so'm. Foydalanuvchi "yechish", "qo'yish" yoki "chiqish" buyruqlarini kiritadi. Yechishda balансdan ko'p summa so'ralsa, xatolik chiqarilsin. "Chiqish" kiritilganda dastur to'xtasin.

---

**Oldingi mavzu:** [11 — Mantiqiy operatorlar va murakkab shartlar](./11_mantiqiy_operatorlar.md)
**Keyingi mavzu:** [13 — for tsikli](./13_for_tsikli.md)
