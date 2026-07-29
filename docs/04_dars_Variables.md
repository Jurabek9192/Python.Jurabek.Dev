# PYTHON BILAN TANISHUV

## Python nima?

**Python** — 1991-yilda Gvido van Rossum tomonidan yaratilgan, yuqori darajadagi (high-level), umumiy maqsadli dasturlash tili. U o'zining sodda va o'qish uchun qulay sintaksisi bilan mashhur — shu sababli ko'plab boshlang'ich dasturchilar aynan Python bilan o'z yo'lini boshlaydi.

Python bugungi kunda quyidagi sohalarda keng qo'llaniladi:

- **Web dasturlash** — Django, Flask kabi freymvorklar yordamida
- **Ma'lumotlar tahlili va sun'iy intellekt** — Pandas, NumPy, TensorFlow, PyTorch
- **Avtomatlashtirish (Automation)** — kundalik ishlarni robotlashtirish, skriptlar yozish
- **O'yin dasturlash** — Pygame kabi kutubxonalar orqali
- **Robototexnika** — Arduino, Raspberry Pi bilan integratsiya

Python nomi aslida ilon turi emas, balki Gvido van Rossumning sevimli komediya shousi *"Monty Python's Flying Circus"* dan olingan.

## Nega aynan Python?

1. **Sodda sintaksis** — kod inson tiliga yaqin, o'qish va tushunish oson
2. **Katta jamoat (community)** — muammoga duch kelsangiz, internetda deyarli har doim javob topiladi
3. **Ko'plab tayyor kutubxonalar** — g'ildirakni qayta ixtiro qilish shart emas
4. **Ko'p platformali** — Windows, macOS, Linux'da bir xil ishlaydi
5. **Keng qo'llanilish sohasi** — bitta til bilan veb-sayt ham, sun'iy intellekt modeli ham yozish mumkin

## Python'ni o'rnatish

1. [python.org](https://www.python.org/downloads/) saytiga kiring
2. O'z operatsion tizimingizga mos versiyani yuklab oling (eng so'nggi barqaror versiya tavsiya etiladi)
3. O'rnatish paytida **"Add Python to PATH"** katagini albatta belgilang — aks holda terminal orqali Python'ni chaqira olmaysiz

O'rnatishni tekshirish uchun terminal (Windows'da CMD yoki PowerShell) oching va yozing:

```bash
python --version
```

```
Python 3.12.4
```

Agar versiya raqami chiqsa — demak Python muvaffaqiyatli o'rnatilgan.

## IDE — dasturlash muhiti

Kod yozish uchun matn muharriri (IDE — Integrated Development Environment) kerak bo'ladi. Eng ko'p tavsiya etiladiganlar:

| IDE | Xususiyati |
|---|---|
| **VS Code** | Bepul, yengil, ko'plab kengaytmalar bilan — eng ommabop tanlov |
| **PyCharm** | Python uchun maxsus yaratilgan, professional funksiyalarga boy |
| **Jupyter Notebook** | Ma'lumotlar tahlili va o'rganish uchun qulay, kod bo'lak-bo'lak ishlaydi |

Ushbu kursda biz **VS Code** dan foydalanamiz.

## Birinchi dastur

Dasturlashni o'rganishning an'anaviy birinchi qadami — ekranga "Salom, Dunyo!" degan matnni chiqarish.

```python
print("Salom, Dunyo!")
```

```
Salom, Dunyo!
```

Tahlil qilaylik:

- `print()` — Python'ning **funksiyasi** bo'lib, qavs ichidagi narsani ekranga chiqaradi
- `"Salom, Dunyo!"` — bu matn (string) ma'lumot turi, shuning uchun qo'shtirnoq ichiga olingan

## Kodni ishga tushirish

Kodni ikki xil usulda ishga tushirish mumkin:

**1-usul: Fayl orqali**

`salom.py` nomli fayl yarating, ichiga kodni yozing va terminalda quyidagini bajaring:

```bash
python salom.py
```

**2-usul: Interaktiv rejim (interpretator)**

Terminalga shunchaki `python` deb yozib Enter bosing — bu sizni Python'ning interaktiv muhitiga olib kiradi, u yerda har bir qatorni alohida sinab ko'rishingiz mumkin.

## Izohlar (comments)

Kod ichida izoh qoldirish uchun `#` belgisidan foydalaniladi. Izohlar Python tomonidan bajarilmaydi — ular faqat dasturchi uchun tushuntirish maqsadida yoziladi.

```python
# Bu birinchi dasturim
print("Salom, Dunyo!")  # ekranga salom chiqaradi
```

Ko'p qatorli izoh uchun uchta qo'shtirnoqdan foydalaniladi:

```python
"""
Bu ko'p qatorli izoh.
Loyiha haqida umumiy ma'lumot yozish uchun qulay.
"""
print("Ishladi!")
```

## Python'ning ishlash mantig'i

Python — **interpretatsiya qilinuvchi (interpreted)** til. Bu shuni anglatadiki, kod C++ yoki Java kabi avval to'liq mashina koduga aylantirilmaydi, balki qator-qator, yuqoridan pastga qarab, darhol bajariladi. Shu sababli xatolik bo'lsa, dastur o'sha qatorgacha ishlaydi va keyin to'xtaydi.

```python
print("Birinchi qator")
print("Ikkinchi qator")
print(1 / 0)  # bu yerda xatolik yuz beradi
print("Bu qator hech qachon ishlamaydi")
```

```
Birinchi qator
Ikkinchi qator
ZeroDivisionError: division by zero
```

## Xatoliklar bilan tanishuv

Dasturlashda xatolik (error) qilishdan qo'rqmang — bu jarayonning tabiiy qismi. Python xatolik yuz berganda sizga qaysi qatorda va nima sababdan xatolik borligini aniq ko'rsatadi. Buni **traceback** deyiladi. Uni o'qishni o'rganish — dasturchilik mahoratining muhim qismi.

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. Ekranga o'z ismingiz va familiyangizni chiqaruvchi dastur yozing.
2. Ekranga 3 qatorlik she'r yoki maqol chiqaring (har bir qator alohida `print()` orqali).
3. `print()` funksiyasidan foydalanib, ekranda kichik "rasm" chizing (masalan `*` belgilaridan uchburchak).
4. Dasturingizga kamida 2 ta izoh (comment) qo'shing — birini bir qatorlik, birini ko'p qatorlik qilib.
5. Terminalda `python --version` va `pip --version` buyruqlarini bajarib, natijalarini yozib qo'ying.

🟡 **O'rta daraja**

6. Qasddan xatolik keltirib chiqaruvchi kod yozing (masalan noto'g'ri yozilgan funksiya nomi) va chiqqan xatolik xabarini (traceback'ni) tahlil qiling — u sizga nima haqida gapiryapti?
7. `print()` funksiyasining `sep` va `end` parametrlarini internetdan qidirib toping va ular yordamida natijani turlicha formatlashga urinib ko'ring.

---

