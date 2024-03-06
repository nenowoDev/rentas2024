# La itu je?

![alt text](/images/image2.png)

First thing first, when we take a look at the website, it is presented with a login form

![alt text](/images/image.png)

Intercepting it using burp suite, it shows that there is another path called register.php

![alt text](/images/image3.png)

After creating an account, and log in, it redirected to dashboard.php, right after that pressing get flag will redirect you to another page which is flag.php

![alt text](/images/image4.png)

![alt text](/images/image5.png)

This part all we did was check the page source and take a look at script.js, inside the file, the js file is obsfucated, therefore we need to use the javascript deobsfucator

![alt text](/images/image6.png)

Next, we just run the generateCode() function using console, then it will alert the code, however making a POST request with the code doesn't provide the solution, another alert box comes out

![alt text](/images/image7.png)

![alt text](/images/image8.png)

After banging my head against the wall for 4 hours straight, I decided to wait for the clues.

![alt text](/images/image9.png)

Here it states shoot to the "head", I guess we need to change the request from post to head?

Nope I was wrong, moving on to another clue shoot the "host", here I changed the host header to localhost and it provide a strange response

![alt text](/images/image10.png)

200 OK and Error executing curl request: empty reply from server

Hmmmm it is clear that it is a vulnerability of SSRF via Host Header

[For Reference](https://payatu.com/blog/unveiling-the-secrets-of-http-host-header-attacks/#:~:text=Server%2DSide%20Request%20Forgery%20(SSRF,header%20of%20an%20HTTP%20request.))

Therefore, all I need to do is create my own domain using requestbin website, and inspect the request


![alt text](/images/image11.png)

![alt text](/images/image12.png)

Lastly, decode the flag from Base64

```RWSC{b045887cbadfda25b29db243a18de38cb1cbfb14}```