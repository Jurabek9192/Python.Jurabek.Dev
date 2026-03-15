#### Ro'yxatlar bilan ishash
Ro'yxatlar ustida turli amallarni bajarishni o'rganamiz

#### Ro'yxatni tartilash
Aksar hollarda ro'yxat ichidagi elementlarni alifbo ketma-ketligida tartiblash talab qilinishi mumkin. Buning uchun list uchun maxsus **.sort()** metodidan foydalanamiz.


```python
viloyatlar=['toshkent', 'andijon', 'far\'ona', 'namangan', 'samarqand',
'xorazm', 'qashqadaryo', 'surxondaryo']
viloyatlar.sort()
mashinalar=['nexia', 'tracker', 'malibu', 'tico', 'matiz', 'damas']
print(mashinalar.sort())
print(viloyatlar)
```

    None
    ['andijon', "far'ona", 'namangan', 'qashqadaryo', 'samarqand', 'surxondaryo', 'toshkent', 'xorazm']
    

Biz kutgan natijani qisman oldik yani birinchi print dan natija None keldi bu nega sodir bo'ldi buning sababi **.sort()** natija qaytarmaydi bu listni o'zgartiradi. Ikkinchi print esa kutilgan natijani berdi ya'ni tartiblangan natija.

Diqqat! Tartiblashda katta harflar kichik harflardan avval kelishini hisobga oling. Agar matndagi so'zlarning bosh harfi katta-kichik aralash yozilgan bo'lsa, ularni bir ko'rinishga keltirib olish maqsadga muvofiq bo'ladi


```python
mashinalar=['damas', 'naxia', 'tico', 'Ravon', 'Tracker', 'aveo']
mashinalar.sort()
print(mashinalar)
```

    ['Ravon', 'Tracker', 'aveo', 'damas', 'naxia', 'tico']
    

Yuqoridagi misolda diqqat qilgan bo'lsangiz mashina nomlar tartiblandi ammo oldin katta harflar tartiblandi keyin kichik harflar tartibga keltirildi.

Ro'yxatni teskari tartibda saqlash uchun **.sort()** metodi ichida reverse=True argumentini kiritamiz.


```python
mashinalar=['damas', 'tico', 'matiz', 'aveo', 'bmw', 'nexia', 'tracker']
mashinalar.sort()
print(mashinalar)
mashinalar.sort(reverse=True)
print(mashinalar)
```

    ['aveo', 'bmw', 'damas', 'matiz', 'nexia', 'tico', 'tracker']
    ['tracker', 'tico', 'nexia', 'matiz', 'damas', 'bmw', 'aveo']
    

**.sort()** metodi ro'yxatni tartiblaydi. Ba'zida asl ro'yxat o'zgartirilmasdan ketma-ketlikni tartiblash talab qilinadi bunda 
biaga **sorted()** funksiyasi yordam beradi ya'ni sorted funksiyasi
asl ro'yxatni o'zgartirmagan holda tartiblangan natijani qaytaradi.


```python
mashinalar=['damas', 'tico', 'matiz', 'aveo', 'bmw', 'nexia', 'tracker']
mevalar=['olma', 'nok', 'shaftoli', 'uzum', 'banan', 'anor', 'tarvuz']
mashinalar.sort()
print("Sort metodining natijasi :", mashinalar)
print("Sorted funksiyasining qaytargan natijasi :", sorted(mevalar))
```

    Sort metodining natijasi : ['aveo', 'bmw', 'damas', 'matiz', 'nexia', 'tico', 'tracker']
    Sorted funksiyasining qaytargan natijasi : ['anor', 'banan', 'nok', 'olma', 'shaftoli', 'tarvuz', 'uzum']
    

Sorted funksiyasi ham teskari tartiblay oladi buning uchun sorted funksiyasiga reverse=True beriladi.


```python
katta_harfli_ismlar=['anvar', 'davron', 'botir', 'Temur', 'Sarvar', 'Farrux']
kichik_harfli_ismlar=['anvar', 'davron', 'botir', 'temur', 'sarvar', 'farrux']
print("Sorted teskari natija aralsh harflar uchun :", sorted(katta_harfli_ismlar, reverse=True))
print("Sorted teskari natija bir xil harflar uchun :", sorted(kichik_harfli_ismlar, reverse=True))
```

    Sorted teskari natija aralsh harflar uchun : ['davron', 'botir', 'anvar', 'Temur', 'Sarvar', 'Farrux']
    Sorted teskari natija bir xil harflar uchun : ['temur', 'sarvar', 'farrux', 'davron', 'botir', 'anvar']
    

