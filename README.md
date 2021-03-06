# A Resizing Service on Azure Functions!

<a href="https://azuredeploy.net/?repository=https://github.com/juliajauss/resizingService" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

This repository gives you everything to deploy your own (basic) image resizing service. 

## Deployment
**You have 3 options:**

1. Just click the "Deploy to Azure Button". 
2. Use Azure CLI to deploy the ARM template. (Take a look at the howto.txt)
3. Use Powershell to deploy the ARM template. (Take a look at the howto.txt)

##Usage
After deployment you will have an HTTP POST endpoint **saveOriginal**. Just add the URL parameter *imgName* and tell the service how your image shall be named. Then attach the file itself and post everything into the interwebsz :)

URL: **https://yourcoolreszingapp.azurewebsites.net/api/saveOriginal**

- Request - URL parameters
  - **code** = your code listed at the function as a very basic way of authentication
  - **imgName** = the name of the file - and all its resizings - within the service
- Request - File attachment
  - attach your image to the POST request
- Response
  - **[string, string]** - a dictionary of URLs in the JSON format which contain all the generated resized versions of your uploaded image with the size as the key

> Response example
~~~~
{
 "original":"https://thumbfuncstorage.blob.core.windows.net/originals/mario/mario.jpeg",
 "200":"https://thumbfuncstorage.blob.core.windows.net/sized/200/mario/mario.jpeg",
 "100":"https://thumbfuncstorage.blob.core.windows.net/sized/100/mario/mario.jpeg",
 "80":"https://thumbfuncstorage.blob.core.windows.net/sized/80/mario/mario.jpeg",
 "64":"https://thumbfuncstorage.blob.core.windows.net/sized/64/mario/mario.jpeg",
 "48":"https://thumbfuncstorage.blob.core.windows.net/sized/48/mario/mario.jpeg",
 "24":"https://thumbfuncstorage.blob.core.windows.net/sized/24/mario/mario.jpeg"
 }
~~~~

In the "background" the second deployed function will be called as soon as the blob service saved the original - and then  the resized images are generated. 

##WOW, a wild mock resizing service appeared

So this is it! Just those few steps and you have a ready to go resizing service!
Nice one!

Have fun and share your feedback with me :)
  


