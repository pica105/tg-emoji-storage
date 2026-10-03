# Премиум эмодзи для Telegram бота

Пак: Арсен Маркарян by @HonexBaby :: @fStikBot, https://t.me/addstickers/arsenmarkaryanbyhonexbaby_by_fStikBot (50 иконок)

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
        '<b><tg-emoji emoji-id="AgADckgAAojU6Eg">🌟</tg-emoji> Отправь сообщение, которое нужно разослать всем пользователям.</b>',
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
        text="Премиум",
        url=CHANNEL_LINK,
        icon_custom_emoji_id="AgAD6EwAAoMe4Ug"
    )],
    [InlineKeyboardButton(
        text="Сияние",
        callback_data="check_subscribe",
        icon_custom_emoji_id="AgADnUcAAkL24Ug"
    )],
])
```

## Кнопки клавиатуры

Правило то же: в `text` без эмодзи, иконка в `icon_custom_emoji_id`. В aiogram это `KeyboardButton(text=..., icon_custom_emoji_id=...)`.

```python
keyboard = {
    "keyboard": [
        [
            {"text": "Успех", "icon_custom_emoji_id": "AgADckgAAojU6Eg"}
        ],
        [
            {"text": "Премиум", "icon_custom_emoji_id": "AgAD6EwAAoMe4Ug"},
            {"text": "Сияние", "icon_custom_emoji_id": "AgADnUcAAkL24Ug"}
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

## Список (50)

Формат строки: эмодзи Название ID. Эмодзи из начала строки ставь внутрь тега <tg-emoji>, ID идёт в emoji-id или icon_custom_emoji_id.

🌟 Успех AgADckgAAojU6Eg
🌟 Премиум AgAD6EwAAoMe4Ug
🌟 Сияние AgADnUcAAkL24Ug
🌟 Особое AgADPk0AAqbe4Ug
🌟 Звезда AgADok0AAi-A4Ug
🥰 Hearts AgADu0YAAkvO6Ug
🫢 Иконка 7 AgADI08AAuR84Ug
🌟 Звезда 6 AgADZEwAAiTd4Eg
🌟 Звезда 7 AgADNEoAAvjC4Eg
🌟 Звезда 8 AgADn0UAAii14Eg
🌟 Звезда 9 AgADKk8AAqRA4Ug
🌟 Звезда 10 AgADEU0AAkIt6Eg
🌟 Звезда 11 AgAD8WUAApfT4Ug
🌟 Звезда 12 AgADCkkAAoPA4Eg
🌟 Звезда 13 AgADFVAAAp5I4Eg
🌟 Звезда 14 AgADhEYAAucB4Eg
🌟 Звезда 15 AgAD6k0AAl7n4Eg
🌟 Звезда 16 AgADdUkAAhxB4Ug
🌟 Звезда 17 AgADC0sAAs8K4Ug
🌟 Звезда 18 AgADLE0AAioh4Ug
🌟 Звезда 19 AgADCj8AAs4q6Eg
🌟 Звезда 20 AgAD6k8AAie_4Eg
🌟 Звезда 21 AgADrk4AAmXo4Eg
🌟 Звезда 22 AgADLUYAAt7P4Ug
🌟 Звезда 23 AgADpEkAAgbW6Ug
😳 Face AgADT1QAAotO4Ug
🐵 Face AgADv3wAAlvR4Eg
🥷 Скрытный AgAD30EAAuYO6Eg
🌟 Звезда 24 AgADB1MAAtUl4Ug
🌟 Звезда 25 AgADmUoAAkT34Ug
🌟 Звезда 26 AgADLkwAAgwf4Ug
🌟 Звезда 27 AgADaE0AAuou4Eg
🌟 Звезда 28 AgADbVEAAlX34Ug
🌟 Звезда 29 AgADdEwAAlgj6Eg
🌟 Звезда 30 AgADd0IAAnox6Ug
🌟 Звезда 31 AgADxUcAAjKX6Eg
🌟 Звезда 32 AgAD-EMAAgfU8Ug
🌟 Звезда 33 AgAD1UUAArIS-Ug
🌟 Звезда 34 AgAD20cAAjy_-Ug
🌟 Звезда 35 AgADwUIAAo1s-Eg
🌟 Звезда 36 AgADLEsAAgiF8Eg
🌟 Звезда 37 AgAD7EcAAgIG-Ug
🌟 Звезда 38 AgAD5EEAAnAc8Eg
🌟 Звезда 39 AgADVU8AApx9-Ug
🌟 Звезда 40 AgADME8AAhp6UEo
😳 Face AgADlk0AAswdoEo
👏 Sign AgADMUwAAvILoEo
😂 Joy AgAD7FQAAuvSkUg
🤫 Lips AgADR1MAApWFkUg
🥴 Mouth AgADnUkAArq8kUg