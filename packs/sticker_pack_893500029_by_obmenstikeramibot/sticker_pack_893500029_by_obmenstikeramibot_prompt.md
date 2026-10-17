# Премиум эмодзи для Telegram бота

Пак: Больше тут | @obmenstickers, https://t.me/addstickers/sticker_pack_893500029_by_ObmenStikeramiBot (44 иконок)

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
        '<b><tg-emoji emoji-id="AgADBQkAAl4UCUU">🎈</tg-emoji> Отправь сообщение, которое нужно разослать всем пользователям.</b>',
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
        text="Шарик",
        url=CHANNEL_LINK,
        icon_custom_emoji_id="AgADXQcAAiQoEUU"
    )],
    [InlineKeyboardButton(
        text="Праздник",
        callback_data="check_subscribe",
        icon_custom_emoji_id="AgADIQgAAio8CEU"
    )],
])
```

## Кнопки клавиатуры

Правило то же: в `text` без эмодзи, иконка в `icon_custom_emoji_id`. В aiogram это `KeyboardButton(text=..., icon_custom_emoji_id=...)`.

```python
keyboard = {
    "keyboard": [
        [
            {"text": "Событие", "icon_custom_emoji_id": "AgADBQkAAl4UCUU"}
        ],
        [
            {"text": "Шарик", "icon_custom_emoji_id": "AgADXQcAAiQoEUU"},
            {"text": "Праздник", "icon_custom_emoji_id": "AgADIQgAAio8CEU"}
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

## Список (44)

Формат строки: эмодзи Название ID. Эмодзи из начала строки ставь внутрь тега <tg-emoji>, ID идёт в emoji-id или icon_custom_emoji_id.

🎈 Событие AgADBQkAAl4UCUU
🎈 Шарик AgADXQcAAiQoEUU
🎈 Праздник AgADIQgAAio8CEU
🎈 Праздник 4 AgAD1AYAAtmbEEU
🎈 Праздник 5 AgADuwcAArAGEUU
🎈 Праздник 6 AgAD6wYAAqzYEEU
🎈 Праздник 7 AgADSgcAAogHCUU
🎈 Праздник 9 AgADGggAAracCEU
🎈 Праздник 10 AgADBAkAAsvcCEU
🎈 Праздник 11 AgAD_AkAAtreCUU
🎈 Праздник 12 AgAD_gcAAnF7CUU
🎈 Праздник 13 AgADzAgAAgPQCEU
🎈 Праздник 14 AgADgQgAAhRGCEU
🎈 Праздник 15 AgADMgcAAqxjEEU
🎈 Праздник 16 AgADywsAAjRwEUU
🎈 Праздник 17 AgADDggAAgbECUU
🎈 Праздник 18 AgAD6AgAAuaDCEU
🎈 Праздник 19 AgAD6wYAAs_-CEU
🎈 Праздник 20 AgADaggAApMbCEU
🎈 Праздник 21 AgAD2gcAAhO_EUU
🎈 Праздник 22 AgADXwgAAvfqEUU
🎈 Праздник 23 AgADbQoAAkhMEUU
🎈 Праздник 24 AgAD7gYAAsGOCEU
🎈 Праздник 25 AgAD6QgAAtqACUU
🎈 Праздник 26 AgAD4wcAAmAqCUU
🎈 Праздник 27 AgADQgYAAvQLCUU
🎈 Праздник 28 AgADVwcAAjS9EEU
🎈 Праздник 29 AgADqwgAAkvbCEU
🎈 Праздник 30 AgADLQgAAuKuCUU
🎈 Праздник 31 AgADtQgAAgZ0CUU
🎈 Праздник 32 AgADeAcAAuj3CUU
🎈 Праздник 33 AgADuggAAoQ0CUU
🎈 Праздник 34 AgADRgkAAt0gCUU
🎈 Праздник 35 AgADPhAAAixlCUU
🎈 Праздник 36 AgADRgcAArrgCEU
🎈 Праздник 37 AgAD8AkAAllPCUU
🎈 Праздник 38 AgADaggAAkBqCUU
🎈 Праздник 39 AgAD0gcAAuIiEUU
🎈 Праздник 40 AgADEggAArckEUU
🎤 Микрофон AgADXggAAkQXEEU
😠 Face AgADCwgAAu32CUU
🙌 Celebration AgADSAgAAk4XCEU
🈵 Ideograph-6E80 AgADcAgAAk63EEU
🎧 Headphone AgADPQYAAjxkCEU