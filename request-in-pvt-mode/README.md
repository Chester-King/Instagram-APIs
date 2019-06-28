# Request Accepting In Private Mode

This API accepts three arguments
* username - Your instagram Username
* password - Your instagram Password
* number - The number of requests you want to accept in Private Mode

## Understanding the CodeBase

The whole task is being run as an aync task
 
### Dependecies used

```javascript
const express=require('express')
const puppeteer = require('puppeteer');
const app=express()
const readline = require('readline');
const randomUseragent = require('random-useragent');
```

### Page Deployment 

```javascript
const browser = await puppeteer.launch({ headless: true, defaultViewport: null, args: ['--no-sandbox', '--disable-setuid-sandbox','--start-maximized'] });
    const page = await browser.newPage();
```

### Actions on Instagram Page

We are directly opening the Login page instead of Instagram page
```javascript
await page.goto(`https://www.instagram.com/accounts/login/?source=auth_switcher`, { waitUntil: 'networkidle0' });
```

The requests are being accepted in Chunks of 9 requests for performace purposes
```javascript
for (step = 2; step < 11; step++) {
        element = await page.$x(`//div[`+step+`]/div[3]/div/div/button`);
        await element[0].click();
        console.log('Step ',step, 'click');
        }

``` 

### Closing the browser when opertaion is complete

```javascript
console.log('Task Succesfully Completed')
    await browser.close();
    return res.send('Task Succesfully Completed')
```

## How to start the Server

### Open terminal where your script lies

![Terminal](https://raw.githubusercontent.com/Chester-King/Instagram-APIs/master/Readme-Images/to/commandprompt.PNG)

Make sure you are in the directory of the script

To make sure of this try the `DIR` or `ls` command

![Directories](https://drive.google.com/open?id=1IeIVxgNKcmwzc8YiFEi7Cbd6en-YK0Ic)

### Installing Dependencies and Starting server

Type the command `npm install` in the terminal and hit enter
Then to start the server type the command `node app.js`

You will get a Message on the termial on succesfull server Deployment
`Server is up on port 3000`

![Server Up](https://drive.google.com/open?id=19680PoGPWyVSbj0wkDv1lcpZA0iHfPKZ)
