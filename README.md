# COVID Crisis Communications: Sherlock's Watson Assistant

This solution starter was created by technologists from IBM. It is further extended for this idea by Sanker Akella

## Authors

- [Donna Byron](https://developer.ibm.com/profiles/dkbyron/) - IBM
- [John Walicki](https://developer.ibm.com/profiles/walicki/) - IBM
- [Matt Price](https://developer.ibm.com/profiles/pricem/) - IBM
- [Mofizur Rahman](https://developer.ibm.com/profiles/mofizur.rahman) - IBM
- [Pooja Mistry](https://developer.ibm.com/profiles/pmistry/) - IBM
- [Upkar Lidder](https://developer.ibm.com/profiles/ulidder/) - IBM

## Contents

1. [Overview](#overview)
2. [Video](#video)
3. [The idea](#the-idea)
4. [How it works](#how-it-works)
5. [Diagrams](#diagrams)
6. [Documents](#documents)
7. [Datasets](#datasets)
8. [Technology](#technology)
9. [Getting started](#getting-started)
10. [Resources](#resources)
11. [License](#license)

## Overview

### What's the problem?
Government is providing information about pandemic but people are not able to get the full picture as the information is scattered at various places. As an example, many get confused if they could park their cars on the yellow line or not. Do they get fined for that or parking rules are lifted temporarily to facilitate the lockdown. 
Secondly, there is too much information that people do get confused on what they could or could not do which is one of the causes of these many deaths or confirmed cases. Hence if they have a chat bot in hand which can help them answer their questions with accuracy, then there are high chances of people following the rules properly.

### Solution Approach ?

Before the smartphones entered the market, emails and chats were done online using laptops where the person has to physically go to the laptop or desktop and send that mail or chat. Since the smartphone evolution, apps started to get developed and as a result everything could be done with a click of a button. This has resulted in more online communication than before just because of accessibility and comfort of not going anywhere just to complete a small task.
I want to bring-in same concept. If my chatbot can do the hard work by searching all the information and provide accurate information to the user, then that’s a win-win situation. Hence multiple chats are assembled for this idea where the 1st chatbot is prepared on Node-Red for a user to type or speak out his question and in response the bot will output the result in text format as well as an audio output of the response. Along with that chat option, user can also check the latest statistics on Covid across various countries, graphical representation split at the level of counties.
Second chat bot is a facebook messenger which has dialog and search skills along with function integration for better refined results. Third app is a Slack bot for professionals where they can subscribe for the government guidelines. Final chatbot is a webhook which can be hooked to any website with admin privileges. The final one is very critical as the government websites do not have chat option and if government agrees, then that will be a great benefit.
In the roadmap I had watsapp, viber, Telegram and Twitter integration. Followed by push notification via twillio as we still have a good amount of people who doesn’t use smart phones (under 12s and over 60s). Finally, along with having the webhook on to government websites, a mobile app will be developed with all the features needed at the basic level and then that will be expanded to cater for advanced need of consumers.

## Roadmap
COVID-19 has citizens looking for answers about symptoms and testing sites as well as current status of schools, transportation, and other public services. Using Watson Assistant a virtual assistant is designed to understand and respond to common questions about COVID-19, scan COVID-19 news articles using Watson Discovery and respond to COVID statistics inquires with data from trusted sources. This is also integrated into a Slack integration or via a Node-RED Dashboard.

![Crisis Comms Roadmap diagram](/images/Roadmap.JPG)

The Roadmap contains:
•	The 1st phase (Informative Voice-enabled chatbot, slack channel, facebook messenger, webhook) is already ready to use.
•	Phase 2 is to extend the usage on to watsapp, viber, telegram, twitter and introduce the push notification via sms service using Twillio.
•	Phase 3 is to integrate my webhook on to government websites by seeking their approval.
•	Phase 4 is to build a mobile app based chat bot which will have latest features based on the feedback we’ll receive from the users on the previous phases.

## How it works

[![Sherlock's Watson Assistant](/images/Thumbnail.png)](https://www.youtube.com/watch?v=zoZbpbErK3I)

## Architectural Diagrams

![Crisis Comms Architectural Diagram](/images/Architectural_Diagram.jpg)

### Slack integration with COVID-19 crisis communication chatbot

![Crisis Comms Architecture diagram](/images/Crisis-Comms-Architecture-Slack-Integration.png)

1. User invokes a COVID-19 Slack integration chatbot app and asks a question.
2. Slack app calls the Watson Assistant service hosted in IBM Cloud.
3. Watson Assistant uses Search skill to connect to the Discovery's Web claw into gov.uk website to look for an appropriate response.
4. If the response has low confidence level, then Watson Assistant uses natural language understanding and machine learning to extract entities and intents of the user question.
5. Source COVID-19 FAQ information from trusted CDC data
6. Watson Assistant invokes an OpenWhisk open source powered IBM Cloud Function.
7. IBM Cloud Function calls the Watson Discovery service running in IBM Cloud.
8. Watson Discovery scans news articles and responds with relevant articles.
9. Watson Assistant invokes an OpenWhisk open source powered IBM Cloud Function.
10. IBM Cloud Function calls the COVID-19 API to get statistics.
11. Watson Assistant replies to the Slack application.
12. Slack app displays the chat answer to the user.

![Crisis Comms Slack Response](/images/Slack_Response.png)

### Facebook messenger integration with COVID-19 crisis communication chatbot

1. User invokes a COVID-19 Facebook messenger chatbot app and asks a question.
2. Messenger calls the Watson Assistant service hosted in IBM Cloud.
3. Watson Assistant uses Search skill to connect to the Discovery's Web claw into gov.uk website to look for an appropriate response.
4. If the response has low confidence level, then Watson Assistant uses natural language understanding and machine learning to extract entities and intents of the user question.
5. Source COVID-19 FAQ information from trusted CDC data
6. Watson Assistant invokes an OpenWhisk open source powered IBM Cloud Function.
7. IBM Cloud Function calls the Watson Discovery service running in IBM Cloud.
8. Watson Discovery scans news articles and responds with relevant articles.
9. Watson Assistant invokes an OpenWhisk open source powered IBM Cloud Function.
10. IBM Cloud Function calls the COVID-19 API to get statistics.
11. Watson Assistant replies to the facebook messenger application.
12. Messenger displays the chat answer to the user.

![Crisis Comms Slack Response](/images/Thumbnail.png)

### Voice enabled COVID-19 crisis communication chatbot using Node-RED

![Crisis Comms Architecture diagram](/images/Crisis-Comms-Architecture-Node-RED.png)

1. User visits a voice-enabled Node-RED website with the COVID-19 chatbot and asks a question.
2. Node-RED records the speech wav file and calls the Watson Speech to Text service hosted in IBM Cloud.
3. Watson Speech to Text uses machine learning to decode the user's speech.
4. Watson Speech to Text replies with a transcript of the COVID-19 question and Node-RED calls Watson Assistant service hosted in IBM Cloud.
5. Watson Assistant uses Search skill to connect to the Discovery's Web claw into gov.uk website to look for an appropriate response.
6. Watson Assistant uses natural language understanding and machine learning to extract entities and intents of the user's question.
7. Source COVID-19 FAQ information from trusted CDC data
8. Watson Assistant invokes an OpenWhisk open source powered IBM Cloud Function.
9. IBM Cloud Function calls the Watson Discovery service running in IBM Cloud.
10. Watson Discovery scans news articles and responds with relevant articles.
11. Watson Assistant invokes an OpenWhisk open source powered IBM Cloud Function.
12. IBM Cloud Function calls the COVID-19 API to get statistics.
13. Watson Assistant replies to the user inquiry and Node-RED sends the text transcript to Watson Text to Speech.
14. Watson Text to Speech encodes the message in the user's language.
15. Node-RED plays the chat answer wav file to the user.
16. User listens to the chat answer.The user can also see the graph of latest covid statistics, actual figures split by countries and Covid tracker where you can see the graph of each county.

![Crisis Comms Voice Chatbot](/images/Voice_Chatbot.png)
![Crisis Comms Tracker](/images/Tracker.png)

## Documents

### Trusted sources for COVID-19 information
- [CDC COVID-19 FAQ](https://www.cdc.gov/coronavirus/2019-ncov/faq.html)

### Tutorials and documentation:

- [How-to guides for chatbots](https://www.ibm.com/watson/how-to-build-a-chatbot)
- [Learning path: Getting started with Watson Assistant](https://developer.ibm.com/series/learning-path-watson-assistant/)
- [Chatbot with Watson Discovery](https://github.com/IBM/watson-discovery-sdu-with-assistant)
- [Chat Bot Slack Deployment](https://cloud.ibm.com/docs/assistant?topic=assistant-deploy-slack)
- [Node-RED Slack Integration](https://www.ibm.com/cloud/blog/create-a-chatbot-on-ibm-cloud-and-integrate-with-slack-part-1)
- [Train a speech-to-text model](https://developer.ibm.com/patterns/customize-and-continuously-train-your-own-watson-speech-service/)
- [Making Programmatic Calls from Watson Assistant](https://cloud.ibm.com/docs/assistant?topic=assistant-dialog-webhooks)
- [Watson Assistant](https://cloud.ibm.com/docs/assistant?topic=assistant-getting-started)

## Datasets

- [covid19api](https://covid19api.com/)

## Technology

### IBM technology

- [IBM Watson Assistant](https://www.ibm.com/cloud/watson-assistant/)
- [Watson Discovery](https://www.ibm.com/cloud/watson-discovery)
- [Watson Speech to Text](https://www.ibm.com/cloud/watson-speech-to-text)
- [Watson Text to Speech](https://www.ibm.com/cloud/watson-text-to-speech)
- [IBM Cloud Functions](https://cloud.ibm.com/functions/)

### Open source technology

- [Apache OpenWhisk](https://openwhisk.apache.org/)
- [Node-RED](https://nodered.org/)

## Getting started

### Prerequisite

- Log-in to IBM Cloud platform [IBM Cloud Platform](https://cloud.ibm.com/) with your own registered account.
- The account has to be at least a Plus account to use Watson Assistant - Search skills.

### Set up an instance of Watson Assistant

Log in to IBM Cloud and provision a Watson Assistant instance.

**Step 1.** From the [IBM Cloud catalog](https://cloud.ibm.com/catalog/services/watson-assistant), provision an an instance of **Watson Assistant**.
  ![Watson Assistant Catalog](/starter-kit/assistant/WA-Photo1.png)

**Step 2.**  Launch the Watson Assistant service.

**Step 3.** Click **Create assistant** and follow [these detailed instructions](https://cloud.ibm.com/docs/assistant?topic=assistant-assistant-add) for how to create an assistant.
  ![Watson Assistant Photo2 ](/starter-kit/assistant/WA-Photo2.png)

**Step 4.** Name the Watson Assistant instance **COVID Crisis Communication**
  ![Watson Assistant Photo3 ](/starter-kit/assistant/WA-Photo3.png)

**Step 5.** Click **Add Dialog skill** to add this to your assistant. Follow [the documentation](https://cloud.ibm.com/docs/assistant?topic=assistant-skill-dialog-add) if you have questions.
  ![Watson Assistant Photo4 ](/starter-kit/assistant/WA-Photo4.png)

**Step 6.** Click **Import skill > Choose JSON file** and import the [`skill-CDC-COVID-FAQ.json`](./starter-kit/assistant/skill-CDC-COVID-FAQ.json) file.
  ![Watson Assistant Photo5 ](/starter-kit/assistant/WA-Photo5.png)

**Step 7.** Go back to the All Assistants page. From the action menu ( **`⋮`** ), open **Settings**.
  ![Watson Assistant Photo6 ](/starter-kit/assistant/WA-Photo6.png)

**Step 8.**  On the Settings tab, click **API Details** on the left and make a note of the `Assistant ID` and `Api Key` for future use.
  ![Watson Assistant Photo7 ](/starter-kit/assistant/WA-Photo7.png)

**Step 9.** Go back to the All Assistants page and click on the **Skills** link.
  ![Watson Assistant Skills ](/starter-kit/assistant/WA-Skills.png)

**Step 10.** On the Skill page, click on the action menu ( **`⋮`** ), open **View API Details**.
  ![Watson Assistant Skill Properties](/starter-kit/assistant/WA-SkillAPIProperties.png)

**Step 11.** On the Skill Details page, make note of the `Skill ID` for future use.
  ![Watson Assistant Skill Details](/starter-kit/assistant/WA-SkillDetails.png)

**Step 12.**  Go back to your dialog skill and click on the **Preview Link** button on the side to get a link to test and verify your assistant.
  ![Watson Assistant Photo9 ](/starter-kit/assistant/WA-Photo91.png)

**Step 13.** Ask the Watson Assistant chatbot some questions about COVID-19.
<p align="center">
<img width="50%" height="50%" src="https://raw.githubusercontent.com/Call-for-Code/Solution-Starter-Kit-Communication-2020/master/starter-kit/assistant/WA-Photo101.png">
</p>


### Connect your chatbot to data sources via a webhook

Now that you’ve created your Watson Assistant-enabled chatbot, you need to connect it to a data source. With Watson Assistant, you need to do this via a webhook.

A webhook is a mechanism that allows you to call out to an external program based on something happening in your program. When used in a dialog skill, a webhook is triggered when the assistant processes a node that has a webhook enabled. The webhook collects data that you specify or that you collect from the user during the conversation and save in context variables. It sends the data as part of a HTTP POST request to the URL that you specify as part of your webhook definition. The URL that receives the webhook is the listener. It performs a predefined action using the information that you pass to it as specified in the webhook definition, and can optionally return a response.

[Follow these instructions for setting up webhook](./starter-kit/webhook/README.md) with the Watson Assistant chatbot you just provisioned.

### Integrate your COVID-19 chatbot with Slack

Now that you have a functioning Watson Assistant, let's deploy it to Slack. Slack is a cloud-based messaging application that helps people collaborate with one another. After you configure a dialog skill and add it to an assistant, you can integrate the assistant with Slack.

When integrated, depending on the events that you configure the assistant to support, your assistant can respond to questions that are asked in direct messages or in channels where the assistant is directly mentioned.

[Read these instructions](/starter-kit/slack/README.md) to learn how to integrate your COVID-19 chatbot with Slack.

![Slack Gif](/starter-kit/slack/readme_images/Slack.gif)

### Integrate your COVID-19 chatbot with Node-RED

Want to create a voice-enabled chatbot? This tutorial teaches you how to [create a voice enabled chatbot using Node-RED](./starter-kit/node-red/README.md) and the Watson Assistant, Watson Speech to Text, and Watson Text to Speech nodes.

## Disclosures

This tool is intended to provide information based on currently available CDC and other public information to help you make decisions about seeking appropriate medical care. This system is not intended for the diagnosis or treatment of disease or other conditions, including COVID-19, and you should not provide any personally identifying or private health information.

This Watson Assistant bot is populated with data that is sourced from the following resources:

- Most static responses provide information found on the CDC's COVID FAQ Page: https://www.cdc.gov/coronavirus/2019-ncov/faq.html
- Dynamic infection and death counts are sourced from Johns Hopkins University via the following API: https://www.covid19api.com/
- Dynamic news stories are sourced from Watson Discovery's news feed. Additional information on that service can be found here: https://www.ibm.com/watson/services/discovery-news/

## License

This solution starter is made available under the [Apache 2 License](LICENSE).
