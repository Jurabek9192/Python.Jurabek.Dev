# SONLAR VA MATEMATIK AMALLAR

## Son turlari

Python'da ikkita asosiy son turi bor:

- **`int`** — butun sonlar: `5`, `-100`, `0`, `1000000`
- **`float`** — kasr (o'nlik) sonlar: `3.14`, `-0.5`, `2.0`

```python
butun = 10
kasr = 10.5
print(type(butun))
print(type(kasr))
```

```
<class 'int'>
<class 'float'>
```

**Diqqat:** `10` va `10.0` Python uchun turli xil qiymatlar — biri `int`, ikkinchisi `float`.

## Asosiy matematik operatorlar

| Operator | Ma'nosi | Misol | Natija |
|---|---|---|---|
| `+` | Qo'shish | `5 + 3` | `8` |
| `-` | Ayirish | `5 - 3` | `2` |
| `*` | Ko'paytirish | `5 * 3` | `15` |
| `/` | Bo'lish (natija doim float) | `5 / 2` | `2.5` |
| `//` | Butun bo'lish (qoldiqsiz) | `5 // 2` | `2` |
| `%` | Bo'lishdan qolgan qoldiq | `5 % 2` | `1` |
| `**` | Darajaga ko'tarish | `5 ** 2` | `25` |

```python
a = 17
b = 5

print(a + b)    # 22
print(a - b)    # 12
print(a * b)    # 85
print(a / b)    # 3.4
print(a // b)   # 3
print(a % b)    # 2
print(a ** b)   # 1419857
```

## `/` va `//` orasidagi farq

Bu ikkalasi ko'p chalkashtiriladi:

```python
print(7 / 2)    # 3.5   — oddiy bo'lish, natija doim float
print(7 // 2)   # 3     — butun qism olinadi (pastga qarab yaxlitlanadi)
print(-7 // 2)  # -4    — diqqat! pastga qarab yaxlitlash manfiy tomonga ham ishlaydi
```

## `%` operatori — qoldiqni topish

`%` operatori amaliyotda juda ko'p ishlatiladi, masalan sonning juft yoki toqligini aniqlashda:

```python
son = 7
if son % 2 == 0:
    print("Juft son")
else:
    print("Toq son")
```

```
Toq son
```

Bu shu bilan ishlaydi: agar son 2 ga qoldiqsiz bo'linsa (`% 2 == 0`), demak u juft.

## Amallar ustuvorligi (operator precedence)

Matematikadagi kabi, Python'da ham amallar ma'lum tartibda bajariladi:

1. `()` — qavslar birinchi
2. `**` — darajaga ko'tarish
3. `*`, `/`, `//`, `%` — ko'paytirish/bo'lish
4. `+`, `-` — qo'shish/ayirish

```python
natija = 2 + 3 * 4        # avval 3*4=12, keyin 2+12=14
print(natija)              # 14

natija = (2 + 3) * 4       # avval qavs: 2+3=5, keyin 5*4=20
print(natija)               # 20
```

## Foydali matematik funksiyalar

```python
print(round(3.7))       # 4    — yaqin butun songa yaxlitlash
print(round(3.14159, 2)) # 3.14 — 2 xonagacha yaxlitlash
print(abs(-15))          # 15   — mutlaq qiymat (manfiylikni olib tashlaydi)
print(max(4, 9, 2))      # 9    — eng katta qiymat
print(min(4, 9, 2))      # 2    — eng kichik qiymat
print(pow(2, 5))         # 32   — 2 ni 5-darajaga ko'tarish (** bilan bir xil)
```

Murakkabroq matematik funksiyalar uchun `math` moduli ishlatiladi:

```python
import math

print(math.sqrt(16))     # 4.0   — kvadrat ildiz
print(math.floor(3.9))   # 3     — pastga yaxlitlash
print(math.ceil(3.1))    # 4     — yuqoriga yaxlitlash
print(math.pi)            # 3.141592653589793
```

## Qisqartirilgan tenglashtirish operatorlari

O'zgaruvchi ustida amal bajarib, natijani o'sha o'zgaruvchiga qaytadan yozish uchun qisqa yozuv qo'llaniladi:

```python
son = 10
son += 5    # son = son + 5  natija: 15
son -= 3    # son = son - 3  natija: 12
son *= 2    # son = son * 2  natija: 24
son /= 4    # son = son / 4  natija: 6.0
son //= 2   # son = son // 2 natija: 3.0
son **= 2   # son = son ** 2 natija: 9.0
print(son)
```

## Sonlarni solishtirish operatorlari

Bu operatorlar `True` yoki `False` qaytaradi (`bool` turi):

```python
print(5 > 3)     # True
print(5 < 3)     # False
print(5 == 5)    # True
print(5 != 3)    # True
print(5 >= 5)    # True
print(5 <= 4)    # False
```

## Amaliy misol: BMI kalkulyatori

```python
vazn = float(input("Vazningizni kiriting (kg): "))
boy = float(input("Bo'yingizni kiriting (m): "))

bmi = vazn / (boy ** 2)
print(f"Sizning BMI ko'rsatkichingiz: {round(bmi, 2)}")
```

```
Vazningizni kiriting (kg): 70
Bo'yingizni kiriting (m): 1.75
Sizning BMI ko'rsatkichingiz: 22.86
```

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. Ikkita son kiritilsin va ularning yig'indisi, ayirmasi, ko'paytmasi, bo'linmasi ekranga chiqarilsin.
2. Foydalanuvchi kiritgan sonning juft yoki toqligini aniqlovchi dastur yozing.
3. To'rtburchakning eni va bo'yini so'rab, uning yuzini va perimetrini hisoblang.
4. Foydalanuvchidan sekundlarda vaqt kiritilsin va uni soat:minut:sekund formatiga o'girib chiqaring (`//` va `%` dan foydalaning).
5. Uchta sondan eng kattasini `max()` funksiyasi orqali toping.

🟡 **O'rta daraja**

6. Doira radiusini so'rab, uning yuzi va aylanasi uzunligini hisoblang (`math.pi` dan foydalaning).
7. Ikki xonali sonning raqamlari yig'indisini toping (masalan 45 → 4+5=9). `//` va `%` operatorlaridan foydalaning.
8. Kompound foiz kalkulyatori: boshlang'ich summa, yillik foiz stavkasi va yillar sonini so'rab, yakuniy summani hisoblang (`summa * (1 + foiz/100) ** yillar`).

---

