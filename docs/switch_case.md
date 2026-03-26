# MATCH-CASE

Python'da match-case (Strukturali Pattern Matching) operatori 3.10 versiyasidan boshlab kiritilgan. Bu operator an'anaviy if-elif-else zanjirining yanada o'qishli va kuchliroq muqobili hisoblanadi.

Quyida match-caseni qo'llashning asosiy usullarini ko'rib chiqamiz:

1. Oddiy qiymatlarni solishtirish
Bu eng ko'p tarqalgan usul bo'lib, o'zgaruvchi ma'lum bir qiymatga tengligini tekshiradi.


```python
status_code = 404

match status_code:
    case 200:
        print("Muvaffaqiyatli!")
    case 404:
        print("Sahifa topilmadi.")
    case 500:
        print("Server xatosi.")
    case _:
        print("Noma'lum xatolik.")
```

    Sahifa topilmadi.
    

Eslatma: _ (pastki chiziq) belgisi "wildcard" (universal) belgi bo'lib, yuqoridagi variantlarning hech biri mos kelmasa ishlaydi (else kabi).

2. Bir nechta qiymatni guruhlash
Agar bir nechta holat uchun bitta natija kerak bo'lsa, | (OR - yoki) belgisidan foydalanamiz.


```python
day = "Shanba"

match day:
    case "Dushanba" | "Seshanba" | "Chorshanba" | "Payshanba" | "Juma":
        print("Ish kuni")
    case "Shanba" | "Yakshanba":
        print("Dam olish kuni")
```

    Dam olish kuni
    

3. Ro'yxatlar va Tuple bilan ishlash
match-case nafaqat qiymatni, balki ma'lumotning tuzilishini (strukturasini) ham tekshira oladi.


```python
command = ["move", "right", 10]

match command:
    case ["stop"]:
        print("To'xtash buyrug'i berildi.")
    case ["move", direction, distance]:
        print(f"{direction} yo'nalishida {distance} qadam yurish.")
    case ["jump", *others]:
        print(f"Sakrash va boshqa parametrlar: {others}")
```

    right yo'nalishida 10 qadam yurish.
    

Ro'yxatlar (Lists) bilan murakkab shartlar
Ro'yxat ichidagi elementlarning qiymatini tekshirishda juda qo'l keladi:


```python
items = ["apple", 5]

match items:
    case [name, count] if count > 10:
        print(f"Omborda {name} juda ko'p.")
    case [name, count] if count > 0:
        print(f"Bizda {count} ta {name} bor.")
    case [name, 0]:
        print(f"{name} tugagan.")
```

    Bizda 5 ta apple bor.
    

4. Shartli tekshirish (Guards)
case ichida qo'shimcha if sharti qo'shish imkoniyati mavjud.


```python
age = 25

match age:
    case n if n < 18:
        print("Siz hali voyaga yetmagansiz.")
    case n if 18 <= n < 60:
        print("Siz mehnat yoshidasiz.")
    case _:
        print("Siz nafaqadasiz.")
```

    Siz mehnat yoshidasiz.
    

Raqamlarni oraliq bo'yicha tekshirish
Tasavvur qiling, haroratga qarab tavsiya bermoqchisiz:


```python
temperature = 25

match temperature:
    case t if t < 0:
        print("Juda sovuq, qalin kiyining!")
    case t if 0 <= t <= 20:
        print("Havo salqin.")
    case t if 21 <= t <= 30:
        print("Havo juda yaxshi, sayrga chiqing.")
    case _:
        print("Kun issiq.")
```

    Havo juda yaxshi, sayrga chiqing.
    

Bir nechta o'zgaruvchini solishtirish
if yordamida match qilinayotgan o'zgaruvchini tashqi o'zgaruvchilar bilan ham solishtirish mumkin:


```python
allowed_user = "admin"
current_user = {"name": "Ali", "role": "admin"}

match current_user:
    case {"name": name, "role": role} if role == allowed_user:
        print(f"Kirishga ruxsat berildi, {name}!")
    case _:
        print("Kirish taqiqlangan.")
```

    Kirishga ruxsat berildi, Ali!
    

5. Lug'atlar (Dictionaries) bilan ishlash
Ma'lumotlar bazasi yoki API'dan kelgan JSON formatidagi ma'lumotlarni saralashda juda qulay.


```python
user = {"name": "Ali", "role": "admin"}

match user:
    case {"name": name, "role": "admin"}:
        print(f"Xush kelibsiz, Admin {name}!")
    case {"name": name, "role": "user"}:
        print(f"Xush kelibsiz, Foydalanuvchi {name}!")
```

    Xush kelibsiz, Admin Ali!
    

Nima uchun match-case yaxshi?  
* O'qishli: Murakkab if-elif zanjirlaridan ko'ra tushunarliroq.

* Xavfsiz: Strukturani tekshirish orqali xatolarni oldini oladi.

* Tez: Ma'lum holatlarda if-elsega qaraganda tezroq ishlashi mumkin.

# TOPSHIRIQ

#### 1-qism: Sonlar bilan ishlash (Math & Logic)

* Musbat/Manfiy: Son kiritilganda uning musbat, manfiy yoki nol ekanini aniqlang.  

* Juft/Toq: Sonning juft yoki toqligini match n if n % 2 == 0 ko'rinishida tekshiring.  

* 3 ga bo'linish: Son 3 ga qoldiqsiz bo'linishini tekshiring.  

* Katta-kichik: x soni kiritilganda, u 100 dan katta yoki kichikligini aniqlang.  

* Oraliq (Range): Ball kiritilganda (0-100), u 50 dan yuqori yoki pastligini if bilan tekshiring.  

* Ikkita sonni solishtirish: Faqat bitta match x: ichida if x > y sharti bilan ikkita sonni solishtiring.  

* Yil tekshiruvi: Kiritilgan yil kabisa yili ekanini tekshiring (4 ga bo'linishi sharti bilan).  

* Hafta kuni raqami: 1 dan 7 gacha son kiritilganda kun nomini chiqaring.  

* Farengeyt/Selsiy: Harorat 0 dan past bo'lsa "Muzlash nuqtasi" deb chiqaring.  

* Kvadrat son: Sonning ildizi butun son ekanini if orqali tekshiring.  

#### 2-qism: Satrlar (Strings) bilan ishlash

* Salomlashish: Kiritilgan so'z "Salom" bo'lsa "Alik", "Xayr" bo'lsa "Omon bo'ling" deb javob bering.  

* Uzunlik tekshiruvi: Matn kiritilganda s if len(s) > 10 bo'lsa "Uzun matn" deb chiqaring.  

* Bo'sh satr: Foydalanuvchi hech narsa kiritmaganini (bo'sh qator) case "" orqali aniqlang.  

* Parol xavfsizligi: Parol kiritilganda p if "123" in p bo'lsa "Juda oddiy parol" deb ogohlantiring.  

* Tilni aniqlash: "uz", "en", "ru" kodlari kiritilganda mos til nomini chiqaring.  

* Katta-kichik harf: Matn faqat katta harflardan iboratligini if s.isupper() bilan tekshiring.  

* Ism tahlili: Ism kiritilganda, agar u "A" harfi bilan boshlansa, maxsus xabar chiqaring.  

* Sonli satr: Satr ichida faqat raqamlar borligini if s.isdigit() orqali tekshiring.  

* Email belgisi: Kiritilgan matnda @ belgisi bor-yo'qligini if "@" in s bilan aniqlang.  

* Unli harf: Kiritilgan bitta harf unli yoki undoshligini case "a" | "e" | "i" | "o" | "u" ko'rinishida tekshiring.
