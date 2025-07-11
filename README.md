# python-telegram-bot
python-telegram-bot
from telegram import Update
from telegram.ext import ApplicationBuilder, CommandHandler, MessageHandler, ContextTypes, filters

# Ответ на команду /start
async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text("Привет! Я простой Telegram-бот.")

# Ответ на любое текстовое сообщение
async def echo(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text("Привет!")

def main():
    app = ApplicationBuilder().token("YOUR_BOT_TOKEN_HERE").build()

    app.add_handler(CommandHandler("start", start))
    app.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, echo))

    app.run_polling()

if __name__ == "__main__":
    main()
