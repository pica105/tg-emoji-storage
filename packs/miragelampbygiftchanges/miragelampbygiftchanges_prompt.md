# Премиум эмодзи для Telegram бота

Пак: Mirage Lamp by @GiftChanges, https://t.me/addstickers/MirageLampByGiftChanges (52 иконок)

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
        '<b><tg-emoji emoji-id="AgADk6MAAqsd8Uk">🕯</tg-emoji> Отправь сообщение, которое нужно разослать всем пользователям.</b>',
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
        text="Candle",
        url=CHANNEL_LINK,
        icon_custom_emoji_id="AgAD0aoAAtVV8Ek"
    )],
    [InlineKeyboardButton(
        text="Candle",
        callback_data="check_subscribe",
        icon_custom_emoji_id="AgADjKAAAgHd8Ek"
    )],
])
```

## Кнопки клавиатуры

Правило то же: в `text` без эмодзи, иконка в `icon_custom_emoji_id`. В aiogram это `KeyboardButton(text=..., icon_custom_emoji_id=...)`.

```python
keyboard = {
    "keyboard": [
        [
            {"text": "Candle", "icon_custom_emoji_id": "AgADk6MAAqsd8Uk"}
        ],
        [
            {"text": "Candle", "icon_custom_emoji_id": "AgAD0aoAAtVV8Ek"},
            {"text": "Candle", "icon_custom_emoji_id": "AgADjKAAAgHd8Ek"}
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

## Список (52)

Формат строки: эмодзи Название ID. Эмодзи из начала строки ставь внутрь тега <tg-emoji>, ID идёт в emoji-id или icon_custom_emoji_id.

🕯 Candle AgADk6MAAqsd8Uk
🕯 Candle AgAD0aoAAtVV8Ek
🕯 Candle AgADjKAAAgHd8Ek
🕯 Candle AgADuqgAAnRv-Ek
🕯 Candle AgADO6EAAuKD8Uk
🕯 Candle AgADtacAAjib-Uk
🕯 Candle AgAD05wAAt3D8Ek
🕯 Candle AgADA6kAAm-0-Uk
🕯 Candle AgADyqUAAnhL-Uk
🕯 Candle AgADvaIAAvnE8Uk
🕯 Candle AgADjZ8AAj5p8Uk
🕯 Candle AgADKaIAAqML-Uk
🕯 Candle AgADUKsAAj37-Ek
🕯 Candle AgADwqYAAuxI8Uk
🕯 Candle AgAD6KEAAsLk-Uk
🕯 Candle AgADo64AAj8v-Uk
🕯 Candle AgADfqAAAl5N-Uk
🕯 Candle AgADjaYAAtUo8Uk
🕯 Candle AgADs6YAAuse8Ek
🕯 Candle AgADV6QAAlaf8Uk
🕯 Candle AgADt6sAAqbz8Ek
🕯 Candle AgADgKcAAgP1-Ek
🕯 Candle AgAD3q8AAiae8Ek
🕯 Candle AgADYakAAucT-Uk
🕯 Candle AgADqaMAAoCK8Uk
🕯 Candle AgAD8KsAAli1-Uk
🕯 Candle AgADPqMAAuzG8Ek
🕯 Candle AgADSaoAAqqd8Ek
🕯 Candle AgADGaMAAjO78Uk
🕯 Candle AgAD-agAArJx-Uk
🕯 Candle AgADG6sAAg4E-Ek
🕯 Candle AgAD5agAAhPt8Ek
🕯 Candle AgADZKUAAkei8Ek
🕯 Candle AgADsKwAAtpb-Ek
🕯 Candle AgADJP0AAvto8Ek
🕯 Candle AgADtKYAAkNg8Ek
🕯 Candle AgAD_KoAAvKX-Ek
🕯 Candle AgADLbMAAk_4-Uk
🕯 Candle AgADWqEAArrx8Ek
🕯 Candle AgADs6kAAmV4-Uk
🕯 Candle AgADDagAApAS8Ek
🕯 Candle AgADEqUAAvuf8Uk
🕯 Candle AgADlqAAAsw28Uk
🕯 Candle AgADs64AAske-Uk
🕯 Candle AgAD2KMAAtLj8Ek
🕯 Candle AgADCqwAAovM8Ek
🕯 Candle AgADRKMAAh9m-Ek
🕯 Candle AgADO50AAojp8Ek
🕯 Candle AgADuK8AArI38Uk
🕯 Candle AgADUaQAAoQh-Ek
🕯 Candle AgADEakAAmSv8Ek
🕯 Candle AgADCaMAAtfI8Uk