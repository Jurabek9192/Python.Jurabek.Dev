# 21 — FUNKSIYALAR. LAMBDA VA SO'NGSO'Z

## Lambda — nomsiz, bir qatorlik funksiya

```python
kvadrat = lambda x: x ** 2
print(kvadrat(5))     # 25

qoshish = lambda a, b: a + b
print(qoshish(3, 5))     # 8
```

## Lambda qачон ishlatiladi — sorted() bilan

```python
talabalar = [("Ali", 85), ("Vali", 92), ("Guli", 78)]
saralangan = sorted(talabalar, key=lambda t: t[1])
print(saralangan)
```

## map() va filter()

```python
sonlar = [1, 2, 3, 4, 5]
kvadratlar = list(map(lambda x: x**2, sonlar))
juftlar = list(filter(lambda x: x % 2 == 0, sonlar))
```

## Funksiyalarni yaxshi yozish tamoyillari — xulosa

1. **Bitta funksiya — bitta vazifa** (Single Responsibility)
2. **Mazmunli nomlar** — `hisobla()` emas, `bmi_hisobla()`
3. **Kichik funksiyalar** — 20-30 qatordan oshsa, bo'lib tashlashni o'ylab ko'ring
4. **Docstring yozing** — boshqalar (va o'zingiz) tushunishi uchun
5. **Global o'zgaruvchidan saqlaning** — parametr va `return` orqali ishlang

## Funksiyalar — nima o'rgandik

Ushbu bo'limda funksiyaning barcha asosiy qirralarini o'rgandik: oddiy funksiya, parametrlar, `return`, `*args`/`**kwargs`, lambda. Bu — dasturlashning eng muhim vositalaridan biri, chunki u kodni tartibli va qayta ishlatiladigan qiladi.

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ikki sonni qo'shuvchi lambda funksiya yarating.
2. Sonni 2 baravar qaytaruvchi lambda yarating.
3. `map()` va lambda bilan ro'yxatning har bir elementini 10ga ko'paytiring.
4. `filter()` va lambda bilan ro'yxatdan faqat musbat sonlarni ajrating.
5. Ism-familiyalar ro'yxatini familiya bo'yicha `sorted()` va lambda bilan saralang.
6. Lambda ichida ternary (`if/else`) ishlatib, son juft/toqligini aniqlang.
7. 3 ta oddiy funksiyani lambda ko'rinishida qayta yozing.
8. `sorted()` va `key=lambda` bilan so'zlar ro'yxatini uzunligiga qarab saralang.

🟡 **O'rta (9-15)**

9. Talabalar ro'yxatini (ism, baho) baho bo'yicha kamayish tartibida saralang.
10. `filter()` yordamida ro'yxatdan faqat 3 harfdan uzun so'zlarni ajrating.
11. Mahsulotlar ro'yxatini (nomi, narxi) narx bo'yicha arzondan qimmatga saralang.
12. `map()` va `filter()`ni birlashtirib, avval juft sonlarni ajratib, so'ng ularni kvadratga oshiring.
13. Lambda yordamida, ikki ro'yxatni solishtirib, kattasini qaytaruvchi funksiya yozing.
14. Ism-yosh juftliklaridan faqat 18 yoshdan katta bo'lganlarning ismlarini `filter()` va lambda bilan ajrating.
15. `sorted()` bilan, talabalar ro'yxatini avval guruh, keyin ism bo'yicha (ikki mezon bilan) saralang.

🔴 **Qiyin (16-20)**

16. Mahsulotlar ro'yxatidan (nomi, narxi, miqdori) `filter()` bilan narxi 100,000dan yuqorilarini tanlang, `map()` bilan umumiy qiymatini hisoblang, natijani `sorted()` bilan saralang — barchasini bitta zanjirda.
17. Funksiyalar haqida o'rgangan barcha bilimingizni (oddiy funksiya, `*args`, `return`, lambda) birlashtirib, "talabalar boshqaruv tizimi" (qo'shish, o'rtachasini hisoblash, eng yaxshisini topish, saralash) yozing.
18. Matnlar ro'yxatidan `filter()` va lambda bilan faqat raqam bilan boshlanmaydiganlarini ajrating.
19. Ikki xil "saralash mezoni" (masalan avval narx, keyin nom) bilan mahsulotlar ro'yxatini ikki xil tartibda chiqaring.
20. To'liq "mini-analitika" funksiyasini yozing — sonlar ro'yxatini qabul qilib, `filter`/`map`/`lambda` yordamida musbat, manfiy, juft, toq sonlar sonini alohida hisoblab, dictionary sifatida qaytarsin.

---

**Oldingi mavzu:** [20 — Modullar](./20_modullar.md)
**Keyingi mavzu:** [22 — "SON TOPISH" o'yini (amaliy loyiha)](./22_son_topish_oyini.md)
