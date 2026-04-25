# FUNKSIYA

Pythpnda funksiyalar bilan tanishamiz

#### FUNKSIYA NIMA?

Funksiya ma'lum bir vazifani bajarishga mo'ljallangan kodlar yig'indisi. Biz shu paytgacha bir nechta tayyor funksiyalardan foydalanib keldik. Misol uchun print() funksiyasi konsolga matn chiqarish uchun, range() funksiyasi esa ma'lum oraliqdagi sonlarni yaratish uchun ishlatiladi.  

Aslida har qanday funksiyaning ortida ham bir necha qatordan iborat kod bo'ladi, lekin biz funksiyaga murojat qilganda uning nomini yozamiz xolos. Funksiya ortidagi kod esa biz uchun yashirin bo'lib qolaveradi. Funksiyalarning qulayligi ham shunda. Dastur davomida ma'lum bir kodlarni qayta-qayta yozmaslik uchun biz ularni jamlab, bitta funksiya ichiga joylashimiz va dastur davomida bu kodlarga funksiya nomi orqali murojat qilishimiz mumkin. 

Funksiyalar turlicha bo'ladi, ba'zi funksiyalar sizdan qiymat qabul qilib, konsolga biror ma'umot chiqaradi, ba'zilari esa sizdan qabul qilgan qiymat ustida turli amallar bajarib yangi qiymat qaytaradi. Foydalanuvchidan mutlaqo qiymat qabul qilmaydigan funksiyalar ham mavjud. 

Ushbu mavzuda siz qanday qilib Pythonda yangi funksiya yaratish, unga murojat qilish, tekshirish va to'g'rilashni o'rganasiz. Shuningdek darsimiz yakunida dasturimizni bir nechta faullarga ajratishni va funksiylarani alohida, module deb ataluvchi fayllarga joylashni ham o'rganamiz.

#### FUNKSIYA YARATAMIZ

Keling oddiy, salom_ber deb nomlangan funksiya yaratamiz. Bu funksiya murojat qilganimizda konsolga "Assalom alaykum!" degan xabarni chiqarsin.


```python
def salom_ber():
    """Salom beruvchi funksiya"""
    print("Assalomu alekum!")

salom_ber()
```

    Assalomu alekum!
    

Kodni qatroma-qator tahlil qilaylik:

Avvalo def operatori yordamida Pythonga funksiya yaratayotganimizni bildirdik. def dan so'ng esa funksiyamizga nom berdik va qavslarni ochib, yopdik. Bizning funksiyamiz foydalanuvchidan hech qanday qiymat qabul qilmaydi, shuning uchun ham qavs ichi bo'sh. Keyingi misollarda foydalanuvchidan qiymat qabul qiluvchi funksiyalarni ham ko'ramiz.

def qatoridan keyin o'ngga surib yozilgan har qanday kod funksiyaning badani hisoblanadi. 2-qatorda biz uchta ketma-ket qo'shtirnoq ichida funksiya haqida ma'lumot berdik. Python mana shu ma'lumotni o'qib, dasturchi funksiya haqida bilmoqchi bo'lganda aynan shu matnni ko'rsatadi. 

Oxirgi qatorimizda esa "Assalomu alaykum!" matnini konsolga chiqarishni buyurdik. Bizning sodda funksiyamizning asosiy vazifasi ham shu.

Mana funksiya tayyor. Endi bu funksiyadan foydalanish uchun uni chaqiramiz. Buning uchun funksiya nomini yozamiz va qavslarni ochib, yopamiz (esingizda bo'lsa bizning funksiyamiz qiymat qabul qilmaydi, shuning uchun qavslar ichi bo'sh).


```python
salom_ber()
```

    Assalomu alekum!
    

Funksiyaga nom berishda fe'l, ya'ni harakatni bildiruvchi so'zlar yoki jumlalardan foydalaning. Bu bilan siz o'zgaruvchi va funksiya o'rtasini farqlashingiz oson bo'ladi. Misol uchun, yuqorida biz funksiyamizni salom emas salom_ber deb nomladik.

