# WHILE TSIKLI

while tsikli bilan tanishamiz.

#### YANA input()

Dasturlar foydalanuvchilarning mauammolarini hal qilish uchun yoziladi. Buning uchun esa foydalanuvchi bilan aloqa o'rnatish undan turli ma'lumotlarni qabul qilib olish va ularni qayta ishlash talab qilinadi.
Misol uchun, dasturimiz foydalanuvchiga ismi bilan murojaat qilishi uchun, avval uning ismni so'rash kerak. Yoki foydalanuvchi istagan ma'lumotni topish uchun avval undan biror kalit so'z kiritishini so'rash kerak va hokazo.

Biz avvalgi darsimizda input() yordamida fpydalanuvchidan qiymat qabul qilishni o'rgangan edik. Dastur davomida input() funksiysini chaqirganimizda dastur foydalanuvchi biror matn kiritib Enter tugmasini busgungacaha to'xtab turadi.

Foydalanuvchi kiritgan qiymatni biror o'zgaruvchiga yuklash va undan dastur davomida foydalanish mumkin:


```python
ism=input("Ismingizni kiriting :")
print(f"Salom , {ism.title()}")
```

    Salom , Jurabek Sevinchov
    

input() funksiyasining ishidagi matn ingliz tilida prompt, savol deyiladi. Aslida biz savolni ham o'zgaruvchiga yuklab shaxsiy so'rovnoalar ham yaratishimiz mumkin.


```python
ism=input("ismingiz nima? :")
savol=f"Salom, {ism.title()} . Yoshingiz nechida ? :"
yosh=input(savol)
```

Yuqorida birinchi input() bilan foydalanuvchining ismini so'radik va yangi savl matnini yasab oldik.

#### Sonlar va input()

input() funksiyasi har qanday kiritilgan qiymatni matn sifatida qabul qilib oladi. Agar foydalanuvchidan son talab qilinsa, foydalanuvchi kiritgan qiymatni butun (integer) yoki (float) son ko'rinishiga o'tkazib olish kerak.

Buning uchun int() yoki float() funksiyalaridan foydalanamiz.

#### 


```python
ism=input("Ismingiz nima ? ")
savol=f"Salom, {ism.title()}. Yoshingiz nechida ? "
yosh=input(savol)
yosh=int(yosh)
height=input("Bo'yingiz necha metr")
height=float(height)

```

Foydalanuvchidan qiymat so'raganingizda input()ichidagi savolni aniq va tushunarli qilib yozing. Masalan: input("Tug'ilgan yilingizni kiriting: ")

#### ehilr TSIKLI BILAN TANISHAMIZ

Biz avvvalroq for tsikli bilan tanishgan edik. for tsikli ma'lum bir ro'yxatni olib, ro'yxat ichidagi qiymatlar tugagunga qadar biror kodni takrorlar edi. while ham takrorlash operatori bo'lib, for dan farqli ravishda toki ma'lum bir shart to'g'ri (True) bo'lsa, kodni takrorlayveradi.

while so'zi ingiz tilidan "toki" yoki "-gacha" deb tarjima qilinadi.

Keling sodda misol ko'ramiz ingliz tilidan "toki" yoki "-gacha" deb tarjima qilinadi.

Kleing sodda misol ko'ramiz, while yordamida 5 gacha sanaymiz:


```python
son=1
while son<=5:
    print(son, end=" ")
    son+=1
```

    1 2 3 4 5 

Yuqoridagi kodni tahlil qilamiz:


* avval son degan o'zgaruvchi yaratdik va unga 1 qiymatini berdik. 

* 2-qatorda esa toki son 5 dan kichik yoki teng ekan 3-4-qatorlarni bajar dedik. 

* 3-qatorda son ni konsolga chiqardik

* 4-qatorda son ga 1 qo'shdik. 

* 4-qatordan so'ng kod yana 2-qatorga qaytadi va son<=5 shartini tekshiradi, agar shart bajarilsa 3-4 qator qayta-qayta bajarilaveradi. 

