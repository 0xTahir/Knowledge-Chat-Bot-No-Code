# Knowledge Chat Bot (No Code)

Recently my customers was looking for a solution where on-field guys can search for answers related to their tasks and it was a perfect scenario to develop a Chat Bot. [Microsoft Bot Framework](https://dev.botframework.com/) has been available for quite some time now and its functionality is keep on getting enhanced with different aspect of Artificial Intelligence like speech recognition, face recognition etc. With recent [announcement](https://techcrunch.com/2017/12/13/microsoft-makes-azure-bot-service-generally-available/) of GA of [Azure Bot Services](https://azure.microsoft.com/en-us/services/bot-service/), now we have one place to develop, deploy and expose our intelligent bots to channels like Web, Skype, FB Messenger etc.

In this post, I will walk you through Azure Bot Services(https://docs.microsoft.com/en-us/Bot-Framework) to build and connect a bot but first we need to build our bot's brain and fill it with the knowledge using QnAMaker( http://qnamaker.ai). 

This post is divided into following three sections: 
1. Architecture
2. Building the Knowledge Base (KB)
3. Building the Chat Bot

**Note:** You need Azure subscription to build this bot.

## Architecture 

Following is the architecture of our solution where we will build a service (bot's brain) in QnA Maker and then fill it with our Knowledge Base. Then we will create our bot in Azure Bot Services and link it to the bot's brain (MyBotService) and then we can publish our bot via different channels. We can use Channels to display our bot inside a SharePoint Page, Skype, Teams, Facebook Messenger etc.

<img src="https://github.com/BotNinja/Knowledge-Chat-Bot-No-Code/blob/master/images/01.png" width="75%" height="75%">

## Building the Knowledge Base (KB) 

1. Log on to QnA Maker at https://qnamaker.ai.
2. Select **Create New Service** tab and provide name of the bot service e.g. **MyBotService**, leave remaining fields as it is and hit **Create** button to create the service which will serve as brain of the bot.
<img src="https://github.com/BotNinja/Knowledge-Chat-Bot-No-Code/blob/master/images/02.png" width="75%" height="75%">
3. You should see the screen where you can provide the knowledge base for your bot. Add couple of questions and their answers by selecting **+ Add QnA Pair**. Once you add few QnA pairs, hit **Save and retrain** to train your model. You can also provide the questions and answers in text, pdf and document format.
<img src="https://github.com/BotNinja/Knowledge-Chat-Bot-No-Code/blob/master/images/03.png" width="75%" height="75%">

4. You can select **Test** tab to test the knowledge base in chat format.
5. Hit **Publish** once testing is done, and then hit **publish** again on the next screen to publish MyBotService to the web. We will consumed this service through our Bot.
6. Once the MyBotService is published, Save the two values highlighted in the screen shot below as **QnAKnowledgebaseId** and **QnASubscriptionKey**. We need this information in our Bot's settings.
<img src="https://github.com/BotNinja/Knowledge-Chat-Bot-No-Code/blob/master/images/04.png" width="75%" height="75%">

**Note:** You can access further documentation about QnA Maker at https://qnamaker.ai/Documentation.

## Building the Chat Bot 
1. Log on to Azure at http://portal.azure.com.
2. Select **New** and go to **AI + Cognitive Services** section and choose **Web App Bot**.

<img src="https://github.com/BotNinja/Knowledge-Chat-Bot-No-Code/blob/master/images/05.png" width="75%" height="75%">

3. Provide a unique Bot Name (e.g. DemoBot101), select **Subscription** and then choose **Bot template** as **Question and Answer**. You can also choose between C# or Node.js SDK which doesn't matter in this case as we are not writing any code. Select Create button at the end to create the Bot.
<img src="https://github.com/BotNinja/Knowledge-Chat-Bot-No-Code/blob/master/images/06.png" width="75%" height="75%">

4. Once the basic bot has been created you will be notified and select **Go to resources** from the notification section to see the Bot's details, settings etc.
<img src="https://github.com/BotNinja/Knowledge-Chat-Bot-No-Code/blob/master/images/07.png" width="75%" height="75%">

5. Select **Application Settings** of the bot and go to the **App settings** section and provide the value of the keys **QnAKnowledgebaseId** and **QnASubscriptionKey** which we copied while creating the MyBotService and hit **Save**.
<img src="https://github.com/BotNinja/Knowledge-Chat-Bot-No-Code/blob/master/images/08.png" width="75%" height="75%">

6. Now you can test the bot from **Test in Web Chat** tab.
<img src="https://github.com/BotNinja/Knowledge-Chat-Bot-No-Code/blob/master/images/09.png" width="75%" height="75%">

7. Once the testing is completed, this Chat Bot can be published to web, Skype, Teams, MSN Messenger etc via **Channels**.
<img src="https://github.com/BotNinja/Knowledge-Chat-Bot-No-Code/blob/master/images/10.png" width="75%" height="75%">

**Note:** You can access Azure Bot Services documentation here: https://azure.microsoft.com/en-us/services/bot-service
