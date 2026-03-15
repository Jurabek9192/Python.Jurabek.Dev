#### List bilan tanishamiz
Esingizda bo'lsa biz o'zgarvchi yaratib unga ma'lumotlar yuklashni keyin foydalanuvchidan ham olib printda chiqarishni o'rgangan ediik endi biz bitta o'zgaruvchiga bir necha ma'lumotni yuklashni ular ustida turli amallar qilishni o'rganamiz.

Buning uchun biz yangi ma'lmot turi **list** *ro'yxat* bilan tanishib olishimiz kerak bo'ladi ya'ni nomidan ham aytib turibdi ro'yxatda ma'lumotlar ro'yxat shaklida bo'ladi. Ro'yxatning ishida esa uning **element**lari bo'ladi.
Ro'yxatda son, matn, yoki aralsh turdagi ma'lumotlar saqlanishi mumkin.

List quyidagicha bo'ladi.


```python
mevalar=['olma', 'nok', 'uzum', 'shaftoli', 'kivi', 'apelsin'] # Stringlar
narxlar=[20000, 23000, 15000, 13000, 15000, 24000] # Sonlar
sonlar=['bir', 'ikki', 3, 4, True] # Aralash
ismlar=[] # Bo'sh ro'yxat
```

Ro'yxat saqlaydigan o'zgaruvchilarni Ko'plik shakllarda nomlash tavsiya qilinadi ammo bu qoida emas

#### List elementlari
Ro'yxatdagi har bir elementning o'zining tartib raqami (index) bo'ladi va ularga shu index orqali murojaat qilamiz.

Dasturlash olamida indeks 0 dan boshlanadi! Ya'ni Listning birinchi elementing tartib raqami (indeksi) 0 ga, ikkinchi elementning indeksi 1 ga teng va hokazo.


```python
mevalar=['olma', 'nok', 'uzum', 'shaftoli', 'kivi', 'apelsin']
print(f"Birinchi meva : {mevalar[0]}")
print(f"Ikkinchi meva : {mevalar[1]}")
```

    Birinchi meva : olma
    Ikkinchi meva : nok
    

Agar list ichidagi elementlar string bo'lsa ularga [string metodlarini](https://www.w3schools.com/python/python_ref_string.asp) qo'llashimiz mumkin:



```python
universitetlar=['toshkent davlat texnika universiteti', 'toshkent axborot texnologiyalari universiteti',
                'samarqand pedagogika universitet']

print(universitetlar[0].title())
print(universitetlar[1].capitalize())
print(universitetlar[2].upper())
```

    Toshkent Davlat Texnika Universiteti
    Toshkent axborot texnologiyalari universiteti
    SAMARQAND PEDAGOGIKA UNIVERSITET
    

Elementlar ustida turli arifmetik amallar bajaramiz


```python
narxlar=[12_000, 15_000, 14000, 4_000 ]
print(narxlar[0]+narxlar[2])
```

    26000
    

Pythonda Listning eng oxirgi elementiga -1 indeksi orqali ham murojaat qilish mumkin. Bu usul Listning uzunligini bilmaganda yoki unutib qo'yganda juda qo'l kelganda.


```python
mashinalar=['Damas', 'Matiz', 'Nexia', 'Nexia 3', 'Tracker']
print(mashinalar[-1]) # -1 Bilan oxirgi mashinaga murojaat qilamiz.
```

    Tracker
    

#### Listga elementlarni qo'shish, o'chirish va almashtirish
Ro'yxatdagi biror elementning qaymatini o'zgartirish uchun, o'sha elementning indeksi bilan murojaat qilamiz va yangi qiymat yuklaymiz.


```python
narxlar=[12_000, 18000, 6000, 39999]
narxlar[-1]=40000
narxlar[2]=5000
narxlar[1]=narxlar[3] + 2000
narxlar[1]=narxlar[0]+narxlar[2]
print(narxlar)
```

    [12000, 17000, 5000, 40000]
    

#### Yangi element qo'shish
**.append() metodi**
Ro'yxatga yangi elemment qo'shishning oson usuli bu *.append()* metodi yordamida ro'xatga oxirgi qiymat qo'shish mumkin.


```python
mevalar=['olma', 'nok']
print(mevalar)
mevalar.append('tarvuz')
mevalar.append('uzum')
print(mevalar)
```

    ['olma', 'nok']
    ['olma', 'nok', 'tarvuz', 'uzum']
    

**.append()**  metodi bo'sh listni to'ldirishda juda qulay ayniqsa dastur boshida bo'sh ro'yxat yaratib olib keyin uni dastur davomida to'ldirib borish qulay


```python
tumanlar=[]
tumanlar.append('yakkabog\'')
tumanlar.append('g\'uzor')
tumanlar.append('qamashi')
tumanlar.append('chiroqchi')
print(tumanlar)
```

    ["yakkabog'", "g'uzor", 'qamashi', 'chiroqchi']
    

**.insert() metodi**
Ro'yxatning istalgan joyiga yangi element qo'shishda *.insert()* metodi ishlatiladi. .insert() metodining ichida yangi element indeksi va qiymati beriladi.


```python
mashinalar=['matiz', 'tico', 'jentra']
print(mashinalar)
mashinalar.insert(2, 'malibu')
print(mashinalar)
```

    ['matiz', 'tico', 'jentra']
    ['matiz', 'tico', 'malibu', 'jentra']
    

