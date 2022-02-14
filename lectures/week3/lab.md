# 🤖✉️ lab group work: 
# sending an e-mail with Node.js and serverless functions

## goals:
- create a button on a static website that sends an e-mail
- set up a Node.js environment in Glitch that can receive and send data
- work together and collaboratively 

## tools:
- ✨Glitch.com account
- 🦆 [Ethereal Email](https://ethereal.email/)
- 📧 [Nodemailer](https://nodemailer.com/about/) module

You'll use a Node module, or a pre-written open source block of code, to set up an e-mail sending function on your static blog site. You can use Ethereal e-mail to create a temporary "fake" test e-mail address.

## suggested steps: (how can you divide this labor as a group?)

### setup
1. Introduce yourselves as a group! 
2. [Re-mix](https://glitch.com/edit/#!/faint-rustic-anaconda) this site, a super-basic Node app. Read the README.md, and check out the structure and comments in `server.js`
3. You can do what makes the most sense for your team in order to share work - do you want to share screens and each have projects open and follow along? Do you want to [invite people](https://glitch.happyfox.com/kb/article/49-inviting-members-to-your-project/) to 1 shared Glitch project that you work on together? (You can code simultaneously this way.)  
4. Check out [Ethereal Email](https://ethereal.email/). Start by reading their FAQ, and then Create Ethereal Account. What do you see on the screen that says **Account created**? You'll need this information later.
5. Check out [Nodemailer](https://nodemailer.com/about/) - read through the About page.
6. Install `nodemailer` in your re-mixed Node project. You can do this via the terminal as the Nodemailer About page suggests, or you can [use Glitch's package.json](https://help.glitch.com/kb/article/42-adding-npm-packages/) method and instructions. 

### functions
7. Add a `function` to `server.js` in your Node project that will run the code that sends your e-mail. To start, you can copy the code that is currently there: 
```
  fastify.get("/function-name", function (request, reply) {
    console.log("🪵 something!");
  });
```
8. Add a button on your static Glitch blog site that calls that function.
  - Use your logs on the Node.js project - does pressing the button call the external function?
  - Do you remember how to write the `fetch` function? We wrote a very basic one in the random number example in class. You can use [this documentation](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) if you need to look at the syntax again ... there are some other examples [here](https://developers.google.com/web/updates/2015/03/introduction-to-fetch).

### emails!
9. Inside your "serverless" function in the Node.js project, write the code that sends your e-mail via Nodemailer. You'll find this in Javascript on the Nodemailer about page.
10. What do you need to customize in order for this function to correctly send an e-mail to your **test Ethereal e-mail account?** Hint: you can look back at the "Account created" page on Ethereal.
11. What else can you customize here? What will your e-mail message say, who is it from?

### test
12. Click your button on your static Glitch blog - does it work? Does it send an e-mail to your test Ethereal account? Can you read the message?
  

### extensions? if you're done ...
13. Change something or create an alert on the static webpage to show that the e-mail has been sent.
14. How could you let the user on the static site write the content of the e-mail? You could try this first by hard-coding it via the static site, or you can investigate [forms](https://simonplend.com/how-to-use-fetch-to-post-form-data-as-json-to-your-api/)...
