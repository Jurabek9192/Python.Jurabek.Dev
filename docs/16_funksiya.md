# 16 — FUNKSIYA

## Funksiya nima va nega kerak?

Takrorlanadigan kodni bitta joyga jamlab, qayta-qayta ishlatish imkonini beradi.

```python
def salomlash():
    print("Salom, Dunyo!")

salomlash()      # chaqirish
```

## Parametrli funksiya

```python
def salomlash(ism):
    print(f"Salom, {ism}!")

salomlash("Ali")
salomlash("Vali")
```

## Standart (default) qiymat

```python
def salomlash(ism, til="uz"):
    if til == "uz":
        print(f"Salom, {ism}!")
    else:
        print(f"Hello, {ism}!")

salomlash("Ali")
salomlash("John", "en")
```

**Muhim qoida:** Standart qiymatli parametrlar har doim oddiy parametrlardan **keyin** yoziladi:

```python
def togri(a, b=10):       # to'g'ri
    pass

# def notogri(a=10, b):     # XATOLIK! SyntaxError
```

## Kalit so'z orqali chaqirish (keyword arguments)

```python
def royxatga_olish(ism, yosh, guruh):
    print(f"{ism}, {yosh}, {guruh}")

royxatga_olish(guruh="B", ism="Vali", yosh=22)     # tartib muhim emas
royxatga_olish("Ali", guruh="A", yosh=20)             # pozitsion va kalit so'z aralash
```

## Faqat pozitsion va faqat kalit so'z parametrlar (Python 3.8+)

```python
def funksiya(a, b, /, c, d, *, e, f):
    # a, b — FAQAT pozitsion (/ dan oldin)
    # c, d — pozitsion HAM, kalit so'z HAM bo'lishi mumkin
    # e, f — FAQAT kalit so'z (* dan keyin)
    print(a, b, c, d, e, f)

funksiya(1, 2, 3, d=4, e=5, f=6)      # to'g'ri
```

Bu — katta loyihalarda funksiya "shartnomasi"ni aniqroq qilish uchun ishlatiladi.

## Mahalliy (local) va global o'zgaruvchilar

```python
hisob = 0

def qoshish():
    hisob = 10       # bu yangi, LOCAL o'zgaruvchi — globalga tegmaydi
    print(hisob)

qoshish()
print(hisob)      # 0 — global o'zgarmadi

def haqiqiy_qoshish():
    global hisob        # global kalit so'zi — endi haqiqiy globalni o'zgartiradi
    hisob += 10

haqiqiy_qoshish()
print(hisob)      # 10
```

## Docstring — funksiyani hujjatlashtirish

```python
def yigindi(a, b):
    """
    Ikki sonning yig'indisini hisoblaydi.

    Parametrlar:
        a (int): birinchi son
        b (int): ikkinchi son

    Qaytaradi:
        int: a va b ning yig'indisi
    """
    return a + b

print(yigindi.__doc__)     # docstring'ni ko'rsatadi
help(yigindi)                  # to'liq yordam ma'lumotini ko'rsatadi
```

## Funksiyalar — "birinchi darajali obyekt"

Python'da funksiyalar ham xuddi son yoki string kabi obyekt hisoblanadi:

```python
def salomlash():
    print("Salom!")

mening_funksiyam = salomlash     # funksiyani o'zgaruvchiga yozish (chaqirmasdan!)
mening_funksiyam()                  # endi uni chaqirish mumkin

def bajarilishi_organ(funksiya):        # funksiyani argument sifatida qabul qilish
    funksiya()

bajarilishi_organ(salomlash)
```

## Rekursiya — funksiyaning o'zini o'zi chaqirishi

```python
def faktorial(n):
    if n <= 1:              # to'xtash sharti (base case) — SHART, aks holda cheksiz ishlaydi
        return 1
    return n * faktorial(n - 1)      # o'zini o'zi chaqiryapti

print(faktorial(5))     # 120
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Hech qanday parametrsiz, "Xush kelibsiz!" deb chiqaruvchi funksiya yozing.
2. Ism qabul qilib, salomlashuvchi funksiya yozing.
3. Ikki son qabul qilib, ularning yig'indisini ekranga chiqaruvchi funksiya yozing.
4. Standart qiymatli parametr bilan funksiya yozing (masalan shahar, standart "Toshkent").
5. Ism va yoshni qabul qilib, tanishtiruvchi gapni chiqaruvchi funksiya yozing.
6. 3 ta funksiyani kalit so'z orqali (`ism=..., yosh=...`) chaqirib sinab ko'ring.
7. Funksiya ichida local o'zgaruvchi yarating va uni funksiyadan tashqarida chaqirishga urinib, xatolikni ko'ring.
8. Docstring'i bo'lgan funksiya yozing va uning docstring'ini `__doc__` orqali va `help()` orqali chiqaring.

🟡 **O'rta (9-15)**

9. Uch son qabul qilib, ular orasidan eng kattasini ekranga chiqaruvchi funksiya yozing.
10. To'rtburchakning eni va bo'yini qabul qilib, yuzasini ekranga chiqaruvchi funksiya yozing.
11. `global` kalit so'zidan foydalanib, funksiya ichida global hisoblagichni oshiruvchi dastur yozing, uni 5 marta chaqirib sinang.
12. Standart qiymatli ikkita parametrli "kuchga oshirish" funksiyasini yozing.
13. Faktorialni rekursiya orqali hisoblovchi funksiya yozing va 3 xil son bilan sinab ko'ring.
14. Funksiyani o'zgaruvchiga yozib (chaqirmasdan), keyin o'sha o'zgaruvchi orqali chaqiring.
15. Global va local o'zgaruvchi farqini ko'rsatuvchi 3 ta misol yozing, har birida natijani izohlab bering.

🔴 **Qiyin (16-20)**

16. Talaba ma'lumotlarini (ism, yosh, guruh) qabul qilib, chiroyli formatlangan "profil karta" chiqaruvchi funksiya yozing.
17. Fibonachchi sonini rekursiya orqali hisoblovchi funksiya yozing (`fib(n) = fib(n-1) + fib(n-2)`, `fib(0)=0`, `fib(1)=1`).
18. `/` va `*` belgilaridan foydalanib, faqat pozitsion va faqat kalit so'z parametrli funksiya yozing, uni to'g'ri va noto'g'ri chaqirib sinab ko'ring.
19. Bir-birini chaqiradigan ikkita funksiya yozing (masalan `tekshir()` funksiyasi `chiqar()` funksiyasini chaqiradi).
20. To'liq "vizit karta generatori" funksiyasini yozing — ism, kasb, telefon, email parametrlari (ba'zilari standart qiymat bilan) va chiroyli ramkali chiqish bilan.

---

**Oldingi mavzu:** [15 — While, ro'yxatlar va lug'atlar](./15_while_royxatlar.md)
**Keyingi mavzu:** [17 — Qiymat qaytaruvchi funksiya](./17_qiymat_qaytarish.md)
