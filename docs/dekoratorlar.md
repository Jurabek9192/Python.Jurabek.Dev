# DEKORATORLAR (DECORATORS)

## Boshlashdan oldin — funksiyalar "birinchi darajali obyekt"

Python'da funksiyalar ham xuddi son, string yoki list kabi **oddiy obyekt** hisoblanadi. Ularni o'zgaruvchiga yozish, boshqa funksiyaga argument sifatida uzatish, hatto funksiyadan qaytarish mumkin. Dekoratorlarni tushunish uchun aynan shu tushuncha — asos.

```python
def salomlash():
    print("Salom!")

mening_funksiyam = salomlash     # funksiyani o'zgaruvchiga yozish (qavssiz — CHAQIRMASDAN!)
mening_funksiyam()                  # endi uni chaqirish mumkin -> Salom!

print(salomlash)              # <function salomlash at 0x...> — funksiyaning o'zi, natijasi emas
print(salomlash())               # Salom! \n None — bu FUNKSIYANI CHAQIRISH, natijasi qaytariladi
```

**Farqni yodda tuting:** `salomlash` — bu funksiyaning o'zi (obyekt). `salomlash()` — bu funksiyani ishga tushirish (chaqirish).

## Funksiya ichida funksiya (nested function)

```python
def tashqi_funksiya():
    print("Tashqi funksiya boshlandi")

    def ichki_funksiya():
        print("Men ichki funksiyaman")

    ichki_funksiya()          # ichki funksiya faqat SHU YERDA chaqirilishi mumkin
    print("Tashqi funksiya tugadi")

tashqi_funksiya()
# ichki_funksiya()      # XATOLIK! ichki_funksiya tashqarida "ko'rinmaydi" (mahalliy qamrov)
```

## Funksiyani argument sifatida qabul qilish

```python
def bajarilishini_korsat(funksiya):
    print("--- Boshlanishidan oldin ---")
    funksiya()                    # bu yerda "funksiya" parametri chaqirilyapti
    print("--- Tugagandan keyin ---")

def salomlash():
    print("Salom, Dunyo!")

bajarilishini_korsat(salomlash)     # DIQQAT: salomlash — qavssiz, funksiyaning o'zi uzatilyapti!
```

```
--- Boshlanishidan oldin ---
Salom, Dunyo!
--- Tugagandan keyin ---
```

## Funksiyadan funksiya qaytarish

```python
def tashqi():
    def ichki():
        print("Men ichkidaman")
    return ichki       # funksiyaNI o'zini QAYTARYAPMIZ, ChaqirMASDAN! (qavs yo'q)

natija = tashqi()      # natija — endi "ichki" funksiyasining o'zi
print(natija)              # <function tashqi.<locals>.ichki at 0x...>
natija()                      # endi uni chaqiramiz -> "Men ichkidaman"
```

## Dekorator nima?

**Dekorator** — boshqa funksiyani "o'rab" (wrap qilib), uning **asl kodini o'zgartirmasdan**, uning atrofida qo'shimcha xatti-harakat qo'shuvchi funksiya. Bu — yuqorida ko'rgan uch tushunchani (funksiya argument sifatida, ichki funksiya, funksiya qaytarish) birlashtiradi.

```python
def mening_dekoratorim(funksiya):
    def ichki_wrapper():                    # "wrapper" — funksiyani "o'rab turuvchi" degani
        print("--- Funksiya ishga tushishidan oldin ---")
        funksiya()                              # asl funksiya shu yerda chaqiriladi
        print("--- Funksiya tugagandan keyin ---")
    return ichki_wrapper                          # o'ralgan yangi funksiyani qaytaramiz

def salomlash():
    print("Salom!")

salomlash = mening_dekoratorim(salomlash)     # QO'LDA dekoratsiya qilish
salomlash()                                       # endi salomlash — bu ASLIDA "ichki_wrapper"!
```

```
--- Funksiya ishga tushishidan oldin ---
Salom!
--- Funksiya tugagandan keyin ---
```

