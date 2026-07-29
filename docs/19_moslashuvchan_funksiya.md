# 19 — MOSLASHUVCHAN FUNKSIYA (*ARGS, **KWARGS)

## Muammo: nechta argument kelishi noma'lum

```python
def yigindi(*args):
    print(args)          # tuple ko'rinishida keladi
    return sum(args)

print(yigindi(1, 2, 3))          # 6
print(yigindi(5, 10, 15, 20))     # 50
```

## **kwargs — nomlangan argumentlar

```python
def profil(**kwargs):
    for kalit, qiymat in kwargs.items():
        print(f"{kalit}: {qiymat}")

profil(ism="Aziza", yosh=23, shahar="Namangan")
```

## Barchasini birga

```python
def malumot(ism, *args, **kwargs):
    print(f"Ism: {ism}")
    print(f"Qo'shimcha: {args}")
    print(f"Kalit-qiymat: {kwargs}")

malumot("Sardor", 25, "Toshkent", kasb="dasturchi")
```

## List/dict'ni funksiyaga "yoyib" uzatish

```python
def qoshish(a, b, c):
    return a + b + c

sonlar = [1, 2, 3]
print(qoshish(*sonlar))       # qoshish(1,2,3) ga teng
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. `*args` yordamida istalgan sondagi sonni qabul qilib, ularning ko'paytmasini qaytaruvchi funksiya yozing.
2. `**kwargs` yordamida foydalanuvchi ma'lumotlarini chop etuvchi funksiya yozing.
3. `*args` bilan eng kichik sonni topuvchi funksiya yozing.
4. Listni `*` bilan "yoyib", 3 argumentli funksiyaga uzating.
5. `*args` yordamida berilgan sonlarning o'rtachasini qaytaruvchi funksiya yozing.
6. `**kwargs` bilan kelgan barcha kalitlarni (faqat nomlarini) chiqaruvchi funksiya yozing.
7. Oddiy parametr + `*args` birga ishlatilgan funksiya yozing (masalan ism va bir nechta hobbi).
8. `*args` yordamida kelgan sonlar ichidan eng kattasini toping.

🟡 **O'rta (9-15)**

9. Talabalarning istalgan sondagi bahosini (`*args`) qabul qilib, statistika (o'rtacha, eng katta, eng kichik) qaytaruvchi funksiya yozing.
10. `**kwargs` yordamida, kelgan ma'lumotlar asosida "profil karta" matnini yasovchi funksiya yozing.
11. Oddiy parametr, `*args` va `**kwargs`ni birga ishlatuvchi "buyurtma" funksiyasini yozing (mijoz ismi, taomlar, qo'shimcha ma'lumot).
12. Dictionary'ni `**` bilan "yoyib", nomlangan argumentli funksiyaga uzating.
13. `*args` bilan kelgan barcha matnlarni bitta gapga birlashtiruvchi funksiya yozing.
14. Ixtiyoriy sondagi ro'yxatlarni (`*args`) qabul qilib, ularni bitta ro'yxatga birlashtiruvchi funksiya yozing.
15. `**kwargs` yordamida sozlamalar (settings) qabul qiluvchi, standart qiymatlarni qo'llovchi funksiya yozing.

🔴 **Qiyin (16-20)**

16. Restoran buyurtma tizimi: `buyurtma(mijoz_ismi, *taomlar, **qoshimcha)` funksiyasi — chiroyli chek (receipt) formatida chiqarsin.
17. `*args` va `**kwargs`dan foydalanib, istalgan sondagi va turdagi ma'lumotni qabul qiluvchi "universal logger" funksiyasini yozing.
18. Matematik amallar kalkulyatori: `hisobla(amal, *sonlar)` funksiyasi — amal turiga ("yigindi", "kopaytma") qarab natijani hisoblasin.
19. `**kwargs` yordamida, talaba ma'lumotlarini (ism majburiy, qolgani ixtiyoriy) qabul qilib, mavjud bo'lgan maydonlarni chiroyli chiqaruvchi funksiya yozing.
20. To'liq "mahsulot yaratish" funksiyasi: `mahsulot(nomi, narxi, *teglar, **xususiyatlar)` — barcha ma'lumotlarni tartibli formatda chiqarsin.

---

**Oldingi mavzu:** [18 — Funksiya va ro'yxat](./18_funksiya_va_royxat.md)
**Keyingi mavzu:** [20 — Modullar](./20_modullar.md)
