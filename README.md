# Hate-speech-detection-telegram-bot

Hate speech detection telegram bot using Hierarchical Attention Networks (HAN)

## Hate speech detection telegram bot using Hierarchical Attention Networks (HAN)

<!--#![hatespeechbot](https://user-images.githubusercontent.com/53829167/95406020-5c936b00-0954-11eb-9ba7-f9110b95b2cb.png)-->
<div>
 <img align="right" style="float: right;" width="200" src="https://user-images.githubusercontent.com/53829167/95406020-5c936b00-0954-11eb-9ba7-f9110b95b2cb.png">
</div>

### Features

- Detect whether the sentence is hate speech or not
- Explain why the machine came to judge the sentence as hate speech.

We presented an example sentence and an output image together to explain which part of the sentence played a major role in judging hate expressions. If the example sentence is not hate speech, nothing is appeared because the bot judged that it is not hate speech. On the other hand, in the case of the hate speech sentence, our bot prints the visualized image that highlights the key words. For instance, if you use the word "I hate you", the bot outputs an image by highlighting the word "hate" in the sentence.

In addition, it also contains a visualization at the document level. Multiple sentences entered by the user at once can be called a document. Among these sentences, our bot can find which one is played a more important role in judging hate speech. For example, if user types two sentences such as "Everyone loves you. But I hate you.", the bot prints an image by highlighting the sentence "But I hate you." In short, our bot can provide not only finding important words in sentences, but also gives the important sentences in documents. It is possible because of the feature of the hierarchical attention network (HAN) that we used for training the hate speech detection bot.

<!--
You can stop getting these automatic updates by sending `/quiet`:
<img src="images/IMG-7.JPG" alt="IMG-7" width="300"/>
-->
<!--
To turn updates back on, send `/start` again.
At any time (even on quiet mode), send `/status` to get the update of the latest epoch:
<img src="images/IMG-8.JPG" alt="IMG-8" width="300"/>
-->
<!--
##### Modifying the learning rate:
If your model's convergence plateaus, and you want to change the learning rate of your optimizer, simply send `/setlr`:
<img src="images/IMG-9.JPG" alt="IMG-9" width="300"/><br>
<img src="images/IMG-10.JPG" alt="IMG-10" width="300"/>

<!--
##### Plotting convergence graphs
To get a convergence plot of the loss, send `/plot` from the app:
 <img src="images/IMG-12.JPG" alt="IMG-12" width="300"/>
-->
<!--
##### Stop training process
If you want, you can stop your training process from the app. Just send `/stoptraining` and click on the Yes button.
With the Keras callback, training is stopped safely. Other operations that needed to happen after training will still take place:
<img src="images/IMG-13.JPG" alt="IMG-13" width="300"/>
-->

### Dependencies

- [python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot)
- Keras (optional, if you want to use the Keras callback)
- matplotlib (optional, to send convergence plots )

Tested in the following environment:

- Python 3.5
- Tensorflow 1.11
- Keras 2.2.4
- Mac OS

### Installation

1. Install [python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot):  
   `$ pip install python-telegram-bot --upgrade`
2. Clone this repository

3. Add `dl_bot.py` to your project

<!--### Usage
First, create a Telegram bot using the Telegram app.
It is very simple, just follow the steps in the dedicated section below.
Once you have created your bot, search for it and start a conversation with it on the Telegram app.
You can supply a `user_id` to restrict interaction with your bot only to a specific user. This is highly recommended.
(Instructions on how to find your user id are provided below)
You can either use the Keras callback to automatically interact with the bot, or to customize the interactions yourself.
__Note that the bot will start sending messages only after you send it the `/start` message from the app.__
-->
<!--
#### Keras Callback
The following block is all you need in order to use the Keras Telegram bot callback:
```python
# Telegram Bot imports
from dl_bot import DLBot
from telegram_bot_callback import TelegramBotCallback
<!--
telegram_token = "TOKEN"  # replace TOKEN with your bot's token
<!--
#  user id is optional, however highly recommended as it limits the access to you alone.
telegram_user_id = None  # replace None with your telegram user id (integer):
<!--
# Create a DLBot instance
bot = DLBot(token=telegram_token, user_id=telegram_user_id)
# Create a TelegramBotCallback instance
telegram_callback = TelegramBotCallback(bot)
```
Just add `telegram_callback` to the list of callbacks passed to model.fit:
```python
model.fit(x_train, y_train,
          batch_size=batch_size,
          epochs=epochs,
          verbose=1,
          validation_data=(x_test, y_test),
          callbacks=[telegram_callback])
```
<!--
That's all, you are good to go!
__An example usage is included in `keras_mnist_example.py`__
#### Custom messages
If you are using TensorFlow (or using Keras and want to customize interactions with the bot). Start by including the following code in your script:
-->

```python
# Telegram Bot imports
from dl_bot import DLBot

telegram_token = "TOKEN"  # replace TOKEN with your bot's token

# user id is optional, however highly recommended as it limits the access to you alone.
telegram_user_id = None   # replace None with your telegram user id (integer):

# Create a DLBot instance
bot = DLBot(token=telegram_token, user_id=telegram_user_id)
# Activate the bot
bot.activate_bot()
```

<!--
Then you will need to implement responses for the `/setlr`, `/getlr`, `/status`, `/stoptraining`,`/quiet` messages.
Also, you will need to send the bot the loss values each epoch in order to use the `/plot` command.
It is fairly easy to include these responses, a full example is included in `tf_mnist_example.py`
### Examples
Implementation examples are included for both Keras and TensorFlow in `keras_mnist_example.py` and `tf_mnist_example.py`.
Both examples include all bot functions over the official keras/tf MNIST examples.
-->

##### Creating a Telegram bot

To create a Telegram bot using the Telegram app, follow these steps:

1. Open the Telegram app
2. Search for the BotFather user (@botfather):


   <img width="409" alt="그림1" src="https://user-images.githubusercontent.com/53829167/95413397-45f60f80-0966-11eb-890a-82e0a6655029.png">
3. Start a conversation with BotFather and click on `start`

4. Send /newbot and follow instructions on screen:

   <img width="327" alt="그림2" src="https://user-images.githubusercontent.com/53829167/95407640-8fd7f900-0958-11eb-9933-d9e235ca7abf.png">
   
5. Copy the bot token, you will need it when using the DL-Bot:  


   <img width="414" alt="그림3" src="https://user-images.githubusercontent.com/53829167/95407701-b7c75c80-0958-11eb-8b22-7e44fc62d341.png">

##### Finding your Telegram user id:

1. Open the Telegram app
2. Search for the userinfobot user (@smilespeech):


   <img width="409" alt="그림4" src="https://user-images.githubusercontent.com/53829167/95408618-d4649400-095a-11eb-9574-57af4db472c4.png">
   
   
3. Start a conversation with the bot and get your user id

### References

- [Telegram bots documentation](https://core.telegram.org/bots)
