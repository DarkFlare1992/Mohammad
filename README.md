import telebot
bot = telebot.TeleBot ('Token bot')


@bot.message_handler(commands= ['start'])
def start_message(message):
    bot.send_message(message.chat.id, 'Have you done morning exercise?') #reply_mrkup=inline_Keyboard
    bot.register_next_step_handler(message, morning_exercise ) 

def morning_exercise(message):
    answer = message.text
    bot.send_message(message.chat.id, 'OK Good Have you meditated for at least 10 minutes?')   
    bot.register_next_step_handler(message, meditation_10Min )

def meditation_10Min(message):
    ansswer2 = message.text
    bot.send_message (message.chat.id, 'OK Good work')

bot.polling()
