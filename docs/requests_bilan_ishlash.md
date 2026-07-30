# REQUESTS KUTUBXONASI (API BILAN ISHLASH)

## API nima?

**API (Application Programming Interface)** — ikki dastur bir-biri bilan "gaplashishi" uchun ishlatiladigan qoidalar va vositalar to'plami. Masalan, ob-havo ilovasi ob-havo ma'lumotini o'zi "o'ylab topmaydi" — u ob-havo xizmatining API'siga so'rov yuborib, natijani oladi. Xuddi shunday, Telegram bot ham Telegram serverining API'si orqali ishlaydi.

**`requests`** — Python'da internet orqali (HTTP protokoli bo'yicha) so'rov yuborish uchun eng mashhur va qulay kutubxona.

```bash
pip install requests
```

```python
import requests
```

## HTTP so'rov turlari — asosiy tushunchalar

| Metod | Vazifasi |
|---|---|
| `GET` | Ma'lumot **olish** (masalan sahifani ochish, ma'lumot so'rash) |
| `POST` | Yangi ma'lumot **yuborish/yaratish** (masalan ro'yxatdan o'tish formasi) |
| `PUT` | Mavjud ma'lumotni **to'liq yangilash** |
| `PATCH` | Mavjud ma'lumotni **qisman yangilash** |
| `DELETE` | Ma'lumotni **o'chirish** |

Boshlang'ich darajada eng ko'p ishlatiladigani — **GET** va **POST**.

## Eng oddiy GET so'rovi

```python
import requests

javob = requests.get("https://api.github.com")
print(javob.status_code)     # 200 — muvaffaqiyatli degani
print(javob.text)               # javobning to'liq matni (odatda JSON formatida)
```

## status_code — natija muvaffaqiyatlimi?

| Kod | Ma'nosi |
|---|---|
| `200` | OK — hammasi muvaffaqiyatli |
| `201` | Created — yangi narsa yaratildi (POST'dan keyin) |
| `400` | Bad Request — so'rov noto'g'ri tuzilgan |
| `401` | Unauthorized — autentifikatsiya (token) kerak |
| `403` | Forbidden — kirish taqiqlangan |
| `404` | Not Found — so'ralgan narsa topilmadi |
| `500` | Internal Server Error — server tomonida xatolik |

```python
javob = requests.get("https://api.github.com/users/notmvjqiwjeoqwjeoqwj")
if javob.status_code == 200:
    print("Muvaffaqiyatli!")
elif javob.status_code == 404:
    print("Topilmadi")
else:
    print(f"Xatolik: {javob.status_code}")
```

## JSON javobni Python obyektiga aylantirish — .json()

Ko'pchilik zamonaviy API'lar javobni JSON formatida qaytaradi. `requests` buni to'g'ridan-to'g'ri Python dictionary/list'iga aylantirib beradigan qulay metodga ega:

```python
import requests

javob = requests.get("https://api.github.com/users/torvalds")
malumot = javob.json()          # JSON matnni Python dictionary'ga aylantiradi (json.loads() kabi)

print(type(malumot))              # <class 'dict'>
print(malumot["name"])               # Linus Torvalds
print(malumot["public_repos"])          # ochiq repozitoriylar soni
```

**Diqqat:** `.json()` — bu Kitob 2'da o'rgangan `json.loads()` bilan bir xil ishni bajaradi, faqat `requests` buni avtomatik, qulayroq qilib beradi.

## Query parametrlari — so'rovga qo'shimcha ma'lumot berish

Ko'p API'lar URL orqali qo'shimcha parametr (masalan qidiruv so'zi, sahifa raqami) qabul qiladi:

```python
import requests

parametrlar = {"q": "python", "sort": "stars"}
javob = requests.get("https://api.github.com/search/repositories", params=parametrlar)

# bu quyidagi URL'ga teng:
# https://api.github.com/search/repositories?q=python&sort=stars

natija = javob.json()
print(natija["total_count"])
```

## Headers — so'rovga qo'shimcha "ma'lumot"

Ba'zi API'lar maxsus sarlavha (header) talab qiladi — masalan autentifikatsiya tokeni:

