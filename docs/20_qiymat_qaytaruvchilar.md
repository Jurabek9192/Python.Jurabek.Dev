# QIYMAT QAYTARUVCHI FUNKSIYA

Funksiyadan qiymat qaytarishni o'rganamiz

Avvalgi darsimizda yaratgan barcha funksiyalarimiz konsolga ma'lumot chiqarayotgan edi. Aslida, aksar holatlarda bu g'ayritabiiy. Sababi, dasturchi sifatida biz konsolga chiqqan ma'lumotdan unumli foydalana olmaymiz. Konsoldagi qiymatni o'zgaruvchiga yuklab, undan kelajakda foydalanib ham bo'lmaydi. Mana shunday holatlarda, funksiyadan unumli foydalanish uchun undan biror qiymatni qaytarish maqsadga muvofiq bo'ladi.

#### FUNKSIYADAN ODDIY QIYMAT QAYTARISH

Keling ism va familiya degan parametrlarni olib, toliq_ism qaytaradigan sodda funksiya yasaymiz.


```python
# Funksiyadan oddiy qiymat qaytarish

def toliq_ism_yasa(ism, familiya):
    """To'liq ism qaytaruvchi funksiya."""
    toliq_ism=f"{ism.title()} {familiya.title()}"
    return toliq_ism
```

Yuqoridagi funksiyamizga ahamiyat bersangiz, uning badanida endi print() funksiyasi yo'q. Buning o'rniga, funksiyamiz return operatori yordamida toliq_ism degan o'zgaruvchining qiymatini qaytaradi.

Endi funksiyadan to'g'ri foydalanish uchun u qaytargan qiymatni biror o'zgaruvchiga yuklashimiz kerak:


```python
talaba1 = toliq_ism_yasa('olim','hakimov')
talaba2 = toliq_ism_yasa('hakim','olimov')
```

Yuqoridagi kodlarni bajarganimizda konsolga hech narsa chiqmaydi. talaba1 va talaba2 o'zgaruvchilarining qiymatini ko'rish uchun esa print() funksiyasidan foydalanamiz.


```python
print(f"Darsga kelmagan talabalar: {talaba1} va {talaba2}")
```

    Darsga kelmagan talabalar: Olim Hakimov va Hakim Olimov
    

Demak, qiymat qaytaradigan funksiyaning afzalligi shundaki, biz bu qiymatlardan keyin ham bemalol foydalanishimiz mumkin.

Funksiya ichidagi o'zgaruvchilar mahalliy yoki ichki o'zgaruvchilar deyiladi (local variables). Ichki o'zgaruvchilar faqatgina funksiya ichida mavjud bo'ladi, ularga tashqaridan murojat qilib bo'lmaydi. Shuning uchun ham funksiya o'zgaruvchi emas qiymat qaytaradi.

# IXTIYORIY ARGUMENTLAR

Avvalgi darsizmida funksiyalarga standart parametr berishni ko'rgan edik. Huddi shu usul bilan, ba'zi argumentlarni ixtiyoriy qilishimiz mumkin. Ya'ni funksiya ishlashi uchun bu agrumentarni kiritish majburiy emas, ixtiyoriy bo'ladi.

Keling avvalgi funksiyamizni o'zgartiramiz va unga yana bitta otasiningismi degan paramter qo'shamiz, lekin bu parametr ixtiyoriy bo'ladi. Buning uchun funksiya yaratishda otasining_ismi='' deb yozib ketamiz.


```python
def toliq_ism_yasa(ism, familiya, otasining_ismi=""):
    """Toliq ism qaytaruvchi funksiya"""
    if otasining_ismi:
        toliq_ism=f"{ism.title()} {otasining_ismi.title()} {familiya.title()}"
    else:
        toliq_ism=f"{ism.title()} {familiya.title()}"
    return toliq_ism
```

Yuqoridagi funksiyani tahlil qiladigan bo'lsak, 3-qatorda biz otasiningismi parametri bo'sh yoki yo'qligini tekshiramiz. Pythonda if dan so'ng bo'sh bo'lmagan matn (string) yozsak, bu shart True qaytaradi. Demak, bu ixtiyoriy parametr kiritilgani yoki yo'qligiga qarab, funksiyamiz turlicha qiymat qaytaradi.


```python
talaba1 = toliq_ism_yasa('olim','hakimov') #otasining_ismi kiritilmadi
talaba2 = toliq_ism_yasa('hakim','olimov','abrorovich')
print(f"Darsga kelmagan talabalar: {talaba1} va {talaba2}")
```

    Darsga kelmagan talabalar: Olim Hakimov va Hakim Abrorovich Olimov
    

#### FUNKSIYADAN LUG'AT QAYTARAMIZ

Funksiyadan sodda qiymat emas, ro'yxat, lu'gat va boshqa ma'lumot turlarini ham qaytarishimiz mumkin.  Quyidagi funksiya ham mashina haqidagi ma'lumotlarni jamlab, ularni lug'at ko'rinishida qaytaradi:


