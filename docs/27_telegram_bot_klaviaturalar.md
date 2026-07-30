# 27 — TELEGRAM BOT: KLAVIATURALAR (TUGMALAR)

## Ikki xil klaviatura turi

Telegram botlarida ikki xil tugmalar mavjud:

1. **Reply klaviatura** — ekran pastida, oddiy klaviatura o'rnida chiqadi, tugma bosilganda oddiy matn xabari yuboriladi
2. **Inline klaviatura** — xabarning o'zi ostida chiqadi, tugma bosilganda maxsus "callback" signali yuboriladi (matn yubormaydi)

## Reply klaviatura yaratish

```python
from aiogram.types import ReplyKeyboardMarkup, KeyboardButton
from aiogram.utils.keyboard import ReplyKeyboardBuilder

def asosiy_menyu():
    builder = ReplyKeyboardBuilder()
    builder.add(KeyboardButton(text="📚 Darslar"))
    builder.add(KeyboardButton(text="ℹ️ Ma'lumot"))
    builder.add(KeyboardButton(text="📞 Aloqa"))
    builder.adjust(2)      # bir qatorda nechta tugma bo'lishi
    return builder.as_markup(resize_keyboard=True)

@dp.message(Command("start"))
async def start_handler(message: types.Message):
    await message.answer("Menyudan tanlang:", reply_markup=asosiy_menyu())
```

