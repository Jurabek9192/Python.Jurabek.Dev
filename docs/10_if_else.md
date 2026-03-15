# IF-ELSE

Dasturni tarmoqlashni o'rganamiz

# Tarmoqlanish

Shu paytgacha yozgan kodlarimizga bir qaraylik biz shu vaqtgacha faqat tepadan pastga qarab o'qiladigan kodlarni yozib keldik. Ya'ni kodlarimiz tepadan pastga qarab bajariladigan kodlarni yoaxib keldik.
Ammo dasturlashda hamma kodlar ham faqat tepadan pastga qarab ishlamaydi ya'ni biron narsa sodir bo'lsa nimadir bo'lsin qabilida ishlaydi ya'ni biron shart bo'lsa nimadir bo'ladi xuddi shu tartibda amalga oshadi hammasi.
Buni esa dasturlashda **tarmoqlanish** deb ataladi.


![IF, ELSE, ELSE IF Statement in R.jpg](<10_if_else_files/IF, ELSE, ELSE IF Statement in R.jpg>)

Ushbu darsimizda biz **if** operatori yordamida shunday shartlar bilan ishlashni o'rganamiz

### if OPERATORI

**if** so'zi ingliz tilidan **"agar"** deb tarjima qilinadi va deeyarli barcha dasturlash tillarida shartlarni yozish uchn ishlatiladi. 

Keling ba'zi misollarda **if** operatorini ishlatib ko'raylik


```python
ism="farhod"
if ism.endswith("hod"):
    print(f"Sizning ismingiz {ism.title()}")

```

    Sizning ismingiz Farhod
    

Tepadagi kodni tahlil qilaylik bunda ya'ni nima sodir bo'lyapdi.

1-qatorda biz *ism* degan o'zgaruvchiga "farhod" degan ma'lumotni yukladik

2-qatorda ismni *endswith* metodi orqali bu ism hod bilan tugaganmi yoki yo'qmi buni tekshirib oldik va **if** shart operatorining ichida 

3-qatorda agar bu rost bo'lsa ya'ni ism *hod* bilan tugasa unda bu ismni *title* metodi orqali birinchi harfini katta qilib chiqarib ber degan buyruqni berdik va agar ism *hod* bilan tugamasa unda ismning o'zini chiqarib ber degan buyruqni berdik.

Diqqat! Shart "badani" shartdan biroz o'ngga surib yoziladi (huddi for tsikli kabi). if/else dan keyin kelgan va o'ngga surib yozilgan har bir qator if/else shartining badani hisoblanadi.

Keling yana bir necha misollarni bajaraylik bunda bizga yanada tushunarli bo'ladi


```python
text="Men bmw mashinasini yaxshi ko'raman"
if text.find('bmw') !=-1:
    text=text.replace('bmw', 'BMW')
print(text)
```

    Men BMW mashinasini yaxshi ko'raman
    


```python
ism='kamola'
if ism.endswith('a'):
    print(f"{ism.title()} siz qiz bolasiz.")
```

    Kamola siz qiz bolasiz.
    


```python
ism='davron'
if not ism.endswith('a'):
    print(f"{ism.title()} siz o'g'il bolasiz.")
```

    Davron siz o'g'il bolasiz.
    

Tepadagi misollar bizga if shart operatorini yanada yaxshiroq tushunib olishimiz uchun xizmat qildi degan umiddaman.

### TRUE/FALSE

Yuqorida shartni tekshirish uchun **==** operatoridan foydalandik. Bu oddiy tilda **tengmi** degan ma'noni anglatadi.

Agar shartning ikki tomoni qiymatlari teng bo'lsa **True** degan qiymat qaytaradi ("True" so'zi ingliz tilidan "Haqiqiy" yoki "Rost" yokida "To'g'ri"
deb tarjima qilinadi.)

Aksincha qiymatlar tenglikni qanoatlintirmasa ifoda **False** degan qiymatni qaytaradi ("False" ingliz tilidan "yolg'on" deb tarjima qilinadi.)

Quyidagi misolga diqqat qiling biz ism degan o'zgaruvchi yasaymiz va unga 'Ali' matnini yuklaymiz. Endi esa keling == operatori yordamida ism degan o'zgaruvchining qiymatini tekshirib ko'ramiz.


```python
ism='Ali'              # ism degan o'zgaruvchiga 'Ali' degan qiymat yukladik
print(ism=='Ali')      # ism 'Ali' ga tengmi tekshirib ko'ryapmiz

print(ism=='Vali')     # ism 'Vali' ga tengmi buni ham tekshirdik.
```

    True
    False
    

Bu yerda ko'rganimizdek avval ism=='Ali' (ism 'Ali' ga tengmi?) deb so'raganimizda ifoda bizga True(Ha) bu ism 'Ali' ga teng degan qiymatni qaytardi, keyin esa ism=='Vali' (ism 'Vali' ge tengmi?) deb so'raganumizda esa, ifoda bizga False (Yo'q) degan qiymatni qaytardi ya'ni ism 'Vali' ga teng emas degan natijani oldik. 

