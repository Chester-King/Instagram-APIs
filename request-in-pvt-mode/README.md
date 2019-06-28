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

![Terminal](https://00e9e64bac026702330248863454fed632ec3b48ce8ea7f8a0-apidata.googleusercontent.com/download/storage/v1/b/github-repo-pictures/o/commandprompt.PNG?qk=AD5uMEtzqFI6_hNVCkYPvX1Gopq6mt84h78KntXvq_jZp5V2jDcg8O2ghf7UX4CZTbblz1SlP4m18dyDOQ7ICQ-Ni_cPFQEoVslElkmxt1vKDVCZIqulz57invkePpyJkD16qlEa2kIag0toy-GwDmR8eHeV1Z9I3JccctYZh8PbldlJ_MLahyK4JNGI0V8vGydmlOe8JCEnnblh9VMfpRPwmyhUyLJewzazyjIObApOEc4PToMzDC4EckL4lmUCkgMOZvBt6QFKoflDO0Z15F0saSTogiCPtmc2JUySDZFRe9u6j_KMDe64fTmpAwlzoQTsHFdlIl1HWleClSdmm1fJkks1frZM3cjW6luoFEiYSqX3S4KSezhSzl4T0tZK4dbHFEAVg9vq9Zz3cBuyk0rD7XANPSEfT-LpB8g30UIMzDMD7HHRa3N9pZuzZ2aqC4iYNyh4NV_90OVS2CXO4_f6sQuecXkbfK3_bilgSRs8pS8QYkVj7aZCvj_WkT1Q2qUuaMteu8Sx6-OTdQjfXXY-yGenaY6SfLXjH_RznEE8WCZR36p7BKD6kEQPfkKLMQy3Hkf3ezp_tLqrAyrgx0NLyOKSTDj4oor7SgVZ_CE4xbdNINU-YUv3WT6fZGB11yqn5jr35syoLyLlCDfTgMqNlR4RZVFZaobvcrPVGy3HVSdtq4HfpITfFIj9MJYG1RU-MoaT0n9osTFTkpIJdcY2qIWh9mg9x13CCCj8h1LEBtY3lPxVLexXU6V9hvSMl7BeD776-US3-ds3OPIMBEilIE0HJg_i2w)

Make sure you are in the directory of the script

To make sure of this try the `DIR` or `ls` command

![Directories](https://drive.google.com/open?id=1IeIVxgNKcmwzc8YiFEi7Cbd6en-YK0Ic)

### Installing Dependencies and Starting server

Type the command `npm install` in the terminal and hit enter
Then to start the server type the command `node app.js`

You will get a Message on the termial on succesfull server Deployment
`Server is up on port 3000`

![Server Up](https://drive.google.com/file/d/19680PoGPWyVSbj0wkDv1lcpZA0iHfPKZ/view?usp=sharing)
