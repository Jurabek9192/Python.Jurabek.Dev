# for BILAN TANISHAMIZ

Dasturlash davomida kodimizning bir qismini bir necha marta takrorlanishi talab etilishi mumkin. Misol uchun, ro'yxat ichidagi har bir elementni alohida konsolga chiqarish, yoki bo'lmasa har bir elemntni kvadratga oshirish va hokazo.


Bunday vaziyatlarda bizga **for** yordam beradi bu **tsikl (loop)** deyiladi.

Buni quyiagi misolda yanada yaxshiroq anglashimiz mumkin bo'lasdi.
Deylik bizda maxsulotlar ro'yxati bor va biz bu ro'yxati ro'yxat sifatida.


```python
mahsulotlar=['olma', 'banan', 'uzum', 'shaftoli', 'nok', 'qulupnay', 'olcha', 'gilos']
print(mahsulotlar)
```

    ['olma', 'banan', 'uzum', 'shaftoli', 'nok', 'qulupnay', 'olcha', 'gilos']
    

Va har birini alohida tartiblangan usulda ko'raylik


```python
mahsulotlar=['olma', 'banan', 'uzum', 'shaftoli', 'nok', 'qulupnay', 'olcha', 'gilos']
for mahsulot in mahsulotlar:
    print(mahsulot.title())
```

    Olma
    Banan
    Uzum
    Shaftoli
    Nok
    Qulupnay
    Olcha
    Gilos
    

Keling endi yozgan kodimizni biroz tahlil qilamiz bunda biz 1-kodda shunchaki har bir mevani bitta list sifatda ko'ra oldik xolos unga alohida murojaat qilishimiz uchun har biriga alohida kod yoshimiz kerak bo'lardi ya'ni print(ahsulotlar[0]) va hokazo.

Endi esa 2-kodimizni tahlil qilsak bunda biz biroz boshqacha yondoshdik xolos ya'ni **for tsikli** bilan bunda biz 1-qatorda list ya'ni ro'yxatni shakllantirib oldik va 2-qatorda unga for orqali buyurdik ya'ni mahsulotlatning ichidagi har bir elementni alohida chaqirib print() qildik bunda har bir element alohida chiqib keldi.

"For" so'zi ingliz tilidan "uchun" deb tarjima qilinadi.

Endi yana bir bor yozgan kodimizni tarjima qilamiz bunda quyidagicha bo'ladi
"Mahsulotlar ro'yxatidagi har bir mahsulot uchun uning qiymatini console ga chiqar.

# for QANDAY ISHLAYDI


Keling yana bir necha misollar ko'raylik.


```python
mahsulotlar=['olma', 'banan', 'uzum', 'shaftoli', 'nok', 'qulupnay', 'olcha', 'gilos']
for mahsulot in mahsulotlar:
    print(f"Men bugun bozorda uyga {mahsulot} sotib olishim kerak.")
```

    Men bugun bozorda uyga olma sotib olishim kerak.
    Men bugun bozorda uyga banan sotib olishim kerak.
    Men bugun bozorda uyga uzum sotib olishim kerak.
    Men bugun bozorda uyga shaftoli sotib olishim kerak.
    Men bugun bozorda uyga nok sotib olishim kerak.
    Men bugun bozorda uyga qulupnay sotib olishim kerak.
    Men bugun bozorda uyga olcha sotib olishim kerak.
    Men bugun bozorda uyga gilos sotib olishim kerak.
    


```python
mashinalar=['cobalt', 'tico', 'nexia', 'matiz', 'gentra', 'lacetti']
for mashina in mashinalar : 
    print(f"O'zbekiston gm mashina zavodi shu paytgacha {mashina} kabi mashinalar chiqargan.")
```

    O'zbekiston gm mashina zavodi shu paytgacha cobalt kabi mashinalar chiqargan.
    O'zbekiston gm mashina zavodi shu paytgacha tico kabi mashinalar chiqargan.
    O'zbekiston gm mashina zavodi shu paytgacha nexia kabi mashinalar chiqargan.
    O'zbekiston gm mashina zavodi shu paytgacha matiz kabi mashinalar chiqargan.
    O'zbekiston gm mashina zavodi shu paytgacha gentra kabi mashinalar chiqargan.
    O'zbekiston gm mashina zavodi shu paytgacha lacetti kabi mashinalar chiqargan.
    


```python
sniflar=[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
for snif in sniflar:
    print(f"Bizning maktabda {snif}-snif o'quvchilari bor.")
```

    Bizning maktabda 1-snif o'quvchilari bor.
    Bizning maktabda 2-snif o'quvchilari bor.
    Bizning maktabda 3-snif o'quvchilari bor.
    Bizning maktabda 4-snif o'quvchilari bor.
    Bizning maktabda 5-snif o'quvchilari bor.
    Bizning maktabda 6-snif o'quvchilari bor.
    Bizning maktabda 7-snif o'quvchilari bor.
    Bizning maktabda 8-snif o'quvchilari bor.
    Bizning maktabda 9-snif o'quvchilari bor.
    Bizning maktabda 10-snif o'quvchilari bor.
    Bizning maktabda 11-snif o'quvchilari bor.
    

