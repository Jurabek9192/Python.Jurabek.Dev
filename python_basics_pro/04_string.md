# 04 — STRING (MATN)

## String yaratish

```python
ism1 = "Nodira"
ism2 = 'Nodira'          # bittirnoq ham ishlaydi
kop_qatorli = """Birinchi qator
Ikkinchi qator"""
```

## Birlashtirish va f-string

```python
ism = "Sardor"
yosh = 20

# eski usul
print("Ism: " + ism + ", Yosh: " + str(yosh))

# zamonaviy va tavsiya etiladigan usul — f-string
print(f"Ism: {ism}, Yosh: {yosh}")
print(f"Ikki yildan keyin {yosh + 2} yoshda bo'ladi")
```

## Indekslash va kesish (slicing)

```python
soz = "Python"
#      P  y  t  h  o  n
#      0  1  2  3  4  5

print(soz[0])       # P
print(soz[-1])        # n (oxirgi)
print(soz[0:4])         # Pyth
print(soz[::-1])          # nohtyP (teskari)
```

## Muhim string metodlari

```python
matn = "  Salom, Dunyo!  "

print(matn.upper())         # katta harflar
print(matn.lower())          # kichik harflar
print(matn.strip())           # bo'sh joylarni olib tashlash
print(matn.replace("Salom", "Xayr"))
print(matn.split(","))          # ro'yxatga bo'lish
print(len(matn))                  # uzunligi
print("Dunyo" in matn)              # True — tekshirish
```

## Yangi zamonaviy imkoniyat — f-string ichida formatlash va `=` belgisi

Python 3.8+ da f-string ichida `=` belgisi orqali o'zgaruvchi nomi va qiymatini birga chiqarish mumkin — bu debugging uchun juda qulay:

```python
yosh = 25
print(f"{yosh=}")     # yosh=25
```

Sonlarni formatlash:

```python
narx = 1234567.891
print(f"{narx:,.2f}")     # 1,234,567.89
```

## String — o'zgarmas (immutable)

```python
soz = "salom"
# soz[0] = "S"     # XATOLIK! stringni to'g'ridan-to'g'ri o'zgartirib bo'lmaydi
soz = "S" + soz[1:]   # yangi string yaratish orqali
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ism va familiyani alohida o'zgaruvchiga yozib, f-string orqali "To'liq ism: ..." deb chiqaring.
2. Berilgan matnni katta va kichik harflarga aylantirib chiqaring.
3. Matn uzunligini (`len()`) chiqaring.
4. Matnni teskari tartibda (`[::-1]`) chiqaring.
5. Matnda muayyan so'z borligini `in` operatori orqali tekshiring.
6. Ism va yoshni f-string yordamida bitta gapga birlashtiring.
7. Berilgan gapdagi bo'sh joylarni olib tashlang (`.strip()`).
8. Berilgan matndagi bitta so'zni boshqasiga almashtiring (`.replace()`).

🟡 **O'rta (9-15)**

9. Foydalanuvchidan email so'rang, uni `@` belgisi bo'yicha ikkiga (`.split("@")`) bo'lib, ikkala qismini alohida chiqaring.
10. Berilgan gapdagi so'zlar sonini (`.split()` orqali) hisoblang.
11. Berilgan so'zning palindrom (old-orqasiga bir xil o'qiladigan) ekanligini tekshiring.
12. Ism va familiyadan foydalanuvchi nomi (username) generatsiya qiling: kichik harflarda, orasida nuqta bilan (masalan "ali.karimov").
13. Berilgan matndagi har bir so'zning bosh harfini katta qiling (`.title()` ishlatmasdan, qo'lda).
14. f-string bilan narxni minglik ajratkich va 2 xonali kasr bilan chiqaring.
15. Berilgan matnda muayyan harf nechta marta uchrashini (`.count()`) hisoblang.

🔴 **Qiyin (16-20)**

16. Parolni "yashirish" funksiyasi — faqat birinchi va oxirgi belgini ko'rsatib, qolganini `*` bilan almashtiring (masalan "parol123" -> "p******3").
17. Berilgan matndagi unli va undosh harflar sonini alohida-alohida hisoblang.
18. Ism-familiyadan "inisiallar" (bosh harflar) yasang (masalan "Ali Karimov" -> "A.K.").
19. Berilgan gapni so'zlarga bo'lib, ularni teskari tartibda (oxirgi so'zdan birinchisigacha) birlashtirib chiqaring.
20. Oddiy "matn shifrlash" — har bir harfni alifbo bo'yicha 3 pozitsiyaga siljitib chiqaruvchi dastur yozing (faqat lotin harflari uchun, Caesar shifri).

---

**Oldingi mavzu:** [03 — O'zgaruvchilar](./03_ozgaruvchilar.md)
**Keyingi mavzu:** [05 — Sonlar](./05_sonlar.md)
