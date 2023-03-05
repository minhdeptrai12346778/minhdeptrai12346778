import requests
from bs4 import BeautifulSoup
import asyncio
import telegram
url = ' ur url web u want to send'
bot = telegram.Bot(token='ur bot telegram token')
async def send_message():
    while True:
        response = requests.get(url)
        soup = BeautifulSoup(response.text, 'html.parser')
        news_div = soup.find('div', {'class': 'list_news'})
        news_links = news_div.find_all('a')
        for news_link in news_links:
            news_title = news_link.text.strip()
            news_href = news_link['href']
            await bot.send_message(chat_id='ur profile id in telegram', text=f"ur tittle u want to send imao:\n\n{news_title}\n{news_href}")
        await asyncio.sleep(3)
        
        
        
        
        #if u have bug just ask chatgpt lol
