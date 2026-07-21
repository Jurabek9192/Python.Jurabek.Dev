# Python-da Set 
Set (to'plam) — bu o'ziga xos xususiyatlarga ega bo'lgan ma'lumotlar turi. Uni tushunish uchun matematikadagi to'plamlar nazariyasini eslash kifoya.


Setning 3 ta asosiy qoidasi bor:

* Tartiblanmagan (Unordered): Elementlar qaysi tartibda kiritilsa, shunday saqlanmaydi.

* Takrorlanmas (Unique): Bir xil elementdan faqat bitta bo'lishi mumkin.

* O'zgaruvchan (Mutable): To'plamga element qo'shish yoki o'chirish mumkin, lekin uning ichidagi elementlar o'zgarmas (immutable) bo'lishi shart (masalan, list qo'shib bo'lmaydi).

#### Set yaratish
To'plam figurali qavslar { } yoki set() funksiyasi yordamida yaratiladi.


```python
mevalar = {"olma", "banan", "olcha", "olma"} 
print(mevalar) 
# Natija: {'olma', 'banan', 'olcha'}  --> "olma" takrorlangani uchun bittasi qoldi.
```

Eslatma: Bo'sh to'plam yaratish uchun {}  ishlatmang (chunki bu bo'sh lug'at - dict yaratadi), doim set() dan foydalaning.

#### Element qo'shish va o'chirish
* add(): Bitta element qo'shish.

* update(): Bir nechta element (yoki ro'yxat) qo'shish.

* remove() yoki discard(): Elementni o'chirish. (remove agar element bo'lmasa xato beradi, discard esa bermaydi).


```python
raqamlar = {1, 2, 3}
raqamlar.add(4)
raqamlar.update([5, 6, 7])
raqamlar.discard(2)
print(raqamlar) # {1, 3, 4, 5, 6, 7}
```

    {1, 3, 4, 5, 6, 7}
    

#### To'plamlar ustida matematik amallar
Setning eng kuchli tomoni — ikki to'plamni solishtirishdir.

![1.jpg](set/1.jpg)

| Amal nomi | Belgisi / Metodi | Vazifasi |
| :--- | :--- | :--- |
| **Birlashma (Union)** | \| yoki `.union()` | Ikkala to'plamdagi barcha elementlarni yig'adi. |
| **Kesishma (Intersection)** | \& yoki `.intersection()` | Faqat ikkalasida ham bor elementlarni oladi. |
| **Ayirma (Difference)** | \- yoki `.difference()` | Birinchisida bor, lekin ikkinchisida yo'q elementlar. |
| **Simmetrik ayirma** | \^ | Faqat bittasida bor elementlar (umumiy bo'lmaganlar). |


```python
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

print(a & b) # {3, 4} (Kesishma)
print(a | b) # {1, 2, 3, 4, 5, 6} (Birlashma)
print(a - b) # {1, 2} (Ayirma)
```

    {3, 4}
    {1, 2, 3, 4, 5, 6}
    {1, 2}
    

#### Qachon ishlatiladi?
Takrorlanishni yo'qotish: Ro'yxatdagi (list) dublikatlarni bitta qatorda o'chirmoqchi bo'lsangiz: list(set(my_list)).

A'zolikni tekshirish: Biror element to'plam ichida bor-yo'qligini tekshirish listga qaraganda million marta tezroq ishlaydi (Hashing hisobiga).

Taqqoslash: Ikki xil ma'lumotlar bazasidagi farqlarni tezda topishda.

Shu o'rinda nima uchun set kerak agar bizda boshqa ma'lumot turlari borku ro'yxat bilan ishlashning degan savolga javob berishga harakat qilamiz:

#### Dictionary va Set 
ma'lumot qidirish tezligi bo'yicha List va Tupledan o'nlab, hatto millionlab marta tezroq ishlashi mumkin.

Buning sababini oddiy hayotiy misol va texnik misolda ko'ramiz

#### 1. "Varaqlash" vs "Manzil" (Mantiqiy farq)
List va Tuple (Varaqlash): Tasavvur qiling, sizda 1000 sahifali kitob bor va siz undan biror so'zni qidiryapsiz. Siz 1-betdan boshlab oxirigacha birma-bir qarab chiqasiz. Agar qidirayotgan so'zingiz 999-betda bo'lsa, juda ko'p vaqt yo'qotasiz. Bunga dasturlashda $O(n)$ (chiziqli vaqt) deyiladi.Set va Dictionary (Manzil): Bu xuddi kitobning mundarijasi yoki lug'atga o'xshaydi. Siz "Olma" so'zini qidirmoqchi bo'lsangiz, hashing algoritmi sizga darrov "u 50-betda" deb manzilni ko'rsatadi. Siz to'g'ridan-to'g'ri o'sha betni ochasiz. Bunga $O(1)$ (doimiy vaqt) deyiladi.

2. Tezlikni amalda solishtirish
Keling, kichik bir test o'tkazamiz. Tasavvur qiling, bizda 1 millionta son bor va biz oxirgi sonni qidiryapmiz:

### Ma'lumot turlarining qidirish tezligi bo'yicha taqqoslanishi (1 mln element misolida)

| Ma'lumot turi | Qidirish mexanizmi | Tezlik (Complexity) | Izoh |
| :--- | :--- | :--- | :--- |
| **List** | Chiziqli qidiruv (Linear search) | $O(n)$ - Sekin | Har bir elementni birma-bir tekshiradi. |
| **Tuple** | Chiziqli qidiruv (Linear search) | $O(n)$ - Sekin | List bilan bir xil mexanizmda ishlaydi. |
| **Set** | Hashing (Hash table) | $O(1)$ - Juda tez | Hash-kod orqali element manzilini darrov topadi. |
| **Dictionary** | Hashing (Key-based) | $O(1)$ - Juda tez | Kalit (key) bo'yicha to'g'ridan-to'g'ri murojaat qiladi. |

#### 3. Nima uchun har doim Set ishlatmaymiz?
Agar Set va Dict shunchalik tez bo'lsa, nima uchun List kerak? Chunki ularning ham o'z "kamchiliklari" bor:

Xotira (RAM): Set va Dictionary tez ishlashi uchun xotiradan ko'proq joy talab qiladi (Hash-jadval qurish uchun). List esa ancha tejamkor.

Tartib: Listda elementlar tartibi (index) muhim. Setda esa elementlar tartibsiz saqlanadi.

Takrorlanish: Listda bir xil elementni ko'p marta saqlash mumkin, Setda esa yo'q.

#### 4. Qachon qaysinisini tanlash kerak?
List/Tuple: Agar elementlar tartibi muhim bo'lsa va siz ko'pincha elementlarni qo'shib borish (append) bilan shug'ullansangiz.

Set: Agar sizga faqat unikal (takrorlanmas) elementlar kerak bo'lsa va asosiy ishingiz "bu element bormi yoki yo'qmi?" deb tekshirish bo'lsa (if x in my_set).

Dictionary: Agar ma'lumotlarni juftlikda (kalit-qiymat) saqlash va kalit orqali juda tez topish kerak bo'lsa.

#### Amaliy sinov (ipynb uchun):


```python
import time

# 1 million elementli list va set yaratamiz
katta_list = list(range(1000000))
katta_set = set(range(1000000))

# Listda qidirish
start = time.time()
999999 in katta_list
print(f"Listda qidirish vaqti: {time.time() - start} sek")

# Setda qidirish
start = time.time()
999999 in katta_set
print(f"Setda qidirish vaqti: {time.time() - start} sek")
```

    Listda qidirish vaqti: 0.03339552879333496 sek
    Setda qidirish vaqti: 0.0010166168212890625 sek
    

Natijada Set taxminan 10 000 - 100 000 marta tezroq ekanini ko'rasiz.



#### Topshiriqlar

1. To'plam yaratish va takrorlanuvchi elementlar
Topshiriq: Berilgan [1, 2, 2, 3, 4, 4, 5, 1] ro'yxatidan foydalanib to'plam yarating va natijani ekranga chiqaring. Ekranda takrorlangan elementlar yo'qligiga e'tibor bering.

2. Element qo'shish (add)
Topshiriq: Bo'sh colors = {"red", "green", "blue"} to'plamiga add() metodi yordamida "yellow" rangini qo'shing.

3. Mavjud elementni nusxalash (copy)
Topshiriq: original_set = {10, 20, 30} to'plamining nusxasini copy_set o'zgaruvchisiga oling va copy_set ga 40 ni qo'shing. original_set o'zgarmaganini tekshiring.

4. Elementni o'chirish (remove va discard)
Topshiriq: {5, 10, 15, 20} to'plamidan remove() yordamida 15 ni, discard() yordamida esa to'plamda yo'q bo'lgan 100 ni o'chirishga harakat qiling (xatolik bermasligini kuzating).

5. Tasodifiy elementni sug'urib olish (pop)
Topshiriq: items = {"apple", "banana", "cherry"} to'plamidan pop() metodini ishlatib tasodifiy elementni sug'urib oling va qolgan to'plamni chiqaring.

6. To'plamni to'liq tozalash (clear)
Topshiriq: data = {1, 2, 3, 4, 5} to'plamini clear() metodi yordamida bo'shating.

7. Birlashma amali (union va |)
Topshiriq: set_a = {1, 2, 3} va set_b = {3, 4, 5} to'plamlarining birlashmasini ham union() metodi, ham | operatori yordamida toping.

8. Kesishma amali (intersection va &)
Topshiriq: Yuqoridagi set_a va set_b to'plamlarining kesishmasini toping.

9. Ayirma amali (difference va -)
Topshiriq: set_a da bor, lekin set_b da yo'q bo'lgan elementlarni toping (set_a - set_b).

10. Simmetrik ayirma (symmetric_difference va ^)
Topshiriq: Ikkala to'plamning faqat bittasida qatnashgan (umumiy bo'lmagan) elementlarni toping.

11. To'plamlarni yangilash (update)
Topshiriq: base_set = {1, 2} to'plamiga update() metodi yordamida [3, 4, 5] ro'yxatidagi elementlarni qo'shing.

12. Kesishmani yangilash (intersection_update)
Topshiriq: x = {1, 2, 3, 4} va y = {3, 4, 5, 6} berilgan. x ustida intersection_update(y) ni bajaring va x ning qiymati qanday o'zgarganini ko'ring.

13. Ayirmani yangilash (difference_update)
Topshiriq: s1 = {1, 2, 3, 4} to'plamidan s2 = {3, 4} elementlarini difference_update() yordamida ayirib tashlang.

14. Qism to'plamni tekshirish (issubset)
Topshiriq: sub = {2, 3} va main = {1, 2, 3, 4, 5} berilgan. sub to'plami main ning qism to'plami ekanligini issubset() orqali tekshiring.

15. Ustuvor to'plamni tekshirish (issuperset)
Topshiriq: main to'plami sub ni o'z ichiga olishini (ya'ni issuperset ekanligini) tekshiring.

16. Kesishmasligini tekshirish (isdisjoint)
Topshiriq: group1 = {1, 2, 3} va group2 = {4, 5, 6} to'plamlarining kesishmasi bo'sh ekanligini isdisjoint() yordamida aniqlang.

17. Ro'yxatdagi dublikatlarni tozalash funksiyasi
Topshiriq: Istalgan ro'yxatni qabul qilib, undagi barcha takrorlangan elementlarni olib tashlaydigan va natijani tartiblangan holda qaytaruvchi funksiya yozing.

18. Ikki matndagi umumiy harflarni topish
Topshiriq: Berilgan ikki xil matn (str1 = "python", str2 = "java") tarkibidagi umumiy harflarni to'plam yordamida toping.

19. Immutability va Frozenset
Topshiriq: O'zgartirib bo'lmaydigan to'plam — frozenset yarating va unga yangi element qo'shib ko'ring (qanday xatolik chiqishini kuzating).

20. Set Comprehension
Topshiriq: 1 dan 10 gacha bo'lgan sonlar orasidan faqat juft sonlarning kvadratlarini o'z ichiga olgan to'plamni set comprehension yordamida hosil qiling.














