### Floats-O'nlik sonlar
Pythonda o'nlik sonlar *floating point numbers* yoki qisqa qilib floats deyiladi. *"Floating point numbers"* atamasi o'zbek tiliga *"suzuvchi nuqtali sonlar"* deb tarjima qilish mumkin.Ingliz tilida o'nlik sonlarni yozish uchun (,) vergul emas (.) ishlatiladi, va bu nuqta sonning katta kichikligiga qarab joyi o'zgargani uchun *"floating" (suzuvchi)* deyiladi


```python
pi=3.14159          # o'nlik son(float)
radius=10           # butun son (integer)
diametr=2*radius
print("Aylana uzunligi ", pi*diametr, " ga teng.")
```

    Aylana uzunligi  62.8318  ga teng.
    

### Butun sondan o'nlik songa
Avval aytganimizdek ikki butun sonni bo'lishda ham o'nlik son hosil bo'ladi natija butun bo'lsa ham.


```python
a=-20
b= 40
print(b/a)
```

    -2.0
    

va bundan tashqari butun son va o'nlik sonlar orasidagi har qanday amal ham o'nlik son qaytaradi.


```python
a=4
b=5.0
# Quyida barcha arifmetik amallarni bajaramiz
print(f"{a} + {b} = {a+b}")
print(f"{a} - {b} = {a-b}")
print(f"{a} * {b} = {a*b}")
print(f"{a} / {b} = {a/b}")
```

    4 + 5.0 = 9.0
    4 - 5.0 = -1.0
    4 * 5.0 = 20.0
    4 / 5.0 = 0.8
    

**Uzun sonlarni kiritish**
Uzun sonlarni kiritishda qulaylik uchun, raqamlarni pastki chiziq(\_) yordamida guruhlash mumkin. *Python-son tarkibidagi pastki chiziqlarni (\_)* **inobatga olmaydi** yodda saqlang bunda bu sonlar uzun son sifatida qabul qilinadi.


```python
aholi_soni=7_893_000_000 # shunda qulayroq ko'rinadi
print(f"Yer yuzidagi aholi soni : {aholi_soni} ga teng.")
```

    Yer yuzidagi aholi soni : 7893000000 ga teng.
    

