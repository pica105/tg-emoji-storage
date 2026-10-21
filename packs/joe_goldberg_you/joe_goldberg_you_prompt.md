# Премиум эмодзи для Telegram бота

Пак: Joe Goldberg | @Officer_friendly10, https://t.me/addstickers/Joe_goldberg_you (105 иконок)

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
        '<b><tg-emoji emoji-id="AgADiBgAAldAcVI">🧢</tg-emoji> Отправь сообщение, которое нужно разослать всем пользователям.</b>',
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
        text="Cap",
        url=CHANNEL_LINK,
        icon_custom_emoji_id="AgADMRYAAqh5cFI"
    )],
    [InlineKeyboardButton(
        text="Cap",
        callback_data="check_subscribe",
        icon_custom_emoji_id="AgADZBcAAlXkcFI"
    )],
])
```

## Кнопки клавиатуры

Правило то же: в `text` без эмодзи, иконка в `icon_custom_emoji_id`. В aiogram это `KeyboardButton(text=..., icon_custom_emoji_id=...)`.

```python
keyboard = {
    "keyboard": [
        [
            {"text": "Cap", "icon_custom_emoji_id": "AgADiBgAAldAcVI"}
        ],
        [
            {"text": "Cap", "icon_custom_emoji_id": "AgADMRYAAqh5cFI"},
            {"text": "Cap", "icon_custom_emoji_id": "AgADZBcAAlXkcFI"}
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

## Список (105)

Формат строки: эмодзи Название ID. Эмодзи из начала строки ставь внутрь тега <tg-emoji>, ID идёт в emoji-id или icon_custom_emoji_id.

🧢 Cap AgADiBgAAldAcVI
🧢 Cap AgADMRYAAqh5cFI
🧢 Cap AgADZBcAAlXkcFI
🧢 Cap AgADSxYAAv0zaVI
🧢 Cap AgAD-hUAAkmYcVI
🧢 Cap AgADNRUAAlNMcFI
🧢 Cap AgADgRUAAkWrcFI
🧢 Cap AgADaxoAAtd7cVI
🧢 Cap AgADchYAAkvDcFI
🧢 Cap AgADwhcAAmRpcVI
🧢 Cap AgADYBoAAquxcFI
🧢 Cap AgAD8RUAAqgVcFI
🧢 Cap AgADBhYAAtwtcVI
🧢 Cap AgADlRUAAjKAcVI
🧢 Cap AgADXRgAArh3cVI
🧢 Cap AgADyRYAAtXRcVI
🧢 Cap AgADMBkAAnJjcFI
🧢 Cap AgADDRgAAvmIcFI
🧢 Cap AgADSxgAAjuKcVI
🧢 Cap AgADexsAAsjDcFI
🧢 Cap AgADsBQAApfKcFI
🧢 Cap AgADbhQAAouIcFI
🧢 Cap AgAD3m4AAs5BaFI
🧢 Cap AgADFRgAAqLscVI
🧢 Cap AgADpxYAAjtjcVI
🧢 Cap AgADoBYAAgt-cFI
🧢 Cap AgAD4BYAAvMHcFI
🧢 Cap AgADuCQAAnQNcVI
🧢 Cap AgADfxUAAnQdcVI
🧢 Cap AgADkxcAAgfRcVI
🧢 Cap AgADtRYAAs9qaFI
🧢 Cap AgADPBgAAksMcFI
🧢 Cap AgADwxYAAlpvcVI
🧢 Cap AgADVRYAAgGIcVI
🧢 Cap AgADwBQAAgZEcFI
🧢 Cap AgAD1hcAAoNEcFI
🧢 Cap AgADvBcAAsU2cVI
🧢 Cap AgADjxgAAsjEcFI
🧢 Cap AgADbRYAAppQcVI
🧢 Cap AgADoBcAAvJTaFI
🧢 Cap AgADShgAAgqccVI
🧢 Cap AgADeh0AAjWKcFI
🧢 Cap AgADwxQAAr6WcFI
🧢 Cap AgADwhcAAn37aFI
🧢 Cap AgADhxUAAnXzcFI
🧢 Cap AgADjRYAAkNBcFI
🧢 Cap AgAD8xcAAlCkcFI
🧢 Cap AgAD3yIAAlo3cFI
🧢 Cap AgAD1h4AAuSzcVI
🧢 Cap AgADzRcAAq23cFI
🧢 Cap AgAD5BgAAg70cVI
🧢 Cap AgADBBcAAjt_cVI
🧢 Cap AgADZhYAAmqpaVI
🧢 Cap AgADCxYAAiywaFI
🧢 Cap AgAD_hUAAs_wcFI
🧢 Cap AgADIBoAAvNHcVI
🧢 Cap AgADIRwAAopqcVI
🧢 Cap AgADTBgAAqFlcFI
🧢 Cap AgADmhcAAq0icFI
🧢 Cap AgADtxYAAloDcVI
🧢 Cap AgADzRkAArh-OFA
🧢 Cap AgADnhsAAtLLOFA
🧢 Cap AgADO1YAAoUYOFA
🧢 Cap AgAD3RgAApYKOVA
🧢 Cap AgADbBsAAqwBMVA
🧢 Cap AgADNxwAAvIzOFA
🧢 Cap AgADDh4AAutDMVA
🧢 Cap AgAD6xkAAuoVMVA
🧢 Cap AgADXSUAAnxxOVA
🧢 Cap AgADRRkAAkTfMFA
🧢 Cap AgAD4hkAAh8bOVA
🧢 Cap AgADcBkAAlxaMVA
🧢 Cap AgAD9x8AAmtTOVA
🧢 Cap AgADGBkAAuiIOVA
🧢 Cap AgAD8xYAAuf8OVA
🧢 Cap AgADgBgAAjvGOVA
🧢 Cap AgADSBgAApn1OVA
🧢 Cap AgADnBsAAm6VOVA
🧢 Cap AgAD2xgAArXPOFA
🧢 Cap AgADLBwAAiuaOFA
🧢 Cap AgADnRkAArRyOFA
🧢 Cap AgADcxsAAgljOVA
🧢 Cap AgADIx0AAsluOVA
🧢 Cap AgADdBsAAtDNOVA
🧢 Cap AgADrBoAAjNxMFA
🧢 Cap AgAD9RgAAj5iOVA
🧢 Cap AgADmRsAAkvPOVA
🧢 Cap AgADVBsAAshaOVA
🧢 Cap AgADeBsAAhDtMVA
🧢 Cap AgADuBsAAhbpOFA
🧢 Cap AgADDhkAAt0aMVA
🧢 Cap AgADByEAAmLLOVA
🧢 Cap AgADaxwAAu8XOVA
🧢 Cap AgADyxsAArbnOVA
🧢 Cap AgAD0BsAAqjsMFA
🧢 Cap AgADoBsAAsQ4MFA
🧢 Cap AgADrhgAAoO2OFA
🧢 Cap AgAD7hoAAgNfOVA
🧢 Cap AgADeB0AAih1OVA
🧢 Cap AgADXhoAAgO7OVA
🧢 Cap AgADLRkAArjNMFA
🧢 Cap AgADJB0AAhpTOVA
🧢 Cap AgAD7RsAAoSTOFA
🧢 Cap AgADkxUAAgi0OFA
🧢 Cap AgAD9x0AAo1KMVA