# XATOLAR BILAN ISHLASH

Har qanday dasturchi kod yozishda xato qiladi. Ko'p yozgan odam esa ko'p xato qiladi va bu tabiiy. Ba'zi xatolarimiz Python tomonidan dastur bajarilishdan avvalroq aniqlanadi. Ba'zilari esa dastur bajarilish jarayonida aniqlab, dasturimiz to'xtab qoladi. Keling, bugun  dasturlashni yangi boshlaganlar eng ko'p yo'l qo'yadigan xatolar bilan tanishamiz.

#### SyntaxError-SINTEKS XATOLAR

**syntax error** bu eng ko'p uchraydigan xato bo'lib, odatda dasturlash tili qoiddalariga amal qilmaslik natijasida kelib chiqadi. Aksar dasturlash muhitlari sintaks xatolikni dastur bajarilishidan oldinroq aniqlab, dasturchiga ishora beradi.

Sintaks xatolik bor dasturni Python bajarmaydi.


```python
print "Hello World"
```


      Cell In[1], line 1
        print "Hello World"
        ^
    SyntaxError: Missing parentheses in call to 'print'. Did you mean print(...)?
    


Odatda dasturlash muhiti xatoning turi bilan birga (SyntaxError), xato haqida qo'shimcha ma'lumot ham beradi (Missing parentheses in call to 'print'. Did you mean print("Hello World")?). Agar ingliz tilini tushunmasangiz, [GoogleTranslater](https://translate.google.com/?ui=tob&sl=en&tl=ru&op=translate) sahifasi yordamida matnni rus yoki o'zbek tiliga tarjima qilib olishingiz mumkin.

Agar rus tilini bilsangiz, xato matnini rus tilga tarjima qiling. O'zbek tilidagi tarjimalar hali biroz tushunarsiz.

#### EOL va EOF xatolik

EOL (End of Line-qator yakuni) xatoligi sintaks xatolikning bor turi bo'lib, odatda qator oxirida qo'shtirnoq (birtirnoq)ni yopish esdan chiqqanda yuzaga keladi.


```python
print('hello world
```


      Cell In[5], line 1
        print('hello world
              ^
    SyntaxError: unterminated string literal (detected at line 1)
    


Natija: SyntaxError: EOL while scanning string literal

EOF (End of Function-funksiya yakuni) xatoligi esa funksiya oxirida qavsni yopish esdan chiqqanda yuzaga keladi.


```python
print('hello world'
```


      Cell In[6], line 1
        print('hello world'
                           ^
    _IncompleteInputError: incomplete input
    


Natija: SyntaxError: unexpected EOF while parsing

#### IndentationError-JOY TASHLASHDA XATOLIK

Python tilida qator boshidan yoki joy tashlab yozish muhim ahamiyatga ega.
Qator boshidan asossiz joy qolsdirish IndentationError ga olib keladi.

Quyidagi kodga etibor bering, qator boshida 1 dona bo'sh joy qolgani uchunoq Python qatolikni aqniqlab, qizil bilan belgilab qo'ydi.


```python
print("Hello world.")
    print("Hello world.")
```


      Cell In[8], line 2
        print("Hello world.")
        ^
    IndentationError: unexpected indent
    


Ba'zi joylarda esa aksincha joy tashlab yozish talab etiladi. Masalan, for tsiklida yoki if-elif-else shartlarining ichida va hokazo.


```python
print("O'ngacha sanaymiz.")
for n in range(10):
print(n+1)
```


      Cell In[10], line 3
        print(n+1)
        ^
    IndentationError: expected an indented block after 'for' statement on line 2
    



```python
son=50
if son>=0:
    print("Musbat son")
else:
print("Manfiy son")
```


      Cell In[11], line 5
        print("Manfiy son")
        ^
    IndentationError: expected an indented block after 'else' statement on line 4
    


#### QANCHA JOY TASHLAYMIZ?

Yuqoridagi misollarda IndentationError oldini olish uchun joy tashlash talab qilindi. Xo'sh qancha joy tashlaymiz.

Aslida, hech bo'lmaganda 1 harflik bo'sh joy qoldirish ham bizni IndentationError dan xalos qiladi. LEKIN, biz dastur davomida bir hil joy tashlashga odatlanishimiz kerak.

Qoida sifatida kamida 4 ta harflik bo'sh joy yoki 1 ta TAB (klaviaturadagi tab tugmasi) joy tashlashni odat qilishimiz kerak. Va eng muhimi ikkalasini aralashtirib yubormasligimiz lozim. Ya'ni agar siz joy tashlash uchun Space(Probel) ishlatdangiz, oxirigacha shunday qiling, agar Tab ishlatdangiz oxirigacha Tab ishlating. Ikkalasini aralashtirmagn!

#### RUN TIME ERROR-DASTURNI BAJARISHDA XATOLIK

Run time error-dasturni bajarish jarayonida kelib chiqadi va dasturning ishlashini to'xtatadi. Syntax xatolikdan farqli ravishda Python bunday xatolarni dasturni bajarishdan avval aniqlay olmaydi. Run time error ning bir necha turi bor. Keling, ulardan ba'zilari bilan tanishamiz.

#### TypeError

Biror amalni (funksiya, metod) noto'g'ri ma'lumot turi ustida bajarish


```python
son=input("Istalgan sonni kiriting :")
print(f"{son} ning kvadrati {son**2} ga teng.")
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[12], line 2
          1 son=input("Istalgan sonni kiriting :")
    ----> 2 print(f"{son} ning kvadrati {son**2} ga teng.")
    

    TypeError: unsupported operand type(s) for ** or pow(): 'str' and 'int'


Yuqoridagi kodda biz foydalanuvchi kiritgan qiymatni matndan songa o'tkazib olishni unutdik, natijada sonning kvadratini hisoblashda Python xato berdi.

#### NameError

O'zgaruvchi, funksiya, obyekt nomini noto'g'ri yozish natijasida kelib chiquvchi xatolik.


```python
prit("Hello world")
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    Cell In[13], line 1
    ----> 1 prit("Hello world")
    

    NameError: name 'prit' is not defined



```python
mevalar=['olma', 'uzum', 'nok', 'anor', 'anjir']
for meva in mvalar:
    print(meva)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    Cell In[14], line 2
          1 mevalar=['olma', 'uzum', 'nok', 'anor', 'anjir']
    ----> 2 for meva in mvalar:
          3     print(meva)
    

    NameError: name 'mvalar' is not defined


#### ValueError

Funksiyaga noto'g'ri qiymatni yuborish natijasidagi xatolik


```python
son=int(input("istalgan sonni kiriting :"))
if son>=0:
    print("Musbat son.")
else :
    print("Manfiy son.")
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    Cell In[15], line 1
    ----> 1 son=int(input("istalgan sonni kiriting :"))
          2 if son>=0:
          3     print("Musbat son.")
    

    ValueError: invalid literal for int() with base 10: 'd'


Yuqoridagi dasturning 1-qatorida foydalanuvchidan istalgan son kiritishini so'rayapmiz va foydalanuvchi qiymatni int ya'ni butun songa o'tkazyapmiz. Kodning o'zida xato yo'q lekin dastur bajarish jarayonida foydalanuvchi butun son emas, o'nlik son kirigani yoki harf kiritib yuborgani uchun ValueError xatosi chiqdi. Sababi int() funksiya faqatgina butun sonlar ko'rinishidagi matn bilan ishlaydi.

Dastur xato bermasligi uchun yoki int() funksiyasini float() ga almashtirish kerak, yoki foydalanuvchidan butun son kiritishini talab qilishimiz kerak.

#### IdexError

Yangi dasturchilar yo'l qo'yadigan yana bir xato bu indeks xatolik. Ya'ni ro'yxat elementlariga murojaat qilishda indeksni noto'g'ri kiritish.


```python
mevalar=['olma', 'anor', 'uzum']
print(mevalar[3])
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    Cell In[16], line 2
          1 mevalar=['olma', 'anor', 'uzum']
    ----> 2 print(mevalar[3])
    

    IndexError: list index out of range


Bizda mevalar degan ro'yxat bor va ro'yxatda uchta meva bor. Biz 3-elementni konsolga chiqarmoqchimiz va print(mevalar[3]) deb yozdik va IndexError natijasini oldik. Sababi, dasturlashda indeks 0 boshlanadi va 3-elementga murojaat qilish uchun 2-indeksni tanlaymiz. Demak, to'g'ri kod:


```python
mevalar=['olma', 'uzum', 'anor']
print(mevalar[2])
```

    anor
    

#### ZeroDivisionError

Dastur jarayonida 0 ga bo'lish yuzaga kelgandagi xatolik


```python
x, y=50, 50
z=300/(x-y)
```


    ---------------------------------------------------------------------------

    ZeroDivisionError                         Traceback (most recent call last)

    Cell In[18], line 2
          1 x, y=50, 50
    ----> 2 z=300/(x-y)
    

    ZeroDivisionError: division by zero


#### MANTIQIY XATOLAR

Mantiqiy xatolar-dasturchi tomonidan yo'l qo'yiladigan va kutilgan natijani berishda to'sqinlik qiladigan xatolar. Bunday xatolar eng ko'p uchraydigan va aniqlash eng qiyin bo'lgan xatolar hispblanadi.
Aksar holatlarda Python mantiqiy xatolarni aniqlamaydi va dastur bajarilaverad (lekin kutilgan natija chiqmaydi).

Mantiqiy xatolar turli ko'rinishda bo'lishi mumkin, masalan sonlar bilan ishlashda:


```python
radius=5
pi=4.14
aylana_yuzasi=pi*radius**2
print(aylana_yuzasi)
```

    103.49999999999999
    

Yuqoridagi kod bajarildi va natija ham chiqdi. Lekin natija xato. Nima uchun? Sababi biz pi=4.14 deb xato qiymat yosib ketdik.

Yana bir misol ko'raylik:


```python
son=float(input("Istalgan sonni kiriting : "))
ildiz=son**1/2
print(f"{son} ning ildizi {ildiz} ga teng.")
```

    9.0 ning ildizi 4.5 ga teng.
    

Yuqoridagi natijaga e'tibor bersangiz, 9 sonining ildizi 4.5 deb chiqdi. Sababi 2-qatorda ildizni hisoblashda foydalanuvchi kiritgan son avval 1-darajaga oshirildi va undan keyin 2 ga bo'lindi. Kodni tuzatamiz: 


```python
son=float(input("Istalgan sonni kiriting : "))
ildiz=son**(1/2)
print(f"{son} ning ildizi {ildiz} ga teng.")
```

    9.0 ning ildizi 3.0 ga teng.
    

Noo'rin bo'sh joy qoldirish (yoki qoldirmaslik) ham mantiqiy xatoga olib kelishi mumkin:


```python
mevalar = ['olma','uzum','nok','anor','anjir']
for meva in mevalar:
    print(meva)
    print("Dastur tugadi")
```

    olma
    Dastur tugadi
    uzum
    Dastur tugadi
    nok
    Dastur tugadi
    anor
    Dastur tugadi
    anjir
    Dastur tugadi
    

Yuqoridagi "Dastur tugadi" matni bir marta, dastur tugagach chiqishi kerak edi.
Lekin o'ngga surilib qolgani uchun bir necha bor qaytarildi.

Bundan boshqa ham mantiqiy xatoliklar juda ko'p uchraydi.

Mantiqiy xatoliklar mutlaqo topilmasdan ham qolib ketishi  va dastur bozorga chiqqandan keyin aniqlasnishi tabiiy hol. Shuning uchun aksar dasturlar tez-tez yangilanib turadi.

Dastur jarayonida ham bundan boshqa xatoliklar ham ko'p uchraydi. Biz ulardan ba'zilari bilan tanishdik xolos.

# TOPSHIRIQLAR

Quyidagi xatolarni tuzating agar ular mavjud bo'lsa:


```python
pasword = "python2024"
if pasword == "python2024" or "admin123":
    print("Xush kelibsiz!")
# Bu kodda har qanday noto'g'ri parol ham o'tib ketadi. Nega?
```


```python
ball = 85
if ball > 70:
    print("Yaxshi")
elif ball > 80:
    print("A'lo")
# Nega 85 ball olgan talabaga "A'lo" chiqmayapti?
```


```python
a = 10
b = 20
c = 30
print(a < b < c) # Bu to'g'ri ishlaydi
print(a == 10 or 20) # Bu yerda nima chiqadi deb o'ylaysiz?
```


```python
print("Natija:", 5 + 5 * 2 / (3 - 3))
```


```python
ism = "Ali"
print(f"Salom, {Ism}")
```


```python
yosh = input("Yoshingizni kiring: ")
print("Siz 5 yildan keyin", yosh + 5, "yoshda bo'lasiz")
```


```python
son = 10
if son / 2 == 5:
    print("Bu butun son")
# Kod ishlaydi, lekin `10 / 2` har doim qanday turdagi son qaytaradi?
```


```python
print("Mening yoshim " + 25)
```


```python
x = "False"
if x:
    print("Bu rost!")
else:
    print("Bu yolg'on!")
# Nega "False" yozilgan bo'lsa ham "Bu rost!" chiqyapti?
```


```python
meva = "olma"
if not meva == "anor" or "shaftoli":
    print("Bu anor ham emas, shaftoli ham emas")
# Shaftoli deb yozsangiz ham kod "Bu anor ham emas..." deb chiqaraveradi. Nega?
```
