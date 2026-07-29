# LAMBDA FUNKSIYALAR

## Lambda nima?

**Lambda funksiya** — nomsiz (anonymous), bir qatorlik, oddiy funksiya. U `def` o'rniga `lambda` kalit so'zi bilan yaratiladi va odatda juda qisqa, bir martalik vazifalar uchun ishlatiladi.

```python
# oddiy funksiya
def kvadrat(x):
    return x ** 2

# xuddi shu narsa — lambda ko'rinishida
kvadrat_lambda = lambda x: x ** 2

print(kvadrat(5))          # 25
print(kvadrat_lambda(5))    # 25
```

## Sintaksis

```
lambda parametrlar: ifoda
```

- `return` kalit so'zi yozilmaydi — natija avtomatik qaytariladi
- Faqat **bitta ifoda** yozish mumkin, bir nechta qator yoki `if/for` bloklarini to'liq yozib bo'lmaydi

```python
qoshish = lambda a, b: a + b
print(qoshish(3, 5))    # 8

salomlash = lambda ism: f"Salom, {ism}!"
print(salomlash("Dilnoza"))
```

## Lambda ichida shart

Lambda ichida to'liq `if/else` bloki bo'lmaydi, lekin ternary operator ishlatish mumkin:

```python
juft_yoki_toq = lambda son: "juft" if son % 2 == 0 else "toq"
print(juft_yoki_toq(7))    # toq
print(juft_yoki_toq(8))    # juft
```

## Lambda qachon ishlatiladi?

Lambda odatda **mustaqil o'zgaruvchiga yozilmaydi** — u boshqa funksiyalarga argument sifatida, bir martalik ishlatish uchun beriladi. Eng ko'p uchraydigan holatlar: `sorted()`, `map()`, `filter()`.

### 1. sorted() bilan — maxsus saralash kaliti

```python
talabalar = [("Ali", 85), ("Vali", 92), ("Guli", 78)]

# baho bo'yicha saralash
saralangan = sorted(talabalar, key=lambda talaba: talaba[1])
print(saralangan)
```

```
[('Guli', 78), ('Ali', 85), ('Vali', 92)]
```

Bu yerda `key=lambda talaba: talaba[1]` Python'ga "har bir elementning 1-indeksidagi (baho) qiymatiga qarab saralashni" buyuradi.

```python
# kamayish tartibida
saralangan_teskari = sorted(talabalar, key=lambda talaba: talaba[1], reverse=True)
print(saralangan_teskari)
```

### 2. map() bilan — har bir elementga funksiya qo'llash

```python
sonlar = [1, 2, 3, 4, 5]
kvadratlar = list(map(lambda x: x ** 2, sonlar))
print(kvadratlar)     # [1, 4, 9, 16, 25]
```

`map()` — berilgan funksiyani ro'yxatning **har bir** elementiga qo'llaydi va natijalarni qaytaradi (natija `map` obyekti bo'lgani uchun ko'pincha `list()` bilan o'raladi).

### 3. filter() bilan — shartga mos elementlarni tanlash

```python
sonlar = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
juftlar = list(filter(lambda x: x % 2 == 0, sonlar))
print(juftlar)     # [2, 4, 6, 8, 10]
```

`filter()` — funksiya `True` qaytargan elementlarnigina saqlab qoladi.

## Lambda vs def — qachon qaysi biri?

| Holat | Tanlov |
|---|---|
| Funksiya bir necha marta ishlatiladi | `def` |
| Funksiya murakkab mantiqqa ega (bir necha qator, shart, tsikl) | `def` |
| Funksiya boshqa funksiyaga (masalan `sorted`) bir martalik argument sifatida beriladi | `lambda` |
| Kodni tushunarli, o'qish oson qilish muhim | ko'pincha `def` afzal |

**Amaliy maslahat:** Lambda kuchli vosita, lekin ortiqcha ishlatilsa kodni o'qishni qiyinlashtiradi. Agar lambda mantig'i murakkablashsa yoki uni bir necha joyda ishlatish kerak bo'lsa — bemalol oddiy `def` funksiyasiga o'ting.

## Amaliy misol: mahsulotlarni narxi bo'yicha saralash

```python
mahsulotlar = [
    {"nom": "Noutbuk", "narx": 8000000},
    {"nom": "Sichqoncha", "narx": 150000},
    {"nom": "Klaviatura", "narx": 300000}
]

arzon_dan_qimmat = sorted(mahsulotlar, key=lambda m: m["narx"])
for m in arzon_dan_qimmat:
    print(f"{m['nom']}: {m['narx']:,} so'm")
```

```
Sichqoncha: 150,000 so'm
Klaviatura: 300,000 so'm
Noutbuk: 8,000,000 so'm
```

## Amaliy misol: matnlarni uzunligiga qarab saralash

```python
sozlar = ["dastur", "AI", "kompyuter", "kod", "robototexnika"]
saralangan = sorted(sozlar, key=lambda soz: len(soz))
print(saralangan)
```

```
['AI', 'kod', 'dastur', 'kompyuter', 'robototexnika']
```

---

## 🎯 Mashqlar

🟢 **Oson daraja**

1. Ikki sonni qo'shuvchi lambda funksiya yarating va uni chaqiring.
2. Sonni qabul qilib, uni 2 baravar qaytaruvchi lambda yarating.
3. Sonlar ro'yxatini `map()` va lambda yordamida barcha elementlarini 10 ga ko'paytiring.

🟡 **O'rta daraja**

4. Sonlar ro'yxatidan faqat 50 dan katta bo'lganlarini `filter()` va lambda yordamida ajratib oling.
5. Ism-familiyalar ro'yxatini (`["Vali Aliyev", "Ali Karimov", "Zebo Nabiyeva"]`) familiya bo'yicha alifbo tartibida saralang (`lambda` va `sorted()` dan foydalaning).
6. Talabalar ro'yxati (ism va baho) berilgan — ularni baho bo'yicha kamayish tartibida saralang va eng yuqori 3 talabani chiqaring.

🔴 **Murakkabroq**

7. Mahsulotlar ro'yxati (nom, narx, miqdor) berilgan — `filter()` yordamida faqat narxi 100,000 dan yuqori bo'lganlarini tanlang, so'ng `map()` yordamida har birining umumiy qiymatini (narx × miqdor) hisoblab, yangi ro'yxat hosil qiling.

---

**Oldingi mavzu:** [16 — Funksiya argumentlari (*args, **kwargs)](./16_funksiya_argumentlari.md)
**Keyingi mavzu:** [18 — List comprehension](./18_list_comprehension.md)
