# 23 — "SO'Z TOPISH" O'YINI (AMALIY LOYIHA)

## Loyiha haqida

Mashhur "Hangman" o'yinining Python versiyasi. Kompyuter so'z "o'ylaydi", foydalanuvchi harflarni taxmin qiladi.

## To'liq kod

```python
import random

def oyin():
    sozlar = ["python", "dasturlash", "kompyuter", "robototexnika", "algoritm"]
    maxfiy_soz = random.choice(sozlar)
    topilgan_harflar = ["_"] * len(maxfiy_soz)
    ishlatilgan_harflar = []
    xatolar = 0
    max_xato = 6

    print("SO'Z TOPISH O'YINI!")
    print(" ".join(topilgan_harflar))

    while xatolar < max_xato and "_" in topilgan_harflar:
        harf = input("Bir harf kiriting: ").lower()

        if len(harf) != 1 or not harf.isalpha():
            print("Iltimos, bitta harf kiriting!")
            continue

        if harf in ishlatilgan_harflar:
            print("Bu harfni allaqachon ishlatgansiz!")
            continue

        ishlatilgan_harflar.append(harf)

        if harf in maxfiy_soz:
            print("To'g'ri!")
            for i, s in enumerate(maxfiy_soz):
                if s == harf:
                    topilgan_harflar[i] = harf
        else:
            xatolar += 1
            print(f"Noto'g'ri! Xatolar: {xatolar}/{max_xato}")

        print(" ".join(topilgan_harflar))

    if "_" not in topilgan_harflar:
        print(f"Tabriklaymiz! So'zni topdingiz: {maxfiy_soz}")
    else:
        print(f"Afsuski, yutqazdingiz. So'z: {maxfiy_soz} edi.")

if __name__ == "__main__":
    oyin()
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Yuqoridagi kodni qo'lda qayta yozing va bir necha marta o'ynang.
2. So'zlar ro'yxatiga o'zingizning 5 ta so'zingizni qo'shing.
3. `max_xato` qiymatini 6 dan 8 ga o'zgartiring.
4. Har noto'g'ri urinishdan keyin, qolgan xatolar sonini aniqroq ko'rsating.
5. O'yin boshida foydalanuvchi ismini so'rab, xabarlarga qo'shing.
6. Katta harf bilan kiritilgan harfni ham to'g'ri qabul qilishini tekshiring (`.lower()` ishlayaptimi).
7. Ikki xonali son yoki belgi kiritib, dastur to'g'ri xatolik berishini tekshiring.
8. O'yin tugagach, "Yana o'ynaysizmi?" deb so'rang.

🟡 **O'rta (9-15)**

9. Qiyinlik darajasi qo'shing — oson (qisqa so'zlar), qiyin (uzun so'zlar).
10. Foydalanuvchiga "yordam" (bitta harfni bepul ochish) imkoniyatini bering, lekin faqat 1 marta ishlatilsin.
11. So'zlar ro'yxatini kategoriyalarga bo'ling (hayvonlar, mevalar, kasblar) va foydalanuvchi kategoriya tanlasin.
12. "ASCII rasm" qo'shing — har xatoda oddiy matn bilan "osilgan odam" rasmi bosqichma-bosqich chiqsin.
13. O'yin natijalarini (g'alaba/mag'lubiyat, ishlatilgan urinishlar) statistika sifatida saqlab boring.
14. Butun so'zni (harflarni emas) taxmin qilish imkoniyatini ham qo'shing.
15. Ikki o'yinchili versiya — biri so'z o'ylaydi (kiritadi), ikkinchisi topadi.

🔴 **Qiyin (16-20)**

16. So'zlar ro'yxatini alohida faylda (`.txt` yoki `.json`) saqlang va o'yin boshida o'sha fayldan o'qing.
17. To'liq statistika tizimi: nechta o'yin o'ynalgan, nechtasida yutilgan, eng ko'p ishlatilgan harflar.
18. Vaqt chegarasi qo'shing — har bir harf uchun 15 soniya, vaqt tugasa xato hisoblansin.
19. O'yinni to'liq OOP asosida (`SozTopishOyini` klassi) qayta yozing.
20. Ikki tilli (o'zbek va ingliz) versiyasini yasang — foydalanuvchi til tanlasin, mos so'zlar ro'yxati va xabarlar ishlatilsin.

---

**Oldingi mavzu:** [22 — "SON TOPISH" o'yini](./22_son_topish_oyini.md)
**Keyingi mavzu:** [24 — RegEx (matn andozalari)](./24_regex.md)
