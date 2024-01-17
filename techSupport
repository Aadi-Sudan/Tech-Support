import discord
import openai
import json
import pandas as pd

bot_token = 'ENTER YOUR DISCORD BOT TOKEN HERE'
openai_key = 'ENTER YOUR OPENAI API KEY HERE'
openai.api_key = openai_key

# Create an instance of the bot with command prefix '!'
intents = discord.Intents.default()  # Create a default set of intents
intents.message_content = True
bot = discord.Client(command_prefix="-", intents=intents, case_insensitive=True)

@bot.event
async def on_ready():
    print(f'{bot.user.name} is now running')

@bot.event
async def on_message(message):
    if message.author == bot.user:
        return  # Don't respond to messages from the bot itself

        # Use GPT-3 to generate a response
    if message.content.startswith("-ai"):
        prompt = message.content.replace("-ai", "").strip()
        response = openai.Completion.create(
            engine="text-davinci-002",
            prompt=prompt,
            max_tokens=150
        )

        await message.channel.send(response.choices[0].text)

bot.run(bot_token)
