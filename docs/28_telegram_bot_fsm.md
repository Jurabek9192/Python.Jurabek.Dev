# 28 — TELEGRAM BOT: HOLATLAR (FSM)

## Muammo: bosqichma-bosqich suhbat

Ko'p botlar foydalanuvchidan **ketma-ket bir necha savol** so'rashi kerak bo'ladi — masalan ro'yxatdan o'tishda: avval ism, keyin yosh, keyin telefon raqami. Bot bu jarayonning **qaysi bosqichida** ekanligini "eslab qolishi" kerak. Buni hal qiluvchi vosita — **FSM (Finite State Machine — chekli holatlar mashinasi)**.

## FSM asosiy tushunchalari

- **State (holat)** — foydalanuvchi suhbatning qaysi bosqichida ekanligini bildiruvchi "belgi" (masalan "ism kutilmoqda", "yosh kutilmoqda")
- **StatesGroup** — bir nechta bog'liq holatni guruhlaydigan klass
- **FSMContext** — har bir foydalanuvchi uchun holat va vaqtinchalik ma'lumotlarni saqlovchi obyekt

## Holatlarni e'lon qilish

```python
from aiogram.fsm.state import State, StatesGroup

class RoyxatdanOtish(StatesGroup):
    ism_kutilmoqda = State()
    yosh_kutilmoqda = State()
    telefon_kutilmoqda = State()
```

## Dispatcher'ni "storage" bilan sozlash

FSM ishlashi uchun holatlarni qayerdadir saqlash kerak — eng oddiy usul, xotirada (dastur o'chsa, ma'lumot yo'qoladi):

```python
from aiogram.fsm.storage.memory import MemoryStorage

dp = Dispatcher(storage=MemoryStorage())
```

## To'liq FSM misoli — ro'yxatdan o'tish

```python
from aiogram.fsm.context import FSMContext

@dp.message(Command("royxatdanotish"))
async def royxat_boshlash(message: types.Message, state: FSMContext):
    await message.answer("Ismingizni kiriting:")
    await state.set_state(RoyxatdanOtish.ism_kutilmoqda)

@dp.message(RoyxatdanOtish.ism_kutilmoqda)
async def ism_qabul_qilish(message: types.Message, state: FSMContext):
    await state.update_data(ism=message.text)          # ma'lumotni saqlash
    await message.answer("Yoshingizni kiriting:")
    await state.set_state(RoyxatdanOtish.yosh_kutilmoqda)

@dp.message(RoyxatdanOtish.yosh_kutilmoqda)
async def yosh_qabul_qilish(message: types.Message, state: FSMContext):
    if not message.text.isdigit():
        await message.answer("Iltimos, faqat raqam kiriting!")
        return
    await state.update_data(yosh=message.text)
    await message.answer("Telefon raqamingizni kiriting:")
    await state.set_state(RoyxatdanOtish.telefon_kutilmoqda)

@dp.message(RoyxatdanOtish.telefon_kutilmoqda)
async def telefon_qabul_qilish(message: types.Message, state: FSMContext):
    await state.update_data(telefon=message.text)

    malumot = await state.get_data()      # barcha saqlangan ma'lumotni olish
    await message.answer(
        f"Ro'yxatdan o'tish yakunlandi!\n"
        f"Ism: {malumot['ism']}\n"
        f"Yosh: {malumot['yosh']}\n"
        f"Telefon: {malumot['telefon']}"
    )
    await state.clear()      # holatni tozalash — suhbat tugadi
```

## Jarayonni bekor qilish

Foydalanuvchi istalgan vaqtda jarayonni to'xtatishi uchun, alohida `/bekor` buyrug'i qo'shiladi:

```python
@dp.message(Command("bekor"))
async def bekor_qilish(message: types.Message, state: FSMContext):
    joriy_holat = await state.get_state()
    if joriy_holat is None:
        await message.answer("Hech qanday faol jarayon yo'q")
        return
    await state.clear()
    await message.answer("Jarayon bekor qilindi")
```

## FSM va inline klaviaturalarni birga ishlatish

FSM oddiy matnli javoblardan tashqari, tugma bosishlarni ham "kutish" holatida ishlatilishi mumkin — masalan foydalanuvchi ro'yxatdan o'tayotganda, "jinsi" savoli uchun inline tugmalar berish mumkin.

---

## 🎯 MASHQLAR (20 ta)

🟢 **Oson (1-8)**

1. Ikki bosqichli (ism va yosh so'rovchi) oddiy `StatesGroup` yarating.
2. `/royxatdanotish` buyrug'i bilan birinchi holatga o'tuvchi handler yozing.
3. Ism kiritilgandan keyin, uni `state.update_data()` bilan saqlang.
4. Barcha ma'lumot yig'ilgach, `state.get_data()` bilan olib, foydalanuvchiga qaytarib ko'rsating.
5. `/bekor` buyrug'i bilan jarayonni istalgan bosqichda to'xtatuvchi handler yozing.
6. Yosh kiritilganda, `isdigit()` bilan tekshirib, noto'g'ri bo'lsa qayta so'rang.
7. Jarayon tugagach, `state.clear()` chaqirilganini tekshiring — botni qayta ishga tushirmasdan, `/royxatdanotish`ni qayta chaqiring.
8. 3 bosqichli FSM jarayonini to'liq, boshidan oxirigacha qo'lda sinab ko'ring.

🟡 **O'rta (9-15)**

9. "Fikr-mulohaza (feedback) boti" yarating — foydalanuvchidan ism, mavzu va fikr-mulohaza matnini ketma-ket so'rang.
10. Har bir bosqichda, foydalanuvchiga "hozir qaysi bosqichdasiz" degan progress ko'rsating (masalan "1/3-qadam: Ism").
11. FSM jarayoniga inline tasdiqlash tugmasini ("Ha, to'g'ri" / "Qaytadan boshlash") qo'shing.
12. Telefon raqamini FSM orqali so'rab, uni regex (Kitob 3'dagi bilim) bilan tekshiring — noto'g'ri formatda bo'lsa qayta so'rang.
13. "Buyurtma berish boti" — mahsulot nomi, miqdori, yetkazib berish manzilini ketma-ket so'rovchi FSM yarating.
14. Har bir FSM bosqichida, `/bekor` buyrug'i ishlashini alohida tekshirib chiqing (har bosqichdan bekor qilib ko'ring).
15. Foydalanuvchi FSM jarayonida bo'lmagan vaqtda oddiy xabar yozsa, "Avval biror buyruq tanlang" deb javob beruvchi umumiy handler qo'shing.

