# 04 — STRING (MATN)

## String yaratish usullari

```python
ism1 = "Nodira"
ism2 = 'Nodira'                 # bittirnoq ham ishlaydi — farqi yo'q
kop_qatorli = """Birinchi qator
Ikkinchi qator"""                 # uch tirnoq — ko'p qatorli matn uchun

# tirnoq ichida tirnoq kerak bo'lsa
gap = "U menga: 'Salom' dedi"
gap2 = 'U menga: "Salom" dedi'

# raw string — \ belgisini "xom" holda saqlaydi (masalan fayl yo'llarida)
yol = r"C:\Users\Ali\Desktop"
print(yol)     # C:\Users\Ali\Desktop (backslash o'zgarmaydi)
```

## Birlashtirish va takrorlash

```python
ism = "Sardor"
familiya = "Aliyev"

print(ism + " " + familiya)     # Sardor Aliyev — birlashtirish (+)
print("Ha! " * 3)                  # Ha! Ha! Ha! — takrorlash (*)
```

## f-string — eng qulay formatlash usuli

```python
ism = "Sardor"
yosh = 20

print(f"Ism: {ism}, Yosh: {yosh}")
print(f"Ikki yildan keyin {yosh + 2} yoshda bo'ladi")     # ichida hisob-kitob ham bo'lishi mumkin

# f-string ichida = belgisi (debugging uchun, Python 3.8+)
print(f"{yosh=}")          # yosh=20

# sonlarni formatlash
narx = 1234567.891
print(f"{narx:,.2f}")         # 1,234,567.89 — minglik ajratkich + 2 xona
print(f"{75:>10}")               # o'ngga tekislash, 10 belgi kenglikda
print(f"{75:<10}|")               # chapga tekislash
print(f"{75:^10}|")                # markazga tekislash
print(f"{0.856:.1%}")                # 85.6% — foiz formatida
```

## Eski formatlash usullari (bilish foydali)

```python
# .format() metodi
print("Men {}, {} yoshdaman".format(ism, yosh))
print("Men {0}, {1} yoshdaman, yana {0}".format(ism, yosh))     # indeks orqali qayta ishlatish

# % operatori (eng eski usul)
print("Salom, %s! Sen %d yoshdasan" % (ism, yosh))
```

## Indekslash va kesish (slicing)

```python
soz = "Python"
#      P  y  t  h  o  n
#      0  1  2  3  4  5
#     -6 -5 -4 -3 -2 -1

print(soz[0])          # P
print(soz[-1])           # n (oxirgi)
print(soz[0:4])            # Pyth
print(soz[2:])               # thon
print(soz[:4])                 # Pyth
print(soz[::2])                  # Pto (har 2-belgidan)
print(soz[::-1])                   # nohtyP (teskari)
print(soz[1:5:2])                    # yh
```

## String — TO'LIQ METODLAR RO'YXATI

### Katta/kichik harflarga aylantirish

```python
matn = "salom Dunyo"

print(matn.upper())          # SALOM DUNYO — barchasi katta
print(matn.lower())            # salom dunyo — barchasi kichik
print(matn.title())              # Salom Dunyo — har so'z bosh harfi katta
print(matn.capitalize())           # Salom dunyo — faqat birinchi harf katta
print(matn.swapcase())               # SALOM dUNYO — katta<->kichik almashadi
print(matn.casefold())                 # kuchliroq lower() — turli tillar uchun
```

### Bo'sh joylarni boshqarish

```python
matn = "   Salom, Dunyo!   "

print(matn.strip())          # "Salom, Dunyo!" — ikkala tarafdan
print(matn.lstrip())            # "Salom, Dunyo!   " — chapdan
print(matn.rstrip())              # "   Salom, Dunyo!" — o'ngdan
print(matn.strip(" !"))             # belgilarni ham ko'rsatish mumkin
```

### Qidirish va tekshirish

```python
matn = "Men Python o'rganyapman"

print(matn.find("Python"))         # 4 — topilgan indeks (topilmasa -1)
print(matn.rfind("a"))                # oxirgi "a" indeksi
print(matn.index("Python"))             # 4 — find() bilan bir xil, lekin topilmasa XATOLIK beradi
print(matn.count("a"))                    # nechta "a" borligi
print("Python" in matn)                     # True — eng ko'p ishlatiladigan usul
print(matn.startswith("Men"))                 # True
print(matn.endswith("man"))                     # True
print(matn.startswith(("Men", "Biz")))            # True — bir nechta variant tuple bilan
```

### Almashtirish va bo'lish

```python
matn = "olma,banan,uzum"

print(matn.replace(",", " - "))            # olma - banan - uzum
print(matn.replace(",", " - ", 1))            # faqat birinchi marta almashtiradi

print(matn.split(","))                          # ['olma', 'banan', 'uzum']
print(matn.rsplit(",", 1))                        # o'ngdan boshlab, faqat 1 marta bo'ladi
print("bir ikki   uch".split())                     # bo'sh joy bo'yicha, ortiqcha joylarni e'tiborsiz qoldiradi
print("qator1\nqator2\nqator3".splitlines())          # ['qator1', 'qator2', 'qator3']

royxat = ["olma", "banan", "uzum"]
print("-".join(royxat))                                 # olma-banan-uzum — split()ning teskarisi
print(", ".join(royxat))                                  # olma, banan, uzum

print("  salom  dunyo  ".partition("salom"))                # ('  ', 'salom', '  dunyo  ') — 3 qismga bo'ladi
```