Endi biz yana bir operator yoki **if** bog'lamasi **else** bilan tanishsak bo'ladi bu ifoda ya'ni **else** ingliz tilidan "bo'lmasa" yoki "aks holda" deb tarjima qilsak bo'ladi yani agar bir shart berilsa buni bajar agar shart bajarilmasa unda bunisini bajar degan buyruqni anglatadi ya'ni if qismi bergan shartimizdan True qaytganda va else qismi esa False qaytganda ishga tushadi.

#### MATNALRNI SOLISHTIRISH

Aksar tizimlar foydalanuvchi kiritgan ma'lumotlarni bir formatga keltirib oladi bu ma'lumotlar bilan ishlashda va foydalanuvchi ma'lumotlarini izlashda juda samarali usul hisoblanadi va qolaversa kopyuter uchun 'Aziz', 'AZIZ' va 'aziz' bu uchta turli xil ism. Ularni solishritish uchun esa bir ko'rinishga keltirib olish kerak.

Tasavvur qiling siz yangi email ochmoqchisiz, va o'zingizga yangi foydalanuvchi ismini qanlashingiz kerak. Kompyuter siz siz kiritgan ism yoki loginni tizimdagi mavjud ismlar bilan solishtirib ko'rishi agar bunday foydalanuvchi mavjuda bo'lsa unda bunday foydalanuvchi mavjud siz boshqa login yoki ism tanlang degan xatolikni sizga shiqarib berishi kerak bo'ladi ammo agar bunni tekshirmasdan sizning ma'lumotlarni ham ola boshqa foydalanuvchining ham sizning ism bilan bir xil ismni olsa keyinchalik tiqimdan o'zingiz haqingizdagi ma'lumotni olishga urinsangiz sizning emas boshqa foydalanuvchining ma'lumotlarini chqairb bersa bu qanchalik yomon ekanini o'zingiz taxmin qiling bunda foydalanuvchilarning ma'lumotlari himoyalanishi buziladi bu albatta juda yomon.


Aynan mana shu muammolar sodir bo'lmasligi uchun ham kiritlgan ismlarni oldin hammsini kichik yoki katta formatga o'tkazib olib keyin bunday foydalanuvchi mavjudami yo'qmi buni tekshirib olishi kerak bo'ladi va undan keyin ma'lumotni tizimga kiritishi kerak bo'ladi.

![Suggested Content.jpg](<10_if_else_files/Suggested Content.jpg>)

Hop biz nima uchun ma'lumotlarni kir xil formaga keltirishni tushunib oldik ammo bu aslida qanday amalga oshiriladi?
Bu judda oddiy biz shu patygacha foydalangan **lower()** metodimizdan foydalangan holda amalga oshiramiz buni



```python
ism='Ali'

print(ism.lower()=='ali')
```

    True
    

#### QIYMATLARNI TENG YOKI TENG EMASLIGINI TEKSHIRISH

Agar ikki qiymat teng emasligini tekshirish talab qilinsa, **!=** opertoridan foydalanamiz.


```python
ism=input("Ismingizini kiriting : ")

if ism.lower() !="hasan" :
    print(f"{ism.title()} kechirasiz siz Hasan emassiz.")
else : print("Assalamu alekum Hasan.")
```

    Dsdxfg kechirasiz siz Hasan emassiz.
    

Demak biz yuqoridagi kodda nima qildik oldin biz foydalanuvchidan isminni kiritishini so'radik va uning ismini ism degan o'zgaruvchiga yukladik va buni, ya'ni ismni **lower()** metodi orqali kichik harflarga o'tkazib oldik va *"hasan"* bilan bir emasmi tekshirib oldik va unday emas ya'ni ism boshqa bo'lsa shunchaki biz Hasanni kutayoganimizni bildirdik xolos.

Shartlarda else qismi bo'lishi majburiy emas. Bunga keyingi bo'limlarda tushunarliroq misollar ko'ramiz.

#### SONLARNI SOLISHTIRISH

Keling endi biz ishlatgan opertaorlar **(==), (!=)** larni sonlar uchun ham ishlatib ko'raylik

Kichik: a<b

Kichik yoki teng: a<=b

Katta: a>b

Katta yoki teng: a>=b


```python
son=32
if son==23: print("Siz hali yoshsiz.")
else : print("Siz qaridingiz.")
```

    Siz qaridingiz.
    


```python
son=18
if son!=20: print("Siz 20 da emas ekansiz.")
else : print("Siz 20 da ekansiz.")
```

    Siz 20 da emas ekansiz.
    


```python
javob=int(input("6x6 nechiga teng "))
if javob!=36 : print("Siz xato javob berdingiz")
else : print("Siz to'g'ri javob berdingiz.")
```

    Siz to'g'ri javob berdingiz.
    


```python
login = input("Yangi login tanlang:")
if len(login)<=5: # login uzunligini tekshiramiz
    print("Login 5 harfdan ko'proq bo'lishi shart!")
```

Sonlarni solishtirishda arifetik ifodalar ham yozishimiz mumkin