🔴 **Qiyin (16-20)**

16. To'liq "ro'yxatdan o'tish" tizimini yarating — ism, yosh, telefon, shahar so'ralib, oxirida barcha ma'lumot fayl yoki JSON'ga saqlansin (Kitob 2'dagi bilim bilan).
17. "Test topshirish boti" — FSM yordamida foydalanuvchiga ketma-ket 5 ta savol beriladi, har biriga inline tugmalar orqali javob beriladi, oxirida natija chiqadi.
18. Ko'p bosqichli "buyurtma" jarayoniga, har bosqichda "orqaga qaytish" imkoniyatini (oldingi holatga qaytish) qo'shing.
19. FSM va oddiy dictionary (foydalanuvchilar bazasi o'rnini bosuvchi) yordamida, "profil tahrirlash" tizimini yarating — foydalanuvchi mavjud ma'lumotini yangilay olsin.
20. To'liq UNIWAY ACADEMY "ro'yxatdan o'tish boti" — talaba ismi, yoshi, qaysi yo'nalishni (Python/C++/Robotika/Scratch) tanlashi FSM orqali so'ralib, oxirida ma'lumotlar tartibli formatda tasdiqlansin va (agar bilsangiz) faylga saqlansin.

---

**Oldingi mavzu:** [27 — Telegram bot: Klaviaturalar](./27_telegram_bot_klaviaturalar.md)
**Keyingi mavzu:** [29 — YAKUNIY LOYIHA: To'liq Telegram bot](./29_telegram_bot_yakuniy_loyiha.md)
