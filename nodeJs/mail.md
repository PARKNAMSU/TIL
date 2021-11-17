# Nodemailer

### nodemailer 로 E-mail 전송

모듈 사용 전 nodemailer 와 nodemailer-smtp-transport을 install 한다

```
npm install nodemailer
npm install nodemailer-smtp-transport
```

<br>

nodemiler, nodemailer-smtp-transport를 require 하고, 메일을 transporter 설정을 위해 smtp를 이용하여 객체로 생성해 준다

```javascript
const mailer = require('nodemailer');
const smtp = require('nodemailer-smtp-transport');

const transporter =  mailer.createTransport(smtp({
    service:'gmail',
    host:'smtp.gmail.com',
    auth:{
        user:'example@google.com',
        pass:'your password'
    }
}));
```

<br>

메일을 보낼 이메일, 받을 이메일, 제목, 내용을 생성해 준다.

```javascript
const mailOpt = {
    from:'example@gmail.com',
    to:'tomail@gmail.com',
    subject:'your subject',
    text:'your text'
}
```

<br>

transporter.sendMail 메서드를 통해 메일을 전송해 준다.

```javascript
/*
  arg1 : mail 옵션
  arg2 : 전송 후 콜백함수
*/
transporter.sendMail(mailOpt,(err,info) => {
    if(err)
        throw err;
    else{
        console.log(`sent: ${info.response}`);
        res.status(200).send(info.response);
    }
});

```

<br>

### 전체 코드
```javascript
const mailer = require('nodemailer');
const smtp = require('nodemailer-smtp-transport');

const transporter =  mailer.createTransport(smtp({
    service:'gmail',
    host:'smtp.gmail.com',
    auth:{
        user:'example@google.com',
        pass:'your password'
    }
}));

const mailOpt = {
    from:'example@gmail.com',
    to:'tomail@gmail.com',
    subject:'your subject',
    text:'your text'
}

transporter.sendMail(mailOpt,(err,info) => {
    if(err)
        throw err;
    else{
        console.log(`sent: ${info.response}`);
        res.status(200).send(info.response);
    }
});
```

<br>

참조: [w3school](https://www.w3schools.com/nodejs/nodejs_email.asp)
