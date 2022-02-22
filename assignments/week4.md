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

1. <a href="https://glitch.com/edit/#!/blushing-rose-turnover" target="blank">Remix this Glitch project</a> - press "Remix" in the upper right, and wait for the project to regenerate so that you can edit it. It should have its own three-word-domain.glitch.me now. Take a look around. This Node project will act like your server, where you will write functions that program your new Twilio phone number.
2. Get a free account at [Twilio.com](https://twilio.com) - click "Sign up." You'll need to verify your e-mail address and a phone number - either your real one, or something like [Google Voice](https://voice.google.com), or use the temporary numbers on [this website](https://receive-sms-free.cc/).
3. Choose a new Twilio phone number! This is the number we are going to program. You can get a phone number from anywhere, just make sure it has "SMS" capabilities. (You will see that you have $15 balance for free in your trial account - it will not cost any money to "buy" this trial phone number.)
4. Get familiar with the [Twilio console](https://twilio.com/console). You should see an Accound SID, an Auth Token, and your new Twilio phone number listed under "Account Info."

**in Node.js, SEND SMS:**
1. Check out your `.env` file - there should be a list of variables that you need, but they'll be empty. Input the correct values from your Twilio console. 
2. For `TO_NUMBER`, this needs to be the phone number you used to verify your Twilio account. On the free trial versions we are playing with, we can only send SMS to this number. This should be in the same format as the new Twilio phone number: +15555555555 for example. Twilio just needs [this formatting, called e.164](https://www.twilio.com/docs/glossary/what-e164).
3. Check out `package.json` to see what dependencies are already installed. You should have everything you need.
4. Find `server.js` - we want to write our first function, to send our SMS when the function is called. Look for a function called `/send-sms`.
5. Where the comments suggest, you'll want to write the code to send an outbound SMS! See [this documentation](https://www.twilio.com/docs/sms/quickstart/node#send-an-outbound-sms-message-with-nodejs) for guidance.
6. For the content of your SMS message, ask your 'user' a question. What is this poll about, what are they voting on? Is this a survey, a quiz? What data are you collecting? For example, "Do you agree with the following statement: cats rule the internet?"

**let's call this function, from static site:**

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
2. Test your function by pressing the button! What do you see in your server's logs? Do you receive an SMS at your phone number?

**in Node.js, RECEIVE SMS:**
1. Now we want to write a function that runs whenever our number _receives_ an SMS. Go back to `server.js` in your Node project, and find the function called `/reply-sms`.
2. What's going on in this function? There are some instructions in the comments. We basically are able to understand the incoming message, and we want to respond conditionally.  For example: 
```
if (incoming === 'yes') {
  responseMessage = 'I agree too!';
 } else {
  responseMessage = 'I guess we don't agree.';
 }
 ```
 3. How do we get this function to work? We have to connect it to our Twilio phone number. We can use a command line (Terminal) tool to do this.
 4. Open the Glitch Terminal in the lower left, and type: `twilio login`. Where can you find the Account SID and Auth token info they are asking for?
 5. After you've logged in and created your profile via the Terminal, you can type:
 ```
 twilio phone-numbers:update "+1TWILIONUMBER" --sms-url="https://your-glitch-project.glitch.me/reply-sms"
 ```
 You'll need to replace "+1TWILIONUMBER" with your new Twilio number, and the URL with your `server.js` project's address. This connects your new Twilio number to the function you just wrote. 
 
 **putting it all together!**
 1. Keep your Glitch Node server.js project open - you'll want to look at your logs.
 2. Press your button on your static blog post - did you receive an SMS? What do your server's logs show you? Can you see the content of your SMS?
 3. Does your new 'bot' respond based on the conditional you wrote in your function? Keep chatting!


### to finish:

1. Leave your new post up on your static site blog - I will check out the button.
2. If this didn't work for you after trying for awhile - how far did you get? Where would you continue debugging? What was difficult? What was clear to you?
3. Under the button, write at least 2 completely new project ideas using telecommunications (you can imagine doing similar things with voice, video, etc.).  If you need project inspirations, check out the [Twilio blog](https://www.twilio.com/blog). These can just be short sentence brainstorms.

More help, tools, ideas - see this week's list of [links](https://github.com/mab253/software-interventions-spring22/blob/main/lectures/week4/links.md)
