# O'zgaruvchilar

**O'zgaruvchi**-kompyuter xotirasida ma'lum bir qiymatni saqlash uchun ajratilgan joy. Soddaroq qilib tushuntirsak, o'zgaruvchini quti, quti ichidagi narsani esa qiymat deb tasavvur qilish mumkin. Pythonda qiymatlar son, matn, ro'yxat va hokazo ko'rinishida bo'lishi mumkin.

![image.jpg](../.gitbook/assets/image.jpg)

Bular a'lumot turlari va ularning xotiradan egallaydigan joylari ham turli bo'ladi.\
Quyida ma'lumot turlarining umumiy xotiradan oladigan joylari haqida gaplashamiz.\
Ma'lumot turi,Hajmi (Bayt),Izoh\
**int** (0),24 - 28 bayt,Son kattalashgan sari hajm ortadi (chegara yo'q).\
**float**,24 bayt,O'nlik kasr sonlar uchun standart hajm.\
**bool**,24 - 28 bayt,True yoki False (aslida 1 va 0 integerlari). **str** (matn),49 - 50 bayt,+1 bayt [(ASCII)](https://www.ascii-code.com/) yoki +2/4 [(Unicode)](https://home.unicode.org/).

Ma'lumot turi,Boshlang'ich (bo'sh),Har bir qo'shimcha element uchun

_list_ (ro'yxat),56 bayt,+8 bayt (har bir element manzili uchun).\
_tuple_,40 bayt,+8 bayt (o'zgarmas bo'lgani uchun listdan kichik).\
_set_ (to'plam),216 bayt,Xesh-jadval ishlatgani uchun katta joy oladi.\
_dict_ (lug'at),232 bayt,Eng ko'p xotira talab qiladigan tur.\
_noneType_,16 bayt,Bo'sh qiymat (None).\
_complex_,32 bayt,Kompleks sonlar (a+bj).

```python
print("Assalamu alekum")
```

```
Assalamu alekum
```

```python
name="Abdulloh"
age=25
print(name)
print(age)
```

```
Abdulloh
25
```

**O'zgaruvchi-variable** - bunday deyilishiga sabab bu o'zgaradi yani yangi ma'lumot yuklash mumkin.

```python
name="Abdulloh"
print(name)
name="Davlat"
print(name)
```

```
Abdulloh
Davlat
```

**Diqqat** o'zgaruvchiga nimadir nom berishda ehtiyot bo'lamiz

O'zgaruvchilarga nom berishda quyidagi qoidalarga amal qiling:

O'zgaruvchi nomi harf yoki pastki chiziq (\_) bilan boshlanishi kerak

O'zgaruvchi nomi raqam bilan boshlanishi mumkin emas

O'zgaruvchi nomida faqatgina lotin alifbosi harflari (A-z), raqamlar (0-9) va pastki chiziq (\_) qatnashishi mumkin

O'zgaruvchi nomida bo'shliq (пробел) bo'lishi mumkin emas

O'zgaruvchi nomida katta-kichik harflar turlicha talqin qilinadi (ism, ISM, va Ism uchta turli o'zgaruvchi)

**Eslatma** o'zgaruvchiga nom berishda kichik harflardan foydalaning agar nom ikki va undan ortiq so'z bo'lsa unda orasida ( ) bo'sh joy qoldirmang (\_) pastki chizidan foydalaning va iloji boricha o'zgaruvchiga tushunarli nom bering adashib ketmasligingiz uchun foydali bu **Diqqat** o'zgaruvchiga bermaslik kerak bo'lgan so'zlar mavjud

![image.png](../.gitbook/assets/image.png)

"Hello World" matnini yangi o'zgaruvchiga yuklang va print() qiling

Ism va yosh o'zgaruvchilarini yarating va ularni bitta print() da chiqaring.

radius = 5 o'zgaruvchisini yarating va doira yuzini hisoblab (3.14 \* radius\*\*2) natijani chiqaring

xabar deb nomlangan o'zgaruvchiga biron matn yuklang unni chiqaring va yangi ma'lumot yuklab uni ham chiqaring

class deb o'zgaruvchiga ma'lumot yuklab uni chiqarishga harakat qiling

Quyidagi kodni bajaring:

radius = 5 pi = 3.14159 aylana\_yuzi = pi \* radius\*\*2 print("Radiusi" , radius, "ga teng aylananing yuzi=", aylana\_yuzi)
