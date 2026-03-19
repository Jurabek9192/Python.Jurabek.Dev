# BIR NECHA SHARTLAR BILAN ISHLASH

**if-elif-else** zanjiri, **end, or** operatorlari bilan tanishamiz. 

### if-elif-else KETMA-KETLIGI

Dastur davomida bir nechta shartni tekshirish talab qilinishi mumkin. Buunday holatlarda biz **if-elif-else** ketma-ketligidan foydalanamiz. elif-else va if so'zlarining jamlanmasi bo'lib, **"aks holda, agar"** deb tarjima qilsak xato bo'lmaydi. if bilan boshlangan ketma-ketlikda bir necha elif lardan foydalanishimiz mumkin.

Python avval if shartni tekshiradi, shart bajarilmasa elif ga o'tadi, birinchi elif sharti bajarilmasa keyingi elif ga o'tadi va hokazo davom etaveradi.

 Diqqat!if-elif-else ketma-ketlikda biror shart bajarilishi bilan, Python qolgan shartlarni tekshirmaydi.

Keling bir misol ko'ramiz. Teatrga kirish uchun biletning narxini quridagi shartlar asosida belgilangan bo'lsin.

* 4 yoshgacha bolalarga kirish tekin
* 4 yoshdan 12 yoshgacha irish 5000 so'm
* 12 yoshdan kattalarga 10000 so'm

Foydalanuvchidan yoshini so'rab, teatrga kirish chiptasini narxini chiqaruvchi dastur yozamiz


```python
yosh=int(input("Yoshingizni kiriting :"))
if yosh<=4:
    print("Sizga kirish tekin.")
elif yosh<=12:
    print("Sizga kirish 5000 so'm")
else:
    print("Sizga kirish 10000 so'm.")
```

Yuqoridagi kod avval foydalanuvchi yoshini so'raydi. 2-qatorda yosh 4 dan kichik ekanligini tekshiradi. Agar bu shart bajarilsa shartlarni tekshirish shu yerdayoq tugaydi va keyingi shartlar tashlab ketiladi.

Agar yosh<=4 shart bajarilmasa, keyingi elif yosh<=12 sharti tekshiriladi, agar shart bajarilsa **Sizga kirish 5000 so'm** natija chiqadi.

Agar yuqoridagi shart bajarilmasa unda **Sizga kirish 10000 so'm**
natija chiqib keladi.

Kod yozishda yaxshi amaliyotlardan biri, kodlarni qisqa yozish va buyruqlarni qayta-qayta takrorlamaslik. Bu kelajakda kodni o'zgartirishda ham juda qo'l keladi. 


```python
yosh=int(input("Yoshingizni kiriting :"))
if yosh<=4:
    price=0
elif yosh<=12:
    price=5000
else:
    price=10000

print(f"Sizga kirish {price} so'm.")
```

if-elif-else zanjirida ham else qismi majburiy emas.


```python
score=int(input("Balingizni kiriting: "))
if score>=90:
    mark="A"
elif score>=80:
    mark="B"
elif score>=70:
    mark="C"
elif score>=60:
    mark="D"
elif score<60:
    mark="F"

print(f"Sizning bahoyingiz {mark}")

```

#### AND, OR OPERATORLARI

Yuqorida aytganimizdek, if-elif-else zanjirida shartlarning biri bajarilishi bilan,
Python qolgan shartlarni tekshirmaydi va ularni bajarmaydi. Lekin ba'zida biz 2 yoki undan ko'p shartlarni tekshirishni talab qilishimiz mumkin, buning uchun AND va OR operatorlaridan foydalanamiz.

OR ingliz tilidan "yoki" deb tarjima qilinadi va u ikki va undan ko'p shartlardan biri bajarilishini tekshirishda ishlatiladi. Quyidagi misolni ko'raylik, foydalanuvchidan hafta kunini so'raymiz va agar kun shanba yoki yakshanba bo'lsa, bugun dam olish kuni degan xabarni chiqaramiz, aks holda bugun ish kuni degan xabarni chiqaramiz.


```python
kun=input("Bugun nima kun ?>>>")
if kun.lower()=="shanba" or kun.lower()=='yakshanba':
    print("Bugun dam olish kuni.")
else:
    print("Bugun ish kuni.")
```

