# 26 — TELEGRAM BOT ASOSLARI (AIOGRAM)

## aiogram nima?

**aiogram** — Telegram botlarini Python'da yozish uchun mo'ljallangan, to'liq **asinxron (async)** kutubxona. U Kitob 3'da o'rgangan `threading` mavzusiga yaqin, lekin undan farqli, `asyncio` asosida ishlaydi — bu botlar uchun ayniqsa mos, chunki bot bir vaqtning o'zida yuzlab foydalanuvchidan kelayotgan xabarlarni kutishi va qayta ishlashi kerak.

```bash
pip install aiogram
```

## Bot yaratish — @BotFather

1. Telegram'da **@BotFather** botini toping
2. `/newbot` buyrug'ini yuboring
3. Bot uchun nom va username bering (username `bot` bilan tugashi kerak, masalan `mening_birinchi_bot`)
4. BotFather sizga maxsus **token** beradi (masalan `123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11`) — bu tokenni **hech kimga bermang**, u botingizga to'liq kirish huquqini beradi

## Eng oddiy bot — asosiy tuzilma

```python
import asyncio
from aiogram import Bot, Dispatcher, types
from aiogram.filters import Command

TOKEN = "SIZNING_TOKENINGIZ"

bot = Bot(token=TOKEN)
dp = Dispatcher()

@dp.message(Command("start"))
async def start_handler(message: types.Message):
    await message.answer(f"Salom, {message.from_user.first_name}! Men botman 🤖")

async def main():
    await dp.start_polling(bot)

if __name__ == "__main__":
    asyncio.run(main())
```

## Tuzilmani tushunish

- **`Bot`** — Telegram API bilan bevosita muloqot qiluvchi obyekt (token orqali autentifikatsiya qilinadi)
- **`Dispatcher`** — kelayotgan xabarlarni tegishli handler (ishlov beruvchi funksiya)larga yo'naltiruvchi "markaziy boshqaruvchi"
- **`@dp.message(...)`** — dekorator, muayyan turdagi xabar kelganda qaysi funksiya ishga tushishini belgilaydi
- **`async def`** — barcha handler funksiyalar **asinxron** bo'lishi shart (Kitob 3'dagi `threading` mavzusiga yaqin tushuncha)
- **`await`** — asinxron amalni "kutish" (masalan xabar yuborishni)
- **`dp.start_polling(bot)`** — botni ishga tushiradi, u Telegram serverlaridan doimiy ravishda yangi xabarlarni "so'rab" turadi (polling)

## Buyruqlarga javob berish

```python
@dp.message(Command("start"))
async def start_handler(message: types.Message):
    await message.answer("Botga xush kelibsiz!")

@dp.message(Command("help"))
async def help_handler(message: types.Message):
    await message.answer("Mavjud buyruqlar:\n/start — boshlash\n/help — yordam")
```

## Oddiy matnli xabarlarga javob berish

```python
from aiogram import F

@dp.message(F.text == "Salom")
async def salom_handler(message: types.Message):
    await message.answer("Va alaykum salom!")

@dp.message()      # filtrsiz — qolgan BARCHA xabarlarga javob (eng oxirida yoziladi)
async def echo_handler(message: types.Message):
    await message.answer(f"Siz yozdingiz: {message.text}")
```

`F` — aiogram'ning "magic filter" vositasi bo'lib, xabar xususiyatlariga (matn, fayl turi va h.k.) qarab filtrlash imkonini beradi.

## message obyektining foydali atributlari

```python
@dp.message()
async def malumot_handler(message: types.Message):
    print(message.from_user.id)              # foydalanuvchi ID'si
    print(message.from_user.first_name)         # ismi
    print(message.from_user.username)             # @username
    print(message.chat.id)                           # chat ID'si
    print(message.text)                                # yuborilgan matn
```

## Botni ishga tushirish

```bash
python bot.py
```

Terminalda dastur to'xtamasdan ishlab turadi — bu bot "tirik" ekanligini bildiradi. To'xtatish uchun `Ctrl+C`.