`resize_keyboard=True` — klaviaturani tugmalar soniga moslab kichraytiradi (aks holda katta bo'lib chiqadi).

## Reply tugma bosilganda javob berish

Reply tugma oddiy matn xabari sifatida keladi, shuning uchun uni `F.text` bilan ushlaymiz:

```python
@dp.message(F.text == "📚 Darslar")
async def darslar_handler(message: types.Message):
    await message.answer("Bizda Python, C++, Robotika va Scratch darslari mavjud!")

@dp.message(F.text == "📞 Aloqa")
async def aloqa_handler(message: types.Message):
    await message.answer("Telefon: +998 90 123 45 67")
```

## Klaviaturani olib tashlash

```python
from aiogram.types import ReplyKeyboardRemove

await message.answer("Klaviatura yopildi", reply_markup=ReplyKeyboardRemove())
```

## Inline klaviatura yaratish

```python
from aiogram.types import InlineKeyboardButton
from aiogram.utils.keyboard import InlineKeyboardBuilder

def tasdiqlash_klaviaturasi():
    builder = InlineKeyboardBuilder()
    builder.add(InlineKeyboardButton(text="✅ Ha", callback_data="tasdiq_ha"))
    builder.add(InlineKeyboardButton(text="❌ Yo'q", callback_data="tasdiq_yoq"))
    return builder.as_markup()

@dp.message(Command("tasdiqla"))
async def tasdiqla_handler(message: types.Message):
    await message.answer("Roziligingizni tasdiqlaysizmi?", reply_markup=tasdiqlash_klaviaturasi())
```

## Inline tugma bosilganda — CallbackQuery

Inline tugma bosilganda, `message` emas, alohida **`CallbackQuery`** obyekti keladi:

```python
from aiogram.types import CallbackQuery

@dp.callback_query(F.data == "tasdiq_ha")
async def tasdiq_ha_handler(callback: CallbackQuery):
    await callback.answer("Rahmat!")                        # kichik bildirishnoma (popup)
    await callback.message.answer("Siz tasdiqladingiz ✅")     # oddiy xabar

@dp.callback_query(F.data == "tasdiq_yoq")
async def tasdiq_yoq_handler(callback: CallbackQuery):
    await callback.answer()
    await callback.message.answer("Bekor qilindi ❌")
```

**Muhim:** `callback.answer()` chaqirilishi **shart** — aks holda foydalanuvchi tugmasida "yuklanmoqda" belgisi doimiy aylanib turadi.

## Inline tugmalar bilan URL ochish

```python
builder = InlineKeyboardBuilder()
builder.add(InlineKeyboardButton(text="Bizning kanal", url="https://t.me/robocode_uzbekistan"))
```

## Xabarni tahrirlash (edit)

Inline tugma bosilganda, yangi xabar yubormasdan, mavjud xabarni "tahrirlash" mumkin — bu chiroyli menyu naqshlarida ko'p ishlatiladi:

```python
@dp.callback_query(F.data == "orqaga")
async def orqaga_handler(callback: CallbackQuery):
    await callback.message.edit_text("Asosiy menyu", reply_markup=asosiy_inline_menyu())
```

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. 3 ta tugmali (masalan "Darslar", "Aloqa", "Manzil") reply klaviatura yarating va `/start` buyrug'ida chiqaring.
2. Har bir reply tugmaga alohida javob beruvchi handler yozing.
3. `ReplyKeyboardRemove()` yordamida klaviaturani yopuvchi `/yopish` buyrug'ini qo'shing.
4. 2 ta tugmali ("Ha", "Yo'q") inline klaviatura yarating.
5. Inline tugmalar bosilganda `callback.answer()` bilan kichik bildirishnoma chiqaring.
6. URL ochuvchi inline tugma yarating (masalan sizning Instagram yoki Telegram kanalingizga).
7. `builder.adjust()` yordamida tugmalar joylashuvini (masalan 1 qatorda 3 ta) sozlang.
8. Reply va Inline klaviaturaning ishlash farqini o'zingiz sinab, izoh sifatida yozing.

🟡 **O'rta (9-15)**

9. "Ha/Yo'q" tasdiqlash tizimini to'liq ishlab chiqing — har ikkala tugma uchun mos javoblar bilan.
10. 4 ta fan nomidan iborat inline klaviatura yarating, har biri bosilganda o'sha fan haqida qisqa ma'lumot chiqsin.
11. "Orqaga" tugmasi bilan ikki bosqichli inline menyu yarating (asosiy menyu -> fan tanlash -> orqaga).
12. Reply klaviatura orqali "Til tanlash" menyu yarating (O'zbek/Rus/Ingliz), tanlangan tilga qarab keyingi xabarlar shu tilda chiqsin.
13. `callback.message.edit_text()` yordamida, inline menyuda sahifalar orasida (masalan 1-sahifa/2-sahifa) o'tish tizimini yarating.
14. Mahsulotlar katalogi bot: har mahsulot uchun "Batafsil" inline tugmasi, bosilganda mahsulot haqida to'liq ma'lumot chiqadigan qiling.
15. Reyting tizimi: 1 dan 5 gacha yulduzcha (inline tugmalar) orqali foydalanuvchi baho bera oladigan tizim yarating.

🔴 **Qiyin (16-20)**

16. To'liq "restoran menyu boti" — kategoriyalar (taomlar, ichimliklar, desertlar) inline tugmalar orqali, har birida "orqaga" va "asosiy menyu" tugmalari bilan.
17. "Viktorina (quiz) boti" — savol beriladi, 4 ta inline javob variantidan biri tanlanadi, to'g'ri/noto'g'ri javob ko'rsatiladi.
18. Reply klaviatura bilan "sozlamalar" menyusi yarating — foydalanuvchi bildirishnomalarni yoqish/o'chirish, tilni o'zgartirish kabi amallarni bajara olsin.
19. Inline klaviatura orqali "buyurtma savati" tizimi — mahsulot tanlanganda "savatga qo'shildi" xabari, alohida "Savatni ko'rish" tugmasi bilan.
20. To'liq UNIWAY ACADEMY "ma'lumot boti"ni klaviaturalar bilan boyiting — asosiy menyu (Darslar/Narxlar/Aloqa/Manzil), har biri bosilganda tegishli ma'lumot va "Orqaga" tugmasi bilan qaytish imkoniyati.

---

**Oldingi mavzu:** [26 — Telegram bot asoslari](./26_telegram_bot_asoslari.md)
**Keyingi mavzu:** [28 — Telegram bot: Holatlar (FSM)](./28_telegram_bot_fsm.md)
