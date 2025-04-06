#ECObot

import telebot
import os
import requests
import random
bot = telebot.TeleBot("ТОКЕН")

## Обработчик команды '/start' и '/hello'
@bot.message_handler(commands=['start', 'hello'])
def send_welcome(message):
    bot.reply_to(message, 'Привет! Я бот ECO_ALENAbot! Напиши /help, чтобы узнать что я умею')
    
![start](https://github.com/user-attachments/assets/ffb96346-2fd9-4164-bb84-e0b00497adcf)


## Обработчик команды '/help'
@bot.message_handler(commands=['help'])
def send_welcome(message):
    bot.reply_to(message, "Привет, напиши /ECO_sovet, чтобы узнать экологичные советы; напиши /rubbish, чтобы узнать куда правильно сдавать мусор; напиши /eco_action, чтобы поучаствовать в акциях; напиши /ECOnom, чтобы получить советы, по экономии природных ресурсов.")
    
![help](https://github.com/user-attachments/assets/41aa9e55-025a-4274-b08b-32b44cf77b70)

## Обработчик команды '/ECO_sovet'
def gen_sovet():
    soveti = ["Сдайте батарейки и лампочки в пункт переработки", "устройте день без автомобиля", "используйте бумажные пакеты вместо пластиковых", "посадите дерево"]
    return random.choice(soveti)

@bot.message_handler(commands=['ECO_sovet'])
def vernut_sovet(message):
    back_sovet = gen_sovet()
    bot.reply_to(message, back_sovet)

![ECO_sovet](https://github.com/user-attachments/assets/3b8d08be-a61a-49aa-b153-668cba71b5c6)

## Обработчик команды '/rubbish'
def gen_fact():
    facti = ["бумагу помещайте в синие контейнеры", "пищевые отходы помещайте в коричневые контейнеры", "пластик помещайте в оранжевые контейнеры", "стекло помещайте в зелёные контейнеры", "металл сдавайте в специальные пункты приёма"]
    return random.choice(facti)

@bot.message_handler(commands=['rubbish'])
def vernut_fact(message):
    back_fact = gen_fact()
    bot.reply_to(message, back_fact)

![rubbish](https://github.com/user-attachments/assets/f776e6c8-313c-42f9-9f3b-29486712bd6f)


## Обработчик команды '/eco_action'
@bot.message_handler(commands=['eco_action'])
def vernut_ssilky(message):
    bot.reply_to(message, "https://ecowiki.ru/ - это ссылка на сайт, где можно узнать о местах проведения экологических акций 🌏😘")

![eco_action](https://github.com/user-attachments/assets/d816ac3f-24e6-4f6f-8c94-fb6558fedbf5)


## Обработчик команды '/ECOnom'
def gen_econom_sovet():
    e_soveti = ["не включайте свет, когда светло", "закрывайте кран, когда вам не нужна вода", "полностью наполняйте стиральную машину", "используйте многоразовую посуду", "ходите в магазин с многоразовой сумкой", "замените обычные лампы на энергосберегающие", "выключайте из разетки всю неиспользуемую бытовую технику", "при использовании бытовой техники пользуйтесь программами экономичных режимов", "поставьте холодильник подальше от тепла и чаще мойте уплотнитель на его двери", "отремонтируйте сантехнику"]
    return random.choice(e_soveti)

@bot.message_handler(commands=['ECOnom'])
def vernut_econom_sovet(message):
    econom_back_sovet = gen_econom_sovet()
    bot.reply_to(message, econom_back_sovet)

![ECOnom](https://github.com/user-attachments/assets/ad3bc212-cc32-49cb-971f-c61417f603d7)


if __name__ == "__main__":
    bot.polling(none_stop=True)

bot.infinity_polling()