```python
yil = int(input("Tug'ilgan yilingizni kiriting:"))
if 2020-yil<18: # foydalanuvchining yoshini hisoblaymiz
    print(f"Yoshingiz {2020-yil}da ekan.")
    print("Kirish mumkin emas!")
else:
    print("Xush kelibsiz!")
```

    Xush kelibsiz!
    

#### BIR QATOR if/else

Qisqa kodlar uchun shart va uning badanini 1 qatorga jamlab ham yoszishimiz mumkin.


```python
yosh=int(input("Yoshingizni kiriting : "))

if yosh>65: print("Siz nafaqa yoshidasiz.")
```

    Siz nafaqa yoshidasiz.
    

Yoki:


```python
x, y = 25, 50 # x=25 va y=50
print("x>y") if x>y else print("x<y")
```

    x<y
    

🟢 Oson daraja (1-7)  
Toq yoki juft: Foydalanuvchi kiritgan sonni juft yoki toqligini aniqlab beruvchi dastur tuzing.  
Musbat yoki manfiy: Kiritilgan son noldan katta bo'lsa "Musbat", kichik bo'lsa "Manfiy", nolga teng bo'lsa "Nol" deb chiqaring.  
Yosh cheklovi: Foydalanuvchining yoshini so'rang. Agar 18 dan katta bo'lsa "Xush kelibsiz", kichik bo'lsa "Kirish taqiqlanadi" deb yozing.  
Hafta kunlari: 1 dan 7 gacha son kiriting va unga mos hafta kunini (Dushanba, Seshanba...) chiqaring.  
Eng katta son: Ikkita son kiriting va ularning kattasini konsolga chiqaring.  
Baholash tizimi: Talabaning foizini (0-100) so'rang. 90+ bo'lsa "A", 80+ bo'lsa "B", 70+ bo'lsa "C" va undan past bo'lsa "F" deb chiqaring.  Foydalanuvchi nomi: Foydalanuvchi ismini so'rang. Agar ism "Admin" bo'lsa "Xush kelibsiz, boshliq", aks holda "Salom, [ism]" deb chiqaring.  
🟡 O'rta daraja (8-15)  
Uchta sonning eng kattasi: Foydalanuvchi uchta turli xil son kiritsin. Ulardan eng kattasini if-elif-else yordamida toping.    
Parol tekshiruvi: Foydalanuvchidan yangi parol va uning tasdig'ini so'rang. Agar ular bir-biriga mos kelsa "Parol o'rnatildi", aks holda "Xato: Parollar mos kelmadi" deb chiqaring.  
Fasllar: Oy raqamini kiriting (1-12). Shunga qarab yilning qaysi fasli ekanligini aniqlang.  
Harorat tavsiyasi: Haroratni (Celsius) so'rang. Agar 0 dan past bo'lsa "Juda sovuq, palto kiying", 0-20 oralig'ida bo'lsa "Havo salqin", 20-35 oralig'ida bo'lsa "Yaxshi ob-havo", 35 dan yuqori bo'lsa "Juda issiq" deb chiqaring.  
Login tizimi: Foydalanuvchi nomi va parolni so'rang. Agar username="user123" va password="p@ssword" bo'lsa "Tizimga kirdingiz", aks holda "Ma'lumotlar xato" deb chiqaring.  
Kabisa yili: Kiritilgan yil kabisa yili ekanligini aniqlang (4 ga bo'linadigan, lekin 100 ga bo'linmaydigan yoki 400 ga bo'linadigan yillar).  
To'rtburchak turi: To'rtburchakning ikki tomonini so'rang ($a$ va $b$). Agar ular teng bo'lsa "Kvadrat", teng bo'lmasa "To'rtburchak" deb chiqaring.  
Bo'linish alomati: Son 3 ga ham, 5 ga ham qoldiqsiz bo'linsa "FizzBuzz", faqat 3 ga bo'linsa "Fizz", faqat 5 ga bo'linsa "Buzz" deb chiqaring.  
🔴 Murakkabroq mantiq (16-20)  
Uchburchak sharti: Foydalanuvchi uchta son ($a, b, c$) kiritadi. Shu sonlar uchburchakning tomonlari bo'la oladimi yoki yo'qligini aniqlang ($a+b > c$ va h.k.).  
Chipta narxi: Kinoteatr uchun chipta: agar foydalanuvchi 7 yoshdan kichik bo'lsa 5000 so'm, 7-18 yoshda bo'lsa 10000 so'm, 18-65 yoshda bo'lsa 20000 so'm, 65 dan katta bo'lsa bepul.  
Kalkulyator: Ikkita son va bitta amal (+, -, *, /) so'rang. Tanlangan amalga qarab natijani hisoblang (Nolga bo'lish xatosini ham hisobga oling).  
Oylik ish haqi: Foydalanuvchi ishlagan soatini kiriting. Agar 40 soatdan ko'p ishlagan bo'lsa, ortiqcha soatlar uchun 1.5 barobar ko'p haq to'lanishini hisobga olgan holda umumiy summani hisoblang.  
Taksi narxi: Taksi yo'l haqi: birinchi 3 km uchun 5000 so'm (fiksirlangan), undan keyingi har bir km uchun 2000 so'm. Foydalanuvchi kiritgan masofaga qarab narxni chiqaring
