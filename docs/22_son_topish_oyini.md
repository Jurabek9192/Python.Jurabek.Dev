# 22 — "SON TOPISH" O'YINI (AMALIY LOYIHA)

## Loyiha haqida

Bu — birinchi katta amaliy loyihamiz. Unda `random`, `while`, `if/elif/else`, `try/except` va funksiyalarni birlashtiramiz.

## O'yin qoidasi

Kompyuter 1 dan 100 gacha bo'lgan tasodifiy sonni "o'ylaydi". Foydalanuvchi uni cheklangan urinishlar sonida topishi kerak. Har urinishdan keyin "kattaroq" yoki "kichikroq" ko'rsatkichi beriladi.

## To'liq kod

```python
import random

def oyin():
    maxfiy_son = random.randint(1, 100)
    urinishlar_soni = 7
    ishlatilgan = 0

    print("1 dan 100 gacha sonni o'yladim. Uni toping!")
    print(f"Sizda {urinishlar_soni} ta urinish bor.")

    while ishlatilgan < urinishlar_soni:
        try:
            taxmin = int(input("Taxminingiz: "))
        except ValueError:
            print("Iltimos, faqat son kiriting!")
            continue

        ishlatilgan += 1

        if taxmin < maxfiy_son:
            print(f"Kattaroq son kiriting! (Qolgan urinishlar: {urinishlar_soni - ishlatilgan})")
        elif taxmin > maxfiy_son:
            print(f"Kichikroq son kiriting! (Qolgan urinishlar: {urinishlar_soni - ishlatilgan})")
        else:
            print(f"Tabriklaymiz! Siz {ishlatilgan} ta urinishda topdingiz!")
            return

    print(f"Afsuski, urinishlar tugadi. Maxfiy son {maxfiy_son} edi.")

if __name__ == "__main__":
    oyin()
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Yuqoridagi kodni o'zingiz qo'lda qayta yozib, ishga tushiring va bir necha marta o'ynang.
2. Urinishlar sonini 7 dan 10 ga o'zgartiring.
3. Sonlar oralig'ini 1-100 dan 1-50 ga o'zgartiring.
4. O'yin boshida foydalanuvchi ismini so'rab, xabarlarga ismini qo'shing.
5. Har muvaffaqiyatsiz urinishdan keyin, nechta urinish qolganini aniqroq ko'rsating.
6. O'yin tugagach, "Yana o'ynaysizmi? (ha/yo'q)" deb so'rab, "ha" bo'lsa qaytadan boshlang.
7. Agar foydalanuvchi son o'rniga matn kiritsa, dastur qulamasligini tekshiring.
8. O'yinni ishga tushirib, qasddan 3 marta xato ma'lumot (matn) kiritib, dastur qanday reaksiya berishini kuzating.

🟡 **O'rta (9-15)**

9. Qiyinlik darajasini tanlash imkonini qo'shing (oson=15 urinish, o'rta=10, qiyin=5).
10. Har bir o'yindan keyin natijani (ism, urinishlar soni) faylga yozib boring (Kitob 2 bilimidan foydalaning, agar bilsangiz).
11. "Eng yaxshi natija" (eng kam urinishda topilgan) ni saqlab, har o'yin oxirida ko'rsating.
12. Sonlar oralig'ini foydalanuvchi o'zi kiritadigan qilib o'zgartiring (masalan 1 dan N gacha, N — kiritiladi).
13. Har bir taxminning "qanchalik yaqin" ekanligini ham ko'rsating (masalan farq 1-5 bo'lsa "juda yaqin!").
14. O'yinni funksiyalarga to'liq bo'lib chiqing: `sozlamalarni_olish()`, `oyin_jarayoni()`, `natijani_korsat()`.
15. Kompyuter foydalanuvchi o'rniga o'ynaydigan versiyasini yozing — kompyuter o'zi "aqlli" taxmin qiladi (binary search mantig'ida: har safar o'rtani tanlaydi).

🔴 **Qiyin (16-20)**

16. To'liq statistika tizimi qo'shing: nechta o'yin o'ynalgani, o'rtacha urinishlar soni, eng yaxshi va eng yomon natija.
17. Ikki o'yinchili versiya yasang — ikkalasi ham navbat bilan taxmin qiladi, birinchi topgan g'olib bo'ladi.
18. "Vaqt cheklovi" qo'shing (`time` moduli yordamida) — agar foydalanuvchi 30 soniyada javob bermasa, urinish "yonib ketadi".
19. O'yinni to'liq OOP asosida (`OyinKlassi`) qayta yozing — holat (state) va metodlar orqali.
20. Multiplyer/level tizimi qo'shing — har yutilgan o'yinda "daraja" oshib boradi va son oralig'i kengayadi (masalan 1-daraja: 1-50, 2-daraja: 1-100, va h.k.).

---

**Oldingi mavzu:** [21 — Lambda va so'ngso'z](./21_lambda_songsoz.md)
**Keyingi mavzu:** [23 — "SO'Z TOPISH" o'yini (amaliy loyiha)](./23_soz_topish_oyini.md)