```python
def avto_info(kompaniya, model, rangi, korobka, yili, narxi=None):
    """Lug'at qaytaradigan funksiya."""
    avto={
        'kompaniya' : kompaniya,
        'model' : model,
        'rang' : rangi,
        'korobka' : korobka,
        'yil' : yili,
        'narxi' : narxi
    }
    return avto
```

E'tibor bering, narhi nomli parametrga None standart qiymatini berib ketdik. None Pythonda mavjud emas ma'nosini beradi, va if yordamida tekshirganda False mantiqiy qiymatini qaytardi. 

Quyidagi kodni tahlil qilishni sizga vazifa sifatida qoldiramiz:


```python
avto1 = avto_info('GM','Malibu','Qora','Avtomat',2018)
avto2 = avto_info('GM','Gentra','Oq','Mexanika',2016,15000)
avtolar = [avto1, avto2]
print('Onlayn bozordagi mavjud avtomashinalar:')
for avto in avtolar:
    if avto['narxi']:
        narh = avto['narxi']
    else:
        narh = "Noma'lum"
    print(f"{avto['rang']} {avto['model']}. Narhi: {narh}")
```

    Onlayn bozordagi mavjud avtomashinalar:
    Qora Malibu. Narhi: Noma'lum
    Oq Gentra. Narhi: 15000
    

#### FUNKSIYADAN RO'YXAT QAYTARAMIZ

Biz avvalroq range() funksiyasi bilan tanishgan edik. Bu funksiya 2 ta son qabul qilib, shu ikki son orali'g'idagi sonlarni qaytaradi. Keling biz oraliq() degan yangi funksiya yaratamiz. range() dan farqli ravishda, funksiyamiz 2 son oralig'idagi sonlarni ro'yxat ko'rinishida qaytarsin.


```python
def oraliq(min, max):
    """Min va max orasidagi sonlarni qaytaradi"""
    sonlar=[]
    while min<max:
        sonlar.append(min)
        min+=1
    return sonlar
```

Funksiyani tekshiramiz:


```python
print(oraliq(0,10))
print(oraliq(10,21))
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    [10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20]
    

Yuqoridagi funksiyaga uchinchi, qadam deb nomlangan ixtiyoriy parameterni qo'sha olasizmi?


```python
print(oraliq(0,21,2)) # 0 dan 21 gacha 2 qadam bilan
```

Quyida yechim berilgan 


```python
def oraliq_sonlar(min, max, qadam=1 ):
    """Min va max orasidagi donlarni qadamlarda qaytaradi."""
    sonlar=[]
    while min<max:
        sonlar.append(min)
        min+=qadam
    return sonlar

print(oraliq_sonlar(0, 10, 2))
print(oraliq_sonlar(0, 30, 2))
```

    [0, 2, 4, 6, 8]
    [0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28]
    

#### FUNKSIYALARNI TSIKLDA ISHLASH

Funksiyalarni takrorlash uchun tsikldan foydalanishimiz mumkin. Quyidagi misolda biz while yordamida avvalroq yaratgan avto_info funksiyamizni bir necha bor chaqiramiz va salondagi avtolar ro'yxatini shakllantiramiz. Bunda, ro'yxatning har bir elementi avto_info funksiyasidan qaytgan lug'at bo'ladi.


```python
print("Saytimizdagi avtolar ro'yxatini shakklantiramiz.")
avtolar=[]
while True:
    print("Quyidagi ma'lumotlarni kiriting", end="")
    kompaniya=input("Ishlab chiqaruvchi :")
    model=input("Modeli: ")
    rangi=input("Rangi :")
    korobka=input("Korobka :")
    yili=input("Yili :")
    narxi=input("Narxi :")

    # Foydalanuvchi kiritgan ma'lumotlardan avvto_info yordamida
    # lug'at shakllantirib, har bir lug'atni ro'yxatga qo'shamiz:
    avtolar.append(avto_info(kompaniya, model, rangi, korobka, yili, narxi))

    # Yana avto qo'shish qo'shmaslikni so'raymiz
    javob=input("Yana avto qo'shasizmi (y/n): ")
    if javob=='n':
        break 
