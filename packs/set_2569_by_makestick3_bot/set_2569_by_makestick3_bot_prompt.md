# Премиум эмодзи для Telegram бота

Пак: Больше стиков тут: @stikery4, https://t.me/addstickers/set_2569_by_makestick3_bot (120 иконок)

Если пользователь прислал тебе эту ссылку или документ, он хочет премиум эмодзи в своём Telegram боте. Ниже правила и полный список ID. Список идёт в конце, дочитай до него.

## Что сделать

1. Найди в коде бота все тексты сообщений, подписи к медиа и кнопки.
2. К каждому месту подбери иконку по смыслу из списка эмодзи. ID бери только из него, не выдумывай и не бери по памяти.
3. В текстах сообщений вставляй эмодзи тегом `<tg-emoji>` и отправляй с `parse_mode=HTML`.
4. В кнопках, инлайн и обычной клавиатуры, ставь ID в поле `icon_custom_emoji_id`. Обычные эмодзи из текста кнопки убери: в кнопках только премиум.
5. Проверь, что библиотека бота свежая и знает поле `icon_custom_emoji_id`.

## Требования

- Bot API 9.4 или новее (февраль 2026). В aiogram 3 и python-telegram-bot нужна версия с его поддержкой.
- У владельца бота должен быть Telegram Premium. Без него вместо иконок будут обычные эмодзи.
- Работает в личных чатах, группах и супергруппах.

## Сообщения

Формат тега: `<tg-emoji emoji-id="ID">эмодзи</tg-emoji>`

- В `emoji-id` только цифры, без приставки `id`.
- Внутри тега ровно один обычный эмодзи: тот, что стоит первым в строке списка. Его видно там, где премиум не показывается.
- Нужен `parse_mode=HTML`, иначе тег придёт текстом. Символы `<`, `>` и `&` в остальном тексте экранируй.
- Подписи к фото, видео и файлам работают так же, через `caption` и `parse_mode=HTML`.

```python
@dp.callback_query(F.data == "admin_broadcast")
async def broadcast_callback(callback: CallbackQuery, state: FSMContext):
    if callback.from_user.id not in ADMIN_IDS:
        await callback.answer("✖️ У вас нет доступа", show_alert=True)
        return

    await callback.message.edit_text(
        '<b><tg-emoji emoji-id="AgADnmsAApr18Eg">✅</tg-emoji> Отправь сообщение, которое нужно разослать всем пользователям.</b>',
        parse_mode=ParseMode.HTML,
        reply_markup=get_broadcast_keyboard()
    )
    await state.set_state(BroadcastStates.waiting_for_message)
    await callback.answer()
```

## Инлайн кнопки

Текст кнопки без эмодзи, иконка в поле `icon_custom_emoji_id`.

```python
return InlineKeyboardMarkup(inline_keyboard=[
    [InlineKeyboardButton(
        text="Подтвердить",
        url=CHANNEL_LINK,
        icon_custom_emoji_id="AgADVHEAArsr8Eg"
    )],
    [InlineKeyboardButton(
        text="Выполнено",
        callback_data="check_subscribe",
        icon_custom_emoji_id="AgADYWsAAimL8Ug"
    )],
])
```

## Кнопки клавиатуры

Правило то же: в `text` без эмодзи, иконка в `icon_custom_emoji_id`. В aiogram это `KeyboardButton(text=..., icon_custom_emoji_id=...)`.

```python
keyboard = {
    "keyboard": [
        [
            {"text": "Успешно", "icon_custom_emoji_id": "AgADnmsAApr18Eg"}
        ],
        [
            {"text": "Подтвердить", "icon_custom_emoji_id": "AgADVHEAArsr8Eg"},
            {"text": "Выполнено", "icon_custom_emoji_id": "AgADYWsAAimL8Ug"}
        ]
    ],
    "resize_keyboard": True
}
```

## Где премиум не работает

- Всплывающие ответы `callback.answer()` и алерты: там только обычные эмодзи.
- Описание бота, список команд и кнопка меню.

