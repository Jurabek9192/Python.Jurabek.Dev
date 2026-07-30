# 13 — NESTING (ICHMA-ICH TUZILMALAR)

## Dictionary ichida list

```python
odam = {
    "ism": "Ali",
    "sevimli_mevalar": ["olma", "banan", "uzum"]
}
print(odam["sevimli_mevalar"][0])     # olma
```

## List ichida dictionary — eng ko'p uchraydigan struktura

```python
talabalar = [
    {"ism": "Ali", "baho": 90},
    {"ism": "Vali", "baho": 85}
]

for talaba in talabalar:
    print(f"{talaba['ism']}: {talaba['baho']}")
```

Bu struktura — real dunyoda API'lardan keladigan ma'lumotlarning (JSON) eng tipik ko'rinishi.

## Dictionary ichida dictionary

```python
foydalanuvchilar = {
    "user1": {"ism": "Ali", "yosh": 20},
    "user2": {"ism": "Vali", "yosh": 22}
}
print(foydalanuvchilar["user1"]["ism"])     # Ali
```

## Chuqur nesting bilan ishlash

```python
maktab = {
    "sinf_A": {
        "talabalar": ["Ali", "Vali"],
        "ustoz": "Karimov"
    },
    "sinf_B": {
        "talabalar": ["Guli", "Laylo"],
        "ustoz": "Sodiqova"
    }
}

for sinf, malumot in maktab.items():
    print(f"{sinf}: ustoz {malumot['ustoz']}, talabalar: {malumot['talabalar']}")
```

## Ichma-ich strukturaga yangi element qo'shish

```python
maktab["sinf_A"]["talabalar"].append("Sardor")
print(maktab["sinf_A"]["talabalar"])
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ism va sevimli ranglar (list) dan iborat dictionary yarating.
2. 3 ta talabadan iborat, har biri ism va baho bo'lgan list-of-dictionaries yarating.
3. Ichma-ich dictionary yaratib (2 ta foydalanuvchi), ularning ismlarini chiqaring.
4. List ichidagi dictionary'ga yangi kalit-qiymat qo'shing.
5. Dictionary ichidagi listga yangi element (`append`) qo'shing.
6. Ichma-ich strukturadan muayyan qiymatni (masalan `data["a"]["b"]`) o'qing.
7. 2 ta mahsulot uchun {nomi, narxi, miqdori} strukturasidan iborat list yarating.
8. Talabalar list-of-dict'idan barcha ismlarni alohida listga yig'ing.

🟡 **O'rta (9-15)**

9. Talabalar list-of-dict'idan (ism, baho) eng yuqori bahoga ega talabani toping.
10. Sinf-talabalar strukturasidan (dictionary ichida list) barcha talabalar sonini hisoblang.
11. Ichma-ich dictionary'dan (foydalanuvchilar) barcha 20 yoshdan katta foydalanuvchilarni filtrlang.
12. Mahsulotlar list-of-dict'idan (nomi, narxi, miqdori) umumiy inventar qiymatini hisoblang.
13. Ikki sinf o'quvchilari ro'yxatini (ichma-ich struktura) birlashtirib, umumiy talabalar ro'yxatini yasang.
14. Talabalar list-of-dict'iga yangi talaba qo'shing va ro'yxatni baho bo'yicha saralab chiqaring.
15. Har bir talabada bir nechta fan bahosi (list) bo'lgan strukturani yarating va har birining o'rtachasini hisoblang.

🔴 **Qiyin (16-20)**

16. To'liq "maktab" strukturasi (bir nechta sinf, har birida talabalar va ustoz) yarating va har bir sinfning o'rtacha talaba yoshini hisoblang (agar yosh ma'lumoti qo'shilsa).
17. Ichma-ich JSON-ga o'xshash struktura (buyurtmalar -> mijoz -> mahsulotlar ro'yxati) yarating va umumiy savdo summasini hisoblang.
18. Do'kon inventari: mahsulot nomi kalit, {narx, miqdor, kategoriya} qiymat — kategoriya bo'yicha guruhlab, har bir kategoriya umumiy qiymatini chiqaring.
19. Ijtimoiy tarmoq simulyatori: foydalanuvchilar dictionary'si, har birida "do'stlar" (list) maydoni — ikkita foydalanuvchining umumiy do'stlarini toping.
20. To'liq talabalar jurnali strukturasini (ism, guruh, fanlar va baholar dictionary) yarating, guruh bo'yicha o'rtacha bahoni hisoblab chiqaring.

---

**Oldingi mavzu:** [12 — Dictionary bilan tanishuv](./12_dictionary.md)
**Keyingi mavzu:** [14 — While tsikli](./14_while.md)
