# Премиум эмодзи для Telegram бота

Пак: Sticker pack @emojistikerybot, https://t.me/addstickers/Stikerytg1857_by_emojistikerybot (100 иконок)

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
        '<b><tg-emoji emoji-id="AgADG6QAApek6Eo">🙂</tg-emoji> Отправь сообщение, которое нужно разослать всем пользователям.</b>',
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
        text="Joy",
        url=CHANNEL_LINK,
        icon_custom_emoji_id="AgADwaIAAqkq6Uo"
    )],
    [InlineKeyboardButton(
        text="Arrow",
        callback_data="check_subscribe",
        icon_custom_emoji_id="AgADjqgAAjMk4Uo"
    )],
])
```

## Кнопки клавиатуры

Правило то же: в `text` без эмодзи, иконка в `icon_custom_emoji_id`. В aiogram это `KeyboardButton(text=..., icon_custom_emoji_id=...)`.

```python
keyboard = {
    "keyboard": [
        [
            {"text": "Улыбка", "icon_custom_emoji_id": "AgADG6QAApek6Eo"}
        ],
        [
            {"text": "Joy", "icon_custom_emoji_id": "AgADwaIAAqkq6Uo"},
            {"text": "Arrow", "icon_custom_emoji_id": "AgADjqgAAjMk4Uo"}
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

## Список (100)

Формат строки: эмодзи Название ID. Эмодзи из начала строки ставь внутрь тега <tg-emoji>, ID идёт в emoji-id или icon_custom_emoji_id.

🙂 Улыбка AgADG6QAApek6Eo
😂 Joy AgADwaIAAqkq6Uo
⬆️ Arrow AgADjqgAAjMk4Uo
😍 Eyes AgADe7YAAtS-6Eo
🔥 Огонь AgADLagAAnn66Uo
❤️ Лайк AgADPKgAAudA4Uo
👍 Одобрить AgADeJ4AAm386Eo
😎 Sunglasses AgAD6LUAAjVV4Eo
🥰 Hearts AgADpqMAAkSz6Eo
😱 Fear AgAD_50AAmZB6Eo
😭 Face AgADCaEAAkBk6Uo
🤩 Eyes AgADp50AAtnT4Eo
😇 Ангел AgADMroAAtbv4Uo
😈 Horns AgADL6IAApFR4Eo
🙃 Face AgADzpkAAu0Z6Uo
😉 Face AgADdqMAAofi6Eo
😋 Food AgADvasAAgcd4Uo
🤪 Eye AgADXKMAAj-o4Uo
😜 Eye AgADQKMAAsMx6Eo
😌 Релакс AgADLKkAAoCd4Uo
😳 Face AgADO64AAhde6Eo
😡 Face AgADGasAAkYL4Eo
🤯 Head AgADC54AAoG_4Uo
🥺 Умиление AgADiqkAAniq4Uo
👏 Sign AgADa6YAAp3q6Uo
💪 Сила AgADuqkAAvap4Eo
✨ Новинки AgADMrMAAq8s6Eo
⭐ Избранное AgADq6YAAitV6Eo
💯 Качество AgADnqkAAsJm4Eo
🎉 Вечеринка AgADM6EAAkaZ6Eo
🚀 Ракета AgADM5sAAvP44Uo
🐱 Кот AgADJaAAAgPU6Eo
🐶 Стикеры AgADAaAAAuHU4Uo
🌟 Успех AgADUbAAArXD6Eo
💫 Искры AgADhqQAAmn-4Uo
🎯 Hit AgADkaMAApLy6Uo
😴 Face AgADJKYAAjmL4Uo
🤗 Face AgADB6sAAjf86Eo
🫶 Руки сердечком AgADc6IAAmPC6Uo
😏 Face AgADzKkAAqjA4Uo
🤝 Партнёрство AgADBKcAAjXf6Uo
🎁 Present AgADea4AAt2c4Uo
🍀 Clover AgADVKUAAsAE4Uo
🌈 Rainbow AgAEtAAC3N7gSg
⚡ Молния AgADI68AAvjS6Eo
🌸 Blossom AgADLakAAtAd6Uo
🍓 Strawberry AgADo6UAAux_4Eo
💎 Премиум AgAD76kAAuiS6Eo
🧠 ИИ AgADltgAAmnb6Uo
🙂 Реакция AgADL6sAAjXD6Eo
😂 Joy AgAD0KMAAqeC6Uo
😍 Eyes AgADYqkAAi1n4Uo
🔥 Тренды AgADobMAAgKe4Uo
❤️ Сердце AgADDKUAAmXu4Uo
👍 Нравится AgAD_aUAAvea6Uo
😎 Sunglasses AgADJ68AAtpi6Uo
🥰 Hearts AgAD96kAAufV6Uo
😱 Fear AgADuKMAAn1X4Eo
😭 Face AgADQqwAAkAr4Uo
🤩 Eyes AgADtaMAAtqg6Eo
😇 Спокойствие AgADMqcAAmYw6Uo
😈 Horns AgADtagAAglv6Uo
🙃 Face AgADyKwAAoBF4Eo
😉 Face AgADc6MAApxI4Eo
😋 Food AgAD4KQAArDt6Eo
🤪 Eye AgADZKUAAgy16Eo
😜 Eye AgADjKQAAsvB4Uo
😌 Отдых AgADG6YAAkSA4Eo
😳 Face AgAD-ZwAAn3G6Uo
😡 Face AgADU7MAAu1d4Uo
🤯 Head AgADfaYAAlVB6Uo
🥺 Просьба AgAD4qUAAu6p4Uo
👏 Sign AgADNKwAAlwr6Uo
💪 Мощь AgADDacAAmCJ4Eo
✨ Магия AgADDaoAAtp84Eo
⭐ Рейтинг AgADza4AAiwa4Uo
💯 100% AgAD0awAAphj4Uo
🎉 Праздник AgADya0AAska4Uo
🚀 Запуск AgADgawAAnT04Uo
🐱 Кошка AgAD6qMAArCm4Uo
🐶 Собака AgADQ50AAvAz6Eo
🌟 Премиум AgADqqQAArCi6Uo
💫 Звёзды AgADbdUAApJA4Uo
🎯 Hit AgADN6kAAgTf6Eo
😴 Face AgADpqoAAj8g6Eo
🤗 Face AgADOq4AAv2m4Eo
🫶 Любовь AgADhaYAAjd54Eo
😏 Face AgADc60AAt5U4Uo
🤝 Сделка AgADPKsAAtO06Eo
🎁 Present AgADhakAAjx66Eo
🍀 Clover AgADVZ8AAmdT6Uo
🌈 Rainbow AgAD4q4AAteE4Eo
⚡ Быстро AgADdKUAAi6m6Uo
🌸 Blossom AgAD06oAAoxC4Uo
🍓 Strawberry AgAD_bIAAg204Uo
💎 VIP AgADEqMAAmoS6Eo
🧠 Разум AgADiZsAAoWp6Eo
🙂 Позитив AgAD25kAAn224Eo
😂 Joy AgADoKsAAjq96Eo
😍 Eyes AgADDqoAAnlD6Eo