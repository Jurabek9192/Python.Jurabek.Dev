# MATNLAR (STRING) VA METODLARI

## String nima?

**String** (matn) — qo'shtirnoq (`" "`) yoki bittirnoq (`' '`) ichiga olingan belgilar ketma-ketligi. Python'da ikkalasi ham bir xil ishlaydi, farqi yo'q.

```python
ism1 = "Nodira"
ism2 = 'Nodira'
print(ism1 == ism2)   # True
```

Agar matn ichida tirnoq ishlatish kerak bo'lsa, tashqi va ichki tirnoqlarni farqlash kerak:

```python
gap = "U menga: 'Salom' dedi"
gap2 = 'U menga: "Salom" dedi'
print(gap)
print(gap2)
```

Ko'p qatorli matn uchun uchta tirnoq ishlatiladi:

```python
matn = """Bu birinchi qator.
Bu ikkinchi qator."""
print(matn)
```

## Stringlarni birlashtirish (concatenation)

```python
ism = "Sardor"
familiya = "Aliyev"
tolik = ism + " " + familiya
print(tolik)
```

```
Sardor Aliyev
```

**Diqqat:** `+` operatori bilan faqat string'ni string bilan birlashtirish mumkin. Sonni to'g'ridan-to'g'ri birlashtirib bo'lmaydi:

```python
yosh = 20
# print("Yoshim: " + yosh)     # XATOLIK! int'ni str bilan qo'shib bo'lmaydi
print("Yoshim: " + str(yosh))  # to'g'ri — avval str() ga aylantirildi
```

## f-string — zamonaviy formatlash usuli

Matn ichiga o'zgaruvchi qiymatlarini kiritishning eng qulay yo'li — **f-string**:

```python
ism = "Malika"
yosh = 19

print(f"Mening ismim {ism}, yoshim {yosh}")
print(f"Ikki yildan keyin {yosh + 2} yoshda bo'laman")
```

```
Mening ismim Malika, yoshim 19
Ikki yildan keyin 21 yoshda bo'laman
```

f-string ichida istalgan Python ifodasi (hisob-kitob, funksiya chaqiruvi) ishlatilishi mumkin — bu uni `+` orqali birlashtirishdan ancha qulay va toza qiladi.

## Stringning indekslanishi

Har bir belgi (harf) stringda o'z **indeksi** (o'rni)ga ega, sanoq `0` dan boshlanadi:

```python
soz = "Python"
#      P  y  t  h  o  n
#      0  1  2  3  4  5
#     -6 -5 -4 -3 -2 -1

print(soz[0])    # P
print(soz[5])    # n
print(soz[-1])   # n  (охиридан биринчи)
print(soz[-2])   # o  (охиридан иккинчи)
```

## Kesish (slicing)

Stringning bir qismini olish uchun `[boshlanish:tugash]` sintaksisi ishlatiladi (`tugash` indeksi kiritilmaydi):

```python
soz = "Dasturlash"

print(soz[0:4])    # Dast
print(soz[4:])      # urlash  (4-indeksdan oxirigacha)
print(soz[:4])      # Dast    (boshidan 4-indeksgacha)
print(soz[:])       # Dasturlash  (butun matn)
print(soz[::2])     # Dsurah  (har 2-belgidan)
print(soz[::-1])    # halsrutsaD  (teskari tartibda)
```

## String uzunligi

```python
soz = "Toshkent"
print(len(soz))     # 8
```

## Muhim string metodlari

Python stringlar bilan ishlash uchun ko'plab tayyor **metodlar**ni taqdim etadi. Metod — obyektga tegishli funksiya bo'lib, `.` orqali chaqiriladi.

```python
matn = "  Salom, Dunyo!  "

print(matn.upper())         # "  SALOM, DUNYO!  "     — katta harflarga
print(matn.lower())         # "  salom, dunyo!  "     — kichik harflarga
print(matn.strip())         # "Salom, Dunyo!"          — bo'sh joylarni olib tashlash
print(matn.title())         # "  Salom, Dunyo!  "      — har so'zning bosh harfi katta
```

```python
soz = "Men Python o'rganyapman"

print(soz.replace("Python", "JavaScript"))   # almashtirish
print(soz.split())                            # ["Men", "Python", "o'rganyapman"] — ro'yxatga bo'lish
print(soz.find("Python"))                     # 4 — qidirilgan matn boshlanadigan indeks
print(soz.count("a"))                          # nechta "a" borligini sanaydi
print(soz.startswith("Men"))                   # True
print(soz.endswith("man"))                     # True
```

## split() va join() — bog'liq juftlik

`split()` matnni ro'yxatga bo'lsa, `join()` ro'yxatni matnga birlashtiradi — bular bir-birining teskarisi:

```python
gap = "olma,uzum,anor"
royxat = gap.split(",")
print(royxat)               # ['olma', 'uzum', 'anor']

qayta = "-".join(royxat)
print(qayta)                 # olma-uzum-anor
```

## String tekshiruv metodlari

Bu metodlar `True`/`False` qaytaradi:

```python
print("12345".isdigit())     # True — faqat raqamlardan iboratmi
print("Python".isalpha())    # True — faqat harflardan iboratmi
print("Python3".isalnum())   # True — harf va raqamlardan iboratmi
print("   ".isspace())        # True — faqat bo'sh joylardan iboratmi
print("PYTHON".isupper())     # True — barchasi katta harfmi
print("python".islower())     # True — barchasi kichik harfmi
```

Bu metodlar amaliyotda foydalanuvchi kiritgan ma'lumotni tekshirishda juda foydali, masalan telefon raqami faqat sonlardan iboratligini tekshirishda.

## Stringlar o'zgarmasdir (immutable)

Muhim qoida: Python'da stringni **to'g'ridan-to'g'ri o'zgartirib bo'lmaydi**. Har qanday "o'zgartirish" metodi aslida yangi string yaratadi:

```python
soz = "salom"
# soz[0] = "S"    # XATOLIK! stringni indeks orqali o'zgartirib bo'lmaydi

soz = "S" + soz[1:]   # bu ishlaydi — yangi string yaratildi
print(soz)              # Salom
```

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. Foydalanuvchidan ism va familiyani alohida so'rab, f-string yordamida "Sizning to'liq ismingiz: [ism] [familiya]" deb chiqaring.
2. Foydalanuvchi kiritgan matnni katta harflarga, so'ng kichik harflarga aylantirib chiqaring.
3. Foydalanuvchi kiritgan matn nechta harfdan iboratligini (`len()`) chiqaring.
4. Berilgan so'zni teskari tartibda chiqaring (slicing `[::-1]` dan foydalaning).
5. Foydalanuvchi kiritgan gapda muayyan bir so'z nechta marta uchrashini (`.count()`) toping.

🟡 **O'rta daraja**

6. Foydalanuvchidan email manzilini so'rang va u `@` belgisini o'z ichiga olishini tekshiring (`in` operatoridan yoki `.find()` dan foydalaning).
7. Foydalanuvchi kiritgan gapdagi so'zlar sonini (`.split()` orqali) hisoblang.
8. Berilgan matndagi barcha bo'sh joylarni pastki chiziq (`_`) bilan almashtiruvchi dastur yozing.
9. Palindrom tekshiruvchi dastur yozing — so'z old-orqasiga bir xil o'qiladimi (masalan "ANNA"). Katta-kichik harflarni hisobga olmang.

---
