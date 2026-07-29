# FUNKSIYALAR — ASOSLAR

## Funksiya nima?

**Funksiya** — ma'lum bir vazifani bajaruvchi, qayta-qayta ishlatilishi mumkin bo'lgan kod bo'lagi. Funksiyalar dasturlashning eng muhim tushunchalaridan biri, chunki ular kodni:

- **Takrorlanishdan saqlaydi** (DRY — Don't Repeat Yourself printsipi)
- **Tartibli va o'qish oson qiladi**
- **Test qilish va xato tuzatishni osonlashtiradi**
- **Qayta ishlatish imkonini beradi**

Biz allaqachon ko'plab tayyor funksiyalardan foydalangan edik: `print()`, `len()`, `input()`, `type()` — bular Python'ning **o'rnatilgan (built-in)** funksiyalari. Endi o'zimiznikini yaratishni o'rganamiz.

## Funksiya yaratish sintaksisi

```python
def salomlash():
    print("Salom, Dunyo!")

salomlash()   # funksiyani chaqirish
```

```
Salom, Dunyo!
```

Tahlil:
- `def` — funksiya e'lon qilinayotganini bildiruvchi kalit so'z
- `salomlash` — funksiya nomi (o'zgaruvchi nomlash qoidalariga bo'ysunadi)
- `()` — parametrlar shu yerga yoziladi (hozircha bo'sh)
- `:` va indentatsiya — funksiya tanasi

**Muhim:** Funksiyani yaratish (`def`) uni ishga tushirmaydi! Funksiya faqat **chaqirilganda** (`salomlash()`) ishlaydi.

## Parametrli funksiyalar

Funksiyaga tashqaridan ma'lumot uzatish uchun **parametrlar** ishlatiladi:

```python
def salomlash(ism):
    print(f"Salom, {ism}!")

salomlash("Aziz")
salomlash("Malika")
```

```
Salom, Aziz!
Salom, Malika!
```

Bir nechta parametr:

```python
def tanishtir(ism, yosh):
    print(f"Bu {ism}, u {yosh} yoshda")

tanishtir("Bekzod", 25)
```

## return — qiymat qaytarish

Hozirgacha funksiyalarimiz faqat ekranga chiqarardi (`print`), lekin natijani **qaytarmasdi**. `return` funksiyaning natijasini tashqariga chiqarish imkonini beradi:

```python
def qoshish(a, b):
    return a + b

natija = qoshish(5, 3)
print(natija)          # 8
print(qoshish(10, 20))  # 30
```

## print() va return orasidagi farq

Bu boshlang'ich dasturchilar ko'p chalkashtiradigan joy:

```python
def qoshish_print(a, b):
    print(a + b)     # faqat ekranga chiqaradi, qaytarmaydi

def qoshish_return(a, b):
    return a + b       # natijani qaytaradi, keyin ishlatish mumkin

x = qoshish_print(5, 3)    # ekranga 8 chiqadi
print(x)                     # None — chunki funksiya hech narsa qaytarmadi!

y = qoshish_return(5, 3)    # ekranga hech narsa chiqmaydi
print(y)                      # 8 — chunki funksiya natijani qaytardi
```

**Qoida:** Agar funksiya natijasidan keyinchalik foydalanish kerak bo'lsa (masalan boshqa hisob-kitobda), albatta `return` ishlatilishi kerak. `print()` faqat ekranga ko'rsatish uchun, dastur mantig'ida ishlatib bo'lmaydi.

## return — funksiyani darhol to'xtatadi

`return` ishga tushishi bilan funksiya darhol tugaydi, undan keyingi kod bajarilmaydi:

```python
def tekshir(son):
    if son < 0:
        return "Manfiy son"
    return "Musbat yoki nol"
    print("Bu qator hech qachon ishlamaydi")  # o'lik kod

print(tekshir(-5))
print(tekshir(5))
```

## Standart (default) qiymatli parametrlar

Parametrga standart qiymat berish mumkin — agar chaqirishda bu argument berilmasa, standart qiymat ishlatiladi:

```python
def salomlash(ism, til="uz"):
    if til == "uz":
        print(f"Salom, {ism}!")
    elif til == "en":
        print(f"Hello, {ism}!")

salomlash("Ali")              # standart til ishlatiladi (uz)
salomlash("John", "en")        # aniq til ko'rsatildi
```

```
Salom, Ali!
Hello, John!
```

**Qoida:** Standart qiymatli parametrlar har doim oddiy parametrlardan **keyin** yozilishi kerak:

```python
def togri(a, b=10):       # to'g'ri
    pass

# def notogri(a=10, b):   # XATOLIK! SyntaxError
```

## Kalit so'z orqali argument berish (keyword arguments)

Argumentlarni nom orqali berish mumkin — bu tartibdan qat'iy nazar ishlaydi va kodni tushunarliroq qiladi:

```python
def talaba_royxatga_olish(ism, yosh, guruh):
    print(f"{ism}, {yosh} yosh, {guruh}-guruh")

# oddiy (pozitsion) chaqiruv
talaba_royxatga_olish("Ali", 20, "A")

# kalit so'z orqali chaqiruv — tartib muhim emas
talaba_royxatga_olish(guruh="B", ism="Vali", yosh=22)
```

## Funksiya ichidagi o'zgaruvchilar — mahalliy doira (local scope)

Funksiya ichida yaratilgan o'zgaruvchilar faqat **shu funksiya ichida** mavjud bo'ladi:

```python
def hisobla():
    natija = 100    # bu — local (mahalliy) o'zgaruvchi
    print(natija)

hisobla()
# print(natija)     # XATOLIK! NameError — natija funksiyadan tashqarida mavjud emas
```

Bu — dasturlashda **scope (qamrov)** deyiladigan muhim tushuncha bo'lib, keyingi mavzularda (funksiya argumentlari) chuqurroq o'rganamiz.

## Global va local o'zgaruvchilar

```python
hisob = 0   # global o'zgaruvchi

def qoshish():
    hisob = 10   # bu YANGI, local o'zgaruvchi — globalga tegmaydi!
    print(hisob)   # 10

qoshish()
print(hisob)   # 0 — global o'zgaruvchi o'zgarmadi
```

Agar funksiya ichida global o'zgaruvchini o'zgartirish zarur bo'lsa (odatda tavsiya etilmaydi, lekin bilish kerak):

```python
hisob = 0

def qoshish():
    global hisob
    hisob += 10

qoshish()
print(hisob)   # 10
```

## Funksiyalarni to'g'ri hujjatlash (docstring)

Professional kodda funksiyaning nima qilishini tushuntiruvchi qisqa izoh yoziladi — bu **docstring** deyiladi:

```python
def yigindi(a, b):
    """
    Ikki sonning yig'indisini hisoblaydi.
    a: birinchi son
    b: ikkinchi son
    qaytaradi: a va b ning yig'indisi
    """
    return a + b
```

## Amaliy misol: soddalashtirilgan kalkulyator

```python
def qoshish(a, b):
    return a + b

def ayirish(a, b):
    return a - b

def kopaytirish(a, b):
    return a * b

def bolish(a, b):
    if b == 0:
        return "Nolga bo'lib bo'lmaydi"
    return a / b

x, y = 10, 3
print(f"Yig'indi: {qoshish(x, y)}")
print(f"Ayirma: {ayirish(x, y)}")
print(f"Ko'paytma: {kopaytirish(x, y)}")
print(f"Bo'linma: {bolish(x, y)}")
```

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. Ism qabul qilib, "Xush kelibsiz, [ism]!" deb chiqaruvchi funksiya yozing.
2. Ikki sonni qabul qilib, ularning ko'paytmasini qaytaruvchi funksiya yozing.
3. Sonni qabul qilib, uning juft yoki toqligini "juft"/"toq" ko'rinishida qaytaruvchi funksiya yozing.
4. Standart qiymati bor funksiya yozing: shahar nomini qabul qiladi, agar berilmasa "Toshkent" standart bo'lsin.

🟡 **O'rta daraja**

5. Uch sonni qabul qilib, ular orasidan eng kattasini qaytaruvchi funksiya yozing (`max()` ishlatmasdan).
6. To'rtburchakning eni va bo'yini qabul qilib, yuzi va perimetrini (ikkalasini alohida) qaytaruvchi ikkita funksiya yozing.
7. Matnni qabul qilib, undagi unli harflar sonini qaytaruvchi funksiya yozing.
8. Sonlar ro'yxatini qabul qilib, ularning o'rtacha qiymatini qaytaruvchi funksiya yozing.

🔴 **Murakkabroq**

9. Sonni qabul qilib, u tub son (prime) ekanligini `True`/`False` ko'rinishida qaytaruvchi funksiya yozing, so'ng bu funksiyadan foydalanib 1 dan 50 gacha barcha tub sonlarni chiqaring.
10. Ikki funksiya yozing: `celsius_to_fahrenheit(c)` va `fahrenheit_to_celsius(f)`. Ular bir-birini tekshirish uchun ishlatilsin (masalan 0°C ni Fahrenheit'ga, keyin qaytadan Celsius'ga aylantiring va natija 0 ga tengligini tekshiring).

---

**Oldingi mavzu:** [14 — break, continue, pass](./14_break_continue_pass.md)
**Keyingi mavzu:** [16 — Funksiya argumentlari (*args, **kwargs)](./16_funksiya_argumentlari.md)
