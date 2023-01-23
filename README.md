using System;
using Telegram.Bot;
using Telegram.Bot.Types;

class program
{
    
    static void Main(string[] args)
    {
        var client = new TelegramBotClient("Токен ты где(Сюда надо вставить токен)");
        client.StartReceiving(Updata, Error);
        Console.ReadLine();
    }

    private static Task Error(ITelegramBotClient arg1, Exception arg2, CancellationToken arg3)
    {
        throw new NotImplementedException();
    }

    async private static Task Updata(ITelegramBotClient botClient, Update update, CancellationToken token)
    {
        var message = update.Message; 
        var chatId = message.Chat.Id;
        if (message.Text != null)
        {
            Console.WriteLine($"Пришло сообщение с текстом: {message.Text}");
        Message sentMessage = await botClient.SendTextMessageAsync
        (chatId: chatId,text: "Вы написали:\n" + message.Text);
        }
    }
}
