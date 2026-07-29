# 15 — WHILE, RO'YXATLAR VA LUG'ATLAR

## Ro'yxat bo'shamaguncha ishlash

```python
vazifalar = ["Non olish", "Kitob o'qish", "Sport"]

while vazifalar:               # ro'yxat bo'sh bo'lmaguncha (truthy)
    joriy = vazifalar.pop()
    print(f"Bajarilmoqda: {joriy}")

print("Barcha vazifalar tugadi!")
```

## Ro'yxatlar orasida ma'lumot ko'chirish

```python
kutish_royxati = ["Ali", "Vali", "Guli"]
tasdiqlanganlar = []

while kutish_royxati:
    foydalanuvchi = kutish_royxati.pop()
    print(f"{foydalanuvchi} tasdiqlanmoqda...")
    tasdiqlanganlar.append(foydalanuvchi)

print("Tasdiqlanganlar:", tasdiqlanganlar)
```

## Ro'yxatdagi barcha nusxalarni olib tashlash

```python
mevalar = ["olma", "banan", "olma", "uzum", "olma"]

while "olma" in mevalar:
    mevalar.remove("olma")

print(mevalar)     # ['banan', 'uzum']
```

## Dictionary bilan while — so'rovnoma simulyatsiyasi

```python
javob_berish_kerak = ["Ali", "Vali", "Guli"]
natijalar = {}

while javob_berish_kerak:
    joriy = javob_berish_kerak.pop()
    javob = input(f"{joriy}, sevimli tilingiz? ")
    natijalar[joriy] = javob

for ism, til in natijalar.items():
    print(f"{ism}: {til}")
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ro'yxatdagi barcha elementlarni `while` yordamida birma-bir chiqarib, ro'yxatni bo'shating.
2. Ro'yxatdan barcha nusxalarini `while "x" in list` orqali olib tashlang.
3. Kutish ro'yxatidagi (`list`) barcha ismlarni "qayta ishlangan" listga o'tkazing.
4. `while` yordamida ro'yxatga foydalanuvchidan 5 marta element qo'shdiring.
5. Ro'yxatdan manfiy sonlarni `while` va `.remove()` bilan olib tashlang.
6. Dictionary'ni bo'shatib, har bir kalit-qiymatni chiqaring (`while dictionary:`).
7. Vazifalar ro'yxatini `while` bilan bajarib, bajarilganlarni alohida ro'yxatga yig'ing.
8. Foydalanuvchidan "stop" kiritilguncha ismlar ro'yxatga qo'shilsin, so'ng barchasi chiqarilsin.

🟡 **O'rta (9-15)**

9. Kutish ro'yxatidagi mijozlarni birma-bir "xizmat ko'rsatib", tasdiqlanganlar ro'yxatiga o'tkazuvchi simulyatsiya yozing.
10. So'rovnoma dasturi: har bir ism uchun savol berilib, javoblar dictionary'da saqlansin, oxirida barcha natijalar chiqarilsin.
11. Ro'yxatdagi barcha "noto'g'ri" (masalan bo'sh string) elementlarni olib tashlang.
12. Navbat simulyatori: mijozlar ro'yxati `while` orqali birma-bir "xizmat ko'rsatilib" chiqariladi, har birida tasodifiy xizmat vaqti (`random`) ko'rsatiladi.
13. Ombor tizimi: mahsulotlar ro'yxatidan `while` yordamida buyurtma qilinganlarini ayirib boring, ombor tugaguncha.
14. Dictionary asosida "ovoz berish" tizimi — nomzodlar ro'yxati bo'shaguncha har biriga ovozlar sonini kiritdiring.
15. Ikki ro'yxat (kutilayotgan va tayyor) orasida elementlarni `while` bilan ko'chiruvchi, va har safar joriy holatni chiqaruvchi dastur yozing.

🔴 **Qiyin (16-20)**

16. To'liq "restoran navbat tizimi": mijozlar ro'yxati, har biri xizmat ko'rsatilgach vaqt va xarajatni dictionary'ga yozib boring, oxirida umumiy statistikani chiqaring.
17. Ombordagi mahsulotlarni (dictionary: nomi->miqdori) `while` bilan birma-bir "sotib", miqdor 0 ga yetganda ro'yxatdan butunlay olib tashlang.
18. Talabalar ro'yxatidan `while` yordamida navbat bilan test o'tkazish simulyatsiyasi — har biriga tasodifiy ball (`random`) berilib, natijalar dictionary'da saqlansin.
19. "Bank navbat" tizimi: mijozlar ro'yxati, har biriga tasodifiy operatsiya turi va vaqti belgilanib, umumiy kutish vaqtini hisoblang.
20. To'liq interaktiv "kutubxona navbat" tizimi yarating — kitob so'rovlari ro'yxati, mavjud kitoblar dictionary'si, `while` orqali navbat bilan ishlov beriladigan, mavjud bo'lmasa "kutish ro'yxati"ga qo'shiladigan.

---

**Oldingi mavzu:** [14 — While tsikli](./14_while.md)
**Keyingi mavzu:** [16 — Funksiya](./16_funksiya.md)
