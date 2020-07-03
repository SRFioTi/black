const app = require('express')();
const TelegramBot = require('node-telegram-bot-api');
const axios1 = require('axios')
app.listen(3000);
app.get("/", (req, res)=>(res.send("hello world")))

const bot = new TelegramBot('1373705317:AAGhVOjat6Pxfk_UTxFeOuA656La_FA5OCk',{polling:true});

bot.onText(/\/cpf (.+)/, (msg, match) => {

  const chatId = msg.chat.id;
  const resp = match[1]; 
		axios1.get(`https://fiotissh.stne.xyz/puxar.php?lista=${resp}`).then(function(resposta){
		console.log(resposta.data)
		bot.sendMessage(chatId, resposta.data);
		});
});
