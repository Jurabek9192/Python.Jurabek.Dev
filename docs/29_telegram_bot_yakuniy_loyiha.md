# 29 — YAKUNIY LOYIHA: TO'LIQ TELEGRAM BOT

## Loyiha haqida

Kitob 1'ning yakuniy loyihasi sifatida, endi barcha o'rgangan bilimlarni (funksiyalar, dictionary, JSON, FSM, klaviaturalar) birlashtirib, **to'liq ishlaydigan "UNIWAY ACADEMY Yordamchi Bot"** yaratamiz. Bu bot: menyu orqali navigatsiya, ro'yxatdan o'tish (FSM), va ma'lumotlarni saqlashni o'z ichiga oladi.

## Loyihada ishlatiladigan bilimlar

- ✅ aiogram asoslari (Bot, Dispatcher, handlerlar)
- ✅ Reply va Inline klaviaturalar
- ✅ FSM (ro'yxatdan o'tish jarayoni)
- ✅ JSON fayl bilan ishlash (ma'lumotlarni saqlash)
- ✅ Funksiyalar va dictionary (Kitob 1'dan)
- ✅ try/except (xavfsiz kiritish)

## Loyiha tuzilmasi

```
uniway_bot/
├── bot.py              # asosiy fayl
├── .env                  # token (git'ga yuklanmaydi)
└── talabalar.json          # ro'yxatdan o'tgan talabalar
```

## To'liq kod — `bot.py`

```python
import asyncio
import json
import os
from aiogram import Bot, Dispatcher, types, F
from aiogram.filters import Command
from aiogram.fsm.context import FSMContext
from aiogram.fsm.state import State, StatesGroup
from aiogram.fsm.storage.memory import MemoryStorage
from aiogram.types import (
    ReplyKeyboardRemove, InlineKeyboardButton, CallbackQuery
)
from aiogram.utils.keyboard import ReplyKeyboardBuilder, InlineKeyboardBuilder
from dotenv import load_dotenv

load_dotenv()
TOKEN = os.getenv("BOT_TOKEN")

bot = Bot(token=TOKEN)
dp = Dispatcher(storage=MemoryStorage())

# ----- HOLATLAR (FSM) -----
class RoyxatdanOtish(StatesGroup):
    ism_kutilmoqda = State()
    yosh_kutilmoqda = State()
    yonalish_kutilmoqda = State()

# ----- MA'LUMOTLARNI SAQLASH (JSON) -----
FAYL_NOMI = "talabalar.json"

def talabalarni_yuklash():
    try:
        with open(FAYL_NOMI, "r", encoding="utf-8") as fayl:
            return json.load(fayl)
    except FileNotFoundError:
        return []

def talabalarni_saqlash(talabalar):
    with open(FAYL_NOMI, "w", encoding="utf-8") as fayl:
        json.dump(talabalar, fayl, indent=4, ensure_ascii=False)

# ----- KLAVIATURALAR -----
def asosiy_menyu():
    builder = ReplyKeyboardBuilder()
    builder.button(text="📝 Ro'yxatdan o'tish")
    builder.button(text="📚 Yo'nalishlar")
    builder.button(text="📞 Aloqa")
    builder.adjust(2)
    return builder.as_markup(resize_keyboard=True)

def yonalish_klaviaturasi():
    builder = InlineKeyboardBuilder()
    for yonalish in ["Python", "C++", "Robototexnika", "Scratch"]:
        builder.add(InlineKeyboardButton(text=yonalish, callback_data=f"yonalish_{yonalish}"))
    builder.adjust(2)
    return builder.as_markup()

# ----- HANDLERLAR -----
@dp.message(Command("start"))
async def start_handler(message: types.Message):
    await message.answer(
        f"Assalomu alaykum, {message.from_user.first_name}!\n"
        f"UNIWAY ACADEMY yordamchi botiga xush kelibsiz 🤖",
        reply_markup=asosiy_menyu()
    )

@dp.message(F.text == "📚 Yo'nalishlar")
async def yonalishlar_handler(message: types.Message):
    await message.answer(
        "Bizda quyidagi yo'nalishlar mavjud:\n"
        "🐍 Python\n💻 C++\n🤖 Robototexnika\n🎮 Scratch"
    )

@dp.message(F.text == "📞 Aloqa")
async def aloqa_handler(message: types.Message):
    await message.answer("📞 Telefon: +998 90 123 45 67\n📍 Manzil: Toshkent shahri")

# ----- RO'YXATDAN O'TISH (FSM) -----
@dp.message(F.text == "📝 Ro'yxatdan o'tish")
async def royxat_boshlash(message: types.Message, state: FSMContext):
    await message.answer("Ismingizni kiriting:", reply_markup=ReplyKeyboardRemove())
    await state.set_state(RoyxatdanOtish.ism_kutilmoqda)

@dp.message(RoyxatdanOtish.ism_kutilmoqda)
async def ism_qabul_qilish(message: types.Message, state: FSMContext):
    await state.update_data(ism=message.text)
    await message.answer("Yoshingizni kiriting:")
    await state.set_state(RoyxatdanOtish.yosh_kutilmoqda)

@dp.message(RoyxatdanOtish.yosh_kutilmoqda)
async def yosh_qabul_qilish(message: types.Message, state: FSMContext):
    if not message.text.isdigit():
        await message.answer("Iltimos, faqat raqam kiriting!")
        return
    await state.update_data(yosh=message.text)
    await message.answer("Yo'nalishni tanlang:", reply_markup=yonalish_klaviaturasi())
    await state.set_state(RoyxatdanOtish.yonalish_kutilmoqda)

@dp.callback_query(RoyxatdanOtish.yonalish_kutilmoqda, F.data.startswith("yonalish_"))
async def yonalish_tanlash(callback: CallbackQuery, state: FSMContext):
    yonalish = callback.data.replace("yonalish_", "")
    malumot = await state.get_data()

    yangi_talaba = {
        "ism": malumot["ism"],
        "yosh": malumot["yosh"],
        "yonalish": yonalish,
        "telegram_id": callback.from_user.id
    }

    talabalar = talabalarni_yuklash()
    talabalar.append(yangi_talaba)
    talabalarni_saqlash(talabalar)

    await callback.answer("Ro'yxatdan o'tildi!")
    await callback.message.edit_text(
        f"✅ Ro'yxatdan muvaffaqiyatli o'tdingiz!\n\n"
        f"Ism: {yangi_talaba['ism']}\n"
        f"Yosh: {yangi_talaba['yosh']}\n"
        f"Yo'nalish: {yangi_talaba['yonalish']}"
    )
    await state.clear()

@dp.message(Command("bekor"))
async def bekor_qilish(message: types.Message, state: FSMContext):
    await state.clear()
    await message.answer("Jarayon bekor qilindi", reply_markup=asosiy_menyu())

# ----- ISHGA TUSHIRISH -----
async def main():
    print("Bot ishga tushdi...")
    await dp.start_polling(bot)

if __name__ == "__main__":
    asyncio.run(main())
```

## Bu loyihani qanday ishlatish kerak

1. `pip install aiogram python-dotenv`
2. `.env` faylini yarating, ichiga `BOT_TOKEN=sizning_tokeningiz` yozing
3. `python bot.py` bilan ishga tushiring
4. Telegram'da botingizga `/start` yuboring va sinab ko'ring

---

## 🎯 LOYIHANI KENGAYTIRISH — MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Yuqoridagi to'liq botni qo'lda yozib, ishga tushiring va to'liq ro'yxatdan o'tish jarayonini sinab ko'ring.
2. `/mendan` nomli yangi buyruq qo'shing — u foydalanuvchi haqida (agar avval ro'yxatdan o'tgan bo'lsa) `talabalar.json`dan ma'lumot topib chiqarsin.
3. "Yo'nalishlar" javobiga har bir yo'nalish narxini ham qo'shing.
4. Ro'yxatdan o'tishda "shahar" savolini ham qo'shing (4-bosqich sifatida).
5. Bot ishga tushganda konsolga qancha talaba avvaldan ro'yxatdan o'tganini (`len(talabalar)`) chiqaring.
6. `/bekor` buyrug'i FSM'ning har bosqichida to'g'ri ishlashini alohida-alohida tekshiring.
7. Yangi reply tugma ("❓ Savol berish") qo'shing — bosilganda foydalanuvchidan savolini yozishni so'rasin.
8. Botga `/statistika` buyrug'ini qo'shing — u nechta talaba, qaysi yo'nalishdan nechtasi ro'yxatdan o'tganini hisoblab chiqarsin.

🟡 **O'rta (9-15)**

9. Ro'yxatdan o'tishda, agar bir xil `telegram_id` allaqachon mavjud bo'lsa, "Siz allaqachon ro'yxatdan o'tgansiz" deb ogohlantiring va jarayonni to'xtating.
10. Har bir yo'nalish uchun (Python, C++, Robototexnika, Scratch) alohida "Batafsil" inline tugma qo'shing — bosilganda o'sha yo'nalish haqida to'liq matn chiqsin.
11. Adminlar uchun maxsus `/royxat` buyrug'ini qo'shing (faqat sizning `telegram_id`ingiz uchun ishlaydigan) — u barcha ro'yxatdan o'tgan talabalarni chiqarsin.
12. Ro'yxatdan o'tish jarayoniga "Ma'lumotlaringiz to'g'rimi?" degan yakuniy tasdiqlash bosqichini (Ha/Qaytadan) qo'shing.
13. `datetime` modulidan foydalanib, har bir ro'yxatdan o'tishga sana va vaqtni ham qo'shib saqlang.
14. Botga oddiy "FAQ" (tez-tez so'raladigan savollar) bo'limini inline menyu orqali qo'shing (kamida 3 ta savol-javob).
15. Xatolik yuz berganda (masalan `.json` fayl buzilgan bo'lsa), bot qulamasligini `try/except` bilan ta'minlang.

🔴 **Qiyin (16-20)**

16. To'liq "admin panel" qo'shing — faqat sizning ID'ingiz uchun ishlaydigan, `/royxat`, `/ochirish [ism]`, `/statistika` buyruqlari bilan.
17. Talabalar ro'yxatini CSV formatida eksport qiluvchi `/eksport` buyrug'ini qo'shing (Kitob 2'dagi CSV bilimi bilan).
18. Botga "eslatma" tizimini qo'shing — talaba muayyan vaqtda (masalan darsdan 1 soat oldin) avtomatik xabar olishi uchun (`asyncio.sleep()` yordamida oddiy versiyasini sinab ko'ring).
19. Ro'yxatdan o'tgan talabalarni yo'nalishlar bo'yicha guruhlab, har bir yo'nalish uchun alohida statistika (o'rtacha yosh, talabalar soni) chiqaruvchi buyruq yozing.
20. To'liq, professional darajadagi botni yarating — xatoliklarni to'liq boshqarish, chiroyli emoji va formatlash, admin funksiyalari, va barcha ma'lumotlarni ishonchli saqlash bilan. Botni real ishlatishga tayyor holga keltiring va o'z talabalaringiz bilan sinab ko'ring!

---

**Oldingi mavzu:** [28 — Telegram bot: Holatlar (FSM)](./28_telegram_bot_fsm.md)

---

## 🎉 TELEGRAM BOT BO'LIMI YAKUNLANDI!

Siz endi nafaqat Python asoslarini, balki ularni **real dunyoda ishlaydigan mahsulotga** — to'liq funksional Telegram botga aylantirishni ham bilasiz. Bu ko'nikma sizga o'z g'oyalaringizni tezda amalga oshirish, talabalaringiz uchun foydali vositalar yaratish imkonini beradi.
