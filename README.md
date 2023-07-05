# newman-reporter-slackreporter

Custom [Newman](https://github.com/postmanlabs/newman) reporter to send message to [Slack](https://slack.com/)

<img src="https://github.com/stephenwang1011/newman-reporter-slackmsg/blob/master/testResults.png?raw=true">

## Before you get started
- Install [Newman](https://github.com/postmanlabs/newman) ``` $ npm run i -g newman ```
- Create a [Slack incoming webhook url](https://api.slack.com/messaging/webhooks)
or
- Create a [Slack bot to send to channel or user dynamically](https://api.slack.com/messaging/sending)

## Installation
 ```CLI
 npm i -g newman-reporter-slackreporter
 ```

## Usage
```CLI
 newman run <collectionFile> -e <environmentFile> --suppress-exit-code -r slackreporter --reporter-slackreporter-webhookurl '<webhookurl>'
```

## Usage with channel override bot
```CLI
 newman run <collectionFile> -e <environmentFile> --suppress-exit-code -r slackreporter --reporter-slackreporter-webhookurl '<https://slack.com/api/chat.postMessage>' --reporter-slackreporter-token '<bearer token>' --reporter-slackreporter-chanel '<channel or userid>'
```

## Reporter Options Optionals
```
 --reporter-slackreporter-messageSize '<messageSize>' e.g 150
 --reporter-slackreporter-token '<bearer token>' e.g xoxb-XXXXXXXXXXXX-TTTTTTTTTTTTTT
 --reporter-slackreporter-channel '<channel>' e.g #general
 --reporter-slackreporter-buildurl '<buildurl>' e.g ci build url
 --reporter-slackreporter-failureOnly '<boolean>' e.g true
```


## Reporter Options
**webhookurl** 
Webhook URL to point to the slack api where results are published,If you have multiple channels, you must use the '#' to separate. eg:https://hooks.slack.com/services/TXXX#https://hooks.slack.com/services/NNN

**collection** 
Option to add the name of collection file onto the message

**environment**
Option to add the name of environment file onto the message

**messageSize**
Option to change the message size, defaulted to 100

**token**
Option to use bearer token for slack bots for channel override

**channel**
Option to select channel or user receive the result

**buildurl**
The circle ci build url, you can invoke the variable ${CIRCLE_BUILD_URL} 

**failureOnly**
Option to only send Slack message if failures occur. Default to false