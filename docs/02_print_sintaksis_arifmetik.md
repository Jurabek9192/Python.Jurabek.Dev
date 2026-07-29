# 02 — PRINT(), SINTAKSIS VA ARIFMETIK AMALLAR

## print() — bir nechta qiymat bilan

```python
print("Yosh:", 25, "Shahar:", "Toshkent")
```

```
Yosh: 25 Shahar: Toshkent
```

Vergul bilan ajratilgan qiymatlar orasiga Python avtomatik bo'sh joy qo'yadi.

## sep va end parametrlari

```python
print("olma", "banan", "uzum", sep=", ")     # ajratkichni o'zgartirish
print("Salom", end=" ")                        # oxirini o'zgartirish (standart \n o'rniga)
print("Dunyo")
```

```
olma, banan, uzum
Salom Dunyo
```

## Python sintaksisi — asosiy qoidalar

- Har bir buyruq alohida qatorda yoziladi (nuqta-vergul shart emas, C++/Java'dan farqli)
- Bloklar (if, for, funksiya) **indentatsiya (bo'sh joy)** orqali belgilanadi — bu Python'da majburiy
- Katta-kichik harflar farqlanadi (`Yosh` va `yosh` — ikki xil nom)

```python
if True:
    print("Bu bloк ichida")   # 4 ta bo'sh joy bilan suriladi
print("Bu blokdan tashqarida")
```

## Arifmetik amallar

| Operator | Ma'nosi | Misol | Natija |
|---|---|---|---|
| `+` | Qo'shish | `5 + 3` | `8` |
| `-` | Ayirish | `5 - 3` | `2` |
| `*` | Ko'paytirish | `5 * 3` | `15` |
| `/` | Bo'lish | `5 / 2` | `2.5` |
| `//` | Butun bo'lish | `5 // 2` | `2` |
| `%` | Qoldiq | `5 % 2` | `1` |
| `**` | Daraja | `5 ** 2` | `25` |

```python
print(10 + 3)      # 13
print(10 - 3)       # 7
print(10 * 3)        # 30
print(10 / 3)         # 3.3333333333333335
print(10 // 3)         # 3
print(10 % 3)            # 1
print(10 ** 3)             # 1000
```

## Amallar ustuvorligi

Matematikadagi kabi: avval qavs, keyin daraja, keyin ko'paytirish/bo'lish, oxirida qo'shish/ayirish.

```python
natija = 2 + 3 * 4       # 14, chunki avval 3*4
natija2 = (2 + 3) * 4      # 20, chunki avval qavs
print(natija, natija2)
```

## input() bilan arifmetik amal

```python
son1 = int(input("Birinchi son: "))
son2 = int(input("Ikkinchi son: "))
print("Yig'indi:", son1 + son2)
```

**Diqqat:** `input()` har doim matn (`str`) qaytaradi, shuning uchun sonli amal uchun `int()` yoki `float()` ga aylantirish kerak.

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ikkita sonni qo'shib, natijasini chiqaring.
2. Ikkita sonni ayirib, ko'paytirib va bo'lib, uchala natijani ham chiqaring.
3. 17 ni 5 ga bo'lganda qolgan qoldiqni (`%`) toping.
4. 2 ning 10-darajasini (`**`) hisoblang.
5. `sep=", "` parametridan foydalanib, 3 ta mevani vergul bilan ajratib chiqaring.
6. `end=""` parametridan foydalanib, ikkita `print()`ni bir qatorda birlashtiring.
7. Ikkita son kiritilsin (`input()` orqali) va ularning yig'indisi chiqarilsin.
8. To'rtburchakning eni va bo'yi kiritilsin, yuzasi hisoblansin.

🟡 **O'rta (9-15)**

9. Uch xonali sonning har bir raqamini (`//` va `%` yordamida) alohida chiqaring (masalan 235 -> 2, 3, 5).
10. Foydalanuvchidan sekundlar soni so'ralsin va uni soat:minut:sekund ko'rinishiga o'giring.
11. Doira radiusi kiritilsin, uning yuzasi (`3.14159 * r**2`) va aylana uzunligi (`2 * 3.14159 * r`) hisoblansin.
12. Ikki xonali sonni teskarisiga aylantiring (masalan 34 -> 43), faqat matematik amallar bilan (string ishlatmasdan).
13. Amallar ustuvorligini tekshiruvchi 3 ta murakkab ifoda yozing va natijalarini qo'lda hisoblab, dastur natijasi bilan solishtiring.
14. Foydalanuvchidan uch tomonning uzunligini so'rab, uchburchak perimetrini hisoblang.
15. Kompound foiz formulasi (`summa * (1 + foiz/100) ** yillar`) yordamida, boshlang'ich summa va foiz stavkasini kiritib, 5 yildan keyingi summani hisoblang.

🔴 **Qiyin (16-20)**

16. Foydalanuvchidan santimetrda uzunlik kiritilsin va uni metr, kilometr birliklariga aylantirib chiqaring.
17. Ikkita nuqtaning koordinatalari (x1,y1) va (x2,y2) kiritilsin, ular orasidagi masofani formula (`((x2-x1)**2 + (y2-y1)**2) ** 0.5`) orqali hisoblang.
18. Valyuta kalkulyatori: foydalanuvchi USD summasini kiritadi, siz uni belgilangan kursga (masalan 1$ = 12700 so'm) ko'paytirib, so'mga aylantirasiz.
19. BMI (tana massasi indeksi) kalkulyatorini yozing: vazn (kg) va bo'y (m) kiritilib, `vazn / boy**2` formulasi bilan hisoblansin, natija 2 xonagacha yaxlitlansin.
20. Uch xonali sonning raqamlari yig'indisi va ko'paytmasini (faqat matematik amallar bilan, `//` va `%` yordamida) alohida hisoblang.

---

**Oldingi mavzu:** [01 — Dasturlash va Python bilan tanishuv](./01_python_bilan_tanishuv.md)
**Keyingi mavzu:** [03 — O'zgaruvchilar](./03_ozgaruvchilar.md)
