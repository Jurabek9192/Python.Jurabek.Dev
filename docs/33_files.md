# FAYLLAR BILAN ISHLASH
Fayl bilan ishlashni o'rganamiz

#### KIRISH
Ushbu bo'limda katta hajmdagi ma'lumotlarni fayldan yuklab olish va dastur yakunida kerakli ma'lumotlarni va dastur natijasini faylga saqlashni o'rganamiz. Fayllar bilan ishlash dastur foydalanuvchilariga ham dasturga o'zlari istagan ma'lumotlarni yuklash imkoniyatini beradi.

#### FAYLDAN O'QISH
Kompyuterimizda aksar ma'lumotlar fayl ko'rinishida saqlanadi. Bu xoh matn bo'lsin, xoh jadval, xoh rasm, xoh video. Fayllarda turli ma'lumotlar saqlanishi mumkin, ob-havo ma'lumotlari, yillik hisobotlar, mijozlarning telefon raqamlari, talabalarning baholari va hokazo. 

Ko'pgina holatlarda dastur davomida katta ma'lumotlarni aynan fayllardan o'qib olish talab qilinadi. Ayniqsa, tahliliy dasturlarda fayl ko'rinishida saqlangan, katta hajmdagi jadvallar bilan ishlash tabiiy. Lekin fayllar bilan ishlash boshqa holatlarda ham ko'p asqotadi, misol uchun oddiy matnni html ko'rinishga o'tkazishni avtomatlashtiruvchi dastur yozishda.

Fayllar bilan ishlashning birinchi qadami bu fayldagi ma'lumotlarni kompyuter xotirasiga ko'chirish. Buning bir necha usuli bor, quyida ular bilan tanishamiz.

#### FAYLNI TO'LIQLIGACHA O'QISH
Boshlanishiga bizga fayl kerak. Keling, yangi pi.txt faylini yaratamiz, va ichiga quyidagi matnni joylaymiz:


```python
3.1415926535
8979323846
2643383279
```

Uch qatordan iborat faylimiz 
π
π sonining qiymatini saqlaydi (30 xona aniqlik bilan).

Fayli to'lqi o'qish uchun quyidagi kodni yozamiz:


```python
with open('pi.txt') as fayl:
    pi = fayl.read()
```

Kodni tahlil qilamiz:

* Birinchi qatorda open() funksiyasi yordamida faylni ochayapmiz. Bunda funksiyaga argument sifatida fayl nomini berayapmiz. Bu yerda biz ochayotgan fayl va dasturimiz bir papkada bo'lishi muhim.

* open() funksiyasi faylni obyekt sifatida qaytaradi, as operatori yordamida esa biz obyektimizga fayl deb nom berayapmiz. 

* Ikkinchi qatorda .read() metodi yordamida fayl obyektining tarkibidan bizga kerakli matnni olib, yangi, PI o'zgaruvchisiga yuklayabmiz.

* with operatorining vazifasi biz fayl bilan ishlab bo'lganimizdan so'ng faylni yopish. Yuqoridagi misolda, 2-qatordan so'ng Python zudlik bilan faylni yopadi.

Yuqorida ko'rgan usulimiz fayl bilan ishlashning eng xavfsiz usuli. Aslida biz fayllarni to'g'ridan-to'g'ri fayl=open('pi.txt') yordamida ochishimiz, fayl bilan ishlab bo'lgandan so'ng esa fayl.close() komandasi yordamida faylni yopishimiz ham mumkin edi:


```python
fayl = open('pi.txt')
PI = fayl.read()
print(pi)
fayl.close()
```

Lekin, bu usul xavfli hisoblanadi va tavsiya qilinmaydi. Gap shundaki, open() funksiyasi yordamida faylni ochganimizdan keyin, toki close() metodini chaqirgunga qadar faylimiz ochiq holatda turadi. Agar, faylni vaqtida yopmasak, yoki fayl yopilmasidan avval dasturimiz to'xtab qolsa fayl tarkibiga ziyon yetishi, ma'lumotlar yo'qotilishi mumkin. Misol uchun, boshqa dasturlarda ham (masalan Microsoft Word) faylni yopmasdan oldin kompyuteringiz o'chib qolsa, yoki dastur behosdan yopilib ketsa faylingizga ziyon yetkani kabi.

Shuning uchun open() funksiyasiga with orqali murojat qilganimizda, faylimiz with blokining oxirigacha ochiq turadi, va with tugashi bilan, fayl ham yopiladi. Demak fayl ustidagi amallarni biz with bloki ichida bajarib olishimiz kerak.

