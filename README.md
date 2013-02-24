#Reddit Auto Responder

This bot continuously checks for new private messages and responds with a given message if the subject conforms to a certain pattern.

To use the bot, you will need python and [praw](https://github.com/praw-dev/praw/wiki) installed.

Get a copy of the code by running

    $ git clone git://github.com/kragniz/reddit-auto-respond.git

Run the bot with
    
    $ cd reddit-auto-respond
    $ ./responder

To configure, open `config.json` in a text editor and add your username and password in the fields provided.

#Response rules

The rules for choosing what response to give use [regex](http://en.wikipedia.org/wiki/Regular_expression). To configure the bot you will only need to use a very small subset of the regex language. Have a look at [this quick overview](https://github.com/tartley/python-regex-cheatsheet/blob/master/cheatsheet.rst), or modify the examples below.

  Examples
  * `.+` Respond to any subject
  * `.*subreddit.*` Respond to a message with `subreddit` in the title

The order of the rules matter. Rules earlier in the config file take precedence over later rules in the case of multiple rules matching the same subject text.

#Example config

```javascript
{
  "username": "POTATO_IN_YOUR_RESPONSE",
  "password": "correcthorsebatterystaple",

  "responses": 
  {
     ".*report.*": "Please send this message via mod mail instead",
     ".*help.*": "Help yourself to some:\n\n* Cheese\n\n* Cake\n\n* Some bees",
     "^hello.*": "Well hello there",
     ".+": "It might take me a while to get back to you, sorry\n\nSent by a bot"
  }
}
```

Some points about the config:
  * Full reddit markdown notation can be used in the body of the messages, but newline characters are not directly permitted within the config file. Use `\n` in the place of a newline character
  * Regular expressions used are case insensitive for simplicity
  * The rules used in the example config above (in plain english) are:
    1. Any subject including the word `report`
    2. Any subject including the word `help`
    3. Any subject beginning with `hello`
    4. Any subject with one or more characters

#Licence
This code is licenced under the terms of the WTFPLv2. See the `COPYING` file for more details.
