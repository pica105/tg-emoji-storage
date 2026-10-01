# Премиум эмодзи для Telegram бота

Пак: R2-DOG2, https://t.me/addstickers/r2dog2 (27 иконок)

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
        '<b><tg-emoji emoji-id="AgADNj8AAvw3SEk">😎</tg-emoji> Отправь сообщение, которое нужно разослать всем пользователям.</b>',
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
        text="Поцелуй",
        url=CHANNEL_LINK,
        icon_custom_emoji_id="AgADRzkAAl5WcUo"
    )],
    [InlineKeyboardButton(
        text="Одобрить",
        callback_data="check_subscribe",
        icon_custom_emoji_id="AgADNS0AAm4DKEo"
    )],
])
```

## Кнопки клавиатуры

Правило то же: в `text` без эмодзи, иконка в `icon_custom_emoji_id`. В aiogram это `KeyboardButton(text=..., icon_custom_emoji_id=...)`.

```python
keyboard = {
    "keyboard": [
        [
            {"text": "Sunglasses", "icon_custom_emoji_id": "AgADNj8AAvw3SEk"}
        ],
        [
            {"text": "Поцелуй", "icon_custom_emoji_id": "AgADRzkAAl5WcUo"},
            {"text": "Одобрить", "icon_custom_emoji_id": "AgADNS0AAm4DKEo"}
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

## Список (27)

Формат строки: эмодзи Название ID. Эмодзи из начала строки ставь внутрь тега <tg-emoji>, ID идёт в emoji-id или icon_custom_emoji_id.

😎 Sunglasses AgADNj8AAvw3SEk
💋 Поцелуй AgADRzkAAl5WcUo
👍 Одобрить AgADNS0AAm4DKEo
🤯 Head AgADcTsAArVDWUo
👋 Привет AgADMTQAAugboEo
👌 Sign AgAD5zUAAraMQUs
🤌 Fingers AgAD7DYAArtJMUo
🥹 Tears AgADrj4AApxtSEk
😡 Face AgADLDEAAlf4QEs
❤️ Лайк AgADJS0AAgNPSEs
👎 Дизлайк AgAD80EAAm-zaEk
☑️ Выбрано AgADwz0AAswTKUo
🖕 Дерзко AgADLTUAAvz_kEo
🤫 Lips AgADLT0AAoh1SUk
❓ Помощь AgAD1DAAApkwoUo
😴 Face AgADpkMAAlvDKEo
🥺 Умиление AgADrT8AAuoxMEo
🏃 Runner AgADEjUAAsenoUo
😖 Face AgADITgAAqctoUo
🤦‍♂️ Palm AgADHD0AAsldkUk
💸 Wings AgADfz0AAi3JKUo
🦾 Arm AgADTTYAAvfSsEk
💩 Poo AgADSzoAAvloKEo
🤡 Face AgADAzYAAgjOMEo
👨‍💻 Man AgAD3T4AAkAtSEk
🥳 Hat AgADS0cAAoA_YEk
🤔 Face AgADeEYAAi41eEk