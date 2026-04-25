# LUG'AT BILAN TANISHUV

Yangi ma'lumot turi-Dictionary bilan tanishamiz.

Ushbu darsda yangi ma'lumot turi, Lug'at (Dictionary) bilan tanishamiz. Dars davomida lug'at yaratish, unga ma'lumot qo'shish, lug'atning ichida ro'yxat yoki aksincha ro'yxatning ichida lug'at saqlash kabi mavsular bilan tanishamiz.

Lug'at ma'lumotlarni bizga tushunarliroq ko'rinishda saqlash imkonini beradi.
Misol uchun biz biror avtomobilga oid lug'at yaratishimiz va lug'atda shu avtoga tegishli barcha ma'lumotlarni saqlashimiz mukin (nomi, rangi, yili, motori, narxi va hokazo)

#### LUG'AT (DICTIONARY) NIMA?

Keling, nima uchun bu ma'lumot turi lug'at (dictionary) deyilishini tushunish uchun, oddiy lug'atga qaraymiz. Odatda, luga'atdagi ma'lumotlar ikki qismdan iborat bo'ladi : kalit so'z va izoh (yoki tarjima).

Xuddi oddiy lug'atlardagi kabi Python lug'atidagi ma'lumotlar ham ikki qismdan iborat bo'ladi: so'z va qiymat (ingliz tilida key-value pair yoki so'z-qiymat juftligi deyiladi).

Dasturlashda ko'p ishlatiladigan atamalarni ingliz tilida yodlab qolish juda muhim! Bu sizga kelajakda yangi ma'lumotlar izlashda, xatolar usitda ishlashda va umuman ish faoliyatingizda ko'p asqotadi. Shuing uchun variable, integer, float, string, list, tuple, dictionary, function, loop, va boshqa so'zlarni yaxshilab o'zlashtirib oling.

Keling, sodda lug'at yaratamiz:


```python
car_0={'model' : 'ferrari', 'rang' : 'qizil'}
```

Yuqorida car_0 fegan lug'at yaratdik. Lug'atda 2 ta ma'lumot bor: mashinaning modeli (ferrari) va rangi (qizil). Bu yerda 'model' va 'rang' kalit so'zlar, 'ferrari' va 'qizil' esa mos keluvchi kalit so'zlarning qiymatlari. Kalit so'z va qiymat orasi ikki nuqta ( : ) bilan lug'atdagi har bir juftlik esa vergul ( , ) bilan ajratiladi. 

#### LUG'AT BILAN ISHLASH

Demak, Pythonda lug'at *kalit-qiymat* juftliklarining yig'indisi ekan. Lug'atdagi biror qiymatni ko'rish uchun unga kalit *so'z* orqali murojaat qilinadi.


```python
uy={'turi': 'hovli', 'qavat':'bir'}
print(uy['turi'])
```

    hovli
    


```python
print(uy['qavat'])
```

    bir
    

Lug'atdagi qiymatlar son (int, float), matn(string), ro'yxat(list, tuple) va hatto boshqa lug'at ham bo'lishi mumkin.


```python
talaba_0={'ism':'alimov sardor', 'yosh':20, 't_yil':2000}
print(f"{talaba_0['ism'].title()},\
    {talaba_0['t_yil']}-yilda tug'ilgan,\
    {talaba_0['yosh']} yoshda")
```

    Alimov Sardor,    2000-yilda tug'ilgan,    20 yoshda
    

#### YANGI JUFTLIK QO'SHISH

Lug'atga yangi kalit so'z va qiymatlar qo'ahiahimiz ham mumkin. Keling, yuqoridagi talaba_0 nomli lug'atga yana 2 ta yangi, kurs va fakultet nomli, kalit va qiymatlar qo'shamiz.


```python
talaba_0['kurs']=4
talaba_0['fakultet']='informatika'
```

Lug'atni konsolga chiqarib ko'ramiz.


```python
print(talaba_0)
```

    {'ism': 'alimov sardor', 'yosh': 20, 't_yil': 2000, 'kurs': 4, 'fakultet': 'informatika'}
    

#### BO'SH LUG'AT 

Ba'zida dastur davomida lug'atga yangi ma'lumotlar kiritib borish talab qilinishi mumkin. Bunday holatda bo'sh lug'at quyidagicha yaratiladi.


```python
talaba_1={}
```

Dastur davomida esa lug'at qiymatlar kiritib borilishi mumkin:



