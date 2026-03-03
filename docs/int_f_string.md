### int

**int**
bu nima bu ma'lumot turi hisoblanadi 
**string** bilan nimasi bilan farqlanadi bunda quyidagi kodega e'tibor bering


```python
son1=12
son2="12"
print("Bu yerda int ma'lumot turini kirityapmiz",son1)
print("Bu yerda string ma'lumot turini kirityapmiz",son2)

```

    Bu yerda int ma'lumot turini kirityapmiz 12
    Bu yerda string ma'lumot turini kirityapmiz 12
    

Ko'ganmizdek hech qanday farq yo'q yani biz seza oladigan o'zgarish yo'q
ammo endi yana bir razm soling keyingi kodga 


```python
son1=12
son2="12"
print("Bu yerda int turidagi ma'lumotlarni qo'shish", son1+son1)
print("Bu yerda string turidagi ma'lumotlarni qo'shish", son2+son2)
```

    Bu yerda int turidagi ma'lumotlarni qo'shish 24
    Bu yerda string turidagi ma'lumotlarni qo'shish 1212
    

Menimcha farqni sezdingiz bu yaxshi agar sezmagan bo'lsangiz bunda int turidagi qiymatlar matematik amallardagi kabi qo'shildi ammo string turidagilari esa ketma-ket yani text sifatida qo'shildi endi keyingi kodimizga etibor bering


```python
son1=12
son2="12"
print("Biz int va string turidagi ma'lumotlarni text sifatida qo'shamiz", son1, son2)
print("Biz int va string turidagi ma'lumotlarni matematik amallar usulida qo'shamiz", son1+ son2)

```

    Biz int va string turidagi ma'lumotlarni text sifatida qo'shamiz 12 12
    


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[4], line 2
          1 print("Biz int va string turidagi ma'lumotlarni text sifatida qo'shamiz", num1, num2)
    ----> 2 print("Biz int va string turidagi ma'lumotlarni matematik amallar usulida qo'shamiz", num1+ num2)
    

    TypeError: unsupported operand type(s) for +: 'int' and 'str'


Ko'rib turganingizdek bizda xatolik sodir bo'ldi bunda aynan qanday xatolik ekaniga qarang TypeError bu degani malumot turlari mos kelmagani tufayli kodimizda xatolik

*int* bu faqat butun sonlar turi bunda agar variable ga kasrli ya'ni 10.9 yoki 1.5 kabi sonlarni avtomatik tarzda yaxlitlab ketadi sonlarni ya'ni quyidagi kabi va ularni ham o'zgaruvchida saqlash, ularning ustida turli amallar bajarish (+), (-), (*), (/) kabi [arifmetik amallar](https://docs.python.org/3/library/math.html) bu linkda matematik amallar va yana qo'shimcha ma'lumotlarni topish mumkin va barchasiz ingliz tilida berilgan 


```python
son=int(1.2)
print(son)
```

    1
    

Endi tepada yozgan kodimizga diqqat qiling bunda biz **int()** ni ishlatdik bu nima uchun kerak bo'ladi bu **typecasting** deyiladi ya'ni bir ma'lummot turini boshqasiga o'tkazish yoki ma'lumot turini qo'zgartirish bu bizga kelajakda juda qo'l keladigan va buni biz bilib qo'yishimiz kerak bo'lgan usul
endi variable ga tayyor ma'lumot bermaylik bu ma'lumotni foydalanuvchi kiritsin bu quyidagicha bo'ladi va biz bu ma'lumot ustida turli amallarni ham bajaramiz


```python
ism=input("Ismingizni kiriting :")
yosh=int(input("Yoshingizni kiriting :"))
print(f"Sizning ismingiz {ism} va sizning yoshingiz {yosh} da! ")
```

    Sizning ismingiz jurabek va sizning yoshingiz 31 da! 
    

Keling endi tepadagi chiqarilgan naitjalarimizni biroz chiroyli qilamiz va biroz yangilik kiritamiz.


```python
ism=input("ismingizni kiriting :")
yosh=int(input("Yoshingizni kiriting : "))
yil=int(input("Ayni vaqtda qaysi yil :"))
print(f"Sizning ismingiz {ism.title()} va sizning yoshingiz {yosh} da")
print(f"Hozirda {yil} ekanini hisobga olsak siz {yil-yosh}-yilda tug'ilgansiz.")

```

    Sizning ismingiz Jurabek va sizning yoshingiz 31 da
    Hozirda 2026 ekanini hisobga olsak siz 1995-yilda tug'gilgansiz.
    

Biz tepada f-string yordamida kodimizning natijasini ham tushunarli va print funksiyasini pir ishlatishda chiroyli qilib tayyorlab oldik endi keling **f-string** ga biroz e'tibor beramiz ya'ni uni yana qanday qo'llash mumkin.


```python
ism=input("Ismingizni kiriting :")
familiya=input("Familiyangizni kriting :")
sharif=input("Sharifingzni kiriting :")
print(f"Sizning ismingiz {ism.title()}")
print(f"Sizning familiyangiz {familiya.title()}")
print(f"Sizning sharifingiz {sharif.title()}")

```

    Sizning ismingiz Jurabek
    Sizning familiyangiz Sevinchov
    Sizning sharifingiz Mamusha
    

Endi biz tepada print funksiyasini uch marta qo'lladik endi bundan qulayroq usulni ko'raylik


