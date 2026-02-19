# String va unicode

**string** (matn) - Pythondagi eng mashxur ma'lumot turlaridan biri. Avvalgi darsda ko'rganimizdek, o'zgaruvchiga matn yuklash uchun matn qo'shtirnoq (" ") yoki birtirnoq (' ') ichida yozilishi kerak

*Python* da matnlar unicode jadvalining istalgan belgilari ishlatilishi mumkin
buni o'zingiz kirib ko'ring havoladan  [unicode](https://symbl.cc/) yoki **unicode** deb internetdan qidirsangiz chiqadi ko'rib olishingiz mumkin


```python
emoji="😀"
print(emoji)
telefon="Urra men 📱 oldim "
print(telefon)
```

    😀
    Urra men 📱 oldim 
    

*emoji*-shular kabi bo'ladi
![image.png](05_string_va_unicoda_files/image.png)

### String ustida amallar
#### Matnlar qo'shish
Matnlar + orqali amalga oshiriladi


```python
name="Javohir"
print("Mening ismim " + name)
# Vergul bilan ham chiqarish mumkin ammo vergulda
# doim bitta bo'sh joy bo'ladi
print("Mening ismim ", name)
# bo'sh joy qoldirilmasa ham qoladi
print("Mening ismim", name)
```

    Mening ismim Javohir
    Mening ismim  Javohir
    


```python
first_name="Davron"
last_name="Bekmatov"

# Bunda bo'sh joysiz chiqadi
print(first_name+last_name)

# Bunda bo'sh joy bilan chiqadi
print(first_name+" "+last_name)
```

    DavronBekmatov
    Davron Bekmatov
    

### f-string
Ikki va undan ortiq o'zgaruvchilar uchun juda qo'l keladi


```python
name='Azazmat'
familiya='Sarvarov'
print(f"Sizning ismingiz {name} va fammiliyangiz {familiya}")
```

    Sizning ismingiz Azazmat va fammiliyangiz Sarvarov
    

Bu usul ayniqsa uzun matnlar uchun kerakli


```python
name="Samandar"
lasat_name="Farhodov"
print(f"Mening ismim {name} familiyam {last_name} ya'ni {name} {last_name} man")
```

    Mening ismim Samandar familiyam Bekmatov ya'ni Samandar Bekmatov man
    

*Maxsus belgilar*
Matnga bo'dshliq qo'shish uchun \t yani yani tab tugmasining bo'shliq joyi uchun, yangi qatorga tushirish uchun \n belgisidan foydalaniladi.


```python
print("Hello World!")
print("Hello \tWorld!")
print("Hello \nWorld!")
```

    Hello World!
    Hello 	World!
    Hello 
    World!
    

### String va metodlar
Pythonda string ustida amalga oshirish mumkin bo'lgan tayyor amallar to'plami mavjud. Bunday amallar to'plami **metodlar** deb ataladi. 

Metodlarni qo'llash uchun metod nomi matndan so'ng **.metod_nomi()** kabi yoziladi


```python
name="Javlon"
last_name="Mavlonov"
full_name=f"{name} {last_name}"
print("Oradagi farqlarni ilg'ashga harakat qiling.")
print(full_name.upper())
print(full_name.lower())
print(full_name.title())
print(full_name.capitalize())
```

    Oradagi farqlarni ilg'ashga harakat qiling.
    JAVLON MAVLONOV
    javlon mavlonov
    Javlon Mavlonov
    Javlon mavlonov
    

*strip(), rstrip() va lstrip() metodlari*
Bu metodlar matnning boshi va oxiridagi bo'sh joylarni olib tashlaydi


lstrip() — matn boshidagi bo'shliqni,

rstrip() – matn oxiridagi bo'shliqni,

strip() — matn boshi va oxiridagi bo'shliqlarni olib tashlaydi


```python
fruit="        olma        "
print(fruit)
print(fruit.strip())
print(fruit.lstrip())
print(fruit.rstrip())
meva = "     olma     "
print("Men " + meva.lstrip() + " yaxshi ko'raman")
print("Men " + meva.rstrip() + " yaxshi ko'raman")
print("Men " + meva.strip() + " yaxshi ko'raman")
print("Men " + meva + " yaxshi ko'raman")
```

            olma        
    olma
    olma        
            olma
    Men olma      yaxshi ko'raman
    Men      olma yaxshi ko'raman
    Men olma yaxshi ko'raman
    Men      olma      yaxshi ko'raman
    

#### Input foydalanuvhi bilan munloqot
Input bizga foydalanuvchidan ma'lumot olish imkoninin beradi 


```python
name=input("Please enter your name:")
print("Hello ", name)
```

    Hello  jurabek
    

Keling endi biroz chiroyliroq ilamiz buni 


```python
name=input("Enter your name:\n>>>")
print("Hello ", name.title())
```

    Hello  Jurabek
    

**Topshiriqlar**
🚗 Variant 1: Avtomobil ma'lumotlari (Mashq)
O'zgaruvchilar yaratish:
Quyidagi o'zgaruvchilarni yarating va qiymat bering:

model="Chevrolet"

rang="Oq"

yil="2023"

narx="12000"

Konsolga chiqarish:
Ushbu o'zgaruvchilarni jamlab, quyidagi ko'rinishda chiqaring:
Chevrolet avtomobili, Rangi oq, 2023-yilda ishlab chiqarilgan, Narxi 12000 dollarni tashkil etadi.

Foydalanuvchi kiritishi:
Yuqoridagi 4 ta ma'lumotni foydalanuvchidan input() orqali so'rang va natijani ekranga chiqaring.

Yangi qatorlar:
Natijani chiqarishda har bir verguldan keyin \n yordamida yangi qatorga o'tkazing.

Metodlar bilan ishlash:
Barcha ma'lumotlarni f-string orqali avto_info degan o'zgaruvchiga yuklang va unga .upper(), .lower(), .title() va .capitalize() metodlarini qo'llab ko'ring.

🎓 Variant 2: Talaba anketasi (Mashq)
Ma'lumotlar:
O'zingiz haqingizda (yoki ixtiyoriy shaxs) quyidagi o'zgaruvchilarni yarating:

ism, familiya, yosh, universitet.

Matn shakllantirish:
f-string yordamida quyidagicha gap yasang:
Salom, mening ismim Ism Familiya. Yoshim 20 da. Men Universitet talabasiman.

String manipulyatsiyasi:
Foydalanuvchi ismini kichik harf bilan kiritsa ham, ekranga chiqarayotganda .title() metodi orqali har doim bosh harf bilan chiqadigan qiling.

📦 Variant 3: Maxsus belgi va Formatlash (Qiyinroq)
O'zgaruvchilar:
shahar, davlat, aholi_soni o'zgaruvchilarini yarating.

Belgilar bilan ishlash:
Quyidagi ko'rinishni hosil qiling (bunda \t — tabulyatsiya/bo'sh joydan foydalaning):

Plaintext

Davlat: O'zbekiston
    Shahar: Toshkent
    Aholi: 3 million
Tozalash (strip):
Foydalanuvchidan biror so'z so'rang va u so'zning boshidagi va oxiridagi bo'sh joylarni .strip() metodi bilan olib tashlab, keyin uzunligini (len()) o'lchang.