Yuqoridagi ikki usul bilan sonli ro'yxatlarni ham tartiblashimiz mumkin:


```python
ages=[12, 98, 34, 65, 76, 11]
ages.sort()
print(ages)
print(sorted(ages, reverse=True))
```

    [11, 12, 34, 65, 76, 98]
    [98, 76, 65, 34, 12, 11]
    

#### Ro'yxatni aylantirish
Ba'zida ro'yxatni aylantirish (boshini oxiriga, oxiriga boshiga) talab qilinishi mumkin. Buning uchun **.reverse()** metodidan foydalanamiz.


```python
mevalar=['banan', 'olma', 'uzum', 'kivi', 'nok', 'anjir']
mevalar.reverse()
print(mevalar)
```

    ['anjir', 'nok', 'kivi', 'uzum', 'olma', 'banan']
    

Natija va asl ro'yxatni solishtiring.

#### Ro'yxatning uzunligini bilish
Ro'yxatning uzunlini, ya'ni uning ichidagi elementlar sonini aniqlash uchun **len()** funksiyasidan foydalanamiz:


```python
fruits=['olma', 'nok', 'anor', 'shaftoli', 'anjir']
print("Elementlar soni: " , len(mevalar)) # len() Ro'yxat uzunligini qaytaradi
```

    Elementlar soni:  6
    

#### range() Funksiyasi
Bu funksiya yordamida biz ma'lum oraliqdagi sonlar ketma-ketligini yaratishimiz mumkin.**list()** funksiyasi yordamida esa bu oraliqni ro'yxat
shaklida saqlab olamiz:


```python
sonlar=list(list(range(0, 10)))
print(sonlar)
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    

Yuqoridagi misolda range(0, 10) funksiyasi 0 dan 9 gacha sonlar ketma-ketliginni shakllantirdi, list(range(0, 10)) esa bu ketma-ketlikni ro'yxatga aylantirdi.

Diqqat! E'tibor qiling range() funksiya ikkinchi indeksdan bitta oldin to'xtaydi ya'ni ikkinchi son qaytarilmaydi.

**range()** yordamida qadamni ham berishimiz mumkin.


```python
juft_sonlar=list(range(0, 20, 2))
toq_sonlar=list(range(1, 20, 2))
print(f"Juft sonlar :", juft_sonlar)
print(f"Toq sonlar :", toq_sonlar)
```

    Juft sonlar : [0, 2, 4, 6, 8]
    Toq sonlar : [1, 3, 5, 7, 9]
    

Agar Sonlar 0 dan boshlansa, range() funksiyaga sonlar tugashi kerak bo'lgan sonni kiritish kifoya. Ya'ni range(0, 10) emas range(10) deb yozsak ham bo'laveradi.

#### Sonli ro'yxatlar ustida sodda amllar
Pythonda ro'yxatlar ustida sodda amallarni ham bajarish mumkin.
Misol uchun ro'yxatdagi eng kichik sonni topish uchun **min()** funksiyasidan, 
eng katta sonni topish uchun esa **max()** funksiyasidan, sonlarning yi'gindisini topish uchun **sum()** funksiyasidan foydalanish mumkin.


```python
narxlar=list(range(10000, 100000, 5000))
arzoni=min(narxlar)
qimmati=max(narxlar)
jami=sum(narxlar)
print(f'Narxlarning eng arzoni {arzoni} qimmati {qimmati} va yi\'indisi esa {jami} ga teng.')
```

    Narxlarning eng arzoni 10000 qimmati 95000 va yi'indisi esa 945000 ga teng.
    

#### Ro'yxatni kesish
Ba'zida ro'yxatning ma'lum qismini ajratib olish talab qilinishi mumkin,  deylik biz quyidagi ro'yxatning birinchi 4 ta elementini ajratib olishimiz kerak, buning uchun biz boshlang'ich va oxirgi indekslarni beramiz:


```python
mashinalar=['damas', 'malibu', 'tico', 'matiz', 'tahoe', 'trailblaizer', 'tracker', 'ravon', 'traverse']
arzon_mashinalar=mashinalar[0:4]
print(arzon_mashinalar)
```

    ['damas', 'malibu', 'tico', 'matiz']
    ['tahoe', 'trailblaizer', 'tracker', 'ravon', 'traverse']
    

Diqqat qiling 2-indeksdan oldingi lemntgacha olinadi.
Ya'ni tepada 0, 1, 2, 3 elementlar olindi ammo biz ikkinchi elementga 4 beran edik.

Bu usul bilan ro'yxatlarning istalgan joyidan elementlarni olishimiz mumkin.


```python
mashinalar=['damas', 'malibu', 'tico', 'matiz', 'tahoe', 'trailblaizer', 'tracker', 'ravon', 'traverse']
print(mashinalar[3:5])
```

    ['matiz', 'tahoe']
    

Agar boshlang'ich indeks berilmasa unda ro'yxatning boshidan boshlab oladi.  
Agar oxirgi ikkinchi indeks berilmasa unda ro'yxatning oxirigacha oladi.  
Agar ikkala indekslar berilmasa unda hamma elementlar olinadi.  


```python
mashinalar=['damas', 'malibu', 'tico', 'matiz', 'tahoe', 'trailblaizer', 'tracker', 'ravon', 'traverse']
print(f"Ro'yxatning boshidan boshlab", mashinalar[:5])
print(f"Ro'yxatning 4-elementidan boshlab", mashinalar[4:])
print(f"Ro'yxatning hammasi :", mashinalar[:])
```

    Ro'yxatning boshidan boshlab ['damas', 'malibu', 'tico', 'matiz', 'tahoe']
    Ro'yxatning 4-elementidan boshlab ['tahoe', 'trailblaizer', 'tracker', 'ravon', 'traverse']
    Ro'yxatning hammasi : ['damas', 'malibu', 'tico', 'matiz', 'tahoe', 'trailblaizer', 'tracker', 'ravon', 'traverse']
    

#### Ro'yxatdan nusxa olish
Demak ba'zan ro'yxatdan nusxa olish talab qilinishi mumkin va bunday vaziyatda nima qilinadi. Bunday hollarda (=) dan foydalansak bo'ladimi?


```python
sonlar=list(range(10))
print(sonlar)
sonlar2=sonlar
sonlar2.append(10)
sonlar2.append(12)

