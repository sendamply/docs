# Node.js

Sending an email in Node.js is easy with the module NodeMailer. For more detailed documentation, check out the [NodeMailer community website](https://community.nodemailer.com/).


### Install NodeMailer

Install NodeMailer with the following command:

```
$ npm install --save nodemailer
```

****

### Send an Email

```javascript
var nodemailer = require('nodemailer');

// create reusable transporter object using the default SMTP transport
var transporter = nodemailer.createTransport({
  host: "smtp.sendamply.com",
  port: 465,
  secure: true,
  auth: {
    user: "your_amply_username",
    pass: "your_amply_live_access_key"
  }
});

// setup e-mail data with unicode symbols
var mailOptions = {
    from: '"John Smith" <john@example.com>', // sender address
    to: 'foo@example.com, bar@example.com', // list of receivers
    subject: 'Hello ✔', // Subject line
    text: 'Hello world!', // plaintext body
    html: '<b>Hello world ?</b>' // html body
};

// send mail with defined transport object
transporter.sendMail(mailOptions, function(error, info){
    if(error){
        return console.log(error);
    }
    console.log('Message sent: ' + info.response);
});
```



