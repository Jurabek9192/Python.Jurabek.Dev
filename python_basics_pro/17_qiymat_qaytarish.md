# 17 — QIYMAT QAYTARUVCHI FUNKSIYA

## return — natijani qaytarish

```python
def qoshish(a, b):
    return a + b

natija = qoshish(5, 3)
print(natija)      # 8
```

## print() vs return — muhim farq

```python
def qoshish_print(a, b):
    print(a + b)      # faqat ko'rsatadi, qaytarmaydi

def qoshish_return(a, b):
    return a + b        # qaytaradi, keyin ishlatsa bo'ladi

x = qoshish_print(5, 3)      # ekranga 8 chiqadi
print(x)                        # None!

y = qoshish_return(5, 3)      # hech narsa chiqmaydi
print(y)                         # 8
```

**Qoida:** Agar natijadan keyin foydalanish kerak bo'lsa — `return` ishlating.

## return — funksiyani darhol to'xtatadi

```python
def tekshir(son):
    if son < 0:
        return "Manfiy"
    return "Musbat yoki nol"
```

## Bir nechta qiymat qaytarish (tuple orqali)

```python
def minmax(sonlar):
    return min(sonlar), max(sonlar)

kichik, katta = minmax([5, 2, 9, 1])
print(kichik, katta)     # 1 9
```

## Zamonaviy imkoniyat — funksiyaga type hint qo'shish

```python
def qoshish(a: int, b: int) -> int:
    return a + b
```

Bu — Python'ga majburiy emas, lekin kodni tushunarli qiladi va IDE'lar tomonidan tekshiriladi.

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ikki sonni qo'shib, natijani `return` qiluvchi funksiya yozing va natijani o'zgaruvchiga saqlang.
2. Ikki sonning ko'paytmasini qaytaruvchi funksiya yozing.
3. Sonning juft/toqligini "juft"/"toq" ko'rinishida qaytaruvchi funksiya yozing.
4. Ism qabul qilib, "Salom, [ism]!" matnini qaytaruvchi (chop etmasdan) funksiya yozing.
5. `print()` va `return` orqali yozilgan ikkita funksiyani solishtiring — natijalarini o'zgaruvchiga saqlab, farqini ko'ring.
6. Uch sonning eng kattasini qaytaruvchi funksiya yozing (`max()`siz).
7. To'rtburchakning yuzi va perimetrini ikkita alohida qiymat sifatida (tuple orqali) qaytaruvchi funksiya yozing.
8. Sonlar ro'yxatini qabul qilib, ularning o'rtachasini qaytaruvchi funksiya yozing.

🟡 **O'rta (9-15)**

9. Matnni qabul qilib, undagi unli harflar sonini qaytaruvchi funksiya yozing.
10. Sonni qabul qilib, u tub son (prime) ekanligini `True`/`False` qaytaruvchi funksiya yozing.
11. Ikki sonni qabul qilib, ularning EKUB (eng katta umumiy bo'luvchisi)ni qaytaruvchi funksiya yozing.
12. Celsius'ni Fahrenheit'ga, va aksincha, aylantiruvchi ikkita funksiya yozing — ular bir-birini "tekshirsin" (natijani qaytadan aylantirib, asl qiymatga tenglik tekshiriladi).
13. Ro'yxatni qabul qilib, undagi eng katta va eng kichik qiymatlarni tuple sifatida qaytaruvchi funksiya yozing.
14. Type hint bilan to'liq annotatsiyalangan (`-> int`, `-> str` va h.k.) 3 ta funksiya yozing.
15. Sonning faktorialini qaytaruvchi funksiya yozing.

🔴 **Qiyin (16-20)**

16. Talaba ma'lumotlarini (ism, baholar ro'yxati) qabul qilib, o'rtacha bahoni va harf bahoni (A/B/C/D/F) tuple sifatida qaytaruvchi funksiya yozing.
17. Ikki sonni qabul qilib, ularning yig'indisi, ayirmasi, ko'paytmasi va bo'linmasini (4 ta qiymat) birdaniga qaytaruvchi funksiya yozing.
18. Matnni qabul qilib, u palindrom ekanligini tekshiruvchi va tushuntiruvchi matn (masalan "Ha, bu palindrom" yoki "Yo'q, bu palindrom emas") qaytaruvchi funksiya yozing.
19. Ro'yxatni qabul qilib, undagi barcha tub sonlarni yangi ro'yxat sifatida qaytaruvchi funksiya yozing (boshqa, tub sonni tekshiruvchi funksiyani ichida chaqirsin).
20. To'liq BMI kalkulyatori funksiyasi — vazn va bo'yni qabul qilib, BMI qiymati va toifasini (kam vazn/normal/ortiqcha/semizlik) tuple sifatida qaytarsin.

---

**Oldingi mavzu:** [16 — Funksiya](./16_funksiya.md)
**Keyingi mavzu:** [18 — Funksiya va ro'yxat](./18_funksiya_va_royxat.md)
