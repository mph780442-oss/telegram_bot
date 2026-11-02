import telebot
from telebot.types import ReactionTypeEmoji
import time
import random
import os

TOKEN = os.getenv("TOKEN")
SOURCE = -1004498374357
TARGET = -1004392399255

bot = telebot.TeleBot(TOKEN)
REACTIONS = ["🔥", "❤️", "👍","🥰","😍","🤩","🤗","✈️"]

def add_five_reactions(chat_id, msg_id):
    try:
        chosen = random.sample(REACTIONS, 5)
        acc = []
        for e in chosen:
            acc.append(ReactionTypeEmoji(e))
            bot.set_message_reaction(chat_id, msg_id, reaction=acc)
            time.sleep(1)
        return True
    except Exception as e:
        print(e)
        return False

bot.delete_webhook(drop_pending_updates=True)
print("Bot Started on Koyeb...")

@bot.channel_post_handler(content_types=['text','photo','video','document','audio','animation','voice'])
def forward(m):
    if m.chat.id == SOURCE:
        try:
            new_msg = bot.copy_message(TARGET, m.chat.id, m.message_id)
            time.sleep(1.5)
            add_five_reactions(TARGET, new_msg.message_id)
        except Exception as e:
            print(e)

bot.infinity_polling(skip_pending=True)
