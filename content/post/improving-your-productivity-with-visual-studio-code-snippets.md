---
title: "Improving Your Productivity With Visual Studio Code Snippets"
date: 2019-09-28T18:35:00-05:00
description: Visual Studio Code Tricks
draft: false
tags: ["VSCode", "snippets", "productivity", "trick"]
---

Hey everyone, this is my very first article so I hope that you like it.

Okay, so let's move on to the importance of using Snippets, I will do this by showing some examples and how can we improve both our coding speed and productivity. 

Imagine the next situation: 

You are writing an API and you have to repeat a lot of code every time you return a response, the response can be either a success or an error. So you may have defined a class to handle your errors and also the successful return.

Something like this:
![Alt Text](https://thepracticaldev.s3.amazonaws.com/i/fj9skiyvt1fv5jk3e56l.png)

Your class may have more parameters or less, or you can have only one, just bear with me.

Now anytime you have a request on your API, you may be doing something like this, if you are using express and Node.js:

![Alt Text](https://thepracticaldev.s3.amazonaws.com/i/1yp4aey050npo0e7m7bs.png)

On the image above you can see that we have an endpoint to our API which is:
```javascript 
app.use("/:valid", function(req, res, next){}) 
```
Then we are using our classes that we defined above to handle error or success, and that may happend a lot on our code.
```javascript 
// This is repetition, and we can create a snippet for this.
res.status(200).json(new SuccessHandler(200, "The value is valid", somePayload)) 
next(new ErrorHandler(500, "An Error has occurred"))
```

Let's now create those snippets, that is why you are here. 

So on VSCode we are going to press _ctrl + shift + p_  to open for the command pallet, and then type "Snippets". It will show something like this: 

![Alt Text](https://thepracticaldev.s3.amazonaws.com/i/qcuci2597peysqlg0tsv.png)
Then hit _Enter_ and you will see this:
![Alt Text](https://thepracticaldev.s3.amazonaws.com/i/v6r2qcd2rbnx0y8kqkkn.png)
As you can see in the options you can create global snippets, a file of snippets just for your actual project, or you can create snippets for a particular language. In this case I will just create a global snippet.

Once you hit the button to create a snippet file, VSCode will ask you to give it a name, you can use wherever name you want. I call mine my_snippets.

VSCode will open the file automatically for you to edit your custom snippets, and will show you an example. I will create two examples to show you how can you create yours.

Inside my file I created a new object (Json Key) like so:
```json
"Error Handler": {
  "scope": "javascript",
  "prefix": "ehh",
  "body": [
     "next(new ErrorHandler(${1:500}, ${2:message}))"
  ],
  "description": "optional."
}
```
Okay, let's review the json object, the key would be the name to our snippet, this can be any name you want to put in, but I would recommend something that you will remember on the future, or something related to what the snippet does.

*scope* will indicate what languages are supported(allowed) to use this snippet.
*prefix* is how you will invoke the snippet.
*body* is as the name said the body of our snippet. Here you will define what you want to return when invoking the snippet.

The *$* indicate a new "variable" that you can add there, as I'm creating the handle error I just added the 500 error to the first parameter, but this could be anything you want. For example instead of 500 it could be *${1:statusCode}*. Notice that the *1* inside the braces indicate the first argument of the body value.

Let's create the Success Handler snippet to clarify a little bit. It will look like this:
```json
"Success Handler": {
  "scope": "javascript",
  "prefix": "sh",
  "body": [
	"res.status(200).json(new SuccessHandler(${1:200}, ${2:message}, ${3:payload}))"
  ],
  "description": "Create successful return."
}
```

I haven't show you the usage of those beautiful friends of ours. let's see them in action.

![Alt Text](https://thepracticaldev.s3.amazonaws.com/i/iuxrjh6m2ngdth0dsjmr.gif)

#### Wrap up
Well, this was my first article, I really hope that you like it and find it a little bit useful, there are some features of VSCode that we as developers some times forget to use. See you all next time.

Happy Coding.

