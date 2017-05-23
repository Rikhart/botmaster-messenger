# Botmaster-messenger

[![Build Status](https://travis-ci.org/botmasterai/botmaster-messenger.svg?branch=master)](https://travis-ci.org/botmasterai/botmaster-messenger)
[![Coverage Status](https://coveralls.io/repos/github/botmasterai/botmaster-messenger/badge.svg?branch=master)](https://coveralls.io/github/botmasterai/botmaster-messenger?branch=master)
[![npm-version](https://img.shields.io/npm/v/botmaster-messenger.svg)](https://www.npmjs.com/package/botmaster-messenger)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](LICENSE)

This is the FB messenger integration for botmaster. It allows you to use your 
botmaster bot on FB Messenger

Botmaster is a lightweight chatbot framework. Its purpose is to integrate your existing chatbot into a variety of messaging channels - currently Facebook Messenger, Twitter DM and Telegram.

## Documentation

Find the whole documentation for the Botmaster framework on: <http://botmasterai.com/documentation/latest>

## Installing

```bash
yarn add botmaster-messenger
```

or

```bash
npm install --save botmaster-messenger
```

## Getting your Credentials

If you don't already have these, follow the steps **1-4** on the Facebook Messenger guide:
<https://developers.facebook.com/docs/messenger-platform/guides/quick-start>

In **step 2**, where you setup your webhook, no need to code anything. Just specify the webhook, enter any secure string you want as a verify token(`verifyToken`) and copy that value in the settings object. Also, click on whichever message [those are "update"s using botmaster semantics] type you want to receive from Messenger (`message_deliveries`, `messages`, `message_postbacks` etc...).

To find your Facebook App Secret (`fbAppSecret`), navigate to your apps dashboard and under `App Secret` click show, enter your password if prompted and then there it is.

## Code

```js
const Botmaster = require('botmaster');
const MessengerBot = require('botmaster-messenger');
const botmaster = new Botmaster();

const messengerSettings = {
  credentials: {
    verifyToken: 'YOUR verifyToken',
    pageToken: 'YOUR pageToken',
    fbAppSecret: 'YOUR fbAppSecret',
  },
  webhookEndpoint: 'webhook1234',
};

const messengerBot = new MessengerBot(messengerSettings);

botmaster.addBot(messengerBot);

botmaster.use({
  type: 'incoming',
  name: 'my-middleware',
  controller: (bot, update) => {
    return bot.reply(update, 'Hello world!');
  }
});
```

## Webhooks

If you are not too sure how webhooks work and/or how to get them to run locally, go to [webhooks](/getting-started/webhooks) to read some more.

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### MessengerBot

**Extends BaseBot**

The class to use if you want to add support for FB Messenger in your
Botmaster project.

#### constructor

Constructor to the MessengerBot class

**Parameters**

-   `settings` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** MessengerBot take a settings
    object as first param.

**Examples**

```javascript
const messengerBot = new MessengerBot({ // e.g. MessengerBot
  credentials:   credentials: {
    verifyToken: 'YOUR verifyToken',
    pageToken: 'YOUR pageToken',
    fbAppSecret: 'YOUR fbAppSecret',
  },
  webhookEnpoint: 'someEndpoint'
})
```

#### \_setGetStartedButton

Adds get start button to your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/get-started-button>

**Parameters**

-   `getStartedButtonPayload` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The payload of the postback
    you will get when a user clicks on the get started button.
-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_getGetStartedButton

gets get started button payload from your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/get-started-button>

**Parameters**

-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_removeGetStartedButton

removes get started button from your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/get-started-button>

**Parameters**

-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_setPersistentMenu

Adds account Linking to your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/persistent-menu>

**Parameters**

-   `persistentMenu` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** persistent menu to use for your messenger
    bot
-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_getPersistentMenu

get persistent menu from your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/persistent-menu>

**Parameters**

-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_removePersistentMenu

removes persistent menu from your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/persistent-menu>

**Parameters**

-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_setGreetingText

Adds greeting text to your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/greeting-text>

**Parameters**

-   `greetingObject` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** greeting objects. Can be localized.
-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_getGreetingText

get greeting text from your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/greeting-text>

**Parameters**

-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_removeGreetingText

removes greeting text from bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/greeting-text>

**Parameters**

-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_setWhitelistedDomains

Adds white listed domains to your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/domain-whitelisting>

**Parameters**

-   `domainNameLists` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** List of domains to whitelist.
-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_getWhitelistedDomains

get whitelisted domains from your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/greeting-text>

**Parameters**

-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_removeWhitelistedDomains

removes whitelisted domains from bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/greeting-text>

**Parameters**

-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false
-   `domainNameLists`  

#### \_setAccountLinkingUrl

Adds account Linking url to your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/account-linking-url>

**Parameters**

-   `accountLinkingURL` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** Authentication callback URL.
    Must use https protocol.
-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_getAccountLinkingUrl

get account linking url from your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/account-linking-url>

**Parameters**

-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_removeAccountLinkingUrl

removes account Linking to your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/account-linking-url>

**Parameters**

-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_setTargetAudience

Adds target audience url to your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/target-audience>

**Parameters**

-   `targetAudience` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** 
-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_getTargetAudience

get target audience url from your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/target-audience>

**Parameters**

-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

#### \_removeTargetAudience

removes target audience to your bot. Read more here:
<https://developers.facebook.com/docs/messenger-platform/messenger-profile/target-audience>

**Parameters**

-   `resolveWithFullResponse` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** specify wether request should
    resolve with full response or not. By default, this is false

## Contributing

In order to contribute, you will need to make sure the tests run on your local machine. To do so, follow these steps:

1. Create a `./tests/_config.js` file that looks like this:
```js
'use strict';

const config = {
  messengerCredentials: () => ({
    verifyToken: 'YOUR_VERIFY_TOKEN",
    pageToken: 'YOUR_PAGE_TOKEN',
    fbAppSecret: 'YOUR_FB_APP_SECRET',
  }),

  messengerUserId: () => 'YOUR_USER_ID_FOR_THIS_PAGE', // who to send messages to in tests (that's me again, only in messenger...)
  messengerBotId: () => 'YOUR_BOT_ID', // the id of the bot (as sent in message updates). I.E. your page id
};

module.exports = config;
```

## License

This library is licensed under the MIT [license](LICENSE)
