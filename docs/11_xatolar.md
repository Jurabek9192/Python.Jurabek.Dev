# 11 — XATOLAR BILAN ISHLASH

## "Dasturchi xato qiladi. Yaxshi dasturchi ko'p xato qiladi."

Xatolik — dasturlashning tabiiy qismi. Muhimi — xatolikni qanday boshqarishni bilish.

## try/except asoslari

```python
try:
    son = int(input("Son kiriting: "))
    print(100 / son)
except:
    print("Xatolik yuz berdi")
```

**Diqqat:** `except:` (hech narsa yozmasdan) — barcha xatoliklarni ushlaydi, lekin bu tavsiya etilmaydi, chunki qanday xatolik yuz berganini bilmay qolamiz.

## Muayyan xatolik turlarini ushlash

```python
try:
    son = int(input("Son: "))
    print(100 / son)
except ValueError:
    print("Noto'g'ri son kiritildi")
except ZeroDivisionError:
    print("Nolga bo'lib bo'lmaydi")
```

## Python'ning barcha keng tarqalgan xatolik turlari

| Xatolik | Sabab |
|---|---|
| `ValueError` | Noto'g'ri qiymat (`int("abc")`) |
| `ZeroDivisionError` | Songa nolga bo'lish |
| `TypeError` | Mos kelmaydigan turlar bilan amal (`"5" + 5`) |
| `IndexError` | List/tuple'da mavjud bo'lmagan indeks |
| `KeyError` | Dictionary'da mavjud bo'lmagan kalit |
| `FileNotFoundError` | Fayl topilmadi |
| `AttributeError` | Obyektda mavjud bo'lmagan metod/atribut |
| `ImportError` / `ModuleNotFoundError` | Modul topilmadi |
| `NameError` | E'lon qilinmagan o'zgaruvchi ishlatilgan |
| `IndentationError` | Noto'g'ri bo'sh joy/tab |
| `RecursionError` | Rekursiya juda chuqur ketgan (to'xtash sharti yo'q) |
| `OverflowError` | Son juda katta bo'lib ketgan |
| `StopIteration` | Iterator tugagan |
| `PermissionError` | Fayl/papkaga ruxsat yo'q |
| `KeyboardInterrupt` | Foydalanuvchi Ctrl+C bosgan |

```python
royxat = [1, 2, 3]
try:
    print(royxat[10])
except IndexError:
    print("Xato: bunday indeks mavjud emas")

lugat = {"ism": "Ali"}
try:
    print(lugat["yosh"])
except KeyError:
    print("Xato: bunday kalit mavjud emas")

try:
    print("5" + 5)
except TypeError:
    print("Xato: turlar mos kelmadi")
```

## Bir nechta xatolik turini birga ushlash

```python
try:
    son = int(input("Son: "))
    natija = 100 / son
except (ValueError, ZeroDivisionError) as xatolik:
    print(f"Xato yuz berdi: {xatolik}")
```

## Xatolik xabarini olish — `as`

```python
try:
    son = int("abc")
except ValueError as xatolik:
    print(f"Xatolik: {xatolik}")
    print(type(xatolik))       # <class 'ValueError'>
```

## else va finally

```python
try:
    son = int(input("Son: "))
except ValueError:
    print("Noto'g'ri son")
else:
    print(f"Muvaffaqiyatli: {son}")       # faqat xato bo'lmasa ishlaydi
finally:
    print("Tekshiruv yakunlandi")            # xato bo'lsa ham, bo'lmasa ham HAR DOIM ishlaydi
```

## Umumiy Exception — hamma narsani ushlaydigan "zaxira"

```python
try:
    # kod
    pass
except ValueError:
    print("Aniq xato turi")
except Exception as e:              # boshqa har qanday kutilmagan xatolik uchun
    print(f"Kutilmagan xatolik: {e}")
```

**Qoida:** Har doim eng aniq xatolik turlaridan boshlang, `Exception`ni eng oxiriga qo'ying.

## O'z xatoligingizni chaqirish — raise

```python
def yosh_tekshir(yosh):
    if yosh < 0:
        raise ValueError("Yosh manfiy bo'lishi mumkin emas")
    return yosh

try:
    yosh_tekshir(-5)
except ValueError as e:
    print(f"Xato: {e}")
```

## Xavfsiz kiritish funksiyasi

```python
def son_kiritish(xabar):
    while True:
        try:
            return int(input(xabar))
        except ValueError:
            print("Xato! Faqat son kiriting.")
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Foydalanuvchidan son so'rab, uni 10ga bo'ling — `ValueError` va `ZeroDivisionError` ni alohida ushlang.
2. Listdan foydalanuvchi kiritgan indeks bo'yicha element chiqaring, `IndexError` ni ushlang.
3. Dictionary'dan kalit bo'yicha qiymat oling, `KeyError` ni ushlang.
4. `TypeError` chiqaradigan kod (masalan `"5" + 5`) yozib, uni `try/except` bilan ushlang.
5. `as` orqali xatolik xabarini olib, uni va uning turini (`type()`) chiqaring.
6. `finally` blokidan foydalanib, "Tekshiruv tugadi" degan xabar har doim chiqishini ta'minlang.
7. Mavjud bo'lmagan faylni ochishga urinib, `FileNotFoundError` ni ushlang.
8. `else` blokidan foydalanib, faqat xatosiz holatda "Muvaffaqiyatli!" deb chiqaring.

🟡 **O'rta (9-15)**

9. Xavfsiz son kiritish funksiyasini yozing — foydalanuvchi to'g'ri son kiritmagunicha qayta so'raydigan.
10. Ikkita sonni bo'lishda barcha mumkin bo'lgan xatoliklarni alohida ushlab, har biriga aniq xabar bering.
11. `raise ValueError(...)` yordamida, foydalanuvchi manfiy yosh kiritsa, o'zingiz xatolik chiqaring va uni ushlang.
12. Ro'yxatdan indeks bo'yicha element olishda, agar indeks noto'g'ri bo'lsa, foydalanuvchidan qaytadan so'rovchi dastur yozing.
13. Mavjud bo'lmagan faylni qayta-qayta so'rab, mavjud fayl nomi kiritilguncha davom etuvchi dastur yozing.
14. `except Exception as e` yordamida barcha kutilmagan xatoliklarni ushlab, xabarini chiqaring.
15. Kalkulyator dasturiga (ikkita son va amal) barcha mumkin bo'lgan xatoliklarni qo'shing.

🔴 **Qiyin (16-20)**

16. Bank tizimi simulyatori: pul yechishda agar summa balansdan katta bo'lsa, o'zingiz yaratgan xabar bilan `ValueError` chiqaring.
17. `try/except/else/finally`ning barcha to'rttasini birga ishlatuvchi to'liq dastur yozing va har bir blok qachon ishlaganini konsolga chiqaring.
18. Ichma-ich `try/except` yozing — tashqi blok fayl ochishni, ichki blok fayl ichidagi ma'lumotni songa aylantirishni tekshirsin.
19. Foydalanuvchidan matematik ifoda (masalan "5+3") kiritilib, uni hisoblovchi, lekin xato ifoda kiritilganda chiroyli xabar beruvchi dastur yozing.
20. To'liq "xavfsiz kalkulyator" yarating — foydalanuvchi son yoki amal xato kiritsa, dastur to'xtamasdan, tushunarli xabar bilan qayta so'rasin.

---

**Oldingi mavzu:** [10 — Bir nechta shartlarni tekshirish](./10_murakkab_shartlar.md)
**Keyingi mavzu:** [12 — Dictionary bilan tanishuv](./12_dictionary.md)