```python
talaba_1['ism']='Davronov Sardor'
talaba_1['kurs']=3
talaba_1['yosh']=20
print(talaba_1)
print(f"{talaba_1['ism'].title()} {talaba_1['kurs']}-kurs")
```

    {'ism': 'Davronov Sardor', 'kurs': 3, 'yosh': 20}
    Davronov Sardor 3-kurs
    

Lug'atga kalit so'zlar qanday ketma-ketlikda kiritilsa, shu ketma-ketlik saqlanib qoladi.

#### Qiymatni o'zgartirish

Lug'atda biron juftlik kerak emas bo'lsa uni del operatori yordamida olib tshlash mumkin.


```python
talaba_0 = {'ism':'murod olimov','yosh':20,'t_yil':2000}
print(talaba_0)
del talaba_0['yosh'] # yosh degan kalit so'z (va qiymatni) o'chiramiz
print(talaba_0)
```

    {'ism': 'murod olimov', 'yosh': 20, 't_yil': 2000}
    {'ism': 'murod olimov', 't_yil': 2000}
    

#### LUG'ATNI QATORLARGA BO'LIB YOZISH

Uzun lug'atlarni bir necha qatorga bo'lib yozishmiz ham mumkin. Keling quyidagi misolni ko'ramiz, siz siz do'stlaringizdan ular qanaqa mashina markasini yoqtirishini so'rab ularni bitta lug'atga joylamoqchisiz :



```python
mashinalar={
    'sardor': 'bmw',
    'davron': 'benz',
    'kamron': 'toyota',
    'ali' : 'nissan'
}
```

Demak, lug'atni qatorga bo'lib yozish uchun katta qavs ochamiz, yangi qatordan joy tashlab, birinchi kalit so'z va qiymatni kiritamiz, qator oxirida vergul qo'yib, yangi qatordan keyingi juftlikni yozamiz va hokazo. Oxirgi jufltikdan so'ng vergul qo'ymasdan qatorni tashlab, katta qavsni yopamiz.

Lug'atlarning ishlatilish doirasi juda keng va sizning yondoshuvingizga bog'liq xolos. Yuqoridagi lug'atga ham e'tibor qilsangiz, biz bir narsa (shaxs, avto) haqida ko'p ma'lumotlarni emas,  ko'pchilik haqida bir hil ma'lumotlarni saqladik. 

#### get() METODI

Biz shu vaqtgacha lug'atdagi qiymatlarni ko'rish uchun to'g'ridan-to'g'ri kalit so'z bilan murojaat qilayotgan edik. Bu usulning kamchiligi shundaki, agar lug'atda siz so'ragan kalit topilmasa, dastur **KeyError** xatoligi bilan to'xtab qoladi.


```python
mashina=mashinalar['ali']
print(f"Alining sevimli mashinasi : {mashina.title()}")
```

    Alining sevimli mashinasi : Nissan
    


```python
mashina=mashinalar['abror']
print(f"Abrorning sevimli mashinasi : {mashina.title()}")
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    Cell In[5], line 1
    ----> 1 mashina=mashinalar['abror']
          2 print(f"Abrorning sevimli mashinasi : {mashina.title()}")
    

    KeyError: 'abror'


Lug'atda 'abror' kalit so'zi bo'lmagani uchun, yuworidagi kod **KeyError** degan xatoni qaytardi. KeyError ham Run Time Error qatoriga kiradi. 

Biz kelajakda Pythondagi xatolarni tutib olishni ham o'rgaamiz. Hozircha esa *get()* metodi yordamida lug'atga murojaat qilish va mavjud bo'lmagan kalitning o'rniga biror xabar qaytarishni ko'raylik.


```python
mashina=mashinalar.get('hasan', 'Bunday ism mavjud emas.')
```

Yuqorida, lug'at nomidan so'ng get() metodini yozdik va argumentlar sifatida kalit so'z ('hasan') va kalit mavjud bo'lmagan chiqadigan xabarni yozdik ("Bunday ism mavjud emas')


```python
print(mashina)
```

    Bunday ism mavjud emas.
    

Agar .get() metodida ikkinchi argumentni tashlab ketsangiz, va kalit mavjud bo'lmasa .get() metodi None degan qiymatni qaytaradi. None - qiymat mavjud emas degan ma'noni beradi.


```python
mashina=mashinalar.get('hasan')
print(mashina)
```

    None
    