Va bu kabi misollarni ko'plab keltirish mumkin bunda for tsiklning boshi (:) esa tsiklning boshanishing yakunni keyingi qator esa tsiklning badani deyiladi.

Tsikl badani surilish (indentation) bilan ajratiladi, ya'ni tsiklning takrorlanuvchi qismi asosiy koddan bir muncha o'ngroqqa surilgan bo'ladi. Agar biz mana shu surilishni tark qilsak kodimiz xato beradi:


```python
bolalar=['ali', 'vali', 'lola', 'laylo', 'anvar']
for bola in bolalar:
print(f"Salom bolakay {bola.title()}")
```


      Cell In[8], line 3
        print(f"Salom bolakay {bola.title()}")
        ^
    IndentationError: expected an indented block after 'for' statement on line 2
    


Ko'rib turganingizdek bu yerda xatolik berdi ya'ni **IndentationError:** surilish bilan bog'liq xatolik.

Shunigdek, ko'pchilik yo'l qo'yadigan yana bir xato, qo'shimcha qatorlarni surish esdan chiqishi:


```python
mehmonlar = ['Ali','Vali','Hasan', 'Husan','Olim']
for mehmon in mehmonlar:
    print(f"Hurmatli {mehmon}, sizni 20 Dekabr kuni nahorga oshga taklif qilamiz")
print("Hurmat bilan, Palonchiyevlar oilasi\n")
```

    Hurmatli Ali, sizni 20 Dekabr kuni nahorga oshga taklif qilamiz
    Hurmatli Vali, sizni 20 Dekabr kuni nahorga oshga taklif qilamiz
    Hurmatli Hasan, sizni 20 Dekabr kuni nahorga oshga taklif qilamiz
    Hurmatli Husan, sizni 20 Dekabr kuni nahorga oshga taklif qilamiz
    Hurmatli Olim, sizni 20 Dekabr kuni nahorga oshga taklif qilamiz
    Hurmat bilan, Palonchiyevlar oilasi
    
    

Yuqoridagi kodimizda 4-qatorni o'ngga surmaganimiz uchun, Python bu qatorni tsikl tashqarisida deb qabul qildi va faqatgina 1 marta, tsikl tugaganidan so'ng bajardi.

Huddi shu kabi agar takrorlanishi kerak bo'magan kodni tsikldan so'ng o'ngga surib qo'ysak Python bu qatorni tsiklning tarkibida deb hisoblab, qayta-qayta bajaradi:


```python
mehmonlar = ['Ali','Vali','Hasan', 'Husan','Olim']
for mehmon in mehmonlar:
    print(mehmon)
    
    print(mehmonlar) # bu qator tsikl tashqarisida bo'lishi kerak edi
```

    Ali
    ['Ali', 'Vali', 'Hasan', 'Husan', 'Olim']
    Vali
    ['Ali', 'Vali', 'Hasan', 'Husan', 'Olim']
    Hasan
    ['Ali', 'Vali', 'Hasan', 'Husan', 'Olim']
    Husan
    ['Ali', 'Vali', 'Hasan', 'Husan', 'Olim']
    Olim
    ['Ali', 'Vali', 'Hasan', 'Husan', 'Olim']
    

Yuqoridagi kodda 5-qator surib qolingani uchun buni ham for tsiklining ishidagi kod deb qabul qildi Python va uni ham bajarib qo'ydi.


```python
mehmonlar = ['Ali','Vali','Hasan', 'Husan','Olim']
for mehmon in mehmonlar:
    print(mehmon)
    
print(mehmonlar)
```

    Ali
    Vali
    Hasan
    Husan
    Olim
    ['Ali', 'Vali', 'Hasan', 'Husan', 'Olim']
    

#### for YORDAMIDA SONLAR RO'YXATLAR BILAN ISHLASH

Keling quyidagi misolni ko'ramiz


```python
sonlar=list(range(1, 21))
for son in sonlar:
    print(f'{son} sonining kvadrati {son**2} ga teng.')
```

    1 sonining kvadrati 1 ga teng.
    2 sonining kvadrati 4 ga teng.
    3 sonining kvadrati 9 ga teng.
    4 sonining kvadrati 16 ga teng.
    5 sonining kvadrati 25 ga teng.
    6 sonining kvadrati 36 ga teng.
    7 sonining kvadrati 49 ga teng.
    8 sonining kvadrati 64 ga teng.
    9 sonining kvadrati 81 ga teng.
    10 sonining kvadrati 100 ga teng.
    11 sonining kvadrati 121 ga teng.
    12 sonining kvadrati 144 ga teng.
    13 sonining kvadrati 169 ga teng.
    14 sonining kvadrati 196 ga teng.
    15 sonining kvadrati 225 ga teng.
    16 sonining kvadrati 256 ga teng.
    17 sonining kvadrati 289 ga teng.
    18 sonining kvadrati 324 ga teng.
    19 sonining kvadrati 361 ga teng.
    20 sonining kvadrati 400 ga teng.
    

