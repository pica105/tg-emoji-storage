# Премиум эмодзи для Telegram бота

Пак: Anton Chigurh @EdenGate, https://t.me/addstickers/ChigurhAnton (45 иконок)

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
        '<b><tg-emoji emoji-id="AgADLB8AAmNowFA">🪙</tg-emoji> Отправь сообщение, которое нужно разослать всем пользователям.</b>',
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
        text="Баланс",
        url=CHANNEL_LINK,
        icon_custom_emoji_id="AgADIRkAAnvguFA"
    )],
    [InlineKeyboardButton(
        text="Крипта",
        callback_data="check_subscribe",
        icon_custom_emoji_id="AgAD8RcAAq6_uVA"
    )],
])
```

## Кнопки клавиатуры

Правило то же: в `text` без эмодзи, иконка в `icon_custom_emoji_id`. В aiogram это `KeyboardButton(text=..., icon_custom_emoji_id=...)`.

```python
keyboard = {
    "keyboard": [
        [
            {"text": "Монеты", "icon_custom_emoji_id": "AgADLB8AAmNowFA"}
        ],
        [
            {"text": "Баланс", "icon_custom_emoji_id": "AgADIRkAAnvguFA"},
            {"text": "Крипта", "icon_custom_emoji_id": "AgAD8RcAAq6_uVA"}
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

## Список (45)

Формат строки: эмодзи Название ID. Эмодзи из начала строки ставь внутрь тега <tg-emoji>, ID идёт в emoji-id или icon_custom_emoji_id.

🪙 Монеты AgADLB8AAmNowFA
🪙 Баланс AgADIRkAAnvguFA
🪙 Крипта AgAD8RcAAq6_uVA
🪙 Бонусы AgADFhwAAjX-uVA
🪙 Токены AgADjhYAAjF-uVA
🪙 Токены 6 AgADtRcAAq0DwVA
🪙 Токены 7 AgADCBcAAq6IuVA
🪙 Токены 8 AgADnxcAAlN0uFA
🪙 Токены 9 AgADORsAAnWGuVA
🪙 Токены 10 AgAD8BgAAvOwuVA
🪙 Токены 11 AgAD_hYAArjDwVA
🪙 Токены 12 AgADfxoAAq9OuFA
🪙 Токены 13 AgADiBsAAp7ouFA
🪙 Токены 14 AgADgxYAAllAuFA
🪙 Токены 15 AgADnRkAAkQ8uVA
🪙 Токены 16 AgADCRgAAr9BuFA
🪙 Токены 17 AgAD8CwAAr7BuVA
🪙 Токены 18 AgADMhkAAvXcuFA
🪙 Токены 19 AgADxxYAAhnQuFA
🪙 Токены 20 AgAD4RcAAuDzuFA
🪙 Токены 21 AgADpBkAAmlJuFA
🪙 Токены 22 AgADbhoAAmfxuVA
🪙 Токены 23 AgAD7xcAAlj5wFA
🪙 Токены 24 AgADARoAAjdQwFA
🪙 Токены 25 AgADkxkAAtHJuFA
🪙 Токены 26 AgAD8BgAAg7euFA
🪙 Токены 27 AgADhRcAAqq3uFA
🪙 Токены 28 AgADvxgAAoB0uVA
🪙 Токены 29 AgADRRYAAvQiuFA
🪙 Токены 30 AgADwhcAAqB2uVA
🪙 Токены 31 AgADCBcAAibXuVA
🪙 Токены 32 AgADaRwAApGzwVA
🪙 Токены 33 AgADORoAAqTnuFA
🪙 Токены 34 AgADexUAAoPKwVA
🪙 Токены 35 AgADSBgAApsGuVA
🪙 Токены 36 AgADxRoAAlOUwFA
🪙 Токены 37 AgADSxcAAhXtuFA
🪙 Токены 38 AgADChwAAm3hwFA
🪙 Токены 39 AgADZxkAAjy1wVA
🪙 Токены 40 AgADEhYAAqlZwFA
🪙 Токены 41 AgAD6xoAAjLFuFA
🪙 Токены 42 AgAD8xYAAnMmwFA
🪙 Токены 43 AgADPhcAAqXIuVA
🪙 Токены 44 AgADeBsAAruguFA
🪙 Токены 45 AgADjxcAAvqcuFA