**Nima sodir bo'ldi?** `salomlash = mening_dekoratorim(salomlash)` qatoridan keyin, `salomlash` o'zgaruvchisi endi asl funksiyani emas, balki uni "o'rab turgan" `ichki_wrapper`ni ko'rsatadi. Shu sababli `salomlash()` chaqirilganda, avval "oldin" xabari, keyin asl funksiya, keyin "keyin" xabari chiqadi.

## `@` sintaksisi — dekoratorning qulay yozuvi

Yuqoridagi `funksiya = dekorator(funksiya)` yozuvi ko'p ishlatilgani uchun, Python maxsus, qisqa `@` belgisini taqdim etadi:

```python
def mening_dekoratorim(funksiya):
    def wrapper():
        print("--- Boshlanishidan oldin ---")
        funksiya()
        print("--- Tugagandan keyin ---")
    return wrapper

@mening_dekoratorim      # bu QATOR quyidagiga TENG: salomlash = mening_dekoratorim(salomlash)
def salomlash():
    print("Salom!")

salomlash()      # to'g'ridan-to'g'ri chaqiramiz, endi u avtomatik dekoratsiya qilingan
```

**Bu ikkalasi — aynan bir xil natija beradi**, lekin `@` bilan yozish ancha o'qish oson va Python'da standart amaliyot hisoblanadi.

## Parametrli funksiyalarni dekoratsiya qilish — *args, **kwargs

Agar dekoratsiya qilinayotgan funksiya parametr qabul qilsa, `wrapper` ham ularni "o'tkazib yuborishi" kerak — buning uchun `*args, **kwargs` ishlatiladi (Kitob 1'dagi mavzu bilan bog'liq):

```python
def mening_dekoratorim(funksiya):
    def wrapper(*args, **kwargs):              # istalgan sondagi va turdagi argumentni qabul qiladi
        print("--- Boshlanishidan oldin ---")
        natija = funksiya(*args, **kwargs)         # ularni asl funksiyaga "uzatadi"
        print("--- Tugagandan keyin ---")
        return natija                                  # asl funksiyaning natijasini ham qaytaramiz!
    return wrapper

@mening_dekoratorim
def qoshish(a, b):
    return a + b

natija = qoshish(5, 3)
print(f"Natija: {natija}")
```

```
--- Boshlanishidan oldin ---
--- Tugagandan keyin ---
Natija: 8
```

**Muhim qoida:** Professional dekorator har doim `*args, **kwargs` va `return` ishlatishi kerak — aks holda dekorator faqat parametrsiz, natija qaytarmaydigan funksiyalar bilangina ishlaydi.

## Amaliy misol 1 — ishlash vaqtini o'lchash

```python
import time

def vaqt_olchash(funksiya):
    def wrapper(*args, **kwargs):
        boshlanish = time.time()
        natija = funksiya(*args, **kwargs)
        tugash = time.time()
        print(f"{funksiya.__name__} — {tugash - boshlanish:.4f} soniyada bajarildi")
        return natija
    return wrapper

@vaqt_olchash
def katta_hisoblash():
    return sum(range(10_000_000))

katta_hisoblash()     # katta_hisoblash — 0.3521 soniyada bajarildi
```

## Amaliy misol 2 — funksiya chaqiruvlarini "loglash"

```python
def log(funksiya):
    def wrapper(*args, **kwargs):
        print(f"Chaqirilyapti: {funksiya.__name__}({args}, {kwargs})")
        natija = funksiya(*args, **kwargs)
        print(f"Natija: {natija}")
        return natija
    return wrapper

@log
def kopaytirish(a, b):
    return a * b

kopaytirish(4, 5)
```

```
Chaqirilyapti: kopaytirish((4, 5), {})
Natija: 20
```

## Amaliy misol 3 — kiritilgan qiymatlarni tekshirish (validatsiya)

```python
def musbat_tekshir(funksiya):
    def wrapper(*args, **kwargs):
        if any(son < 0 for son in args):
            print("Xato: manfiy son kiritildi!")
            return None
        return funksiya(*args, **kwargs)
    return wrapper

@musbat_tekshir
def kvadrat_ildiz(son):
    return son ** 0.5

print(kvadrat_ildiz(16))       # 4.0
print(kvadrat_ildiz(-9))          # Xato: manfiy son kiritildi!  -> None
```

