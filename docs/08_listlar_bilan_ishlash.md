# KIRITISH VA CHIQARISH (INPUT/OUTPUT)

## print() funksiyasi chuqurroq

`print()` funksiyasi bilan biz allaqachon tanishganmiz, lekin uning yana bir qancha foydali parametrlari bor.

### Bir nechta qiymatni chiqarish

```python
print("Salom", "Dunyo", 2026)
```

```
Salom Dunyo 2026
```

Vergul bilan ajratilgan qiymatlar orasiga standart holatda **bo'sh joy** qo'yiladi.

### `sep` parametri — ajratkichni o'zgartirish

```python
print("Salom", "Dunyo", sep="-")
print(2025, 7, 27, sep="/")
```

```
Salom-Dunyo
2025/7/27
```

### `end` parametri — oxirini o'zgartirish

Standart holatda `print()` har doim oxirida yangi qatorga o'tadi (`\n`). Buni `end` orqali o'zgartirish mumkin:

```python
print("Salom", end=" ")
print("Dunyo")
```

```
Salom Dunyo
```

Ikkala `print()` ham bir qatorda chiqdi, chunki birinchisi yangi qatorga emas, bo'sh joyga tugadi.

## String formatlash usullari

Python'da matn ichiga qiymat qo'yishning bir nechta usuli bor — tarixiy rivojlanish tartibida ko'raylik.

### 1. `%` operatori (eski usul)

```python
ism = "Aziz"
print("Salom, %s!" % ism)
```

### 2. `.format()` metodi

```python
ism = "Aziz"
yosh = 20
print("Men {}, {} yoshdaman".format(ism, yosh))
```

### 3. f-string (zamonaviy, tavsiya etiladigan usul)

```python
ism = "Aziz"
yosh = 20
print(f"Men {ism}, {yosh} yoshdaman")
```

Ushbu kursda biz doimo **f-string** dan foydalanamiz, chunki u eng qisqa va o'qish uchun eng qulay usul.

## f-string ichida formatlash

f-string sonlarni chiroyli formatda chiqarish uchun ham imkoniyat beradi:

```python
narx = 1234567.891

print(f"{narx:.2f}")        # 1234567.89   — 2 xonagacha yaxlitlash
print(f"{narx:,.2f}")       # 1,234,567.89 — minglik ajratkich bilan
print(f"{75:>10}")           # o'ngga tekislash, 10 belgi kenglikda
print(f"{75:<10}|")          # chapga tekislash
print(f"{75:^10}|")          # markazga tekislash
```

```
1234567.89
1,234,567.89
        75
75        |
    75    |
```

## input() funksiyasi chuqurroq

`input()` funksiyasi foydalanuvchidan klaviatura orqali ma'lumot qabul qiladi va uni **har doim `str` turida** qaytaradi.

```python
ism = input("Ismingizni kiriting: ")
print(f"Xush kelibsiz, {ism}!")
```

### Sonli qiymat kiritish

```python
yosh = int(input("Yoshingizni kiriting: "))
narx = float(input("Narxni kiriting: "))
```

Agar foydalanuvchi son o'rniga matn kiritsa (masalan "yigirma"), `int()` funksiyasi `ValueError` xatoligini beradi. Bu muammoni keyingi mavzularda `try/except` orqali qanday hal qilishni o'rganamiz.

### Bir qatorda bir nechta qiymat kiritish

```python
# Foydalanuvchi "5 10" deb kiritadi (bo'sh joy bilan ajratib)
a, b = input("Ikkita sonni bo'sh joy bilan kiriting: ").split()
a = int(a)
b = int(b)
print(a + b)
```

```
Ikkita sonni bo'sh joy bilan kiriting: 5 10
15
```

Yoki `map()` funksiyasi bilan qisqaroq:

```python
a, b = map(int, input("Ikkita son kiriting: ").split())
print(a + b)
```

## Amaliy misol: mini profil generatori

```python
ism = input("Ismingiz: ")
yosh = int(input("Yoshingiz: "))
shahar = input("Yashash shahringiz: ")
kasb = input("Kasbingiz: ")

print("-" * 30)
print(f"{'ISM':<12}: {ism}")
print(f"{'YOSH':<12}: {yosh}")
print(f"{'SHAHAR':<12}: {shahar}")
print(f"{'KASB':<12}: {kasb}")
print("-" * 30)
```

```
Ismingiz: Bekzod
Yoshingiz: 24
Yashash shahringiz: Buxoro
Kasbingiz: dasturchi
------------------------------
ISM         : Bekzod
YOSH        : 24
SHAHAR      : Buxoro
KASB        : dasturchi
------------------------------
```

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. Foydalanuvchidan uchta narsaning narxini (bittalab) so'rab, ularning jamini `.2f` formatda (2 xonagacha) chiqaring.
2. `sep` va `end` parametrlaridan foydalanib, 1 dan 5 gacha sonlarni bitta qatorda, vergul bilan ajratib chiqaring.
3. Foydalanuvchidan ism va familiyani bitta qatorda, bo'sh joy bilan ajratib kiritishni so'rang (`split()` dan foydalaning) va ularni alohida-alohida chiqaring.

🟡 **O'rta daraja**

4. Foydalanuvchidan mahsulot narxini kiritishni so'rang va uni minglik ajratkich bilan (masalan `1,500,000`) chiqaring.
5. Kvitansiya (chek) generatori: 3 ta mahsulot nomi va narxini so'rab, jadval ko'rinishida (`:<` va `:>` formatlash bilan tekislangan) chiqaring, oxirida umumiy summani ko'rsating.
6. Foydalanuvchidan bitta qatorda uchta son kiritishni so'rang (bo'sh joy bilan ajratilgan) va ularning o'rtacha qiymatini `.2f` formatda chiqaring.

---
