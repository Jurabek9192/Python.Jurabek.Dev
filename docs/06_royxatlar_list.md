# RO'YXATLAR (LIST)

## List nima?

**List (ro'yxat)** — bir nechta qiymatni bitta o'zgaruvchida, tartiblangan holda saqlash imkonini beruvchi ma'lumot turi. Kvadrat qavs `[]` ichida, vergul bilan ajratib yoziladi.

```python
mevalar = ["olma", "banan", "uzum", "anor"]
print(mevalar)
print(type(mevalar))
```

```
['olma', 'banan', 'uzum', 'anor']
<class 'list'>
```

List ichida turli xil ma'lumot turlarini birga saqlash ham mumkin:

```python
aralash = ["Ali", 25, True, 3.14]
```

## Indeks orqali murojaat qilish

Listning har bir elementi o'z indeksiga ega, sanoq `0` dan boshlanadi (string kabi):

```python
mevalar = ["olma", "banan", "uzum", "anor"]

print(mevalar[0])     # olma
print(mevalar[2])     # uzum
print(mevalar[-1])    # anor  (oxirgi element)
```

## Kesish (slicing)

```python
sonlar = [10, 20, 30, 40, 50, 60]

print(sonlar[1:4])     # [20, 30, 40]
print(sonlar[:3])       # [10, 20, 30]
print(sonlar[3:])       # [40, 50, 60]
print(sonlar[::-1])     # [60, 50, 40, 30, 20, 10]  — teskari tartib
```

## Listlar o'zgaruvchan (mutable)!

Stringdan farqli o'laroq, listning elementlarini to'g'ridan-to'g'ri o'zgartirish mumkin:

```python
mevalar = ["olma", "banan", "uzum"]
mevalar[1] = "shaftoli"
print(mevalar)
```

```
['olma', 'shaftoli', 'uzum']
```

## Elementlarni qo'shish

```python
mevalar = ["olma", "banan"]

mevalar.append("anor")          # oxiriga bitta element qo'shadi
print(mevalar)                    # ['olma', 'banan', 'anor']

mevalar.insert(1, "uzum")        # 1-indeksga qo'yadi
print(mevalar)                    # ['olma', 'uzum', 'banan', 'anor']

mevalar.extend(["nok", "shaftoli"])  # boshqa listni oxiriga qo'shib qo'yadi
print(mevalar)
```

**Diqqat:** `append()` bilan `extend()` orasidagi farq — `append(["a","b"])` butun ro'yxatni bitta element sifatida qo'shadi, `extend(["a","b"])` esa har bir elementini alohida qo'shadi:

```python
a = [1, 2]
a.append([3, 4])
print(a)     # [1, 2, [3, 4]]

b = [1, 2]
b.extend([3, 4])
print(b)     # [1, 2, 3, 4]
```

## Elementlarni o'chirish

```python
mevalar = ["olma", "banan", "uzum", "anor"]

mevalar.remove("banan")     # qiymat bo'yicha o'chiradi
print(mevalar)                # ['olma', 'uzum', 'anor']

oxirgisi = mevalar.pop()     # oxirgisini o'chiradi va qaytaradi
print(oxirgisi)                # anor
print(mevalar)                 # ['olma', 'uzum']

del mevalar[0]                # indeks bo'yicha o'chirish
print(mevalar)                 # ['uzum']

mevalar.clear()                # hammasini tozalash
print(mevalar)                  # []
```

## Foydali list metodlari

```python
sonlar = [5, 3, 8, 1, 9, 3]

print(len(sonlar))          # 6      — uzunligi
print(sonlar.count(3))       # 2      — 3 soni nechta uchraydi
print(sonlar.index(8))       # 2      — 8 ning indeksi

sonlar.sort()                 # o'sish tartibida saralaydi (joyida o'zgartiradi)
print(sonlar)                  # [1, 3, 3, 5, 8, 9]

sonlar.sort(reverse=True)     # kamayish tartibida
print(sonlar)                  # [9, 8, 5, 3, 3, 1]

sonlar.reverse()               # tartibni teskari qiladi
print(sonlar)

yangi = sorted([3, 1, 2])      # asl listni o'zgartirmasdan, yangisini qaytaradi
print(yangi)
```

## `in` operatori — mavjudlikni tekshirish

```python
mevalar = ["olma", "banan", "uzum"]

print("olma" in mevalar)        # True
print("shaftoli" in mevalar)    # False
print("shaftoli" not in mevalar) # True
```

## Listlarni birlashtirish va ko'paytirish

```python
a = [1, 2, 3]
b = [4, 5, 6]

print(a + b)      # [1, 2, 3, 4, 5, 6]  — birlashtirish
print(a * 3)       # [1, 2, 3, 1, 2, 3, 1, 2, 3]  — takrorlash
```

## Listlar bilan tsikl (for)

Bu mavzuni keyinroq chuqurroq o'rganamiz, lekin oldindan tanishib qo'yaylik:

```python
mevalar = ["olma", "banan", "uzum"]

for meva in mevalar:
    print(f"Men {meva} yeyman")
```

```
Men olma yeyman
Men banan yeyman
Men uzum yeyman
```

## Ichma-ich listlar (nested list)

Listning ichida boshqa list bo'lishi mumkin — bu jadval yoki matritsalarni ifodalashda qo'l keladi:

```python
matritsa = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

print(matritsa[0])       # [1, 2, 3]
print(matritsa[1][2])    # 6  — 1-qatorning 2-ustuni
```

## List nusxalash haqida muhim eslatma

```python
a = [1, 2, 3]
b = a              # DIQQAT: bu nusxa emas, xuddi shu listga ishoraat!
b.append(4)
print(a)             # [1, 2, 3, 4]  — a ham o'zgardi!

c = a.copy()         # haqiqiy nusxa yaratish
c.append(5)
print(a)              # [1, 2, 3, 4]  — o'zgarmadi
print(c)               # [1, 2, 3, 4, 5]
```

Bu Python'da listlar **mutable (o'zgaruvchan)** obyekt bo'lgani va o'zgaruvchilar aslida xotiradagi manzilga ishora qilgani sababli yuz beradi. Bu — dasturchilar ko'p xato qiladigan joylardan biri, shuning uchun alohida diqqat qiling.

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. 5 ta shaharning nomidan iborat list yarating va ularni birma-bir (tsiklsiz, indeks orqali) chiqaring.
2. Listga yangi shahar qo'shing (`append`), birini o'chiring (`remove`), natijani chiqaring.
3. Berilgan sonlar ro'yxatini o'sish va kamayish tartibida saralab chiqaring.
4. Listda muayyan bir element borligini `in` operatori orqali tekshiring.
5. Listning eng birinchi va eng oxirgi elementlarini chiqaring (indeks va `-1` yordamida).

🟡 **O'rta daraja**

6. Sonlar ro'yxati berilgan — undagi eng katta va eng kichik sonni (`max()`, `min()` funksiyalarisiz, o'zingiz solishtirib) toping.
7. Ro'yxatdagi barcha juft sonlarni yangi ro'yxatga yig'ib chiqaring.
8. Ikkita listni birlashtirib, takrorlanuvchi elementlarni olib tashlang (`set()` dan foydalanishga harakat qiling).
9. 3x3 matritsa (ichma-ich list) yarating va uning barcha elementlari yig'indisini toping.

🔴 **Murakkabroq**

10. Talabalar ismi va bahosidan iborat ichma-ich list berilgan (masalan `[["Ali", 85], ["Vali", 92], ["Guli", 78]]`). Eng yuqori bahoga ega talabani toping va uni ismini chop eting.

---

**Oldingi mavzu:** [05 — Kiritish va chiqarish](./05_kiritish_chiqarish.md)
**Keyingi mavzu:** [07 — Kortejlar (tuple)](./07_kortejlar_tuple.md)