#### FUNKSIYAGA QIYMAT UZATISH

Avvalgi sodda funksiyamiz foydalanivchidan hech qanday qiymat olmaydi va barchaga birday "Assalomu alaykum!" deb javob qiladi. Keling funksiyaga o'zgartirish kiritamiz, funksiya foydalanuvchi ismini qabul qilib, unga ismi bilan murojat qilsin. Buning uchun funksiya nomidan keyin, qavs ichida foydalanuvchi berishi kerak bo'lgan qiymatni ko'rsatamiz.


```python
def salom_ber(ism):
    """Foydlanuvchi ismini qabul qilib,
     unga salom beruvchi funksiya"""
    print(f"Assalommu alekum , hurmatli {ism.title()}")

salom_ber("jurabek")
```

    Assalommu alekum , hurmatli Jurabek
    

Mana endi fuknsiyamiz foydalanuvchidan ism degan qiymatni ham kutadi.


```python
salom_ber('jurabek')
```

    Assalommu alekum , hurmatli Jurabek
    

Agar funksiyaga murojat qilishda, unga qiymat bermasak xatolik vujudga keladi:


```python
salom_ber()
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[13], line 1
    ----> 1 salom_ber()
    

    TypeError: salom_ber() missing 1 required positional argument: 'ism'


#### DOCSTRING

Avval aytganimizdek, funksiya yaratganda, funksiya qanday ishlashi haqida qisqacha ma'lumot berib ketish o'zimiz uchun ham, kelajakda bizni funksiyamizni ishlatadigan boshqa dasturchilar uchun ham juda foydali bo'ladi. Quyidagi funksiyaning 2-qatorda biz funksiya haqida ma'lumot berdik. Bu qator **docstring** deyiladi. Murakkab funksiyalar uchun docstringni bir necha qatorga bo'lib yozishingiz mumkin


```python
def salom_ber(ism):
    """Fodyalanuvchi ismini qabul qilib, 
        unga salom beruvchi funksiya"""
    print(f"Assalomu alaykum, hurmatli {ism.title()}!")
```

Xo'sh, bu ma'lumot qachon va qayerda ko'rsatiladi? Dastur yozish jarayonida funksiya nomini yozishingiz bilan, docstring ko'rsatiladi:

Docstringni konsolga chiqarish uchun print(funksiya_nomi.__doc__) deb ham yozishimiz mumkin:


```python
print(salom_ber.__doc__)
```

    Fodyalanuvchi ismini qabul qilib, 
    unga salom beruvchi funksiya
    

#### FUNKSIYAGA BIR NECHA BOR MUROJAAT QILISH

Funksiya yaratishning asl maqsadlaridan biri, biz unga qayta-qayta, yangi qiymatlar bilan murojat qilishimiz mumkin. 


```python
salom_ber('hasan')
salom_ber('olim')
```

    Assalomu alaykum, hurmatli Hasan!
    Assalomu alaykum, hurmatli Olim!
    

#### ARGUMENT VA PARAMETR

Funksiya yaratishda, qavs ichida berilgan, funksiya to'g'ri ishlashi uchun uzatiladigan qiymat parameter deb ataladi. Yuqoridagi misolda ism bu salom_ber funksiyasining parametri. 

Foydalanuvchi funksiyaga murojat qilishda funksiyaga uzatgan qiymat esa argument deb ataladi. salom_ber('hasan') kodida 'hasan' bu argument. 

Ba'zi manbalarda yoki darslarda argument va parametr so'zlari almashtirib ishlatilishi ham kuzatiladi.

#### FUNKSIYAGA BIR NECHTA ARGUMENT UZATISH

Shunday funksiyalar bor, bir emas bir nechta parameter talab qilishi mumkin, foydalanuvchi esa o'z navbatida bir nechta argumentlar taqdim qilishi kerak. Funksiyaga argument uzatishning bir necha usuli bor, keling ular bilan birma bir tanishamiz.

#### T'G'RI TARTIBDA UZATISH

Bu usulda, funksiya parametrlari qaysi tartibda yozilgan bo'lsa, argumentlar ham aynan shu ketma-ketlikda uzatilishi kerak. Keling bitta misol ko'ramiz. Quyidagi funksiya foydalanuvchining ismi va familiyasini parametr sifatida qabul qilib, ularni jamlab xabar chiqaradi.


```python
def toliq_ism(ism, familiya):
    """Foydalanuvchi ism familiyasini jamlab chiqruvchi funksiya"""
    print(f"Foydalanuvchi ismi : {ism.title()}\n"
          f"Foydalanuvchi familiyasi : {familiya.title()}")


