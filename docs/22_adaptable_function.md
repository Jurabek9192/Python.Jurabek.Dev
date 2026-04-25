# MOSLASHUVCHAN FUNKSIYA (*ARGS, **KWARGS)

*args va **kwargs bilan tanishamiz

#### MOSLASHUVCHAN FUNKSIYA

Agar funksiyangiz bir nechta argument qabul qilishi kerak bo'lsa-yu, lekin siz argumentlar sonini aniq bilmasangiz, Pythonda istalgancha qiymat qabul qiluvchi funksiya yaratish imkoniyati bor.

# args USULI

Agar funksiya qabul qiladigan parametrlar soni noaniq bo'lsa, va parametrlar yagona qiymatlar ko'rinishida uzatilsa, funksiya yaratishda argumentdan avval yulduzcha qo'yiladi (*arguments). 

Quyidagi misolni ko'raylik. summa() nomli funksiyamiz istalgancha sonlarni qabul qilib oladi, va ularning yi'gindisi hisoblaydi:


```python
def summa(*sonlar):
    """Kiritilgan sonlarning yig'indisini hisoblaydigan funksiya."""
    yigindi=0
    for son in sonlar:
        yigindi+=son

    return yigindi

```

Bu funksiyani istalgancha parametr bilan chaqirish mumkin:


```python
print(summa(1,2))
```

    3
    


```python
print(summa(1,2,3,4,5))
```

    15
    

*args usulida, bacha uzatilgan parametrlar (bir dona bo'lsa ham) funksiya ichida o'zgarmas ro'yxatga (tuple) joylanadi. Bundan kelib chiqib, yuqoridagi funksiyamizni yanada soddalashtirib yozishimiz mumkin:


```python
def summa(*sonlar):
    """Kiritilgan sonlarning yig'indisini hisoblaydigan funksiya."""
    return sum(sonlar)

print(summa(1, 2, 3, 4, 5, 76, 8, 7))
```

    106
    

Agar funksiya bir nechta argument qabul qilsa, *args argument doim oxirida yoziladi:


```python
def summa(x,y,*sonlar):
    """Kiritilgan sonlar yig'indisini hisoblaydigan funksiya"""
    return x+y+sum(sonlar)
```

Yuqoridagi funksiyamiz kamida 2 ta parametr qabul qiladi (x va y) va birinchi ikki argumentlar majburiy argumentlardir.


```python
print(summa(2))
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[5], line 1
    ----> 1 print(summa(2))
    

    TypeError: summa() missing 1 required positional argument: 'y'


#### **kwargs USULI

Agar funksiyaga kalit so'z - qiymat ko'rinishidagi argumentlarni uzatish talab qilinsa, va bunday parametrlar soni noma'lum bo'lsa, argument oldidan ikkita yulduzcha qo'yiladi (**kwargs).

**kwargs — keyword arguments (kalit so'zli argumentlar)


```python
def avto_info(kompaniya, model, **malumotlar):
    """Avto ma'lumotlarini lug'at shaklida qaytaradi."""
    malumotlar['kompaniya']=kompaniya
    malumotlar['model']=model
    return malumotlar
```

Yuqoridagi funksiyamiz kompaniya va model degan ikki qiymatni qabul qiladi, undan keyin esa funksiyaga istalgancha parametr uzatish mumkin.  Bunday funksiyaga parametrlar kalitso'z=qiymat ko'rinishida uzatiladi.

Funksiya ichida avval foydalanuvchi kiritgan qo'shimcha qiymatlardan iborat malumotlar deb nomlangan lug'at shakllantiriladi. Undan keyin esa majburiy parametrlarni lug'atga qo'shamiz. 


```python
avto1 = avto_info("GM", "malibu", rang='qora', yil=2018)
avto2 = avto_info("Kia", "K5", rang='qizil', narh=35000)
```


```python
print(avto2)
```

    {'rang': 'qizil', 'narh': 35000, 'kompaniya': 'Kia', 'model': 'K5'}
    

# TOPSHIRIQLAR

* *args (Ixtiyoriy miqdordagi argumentlar)
* Ko'paytuvchi: Istalgancha son qabul qilib, ularning ko'paytmasini qaytaruvchi funksiya yozing. Agar hech qanday son uzatilmasa, 0 qaytarsin.

* Eng uzun matn: Bir nechta matnlarni (so'zlarni) qabul qilib, ular ichidan eng uzunini topib beruvchi funksiya tuzing.

* O'rta qiymat: Noma'lum miqdordagi sonlarni qabul qilib, ularning o'rta arifmetik qiymatini hisoblovchi funksiya yozing.

* Ismlar ro'yxati: Birinchi argument sifatida guruh nomini, keyingi argumentlar (*args) sifatida esa talabalar ismlarini qabul qilib, ularni chiroyli formatda (masalan: "Guruh: Python, Talabalar: Ali, Vali") chiqaruvchi funksiya tuzing.

* Kvadratlar yig'indisi: Uzatilgan barcha sonlarning kvadratlarini hisoblab, ularning umumiy yig'indisini qaytaruvchi funksiya yozing.

* **kwargs (Ixtiyoriy miqdordagi kalit-qiymat juftligi)
* Avto ma'lumot: Mashinaning brendi va modelini majburiy argument sifatida, qolgan ma'lumotlarini (rangi, yili, narxi, korobka va h.k.) esa **kwargs yordamida qabul qilib, lug'at qaytaruvchi funksiya yozing.

* Profil yaratuvchi: Foydalanuvchi haqidagi ma'lumotlarni (ism, familiya - majburiy; yosh, shahar, email - ixtiyoriy) qabul qilib, ularni jadval ko'rinishida konsolga chiqaruvchi funksiya tuzing.

* Qidiruv filtri: Mahsulotlar ombori uchun funksiya yozing. U majburiy argument sifatida maxsulot turini, ixtiyoriy argumentlar sifatida esa filtrlarni (masalan: rang='qizil', narx=5000) qabul qilsin va ularni matn sifatida qaytarsin.

* Lug'atni birlashtirish: Ikkita majburiy lug'at va qo'shimcha **kwargs orqali kelgan ma'lumotlarni bitta katta lug'atga jamlab qaytaruvchi funksiya tuzing.

* Sozlamalar: Dastur sozlamalarini qabul qiluvchi funksiya yozing. Agar **kwargs ichida theme kaliti bo'lsa, uni chiqarsin, bo'lmasa "Standart mavzu" deb xabar bersin.
