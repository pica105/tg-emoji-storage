# Премиум эмодзи для Telegram бота

Пак: Милые горячие парочки  @premstickery, https://t.me/addstickers/lovepacka_by_TgEmodziBot (34 иконок)

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
        '<b><tg-emoji emoji-id="AgAD8BsAAih5cVM">❤️</tg-emoji> Отправь сообщение, которое нужно разослать всем пользователям.</b>',
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
        text="Symbol",
        url=CHANNEL_LINK,
        icon_custom_emoji_id="AgADVh8AAvwAAXFT"
    )],
    [InlineKeyboardButton(
        text="Fear",
        callback_data="check_subscribe",
        icon_custom_emoji_id="AgADwigAAqAg6FE"
    )],
])
```

## Кнопки клавиатуры

Правило то же: в `text` без эмодзи, иконка в `icon_custom_emoji_id`. В aiogram это `KeyboardButton(text=..., icon_custom_emoji_id=...)`.

```python
keyboard = {
    "keyboard": [
        [
            {"text": "Лайк", "icon_custom_emoji_id": "AgAD8BsAAih5cVM"}
        ],
        [
            {"text": "Symbol", "icon_custom_emoji_id": "AgADVh8AAvwAAXFT"},
            {"text": "Fear", "icon_custom_emoji_id": "AgADwigAAqAg6FE"}
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

## Список (34)

Формат строки: эмодзи Название ID. Эмодзи из начала строки ставь внутрь тега <tg-emoji>, ID идёт в emoji-id или icon_custom_emoji_id.

❤️ Лайк AgAD8BsAAih5cVM
🔞 Symbol AgADVh8AAvwAAXFT
😱 Fear AgADwigAAqAg6FE
❤️ Сердце AgAD-B0AAhqncFM
🥰 Hearts AgAD1B8AAuOacFM
🥵 Face AgADchwAAmVzcFM
🔞 Symbol AgAD3RoAAlWreFM
🔞 Symbol AgAD3xwAAgFccFM
😡 Face AgADkiYAAnEmcVM
🥰 Hearts AgADGBsAAsGtcFM
❤️ Любовь AgADoR8AAsmSeVM
🔞 Symbol AgADCBkAAvyecFM
❤️ Любимое AgADWyEAAuFzcVM
❤️ Симпатия AgADzRwAAq56cFM
❤️ Избранное AgADThwAAio9cVM
❤️ Избранное 7 AgADbBoAAuZ2cFM
🥵 Face AgADrRwAAtQDcVM
❤️ Избранное 8 AgAD0B4AAvDLcVM
😏 Face AgAD7x4AAiZtcVM
❤️ Избранное 9 AgADth8AAlkPcVM
❤️ Избранное 10 AgADqB8AAqXfeVM
🔞 Symbol AgADRR8AAh0qeFM
🔞 Symbol AgADcxsAAujrcVM
❤️ Избранное 11 AgADTRkAAvEeeFM
❤️ Избранное 12 AgADyhwAAqU0cVM
❤️ Избранное 13 AgADRRwAAj6deFM
❤️ Избранное 14 AgADRCIAAhQpcFM
🔞 Symbol AgADbRwAApgmcFM
🥵 Face AgADFxkAAsdFcVM
🔞 Symbol AgADbh8AAm0acFM
💋 Поцелуй AgADzRsAAokucFM
💋 Губы AgADHR0AAmmlcVM
🔞 Symbol AgAD4BkAAuceeVM
🔞 Symbol AgADYxwAAq9zcFM