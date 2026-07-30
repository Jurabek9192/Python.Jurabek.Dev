# 01 — DASTURLASH VA PYTHON BILAN TANISHUV

## Dasturlash nima?

**Dasturlash** — kompyuterga bosqichma-bosqich ko'rsatma (instruksiya) berish jarayoni. Kompyuter o'zi hech narsani "o'ylab" qilmaydi — u faqat unga aniq va tartibli tarzda berilgan buyruqlarni bajaradi. Dasturchi vazifasi — masalani kompyuter tushunadigan, aniq qadamlarga bo'lib berish.

## Nega Python?

- **Sodda va tushunarli sintaksis** — kod deyarli inson tiliga o'xshaydi
- **Keng qo'llanilish sohasi** — veb-saytlar, sun'iy intellekt, ma'lumotlar tahlili, robototexnika, o'yinlar, Telegram botlar
- **Katta jamoat** — muammoga duch kelsangiz, javobni internetdan topish oson
- **Bepul va ochiq manba (open source)**
- **"Batteries included"** — Python o'zi bilan juda ko'p tayyor vositalarni (standart kutubxona) olib keladi

## Python qanday ishlaydi — interpretatsiya

Python — **interpretatsiya qilinuvchi (interpreted)** til. Bu C++ yoki Java'dan farqli — u yerda kod avval to'liq "kompilyatsiya" (mashina kodiga aylantirilishi) qilinishi kerak, Python esa kodni qator-baqator, darhol o'qib bajaradi. Bu Python'ni o'rganish va sinab ko'rish uchun ancha tezkor qiladi, ammo ba'zan ishlash tezligi (performance) jihatidan kompilyatsiya qilinuvchi tillardan sekinroq bo'ladi.

## Kerakli dasturlarni o'rnatish