#### Elementni o'chirish
Ro'yxatdan elementni o'chirish uchun elementning indeksini yoki qiymatini bilishimiz kerak bo'ladi.

Indeks yordamida olib tashlash uchun **del** operatoridan foydalanamiz.


```python
mevalar=['olma', 'nok', 'tarvuz', 'uzum']
print(mevalar)
del mevalar[2]
print(mevalar)
```

    ['olma', 'nok', 'tarvuz', 'uzum']
    ['olma', 'nok', 'uzum']
    

Element qiymati bo'yicha o'chirish uchun esa **.remove()** metodidan foydalanamiz. Buning uchun qavs ichida o'chirib tashlsh kerak bo'lgan qiymat beriladi.


```python
mevalar=['nok', 'jiyda', 'olma', 'mandarin']
print(mevalar)
mevalar.remove('mandarin')
print(mevalar)
```

    ['nok', 'jiyda', 'olma', 'mandarin']
    ['nok', 'jiyda', 'olma']
    

!!! info ".remove(qiymat) metodi"
    Bu metod ro'yxatda uchragan birinchi mos keluvchi qiymatni o'chiradi.
    Agar ro'yxatda 2 ta bir xil element bo'lsa, birinchisi o'chadi.


```python
hayvonlar=['it', 'mushuk', 'sichqon', 'ot', 'ilon', 'mushuk']
print(hayvonlar)
hayvonlar.remove('mushuk')
print(hayvonlar)
```

    ['it', 'mushuk', 'sichqon', 'ot', 'ilon', 'mushuk']
    ['it', 'sichqon', 'ot', 'ilon', 'mushuk']
    

Elementni sug'gurib olish bu nima degani elemantni sug'urib olganingizda sizda qiymat qoladi xohlasangiz uni boshqa o'zgaruvchiga yoki listga yuklaysiz asosiy listda esa qolmaydi.


```python
bozorlik = ["yog'", 'un', 'piyoz', 'banan', "go'sht"]
mahsulot = bozorlik.pop(3) # Ro'yxatdan banan ni sug'urib olamiz
print("Men " + mahsulot + " sotib oldim")
print("Olinmagan mahsulotlar: ", bozorlik)
```

    Men banan sotib oldim
    Olinmagan mahsulotlar:  ["yog'", 'un', 'piyoz', "go'sht"]
    

#### Topshiriqlar
1. "Avtopark" mashqi
mashinalar degan ro'yxat yarating va unga 4 ta yoqtirgan avtomobilingiz nomini yozing. Har bir mashina nomini bosh harf bilan konsolga chiqaring (masalan: "Men Chevrolet Gentra haydagim keladi").

2. "Oila a'zolari" (Index bilan ishlash)
oila deb nomlangan ro'yxat tuzing. Ro'yxatdan foydalanib, oilangizning eng kichik va eng katta a'zosini konsolga chiqaruvchi kod yozing.

3. "Dars jadvali" (Elementni o'zgartirish)
fanlar degan ro'yxat yarating. Agar dars jadvalingiz o'zgargan bo'lsa, ro'yxatdagi 2-elementni o'chirib, o'rniga boshqa fan nomini yozing.

4. "Bozorlik" (Arifmetika va List)
narxlar degan ro'yxat yarating (masalan: [12000, 5000, 25000, 18000]). Eng qimmat va eng arzon mahsulotlarning narxini qo'shib, umumiy summani hisoblang.

5. "Kutubxona" (.append() va .insert())
kitoblar nomli bo'sh ro'yxat oching. .append() yordamida oxiriga 3 ta kitob, .insert() yordamida ro'yxat boshiga 1 ta sevimli kitobingizni qo'shing.

6. "Sportchilar" (.remove() va .pop())
sportchilar ro'yxatini tuzing. Jarohat olgan sportchini .remove() bilan o'chiring, faoliyatini yakunlagan sportchini esa .pop() yordamida sug'urib olib: "Ushbu sportchi nafaqaga chiqdi" deb xabar chiqaring.

7. "Shaharlar" (Slicing - Kesib olish)
O'zbekistonning 6 ta viloyati nomini o'z ichiga olgan viloyatlar ro'yxatini yarating. Undan faqat o'rtadagi 2 ta viloyatni ajratib olib, yangi ro'yxatga saqlang.

8. "O'quvchilar reytingi"
ballar degan ro'yxat yarating (masalan: [85, 90, 70, 100, 60]). Ro'yxatdagi eng past ballni topib, unga 5 ball "sovg'a" tariqasida qo'shing va ro'yxatni yangilang.

9. "Sayohat sumkasi" (Kombinatsiya)
sumka nomli ro'yxatga sayohat uchun kerakli 5 ta buyumni yozing. Agar sumkangizda joy qolmagan bo'lsa, bitta keraksiz buyumni o'chirib, o'rniga "Fotoapparat" qo'shing.

10. "Yutuqli o'yin"
ishtirokchilar va goliblar degan ikki ro'yxat tuzing. .pop() yordamida ishtirokchilar orasidan tasodifiy bittasini (yoki oxirgisini) olib, goliblar ro'yxatiga o'tkazing va "G'olib: [ism]" deb e'lon qiling.