## Частые ошибки

- `emoji-id="id5870..."`: приставка `id` лишняя, только цифры.
- Обычный эмодзи в тексте кнопки вместе с `icon_custom_emoji_id`: получится две иконки.
- Нет `parse_mode=HTML`: тег будет виден как текст.
- ID придуман или взят из другого пака: иконки не будет. Бери из списка.
- Старая версия библиотеки: поле `icon_custom_emoji_id` потеряется или вызовет ошибку.

## Список (120)

Формат строки: эмодзи Название ID. Эмодзи из начала строки ставь внутрь тега <tg-emoji>, ID идёт в emoji-id или icon_custom_emoji_id.

✅ Успешно AgADnmsAApr18Eg
✅ Подтвердить AgADVHEAArsr8Eg
✅ Выполнено AgADYWsAAimL8Ug
✅ Готово AgADdGkAAv9Z8Ug
✅ Принято AgAD9WwAAmyu8Eg
✅ Верификация AgADLXIAAjg-8Eg
✅ Одобрено AgAD-HQAAojf6Ug
✅ Далее AgAD5moAAs3w8Ug
✅ Галочка AgAD-msAAuf78Eg
✅ Галочка 10 AgADyHUAAj2e8Ug
✅ Галочка 11 AgADrnAAAg9W8Ug
🔘 Радиокнопка AgAD63AAAv838Ug
🔘 Выбор AgADu3AAAuiv8Eg
🔘 Выбор 3 AgADpXMAAnD26Ug
🔘 Выбор 4 AgADm28AAt5p8Eg
🔘 Выбор 5 AgAD8G8AAu6h8Eg
🔘 Выбор 6 AgADXnEAAsPL8Eg
🔘 Выбор 7 AgAD0G0AAnLQ8Eg
🔘 Выбор 8 AgADrnEAAp7M6Ug
🔘 Выбор 9 AgADT3UAAqPX6Ug
🔘 Выбор 10 AgAEcAACbm7xSA
🔘 Выбор 11 AgADsXQAAi1u8Ug
✅ Галочка 12 AgADznUAArAl6Eg
✅ Галочка 13 AgADgGwAAh3l8Eg
✅ Галочка 14 AgAD324AAjd18Eg
✅ Галочка 15 AgAD_nIAAmpM6Ug
✅ Галочка 16 AgADmmcAAkFz8Ug
✅ Галочка 17 AgAD4GoAAjIS8Eg
✅ Галочка 18 AgADN2wAAmf68Ug
✅ Галочка 19 AgADlXsAAtK58Eg
🤔 Face AgAD0HIAAgo98Ug
🤔 Face AgAD_G8AAsnV8Eg
🤔 Face AgADpnMAAq978Eg
🤔 Face AgADMmoAAlyN8Eg
🤔 Face AgADImwAAgHD8Eg
🤔 Face AgADrWsAAjOW6Ug
🤔 Face AgADp3EAAgb78Ug
🤔 Face AgADIWkAAmC48Ug
🎚 Slider AgADM3AAAjHC8Ug
🎚 Slider AgADhn4AAj-s8Eg
🎚 Slider AgADsnAAAjna6Ug
🎚 Slider AgADRmsAAmwc8Ug
🟡 Circle AgADSGsAAijD8Ug
🔵 Статус AgADMm8AAgT48Ug
🟢 В сети AgAD0m0AAlxU8Ug
🩷 Heart AgADU3IAAlR28Eg
🔴 Не в сети AgADJWgAAstr8Ug
🟤 Circle AgADrooAAunT8Eg
✅ Галочка 20 AgADBnYAAkCk8Eg
✅ Галочка 21 AgADCnMAArXj6Ug
✅ Галочка 22 AgADf28AAs348Ug
✅ Галочка 23 AgADeHIAAiSu8Eg
✅ Галочка 24 AgAD2m0AAmkG8Ug
✅ Галочка 25 AgADH24AAng58Eg
✅ Галочка 26 AgAD22sAAs0_8Eg
✅ Галочка 27 AgAD1HUAAo4q8Ug
🔢 Numbers AgADOWcAAkZr8Eg
🔢 Numbers AgADIHIAAqQg8Ug
🔢 Numbers AgAD8WsAAn558Eg
🔢 Numbers AgADz3MAAoDc8Ug
🔢 Numbers AgADg2QAAmQI8Ug
🔢 Numbers AgAD7W4AAjuk8Eg
🔢 Numbers AgADt2gAAoe-8Eg
🔢 Numbers AgADS2sAAjT08Eg
🔢 Numbers AgADRHIAAsxI8Eg
🔢 Numbers AgAEbQACQi3xSA
🔢 Numbers AgAD13cAAi9X8Eg
🔢 Numbers AgADD3kAAlr48Ug
🔢 Numbers AgADx20AAmKE8Ug
🔢 Numbers AgADgGgAAk948Ug
🔢 Numbers AgADgmsAAvSq8Eg
🔢 Numbers AgADmHAAAkqp8Ug
🔢 Numbers AgAD72wAAiDq8Ug
🔢 Numbers AgADW3IAAsys8Ug
🔢 Numbers AgADNm4AArQ28Ug
🔢 Numbers AgADS2wAAtWA8Eg
🔢 Numbers AgADcnQAArva8Eg
🔢 Numbers AgAD1HAAAnRN8Ug
🔢 Numbers AgADzXIAApU16Ug
🔢 Numbers AgADCnIAAjqx8Ug
🔢 Numbers AgADDmkAAsnL8Eg
🔢 Numbers AgADWGwAAtoN8Ug
🔢 Numbers AgADZ4gAAmbn8Ug
🔢 Numbers AgAD-HYAAr148Ug
🔢 Numbers AgAD-GsAArfz8Ug
🔢 Numbers AgADA2wAAlP48Eg
🔢 Numbers AgADGWoAAk3P8Eg
🔢 Numbers AgADfHIAAjSI8Ug
🔢 Numbers AgAD4WUAAmIc8Ug
🔢 Numbers AgADgGsAAmqC8Eg
🔢 Numbers AgAD-msAAtLE8Ug
🔢 Numbers AgADam0AAhJI8Eg
🔢 Numbers AgADqGsAAszZ8Eg
🔢 Numbers AgADumkAAkoS8Eg
🔢 Numbers AgADOXEAAvyY6Ug
🔢 Numbers AgADt2wAAiA08Eg
✈️ Отправить AgADRnMAAqS-8Ug
✈️ Telegram AgADimgAArLc8Ug
✈️ Рассылка AgADD3YAAgen8Eg
✈️ Перелёт AgADIW4AAltf8Eg
✅ Галочка 28 AgADe3IAAolk8Ug
✅ Галочка 29 AgADKXAAAt7J8Ug
✅ Галочка 30 AgADimgAAvCG8Ug
✅ Галочка 31 AgAD0W8AAoY88Eg
✅ Галочка 32 AgADPXIAAgeo8Eg
✅ Галочка 33 AgADpXEAAqhN8Eg
✅ Галочка 34 AgADHmoAAoeG8Ug
✅ Галочка 35 AgADUW0AAkjR8Ug
✅ Галочка 36 AgADJmwAAtLJ8Eg
✅ Галочка 37 AgADmWoAAnfx8Ug
✅ Галочка 38 AgADxnIAAhsu8Eg
✅ Галочка 39 AgADGHMAAlQ58Eg
✅ Галочка 40 AgADtGoAAk8E8Eg
✅ Галочка 41 AgAD620AAiSw8Eg
✅ Галочка 42 AgADamwAAkce6Eg
✅ Галочка 43 AgADN3EAAr-D8Eg
✅ Галочка 44 AgADfGkAAhjh8Eg
✅ Галочка 45 AgAD8WwAAg716Eg
✅ Галочка 46 AgADXG0AAgbe8Eg
✅ Галочка 47 AgADgm8AAjKc8Eg