* 5-qadamdan so'ng son=5 bo'lganda while tsikli to'xtaydi.

Pythonda += operatori bor. Bu operator o'ng tarafdagi qiymatni chap tarafdagi qiymatga qo'shadi. Misol uchun, yuqorida son = son + 1 o'rniga son += 1 deb yozishimiz mumkin.

#### while va input()

Shu paytgacha yozgan dasturlarimiz faqatgina bir marta bajarilayotgan edi. while tsikli yordamida dasturni to'xtatish imkoniyatini foydalanuvchiga berishimiz mumkin.


```python
print("Kiritilgan sonning kvadratini qaytaruvchi dastur.")
savol = "Istalgan son kiriting "
savol += "(dasturni to'xtatish uchun 'exit' deb yozing): "
qiymat = ''
while qiymat != 'exit':
    qiymat = input(savol)
    if qiymat != 'exit':
        print(float(qiymat)**2)
```

    Kiritilgan sonning kvadratini qaytaruvchi dastur.
    9.0
    25.0
    4.0
    196.0
    

Yuoqridagi dasturimiz toki foydalanuvchi exit deb yozguniga qadar takrorlanaveradi.

#### Ishora (flag)

Yuqoridagi dasturda dasturni to'xtatish uchun yagona shartni tekshirdik (qiymat!='exit'), katta dasturlarda bir emas bir nechta shartlarni tekshirish, va ulardan biri bajarilgan taqdirda dasturni to'xtatish talab qilinishi mumkin. 

Bunday holatlarda biror o'zgaruvchidan ishora (flag) sifatida foydalanishimiz mumkin. Agar dastur bajarilishi davomida dasturni to'xtatish shartlaridan biri bajarilganda ishora o'zgaruvchining qiymatini o'zgartiramiz va dastur o'z-o'zidan to'xtaydi. 


```python
print("Kiritilgan sonning kvadratini qaytaruvchi dastur.")
savol = "Istalgan son kiriting "
savol += "(dasturni to'xtatish uchun 'exit' deb yozing): "
ishora = True
while ishora:
    qiymat = input(savol)
    if qiymat == 'exit':
        ishora = False
    else:
        print(float(qiymat)**2)
```

    Kiritilgan sonning kvadratini qaytaruvchi dastur.
    

#### BREAK OPERATORI

Break operatori yordamida ma'lum bir shartni tekshirish va while tsikli bajarilishini to'xtatib qo'yish mumkin.


```python
print("Kiritilgan sonning kvadratini qaytaruvchi dastur.")
savol = "Istalgan son kiriting "
savol += "(dasturni to'xtatish uchun 'exit' deb yozing): "

while True: # abadiy tsikl
    qiymat = input(savol)
    if qiymat == 'exit':
        break # tsiklni to'xtatish
    else:
        print(float(qiymat)**2)
```

Break for tsiklini to'xtatish uchun ham ishlatiladi.


```python
sonlar = list(range(1,11))
for son in sonlar: 
    if son == 5: # son 5 ga teng bo'lsa kod to'xtaydi
        break
    print(f"{son} ning kvadrati {son**2} ga teng")
```

    1 ning kvadrati 1 ga teng
    2 ning kvadrati 4 ga teng
    3 ning kvadrati 9 ga teng
    4 ning kvadrati 16 ga teng
    

while tsikli ichida bir nechta break operatori ham bo'lishi mumkin.

#### CONTINUE OPERATORI

Continue operatori esa aksincha, ma'lum bir shart bajarilganda qadam tashlab o'tish uchun mo'ljallangan.


```python
sonlar = list(range(1,11))
for son in sonlar:
    if son == 5: # son 5 ga teng bo'lsa tiskl boshiga qaytadi
        continue
    print(f"{son} ning kvadrati {son**2} ga teng")
```

    1 ning kvadrati 1 ga teng
    2 ning kvadrati 4 ga teng
    3 ning kvadrati 9 ga teng
    4 ning kvadrati 16 ga teng
    6 ning kvadrati 36 ga teng
    7 ning kvadrati 49 ga teng
    8 ning kvadrati 64 ga teng
    9 ning kvadrati 81 ga teng
    10 ning kvadrati 100 ga teng
    