```

Yuqoridagi funksiya to'g'ri natija chiqarishi uchun argumentlarni ism va familiya ketma-ketligida kiritishimiz lozim.


```python
toliq_ism('olim', 'hakimov')
```

    Foydalanuvchi ismi : Olim
    Foydalanuvchi familiyasi : Hakimov
    

Agar argumentlarni noto'g'ri ketma-ketlikda bersak, natija ham biz kutganday chiqmaydi:


```python
toliq_ism('hakimov','olim')
```

    Foydalanuvchi ismi : Hakimov
    Foydalanuvchi familiyasi : Olim
    

Ko'p xolatlarda esa, argumentlarni noto'g'ri tartibda uzatish xatolikka ham olib kelishi mumkin.


```python
def yosh_hisobla(ism, t_yil):
    """Foydalanuvchi yoshini hisoblaydigan dastur!
    bunda (ism, tug'ilgan yil) kabi malumot bering"""
    print(f"{ism.title()} {2026-t_yil} yoshda!")


```


```python
yosh_hisobla('olim', 1997)
```

    Olim 29 yoshda!
    


```python
yosh_hisobla(1997, 'olim')
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    Cell In[22], line 1
    ----> 1 yosh_hisobla(1997, 'olim')
    

    Cell In[20], line 4, in yosh_hisobla(ism, t_yil)
          1 def yosh_hisobla(ism, t_yil):
          2     """Foydalanuvchi yoshini hisoblaydigan dastur!
          3     bunda (ism, tug'ilgan yil) kabi malumot bering"""
    ----> 4     print(f"{ism.title()} {2026-t_yil} yoshda!")
    

    AttributeError: 'int' object has no attribute 'title'


#### KALIT SO'Z BILAN UZATISH

Yuqoridagi kabi holatlarning oldini olish uchun argumentlarni parametr nomi bilan qo'shib uzatishimiz mumkin. Buning uchun funksiyaga o'zgartirish kiritish talab qilinmaydi.


```python
yosh_hisobla(t_yil=1990, ism="jurabek")
```

    Jurabek 36 yoshda!
    

Yuoqirdagi misolda funksiyani chaqirishda biz parametrlar ketma-ketligiga rioya qilmagan bo'lsakda, argumentlarni parametr_nomi=qiymat ko'rinishida yozganimiz sababli funksiya to'g'ri ishladi. 

Huddi shu kabi yuqoridagi toliq_ism funksiyasiga murojat qilishimiz mumkin:


```python
toliq_ism(familiya='hakimov',ism='olim')
```

    Foydalanuvchi ismi : Olim
    Foydalanuvchi familiyasi : Hakimov
    

Kalit so'z usulidan foydalanganda parametr nomi to'g'ri yozilganiga ahamiyat bering.

#### STANDART QIYMAT

Funksiya yaratishda, istalgan parametr uchun standart qiymat ko'rsatib ketishimiz mumkin. Agar foydalanuvchi shu parametr uchun qiymat (argument) kiritmasa, funksiya bajarilishi jarayonida standart qiymat ishlatiladi. Standart qiymatni funksiya yaratish vaqtidaparametr = qiymat ko'rinishida beriladi.


