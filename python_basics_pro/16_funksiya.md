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

## Kalit so'z orqali chaqirish

```python
def royxatga_olish(ism, yosh, guruh):
    print(f"{ism}, {yosh}, {guruh}")

royxatga_olish(guruh="B", ism="Vali", yosh=22)     # tartib muhim emas
```

## Mahalliy (local) va global o'zgaruvchilar

```python
hisob = 0

def qoshish():
    hisob = 10       # bu yangi, LOCAL o'zgaruvchi
    print(hisob)

qoshish()
print(hisob)      # 0 — global o'zgarmadi
```

## Docstring — funksiyani hujjatlashtirish

```python
def yigindi(a, b):
    """Ikki sonning yig'indisini hisoblaydi."""
    return a + b

print(yigindi.__doc__)     # docstring'ni ko'rsatadi
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Hech qanday parametrsiz, "Xush kelibsiz!" deb chiqaruvchi funksiya yozing.
2. Ism qabul qilib, salomlashuvchi funksiya yozing.
3. Ikki son qabul qilib, ularning yig'indisini ekranga chiqaruvchi (hozircha `return`siz) funksiya yozing.
4. Standart qiymatli parametr bilan funksiya yozing (masalan shahar, standart "Toshkent").
5. Ism va yoshni qabul qilib, tanishtiruvchi gapni chiqaruvchi funksiya yozing.
6. 3 ta funksiyani kalit so'z orqali (`ism=..., yosh=...`) chaqirib sinab ko'ring.
7. Funksiya ichida local o'zgaruvchi yarating va uni funksiyadan tashqarida chaqirishga urinib, xatolikni ko'ring.
8. Docstring'i bo'lgan funksiya yozing va uning docstring'ini `__doc__` orqali chiqaring.

🟡 **O'rta (9-15)**

9. Uch son qabul qilib, ular orasidan eng kattasini ekranga chiqaruvchi funksiya yozing.
10. To'rtburchakning eni va bo'yini qabul qilib, yuzasini ekranga chiqaruvchi funksiya yozing.
11. Matnni qabul qilib, undagi unli harflar sonini ekranga chiqaruvchi funksiya yozing.
12. Standart qiymatli ikkita parametrli (masalan `daraja=2`) "kuchga oshirish" funksiyasini yozing.
13. Sonni qabul qilib, uning juft/toqligini ekranga chiqaruvchi funksiya yozing.
14. 5 ta turli funksiyadan iborat oddiy "vositalar to'plami" yozing (masalan: salomlash, xayrlashish, tabriklash, ogohlantirish, so'rash).
15. Global va local o'zgaruvchi farqini ko'rsatuvchi 3 ta misol yozing, har birida natijani izohlab bering.

🔴 **Qiyin (16-20)**

16. Talaba ma'lumotlarini (ism, yosh, guruh) qabul qilib, chiroyli formatlangan "profil karta" chiqaruvchi funksiya yozing.
17. `global` kalit so'zidan foydalanib, funksiya ichida global hisoblagichni oshiruvchi dastur yozing, uni 5 marta chaqirib sinang.
18. Oddiy "menyu" funksiyasini yozing — u parametr sifatida tanlov raqamini oladi va mos xabarni chiqaradi (ichida if/elif bilan).
19. Bir-birini chaqiradigan ikkita funksiya yozing (masalan `tekshir()` funksiyasi `chiqar()` funksiyasini chaqiradi).
20. To'liq "vizit karta generatori" funksiyasini yozing — ism, kasb, telefon, email parametrlari (ba'zilari standart qiymat bilan) va chiroyli ramkali chiqish bilan.

---

**Oldingi mavzu:** [15 — While, ro'yxatlar va lug'atlar](./15_while_royxatlar.md)
**Keyingi mavzu:** [17 — Qiymat qaytaruvchi funksiya](./17_qiymat_qaytarish.md)