sonlar2.append(11)
print(f"Sonlar ro'yxati : {sonlar}")
print(f"sonlar2 ro'yxati :{sonlar2}")

ismlar=['anvar', 'mavlon', 'komil', 'davron', 'kamol', 'vahob']
print(f"Ismlar ro'yxati asli : {ismlar}")
ismlar2=ismlar
del ismlar2[5]
print(f"Ismlar ro'yxati ismlar2 dan bir element o'chirilganda : \n{ismlar2}")
print(f"Ismlar2 ro'yxati ismlar2 dan bir element o'chirildi : \n{ismlar2}")
ismlar2.append('javlon')
ismlar2.append('temur')
ismlar2.append('aziz')
print(f"Ismlar2 ro'yxatiga elementlar qo'shilgandan keyin Ismlar ro'yxati : \n{ismlar}")
print(f"Ismlar2 ro'yxatiga o'zgartirish kiritildi : \n{ismlar2}")
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    Sonlar ro'yxati : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 12, 11]
    sonlar2 ro'yxati :[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 12, 11]
    Ismlar ro'yxati asli : ['anvar', 'mavlon', 'komil', 'davron', 'kamol', 'vahob']
    Ismlar ro'yxati ismlar2 dan bir element o'chirilganda : 
    ['anvar', 'mavlon', 'komil', 'davron', 'kamol']
    Ismlar2 ro'yxati ismlar2 dan bir element o'chirildi : 
    ['anvar', 'mavlon', 'komil', 'davron', 'kamol']
    Ismlar2 ro'yxatiga elementlar qo'shilgandan keyin Ismlar ro'yxati : 
    ['anvar', 'mavlon', 'komil', 'davron', 'kamol', 'javlon', 'temur', 'aziz']
    Ismlar2 ro'yxatiga o'zgartirish kiritildi : 
    ['anvar', 'mavlon', 'komil', 'davron', 'kamol', 'javlon', 'temur', 'aziz']
    

