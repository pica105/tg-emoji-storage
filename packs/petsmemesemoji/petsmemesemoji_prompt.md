# Премиум эмодзи для Telegram бота

Пак: Pets Memes Emoji, https://t.me/addemoji/PetsMemesEmoji (15 иконок)

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
        '<b><tg-emoji emoji-id="5237691237124820624">😊</tg-emoji> Отправь сообщение, которое нужно разослать всем пользователям.</b>',
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
        text="Face",
        url=CHANNEL_LINK,
        icon_custom_emoji_id="5237888539332465017"
    )],
    [InlineKeyboardButton(
        text="Face",
        callback_data="check_subscribe",
        icon_custom_emoji_id="5237694986631270872"
    )],
])
```

## Кнопки клавиатуры

Правило то же: в `text` без эмодзи, иконка в `icon_custom_emoji_id`. В aiogram это `KeyboardButton(text=..., icon_custom_emoji_id=...)`.

```python
keyboard = {
    "keyboard": [
        [
            {"text": "Eyes", "icon_custom_emoji_id": "5237691237124820624"}
        ],
        [
            {"text": "Face", "icon_custom_emoji_id": "5237888539332465017"},
            {"text": "Face", "icon_custom_emoji_id": "5237694986631270872"}
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

## Список (15)

Формат строки: эмодзи Название ID. Эмодзи из начала строки ставь внутрь тега <tg-emoji>, ID идёт в emoji-id или icon_custom_emoji_id.

😊 Eyes 5237691237124820624
🤔 Face 5237888539332465017
😲 Face 5237694986631270872
😮 Mouth 5237829955978547322
🙃 Face 5238168687164279948
🕺 Танец 5237874361645417354
😩 Face 5312001713308191394
😭 Face 5339386257283764734
😎 Sunglasses 5355294343701747258
🤢 Face 5393215795369103883
😄 Eyes 5375293584037665784
🐹 Face 5375226170230987109
😺 Mouth 5373223594484587136
😢 Face 5386745190914482793
😕 Face 5386397131059782707