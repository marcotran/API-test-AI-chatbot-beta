# API-test-AI-chatbot-beta
# Testing

```
npm test
```

# Execution

```
npm start
```

# How to Test
Testing is done by adding `/test/dialog-flows` like so:

```js
module.exports = [
  {
    out: "set alarm in 10 seconds"
  },
  {
    in: "What would you like to call your alarm?",
    out: "test"
  }
  /* ... */
];
```

And adding a test via `/test/index.js`;

```js
describe('Bot Tests', () => {

  it('help', function (done) { 
      var connector = new builder.ConsoleConnector();
      var bot = testBot.create(connector);

      common.testBot(bot, require('./dialog-flows/flow.js'), done);
  });
});
```

# Possible tests to messages

* *exact string*: `in: "string to test"`
* *regular expression*: `in: /^(starts with string)/i`
* *function*: `in: (message, assert, callback) => { assert(message.text.length); callback(); }`
