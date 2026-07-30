# 05 — SONLAR

## int va float — asosiy son turlari

```python
butun = 10             # int
kasr = 10.5               # float
manfiy = -7                 # int ham manfiy bo'lishi mumkin
katta = 1_000_000              # pastki chiziq — o'qish qulayligi uchun (Python 3.6+)

print(type(butun), type(kasr))
```

## Arifmetik operatorlar — to'liq jadval

| Operator | Ma'nosi | Misol | Natija |
|---|---|---|---|
| `+` | Qo'shish | `5 + 3` | `8` |
| `-` | Ayirish | `5 - 3` | `2` |
| `*` | Ko'paytirish | `5 * 3` | `15` |
| `/` | Bo'lish (doim float) | `5 / 2` | `2.5` |
| `//` | Butun bo'lish | `5 // 2` | `2` |
| `%` | Qoldiq | `5 % 2` | `1` |
| `**` | Daraja | `5 ** 2` | `25` |

```python
a, b = 17, 5
print(a + b, a - b, a * b, a / b, a // b, a % b, a ** b)
```

## Turlarni bir-biriga aylantirish

```python
print(int("25"))          # 25 — matndan songa
print(int(7.9))              # 7 — kasr qismi TASHLANADI (yaxlitlanmaydi!)
print(float("3.14"))           # 3.14
print(str(100))                  # "100" — sondan matnga
print(bool(0))                     # False
print(bool(5))                       # True — 0dan boshqa har qanday son True
print(complex(2, 3))                   # (2+3j) — kompleks son (kamdan-kam ishlatiladi)
```

## Yaxlitlash va foydali o'rnatilgan funksiyalar

```python
print(round(3.14159))            # 3 — eng yaqin butun songa
print(round(3.14159, 2))            # 3.14 — 2 xonagacha
print(round(2.5))                      # 2 — DIQQAT: "bankers rounding" — juft songa yaxlitlaydi!
print(round(3.5))                        # 4

print(abs(-15))            # 15 — mutlaq qiymat
print(max(3, 9, 1))           # 9
print(min(3, 9, 1))              # 1
print(pow(2, 10))                  # 1024 — 2**10 bilan bir xil
print(pow(2, 10, 3))                  # 1 — (2**10) % 3, katta sonlar uchun tez usul
print(divmod(17, 5))                     # (3, 2) — bo'linma va qoldiqni birga qaytaradi
print(sum([1, 2, 3, 4]))                    # 10
print(sum([1, 2, 3], 100))                    # 106 — boshlang'ich qiymat bilan
```

## math moduli — to'liq imkoniyatlar

```python
import math

print(math.sqrt(16))          # 4.0 — kvadrat ildiz
print(math.floor(3.9))           # 3 — pastga yaxlitlash
print(math.ceil(3.1))               # 4 — yuqoriga yaxlitlash
print(math.trunc(3.9))                 # 3 — kasr qismini tashlaydi
print(math.pi)                            # 3.141592653589793
print(math.e)                               # 2.718281828459045 — Eyler soni
print(math.factorial(5))                       # 120 — 5!
print(math.gcd(12, 18))                          # 6 — EKUB (eng katta umumiy bo'luvchi)
print(math.log(100, 10))                           # 2.0 — logarifm (asosi 10)
print(math.log2(8))                                   # 3.0
print(math.log10(1000))                                 # 3.0
print(math.pow(2, 3))                                      # 8.0 — har doim float qaytaradi (** dan farqli)
print(math.hypot(3, 4))                                       # 5.0 — gipotenuza (kvadrat ildiz yig'indisi)
print(math.isnan(float("nan")))                                  # True
print(math.dist((0,0), (3,4)))                                     # 5.0 — ikki nuqta orasidagi masofa
```

## Zamonaviy imkoniyat — walrus operator (:=)

```python
# eski usul
son = int(input("Son: "))
if son > 10:
    print(f"{son} — 10 dan katta")

# walrus operator bilan (bir qatorda)
if (son := int(input("Son: "))) > 10:
    print(f"{son} — 10 dan katta")
```

## Sonlarni solishtirish va zanjirlangan solishtirish

```python
print(5 > 3)         # True
print(5 == 5)           # True
print(5 != 3)              # True
print(1 <= 5 <= 10)          # True — Python'ga xos, zanjirli solishtirish
```

## random moduli — sonlar bilan bog'liq (oldindan tanishuv)

```python
import random

print(random.randint(1, 100))     # 1 dan 100 gacha (ikkalasi ham kiradi)
print(random.random())               # 0.0 dan 1.0 gacha kasr son
print(random.uniform(1.5, 5.5))         # ikki kasr son oralig'ida
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ikkita son kiritilsin, ular yig'indisi, ayirmasi va ko'paytmasi chiqarilsin.
2. Foydalanuvchi kiritgan sonning juft yoki toqligini aniqlang (`%` yordamida).
3. Kasr sonni `round()` bilan 2 xonagacha yaxlitlang.
4. Uch sondan eng kattasi va eng kichigini (`max()`, `min()`) toping.
5. Manfiy sonning mutlaq qiymatini (`abs()`) toping.
6. `math.sqrt()`, `math.floor()`, `math.ceil()` metodlarini bitta kasr son ustida sinab, farqini tushuntiring.
7. `divmod()` funksiyasidan foydalanib, bo'linma va qoldiqni bir vaqtda oling.
8. `1_000_000` kabi pastki chiziqli yozuvda 3 ta katta son yarating va yig'indisini chiqaring.

🟡 **O'rta (9-15)**

9. To'rtburchakning yuzi va perimetrini hisoblang, natijalarni `round()` bilan 2 xonagacha yaxlitlang.
10. Walrus operatoridan foydalanib, kiritilgan yosh 18dan katta bo'lsa "Kattasiz" deb chiqaring (bitta shart qatorida).
11. `math.factorial()` yordamida foydalanuvchi kiritgan sonning faktorialini toping.
12. `math.gcd()` yordamida ikki sonning EKUBini toping.
13. Doira yuzi va aylanasini `math.pi` yordamida hisoblang.
14. `pow()` va `math.pow()` farqini (natija turi jihatidan) sinab ko'ring va izohlang.
15. `math.hypot()` yordamida to'g'ri burchakli uchburchakning gipotenuzasini toping.

🔴 **Qiyin (16-20)**

16. Sonning tub (prime) ekanligini tekshiruvchi dastur yozing.
17. `math.dist()` yordamida ikki nuqta orasidagi masofani hisoblang.
18. Foydalanuvchidan asosiy summa, foiz stavkasi va yillar sonini so'rab, kompound foiz formulasi bilan yakuniy summani hisoblang.
19. `math.log()` va `math.log2()` yordamida, berilgan son necha marta 2ga bo'linsa 1 ga qolishini (binary logarifm) toping.
20. `random.uniform()` va `round()` ni birlashtirib, 1.0 dan 10.0 gacha tasodifiy narxlar generatsiya qiluvchi kichik dastur yozing (5 ta narx).

---

**Oldingi mavzu:** [04 — String (matn)](./04_string.md)
**Keyingi mavzu:** [06 — List (ro'yxat)](./06_list.md)