1. **Python** — [python.org/downloads](https://www.python.org/downloads/) saytidan yuklab oling. O'rnatishda **"Add Python to PATH"** katagini albatta belgilang.
2. **VS Code** — [code.visualstudio.com](https://code.visualstudio.com/) saytidan yuklab oling. Bu — kod yozish uchun matn muharriri.
3. VS Code'da **Python kengaytmasi (extension)**ni o'rnating — bu kodni ranglab ko'rsatish, xatoliklarni oldindan aniqlash kabi qulayliklarni beradi.

**Muqobil muharrirlar:** PyCharm (professional, murakkabroq loyihalar uchun), Jupyter Notebook (ma'lumotlar tahlili, bo'lak-bo'lak kod ishga tushirish uchun qulay), Thonny (juda boshlang'ich darajadagilar uchun sodda).

O'rnatishni tekshirish uchun terminalda:

```bash
python --version
pip --version
```

```
Python 3.13.0
pip 24.0
```

## Birinchi dasturimiz — "Salom, Dunyo!"

```python
print("Salom, Dunyo!")
```

```
Salom, Dunyo!
```

`print()` — Python'ning **funksiyasi**, u qavs ichidagi narsani ekranga ko'rsatadi.

## Kodni qanday ishga tushiramiz?

1. VS Code'da yangi fayl yarating, nomini `salom.py` deb saqlang (`.py` — Python fayllarining kengaytmasi)
2. Faylga kodni yozing
3. Terminalda faylni ishga tushiring:

```bash
python salom.py
```

## Python interaktiv rejimi (REPL)

Terminalga shunchaki `python` deb yozib Enter bosing — bu sizni **REPL** (Read-Eval-Print Loop) rejimiga olib kiradi, u yerda har bir qatorni alohida, darhol natija ko'rib sinab ko'rish mumkin:

```
>>> 2 + 2
4
>>> print("test")
test
>>> exit()
```

REPL — yangi funksiya yoki metodni tez sinab ko'rish uchun juda qulay vosita.

## Izohlar (comments)

```python
# Bu bir qatorlik izoh
print("Salom, Dunyo!")   # qatorning oxirida ham yozish mumkin

"""
Bu ko'p qatorli izoh (aslida ko'p qatorli string,
lekin izoh sifatida ham keng ishlatiladi).
"""
```

## Xatoliklardan qo'rqmang — traceback'ni o'qish

Python xatolik yuz berganda, qaysi qatorda va nima sababdan xato borligini ko'rsatadi:

```python
print("Salom"
```

```
SyntaxError: '(' was never closed
```

## Foydali "tekshiruv" funksiyalari — help(), dir(), type(), id()

Python'ni o'rganishda quyidagi to'rtta funksiya doimiy hamrohingiz bo'ladi:

```python
print(type(5))          # <class 'int'> — obyektning turini ko'rsatadi
print(type("salom"))      # <class 'str'>

help(print)                 # print() funksiyasi haqida to'liq hujjat chiqaradi

print(dir(str))               # str turiga tegishli BARCHA metodlar ro'yxatini beradi

print(id(5))                    # obyektning xotiradagi noyob "manzili" (identifikatori)
```

`help()` va `dir()` — kelajakda yangi metod yoki funksiyaga duch kelganda, uning nima qilishini va qanday boshqa imkoniyatlari borligini bilish uchun eng tezkor vositalar.

## Zamonaviy imkoniyat — Python versiyasini kodda tekshirish

```python
import sys
print(sys.version)          # to'liq versiya ma'lumoti
print(sys.version_info)      # tuple ko'rinishida (major, minor, micro...)
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. `print()` yordamida ekranga o'z ismingizni chiqaring.
2. Ekranga "Men Python o'rganyapman!" degan xabarni chiqaring.
3. Ketma-ket 3 ta `print()` orqali o'zingiz haqingizda 3 ta jumla chiqaring (ism, yosh, shahar).
4. Bitta `print()` qatoriga izoh (comment) qo'shing.
5. Ko'p qatorli izoh (`"""..."""`) yordamida dasturingiz haqida qisqacha izoh yozing.
6. `print()` yordamida ekranda `*` belgilaridan uchburchak shaklini chizing (5 qator).
7. Terminalda `python --version` va `pip --version` buyruqlarini bajarib, natijalarini yozib qo'ying.
8. Qasddan xatolik keltirib chiqaradigan kod yozing (masalan qavsni yopmang) va chiqqan xatolikni diqqat bilan o'qing.

🟡 **O'rta (9-15)**

9. Ekranga o'zingiz sevgan she'r yoki maqolning 4 qatorini chiqaring.
10. `print()` yordamida oddiy "vizit karta" chizing — ism, kasb, telefon (ramka ichida, `-` va `|` belgilaridan foydalanib).
11. `type()` funksiyasi yordamida 5 xil qiymatning (son, matn, bool va h.k.) turini aniqlang.
12. `help(str)` ni terminalda ishga tushirib, chiqqan ma'lumotni ko'rib chiqing (`q` bilan chiqiladi) va nimalarni tushunganingizni yozing.
13. `dir(list)` natijasidan hozircha tanish bo'lmagan 5 ta metod nomini topib yozib qo'ying — keyingi mavzularda ularni o'rganamiz.
14. Terminal orqali joriy papkadagi barcha `.py` fayllarni ko'ring (`dir` yoki `ls` buyrug'i bilan).
15. Python REPL rejimiga kiring va u yerda 5 ta turli ifodani (`2+2`, `"a"*3` va h.k.) sinab ko'ring.

🔴 **Qiyin (16-20)**

16. Ekranda ASCII-art uslubida o'z ismingizni katta harflar bilan (har bir harfni `*` yoki boshqa belgidan yasab) chizing.
17. Ikkita xato (masalan yopilmagan qavs va noto'g'ri tirnoq) bo'lgan kod yozing, ikkalasini alohida-alohida tuzating va har birida qanday xatolik chiqqanini yozib qo'ying.
18. `sys.version_info` dan foydalanib, joriy Python versiyasining major, minor va micro qismlarini alohida chiqaring.
19. O'z ismingiz, familiyangiz va tug'ilgan yilingizdan "vizit karta" yasang — konsolda chiroyli, ramkali ko'rinishda.
20. `id()` funksiyasidan foydalanib, ikkita xuddi shunday qiymatli (masalan ikkita `5`) o'zgaruvchining xotiradagi manzili bir xil yoki turlichaligini tekshiring va natijani o'zingizcha izohlang.

---

**Keyingi mavzu:** [02 — print(), sintaksis va arifmetik amallar](./02_print_sintaksis_arifmetik.md)