## Bir nechta dekoratorni birga qo'llash (stacking)

```python
@vaqt_olchash
@log
def qoshish(a, b):
    return a + b

qoshish(3, 4)
```

Dekoratorlar **pastdan yuqoriga** qarab qo'llaniladi — avval `@log` o'raydi, keyin natijaviy funksiyani `@vaqt_olchash` yana o'raydi. Ya'ni bu quyidagiga teng: `vaqt_olchash(log(qoshish))`.

## functools.wraps — professional amaliyot (muhim!)

Muammo: dekorator qo'llanganda, asl funksiyaning **nomi va docstring'i "yo'qolib qoladi"**, chunki `wrapper` uni butunlay almashtiradi:

```python
def mening_dekoratorim(funksiya):
    def wrapper(*args, **kwargs):
        return funksiya(*args, **kwargs)
    return wrapper

@mening_dekoratorim
def salomlash():
    """Bu funksiya foydalanuvchini salomlaydi"""
    print("Salom!")

print(salomlash.__name__)     # "wrapper" — NOTO'G'RI! Aslida "salomlash" bo'lishi kerak edi
print(salomlash.__doc__)         # None — docstring HAM yo'qolib qoldi!
```

Buni `functools.wraps` bilan tuzatamiz:

```python
from functools import wraps

def mening_dekoratorim(funksiya):
    @wraps(funksiya)         # asl funksiyaning __name__ va __doc__ini SAQLAB QOLADI
    def wrapper(*args, **kwargs):
        return funksiya(*args, **kwargs)
    return wrapper

@mening_dekoratorim
def salomlash():
    """Bu funksiya foydalanuvchini salomlaydi"""
    print("Salom!")

print(salomlash.__name__)     # "salomlash" — endi TO'G'RI!
print(salomlash.__doc__)         # "Bu funksiya foydalanuvchini salomlaydi" — saqlanib qoldi!
```

**Qat'iy qoida:** Har doim professional dekorator yozganda, `@wraps(funksiya)` qo'shing — bu kichik, lekin muhim detal.

## Parametrli dekorator — "dekorator fabrikasi"

Ba'zan dekoratorning o'ziga ham parametr berish kerak bo'ladi (masalan "necha marta takrorlash"). Bu uchun **yana bitta qo'shimcha "qatlam"** (funksiya ichida funksiya ichida funksiya) kerak bo'ladi:

```python
def takrorlash(necha_marta):          # bu — "dekorator fabrikasi", dekoratorni O'ZI yaratadi
    def dekorator(funksiya):
        @wraps(funksiya)
        def wrapper(*args, **kwargs):
            natija = None
            for _ in range(necha_marta):
                natija = funksiya(*args, **kwargs)
            return natija
        return wrapper
    return dekorator

@takrorlash(3)          # bu — takrorlash(3) FUNKSIYANI chaqiradi, u dekoratorni QAYTARADI
def salomlash(ism):
    print(f"Salom, {ism}!")

salomlash("Ali")     # 3 marta "Salom, Ali!" deb chiqadi
```

```
Salom, Ali!
Salom, Ali!
Salom, Ali!
```

## Amaliy misol 4 — kirishni tekshirish + xatolikni "ushlash" dekoratori

```python
def xavfsiz(funksiya):
    @wraps(funksiya)
    def wrapper(*args, **kwargs):
        try:
            return funksiya(*args, **kwargs)
        except Exception as xatolik:
            print(f"Xatolik yuz berdi ({funksiya.__name__}): {xatolik}")
            return None
    return wrapper

@xavfsiz
def bolish(a, b):
    return a / b

print(bolish(10, 2))     # 5.0
print(bolish(10, 0))        # Xatolik yuz berdi (bolish): division by zero  -> None
```

## Python'ning o'rnatilgan dekoratorlari — eslatma

