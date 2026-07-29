# BREAK, CONTINUE, PASS

Bu uchta kalit so'z tsikllarning (va ba'zan boshqa strukturalarning) oqimini boshqarish uchun ishlatiladi. Oldingi mavzularda `break` va `continue` bilan qisman tanishgan edik — bu yerda ularni chuqurroq, aniq qoidalar bilan ko'rib chiqamiz.

## break — tsiklni to'liq to'xtatish

`break` — joriy tsiklni **butunlay** to'xtatadi va tsikldan keyingi kodga o'tadi.

```python
for son in range(1, 10):
    if son == 5:
        break
    print(son)

print("Tsikldan chiqildi")
```

```
1
2
3
4
Tsikldan chiqildi
```

Diqqat qiling — `5` chop etilmadi, chunki `break` shart bajarilishi bilanoq darhol tsiklni tark etadi.

## continue — faqat joriy qadamni o'tkazib yuborish

`continue` — tsiklni to'xtatmaydi, faqat **joriy iteratsiyani** tugatib, keyingi elementga o'tadi.

```python
for son in range(1, 10):
    if son == 5:
        continue
    print(son)
```

```
1
2
3
4
6
7
8
9
```

Bu safar `5` shunchaki o'tkazib yuborildi, lekin tsikl davom etdi.

## break vs continue — vizual farq

```
break:     1 2 3 4 [STOP]
continue:  1 2 3 4 [5 o'tkazildi] 6 7 8 9
```

## pass — hech narsa qilmaslik

`pass` — Python'da "bu yerda hozircha hech narsa yo'q, lekin sintaktik jihatdan bo'sh qoldirib bo'lmaydi" degan ma'noni bildiradi. U hech qanday amal bajarmaydi, shunchaki joy egallaydi.

```python
for son in range(5):
    if son == 3:
        pass          # hozircha hech narsa qilinmaydi
    print(son)
```

```
0
1
2
3
4
```

### pass qachon kerak bo'ladi?

Python'da bo'sh blok (masalan bo'sh `if`, bo'sh funksiya) yozib bo'lmaydi — bu xatolik beradi:

```python
def kelajakda_yoziladi():
    # hali kod yozilmagan
    # XATOLIK: IndentationError

def kelajakda_yoziladi():
    pass    # to'g'ri — funksiya "bo'sh" holda ham ishlaydi
```

Bu ayniqsa loyihani rejalashtirishda, keyinroq to'ldiriladigan funksiya yoki klasslar uchun "joy band qilib qo'yish"da foydali:

```python
def foydalanuvchi_qoshish():
    pass

def foydalanuvchi_ochirish():
    pass

def foydalanuvchi_royxati():
    pass

print("Struktura tayyor, funksiyalar keyinroq to'ldiriladi")
```

## Ichma-ich tsikllarda break

**Muhim qoida:** `break` faqat **eng yaqin (ichki)** tsiklni to'xtatadi, tashqi tsiklga ta'sir qilmaydi:

```python
for i in range(3):
    for j in range(3):
        if j == 1:
            break        # faqat ichki tsikl to'xtaydi
        print(f"i={i}, j={j}")
```

```
i=0, j=0
i=1, j=0
i=2, j=0
```

Agar ikkala tsiklni ham to'xtatish kerak bo'lsa, odatda maxsus bayroq (flag) o'zgaruvchi yoki funksiya ichiga o'rab, `return` ishlatiladi:

```python
def qidir():
    for i in range(3):
        for j in range(3):
            if i == 1 and j == 1:
                return f"Topildi: i={i}, j={j}"
    return "Topilmadi"

print(qidir())
```

## Amaliy misol: taqiqlangan so'zlarni tekshirish

```python
taqiqlangan = ["yomon", "haqorat", "spam"]
xabar = "Bu yomon xabar emas, oddiy matn"

topildi = False
for soz in taqiqlangan:
    if soz in xabar:
        print(f"Taqiqlangan so'z topildi: {soz}")
        topildi = True
        break

if not topildi:
    print("Xabar toza")
```

## Amaliy misol: menyudagi noto'g'ri kiritishlarni o'tkazib yuborish

```python
royxat = ["olma", "", "banan", None, "uzum", ""]

for element in royxat:
    if not element:          # bo'sh yoki None bo'lsa
        continue
    print(f"Mahsulot: {element}")
```

```
Mahsulot: olma
Mahsulot: banan
Mahsulot: uzum
```

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. 1 dan 20 gacha sonlarni chop eting, lekin 15 ga yetganda tsiklni to'xtating (`break`).
2. 1 dan 20 gacha sonlarni chop eting, lekin 5 ga bo'linadigan sonlarni o'tkazib yuboring (`continue`).
3. Bo'sh funksiya yarating (`pass` yordamida) va uni chaqirib ko'ring — xatolik bermasligiga ishonch hosil qiling.

🟡 **O'rta daraja**

4. Listda berilgan sonlar orasidan birinchi manfiy sonni topib, uni topilgach tsiklni to'xtating. Agar manfiy son bo'lmasa, "Manfiy son yo'q" deb chiqaring (`for...else` dan foydalaning).
5. Foydalanuvchidan ketma-ket sonlar kiritilsin ("stop" kiritilguncha). Agar manfiy son kiritilsa, uni hisobga olmasdan (continue) davom eting, "stop" kiritilganda esa to'xtang (break).
6. Ichma-ich tsikl yordamida 5x5 jadval yarating, lekin diagonal elementlarni (i==j) o'tkazib yuboring.

🔴 **Murakkabroq**

7. Ikki o'lchamli matritsada (list ichida list) berilgan sonni qidiring. Topilgan zahoti uning qatori va ustunini chop etib, ikkala tsikldan ham chiqing (funksiya va `return` yordamida).

---

**Oldingi mavzu:** [13 — for tsikli](./13_for_tsikli.md)
**Keyingi mavzu:** [15 — Funksiyalar — asoslar](./15_funksiyalar_asoslar.md)
