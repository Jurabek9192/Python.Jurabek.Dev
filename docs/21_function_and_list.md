# FUNKSIYA VA RO'YXXAT

Funksiyaga ro'yxat uzatishni o'rganamiz

#### FUNKSIYAGA RO'YXAT UZATISH

Biz avvalgi darslarimizda funksiyaga parametr sifatida yagona qiymat berayotgan edik. Aslida, bu bilan cheklanmasdan, funksiyaga ro'yxat (list) ham berishimiz mumkin. Bunda, funksiya ro'yxat qiymatlariga to'g'ridan-to'g'ri murojat qila oladi.

Keling talabalarni baholaydigan funksiya yozamiz. Funksiyamiz talabalar ro'yxatini qabul qilib oladi, ro'yxatdan har bir talabani sug'urib olib (.pop()), bahosini kiritishni so'raydi. Talaba ismi va bahosini lug'atga joylab, yakuniy lug'atni foydalanuvchiga qaytaradi.


```python
def bahola(ismlar):
    baholar={}
    while ismlar:
        ism=ismlar.pop()
        baho=input(f"Talaba {ism.title()}ning bahosini kiriting: ")
        baholar[ism]=baho
    return baholar

talabalar=['ali', 'hasan', 'farhod', 'davron', 'farrux']
baholar=bahola(talabalar[:])
print(baholar)
print(talabalar)
```

    {'farrux': '5', 'davron': '4', 'farhod': '4', 'hasan': '3', 'ali': '5'}
    ['ali', 'hasan', 'farhod', 'davron', 'farrux']
    


```python
# Matnlardan iborat ro'yxat qabul qilib, ro'yxatdagi 
# har bir matnning birinchi harfini katta harfga
# o'zgatiruvchi funksiya yozing.

def katta(matn):
    """Bu listni title qiladi"""
    # for i in range(len(matn)):
    #     matn[i]=matn[i].title()
    # return matn
    matn=[ism.title() for ism in matn]
    return matn


ismlar=['ali', 'aziz', 'dilshod', 'laziz', 'davron']
print(katta(ismlar))
```

    ['Ali', 'Aziz', 'Dilshod', 'Laziz', 'Davron']
    

#### RO'YXATGA O'ZGARTIRISH KIRITSH

Funksiyaga ro'yxat uzatganimizda, funksiya ro'yxat elementlariga to'g'ridan-to'g'ri murojat qila oladi. Ro'yxatga funksiya ichida kiritilgan o'zgartirishlar asl ro'yxatga ham ta'sir qiladi. Avvalgi misolimizga qaytaylik:


```python
talabalar = ['ali', 'vali', 'hasan', 'husan']
baholar = bahola(talabalar)
print(talabalar)
```

    []
    

Yuqoridagi funksiya unga uzatilgan ro'yxat ichidagi talabalarning ismini .pop() yordamida sug'urib olgani uchun bizning asl ro'yxatimiz ham bo'shab qoldi. E'tibor bering, funksiya tashqarisidagi va ichidagi ro'yxatlar ikki hil nomlangan bo'lsada (talabalar va ismlar), ikkalasi ham xotiradagi bitta ro'yxatga bog'langani sabab ulardan biriga o'zgartirish kiritilishi bilan, ikkinchisi ham o'zgaradi. 

![IMAGE.png](21_function_and_list_files/IMAGE.png)


```python

# Yuoqirdagi funksiyani asl ro'yxatni o'zgartirmaydigan 
# va yangi ro'yxat qaytaradigan qilib o'zgartiring

def katta_qil(ismlar):
    """Asl listni saqlab qoladi"""
    yangi_ismlar=[]
    for i in range(len(ismlar)):
        yangi_ismlar.append(ismlar[i].title())
    
    return yangi_ismlar

def katta_qil_saqla(ismlar):
    return [ism.title() for ism in ismlar]

print(katta_qil(ismlar))
print(katta_qil_saqla(ismlar))
print(ismlar)
```

    ['Ali', 'Aziz', 'Dilshod', 'Laziz', 'Davron']
    ['Ali', 'Aziz', 'Dilshod', 'Laziz', 'Davron']
    ['ali', 'aziz', 'dilshod', 'laziz', 'davron']
    

#### ASL RO'YXATGA O'ZGARTIRISH KIRITISHNING OLDINI OLISH

