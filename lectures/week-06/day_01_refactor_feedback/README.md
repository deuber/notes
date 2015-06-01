# Project 1
## Pair Review


| Objectives |
| :--- | 
| Utilize your knowledge of Mongoose, Express, AJAX, and Templating to refactor project 1 with a partner. |

## Application Overview

Go to your projects on Github. 

* Discuss what each of your applications do at a high level. This should be one or two sentences, an elevator pitch. (5m) 
* Make sure each project has a `README` that highlights these details.
	* If none exists, create one (10m)
* Is there a link on GitHub to the deployed application on Heroku?
	* If none exists, plan to deploy it later.

### Initial Models Review

Everyone should have a `User` model, and a `models` directory. Take time now to review each other's `User` model and any other models. 

* Note any additional model relationships.
	* Discuss why any relationships are there.
	* Discuss why they choose a certain type of relationship: embedded or reference.
* Note any bugs, jumbled code, or indentation problems.
	* Create a Github issue on each repository regarding model bugs or areas to be refactored.

### Routing And Rendering

Review the application routes and identify those that send data to the frontend. 

* Note any bugs or areas for refactor in routing using GitHub issues.
* Can a user `Sign Up`, `Sign In`, and `Logout`.
	* What about that `secret` field for the `express-session` middleware is that visible on GitHub? 
* Discuss where data is being used. 
* Does a user have to be signed in to view the data?
* If there is favoriting logic then discuss how that is being handled. 
	* What kind of checks are being made to see if `_id`'s or data posted to the server actually exist.
* If you're templating then verify that input is being properly escaped. Submit an issue on GitHub for any unescaped data.
	* Can I put `HTML` or `JS` into fields on your site?
		* Try signing up with a `User` that has an email like `<img src="http://onebigphoto.com/uploads/2014/04/cute-mini-lion-kitten.jpg">`.
	* Discuss the `<%- ... %>` vs `<%=  ... %>` in underscore or look at underscore's `escape` method.
	* Are there things like `onclick` inside of the `template`? This is fine to get something up and running, but you should submit a bug for this on GitHub issues. Why? Separation of concerns is being violated `JS` event handling and `HTML` should be separated.
* Note any major layout issues on GitHub. How does it respond to resizing?
	
## Recfactoring Part 1

Pick one or two major areas of refactor that you've identified in each application. This could be something like the following:

* If you created smaller issues for models, routing, or templating then you should consider tackling these first.
* Finishing up a major feature or working on a bug in a feature.

## Refactoring Part 2

Notice for login you have some issues.

* Your secret isn't properly hidden for `express-session`. Try using the following in your applications:
	* `dotenv` for Node and use this to hide your secrets.
	* You'll want to make sure you also have a `.gitignore` file to ignore the usual directories and the `.env` file.
	* Read up on `Heroku` env variables as a pair.
* Note that if you're logged in and your application goes down then you loose your session and  you have to log back in.
	* Try integrating [connect-redis](https://github.com/tj/connect-redis). 
	* [Checkout redis if you're interested](http://try.redis.io/)
	* Try to `brew install redis`