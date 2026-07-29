# 05 — SONLAR

## int va float

```python
butun = 10          # int
kasr = 10.5           # float
print(type(butun), type(kasr))
```

## Turlarni aylantirish

```python
print(int("25"))       # 25 — matndan songa
print(float("3.14"))     # 3.14
print(str(100))            # "100" — sondan matnga
print(int(7.9))              # 7 — kasr qismi tashlanadi (yaxlitlanmaydi!)
print(round(7.9))              # 8 — bu yaxlitlaydi
```

## Foydali funksiyalar

```python
print(abs(-15))            # 15 — mutlaq qiymat
print(max(3, 9, 1))          # 9
print(min(3, 9, 1))            # 1
print(round(3.14159, 2))         # 3.14
print(pow(2, 10))                  # 1024
```

## math moduli

```python
import math

print(math.sqrt(16))       # 4.0
print(math.floor(3.9))       # 3
print(math.ceil(3.1))          # 4
print(math.pi)                    # 3.14159...
```

## Zamonaviy imkoniyat — sonlarni o'qish oson yozish (underscore)

Python 3.6+ da katta sonlarni o'qish osonroq qilish uchun pastki chiziq ishlatish mumkin:

```python
million = 1_000_000
print(million)     # 1000000 — pastki chiziqlar avtomatik olib tashlanadi
```

## Zamonaviy imkoniyat — walrus operator (:=)

Python 3.8+ da qiymatni tekshirish bilan bir vaqtda o'zgaruvchiga yozish mumkin:

```python
# eski usul
son = int(input("Son: "))
if son > 10:
    print(f"{son} — 10 dan katta")

# walrus operator bilan (bir qatorda)
if (son := int(input("Son: "))) > 10:
    print(f"{son} — 10 dan katta")
```

## Sonlarni solishtirish

```python
print(5 > 3)       # True
print(5 == 5)         # True
print(5 != 3)           # True
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ikkita son kiritilsin, ular yig'indisi, ayirmasi va ko'paytmasi chiqarilsin.
2. Foydalanuvchi kiritgan sonning juft yoki toqligini aniqlang (`%` yordamida).
3. Kasr sonni 2 xonagacha yaxlitlang (`round()`).
4. Uch sondan eng kattasi va eng kichigini (`max()`, `min()`) toping.
5. Manfiy sonning mutlaq qiymatini (`abs()`) toping.
6. `math.sqrt()` yordamida sonning kvadrat ildizini toping.
7. `1_000_000` kabi pastki chiziqli yozuvda 3 ta katta son yarating va ularning yig'indisini chiqaring.
8. Foydalanuvchidan kiritilgan matnni songa aylantiring (`int()` yoki `float()`).

🟡 **O'rta (9-15)**

9. To'rtburchakning yuzi va perimetrini hisoblang, natijalarni 2 xonagacha yaxlitlang.
10. Foydalanuvchidan yosh so'rab, walrus operatoridan foydalanib, agar 18 dan katta bo'lsa "Kattasiz" deb chiqaring (bitta shart qatorida).
11. `math.floor()` va `math.ceil()` farqini 5 xil kasr son bilan sinab ko'ring va natijalarni jadval ko'rinishida chiqaring.
12. Doira yuzi va aylanasini `math.pi` yordamida hisoblang.
13. Uch xonali sonning har bir raqamini ajratib, ularning yig'indisini toping.
14. Kompyuter va inson o'rtasidagi "raqamlar taqqoslash" o'yinini yozing — ikkita son kiritilib, kim kattaligi aytilsin.
15. Foydalanuvchidan kelib tushgan pul miqdorini so'rab, undan 3 xil valyuta kursida (siz belgilagan) hisoblang.

🔴 **Qiyin (16-20)**

16. Sonning tub (prime) ekanligini tekshiruvchi dastur yozing (2 dan sonning o'ziga qadar bo'linishini tekshiring).
17. Ikki sonning eng katta umumiy bo'luvchisini (EKUB) topuvchi dastur yozing (Evklid algoritmisiz, oddiy tsikl bilan — while mavzusida chuqurlashtiramiz, hozircha faqat matematik yondashuv bilan urinib ko'ring).
18. Foydalanuvchidan asosiy summa, foiz stavkasi va yillar sonini so'rab, kompound foiz formulasi bilan yakuniy summani hisoblang.
19. Faktorial hisoblovchi dastur yozing (masalan 5! = 5*4*3*2*1) — hozircha faqat ko'paytirish orqali (tsiklsiz, qo'lda yozib ko'ring 5! uchun, keyin umumlashtirishga harakat qiling).
20. Uch o'lchamli fazoda ikki nuqta orasidagi masofani (`math.sqrt((x2-x1)**2+(y2-y1)**2+(z2-z1)**2)`) hisoblovchi dastur yozing.

---

**Oldingi mavzu:** [04 — String (matn)](./04_string.md)
**Keyingi mavzu:** [06 — List (ro'yxat)](./06_list.md)