Tepadagi kodga yana bir bor qayta diqqat qiling.
Bunda e'tibor bering biz kutilgan natijalarga erishmadik yani bunda ikkita ro'yxat ham aslida bitta edi ya'ni bitta ro'yxatga ikkita nom berib qo'ydik xolos ya'ni ro'xat aslida bitta edi va shuning uchun barcha o'zgarishlar ikkala ro'yxatga ham ta'sir qildi.
![image.png](08_listlar_bilan_ishlash_files/image.png)

Endi keling qanday qilib nusxalashni o'rganib olaylik bunda biz nima qilamiz.
Shunchaki mavjuda ro'xatning yoniga [] kvadrat qavslarni o'rtada ikki nuqtasi bilan qoldirib uni yangi ro'xatga tenglash kifoya.


```python
ismlar=['davron', 'laylo', 'komil', 'lobar', 'lola', 'jamol']
ismlar2=ismlar[:]
print(f"Ismlar ro'yxati asli : {ismlar}")
print(f"Ismlar ro'yxati nusxasi : {ismlar2}")
ismlar.append('farhod')
ismlar.append('abror')
ismlar.append('axror')
print(f"Ismlar ro'yxatiga yana qo'shildi : {ismlar}")
print(f"Ismlar ro'yxati o'zraganda nusxasi : {ismlar2}")
print("Endi sonlarga qarang!")
sonlar=list(range(10))
sonlar2=sonlar[:]
print('Sonlar ro\'yxati:', sonlar)
print('Sonlarning nusxasi :', sonlar2)
sonlar.append(10)
sonlar.append(12)
sonlar.append(11)
print(f"Sonlar o'zgardi : {sonlar}")
print(f"Sonlar o'zgarganda nusxasi : {sonlar2}")
```

    Ismlar ro'yxati asli : ['davron', 'laylo', 'komil', 'lobar', 'lola', 'jamol']
    Ismlar ro'yxati nusxasi : ['davron', 'laylo', 'komil', 'lobar', 'lola', 'jamol']
    Ismlar ro'yxatiga yana qo'shildi : ['davron', 'laylo', 'komil', 'lobar', 'lola', 'jamol', 'farhod', 'abror', 'axror']
    Ismlar ro'yxati o'zraganda nusxasi : ['davron', 'laylo', 'komil', 'lobar', 'lola', 'jamol']
    Endi sonlarga qarang!
    Sonlar ro'yxati: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    Sonlarning nusxasi : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    Sonlar o'zgardi : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 12, 11]
    Sonlar o'zgarganda nusxasi : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    

Tepada ko'rganimizdek usulda [:] bilan ro'yxatdan nusxa olsak asl ro'yxat o'zgarmay qoladi.

#### Tuples=O'zgarmas ro'yxat
Dastur yaratish davomida o'zgarmas ro'yxat tuzish talab qilinishi mumkin.
Pythonda bunday ro'yxatlar **tuples** deb ataladi. Tuple ichidagi qiymatlarni bir marta, dastur boshida boshida beriladi va keyin o'zgartirib bo'lmaydi. List dan farqli ravishda, Tuple e'lon qilishda kvadrat qavslar [] o'rniga oddiy qavslar () ishlatiladi.


```python
hafta_kunlari=('dushanba', 'seshanba', 'chorshanba', 'payshanba', 'juma', 'shanba', 'yakshanba')
print(hafta_kunlari)
```

    ('dushanba', 'seshanba', 'chorshanba', 'payshanba', 'juma', 'shanba', 'yakshanba')
    

Tuple elementlariga xuddi ro'yxat elementlariga murojaat qilgandek murojaat qilinaveradi.


```python
oylar=('yanvar', 'fevral', 'mart', 'aprel', 'may', 'iyun')
print(oylar[0])
print(oylar[-1])
print(oylar[1:3])
print(oylar[:4])
```

    yanvar
    iyun
    ('fevral', 'mart')
    ('yanvar', 'fevral', 'mart', 'aprel')
    

Keling Tupe ichidagi elemntlarni o'zgartirib ko'ramiz.