for yordamida yangi ro'yxat ham shakllantirish mumkin.


```python
sonlar=list(range(1, 21))
sonlar_kvadratlari=[]
for son in sonlar:
    sonlar_kvadratlari.append(son**2)

print(sonlar)
print(sonlar_kvadratlari)
```

    [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20]
    [1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400]
    

#### for VA input()

for operatori va input() funksiyasinin jamlab, ro'yxatni foydalanuvchidan olinadigan qiymatla bilan to'ldirish mumkin.


```python
mashinalar=[]
print("Siz yoqtirgan 5-ta mashinani o'ylang.")
for n in range(5):
    mashinalar.append(input(f"{n+1} - mashinaning nomini kiriting :"))

print(mashinalar)
```

    Siz yoqtirgan 5-ta mashinani o'ylang.
    ['sdfg', 'asdfgh', 'asdfgh', 'asdfghj', 'zxcvgh]']
    

Kodni tahlil qilamiz:  

1-qatorda bo'sh mashinalar ro'yxatini yaratdik  

2-qatorda ekranga "Siz yoqtirgan 5-ta mashinani o'ylang." degan xabarni chiqardik

3-qatorda tsiklni boshladik. range(5) funktsiyasi 0 dan 5 gacha sonlar ketma-ketligini yaratadi (0,1,2,3,4) tsikl esa n shularning har biriga teng bo'lib chiqquncha davom etadi. 

4-qatorda tsikl badani kelgan. Bu yerda biz foydalanuvchidan n+1 mashinani kiriting deb so'radik. Nima uchun n+1 (n emas)? Sababi n 0 dan 4 gacha qiymatlarni oladi, foydalanuvchiga tushunarli bo'lishi uchun esa biz "0-mashina nomini kiriting" deb emas, balki n+1 ya'ni 1-ismni kiriting deb murojat qilyapmiz.

5-qatorda shakllangan ro'yxatni konsolga chiqardik.

for tsikli har qanday dasturlash tilining eng muhim qismlaridan hisoblanadi va biz bu operatoraga hali takror-takror qaytamiz.

#### TOPSHIRIQ

Kamida 5 ta elementdan iborat ismlar degan ro'yxat tuzing va for yordamida har bir ismga salom bering.

10 dan 100 gacha bo'lgan toq sonlar ro'yxatini tuzing va ularning kubini alohida qatorlarda chiqaring.

Foydalanuvchidan 5 ta sevimli kinolarini kiritishni so'rang va ularni kinolar ro'yxatiga saqlang, so'ng konsolga chiqaring.

range() yordamida 10 dan 50 gacha bo'lgan juft sonlar yig'indisini hisoblaydigan kod yozing.

1 dan 20 gacha bo'lgan sonlar ro'yxatini yarating va ularning har birining kvadratini ekranga chiqaring.

Ro'yxatdagi barcha so'zlarning birinchi harfini katta qilib chiqaruvchi sikl yozing.

range(1, 12) yordamida yil oylarining tartib raqamlarini chiqaring.

0 dan 100 gacha bo'lgan sonlar ichidan 7 ga qoldiqsiz bo'linadiganlarini ekranga chiqaring.

Foydalanuvchidan bugun nechta odam bilan uchrashganini so'rang va har birining ismini ro'yxatga qo'shib boring.

Berilgan sonlar ro'yxatidagi musbat va manfiy sonlar sonini alohida hisoblovchi sikl tuzing.

"Python zo'r til" jumlasidagi har bir harfni alohida qatorda chiqaruvchi for sikli yozing.

1 dan 10 gacha bo'lgan sonlarning ko'paytirish jadvalini (faqat bitta son uchun, masalan 5 uchun) chiqaring.

Ro'yxatdagi sonlarning o'rta arifmetigini for sikli yordamida toping.

Berilgan ro'yxat ichidagi eng katta sonni for sikli yordamida toping (max funksiyasiz).

Foydalanuvchi kiritgan sonning faktorialini hisoblaydigan dastur tuzing.

for yordamida ekranga "Yulduzcha"lardan (*) uchburchak shaklini yasang.

Ro'yxatdagi faqat uzunligi 5 dan katta bo'lgan so'zlarni ekranga chiqaring.

100 dan 1 gacha bo'lgan sonlarni kamayish tartibida chiqaruvchi range siklini yozing.

Ikkita bir xil uzunlikdagi ro'yxat elementlarini mos ravishda qo'shib yangi ro'yxat hosil qiling.

"To'xtatish" so'zi kiritilmaguncha elementlarni ro'yxatga qo'shuvchi sikl (for va if birga) haqida o'ylang.