Keling endi pi ning qiymatini konsilga chiqaramiz:


```python
>>> print(pi)
3.1415926535
8979323846
2643383279
```

Matn faylda qanday saqlangan bo'lsa, huddi shu ko'rinishda konsolga chiqdi. Saqlangan ma'lumot son bo'lsada, fayldan o'qiganimizda qaytgan qiymat matn ko'rinishida bo'ladi. Matnni songa o'tkazish uchun, unga biroz ishlov beramiz:


```python
pi = pi.rstrip() # qator ohiridagi bo'shliqlarni olib tashlaymiz
pi = pi.replace('\n','') # qator tashlash belgisini almashtiramiz
pi = float(pi) # matnni float (o'nlik) songa o'tkazamiz
print(pi)
```

.replace() metodi matn tarkibidagi biror harf yoki belgini boshqa harf yoki belgi bilan almashtirish uchun ishlatiladi.

#### PAPKA ICHIDAGI FAYLLARNI OCHISH
Agar siz ochayotgan fayl dasturimiz bilan bir papkada emas, shu papka ichidagi papkada joylashgan boʻlsa, fayl nomidan avval papka nomi yoziladi:


```python
with open('data/pi.txt') as fayl:
    pi = fayl.read()
```

Agar papkalar bir necha qavat boʻlsa, fayl nomini va ungacha boʻlgan papkalarni alohida yozib olgan afzal:


```python
faylnomi = 'data/math/numbers/pi.txt'
with open(faylnomi) as fayl:
    pi = fayl.read()
```

Windowsda papkalar orasida "\" belgisi ishlatilsada, Pythonda "/" belgisini ishlataveramiz. Agar \ belgisini ishlatishni istasangiz, bu belgini 2 marta yozing: C:\\python\\darslar\\data

#### FAYLNI QATORMA-QATOR OʻQISH
Baʻzida faylni toʻliqligicha emas, qatorma-qator oʻqish talab qilinishi mumkin. Masalan, faylda talabalrning ismi yoki kundalik ob-havo maʻlumotlari saqlangdanda va hokazo. Bunday hollarda for tsiklidan foydalanamiz:


```python
filename = 'data/talabalar.txt'
with open(filename) as file:
    for line in file:
        print(line)
```

Qatorlarni ro'yxat ko'rinishida saqlab olish uchun, .readlines() metodidan foydalanamiz.


```python
with open(filename) as file:
    talabalar = file.readlines()

print(talabalar)
```

E'tibor bering, har bir talaba ismidan so'ng qator tashlah belgisi (\n) tushib qolgan. Biz bu belgilarni .rstrip() metodi yordamida olib tashlashimiz mumkin:

#### FAYLGA YOZISH
Ma'lumotlarni saqlashning eng qulay usuli bu faylga yozish. Dasturimiz bajarilishdan to'xtaganidan so'ng, xotiradagi ma'lumotlar o'chib ketishi mumkin, lekin faylga yozilgan ma'lumotlar saqlanib turaveradi. Fayllarni kelajakda qaytdan xotiraga yuklab, dasturimizni to'htagan joyidan davom etishimiz mumkin. 

Yuqorida biz faylni ochishda open() funksiyasidan foydalandik, va yagona argument sifatida fayl nomini berdik. Bunda fayl faqatgina o'qish uchun ochiladi, unga yozib bo'lmaydi. Faylga ma'lumot yozish uchun open() funksiyasiga murojat qilishda fayl nomidan tashqari yana bir argument beramiz. Ikkinchi argument faylni aynan nima maqsadda ochishimizni bildiradi. Argumentlar quyidagilardan iborat bo'lishi mumkin:

![image.png](33_files_files/image.png)

#### YANGI FAYLGA YOZISH
Yangi faylga ma'lumot yozish uchun open() funksiyasini chaqirishda 'w' (write) argumentidan foydalanamiz. Ochilgan faylga ma'lumot qo'shish uchun esa .write() metodini chaqiramiz.


```python
faylnomi = 'ustozlar.txt'# ochilayotgan (yaratilayotgan) fayl nomi
with open(faylnomi,'w') as fayl:
    fayl.write('anvar narzullaev') # faylga yozilayotgan ma'lumot
```

Diqqat!!! open() funksiyasini 'w' argumenti bilan chaqirganimizda ehtiyot bo'lishimiz kerak, sababi agar bunday fayl mavjud bo'lsa, uning ichidagi barcha ma'lumotlar o'chib ketadi. 

Faylga yozayotgan ma'lumotlarimiz matn ko'rinishida bo'lishi kerak. Aks holda dasturimiz xato beradi.