```python
oylar=('yanvar', 'fevral', 'mart', 'aprel', 'may', 'iyun')
oylar[2]='avgust'
print(oylar)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[18], line 2
          1 oylar=('yanvar', 'fevral', 'mart', 'aprel', 'may', 'iyun')
    ----> 2 oylar[2]='avgust'
          3 print(oylar)
    

    TypeError: 'tuple' object does not support item assignment


Demak Tuplega o'zgartirish kiritib bo'lmaydi ammo talab qilinsa unda **tuple**ni **list**ga o'zgartirib keyin yana **tuple**ga qaytarib qo'ya olamiz.


```python
oylar=('yanvar', 'fevral', 'mart', 'aprel', 'may', 'iyun')
print(f"Tuple ning turini tekshiramiz {type(oylar)}")
oylar=list(oylar)
print(f"Tuple ning turini yana tekshiramiz{type(oylar)}")
oylar.append('iyul')
oylar.append('avgust')
oylar.append('sentabr')
oylar.append('oktabr')
oylar.append('noyabr')
oylar.append('dekabr')
oylar=tuple(oylar)
print(f"Endi yana bir bor tekshiramiz {type(oylar)}")

```

    Tuple ning turini tekshiramiz <class 'tuple'>
    Tuple ning turini yana tekshiramiz<class 'list'>
    Endi yana bir bor tekshiramiz <class 'tuple'>
    

1-Topshiriq: Avtomobillar bilan ishlash  
Dunyoga mashhur 6 ta avtomobil brendini o'z ichiga olgan cars ro'yxatini   yarating.  
Ro'yxatni alifbo tartibida sorted() funksiyasi bilan chiqaring.  
Ro'yxatning asl holatini o'zgartirmasdan, uni teskari tartibda (Z-A) konsolga chiqaring.append() metodi orqali ro'yxatga yana bitta brend qo'shing.  
insert() metodi orqali ro'yxatning o'rtasiga "Tesla" brendini joylang.  Ro'yxatni sort() metodi yordamida butunlay alifbo tartibida o'zgartiring va natijani ko'ring.  

2-Topshiriq: Sonli tahlil  
(Data Analysis)10 dan 1000 gacha bo'lgan, faqat 5 ga bo'linadigan sonlar ro'yxatini tuzing (range funksiyasidan foydalaning).  
Ro'yxatdagi barcha sonlarning o'rta arifmetik qiymatini hisoblang:  
$$ \text{O'rta qiymat} = \frac{\text{Elementlar yig'indisi}}{\text{Elementlar soni}} $$
Ro'yxatdan eng kichik 5 ta va eng katta 5 ta sonni slicing (kesish) yordamida alohida ro'yxat qilib chiqaring.  
Ro'yxatning aynan o'rtasida joylashgan 10 ta sonni konsolga chiqaring.  

3-Topshiriq:  
Kutubxona boshqaruvi kitoblar degan ro'yxat yarating va kamida 5 ta kitob nomini kiriting.  
library nomli yangi ro'yxat yarating va unga kitoblar[:] orqali nusxa oling.  library ro'yxatidan 2 ta kitobni o'chirib tashlang (pop yoki remove orqali).  library ro'yxatiga boshiga va oxiriga yangi kitob nomlarini qo'shing.  
Har ikkala ro'yxatni konsolga chiqarib, ular orasidagi farqni tekshiring.  

4-Topshiriq:    
O'zgarmas ro'yxatlar va Xatolar ustida ishlash  
Haftaning 7 kunidan iborat hafta_kunlari nomli o'zgarmas ro'yxat (tuple) yarating.  
Konsolga haftaning faqat ish kunlarini (Dushanbadan Jumagacha) kesib chiqaring.  
hafta_kunlari[0] = "Yakshanba" deb qiymatni o'zgartirishga urunib ko'ring va terminalda qanday xato (TypeError) chiqishini kuzating.  
O'zgarmas ro'yxatni oddiy list() funksiyasi yordamida ro'yxatga aylantiring, unga "Dam olish kuni" degan element qo'shing va yana qaytadan tuple() qilib o'zgartiring.  

5-Topshiriq:  
Mehmonlar ro'yxati (Murakkabroq)mehmonlar ro'yxatini tuzing: ['Ali', 'Vali', 'Hasan', 'Husan', 'Olim'].  
Ro'yxatdagi har bir ismning yoniga "xush kelibsiz!" so'zini qo'shib konsolga chiqaring (buni for tsikli bilan qilsangiz nur ustiga a'lo nur).  
Ro'yxatni uzunligi bo'yicha emas, balki teskari (Z-A) tartibda doimiy saqlab qolish uchun sort(reverse=True) ishlating.
