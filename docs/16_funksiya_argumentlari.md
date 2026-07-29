# FUNKSIYA ARGUMENTLARI (*ARGS, **KWARGS)

## Muammo: nechta argument kelishini bilmasak-chi?

Oldingi mavzuda biz funksiyalarga aniq sondagi parametr berardik. Lekin ba'zan funksiyaga **nechta argument kelishini oldindan bilmaymiz**. Masalan, sonlar yig'indisini hisoblovchi funksiya — ba'zan 2 ta, ba'zan 5 ta son bilan chaqirilishi kerak bo'lishi mumkin. Aynan shu muammoni `*args` va `**kwargs` hal qiladi.

## *args — istalgan sondagi pozitsion argument

`*args` funksiyaga istalgan sondagi argumentni qabul qilish imkonini beradi. Ular funksiya ichida **tuple** sifatida keladi.

```python
def yigindi(*args):
    print(args)          # tuple sifatida ko'rinadi
    return sum(args)

print(yigindi(1, 2, 3))         # (1, 2, 3) -> 6
print(yigindi(5, 10))            # (5, 10) -> 15
print(yigindi(1, 2, 3, 4, 5))   # (1, 2, 3, 4, 5) -> 15
```

**Diqqat:** `args` so'zining o'zi shart emas — bu shunchaki qabul qilingan nom (`*narsalar` ham ishlaydi). Muhim bo'lgani — `*` belgisi.

```python
def eng_kattasi(*sonlar):
    if not sonlar:
        return None
    katta = sonlar[0]
    for son in sonlar:
        if son > katta:
            katta = son
    return katta

print(eng_kattasi(3, 7, 2, 9, 4))   # 9
```

## **kwargs — istalgan sondagi kalit-so'z argumenti

`**kwargs` (keyword arguments) — nomlangan argumentlarni istalgan sonda qabul qiladi. Ular funksiya ichida **dictionary** sifatida keladi.

```python
def profil(**kwargs):
    print(kwargs)
    for kalit, qiymat in kwargs.items():
        print(f"{kalit}: {qiymat}")

profil(ism="Aziza", yosh=23, shahar="Namangan")
```

```
{'ism': 'Aziza', 'yosh': 23, 'shahar': 'Namangan'}
ism: Aziza
yosh: 23
shahar: Namangan
```

## Barchasini birga ishlatish

Bitta funksiyada oddiy parametr, `*args` va `**kwargs` birga ishlatilishi mumkin — lekin qat'iy tartibda:

```python
def malumot(ism, *args, **kwargs):
    print(f"Ism: {ism}")
    print(f"Qo'shimcha (args): {args}")
    print(f"Kalit-qiymat (kwargs): {kwargs}")

malumot("Sardor", 25, "Toshkent", kasb="dasturchi", tajriba=3)
```

```
Ism: Sardor
Qo'shimcha (args): (25, 'Toshkent')
Kalit-qiymat (kwargs): {'kasb': 'dasturchi', 'tajriba': 3}
```

**Tartib qoidasi:** `def funksiya(oddiy_parametr, *args, standart=qiymat, **kwargs):` — oddiy parametrlar, keyin `*args`, keyin standart qiymatli parametrlar, oxirida `**kwargs`.

## Listni/dictionary'ni funksiyaga "yozib" (unpack) uzatish

`*` va `**` funksiyani chaqirishda ham ishlatilishi mumkin — mavjud list/dictionary'ni alohida argumentlarga "yoyib" beradi:

```python
def qoshish(a, b, c):
    return a + b + c

sonlar = [1, 2, 3]
print(qoshish(*sonlar))     # bu qoshish(1, 2, 3) ga teng — 6

parametrlar = {"a": 10, "b": 20, "c": 30}
print(qoshish(**parametrlar))  # bu qoshish(a=10, b=20, c=30) ga teng — 60
```

Bu texnika real loyihalarda, ayniqsa ma'lumotlar bazasidan yoki API'dan kelgan dictionary'larni to'g'ridan-to'g'ri funksiyaga uzatishda juda ko'p ishlatiladi.

## Amaliy misol: moslashuvchan statistika funksiyasi

```python
def statistika(*sonlar):
    if not sonlar:
        return "Sonlar berilmagan"
    return {
        "yigindi": sum(sonlar),
        "ortacha": sum(sonlar) / len(sonlar),
        "eng_katta": max(sonlar),
        "eng_kichik": min(sonlar)
    }

natija = statistika(4, 8, 15, 16, 23, 42)
for kalit, qiymat in natija.items():
    print(f"{kalit}: {qiymat}")
```

```
yigindi: 108
ortacha: 18.0
eng_katta: 42
eng_kichik: 4
```

## Amaliy misol: sozlanuvchan profil generatori

```python
def profil_yarat(ism, **qoshimcha):
    natija = f"Ism: {ism}"
    for kalit, qiymat in qoshimcha.items():
        natija += f", {kalit}: {qiymat}"
    return natija

print(profil_yarat("Kamron"))
print(profil_yarat("Kamron", yosh=21))
print(profil_yarat("Kamron", yosh=21, shahar="Xorazm", kasb="talaba"))
```

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. `*args` yordamida istalgan sondagi sonni qabul qilib, ularning ko'paytmasini qaytaruvchi funksiya yozing.
2. `**kwargs` yordamida foydalanuvchi ma'lumotlarini qabul qilib, har birini alohida qatorda chop etuvchi funksiya yozing.
3. `*args` yordamida berilgan sonlar orasidan eng kichigini topuvchi funksiya yozing.

🟡 **O'rta daraja**

4. Talabalarning istalgan sondagi bahosini (`*args`) qabul qilib, o'rtacha bahoni va eng yuqori bahoni qaytaruvchi funksiya yozing.
5. Mavjud list'dagi sonlarni `*` orqali "yoyib" (unpacking) funksiyaga uzatishga misol yozing (masalan `yigindi(*[1,2,3,4,5])`).
6. Restoran buyurtma tizimi: `buyurtma(mijoz_ismi, *taomlar, **qoshimcha_malumot)` funksiyasini yozing — u mijoz ismi, buyurtma qilingan taomlar ro'yxati va qo'shimcha ma'lumotlarni (masalan yetkazib berish manzili) chiroyli formatda chop etsin.

---

**Oldingi mavzu:** [15 — Funksiyalar — asoslar](./15_funksiyalar_asoslar.md)
**Keyingi mavzu:** [17 — Lambda funksiyalar](./17_lambda_funksiyalar.md)