## Tokenni xavfsiz saqlash — muhim amaliyot

Tokenni to'g'ridan-to'g'ri kodga yozish (`TOKEN = "123456:..."`) — yomon amaliyot, ayniqsa kodni GitHub'ga yuklasangiz. Buning o'rniga muhit o'zgaruvchisi (environment variable) yoki alohida `.env` fayl ishlatiladi:

```bash
pip install python-dotenv
```

```python
from dotenv import load_dotenv
import os

load_dotenv()
TOKEN = os.getenv("BOT_TOKEN")
```

**`.env`** fayli (bu faylni `.gitignore`ga qo'shing!):
```
BOT_TOKEN=123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. @BotFather orqali o'zingizning birinchi botingizni yarating va tokenni oling.
2. Yuqoridagi eng oddiy bot kodini yozib, ishga tushiring va `/start` buyrug'iga javob olganini tekshiring.
3. `/help` buyrug'iga javob beruvchi yangi handler qo'shing.
4. Bot foydalanuvchining ismini (`message.from_user.first_name`) javobda ishlatsin.
5. Oddiy "echo" bot yozing — u foydalanuvchi yozgan har qanday matnni aynan o'zi qaytarib yuborsin.
6. `F.text == "..."` yordamida, foydalanuvchi "Salom" deb yozsa, bot maxsus javob bersin.
7. `message.from_user.id` va `message.chat.id` larni konsolga chiqarib, ular orasidagi farqni tushunib oling (izoh sifatida yozing).
8. `.env` fayl va `python-dotenv` yordamida tokenni kod ichidan chiqarib, xavfsiz saqlang.

🟡 **O'rta (9-15)**

9. `/vaqt` nomli maxsus buyruq yarating — u `datetime` moduli yordamida joriy vaqtni chiqarsin (Kitob 3'dagi bilim bilan).
10. `/tasodifiy` buyrug'i — `random.randint(1, 100)` yordamida tasodifiy son yuborsin.
11. Foydalanuvchi yozgan matnni katta harflarga aylantirib qaytaruvchi handler yozing.
12. Foydalanuvchi son yuborsa, uning juft/toqligini aniqlab javob beruvchi bot yozing (`message.text.isdigit()` bilan tekshiring).
13. `/mening_malumotim` buyrug'i — foydalanuvchining ID, ism va username'ini chiroyli formatda chiqarsin.
14. Bot ishga tushganda, konsolga "Bot ishga tushdi!" deb chop etuvchi kodni `main()` funksiyasiga qo'shing.
15. Foydalanuvchi "salom", "assalomu alaykum", "hi" so'zlaridan birini yozsa (bir nechta shart bilan), bot mos ravishda javob bersin.

🔴 **Qiyin (16-20)**

16. Oddiy "kalkulyator bot" yozing — foydalanuvchi "5 + 3" formatida xabar yuborsa, bot natijani hisoblab qaytarsin (`.split()` va `try/except` dan foydalaning).
17. Bot xabarlar sonini hisoblab boruvchi (har foydalanuvchi nechta xabar yozganini kuzatuvchi, oddiy dictionary bilan) tizim yarating.
18. `/vaqt`, `/tasodifiy`, `/malumot` va `/help` buyruqlaridan iborat, to'liq ishlaydigan "ko'p funksiyali yordamchi bot" yarating.
19. Bot xato (masalan noto'g'ri formatdagi xabar) kelganda, `try/except` yordamida chiroyli xatolik xabarini qaytarsin (Kitob 2'dagi bilim bilan).
20. O'zingizning UNIWAY ACADEMY talabalari uchun oddiy "ma'lumot boti" yarating — u `/darslar`, `/aloqa`, `/manzil` kabi buyruqlarga oldindan tayyorlangan javoblar bersin.

---

**Keyingi mavzu:** [27 — Telegram bot: Klaviaturalar (tugmalar)](./27_telegram_bot_klaviaturalar.md)