2-qatordagi or opertoriga e'tibor qiling, bu opertor kun.lower()=='shanba' yoki
kun.lower()=='yakshanba' shartlaridan biri bajarilsa TRUE qiymatini qaytaradi.

#### AND OPERATORI

AND ingliz tilidan "va" deb tarjima qilinadi va ikki va undan ortiq dhartlarning hammasi ya'ni hamma shartlari bajarilgandagina TRUE qiymat qaytadi, agar shartlarning bittasi bajarilmay qolsa ham undan FALSE qaytadi.

Quyidagi misolni ko'ramiz.


```python
login=input("Logingizni kiriting :")
if "admin" in login.lower() and login[-1]=="9":
    print("Assalamu elkum admin.")
elif "superuser" in login.lower() and login[-1]=="5":
    print("Assalamu alekum superuser.")
```

Yuqoridagi kodimizda and operatori ikkita shartni bajarilishini tekshirib ikkalasi ham 
TRUE qaytarsa shundagina if yoki elifning ichiga kirib sshu qismda kodni yakunlaydi.

#### BIR NECHTA SHARTLARNI KETMA-KET YOSISH

Shartlarni yozishda bir necha and or opertarolarini aralashtirib ham kod yozish mumkin.


```python
kun=input("Bugun kun nima :")
toza=input("Uy yig'ishtirilganmi ?")
if (kun.lower()=="shanba" or kun.lower()=="yakshanba") and toza.lower()=="ha":
    print("Demak endi dam olsangiz bo'ladi.")
elif (kun.lower()=="shanba" or kun.lower()=="yakshanba") and toza.lower()=="yo'q":
    print("Demak uyni yig'ishtirishingiz kerak.")
```

Yuuqoridagi kodga diqqat qilining biz if shartlarni tekshirishda albatta or ya'ni yoki qismida () qavslar bilan ajratdik buning sababi and qismining shartlari or qismining shartlaridan oldin tekshiriladi va buni eslab qolsangiz yaxshi bo'lardi.

#### BOOLEAN MA'LUMOTLAR TURI

Avval darsimizda biz turli ifodalarni solishtirish TRUE yoki FALSE qiymatlari qaytishini ko'rdik. Bu qiymatlar boolean (mantiqiy) qiymatlar deb ataladi va dasturlashda juda keng tarqalgan va qo'llaniladi. Pythonda o'zgaruvchilarda boolean qiymatlarni ham saqlash mumkin.

Quyidagi dasturga e'tibor bering. Deylik mehmoxonaning mijozi bir kechalik mehmonxonada qolishni istagan va unga taqsdim qilinadigan xizmatlarning ichidan nonushta pullik edi mijoz buni ishlatib qo'ygan yana boshqa xizmatlar ham bor va mijoz bulardan foydalansa unga qo'shimcha to'lov qilishi kerak bo'ladi.


```python
mehmonxona_bir_kecha=100_000
kofe=True
nonushta=True

if kofe and nonushta:
    mehmonxona_bir_kecha+=20000
elif kofe or nonushta:
    mehmonxona_bir_kecha+=10000

print(f"Jami narx {mehmonxona_bir_kecha} so'm.")
```

    Jami narx 120000 so'm.
    

Bunda diqqat qilishingiz kerak bo'lgan narsa biz shartlarga kofe va nonustani qanday dir qiymatga tenglikka tekshirmadik balki bularning o'zlari True va False qiymatlari qaytgani uchun shunchaki shu qiymatlarning o'zinigina TRUE va FALSE qiymatlarga tekshirib qo'ydik.

Boolean o'zgaruvchilarni saqlashda TRUE va FALSE qiymatlari o'rniga 1 va 0 sonlarini ham ishlatish mumkin.

#### SHARTLARNI KETMA-KET TEKSHIRISH

if-elif-else zanjirining kamchiligidan biri, shartlardan biri bajarilishi bilan, qolgan shartlar tekshirilmaydi. Shuning uchun ba'zida shartlarni ketma-ket tekshirish uchun, har bir shartni alohida if bilan ajratish talab qilinishi talab qilinishi mumkin.

Yuroqidagi misolni kengaytiraylik:


