# 02 — PRINT(), SINTAKSIS VA ARIFMETIK AMALLAR

## print() funksiyasining to'liq imzosi

```python
print(*qiymatlar, sep=' ', end='\n', file=sys.stdout, flush=False)
```

- **`*qiymatlar`** — istalgan sondagi chiqariladigan qiymat
- **`sep`** — qiymatlar orasidagi ajratkich (standart — bo'sh joy)
- **`end`** — oxirida qo'yiladigan belgi (standart — yangi qator `\n`)
- **`file`** — qayerga chiqarilishi (standart — ekran)
- **`flush`** — darhol chiqarish majburiyati

```python
print("Yosh:", 25, "Shahar:", "Toshkent")             # Yosh: 25 Shahar: Toshkent
print("olma", "banan", "uzum", sep=", ")                  # olma, banan, uzum
print("Salom", end=" ")                                      # oxiri probel bilan
print("Dunyo")
```

## Python sintaksisi — asosiy qoidalar

- Har bir buyruq alohida qatorda yoziladi (nuqta-vergul shart emas)
- Bloklar **indentatsiya (bo'sh joy)** orqali belgilanadi — bu Python'da majburiy (odatda 4 ta bo'sh joy)
- Katta-kichik harflar farqlanadi

```python
if True:
    print("Bu bloк ichida")
print("Bu blokdan tashqarida")
```

## Barcha arifmetik operatorlar

| Operator | Ma'nosi | Misol | Natija |
|---|---|---|---|
| `+` | Qo'shish | `5 + 3` | `8` |
| `-` | Ayirish | `5 - 3` | `2` |
| `*` | Ko'paytirish | `5 * 3` | `15` |
| `/` | Bo'lish (natija doim float) | `5 / 2` | `2.5` |
| `//` | Butun bo'lish | `5 // 2` | `2` |
| `%` | Qoldiq | `5 % 2` | `1` |
| `**` | Daraja | `5 ** 2` | `25` |

```python
print(10 + 3, 10 - 3, 10 * 3, 10 / 3, 10 // 3, 10 % 3, 10 ** 3)
```

## divmod() — bo'lish va qoldiqni birga olish

```python
natija = divmod(17, 5)
print(natija)     # (3, 2) — tuple: (butun bo'lim, qoldiq)
buluvchi, qoldiq = divmod(17, 5)
```

## Amallar ustuvorligi (to'liq tartib)

1. `()` — qavslar
2. `**` — daraja (o'ngdan chapga hisoblanadi)
3. `*`, `/`, `//`, `%` — chapdan o'ngga
4. `+`, `-` — chapdan o'ngga

```python
print(2 + 3 * 4)         # 14
print((2 + 3) * 4)          # 20
print(2 ** 3 ** 2)            # 512 — o'ngdan chapga: 2**(3**2)=2**9
```

## Qisqartirilgan tenglashtirish operatorlari (arifmetik bilan bog'liq)

```python
son = 10
son += 5    # 15
son -= 3      # 12
son *= 2       # 24
son /= 4        # 6.0
son //= 2        # 3.0
son **= 2         # 9.0
son %= 4           # 1.0
```

## format() funksiyasi va sonlarni formatlash

```python
narx = 1234567.891
print(format(narx, ",.2f"))     # 1,234,567.89
print(f"{narx:,.2f}")             # xuddi shu natija, f-string orqali

print(format(255, "b"))    # 11111111 — ikkilik (binary)
print(format(255, "o"))      # 377 — sakkizlik (octal)
print(format(255, "x"))       # ff — o'n oltilik (hex)
```

## Son sistemalari — bin(), oct(), hex()

```python
print(bin(10))     # 0b1010
print(oct(10))       # 0o12
print(hex(10))         # 0xa
print(int("1010", 2))    # 10 — ikkilik matndan songa
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
7. `divmod()` yordamida 23 ni 4 ga bo'lganda butun qism va qoldiqni birga oling.
8. To'rtburchakning eni va bo'yi kiritilsin, yuzasi hisoblansin.

🟡 **O'rta (9-15)**

9. Uch xonali sonning har bir raqamini (`//` va `%` yordamida) alohida chiqaring (masalan 235 -> 2, 3, 5).
10. Foydalanuvchidan sekundlar soni so'ralsin va uni soat:minut:sekund ko'rinishiga o'giring (`divmod()` dan foydalanib ko'ring).
11. Doira radiusi kiritilsin, uning yuzasi va aylana uzunligi hisoblansin.
12. `format()` funksiyasi bilan biror narxni minglik ajratkich bilan chiqaring.
13. 10 dan 255 gacha 3 ta sonni `bin()`, `oct()`, `hex()` orqali turli sanoq sistemalarida chiqaring.
14. Foydalanuvchidan uch tomonning uzunligini so'rab, uchburchak perimetrini hisoblang.
15. Kompound foiz formulasi yordamida, boshlang'ich summa va foiz stavkasini kiritib, 5 yildan keyingi summani hisoblang.

🔴 **Qiyin (16-20)**

16. Foydalanuvchidan santimetrda uzunlik kiritilsin va uni metr, kilometr birliklariga aylantirib chiqaring.
17. Ikkita nuqtaning koordinatalari kiritilsin, ular orasidagi masofani formula orqali hisoblang.
18. Valyuta kalkulyatori: foydalanuvchi USD summasini kiritadi, siz uni belgilangan kursga ko'paytirib, so'mga aylantirasiz, natijani `format()` bilan chiroyli chiqaring.
19. BMI kalkulyatorini yozing, natija 2 xonagacha yaxlitlansin va `f"{bmi:.2f}"` bilan chiqarilsin.
20. Ikkilik sondan (masalan "1101") o'nlikka, va aksincha, aylantiruvchi ikki funksiyani `int(x, 2)` va `bin()` yordamida yozing.

---

**Oldingi mavzu:** [01 — Dasturlash va Python bilan tanishuv](./01_python_bilan_tanishuv.md)
**Keyingi mavzu:** [03 — O'zgaruvchilar](./03_ozgaruvchilar.md)
