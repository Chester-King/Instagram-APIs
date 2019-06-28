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

![Directories](https://00e9e64bacf073902922d98e3e65b8a5753bd82f8d265c81e0-apidata.googleusercontent.com/download/storage/v1/b/github-repo-pictures/o/Directories.PNG?qk=AD5uMEt-jl9nXWFMKU0mfDxDZ_VxU12yfK99iXwtg4LvIXgypg57EBk4U5bEUtTU-GtdMWTuSgpiOwwrTH4QtDW9_a-FxFTqehxg1QgC_5Dimk_jiUwet3TyDwLrAfErXiMvRP22pWeJfW33lPxyZTka2zSmWAYKnvL-TXVvd50wkrR_I4AcyjZujewo6YCW_AGiOwma4nM_Yn7qw2zX-TjRKXDgIuDXjd5fcUiGIU_yWW8epH-Cj7R6VgGVNiVnTELysztqbB2miIM_stydjlTOL8qE_5JHzRJg2TLDHuvkP1ENQyttFrbLudMbizlg9gqsoaG99wKl0courit4hADaL7889nhBwz1uOmbQuWJXqfWXvY9c47XYniEkCzxRRenURWR6gZ0kBBX-g3k8bQPHwQtKLqJ1FdFTJohYq4JJtysZlNOrPTUAW_pEugd4upumlTs8o3Xl0rbGKDHw0GufKbUbWH-6I42g5l6gj32rwDH45FAQxtD7xpZZHObEYPr_s4oELGgrmabiYMhMG1eJwqBmLGSK8IqdysgPEmMR_dfVXQ-NCP2pFB6gCwUC-aqc0ZeO-nAGY8ivUzfnWvi-WVtwMnYjKNDovhu_R3c0swIhJAMMtk2t7zxEBeXz9iqBXq53fOZ-DT8nu5mMBJxGoVUcZnVMNpR8sZRvOKtQHEdVlDfV3ZTOMWjizFTmaVzg-b1WU7bXIbNo7rCVLzL7cH_uk4XB8r1QKESBArhA1g93XJpds3JqI3YAaYIczCnRDwawmka241wUwqs_I5NGElczd28WeA)

### Installing Dependencies and Starting server

Type the command `npm install` in the terminal and hit enter
Then to start the server type the command `node app.js`

You will get a Message on the termial on succesfull server Deployment
`Server is up on port 3000`

![Server Up](https://00e9e64bac195c466460234fd38cf1aeffed8562e9c2159eef-apidata.googleusercontent.com/download/storage/v1/b/github-repo-pictures/o/serverdep.PNG?qk=AD5uMEsq0ZxujcFB6OnMcxdJM_PYt7HBaboXdlYwptPGaUrohmN7uoLMv0iigv263VnwJcp-WOBBbP0osOU9O5qxewogpaaRbjWRGUGZelMgaLgz5b93HWkGPwLhg-EJ3q-0DH2o-LiS_eKE389uOQTkPKmqql78Rx-BsFEcbt0i9pB0uSelrK_2PxDA-sJoQ4orXNqAWO0_C62h6nNKXHrAJfHIAxKS1e64stSHZ_SxhTM61U8t-QgHy8C1MfLX7GS8bcqYYZXXO7DxW3L5Udpj3zAdgig963i2Wh8o4f2wVc0ifKaDYBK16QffQyI3sNvs6qmKCKtNCSDtXLlxWaOeCq3SzfckzW33IPm1ZIk1zeQNrfL5rg1vwugSJXpe4jxy-xZ2YK-tFgkt442JyqPKA6_8Pzc8682cmuisHUoRJyLasI2zIQ1EEJcDgNQ7cfo7MC9wUgyuE4rIKFOwVnx75_xRx7ANqwQwY2CUSgEXZ20dNaMJKp-CFAKUIfLn9IwDnX_SyBWonFvpVIoIx3Y2uNPOo--Bjng59zt6nfu924gJRcwo6wr28vcFAtSykncTpJr_d4FnSbn2tNAWQMMmub_h7WfCv1SUcLdE6FdAylx5SuT2Y6BAucWAaE4UaHkx5ccoPI8Tw__OdyX1tRqW1n4SoiPBigMFNSyUiRrU-TXJrd2UlaLZm2ZvhfCCPG4NcYgM9fLVa0fv9vVzVthagcaSfO7TU7zH1y64FWtM0teyEEtbBvkluhnWeyB1DIxUbYTYKs8O9DPBlvpxq2XZnfSsLVvECA)

### Configuring Postman

Open up Postman and create a get request with following configuration(Make sure the server is up and running)

![Postman Entery](https://00e9e64baca899b6194ad5de1410e98679bfc320e48f0c0c66-apidata.googleusercontent.com/download/storage/v1/b/github-repo-pictures/o/Postman%20Entery.PNG?qk=AD5uMEu95gzUIPudBDhOs95poqszaJ_jWxD5HQmBXZPce4Fd33wy4jqpXPstLhP1grLJ3fuoNOH4ACWHuQqaM3SyvveobKFkGGhzMuvqTJh4nWfhGeNaScfkZ92uiHZ9UavQdYJeHGtyrBWAv7NN20M98X-xVNNqamBiFjlmlpr5eZ0FCJVmS2SPyI01SwHrOI_rQ5dDiO_9Sme7lXwxZDMLJR89gaRYJE4Yd2GYChX_4WKVdY_BINz9Cjs-D0TvbIFd8t-DoLDSNBfbPDLdQNp8SQoH7KstcyfFYVOOLEfM8MvD-yLTkD0-LZtSxLgQ65rF5aP4PjrD3ARIvbIhCULKbrUHLDQ9olM62haObHiBrsx1NIO8DjOoJLfXtpXzRzXNWajkidSMnCGFSUdksvbYYcg0lPoo_IPbrNKHCtmd_C0I0EvRZa-fR7iqYaKjwaqLSwoxCA2tIlhXDsH02Vuw6iOOVz0v6Ums06-9Wn5i-0cWiyq0s2R3frVIRJA6rs6_fWGV2haeZrbp9lMonIVOJ-SSNAmc-HykJfR9POb_AMfG-eYcXUqTpLXsZWJyxzUNHUXsVjabJ_YcRHmgaTDv08HMuFrKtCeyIu5inm18rJ5th0zt8qElWvoZPr4eyeHpOyyDfAOoRsKXd6dbiWHxBndPNKNBicwwrRxemlg9tJUsbkv-QMXzDhaYtB9_sXsMiJ0jYZvyzE0RleFk1_KJJbJ0gPKifJEDcxkYVOhj4SX2Bch2AwBnsNpZTg3-gSdCha19B0WzGy9rifar7u6ntdYKCNwmoQ)