```python
mehmonxona=100_000
kofe=True
nonushta=True
xona_xizmati=False
dessert=True
maxsus_xizmat=False
# Quyida har bir shartni alohida tekshiramiz
if kofe:
    print("Mijoz kofe oldi.")
    mehmonxona+=10000
if nonushta:
    print("Mijoz nonushta qildi.")
    mehmonxona+=10000
if xona_xizmati:
    print("Mijoz xona xizmatidan foydalandi.")
    mehmonxona+=10000
if dessert:
    print("Mijoz dessert oldi.")
    mehmonxona+=10000
if maxsus_xizmat:
    print("Mijoz maxsus xizmatlardan foydalandi.")
    mehmonxona+=10000

print(f"Jami {mehmonxona} so'm.")
```

    Mijoz kofe oldi.
    Mijoz nonushta qildi.
    Mijoz dessert oldi.
    Jami 130000 so'm.
    

Yuqoridagi dasturda har bir if alohida tekshiriladi va avvalgi yoki keyingi if ga bog'liq emas.

if-elif-else bu zanjir ba'zida qisqa tekshirish maqsadida bir qatorda ham ishlatilishi mumkin:


```python
num=5
if num>=0: print("Musbat")
else: print("Manfiy")

print("Manfiy") if num<0 else print("Musbat")

```

    Musbat
    Musbat
    

Yuqoridagi misol shuni bildiradiki biz ba'zi qisqa tekshirishlarni bir qator koda yozish orqali amalga oshirishimiz mumkin. Ba'zan esa buni quyidagicha ishlatishimiz mumkin:


```python
num=3
ishora="Musbat" if num>=0 else "Manfiy"
print(ishora)
```

    Musbat
    

Yuqoridagi miisolda biz ishora nomli o'zgaruvchiga qiymatni yuklashdan oldin num ning ishorasini tezda tekshirib olishimiz imkonini beradi hatto quyidagicha ham ishlatishimiz mumkin:


```python
num=0
ishora="Musbat" if num>0 else "Nol" if num==0 else "Manfiy"
print(ishora)
```

    Nol
    

Ammo ko'p shartlarni tekshirishda bir qatorli tekshrish doim ham damarali bo'lmadyi.

#### ALL VA ANY FUNKSIYALARI

IF lar bilan ishlatiladigan **all** va **any** funksiyalarini ham e'tibordan chetda qoldirmaslikni xohladik.