```python
faylnomi = 'new_file.txt'
ism = 'Olimjon Hasanov'
tyil = 2004
with open(faylnomi,'w') as fayl:
    fayl.write(ism)
    fayl.write(tyil)
```

Xatoning oldini olish uchun sonlarni avval str() funksiyasi yordamida matnga keltirib olamiz.


```python
faylnomi = 'new_file.txt'
ism = 'Olimjon Hasanov'
tyil = 2004
with open(faylnomi,'w') as fayl:
    fayl.write(ism)
    fayl.write(str(tyil))
```

Fayllar matn formatida yoziladi, va biz ularni istalgan matn muharriri yordamida ochib ko'rishimiz mumkin.

Afsuski, faylga bir nechta ma'lumot yozganimizda, ma'lumotlar alohida qatordan emas, bir qatorda bir-biriga qo'shib qo'shib yoziladi. 

Buning oldini olishimiz uchun matn so'ngida \n belgisini qo'shib ketishimiz kerak bo'ladi:


```python
faylnomi = 'new_file.txt'
ism = 'Olimjon Hasanov'
tyil = 2004
with open(faylnomi,'w') as fayl:
    fayl.write(ism+'\n')
    fayl.write(str(tyil)+'\n')
```

#### FAYLGA MA'LUMOT QO'SHISH
Agar mavjud faylga ma'lumot qo'shish talab qilinsa, open() funksiyasiga murojat qilishda  'a' (append) argumentidan foydalanamiz. Bunda yangi qo'shilgan ma'lumotlar faylning oxiriga qo'shiladi. 


```python
with open(faylnomi,'a') as fayl:
    fayl.write('Alijon Valiyev\n')
    fayl.write('2000')
```

Agar biz ochayotgan fayl mavjud bo'lmasa, Python yangi fayl yaratadi.

#### O'ZGARUVCHILARNI FAYLDA SAQLASH
Yuqorida biz ma'lumotlarni matn ko'rinishida saqlashni ko'rdik. Agar dastur davomida turli o'zgaruvchilarni faylda saqlash talab qilinsa pickle modulidan foydalanamiz. Pickle ma'lumotlarni biz qanday ko'rinishda bersak, shunday ko'rinishda faylga yozadi. Yuqoridagi usuldan farqli ravishda, pickle yordamida yozilgan fayllarning tarkibini Pythondan tashqarida ko'rib bo'lmaydi. 

#### PICKLE FAYLGA YOZISH
Pickle dan foydalanish uchun biz avval bu modilni import qilamiz. Faylno ochishda esa, open() funksiyasiga ikkinchi argument sifatida 'wb' (write binary) beramiz, ya'ni ikkilik sanoq tizimida yozishni ko'rsatamiz. Faylga yozish uchun esa pickle.dump() metodidan foydalanamiz:


```python
import pickle

talaba1 = {'ism':'hasan', 'familiya':'husanov', 'tyil':2003, 'kurs': 2}
talaba2 = {'ism':'alijon', 'familiya':'valiyev', 'tyil':2004, 'kurs': 1}

with open('info','wb') as file:
    pickle.dump(talaba1,file)
    pickle.dump(talaba2,file)
```

E'tibor bering, yuqorida fayl nomini yozishda uning turini ko'rsatmadik, sababi, avval aytganimizdek bu fayllar Pythondan tashqarida ochilmaydi va biz buning oldini olishimiz kerak. Aslida fayl nomiga .txt qo'shimchasini ham qo'shishimiz mumkin, bu bilan dastur xato ishlamaydi, lekin bu bizni kelajakda chalg'itishi mumkin. Istasangiz faylga .dat (data so'zidan olingan) qo'shimchasini qo'shib qo'yishingiz mumkin (info.dat).

#### PICKLE FAYLDAN O'QISH
Pickle fayldan o'qish uchun open() funksiyasini 'rb' (read binary) argumenti bilan chaqiramiz. O'zgaruvchilarni bitta faylga yozganimizda, har bir o'zgaruvchi alohida qatordan yoziladi. Fayldan o'qishda ham har bir qatorni alohida o'qishimiz kerak bo'ladi:


```python
with open('info','rb') as file:
    talaba1 = pickle.load(file)
    talaba2 = pickle.load(file)
```

O'zgaruvchilar tarkibini ko'ramiz:


```python
print(talaba1)
```


```python
print(talaba1)
```

Adashib ketmaslik uchun, alohida o'zgaruvchilarni alohida fayllarga saqlash tavsiya qilinadi.