#### Konstanta
Aksar dasturlash tillarida konstant qiymatlar tushunchasi bor. Konstantlar o'zgarmas bo'ladi (misol uchun
π
π ning qiymati konstant, o'zgarmas qiymat). Pythonda konstant tushunchasi yo'q, shuning uchun dasturchilar bunday o'zgaruvchilarning nomini katta harflar bilan yozadilar (ogohlantirish sifatida). Bu albatta qat'iy qonun emas, lekin kelajakda o'zgaruvchilar orasida konstant qiymatlarni ajratish uchun yaxshi usul.


```python
PI=3.14159
radius=21.2
```

#### Bir necha o'zgaruvchiga qiymat berish
Bir necha o'zgaruvchiga qiymat beridh uchun o'zgaruvchilar va ularga mos qiymatlar vergul( , ) bilan ajratiladi.


```python
x, y, z=10, -7.94, -30

print(f"x ning turi {type(x)}")
print(f"y ning turi {type(y)}")
print(f"z ning turi {type(z)}")
```

    x ning turi <class 'int'>
    y ning turi <class 'float'>
    z ning turi <class 'int'>
    

#### O'zgaruvchining turini almashtirish (typecasting)
Keling biz siz bilan bir misol ko'ramiz unda ism va yosh degan o'zgaruvchilarga ma'lumotlar yuklaymiz va ularni printda turlicha usulda chiqarib ko'ramiz


```python
ism="Javohir"
yosh=36
xabar=ism+" " + yosh + " yoshda."
print(xabar)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[10], line 3
          1 ism="Javohir"
          2 yosh=36
    ----> 3 xabar=ism+" " + yosh + " yoshda."
          4 print(xabar)
    

    TypeError: can only concatenate str (not "int") to str


Demak biz kutilgan natijani ololmadik ya'ni xatolik chiqdi. Agar xatoni ingliz tilidan tarjima qilsak, matn(str) va son(int) ni jamlab bo'lmaydi degan ma'no chiqadi.

Demak Pythonda matn(string) va son(int, float) turidagi o'zgaruvchilarni jamlab bo'lmaydi. Xo'sh bunda biz nima qila olamiz axir natija bizga kerak va buning yo'li bormi ? **ALBATTA**.

Pythonda bir turdagi o'zgaruvchini boshqa turga o'tkazish mumkin va bu *typecasting* deyiladi. Buni amalga oshirish uchun Pythonda maxsus funksiyalar bor va ular quyidagilar.  
str() --int yoki float turidagi sonlarni matnga o'zgartiradi.  
int() --matn yoki float ko'rinishdagi qiymatlarni butun songa o'tkazadi. Bunda matn va float butun son ko'rinishida bo'lsa o'zgarishsiz agar butun son bo'lmasa unda butun son sifatida yaxlitlab olinadi.  
float() -- mant yoki int butun sonni o'nli kasr son turiga almashtiradi.

Demak tepadagi odimiz to'g'ri ishlashi uchun kodga o'zagrtish kiritamiz.


```python
ism="Javohir"
yosh=36
xabar=ism+" " + str(yosh) + " yoshda."
print(xabar)
```

    Javohir 36 yoshda.
    

**Diqqat** qiling bizning yosh degan o'zgaruvchi o'z holicha qoldi yani uyosh hali ham int turida shunchaki print() ning ichidagina tur o'zgardi holos.

#### O'zgaruvchi turini tekshirish

Kodlarda o'zgaruvchilar ko'payishi tabiiy albatta ayniqsa kodlar ko'paygani sari unda o'zgaruvchilar ham albatta ko'payadi va ba'zan variable ning turini ham untib qo'yish mumkin bunda biz uni osongina teshirib olamiz.
Buning uchun type() ni ishlatamiz.


```python
ism="Gavhar"
yosh=23
print(f"Ismning turi : {type(ism)}")
print(f"Yoshning turi : {type(yosh)}")
```

    Ismning turi : <class 'str'>
    Yoshning turi : <class 'int'>
    

#### Input() va sonlar
Endi keling **input()** bilan yaqindan tanishamiz. Endi input() orqali foydalanuvchidan turli ma'lumotlar olamiz.


```python
# Foydalanuvchining tug'ilgan yilini so'raymiz
t_yil=int(input("Tug'ilgan yilingizni kiriting:"))
# Endi esa uning yoshini hisoblaymiz
yosh=2026-t_yil
print(f"Siz {yosh} yoshdasiz.")
```

    Siz 32 yoshdasiz.
    

Yuqorida biz t_yil da input() ni int() ning ichida yozdik aslida bunday qilmasdan alohida yozsak ham bo'ladi quyidagi kodga diqqat qiling.


```python
t_yil=input("Tug'ilgan yilingizni kiriting:")
t_yil=int(t_yil)
yosh=2026-t_yil
print(f"Siz {yosh} yoshdasiz.")
```

    Siz 32 yoshdasiz.
    

🟢 Oson daraja (Matematik hisob-kitoblar)  
Ism va familiya: Foydalanuvchidan ismi va familiyasini alohida so'rab, ularni bitta qatorda "Assalomu alaykum, [Familiya] [Ism]!" ko'rinishida chiqaruvchi dastur tuzing.  
Yillar va kunlar: Foydalanuvchi yoshini kiritsada, dastur uning taxminan necha kun yashaganini hisoblab chiqarsin (1 yil = 365 kun).  
Kvadrat perimetri: Kvadratning tomoni $a$ berilganda, uning perimetrini ($P = 4a$) hisoblovchi dastur yozing.  
Sekundlarni daqiqaga o'tkazish: Foydalanuvchi sekundlar miqdorini kiritadi (masalan, 120). Dastur buni necha daqiqa ekanligini ko'rsatishi kerak.  
🟡 O'rta daraja (Mantiqiy bog'liqlik)  
Uchburchakning yuzi: To'g'ri burchakli uchburchakning ikkita katetini ($a$ va $b$) so'rang va uning yuzini hisoblang ($S = \frac{1}{2}ab$).  
Tezlik va vaqt: Masofa ($S$) va vaqt ($t$) berilganda, harakat tezligini ($V = \frac{S}{t}$) aniqlaydigan dastur tuzing.  
Yillik daromad: Foydalanuvchidan oylik maoshini so'rang. Dastur uning bir yillik umumiy daromadini va 12% daromad solig'i ushlab qolingandan keyingi sof foydasini ko'rsatsin.  
Sonlarni almashtirish: Ikkita o'zgaruvchi kiriting ($a$ va $b$). Dastur ularning qiymatlarini o'zaro almashtirib qo'ysin (masalan, $a=5, b=10$ bo'lsa, natijada $a=10, b=5$ bo'lib qolsin).  
🔴 Murakkabroq (Qo'shimcha shartlar bilan)  
Vaqt oralig'i: Foydalanuvchi hozirgi soat va minutni kiritadi. Dastur kun yakunlanishiga (ya'ni 24:00 gacha) necha soat va necha minut qolganini hisoblashi kerak.  
Do'kon xaridi: Foydalanuvchi sotib olgan mahsulotining narxi va miqdorini (kg yoki dona) kiritadi. Shuningdek, do'kon beradigan chegirma foizini ham kiritadi. Dastur jami to'lanishi kerak bo'lgan yakuniy summani hisoblab bersin.Kubning xususiyatlari: Kubning tomoni $a$ berilgan. Uning hajmini ($V = a^3$) va to'la sirti yuzini ($S = 6a^2$) hisoblang.