### Tekshiruvchi (is...) metodlar — barchasi True/False qaytaradi

```python
print("12345".isdigit())        # True — faqat raqamlardanmi
print("12345".isnumeric())         # True — raqamlarga yaqin (kasr, rim raqamlari ham)
print("Python".isalpha())            # True — faqat harflardanmi
print("Python3".isalnum())             # True — harf+raqamdanmi
print("   ".isspace())                   # True — faqat bo'sh joydanmi
print("PYTHON".isupper())                  # True — barchasi katta harfmi
print("python".islower())                    # True — barchasi kichik harfmi
print("Salom Dunyo".istitle())                 # True — har so'z Bosh harf bilanmi
print("mening_ismim".isidentifier())             # True — o'zgaruvchi nomi sifatida yaroqlimi
```

### Uzunlik, kenglik va to'ldirish

```python
soz = "42"

print(len(soz))                # 2
print(soz.zfill(5))               # 00042 — nol bilan to'ldirish
print(soz.center(10, "*"))          # ****42**** — markazga, belgilar bilan
print(soz.ljust(10, "-"))             # 42-------- — chapga tekislab, to'ldirish
print(soz.rjust(10, "-"))               # --------42 — o'ngga tekislab, to'ldirish
```

### Almashtirish jadvali — translate()

```python
jadval = str.maketrans("aeiou", "12345")
print("salom".translate(jadval))     # s1l4m — unlilarni raqamga almashtiradi
```

## String — o'zgarmas (immutable)

```python
soz = "salom"
# soz[0] = "S"        # XATOLIK! stringni to'g'ridan-to'g'ri o'zgartirib bo'lmaydi
soz = "S" + soz[1:]      # yechim — yangi string yaratish orqali
```

## String va list orasidagi aylanish

```python
soz = "Python"
harflar = list(soz)          # ['P', 'y', 't', 'h', 'o', 'n']
qayta = "".join(harflar)       # "Python"
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ism va familiyani alohida o'zgaruvchiga yozib, f-string orqali "To'liq ism: ..." deb chiqaring.
2. Berilgan matnni `.upper()`, `.lower()`, `.title()`, `.capitalize()` metodlari bilan alohida-alohida chiqaring.
3. Matn uzunligini (`len()`) chiqaring.
4. Matnni teskari tartibda (`[::-1]`) chiqaring.
5. Matnda muayyan so'z borligini `in` operatori orqali tekshiring.
6. `.strip()`, `.lstrip()`, `.rstrip()` farqini bitta matn ustida sinab, izohlab bering.
7. Berilgan matndagi bitta so'zni `.replace()` bilan boshqasiga almashtiring.
8. `.isdigit()`, `.isalpha()`, `.isalnum()` metodlarini 3 xil matn ustida sinab ko'ring.

🟡 **O'rta (9-15)**

9. Foydalanuvchidan email so'rang, uni `@` bo'yicha `.split()` bilan ikkiga bo'lib chiqaring.
10. Berilgan gapdagi so'zlar sonini `.split()` orqali hisoblang.
11. `.find()` va `.index()` farqini — mavjud bo'lmagan so'z bilan sinab, natijalarini solishtiring.
12. Ism va familiyadan `.lower()` va `.join()` yordamida username generatsiya qiling (masalan "ali.karimov").
13. `.zfill()` yordamida sonni 5 xonali qilib, nol bilan to'ldiring (masalan "7" -> "00007").
14. `.center()`, `.ljust()`, `.rjust()` metodlarini sinab, natijalarini solishtiring.
15. `str.maketrans()` va `.translate()` yordamida oddiy harf almashtirish jadvali yasang.

🔴 **Qiyin (16-20)**

16. Parolni "yashirish" funksiyasi — faqat birinchi va oxirgi belgini ko'rsatib, qolganini `*` bilan almashtiring.
17. `.count()` yordamida berilgan matndagi har bir unli harf nechta marta uchraganini alohida-alohida hisoblang.
18. Ism-familiyadan `.split()` va list comprehension bilan "inisiallar" (A.K.) yasang.
19. `.partition()` metodidan foydalanib, email manzilini "foydalanuvchi nomi" va "domen" qismlariga ajrating.
20. Oddiy Caesar shifrini yozing — har bir harfni alifbo bo'yicha 3 pozitsiyaga siljiting (`ord()` va `chr()` funksiyalaridan foydalaning).

---

**Oldingi mavzu:** [03 — O'zgaruvchilar](./03_ozgaruvchilar.md)
**Keyingi mavzu:** [05 — Sonlar](./05_sonlar.md)