```python
ism=input("Ismingizni kiriting :")
familiya=input("Familiyangizni kriting :")
sharif=input("Sharifingzni kiriting :")
print(f"Sizning ismingiz {ism.title()}\n"
    f"Sizning familiyangiz {familiya.title()}\n"
    f"Sizning sharifingiz {sharif.title()}")
```

    Sizning ismingiz Jurabek
    Sizning familiyangiz Sevinchov
    Sizning sharifingiz Mamusha
    

Demak biz tepedagi usulda ham f-string ni ishlatishimiz mumkin
endi keling biz **f-string** ning yana boshqa imkoniyatlarini ko'rib chiqaylik


```python
a=10
b=5
print(f"{a} + {b} = {a+b}")
```

    10 + 5 = 15
    


```python
b=100
print(f"{b} ning kvadrat ildizi {b**0.5} ga teng")
```

    100 ning kvadrat ildizi 10.0 ga teng
    


```python
ism="davron"
kasbi="dasturchi"
print(f"Sizning ismingiz {ism.upper()} va kasbingiz {kasbi.title()}")
```

    Sizning ismingiz DAVRON va kasbingiz Dasturchi
    


```python
pi=3.14159265
print(f"Pi soni taxminan :{pi}\n"
      f"yoki taxminan {pi:.2f} ga teng")
```

    Pi soni taxminan :3.14159265
    yoki taxminan 3.14 ga teng
    

Tepadagi kodga diqqat qiling bu bazan bizdan 1.234567890 kabi sonlarni o'nliklar yoki yuzliklar xonasigacha yaxlitlashda ishlatiladi


```python
maosh=15000000
print(f"Oylik maosh : {maosh:,} so'm")
```

    Oylik maosh : 15,000,000 so'm
    

Keling yana bir kichik foydali usullarni ko'raylik


```python
text="Men"
print(f"|{text:<10}|") # 10 ta joy ajratib, chapga qo'yadi
print(f"|{text:>10}|") # 10 ta joy ajratib, o'ngga qo'yadi
print(f"|{text:^10}|") # 10 ta joy ajratib, o'rtaga qo'yadi
```

    |Men       |
    |       Men|
    |   Men    |
    

*Foizlarni ko'rsatish*
Sonni $100$ ga ko'paytirib, oxiriga % belgisini qo'shib beradi:


```python
progress=0.756
print(f"Yutuq : {progress:.1%}")
```

    Yutuq : 75.6%
    

### Topshiriq

I. Integer va String farqi (5 ta savol)  
Natijani toping: x = 10 + 5 va y = "10" + "5". x va y ning farqi nimada?  

Ko'paytirish: belgi = "*" o'zgaruvchisi berilgan. Uni 20 marta ketma-ket chiqarish  uchun qanday kod yozish kerak? (Arifmetik amaldan foydalaning).  

Mantiqiy xato: a = "30" va b = "20". print(a - b) kodi nima uchun ishlamaydi?  

Turlarni aniqlash: z = 45.0 soni int mi yoki boshqa turmi? (Sizning faylingizdagi   
int(1.2) misolidan kelib chiqib o'ylang).  

Amallar ketma-ketligi: natija = "Salom" * 2 + "Hayr" * 2. Ekran qanday ko'rinishga   keladi?  

II. F-string: Matematika va Metodlar (5 ta savol)  
Hisoblash: a = 8 va b = 9. F-string ichida ularning ko'paytmasini: 8 * 9 = 72   ko'rinishida chiqaring.  

Kvadrat: son = 12 berilgan. F-string yordamida uning kvadratini (son**2) hisoblab   chiqaring.  

Upper metod: shahar = "toshkent". F-string ichida uni faqat katta harflar bilan   chiqaring.  

Title metod: ism = "ali valiyev". F-string yordamida ismni bosh harflar bilan ("Ali   Valiyev") ko'rsating.  

Aralash format: meva = "olma", narx = 5000. "Olma narxi 5000 so'm" degan gapni f-string   bilan yasang.  

III. F-string: Sonlarni formatlash (5 ta savol)  
Yaxlitlash (Yuzlar): pi = 3.14159 berilgan. Uni .2f orqali faqat 3.14 qilib chiqaring.  

Yaxlitlash (Butun): son = 99.999. Uni verguldan keyin raqamlarsiz, yaxlitlangan holda   chiqaring.  

Minglik ajratgich: masofa = 150000000. Quyoshgacha bo'lgan masofani 150,000,000   ko'rinishida (vergul bilan) chiqaring.  

Foiz (Percent): ulush = 0.5. F-string yordamida uni 50.0% ko'rinishida ko'rsating.  

Katta son va matn: foyda = 2500000. Uni 2,500,000.00 (ikki xona aniqlikda va vergul   bilan) ko'rinishida chiqaring.  

IV. F-string: Tekislash (Alignment) (5 ta savol)  
O'ngga surish: so'z = "Python". 15 ta katak ajratib, so'zni o'ng tomonga taqab chiqaring   (>).

Chapga surish: so'z = "Dasturchi". 20 ta katak ajratib, so'zni chap tomonga taqab   chiqaring (<).  

Markazlash: nom = "MENU". Uni 30 ta katakning o'rtasiga joylashtiring (^).  

To'ldirgich (Padding): id_raqam = 123. Uni 10 ta joy ajratib, bo'sh joylarni nol bilan   to'ldiring (0123 kabi emas, formatlash orqali).  

Murakkab jadvalcha: Ikki qatorda f-string ishlating:  

Birinchi qatorda "Ism" (chapda) va "Ball" (o'ngda) 20 ta masofada tursin.  

Ikkinchi qatorda "Asilbek" va "100" aynan o'sha tartibda tursin.  