```python
def yosh_hisobla(t_yil, joriy_yil=2026):
    """Foydalanuvchi tug'ilgan yilidan uning yoshini hisoblaydi!!!"""
    print(f"Siz {joriy_yil-t_yil} yoshdasiz!!!")

```

Yuqoridagi misolda biz joriy_yil parametriga 2026 standart qiymatini berib ketdik.

Funksiya yaratishda, standart qiymatga ega parametrlar doim oxirida yozilishi kerak. Aks holda xatolik yuzaga keladi.

Keling avval funksiyani ikkala argument bilan chaqiramiz:


```python
yosh_hisobla(1995,2026)
```

    Siz 31 yoshdasiz!!!
    

Endi esa faqat bitta argument (tugilgan_yil) bilan chaqiramiz:


```python
yosh_hisobla(1993)
```

    Siz 33 yoshdasiz!!!
    

Bu safar foydalanuvchi joriy_yil ni kiritmagani sababli, standart qiymat, 2026 ishlatildi. 

#### FUNKSIYAGA MUROJAAT QILISHDA XATOLIKLAR

Funksiyalarga murojat qilishda turli xatoliklarga yo'l qo'shimiz tabiiy. Bunday holatlarda Python qaytargan xatoni sinchiklab o'qib, xato qayerdaligini topishimiz va uni to'g'rilashimiz zarur. Quyida men avvalroq yaratgan funksiyalarimizni xato usullar bilan chaqiraman. Xato nimada ekanini topa olasizmi?


```python
# Foydalanuvchi ismi va yoshini so'rab, uning tug'ilgan yilini hisoblaydigan funksiya yozing.

def yoshni_hisobla(ism, t_yil, joriy_yil=2026):
    """Foydalanuvchi ismi va tug'ilgan yilini kiritasiz
    bu esa uning yoshini hisoblab beradi"""
    print(f"{ism.title()} siz {joriy_yil-t_yil} yoshdasiz!!!")

ism=input("Iltimos ismingizni kiriting :")
yosh=int(input("Tug'ilgan yilingizni kiriting :"))
yoshni_hisobla(ism, yosh)
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    Cell In[11], line 9
          6     print(f"{ism.title()} siz {joriy_yil-t_yil} yoshdasiz!!!")
          8 ism=input("Iltimos ismingizni kiriting :")
    ----> 9 yosh=int(input("Tug'ilgan yilingizni kiriting :"))
         10 yoshni_hisobla(ism, yosh)
    

    ValueError: invalid literal for int() with base 10: ''



```python
def yosh_hisobla(tugilgan_yil, joriy_yil):
    """Foydalanuvchi tug'ilgan yilidan uning yoshini hisoblaydi"""
    print(f"Siz {joriy_yil-tugilgan_yil} yoshdasiz")

yosh_hisobla(1993)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[29], line 5
          2     """Foydalanuvchi tug'ilgan yilidan uning yoshini hisoblaydi"""
          3     print(f"Siz {joriy_yil-tugilgan_yil} yoshdasiz")
    ----> 5 yosh_hisobla(1993)
    

    TypeError: yosh_hisobla() missing 1 required positional argument: 'joriy_yil'



```python
def salom_ber():
    """Salom beruvchi funksiya"""
    print("Assalomu alaykum!")

salom_ber('hasan')
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[30], line 5
          2     """Salom beruvchi funksiya"""
          3     print("Assalomu alaykum!")
    ----> 5 salom_ber('hasan')
    

    TypeError: salom_ber() takes 0 positional arguments but 1 was given



```python
def toliq_ism(ism, familiya):
    """Foydalanuvchi ism va familiyasini jamlab chiqaruvchi funksiya"""
    print(f"Foydalanuvchi ismi: {ism.title()}\n"
          f"Foydalanuvchi familiyasi: {familiya.title()}")
 
 toliq_ism('olim hakimov')
```


      File <string>:6
        toliq_ism('olim hakimov')
                                 ^
    IndentationError: unindent does not match any outer indentation level
    



```python
# Foydalanuvchidan son olib, uning kvadrati va kubini konsolga chiqaruvchi funksiya yozing.