```python
sarlavhalar = {
    "Authorization": "Bearer SIZNING_TOKENINGIZ",
    "User-Agent": "MeningDasturim/1.0"
}
javob = requests.get("https://api.example.com/malumot", headers=sarlavhalar)
```

## POST so'rovi — ma'lumot yuborish

```python
import requests

yangi_malumot = {
    "ism": "Ali",
    "email": "ali@mail.com"
}

javob = requests.post("https://api.example.com/foydalanuvchilar", json=yangi_malumot)
print(javob.status_code)     # odatda 201 (Created)
print(javob.json())
```

`json=yangi_malumot` — `requests`ga dictionary'ni avtomatik JSON formatiga aylantirib, so'rov bilan birga yuborishni buyuradi (`json.dumps()`ni qo'lda chaqirishga hojat yo'q).

## timeout — botni "osilib qolishdan" himoya qilish

Agar server javob bermasa, dastur abadiy kutib qolmasligi uchun, doim `timeout` belgilash tavsiya etiladi:

```python
try:
    javob = requests.get("https://api.example.com", timeout=5)     # 5 soniyadan ko'p kutmaydi
except requests.exceptions.Timeout:
    print("Server javob bermadi (vaqt tugadi)")
```

## Xatoliklarni to'liq boshqarish

```python
import requests

try:
    javob = requests.get("https://api.example.com/malumot", timeout=5)
    javob.raise_for_status()          # agar status_code xato (4xx/5xx) bo'lsa, xatolik chiqaradi
    malumot = javob.json()
    print(malumot)
except requests.exceptions.Timeout:
    print("Vaqt tugadi — server javob bermadi")
except requests.exceptions.ConnectionError:
    print("Internetga ulanishda muammo")
except requests.exceptions.HTTPError as xatolik:
    print(f"HTTP xatoligi: {xatolik}")
except requests.exceptions.RequestException as xatolik:
    print(f"Boshqa xatolik: {xatolik}")
```

## Amaliy misol — valyuta kursini olish

```python
import requests

def dollar_kursi():
    try:
        javob = requests.get("https://api.exchangerate-api.com/v4/latest/USD", timeout=5)
        javob.raise_for_status()
        malumot = javob.json()
        return malumot["rates"]["UZS"]
    except requests.exceptions.RequestException:
        return None

kurs = dollar_kursi()
if kurs:
    print(f"1 USD = {kurs:,.2f} so'm")
else:
    print("Kursni olib bo'lmadi")
```

## Amaliy misol — ob-havo ma'lumotini olish

```python
import requests

def obhavo(shahar):
    parametrlar = {"q": shahar, "appid": "SIZNING_API_KALITINGIZ", "units": "metric", "lang": "uz"}
    javob = requests.get("https://api.openweathermap.org/data/2.5/weather", params=parametrlar, timeout=5)

    if javob.status_code == 200:
        malumot = javob.json()
        harorat = malumot["main"]["temp"]
        tavsif = malumot["weather"][0]["description"]
        return f"{shahar}da harorat: {harorat}°C, {tavsif}"
    return "Ma'lumot topilmadi"

print(obhavo("Tashkent"))
```

## Fayl yuklab olish

```python
import requests

javob = requests.get("https://example.com/rasm.jpg", timeout=10)
with open("yuklangan_rasm.jpg", "wb") as fayl:     # "wb" — binary (rasm/fayl) rejimida yozish
    fayl.write(javob.content)                          # .text emas, .content — xom bayt ma'lumotlar uchun
```

## requests va Telegram bot (aiogram) bog'liqligi