```

    Saytimizdagi avtolar ro'yxatini shakklantiramiz.
    Quyidagi ma'lumotlarni kiritingQuyidagi ma'lumotlarni kiritingQuyidagi ma'lumotlarni kiritingQuyidagi ma'lumotlarni kiriting

# TOPSHIRIQLAR


* Foydanaluvchidan ismi, familiyasi, tug'ilgan yili, tug'ilgan joyi, email manzili va telefon raqamini qabul qilib, lug'at ko'rinishida qaytaruvchi funksiya yozing. Lug'atda foydalanuvchu yoshi ham bo'lsin. Ba'zi argumentlarni kiritishni ixtiyoriy qiling (masalan, tel.raqam, el.manzil)  

* Yuqoridagi funksiyani while yordamida bir necha bor chaqiring, va mijozlar degan ro'yxatni shakllantiring. Ro'yxatdagi mijozlar haqidagi ma'lumotni konsolga chiqaring.  

* Uchta son qabul qilib, ulardan eng kattasini qaytaruvchi funksiya yozing  

* Foydalanuvchidan aylaning radiusini qabul qilib olib, uning radiusini, diametrini, perimetri va yuzini lug'at ko'rinishida qaytaruvchi funksiya yozing  

* Berilgan oraliqdagi tub sonlar ro'yxatini qaytaruvchi funksiya yozing (tub sonlar —faqat birga va o'ziga qoldiqsiz bo'linuvchi, 1 dan katta musbat sonlar)  

* Foydalanuvchidan son qabul qilib, shu son miqdoricha [Fibonachchi](https://janobmusayev.medium.com/fibonachchi-sonlari-va-u-haqida-qiziqarli-faktlar-47000a80264d) ketma-ketligidagi sonlar ro'yxatni qaytaruvchi funksiya yozing.  Ta’rif: Har bir hadi o’zidan oldingi ikkita hadning yig’indisiga teng bo’lgan ketma-ketlik Fibonachchi ketma-ketligi deyiladi. Bunda boshlang’ish had ko’pincha 1 deb olinadi.  1, 1, 2, 3, 5, 8, 13, 21, 34, 55,...

* Sodda amallar (Return bilan tanishuv)  
* To'liq ism yasovchi: Ism va familiyani qabul qilib, ularni bitta matnga birlashtirib qaytaruvchi funksiya yozing.

* Kvadrat qaytaruvchi: Berilgan sonning kvadratini konsolga chiqarmasdan, natija sifatida qaytaruvchi funksiya tuzing.

* Katta son: Ikki son qabul qilib, ulardan kattasini qaytaruvchi funksiya yozing (agar teng bo'lsa, birini qaytarsin).

* Boolean tekshiruv: Sonni qabul qilib, u musbat bo'lsa True, manfiy bo'lsa False qaytaruvchi funksiya tuzing.

* Yuzani hisoblash: To'g'ri to'rtburchakning tomonlarini qabul qilib, uning yuzasini qaytaruvchi funksiya yozing.

* Lug'at va Ro'yxatlar bilan ishlash
Avto ma'lumot: Mashina markasi, modeli va yilini qabul qilib, ulardan lug'at (dictionary) yasab qaytaruvchi funksiya yozing.

* Shaxsiy ma'lumot: Ism, yosh va kasbni qabul qilib, lug'at qaytaruvchi funksiya tuzing (yosh ixtiyoriy argument bo'lsin).

* Oraliq topuvchi: Ikki son qabul qilib, shu sonlar oralig'idagi barcha butun sonlarni ro'yxat (list) ko'rinishida qaytaruvchi funksiya yozing.

* Maksimum topish: Ro'yxat qabul qilib, undagi eng katta sonni qaytaruvchi funksiya tuzing (ichki max() funksiyasiz).

* Filtrlash: Ismlar ro'yxatini qabul qilib, faqat "A" harfi bilan boshlanadiganlarini yangi ro'yxatga solib qaytaruvchi funksiya yozing.

* Murakkab mantiq va Sikllar
Lug'atli ro'yxat: Foydalanuvchidan bir nechta kitob nomlarini so'rab, ularni lug'atga yig'uvchi va umumiy ro'yxat qaytaruvchi funksiya tuzing.

* Faktorial: Berilgan sonning faktorialini hisoblab qaytaruvchi funksiya yozing.

* Tub sonlar: Ma'lum bir oraliqdagi barcha tub sonlarni ro'yxat qilib qaytaruvchi funksiya tuzing.

* So'z sanash: Matn qabul qilib, undagi har bir so'z necha marta qatnashganini lug'at ko'rinishida qaytaruvchi funksiya yozing.

* Unli harflar: Matndagi unli harflarni alohida ro'yxat qilib qaytaruvchi funksiya tuzing.

* Amaliy loyihalar uchun topshiriqlar
Valyuta konvertori: So'm miqdorini va kursni qabul qilib, natijani dollarda qaytaruvchi funksiya yozing.

* O'rtacha ball: Talabaning fanlardan olgan baholari ro'yxatini qabul qilib, o'rtacha ballni qaytaruvchi funksiya tuzing.

* Teskari matn: Berilgan matnni teskari tartibda (masalan: "salom" -> "molas") qaytaruvchi funksiya yozing.

* Min-Max lug'at: Ro'yxat qabul qilib, undagi eng kichik va eng katta sonni bitta lug'atda qaytaruvchi funksiya yozing (masalan: {'min': 1, 'max': 10}).

* Chipta narxi: Yoshni qabul qilib, chipta narxini qaytaruvchi funksiya: 7 yoshgacha - 5000, 7-18 yosh - 10000, kattalarga - 20000 so'm.
