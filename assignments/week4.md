# Week 4: communications API experiment

DUE: Mon. FEB. 28th, 5:00pm

### Create a simple send/receive SMS bot with Node.js, triggered by a button on your static site. 

This project will be a basic prototype for a polling/voting app, an SMS chatbot survey, crowdsourced data collection, etc. 

### tools:

 - ✨Glitch.com account
 - 📱 sms-ready phone: or free [Google Voice](https://voice.google.com), or use the temporary numbers on [this website](https://receive-sms-free.cc/)
 - ☎️ free Twilio account (we'll get one)

### suggested steps:

**setup:**

1. [Remix this Glitch project](https://glitch.com/edit/#!/blushing-rose-turnover) and take a look around. This Node project will act like your server.
2. Get a free account at [Twilio.com](https://twilio.com) - click "Sign up." You'll need to verify your e-mail address and a phone number - either your real one, or something like [Google Voice](https://voice.google.com), or use the temporary numbers on [this website](https://receive-sms-free.cc/).
3. Choose a new Twilio phone number! This is the number we are going to program. (You will see that you have $15 balance for free in your trial account - it will not cost money to "buy" this trial phone number.)
4. Get familiar with the [Twilio console](https://twilio.com/console). You should see an Accound SID, an Auth Token, and your new Twilio phone number listed under "Account Info."

**in Node.js, SEND SMS:**
1. Check out your `.env` file - there should be a list of variables that you need, but they'll be empty. Input the correct values from your Twilio console.
2. Find `server.js` - we want to write our first function, to send our SMS when the function is called. Look for a function called `/send-sms`.
3. Where the comments suggest, you'll want to write the code to send an outbound SMS! See [this documentation](https://www.twilio.com/docs/sms/quickstart/node#send-an-outbound-sms-message-with-nodejs) for guidance.
4. For the content of your SMS message, ask your 'user' a question.  

**let's call this function, in static site:**

1. Open your Glitch static site, your project log. Create a new post, and add a button to it.  Your button should call a Javascript function that looks something like this:
```
<script>
  async function sendSms() {
    try {
      let functionAddress = 'https://your-own-url.glitch.me/send-sms';
      let response = await fetch(functionAddress);
      let data = await response.json();
      alert("sent!");
    }
    catch (error) {
      console.log(error);
      alert("error");
    }  
  }
</script>
```
2. Test your function by pressing the button! What do you see in your server's logs? Do you receive an SMS?

**in Node.js, RECEIVE SMS:**
1. Now we want to write a function that runs whenever our number _receives_ an SMS. Go back to `server.js` in your Node project, and find the function called `/reply-sms`.
2. What's going on in this function? There are some instructions in the comments. We basically are able to understand the incoming message, and we want to respond conditionally.  For example: 
```
if (incoming === 'something') {
  responseMessage = 'text A!';
 } else {
  responseMessage = 'text B!';
 }
 ```
 3. How do we get this function to work? We have to connect it to our Twilio phone number. We can use a command line (Terminal) tool to do this.
 4. Open Terminal again, and type: `twilio login`. Where can you find the Account SID and Auth token info they are asking for?
 5. After you've logged in and created your profile via the Terminal, you can type:
 ```
 twilio phone-numbers:update "+1TWILIONUMBER" --sms-url="https://your-glitch-project.glitch.me/reply-sms"
 ```
 This connects your new Twilio number to the function you just wrote. 
 
 **putting it all together!**
 1. Keep your Glitch Node server.js project open - you'll want to look at your logs.
 2. Press your button on your static blog post - did you receive an SMS? What do your server's logs show you? Can you see the content of your SMS?
 3. Does your new 'bot' respond based on the conditional you wrote in your function? Keep chatting!


### to finish:

1. Leave your new post up on your static site blog - I will check out the button.
2. Under the button, write at least 2 completely new project ideas using telecommunications (you can imagine doing similar things with voice, video, etc.).  If you need project inspirations, check out the [Twilio blog](https://www.twilio.com/blog). These can just be short sentence brainstorms.