Kitob 1'ning Telegram bot bo'limida siz `aiogram`dan foydalangan edingiz — u orqasida aynan shu HTTP so'rovlar mantig'i bilan ishlaydi (faqat asinxron ko'rinishda). Agar botingiz tashqi API'dan (masalan ob-havo yoki valyuta) ma'lumot olishi kerak bo'lsa, aynan `requests` (yoki uning asinxron varianti `aiohttp`) ishlatiladi:

```python
@dp.message(Command("kurs"))
async def kurs_handler(message: types.Message):
    kurs = dollar_kursi()     # yuqorida yozgan funksiyamiz
    if kurs:
        await message.answer(f"1 USD = {kurs:,.2f} so'm")
    else:
        await message.answer("Kursni olishda xatolik yuz berdi")
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. `requests.get("https://api.github.com")` so'rovini yuborib, `status_code` va `text`ni chiqaring.
2. GitHub'dan o'zingiz yoqtirgan ochiq loyihaning (masalan `https://api.github.com/repos/python/cpython`) ma'lumotini `.json()` bilan oling va nomini chiqaring.
3. `https://api.github.com/users/torvalds` so'rovini yuborib, foydalanuvchi ismini va ochiq repozitoriylar sonini chiqaring.
4. `status_code`ni tekshirib, agar 200 bo'lsa "Muvaffaqiyatli", aks holda "Xatolik" deb chiqaring.
5. `timeout=5` parametrini qo'shib, so'rov yuboring.
6. `params` yordamida GitHub qidiruv API'siga (`https://api.github.com/search/repositories`) "python" so'zini qidirtiring.
7. `try/except` bilan `requests.exceptions.Timeout` xatoligini ushlashga tayyor kod yozing.
8. `.json()` orqali olingan dictionary'ning barcha kalitlarini (`.keys()`) chiqaring.

🟡 **O'rta (9-15)**

9. Bir nechta GitHub foydalanuvchisi (masalan 3 ta) haqida ma'lumot olib, ularning ismi va repozitoriylar sonini jadval ko'rinishida chiqaring.
10. `raise_for_status()` metodini sinab, mavjud bo'lmagan sahifaga (masalan noto'g'ri username) so'rov yuborib, qanday xatolik chiqishini kuzating.
11. Ochiq valyuta kursi API'sidan (masalan exchangerate-api.com) foydalanib, USD/UZS kursini oling va chiqaring.
12. Query parametrlar (`params`) yordamida, GitHub qidiruvida natijalarni "stars" bo'yicha saralab so'rang.
13. `requests.exceptions.ConnectionError` va `requests.exceptions.Timeout`ni alohida-alohida ushlaydigan, to'liq xavfsiz so'rov funksiyasini yozing.
14. Bitta funksiya yozing — u shahar nomini qabul qilib, biror ochiq ob-havo API'sidan (ro'yxatdan o'tib, bepul API kalit oling) haroratni qaytarsin.
15. Rasm URL manzilidan foydalanib, uni `.content` va `"wb"` rejimida kompyuteringizga yuklab oling.

🔴 **Qiyin (16-20)**

16. To'liq "GitHub profil tekshiruvchi" dastur yozing — foydalanuvchi username kiritadi, dastur uning ismi, bio, ochiq repozitoriylar sonini chiroyli formatda chiqaradi, agar topilmasa tushunarli xabar beradi.
17. Bir nechta API so'rovini ketma-ket yuborib (masalan 5 xil GitHub foydalanuvchisi), natijalarni JSON faylga saqlang (bu mavzuni JSON mavzusi bilan birlashtiring).
18. `requests.Session()` obyektidan foydalanib, bir nechta so'rovni bitta "sessiya" orqali yuboring (bu tezroq ishlaydi, chunki ulanish qayta ochilmaydi).
19. Valyuta kursi botini yozing — foydalanuvchi summani kiritadi, dastur `requests` orqali joriy kursni olib, so'mga aylantirib chiqaradi, va agar internet aloqasi yo'q bo'lsa, tushunarli xatolik xabari beradi.
20. To'liq Telegram bot (aiogram, Kitob 1'dagi bilim bilan) yozing — u `/kurs` buyrug'iga javoban `requests` orqali joriy USD/UZS kursini olib, foydalanuvchiga yuborsin (xatoliklarni to'liq boshqargan holda).

---

**Bog'liq mavzular:** [JSON bilan ishlash](./json_bilan_ishlash.md) • [26 — Telegram bot asoslari](./26_telegram_bot_asoslari.md)
