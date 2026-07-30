# 14 — WHILE TSIKLI

## Asosiy sintaksis

```python
son = 1
while son <= 5:
    print(son)
    son += 1
```

## Cheksiz tsikl xatosi

```python
# XATO — son += 1 yozilmagan, cheksiz ishlaydi!
# son = 1
# while son <= 5:
#     print(son)
```

Har doim shart qachon `False` bo'lishini o'ylab yozing. Cheksiz tsikldan chiqish uchun terminalda `Ctrl+C`.

## while True va break

```python
son = 1
while True:
    print(son)
    if son == 5:
        break
    son += 1
```

Bu naqsh, ayniqsa foydalanuvchi kiritgan ma'lumotni tekshirishda ko'p ishlatiladi:

```python
while True:
    parol = input("Parol ('stop' bilan chiqish): ")
    if parol == "stop":
        break
    if len(parol) < 8:
        print("Juda qisqa")
        continue
    print("Qabul qilindi")
    break
```

## continue

```python
son = 0
while son < 10:
    son += 1
    if son % 2 == 0:
        continue
    print(son)     # faqat toq sonlar
```

## while ... else

`while` tsikli `break` orqali emas, tabiiy tugasa, `else` bloki ishga tushadi:

```python
son = 1
while son <= 3:
    print(son)
    son += 1
else:
    print("Tsikl muvaffaqiyatli tugadi (break bo'lmadi)")
```

## Walrus operatori bilan while (Python 3.8+)

```python
# eski usul
while True:
    javob = input("Davom etamizmi? (ha/yoq): ")
    if javob == "yoq":
        break
    print("Davom etmoqda...")

# walrus operator bilan qisqaroq
while (javob := input("Davom etamizmi? (ha/yoq): ")) != "yoq":
    print("Davom etmoqda...")
```

## Ichma-ich while tsikllari

```python
i = 1
while i <= 3:
    j = 1
    while j <= 3:
        print(f"{i}x{j}={i*j}", end="  ")
        j += 1
    print()
    i += 1
```

## for vs while — qачон qaysi biri?

| Holat | Tanlov |
|---|---|
| Takrorlanish sonini oldindan bilamiz (ro'yxat, `range`) | **for** |
| Shart bajarilguncha noma'lum son marta takrorlanadi | **while** |
| Foydalanuvchidan to'g'ri ma'lumot kelguncha so'rash | **while** |
| Menyu tizimi (foydalanuvchi chiqishni tanlaguncha) | **while True** |

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. `while` yordamida 1 dan 10 gacha sonlarni chiqaring.
2. 10 dan 1 gacha (kamayish tartibida) sonlarni chiqaring.
3. Foydalanuvchi "stop" kiritmaguncha, kiritgan so'zlarini takrorlab chiqaring.
4. 1 dan 100 gacha juft sonlarning yig'indisini `while` bilan hisoblang.
5. `while True` va `break` yordamida foydalanuvchidan 5 marta ism so'rang.
6. `continue` yordamida 1-20 oralig'ida faqat 3ga bo'linmaydigan sonlarni chiqaring.
7. Foydalanuvchidan parol so'rab, "python123" kiritilmaguncha qayta so'rayvering.
8. `while...else` tuzilmasidan foydalanib, tsikl `break` bo'lmasdan tugaganda maxsus xabar chiqaring.

🟡 **O'rta (9-15)**

9. Sonning faktorialini `while` tsikli bilan hisoblang.
10. Taxminlash o'yini: kompyuter 1-100 orasida son o'ylaydi (`random`), foydalanuvchi taxmin qiladi, "kattaroq"/"kichikroq" ko'rsatkichlar bilan.
11. ATM simulyatori: boshlang'ich balans 1,000,000, foydalanuvchi "yechish"/"qo'yish"/"chiqish" buyruqlarini kiritadi.
12. Walrus operatoridan foydalanib, foydalanuvchi "yoq" kiritmaguncha davom etuvchi `while` tsiklini qisqa yozing.
13. Menyu tizimi (1-Qo'shish, 2-Ko'rish, 3-Chiqish) — foydalanuvchi "3" kiritmaguncha davom etsin.
14. `while` yordamida sonning raqamlar yig'indisini toping.
15. Ikki sonning EKUB (Evklid algoritmi)ni `while` tsikli va `%` operatori bilan toping.

🔴 **Qiyin (16-20)**

16. Parol kuchini tekshiruvchi tizim: foydalanuvchi to'g'ri parol kiritmaguncha qayta so'raladi, urinishlar soni hisoblanadi.
17. Fibonachchi ketma-ketligini `while` bilan, 1000dan katta bo'lgan birinchi songacha hisoblang.
18. "Son topish" o'yinini to'liq yozing: cheklangan urinishlar soni bilan, har urinishdan keyin qolgan urinishlar sonini ko'rsating.
19. Oddiy login tizimi: foydalanuvchiga 3 marta login/parol kiritish imkoni beriladi, 3 marta xato bo'lsa "hisob bloklandi" deb chiqadi.
20. Menyu asosidagi "vazifalar ro'yxati" (to-do list) dasturi: qo'shish, ko'rish, o'chirish, chiqish amallari `while True` menyu ichida ishlasin.

---

**Oldingi mavzu:** [13 — Nesting](./13_nesting.md)
**Keyingi mavzu:** [15 — While, ro'yxatlar va lug'atlar](./15_while_royxatlar.md)