Siz allaqachon (yoki keyingi bosqichda) o'rnatilgan dekoratorlarni ko'rgan/ko'rasiz: `@staticmethod`, `@classmethod`, `@property` — bular OOP klasslarida ishlatiladigan, Python'ning o'zi taqdim etadigan tayyor dekoratorlar. Ularning ichki mexanizmi aynan shu darsda o'rgangan tamoyillarga asoslangan.

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Funksiyani o'zgaruvchiga yozib (chaqirmasdan), so'ng o'sha o'zgaruvchi orqali chaqiring.
2. Funksiya ichida funksiya (nested function) yozing va uni tashqi funksiya ichida chaqiring.
3. Boshqa funksiyani argument sifatida qabul qilib, uni ichida chaqiruvchi funksiya yozing.
4. Har qanday funksiyani chaqirishdan oldin "Boshlanmoqda..." va keyin "Tugadi!" deb chop etuvchi oddiy dekorator yozing (`@` sintaksisisiz, qo'lda: `f = dekorator(f)`).
5. Xuddi shu dekoratorni endi `@` belgisi bilan qayta yozing.
6. Parametrli funksiyaga (masalan 2 ta son qabul qiluvchi) `*args, **kwargs` ishlatuvchi dekorator qo'llang.
7. Dekoratorsiz va dekоrator bilan funksiyaning `__name__` qiymatini solishtirib, farqni ko'ring.
8. `functools.wraps` qo'shib, yuqoridagi muammoni tuzating.

🟡 **O'rta (9-15)**

9. Funksiya nomi va uning argumentlarini chop etuvchi `log` dekoratorini yozing (`log` misoliga o'xshab).
10. `vaqt_olchash` dekoratorini yarating va uni turli murakkablikdagi 2-3 funksiyaga qo'llab, ishlash vaqtlarini solishtiring.
11. Funksiya natijasini 2 baravar ko'paytiruvchi dekorator yozing (faqat son qaytaruvchi funksiyalar uchun).
12. Manfiy sonlarni "tutib qoladigan" (`musbat_tekshir` kabi) validatsiya dekoratorini yozing va uni 2 xil funksiyaga qo'llang.
13. Ikkita dekoratorni (masalan `log` va `vaqt_olchash`) bitta funksiyaga birga qo'llab, ularning qaysi tartibda ishlashini kuzating.
14. `xavfsiz` dekoratorini yozing — u istalgan funksiyadagi xatolikni `try/except` bilan ushlab, dastur qulashining oldini olsin.
15. Funksiya necha marta chaqirilganini hisoblab boruvchi (dekorator ichida hisoblagich saqlanadigan) dekorator yozing.

🔴 **Qiyin (16-20)**

16. Parametrli dekorator (`takrorlash(n)` kabi) yozing — funksiya `n` marta ketma-ket bajarilsin.
17. Faqat "ruxsat etilgan foydalanuvchi" (masalan parametr sifatida beriladigan `ism="admin"`) chaqirsa ishlaydigan, aks holda "Ruxsat yo'q" deb chiqadigan dekorator yozing.
18. Funksiya natijasini keshda (oddiy dictionary'da) saqlab, bir xil argumentlar bilan qayta chaqirilganda hisoblamasdan, saqlangan natijani qaytaruvchi "cache" dekoratorini yozing (bu — mashhur `functools.lru_cache`ning soddalashtirilgan versiyasi).
19. Kelib tushayotgan argumentlarning turini (`type hints` asosida) tekshiruvchi, noto'g'ri tur kelsa xatolik chiqaruvchi dekorator yozing.
20. To'liq "REST API himoyasi" simulyatsiyasi: `@vaqt_olchash`, `@log`, va `@xavfsiz` dekoratorlarining barchasini bitta funksiyaga birlashtirib qo'llang, natijada funksiya vaqti o'lchansin, chaqiruvi loglansin, va xatoliklardan himoyalangan bo'lsin.

---

**Bog'liq mavzular:** [16 — Funksiya](./16_funksiya.md) • [19 — Moslashuvchan funksiya (*args, **kwargs)](./19_moslashuvchan_funksiya.md) • [11 — Xatolar bilan ishlash](./11_xatolar.md)
