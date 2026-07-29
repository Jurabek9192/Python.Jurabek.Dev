# YAKUNIY LOYIHA — KONSOL ASOSIDAGI "TALABALAR JURNALI"

## Loyiha haqida

Tabriklaymiz! Siz Python asoslarining barcha muhim mavzularini o'rgandingiz: o'zgaruvchilar, ma'lumot turlari, shartlar, tsikllar, funksiyalar, list/dict/set/tuple, modullar. Endi vaqt keldi — bularning barchasini **bitta real loyihada** birlashtiramiz.

Ushbu mavzuda biz konsolda ishlaydigan **"Talabalar Jurnali"** dasturini birgalikda quramiz — bu dastur talabalarni ro'yxatga oladi, baholarini saqlaydi va statistikani ko'rsatadi.

## Loyihada ishlatiladigan mavzular

- ✅ Dictionary — har bir talaba ma'lumotini saqlash uchun
- ✅ List — barcha talabalar ro'yxatini saqlash uchun
- ✅ Funksiyalar — har bir amal (qo'shish, o'chirish, ko'rish) uchun
- ✅ while tsikli — asosiy menyu uchun
- ✅ if/elif/else — foydalanuvchi tanlovini boshqarish uchun
- ✅ f-string — chiroyli formatlash uchun
- ✅ List comprehension — filtrlash uchun

## Bosqichma-bosqich qurish

### 1-qadam: Ma'lumotlarni saqlash strukturasi

```python
talabalar = []   # har bir talaba dictionary bo'lib, shu list ichida saqlanadi

# misol struktura: {"ism": "Ali", "baho": 85}
```

### 2-qadam: Talaba qo'shish funksiyasi

```python
def talaba_qoshish():
    ism = input("Talaba ismini kiriting: ")
    try:
        baho = int(input("Bahoni kiriting (0-100): "))
    except ValueError:
        print("Xato! Baho son bo'lishi kerak.")
        return

    if not (0 <= baho <= 100):
        print("Xato! Baho 0 dan 100 gacha bo'lishi kerak.")
        return

    talabalar.append({"ism": ism, "baho": baho})
    print(f"{ism} muvaffaqiyatli qo'shildi!")
```

*(Diqqat: `try/except` — xatoliklarni ushlash usuli, buni Kitob 2'da chuqur o'rganamiz. Hozircha uni "xavfsiz kod yozish" vositasi sifatida qabul qiling.)*

### 3-qadam: Barcha talabalarni ko'rsatish funksiyasi

```python
def talabalar_royxati():
    if not talabalar:
        print("Hozircha talabalar ro'yxati bo'sh")
        return

    print("\n" + "-" * 30)
    for i, talaba in enumerate(talabalar, start=1):
        print(f"{i}. {talaba['ism']} — {talaba['baho']} ball")
    print("-" * 30)
```

### 4-qadam: Statistika funksiyasi

```python
def statistika():
    if not talabalar:
        print("Statistika uchun talabalar mavjud emas")
        return

    baholar = [t["baho"] for t in talabalar]
    ortacha = sum(baholar) / len(baholar)

    eng_yaxshi = max(talabalar, key=lambda t: t["baho"])
    eng_past = min(talabalar, key=lambda t: t["baho"])

    otganlar = [t for t in talabalar if t["baho"] >= 60]

    print("\n📊 STATISTIKA")
    print(f"Jami talabalar: {len(talabalar)}")
    print(f"O'rtacha baho: {ortacha:.2f}")
    print(f"Eng yuqori baho: {eng_yaxshi['ism']} — {eng_yaxshi['baho']}")
    print(f"Eng past baho: {eng_past['ism']} — {eng_past['baho']}")
    print(f"O'tganlar soni (60+): {len(otganlar)} / {len(talabalar)}")
```

### 5-qadam: Talabani o'chirish funksiyasi

```python
def talaba_ochirish():
    ism = input("O'chiriladigan talaba ismini kiriting: ")
    for talaba in talabalar:
        if talaba["ism"].lower() == ism.lower():
            talabalar.remove(talaba)
            print(f"{ism} ro'yxatdan o'chirildi")
            return
    print(f"{ism} nomli talaba topilmadi")
```

### 6-qadam: Asosiy menyu

```python
def menyu():
    while True:
        print("\n===== TALABALAR JURNALI =====")
        print("1 - Talaba qo'shish")
        print("2 - Talabalar ro'yxati")
        print("3 - Statistika")
        print("4 - Talabani o'chirish")
        print("5 - Chiqish")

        tanlov = input("Tanlovingiz (1-5): ")

        if tanlov == "1":
            talaba_qoshish()
        elif tanlov == "2":
            talabalar_royxati()
        elif tanlov == "3":
            statistika()
        elif tanlov == "4":
            talaba_ochirish()
        elif tanlov == "5":
            print("Dastur yopilmoqda. Xayr!")
            break
        else:
            print("Noto'g'ri tanlov, 1 dan 5 gacha son kiriting")
```

### 7-qadam: Dasturni ishga tushirish

```python
if __name__ == "__main__":
    menyu()
```

## To'liq kod (`talabalar_jurnali.py`)

Yuqoridagi barcha bo'laklarni bitta faylga jamlasangiz, to'liq ishlaydigan dastur hosil bo'ladi. Buni o'zingiz VS Code'da yozib, sinab ko'ring — bu eng samarali o'rganish usuli.

## Namunaviy ishlash jarayoni

```
===== TALABALAR JURNALI =====
1 - Talaba qo'shish
2 - Talabalar ro'yxati
3 - Statistika
4 - Talabani o'chirish
5 - Chiqish
Tanlovingiz (1-5): 1
Talaba ismini kiriting: Zarina
Bahoni kiriting (0-100): 92
Zarina muvaffaqiyatli qo'shildi!

===== TALABALAR JURNALI =====
Tanlovingiz (1-5): 3

📊 STATISTIKA
Jami talabalar: 1
O'rtacha baho: 92.00
Eng yuqori baho: Zarina — 92
Eng past baho: Zarina — 92
O'tganlar soni (60+): 1 / 1
```

---

## 🎯 Loyihani kengaytirish vazifalari

Yakuniy loyihani o'zlashtirganingizdan so'ng, uni quyidagi qo'shimchalar bilan mustaqil kengaytiring — bu Kitob 2'ga o'tish uchun ajoyib tayyorgarlik bo'ladi:

🟢 **Oson darajadagi kengaytmalar**

1. Har bir talabaga yosh maydonini ham qo'shing.
2. Talabalarni baho bo'yicha kamayish tartibida saralab ko'rsatuvchi yangi menyu bandini qo'shing.
3. Ism bo'yicha talaba qidiruvi funksiyasini qo'shing.

🟡 **O'rta darajadagi kengaytmalar**

4. Har bir talabaga bir nechta baho (masalan fanlar bo'yicha) saqlash imkonini qo'shing — bunda `baho` maydoni endi bitta son emas, list bo'ladi.
5. Bahoga qarab avtomatik harf baho (A/B/C/D/F) hisoblab beruvchi funksiya qo'shing.
6. "Guruh bo'yicha filtrlash" funksiyasini qo'shing — har bir talaba endi guruh nomiga ham ega bo'lsin.

🔴 **Murakkabroq kengaytmalar**

7. Ma'lumotlarni dastur yopilganda yo'qotmaslik uchun, ularni oddiy matn faylga (`.txt`) saqlash va dastur qayta ochilganda o'sha fayldan o'qib olishni qo'shing (bu Kitob 2'dagi "Fayllar bilan ishlash" mavzusiga bevosita tayyorgarlik bo'ladi).

---

## Kitob 1 yakunlandi! 🎉

Siz Python dasturlash tilining asosiy qurilish bloklarini — o'zgaruvchilar, ma'lumot turlari, shartlar, tsikllar va funksiyalarni — muvaffaqiyatli o'zlashtirdingiz. Bu bilim — dasturlashning har qanday yo'nalishida (veb, sun'iy intellekt, robototexnika, ma'lumotlar tahlili) mustahkam poydevor bo'lib xizmat qiladi.

**Keyingi qadam: Kitob 2 — OOP, Fayllar va Xatoliklar.** Bu kitobda siz Python'ning eng kuchli vositalaridan biri bo'lgan **Object-Oriented Programming (OOP)** bilan tanishasiz, fayllar bilan ishlashni va dasturingizni xatoliklardan himoya qilishni o'rganasiz.

---

**Oldingi mavzu:** [19 — Modullar va paketlar (asoslar)](./19_modullar_paketlar.md)
**Keyingi kitob:** Kitob 2 — OOP, Fayllar va Xatoliklar → 01-mavzu