```python
son = 0
while son<10:
    son += 1
    if son%2!=0:
        continue
    else:
        print(son)
```

    2
    4
    6
    8
    10
    

while tsikli ichida bir nechta continue operatori ham bo'lishi mumkin.

#### ABADIY TSIKL TUZOG'I

Tsikllar bilan ishlashda abadiy tsikl yaratib qo'yishdan ehtiyot bo'lishimiz kerak. Abadiy tsiklga turli mantiqiy xatolar sabab bo'lishi mumkin: noto'g'ri shart, o'zgarmas qiymat, kodlar ketma-ketligida xatolik va hokazo. 

Kelin ba'zi misollarni ko'ramiz:


```python
# infinite loop
son = 0
while son<10:
    if son%2!=0:
        continue
    else:
        print(son)
```

Yuqoridagi kod abadiy davom etadi, sababi biz son ning qiymatini o'zgartirishni esdan chiqardik.


```python
son = 0
while son<10:    
    if son%2!=0:
        continue
    else:
        print(son)
    son += 1
```

Bu kod ham abadiy davom etadi, lekin nima uchun?


```python
son = 1
while son>0: 
    son += 1
    if son%2!=0:
        continue
    else:
        print(son)
```

Yuqoridagi kodda esa xato shart tufayli (son>0) kod abadiy aylanadi.

Dastur bajarilishini to'xtatish uchun konsolda Ctrl+C tugmasini bosing

#### Topshiriqlar

1. Oddiy while sikli
Topshiriq: while siklidan foydalangan holda 1 dan 5 gacha bo'lgan sonlarni ekranga chiqaruvchi dastur tuzing.

2. Shart va o'zgaruvchini yangilash
Topshiriq: 10 dan 1 gacha bo'lgan sonlarni kamayish tartibida while sikli yordamida ekranga chiqaring.

3. Juft sonlarni chiqarish
Topshiriq: while sikli yordamida 1 dan 20 gacha bo'lgan faqat juft sonlarni ekranga chop eting.

4. Sonlar yig'indisini hisoblash (sum)
Topshiriq: 1 dan 10 gacha bo'lgan sonlarning yig'indisini while sikli yordamida hisoblang va natijani chiqaring.

5. break operatori yordamida to'xtatish
Topshiriq: 1 dan 100 gacha sonlarni sanaydigan while siklini yozing, lekin son 5 ga teng bo'lganida break operatori yordamida siklni majburiy to'xtating.

6. continue operatoridan foydalanish
Topshiriq: 1 dan 10 gacha bo'lgan sonlarni chiqaruvchi sikl tuzing, faqat 5 sonini tashlab o'tib ketish (continue yordamida) uchun shart yozing.

7. Cheksiz sikl va uni to'xtatish (Infinite Loop)
Topshiriq: while True cheksiz siklini tuzing va foydalanuvchi "exit" deb yozganda break orqali sikldan chiqib ketadigan mexanizm yarating.

8. Parol kiritish tekshiruvi
Topshiriq: To'g'ri parol ("python123") kiritilmaguncha foydalanuvchidan doimiy ravishda parol so'rab turadigan while siklini tuzing.

9. Sonni topish o'yini (Alohida urinishlar)
Topshiriq: Dastur ichida yashiringan bitta sonni foydalanuvchi topmaguncha while sikli yordamida har safar uning kiritgan soni katta yoki kichikligini aytib turing.

10. while-else konstruksiyasi
Topshiriq: while sikli tugagandan so'ng else bloki ishga tushib, "Sikl muvaffaqiyatli yakunlandi" degan yozuvni chiqaradigan kichik dastur tuzing.
