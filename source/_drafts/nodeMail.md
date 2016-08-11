https://github.com/nodemailer/nodemailer
```
npm install nodemailer
```
```
var nodemailer = require('nodemailer');

var smtpConfig = {
    host: 'smtp.exmail.qq.com',
    port: 465,
    secure: true, // use SSL
    auth: {
        user: 'yanjie@ihomefnt.com',
        pass: 'elona2011PG'
    }
};

// create reusable transporter object using the default SMTP transport
var transporter = nodemailer.createTransport(smtpConfig);

// setup e-mail data with unicode symbols
var mailOptions = {
    from: '"Fred Foo 👥" <yanjie@ihomefnt.com>', // sender address
    to: 'yanjie@ihomefnt.com', // list of receivers
    subject: 'Hello ✔', // Subject line
    text: 'Hello world 🐴', // plaintext body
    html: '<b>Hello world 🐴</b>' // html body
};

// send mail with defined transport object
transporter.sendMail(mailOptions, function(error, info) {
    if (error) {
        return console.log(error);
    }
    console.log('Message sent: ' + info.response);
});
```