def kvadrat_va_kub(son):
    """Sonning kvadrati va kubini hisoblab beradigan funksiya!"""
    print(f"{son} ning kvadrati : {son**2} ga, kubi esa : {son**3} ga teng!")

kvadrat_va_kub(int(input("Istalgan sonni kiriting: ")))
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    Cell In[28], line 7
          4     """Sonning kvadrati va kubini hisoblab beradigan funksiya!"""
          5     print(f"{son} ning kvadrati : {son**2} ga, kubi esa : {son**3} ga teng!")
    ----> 7 kvadrat_va_kub(int(input("Istalgan sonni kiriting: ")))
    

    ValueError: invalid literal for int() with base 10: ''


# TOPSHIRIQLAR

Asosiy funksiyalar va returnSalomlashuv:   
* Foydalanuvchi ismini qabul qilib, "Salom, [ism]!" matnini qaytaruvchi funksiya yozing.  
* Kvadrat: Sonni qabul qilib, uning kvadratini hisoblab beruvchi funksiya tuzing.  
* To'liq ism: Ism va familiyani qabul qilib, ularni birlashtirib qaytaruvchi funksiya yozing.  
* Katta son: Ikkita son qabul qilib, ularning kattasini qaytaruvchi funksiya tuzing.  
* Juft yoki toq: Son juft bo'lsa True, toq bo'lsa False qaytaruvchi funksiya yozing.  
* Ro'yxatlar bilan ishlash  
* Yig'indi: Sonlardan iborat ro'yxatni qabul qilib, uning elementlari yig'indisini hisoblaydigan funksiya tuzing.  
* Eng uzun so'z: Matnlardan iborat ro'yxat ichidan eng uzun so'zni topib beruvchi funksiya yozing.  
* Element sanash:   
* Ro'yxat va biror qiymatni qabul qilib, shu qiymat ro'yxatda necha marta takrorlanganini aniqlang.  
* Teskari ro'yxat: Berilgan ro'yxatni teskari tartibda qaytaruvchi funksiya yozing.
* Filtr:    
* Sonlar ro'yxatidan faqat musbatlarini ajratib oluvchi funksiya tuzing.   
* Matematik va mantiqiy amallar  
* Daraja: x va n sonlarini qabul qilib, $x^n$ ni hisoblovchi funksiya yozing.  
* O'rta arifmetik: Uchta sonning o'rtacha qiymatini hisoblovchi funksiya tuzing.
* Unli harflar:   
* Matn qabul qilib, undagi unli harflar sonini sanovchi funksiya yozing.  
* Parol tekshiruvi: Berilgan matn uzunligi 8 tadan kam bo'lmasa True, aks holda False qaytaruvchi funksiya tuzing.  
* Faktorial: Berilgan sonning faktorialini hisoblovchi funksiya yozing.   
* Moslashuvchan argumentlar (*args, **kwargs)Cheksiz ko'paytma: Istalgancha son qabul qilib (*args), ularning ko'paytmasini qaytaruvchi funksiya yozing.  
* Talaba ma'lumoti: Ism, familiya va qo'shimcha ma'lumotlarni (**kwargs) qabul qilib, ularni chiroyli ko'rinishda chiqaruvchi funksiya tuzing.  
* Loyiha lug'ati:   
* Kalit so'zlar va qiymatlar ko'rinishida ma'lumot qabul qilib, ulardan lug'at (dictionary) yasovchi funksiya yozing.  
* Murakkabroq mantiqIchma-ich funksiya:   
* Doiraning yuzini hisoblaydigan funksiya yozing, uning ichida radiusning kvadratini hisoblash uchun alohida kichik funksiyadan foydalaning.  
* Lug'atni yangilash:   
* Lug'at va yangi kalit-qiymat juftligini qabul qilib, agar kalit bo'lmasa yangisini qo'shadigan, bo'lsa qiymatini yangilaydigan funksiya tuzing.