**all** ingliz tilidan hammsi yoki barchasi deb tarjima qilinadi va unga qiymatlar list (ro'yxat) sifarida beriladi va faqatgina barcha elemntlar TRUE bo'lsagina bu funksiya TRUE qaytaradi:

Keling quyida bir misol ko'raylik bunda foydalanuvchi o'zi uchun daytga kirishda parol tanlayapdi degan faraz bilan unga parolda kamida bitta son, kichik harf, katta harf, bitta belgi larni kiritishini so'rashimiz kerak:


```python
kichik_harf=True
son=True
katta_harf=True
belgi=False

if all([son, kichik_harf, katta_harf, belgi]):
    print("Parol qabul qilindi.")
else:
    print("Paarolda kamida bitta belgi, son , katta harf va kishik harf bo'lishi kerak.")
```

    Paarolda kamida bitta belgi, son , katta harf va kishik harf bo'lishi kerak.
    

Yuqoridagi kodni siz istagandek o'zgartirib ishlatib ko'ring va bunda bizning kodimiz else qismining print ni ishlatdi chunki bizda bitta False bor edi va bu **all** dab False qaymat qaytardi.

Keling endi tepadagi kodni any bilan ishlatib ko'ramiz:


```python
kichik_harf=False
son=False
katta_harf=True
belgi=False

if any([son, kichik_harf, katta_harf, belgi]):
    print("Parol qabul qilindi.")
else:
    print("Paarolda kamida bitta belgi, son , katta harf va kishik harf bo'lishi kerak.")
```

    Parol qabul qilindi.
    

Ko'rganimizdek bizning kodda bu gal any bittagina True qiymati mavjudligi uchun True qiymat qaytardi va bunda any shu tartibda ishlayi yani berilgan elemntlar orasida bittagina True qiymat mavjud bo'lsa ham True natija qaytaradi.

#### in not in OPERATORI

in va not in operatorlari bu biron character (belgi) ning matn ichida yoki biron elemntning biron listning ichida mavjud ekanligini va mavjud emasligini tekshiradi.

Keling buni bir necha misollar bilan tekshirib olaylik:



```python
matn="kitob yangilandi"
if "kitob" in matn:
    print("Kitob matnda mavjud ekan.")
else:
    print("Kitob mathda mavjud emas.")
```

    Kitob matnda mavjud ekan.
    


```python
matn="Biz yangi bilimlarni egallaymiz."
if "bilim" not in matn:
    print("Siz bilimga qiziqmas ekansiz.")
else :
    print("Siz bilimga chanqoq ekansiz.")
```

    Siz bilimga chanqoq ekansiz.
    

Tepadagi in va not in operatorlari ro'yxatlar bilan ham ayni shu tartibda ishlaydi.

#### TOPSHIRIQLAR

Foydalanuvchidan yoshini so'rang: agar 7 yoshdan kichik bo'lsa "Bog'cha bolasi", 7 dan 18 yoshgacha bo'lsa "Maktab o'quvchisi", aks holda "Kattalar" deb chiqaruvchi dastur tuzing.

O'zgaruvchiga ixtiyoriy son yuklang va u musbat ekanligini if-else yordamida bir qatorda tekshirib, natijani ekranga chiqaring.

Foydalanuvchidan bugun nima kun ekanligini so'rang. Agar kun "Shanba" yoki "Yakshanba" bo'lsa "Bugun dam olish kuni", aks holda "Ish kuni" degan xabarni chiqaring.

Ikki xil Boolean o'zgaruvchi yarating: uy_ishi_bajarilgan = True va xona_toza = True. Agar ikkalasi ham True bo'lsa, "Siz o'yinga ruxsat oldingiz" deb chiqaring.

all() funksiyasidan foydalanib, meva savatida "olma", "banan" va "uzum" borligini (hammasi True bo'lganda) tekshiruvchi kod yozing.

Foydalanuvchi kiritgan so'zda "a" harfi bor yoki yo'qligini in operatori yordamida tekshiring.

Mehmonxona misolidagi kabi, agar mijoz "kofe" yoki "nonushta"dan birini tanlagan bo'lsa, narxga 10 000 so'm qo'shuvchi elif zanjiri tuzing.

any() funksiyasi yordamida kamida bitta shart bajarilganda "Xush kelibsiz" so'zini chiqaruvchi dastur yozing.

Foydalanuvchidan parolda kamida bitta son borligini va u "9" bilan tugashini and operatori orqali tekshiring.

Matn ichida "maktab" so'zi yo'qligini not in operatori yordamida tekshiruvchi kod tuzing.

O'quvchining balini so'rang: 90 dan yuqori bo'lsa "A", 80 dan yuqori bo'lsa "B", 70 dan yuqori bo'lsa "C" baholarini chiqaruvchi if-elif zanjirini tuzing.

if-elif-else zanjirida else qismini ishlatmasdan, faqat elif yordamida 3 xil rangni (qizil, sariq, yashil) tekshiruvchi svetofor dasturini yozing.

Foydalanuvchidan ismini so'rang. Agar ismi "Admin" bo'lsa va oxirgi belgisi son bo'lsa, "Assalomu alaykum" deb chiqaring.

num = 0 bo'lganda, bir qatorli kod yordamida "Nol", "Musbat" yoki "Manfiy" degan qiymatni o'zgaruvchiga yuklang.

Shartlarni qavslar ichiga olgan holda, kun dam olish kuni ekanligini VA uy yig'ishtirilganligini birgalikda tekshiring.

Boolean o'zgaruvchilar uchun True o'rniga 1 sonini, False o'rniga 0 sonini ishlatib, narxni hisoblovchi kod yozing.

Bir nechta mevalar ro'yxatini yarating va foydalanuvchi so'ragan meva ro'yxatda borligini in operatori bilan aniqlang.

if operatori yordamida foydalanuvchi kiritgan son juft yoki toqligini aniqlang (maslahat: % operatoridan foydalaning).

Dasturda 5 ta alohida if yozing, ular mijoz buyurtma bergan har bir qo'shimcha mahsulot uchun narxni 5000 so'mdan oshirib borsin.

Foydalanuvchidan parolni so'rang va u kamida 8 ta belgidan iborat ekanligini len() funksiyasi hamda if yordamida tekshiring.
