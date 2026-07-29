# 01 — DASTURLASH VA PYTHON BILAN TANISHUV

## Dasturlash nima?

**Dasturlash** — kompyuterga bosqichma-bosqich ko'rsatma (instruksiya) berish jarayoni. Kompyuter o'zi hech narsani "o'ylab" qilmaydi — u faqat unga aniq va tartibli tarzda berilgan buyruqlarni bajaradi. Dasturchi vazifasi — masalani kompyuter tushunadigan, aniq qadamlarga bo'lib berish.

## Nega Python?

- **Sodda va tushunarli sintaksis** — kod deyarli inson tiliga o'xshaydi
- **Keng qo'llanilish sohasi** — veb-saytlar, sun'iy intellekt, ma'lumotlar tahlili, robototexnika, o'yinlar
- **Katta jamoat** — muammoga duch kelsangiz, javobni internetdan topish oson
- **Bepul va ochiq manba (open source)**

## Kerakli dasturlarni o'rnatish

1. **Python** — [python.org/downloads](https://www.python.org/downloads/) saytidan yuklab oling. O'rnatishda **"Add Python to PATH"** katagini albatta belgilang.
2. **VS Code** — [code.visualstudio.com](https://code.visualstudio.com/) saytidan yuklab oling. Bu — kod yozish uchun matn muharriri.
3. VS Code'da **Python kengaytmasi (extension)**ni o'rnating — bu kodni ranglab ko'rsatish, xatoliklarni oldindan aniqlash kabi qulayliklarni beradi.

O'rnatishni tekshirish uchun terminalda:

```bash
python --version
```

```
Python 3.13.0
```

## Birinchi dasturimiz — "Salom, Dunyo!"

Dasturlashni o'rganishning an'anaviy birinchi qadami:

```python
print("Salom, Dunyo!")
```

```
Salom, Dunyo!
```

Bu bitta qator kod ekranga matn chiqaradi. `print()` — Python'ning **funksiyasi**, u qavs ichidagi narsani ekranga ko'rsatadi.

## Kodni qanday ishga tushiramiz?

1. VS Code'da yangi fayl yarating, nomini `salom.py` deb saqlang (`.py` — Python fayllarining kengaytmasi)
2. Faylga kodni yozing
3. Terminalda faylni ishga tushiring:

```bash
python salom.py
```

## Python — interpretatsiya qilinuvchi til

Python kodi qator-baqator, yuqoridan pastga qarab bajariladi (interpretatsiya qilinadi). Bu — C++ yoki Java kabi avval "kompilyatsiya" qilinadigan tillardan farq qiladi. Shu sababli Python'da kod yozish va sinab ko'rish tezkor va qulay.

## Izohlar (comments)

Kod ichida o'zingiz uchun eslatma yozish uchun `#` belgisi ishlatiladi — bu qatorlar Python tomonidan bajarilmaydi:

```python
# Bu mening birinchi dasturim
print("Salom, Dunyo!")   # ekranga matn chiqaradi
```

## Xatoliklardan qo'rqmang!

Dasturlashda xatolik qilish — jarayonning tabiiy qismi. Har bir tajribali dasturchi ham kuniga o'nlab xatolikka duch keladi. Python xatolik yuz berganda, qaysi qatorda va nima sababdan xato borligini ko'rsatadi — buni **traceback** deyiladi. Buni o'qishni o'rganish — muhim ko'nikma.

```python
print("Salom"
```

```
SyntaxError: '(' was never closed
```

Bu yerda Python bizga aniq aytyapti — qavs yopilmagan.

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. `print()` yordamida ekranga o'z ismingizni chiqaring.
2. Ekranga "Men Python o'rganyapman!" degan xabarni chiqaring.
3. Ketma-ket 3 ta `print()` orqali o'zingiz haqingizda 3 ta jumla chiqaring (ism, yosh, shahar).
4. Bitta `print()` qatoriga izoh (comment) qo'shing.
5. Ko'p qatorli izoh (`"""..."""`) yordamida dasturingiz haqida qisqacha izoh yozing.
6. `print()` yordamida ekranda `*` belgilaridan uchburchak shaklini chizing (5 qator).
7. Terminalda `python --version` buyrug'ini bajarib, natijani skrinshot yoki matn ko'rinishida saqlang.
8. Qasddan xatolik keltirib chiqaradigan kod yozing (masalan qavsni yopmang) va chiqqan xatolikni diqqat bilan o'qing.

🟡 **O'rta (9-15)**

9. Ekranga o'zingiz sevgan she'r yoki maqolning 4 qatorini chiqaring.
10. `print()` yordamida oddiy "vizit karta" chizing — ism, kasb, telefon (ramka ichida, `-` va `|` belgilaridan foydalanib).
11. Bitta faylga 2 ta turli dastur yozing va ularni ketma-ket ishga tushiring.
12. `print("Salom" + " " + "Dunyo")` kodini yozib, natijasini tushuntiring (izoh sifatida yozing).
13. Nima uchun `print(Salom)` (tirnoqsiz) xatolik berishini tushuntirib, buni tuzating.
14. Terminal orqali joriy papkadagi barcha `.py` fayllarni ko'ring (`dir` yoki `ls` buyrug'i bilan).
15. `python` so'zini terminalga yozib, interaktiv rejimga kiring va u yerda `print("test")` ni sinab ko'ring, so'ng `exit()` bilan chiqing.

🔴 **Qiyin (16-20)**

16. Ekranda ASCII-art uslubida o'z ismingizni katta harflar bilan (har bir harfni `*` yoki boshqa belgidan yasab) chizing.
17. Ikkita xato (masalan yopilmagan qavs va noto'g'ri tirnoq) bo'lgan kod yozing, ikkalasini alohida-alohida tuzating va har birida qanday xatolik chiqqanini yozib qo'ying.
18. `print()` funksiyasi haqida Python rasmiy hujjatidan (docs.python.org) qidiruv qilib, uning yana qanday parametrlari borligini toping va ulardan birini sinab ko'ring.
19. O'z ismingiz, familiyangiz va tug'ilgan yilingizdan "vizit karta" yasang — konsolda chiroyli, ramkali ko'rinishda.
20. Kichik "taqvim" chizing — bitta oyning barcha kunlarini `print()` orqali, haftaning har qatorida 7 tadan chiqarib (raqamlarni qo'lda yozib, tsiklsiz).

---

**Keyingi mavzu:** [02 — print(), sintaksis va arifmetik amallar](./02_print_sintaksis_arifmetik.md)