Agar funksiya asl ro'yxatga o'zgartirish kiritishini istamasangiz, funksiyaga ro'yxatning o'zini emas, uning nusxasini uzatish mumkin. Buning uchun funksiya parametrini royxat_nomi[:] ko'rinishida yozish kifoya. Bunda [:] operatori ro'yxatdan nusxa olishni bildiradi:


```python
talabalar = ['ali', 'vali', 'hasan', 'husan']
baholar = bahola(talabalar[:])
print(talabalar)
```

    ['ali', 'vali', 'hasan', 'husan']
    

* Ro'yxatni o'zgartiruvchi funksiyalar
* Kattalashtirish: Matnlardan iborat ro'yxat qabul qilib, har bir elementning birinchi harfini bosh harfga aylantiruvchi (asl ro'yxatni o'zgartiruvchi) funksiya yozing.

* Nollarni o'chirish:   
* Sonlar ro'yxatidan barcha nolga teng elementlarni o'chirib tashlaydigan funksiya tuzing.

* Baholash: Talabalar ismlari ro'yxatini va ularga standart "5" bahosini biriktiruvchi (lug'at ko'rinishida emas, balki ism yoniga yozib qo'yuvchi) funksiya yozing.

* QQS qo'shish: Narxlar ro'yxatidagi har bir songa 12% QQS qo'shib qo'yuvchi funksiya tuzing.

* Indeksli o'zgartirish: Ro'yxatdagi faqat juft indeksda turgan elementlarni "X" belgisiga almashtiruvchi funksiya yozing.

* Ro'yxatdan nusxa olib ishlash
Xavfsiz tahrir: Ro'yxatni qabul qilib, uning asl nusxasiga tegmagan holda, faqat teskari tartibdagi nusxasini qaytaruvchi funksiya yozing.

* Saralangan nusxa: Sonlar ro'yxatini qabul qilib, uni o'sish tartibida saralangan yangi ro'yxat sifatida qaytaring (asl ro'yxat tartibi buzilmasin).

* Ismlar filtri: Ismlar ro'yxatidan faqat 5 harfdan ko'p bo'lganlarini tanlab, yangi ro'yxat qaytaruvchi funksiya tuzing.

* Dublikatlarsiz: Ro'yxat ichidagi takrorlangan elementlarni olib tashlab, faqat noyob elementlardan iborat yangi ro'yxat qaytaring.

* Kvadratlar ro'yxati: Berilgan sonlar ro'yxatidagi har bir sonning kvadratidan iborat yangi ro'yxat shakllantiring.

* Murakkab mantiq va Ro'yxatlar
* Element almashtirish: Funksiya ro'yxat, eski qiymat va yangi qiymat qabul qilsin. Ro'yxatdagi barcha eski qiymatlarni yangisiga almashtirsin.

* Ikki ro'yxat yig'indisi: Ikkita bir xil uzunlikdagi sonli ro'yxatlarni qabul qilib, ularning mos elementlari yig'indisidan iborat uchinchi ro'yxatni qaytaring.

* Juflash: Ismlar ro'yxatini qabul qilib, ularni juft-juft qilib (tuple ko'rinishida) yangi ro'yxatga joylang.

* Eng kichikni o'chirish: Ro'yxatdagi eng kichik sonni topib, uni ro'yxatdan sug'urib oluvchi (pop yoki remove) funksiya yozing.

* Ma'lumotlarni tozalash: Ro'yxat ichidagi bo'sh joylarni (empty strings) olib tashlaydigan funksiya tuzing.

* Amaliy (Project-based) topshiriqlar
* Omborxona: Mavjud mahsulotlar ro'yxati va sotilgan mahsulotlar ro'yxatini qabul qilib, ombordan sotilganlarini ayirib tashlaydigan funksiya yozing.

* Navbat boshqaruvi: Mijozlar ro'yxatidan birinchi kelgan mijozni chiqarib yuborib, unga "Xizmat ko'rsatildi" xabarini beruvchi funksiya tuzing.

* Tasodifiy tanlov: Ro'yxat ichidan tasodifiy 3 ta elementni tanlab oluvchi va ularni asl ro'yxatdan o'chiruvchi funksiya yozing.

* Matnni bo'lish: Gaplardan iborat ro'yxatni qabul qilib, har bir gapni so'zlarga ajratib, umumiy so'zlar ro'yxatini qaytaring.

* Reyting tizimi: Ballar ro'yxatini qabul qilib, 80 dan yuqori ballarni "A'lo", 60-80 orasini "Yaxshi" deb o'zgartiruvchi funksiya yozing.
