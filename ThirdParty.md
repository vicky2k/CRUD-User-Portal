Integrating to 3rd Party systems using nodejs
Example Email Service providers include mailtrap.io, Gmail, Sendgrid, Courier, Amazon SES, Mailgun

Set up and Install the dependencies
create a server, create a post request for sending mails,
setup nodemailer, create email template,
Test the email sending on Postman and verify the result on Mailtrap.io
Using Vanilla JS, Create a contact us form on the front end to send the request
and recieve a response.

Test the work on localhost:4000

const bodyParser = require('body-parser')
const express = require('express')
const dotenv = require('dotenv')
dotenv.config();

const app = express();
app.use(bodyParser.urlencoded({extended: false}));
app.use{bodyParser.json}());
app.use('/', express.static(\_\_dirname + k

const PORT = process.env.PORT || 4000;

app.listen(PORT, () => {
console.log(`Server Listening on Port ${PORT}`)
})

app.post('/', async(req, res) => {
const { name, email, subject, message } = req.body
try{
if (!name && !email && !subject && !message)
return res.join('Incomplete Data')

}catch(err){
console.log(err);
res.status(500).json((message:'Email Not Sent')
}
})

// On postman, make a post request with url localhost:4000

// Setting up node mailer
// create a folder name Utils and create a file
// emailsender
// nodemailer.com/usage
// mailtrap.io/inboxes demo inbox for credentials

const nodemailer = require('nodemailer')

exports.sendMail = async (option) => {

// Creat a transporter object and input all your configurations

const transporter = nodemailer.createTransport({
host: process .env.SMTP_HOST
port: process.env.SMTP_PORT
auth:{
user: process.env.SMTP_USER
pass: process.env.SMTP_PASSWORD

}
})

// The actual email options name, email, subject, message

const mailOptions = (
from:`$(option.name) <$(option.email)>`,
to: process.env.YOUR_EMAIL,
subject: 'Contact US Form- ${option.subject}`,
html: option.message
}

await transporter.sendMail(mailOptions);

// const result = await transporter.sendMail(mailOptions, // function(err, response))
// if (err) console.log(err)

}

// The .env file would contain credentials from demo inbox

// PORT, SMTP_PORT, SMTP_HOST, SMTP_USER, SMTP_PASSWORD, YOUR_EMAIL

// create a simple html page emailtemplate.html
// resave it back to .js and move it into Utils folder

const html = `` where the entire html page is placed
in betwwen the backticks

exports.eMessage = async () => {
``
}

go to mailtrap.io to see the sent email

use expressjs to serve the static html file
