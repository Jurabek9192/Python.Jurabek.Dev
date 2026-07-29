# FOR TSIKLI

## for tsiklining sintaksisi

`for` tsikli — **ma'lum bir to'plam (list, string, tuple, dictionary va h.k.) elementlari bo'ylab** aylanish uchun ishlatiladi. `while`dan farqli o'laroq, `for` odatda takrorlanish sonini oldindan bilamiz degani.

```python
mevalar = ["olma", "banan", "uzum"]

for meva in mevalar:
    print(meva)
```

```
olma
banan
uzum
```

Bu yerda `meva` — har bir aylanishda listning navbatdagi elementini o'zida saqlovchi vaqtinchalik o'zgaruvchi (nomini o'zingiz istagancha tanlashingiz mumkin).

## range() funksiyasi

Ma'lum sonlar oralig'ida takrorlash uchun `range()` funksiyasi ishlatiladi:

```python
for i in range(5):
    print(i)
```

```
0
1
2
3
4
```

**Diqqat:** `range(5)` `0` dan boshlanib `4` da tugaydi (5 ta son: 0,1,2,3,4) — oxirgi son kiritilmaydi, xuddi slicing'dagi kabi.

### range()ning uch xil ko'rinishi

```python
range(5)         # 0, 1, 2, 3, 4              — 0 dan boshlab
range(2, 8)       # 2, 3, 4, 5, 6, 7            — belgilangan boshlanishdan
range(0, 10, 2)   # 0, 2, 4, 6, 8               — qadam bilan
range(10, 0, -1)  # 10, 9, 8, 7, ..., 1          — kamayish tartibida
```

```python
for i in range(2, 11, 2):
    print(i, end=" ")
```

```
2 4 6 8 10
```

## String bo'ylab aylanish

```python
soz = "Python"

for harf in soz:
    print(harf)
```

```
P
y
t
h
o
n
```

## Dictionary bo'ylab aylanish

```python
odam = {"ism": "Aziza", "yosh": 24, "shahar": "Farg'ona"}

for kalit in odam:
    print(kalit, "->", odam[kalit])

print("---")

for kalit, qiymat in odam.items():
    print(f"{kalit}: {qiymat}")
```

## enumerate() — indeks va qiymatni birga olish

Ko'pincha listning elementi bilan birga uning indeksi ham kerak bo'ladi. `enumerate()` buni qulay qiladi:

```python
mevalar = ["olma", "banan", "uzum"]

for indeks, meva in enumerate(mevalar):
    print(f"{indeks}: {meva}")
```

```
0: olma
1: banan
2: uzum
```

Boshlanish sonini o'zgartirish ham mumkin:

```python
for indeks, meva in enumerate(mevalar, start=1):
    print(f"{indeks}. {meva}")
```

```
1. olma
2. banan
3. uzum
```

## zip() — bir nechta listni birga aylanish

```python
ismlar = ["Ali", "Vali", "Guli"]
yoshlar = [20, 22, 19]

for ism, yosh in zip(ismlar, yoshlar):
    print(f"{ism} - {yosh} yoshda")
```

```
Ali - 20 yoshda
Vali - 22 yoshda
Guli - 19 yoshda
```

## Ichma-ich for tsikllari (nested loop)

Tsikl ichida tsikl bo'lishi mumkin — bu jadval yoki matritsa bilan ishlashda ko'p ishlatiladi:

```python
for i in range(1, 4):
    for j in range(1, 4):
        print(f"{i}x{j}={i*j}", end="  ")
    print()   # har qator oxirida yangi qatorga o'tish
```

```
1x1=1  1x2=2  1x3=3  
2x1=2  2x2=4  2x3=6  
3x1=3  3x2=6  3x3=9  
```

### Ko'paytirish jadvali misoli

```python
for i in range(1, 6):
    for j in range(1, 11):
        print(f"{i} x {j} = {i*j}")
    print("-" * 15)
```

## break va continue — for bilan

Bular `while`dagi bilan bir xil ishlaydi:

```python
for son in range(1, 20):
    if son == 10:
        break             # 10 ga yetganda tsikl to'xtaydi
    print(son)
```

```python
for son in range(1, 10):
    if son % 2 == 0:
        continue           # juft sonlarni o'tkazib yuboradi
    print(son)
```

## for ... else

`while`dagi kabi, `for` ham `else` bilan ishlatilishi mumkin — bu tsikl `break` bo'lmasdan tabiiy tugasa ishga tushadi. Ko'pincha "qidiruv" mantig'ida foydali:

```python
sonlar = [2, 4, 6, 8, 10]

for son in sonlar:
    if son % 2 != 0:
        print("Toq son topildi!")
        break
else:
    print("Barcha sonlar juft ekan")
```

```
Barcha sonlar juft ekan
```

## List comprehension — oldindan tanishish

`for` tsiklining qisqa, bir qatorlik ko'rinishi bor — buni keyingi mavzularda chuqur o'rganamiz, lekin bu yerda ko'rib qo'yaylik:

```python
# oddiy usul
kvadratlar = []
for i in range(1, 6):
    kvadratlar.append(i ** 2)
print(kvadratlar)

# list comprehension — qisqa usul
kvadratlar = [i ** 2 for i in range(1, 6)]
print(kvadratlar)
```

Ikkalasi ham bir xil natija beradi: `[1, 4, 9, 16, 25]`

## Amaliy misol: sonlar orasidan tub sonlarni topish

```python
for son in range(2, 30):
    tub = True
    for boluvchi in range(2, son):
        if son % boluvchi == 0:
            tub = False
            break
    if tub:
        print(son, end=" ")
```

```
2 3 5 7 11 13 17 19 23 29
```

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. `range()` yordamida 1 dan 20 gacha barcha sonlarni chiqaring.
2. 1 dan 50 gacha bo'lgan barcha 3 ga bo'linadigan sonlarni chiqaring.
3. Berilgan listdagi barcha elementlarni, indeksi bilan birga (`enumerate` yordamida) chiqaring.
4. 1 dan 10 gacha sonlarning yig'indisini `for` tsikli orqali hisoblang.
5. Berilgan so'zdagi unli harflarni (a, e, i, o, u) sanab chiqing.

🟡 **O'rta daraja**

6. Ko'paytirish jadvalini (1 dan 10 gacha) chiroyli formatda chiqaring.
7. Ikkita listni (mahsulot nomlari va narxlari) `zip()` yordamida birlashtirib, "Non - 3000 so'm" formatida chiqaring.
8. Yulduzchalardan (`*`) uchburchak shaklini chizuvchi dastur yozing (ichma-ich for tsikli yordamida):
```
*
**
***
****
*****
```
9. 1 dan 100 gacha bo'lgan tub sonlarni topib, ularning sonini chiqaring.

🔴 **Murakkabroq**

10. Foydalanuvchidan 5 ta o'quvchining ismi va bahosini kiritishni so'rang (`for` va `range(5)` yordamida), so'ng eng yuqori bahoga ega o'quvchini toping.
11. Ikki o'lchamli list (matritsa) berilgan — uning barcha elementlari yig'indisini va har bir qator yig'indisini alohida hisoblang.

---

**Oldingi mavzu:** [12 — while tsikli](./12_while_tsikli.md)
**Keyingi mavzu:** [14 — break, continue, pass](./14_break_continue_pass.md)
