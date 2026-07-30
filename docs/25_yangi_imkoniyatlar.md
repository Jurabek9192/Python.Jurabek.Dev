# 25 — PYTHON'NING ENG SO'NGGI IMKONIYATLARI (BONUS)

## Kirish

Bu — kursning bonus mavzusi. Bu yerda so'nggi Python versiyalarida (3.8 dan 3.14 gacha) qo'shilgan, amaliyotda foydali bo'lgan eng muhim yangiliklarni ko'rib chiqamiz. Hozirgi barqaror versiya — **Python 3.14** (2025-yil oktabrda chiqqan), undan oldingi **Python 3.13** ham keng qo'llaniladi.

## 1. Walrus operator `:=` (Python 3.8)

Qiymatni tekshirish bilan bir vaqtda o'zgaruvchiga yozish:

```python
# eski usul
son = int(input("Son: "))
if son > 10:
    print(f"{son} katta")

# walrus operator bilan
if (son := int(input("Son: "))) > 10:
    print(f"{son} katta")
```

## 2. f-string ichida `=` belgisi (Python 3.8)

Debugging uchun juda qulay:

```python
yosh = 25
print(f"{yosh=}")     # yosh=25
```

## 3. match-case — structural pattern matching (Python 3.10)

Ko'p `elif` zanjiri o'rniga ishlatiladigan, boshqa tillardagi `switch`ga o'xshash konstruksiya:

```python
def http_xabar(kod):
    match kod:
        case 200:
            return "OK"
        case 404:
            return "Topilmadi"
        case 500 | 502 | 503:
            return "Server xatoligi"
        case _:
            return "Noma'lum kod"
```

`match-case` shuningdek strukturani "yechish" (destructuring) imkonini ham beradi:

```python
buyruq = ("harakat", "yur", 5)

match buyruq:
    case ("harakat", "yur", masofa):
        print(f"{masofa} qadam yurish")
    case ("harakat", "burил", burchak):
        print(f"{burchak} darajaga burilish")
```

## 4. Union turlar — `|` belgisi (Python 3.10)

```python
def id_royxatga_olish(id: int | str) -> str:      # Union[int, str] o'rniga
    return f"ID: {id}"
```

## 5. Dictionary birlashtirish operatori `|` (Python 3.9)

```python
a = {"x": 1, "y": 2}
b = {"y": 3, "z": 4}
birlashgan = a | b     # {'x': 1, 'y': 3, 'z': 4}
```

## 6. Exception Groups va `except*` (Python 3.11)

Bir nechta xatolikni bir vaqtda "guruh" sifatida ushlash imkonini beradi — bu ayniqsa parallel/asinxron kodda foydali:

```python
try:
    raise ExceptionGroup("bir nechta xato", [ValueError("v1"), TypeError("t1")])
except* ValueError as eg:
    print("ValueError turlari:", eg.exceptions)
except* TypeError as eg:
    print("TypeError turlari:", eg.exceptions)
```

## 7. Aniqroq xatolik xabarlari (Python 3.11+)

Python 3.11 dan boshlab, traceback xabarlari xatolik aynan qaysi ifodada yuz berganini **aniqroq** ko'rsatadi (masalan uzun qatorda qaysi qism xato ekanini strelka bilan belgilaydi) — bu debugging'ni sezilarli osonlashtiradi.

## 8. tomllib — TOML formatini o'qish (Python 3.11)

```python
import tomllib

with open("sozlamalar.toml", "rb") as fayl:
    malumot = tomllib.load(fayl)
```

## 9. Yaxshilangan interaktiv interpretator (Python 3.13)

Python 3.13'dan boshlab terminal orqali ishga tushirilgan `python` interaktiv rejimi ko'p qatorli tahrirlash, rangli xatolik xabarlari (colorized traceback) va yaxshilangan avtomatik to'ldirishni qo'llab-quvvatlaydi.

## 10. Free-threaded rejim — GIL'siz Python (Python 3.13-3.14, eksperimental)

Kitob 3'da GIL (Global Interpreter Lock) haqida o'rgangan edik — u bir vaqtning o'zida faqat bitta thread'ga Python kodini bajarishga ruxsat berardi. Python 3.13'dan boshlab, **eksperimental "free-threaded" rejim** joriy qilindi — bu rejimda GIL o'chirilgan bo'lib, thread'lar haqiqiy parallel ishlashi mumkin. Python 3.14'da bu rejim yanada barqarorlashtirildi va mashhur kutubxonalar (NumPy kabi) bilan moslik yaxshilandi.

## 11. Template Strings — t-string (Python 3.14)

f-string'ning "xavfsizroq" muqobili — natija darhol matnga aylanmaydi, balki alohida qayta ishlash (masalan xavfsizlik uchun escaping) imkonini beruvchi maxsus obyekt yaratiladi. Bu ayniqsa SQL so'rovlari yoki HTML yaratishda, zararli kodning "kirib qolishi" (injection)dan himoyalanishda foydali:

```python
from string.templatelib import Template

ism = "Ali"
shablon: Template = t"Salom, {ism}!"    # darhol str emas, Template obyekti
```

## 12. pathlib'ning kengaytirilgan imkoniyatlari (Python 3.14)

`pathlib.Path` endi fayl va papkalarni rekursiv nusxalash (`copy()`) va ko'chirish (`move()`) metodlariga ega bo'ldi — bu oldin faqat `shutil` moduli orqali mumkin edi:

```python
from pathlib import Path

manba = Path("papka1")
manba.copy("papka2")     # butun papkani nusxalaydi
```

## 13. JIT kompilyator (eksperimental, Python 3.13+)

Python 3.13'dan boshlab, dasturni tezlashtirish maqsadida eksperimental **JIT (Just-In-Time) kompilyator** ishlab chiqilmoqda — bu kelajakda Python dasturlarining ishlash tezligini sezilarli oshirishi kutilmoqda.

## Xulosa — nima o'rgandik

Python doimiy rivojlanib boruvchi til. Ushbu kursda siz o'rgangan asoslar (o'zgaruvchilar, ro'yxatlar, funksiyalar, sikllar) — Python qanday versiyasi bo'lishidan qat'iy nazar, hamisha barqaror qoladi. Yuqoridagi yangiliklar esa — bu asoslar ustiga qurilgan, kodni yanada qisqa, xavfsiz va tez yozish imkonini beruvchi qo'shimcha vositalar.

**Amaliy maslahat:** Yangi loyiha boshlaganda, doim `python --version` bilan qaysi versiyada ishlayotganingizni tekshiring va imkon qadar so'nggi barqaror versiyadan foydalaning.

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Walrus operatoridan (`:=`) foydalanib, foydalanuvchi kiritgan son 100dan katta ekanligini bitta shart qatorida tekshiring.
2. f-string ichida `=` belgisidan foydalanib, 3 ta o'zgaruvchining qiymatini "debug" formatida chiqaring.
3. `match-case` yordamida 1 dan 7 gacha bo'lgan songa qarab hafta kunini chiqaring.
4. Ikkita dictionary'ni `|` operatori bilan birlashtiring.
5. `int | str` ko'rinishidagi type hint bilan oddiy funksiya yozing.
6. Terminalda `python --version` bilan qaysi versiya o'rnatilganini tekshiring va yozib qo'ying.
7. `match-case` da `case _:` (standart holat) qanday ishlashini 3 xil misolda sinab ko'ring.
8. Walrus operatoridan `while` tsiklida foydalanib, foydalanuvchidan "stop" kiritilguncha son so'rovchi dastur yozing.

🟡 **O'rta (9-15)**

9. `match-case` yordamida oddiy kalkulyator yozing — amal turi (+, -, *, /) ga qarab natija hisoblansin.
10. Tuple'larni "yechish" (`case (x, y):`) orqali koordinatalarni tekshiruvchi `match-case` yozing.
11. `int | float | str` union turi bilan, istalgan turdagi qiymatni qabul qilib, uni matn ko'rinishida chiqaruvchi funksiya yozing.
12. Ikki xil sozlamalar dictionary'sini `|` bilan birlashtirib, "standart sozlamalar + foydalanuvchi sozlamalari" naqshini amalga oshiring.
13. `match-case` bilan, foydalanuvchi kiritgan buyruqni (masalan "yur 5", "burил 90") tahlil qiluvchi oddiy "robot boshqaruvi" yozing.
14. Walrus operatoridan foydalanib, ro'yxat elementlari ustida `while` tsiklida ishlovchi (masalan `.pop()` bilan) dastur yozing.
15. `match-case` yordamida HTTP status kodlarini (200, 404, 500 va boshqalar) tekshiruvchi funksiya yozing.

🔴 **Qiyin (16-20)**

16. To'liq "buyruqlar tahlilchisi" (command parser) yozing — `match-case` va tuple destructuring yordamida, foydalanuvchi turli formatdagi buyruqlarni (masalan "qoshish 5 3", "salomlash Ali") kirita olsin.
17. Ikkita funksiya yozing — biri eski uslubda (`Union[int, str]`, `typing` modulidan), ikkinchisi yangi uslubda (`int | str`) — va ularning bir xil ishlashini solishtiring.
18. `match-case` bilan to'liq "menyu tizimi" qurib, foydalanuvchi ixtiyoriy formatdagi buyruqlarni (raqam yoki so'z) kirita olsin.
19. Walrus operatori va list comprehension'ni birlashtirib, ro'yxatdan faqat muayyan shartga (masalan uzunligi hisoblab, natija 5dan katta bo'lganlar) mos elementlarni ajratuvchi bir qatorlik kod yozing.
20. O'z tanlovingiz bo'yicha, ushbu mavzuda o'rgangan kamida 3 ta yangi imkoniyatni (masalan `match-case`, `|` union, walrus) birlashtirib, kichik amaliy dastur (masalan oddiy "buyurtma tizimi" yoki "chat-bot javob beruvchisi") yozing.

---

**Oldingi mavzu:** [24 — RegEx (matn andozalari)](./24_regex.md)

---

## 🎉 KURS YAKUNLANDI!

Siz 25 ta mavzu, jami **500 ta mashq** orqali Python dasturlash tilining asoslarini — sodda `print()` dan tortib, zamonaviy `match-case` va Template Strings'gacha — puxta o'rgandingiz. Bu — dasturlashning istalgan yo'nalishida (veb, sun'iy intellekt, robototexnika, ma'lumotlar tahlili) ishonchli poydevor.

**Keyingi qadam:** Object-Oriented Programming (OOP), fayllar bilan ishlash va ilg'or Python vositalarini chuqurroq o'rganish uchun, avvalgi 4 kitoblik "Python bo'yicha to'liq kurs"ingizga qayting.
