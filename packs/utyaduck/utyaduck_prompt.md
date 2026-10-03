# Премиум эмодзи для Telegram бота

Пак: Duck, https://t.me/addstickers/UtyaDuck (40 иконок)

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
        '<b><tg-emoji emoji-id="AgAD8gADVp29Cg">😂</tg-emoji> Отправь сообщение, которое нужно разослать всем пользователям.</b>',
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
        text="Kiss",
        url=CHANNEL_LINK,
        icon_custom_emoji_id="AgADBAEAAladvQo"
    )],
    [InlineKeyboardButton(
        text="Одобрить",
        callback_data="check_subscribe",
        icon_custom_emoji_id="AgAD_gADVp29Cg"
    )],
])
```

## Кнопки клавиатуры

Правило то же: в `text` без эмодзи, иконка в `icon_custom_emoji_id`. В aiogram это `KeyboardButton(text=..., icon_custom_emoji_id=...)`.

```python
keyboard = {
    "keyboard": [
        [
            {"text": "Joy", "icon_custom_emoji_id": "AgAD8gADVp29Cg"}
        ],
        [
            {"text": "Kiss", "icon_custom_emoji_id": "AgADBAEAAladvQo"},
            {"text": "Одобрить", "icon_custom_emoji_id": "AgAD_gADVp29Cg"}
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

## Список (40)

Формат строки: эмодзи Название ID. Эмодзи из начала строки ставь внутрь тега <tg-emoji>, ID идёт в emoji-id или icon_custom_emoji_id.

😂 Joy AgAD8gADVp29Cg
😘 Kiss AgADBAEAAladvQo
👍 Одобрить AgAD_gADVp29Cg
😱 Fear AgAD_wADVp29Cg
👋 Привет AgADAQEAAladvQo
😭 Face AgAD8wADVp29Cg
😳 Face AgAD9AADVp29Cg
😡 Face AgAD9QADVp29Cg
😈 Horns AgAD9gADVp29Cg
😎 Sunglasses AgAD9wADVp29Cg
🙄 Eyes AgAD-AADVp29Cg
🌈 Rainbow AgADBwEAAladvQo
🤷‍♂️ Shrug AgAD-QADVp29Cg
🔥 Огонь AgADBQEAAladvQo
🤤 Face AgAD-gADVp29Cg
😠 Face AgAD-wADVp29Cg
🤔 Face AgADAgEAAladvQo
🤑 Face AgADAwEAAladvQo
😏 Face AgADBgEAAladvQo
👌 Sign AgADCAEAAladvQo
🥶 Face AgADCQEAAladvQo
🤯 Head AgADCwEAAladvQo
👎 Дизлайк AgADDAEAAladvQo
🤗 Face AgADDQEAAladvQo
😴 Face AgADDgEAAladvQo
🦠 Microbe AgAD2gEAAladvQo
📨 Входящие AgADSAIAAladvQo
🤫 Lips AgADSQIAAladvQo
👯‍♀️ Ears AgADTwIAAladvQo
🥳 Hat AgADSgIAAladvQo
💪 Сила AgADryUAApuicEs
🤖 Боты AgADTgIAAladvQo
🛡 Щит AgADTQIAAladvQo
🧮 Abacus AgADSwIAAladvQo
🐯 Face AgADUAIAAladvQo
😘 Kiss AgADBQMAAladvQo
😂 Joy AgADex0AAkWOKUg
😢 Face AgADQxgAArbIKUg
🥳 Hat AgADXhgAAogOKEg
😭 Face AgADRh4AAvyUOEk