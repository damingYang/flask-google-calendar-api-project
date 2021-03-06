# Building Interactive Data Visualization using Python Flask and Google Calendar API

## TODO

* In calendar.html, still need to figure out how to do data.mapValues.max
* Add OAuth so other people can analyze their own calendar [Almost Done]
* Deploy the app using Heroku

## OAuth Section - WIP
* The OAuth flow is still not perfect, I had to always delete events.csv & db/events_all_2014.sqlite3 to restart. The branching logic is still a bit off
* Right now, calendarMap is being stored as a Python global variable. Not good. I tried using cache, but I couldn't easily loop through a cache.
* I think an alternative is, in each view, recompute the calendar map by writing a 'select distinct event_type from Events', but I had no success in implementing that yet in '/distinct' view
* Passing in variables in a template to a included template is free, but you can use { with clause } to make it more explicit
* I did some jank to convert calendarMap into a json object, so it can be used/passed down in/to .js files
* I then used JQuery .foreach to create specific d3.select
* I also remove the handling of white space in /api/event_type calls

## Project Milestones

* **Learn about Google APIs, specifically, Calendar API**
    * Learn what data is queryable through Google's API documentation
    * Learn How to query them. e.g. what parameters to pass in, in what language
    * List out the questions I want to analyze (ANALYSIS.md)

* **Set up a bare-minimum Flask Application**
    * Basic routes. e.g. index.html
    * Use the opportunity to review Twitter Flask Series from Simeon Franklin to get back to speed

* **Modularize HTML pages using templating system JinJia**
    * The philosophy is to keep the business logic in route definition as simplie as possible
    * Remove HTML from views, put them in separate HTML files
    * Learn how to pass in placeholder to build static HTML dynamically
    * Use Template inheritance to set up 'base.html' and extends it to provide consistent theme
    * make views return `render_tempalte` and that is it

* **Leveaging sqlite3 and perform a one time dump**
    * Setting up sqlite3 - nothing but a delimited text file stored in my local laptop
    * Quick Data Modeling on what the schema should be
    * Learn how to query it in Flask
    * Make sure all the data I care about are being dump to a .csv and to sqlite3

* **ORM Database interaction using SQLAlchemy**
    * Again, make views as simple as possible. Hide SQL statement away from views
    * Learn how to query the data using SQLAlchemy constructs instead of direct SQL query
    * Print the raw .csv data onto the Screen using SQLAlchemy
    * Set up new views to render different subset of the db table

* **Twitter Bootstrap**
    * Now that I can issue a query to backend DB and display them as raw data, beautify the webpage by Twitter bootstrap
    * Better layout with consistency (using template inheritance of course)
    * Better index.html page

* **Building API endpoints**
    * Learn how to translate the output into JSON objects
    * Build views to return these JSON objects
    * Here you go the API endpoints

* **Interactive d3 Charts**
    * Create Bootstrap style buttons
    * Create listners (e.g. d3.select.on) that takes in parameters
    * On click, use d3.json to hit my own API endpoints to get data
    * use the data and plot bars and calendars

* **Build OAuth into the app so any authorized Google Calendar can use this app**
    * Implement OAuth 
    * Once users grant their consent, the app stores the data into db
    * Update the front-end code so a list of calendarName would show up
    * Update the front-end code so that bar chart and calendar chart would still work

## Review of the Fundamentals of Web Application
* Python
    * [Starting a Python Project the Right Way]
    * [Writing Idiomatic Python]: Also there are three vidoes on this very topic
    * [Import from a relative path]

* Web Programming
    * [Web Programming Basics]: Philip Guo's intro to web programming
    * [What is a Web Framework?]: Given the foundation above, how web framework can help
    * Client-Server Interaction via HTTP protocol
    * The request always is initiated by the client, the server also respond with, eventually, a HTML
    * Web frameworks solves the nitty gritty details of routing and template-ing

## Flask Resources
* [Intro to Flask with JQuery]: Philip Guo
* [Flask for Data Science]
* [Jeff Knupp's Flask Posts]
* [Building a Flask web app with EC2, D3]

## Git References
* [Resovling Git Merge Conflicts]
* [How and When to Do Git Rebase]
* [Uncommit a Git Commit]
* [Remove directory from git but not local]
* [Use .gitignore to ignore checking in certain files]

## D3 References
* [General Update Pattern]
* [General Update Pattern III]
* [d3 nest]

## Google API References
* [QPX Express API]: Global airline pricing and shopping in a single, standard API.
* [Google Calendar API]

## Using Grunt to do Front-End Web Development
* [Browser Auto-refresh]
* [Another example]

## Heroku
* [Python Boilerplate] - Deploy to Heroku section
* [Getting started with Python in Heroku]

## OAuth on Flask
* [Using Google OAuth2 on Flask]
* [OAuth 2.0 overview]
* [Google API client library python]
* [Using OAuth2.0 for web application python]

## JQuery
* [Select id with space]

Another new thing I am doing is to paste the references I found right next to the code I wrote down to solve a particular problem. 

[question]: https://www.quora.com/As-a-data-scientist-what-are-the-things-that-I-can-learn-from-full-stack-developers-so-that-I-can-build-interesting-web-applications-for-data-science

[Starting a Python Project the Right Way]: http://www.jeffknupp.com/blog/2014/02/04/starting-a-python-project-the-right-way/
[Writing Idiomatic Python]: https://speakerdeck.com/nycpython/writing-idiomatic-python-jeff-knupp
[Import from a relative path]:http://stackoverflow.com/questions/279237/import-a-module-from-a-relative-path

[Web Programming Basics]: http://www.pgbovine.net/teaching-web-programming.htm
[What is a Web Framework?]: http://www.jeffknupp.com/blog/2014/03/03/what-is-a-web-framework/
[Intro to Flask with JQuery]: http://www.pgbovine.net/flask-python-tutorial.htm
[Flask for Data Science]: http://www.datacommunitydc.org/blog/2014/02/flask-mega-meta-tutorial-data-scientists
[Jeff Knupp's Flask Posts]: http://www.jeffknupp.com/blog/categories/flask/
[Building a Flask web app with EC2, D3]: http://www.datasciencebytes.com/bytes/2015/03/07/a-d3js-plot-powered-by-a-sql-database/

[Resovling Git Merge Conflicts]: https://help.github.com/articles/resolving-a-merge-conflict-from-the-command-line/
[How and When to Do Git Rebase]: https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase/
[Uncommit a Git Commit]: http://stackoverflow.com/questions/2845731/how-to-uncommit-my-last-commit-in-git
[Remove directory from git but not local]: http://stackoverflow.com/questions/6313126/how-to-remove-a-directory-in-my-github-repository
[Use .gitignore to ignore checking in certain files]:https://help.github.com/articles/ignoring-files/

[QPX Express API]: https://developers.google.com/qpx-express/
[Google Calendar API]: https://developers.google.com/google-apps/calendar/

[Browser Auto-refresh]: http://stackoverflow.com/questions/21913363/why-isnt-grunt-contrib-watch-livereload-working
[Another example]: http://justinklemm.com/grunt-watch-livereload-javascript-less-sass-compilation/

[General Update Pattern]: http://bl.ocks.org/mbostock/3808218
[General Update Pattern III]: http://bl.ocks.org/mbostock/3808234
[d3 nest]: http://bl.ocks.org/phoebebright/raw/3176159/

[Python Boilerplate]: https://github.com/mjhea0/flask-boilerplate
[Getting started with Python in Heroku]: https://devcenter.heroku.com/articles/getting-started-with-python#next-steps

[Using Google OAuth2 on Flask]: https://github.com/mimming/python-flask-google-api-starter
[OAuth 2.0 overview]: https://developers.google.com/identity/protocols/OAuth2
[Google API client library python]: https://developers.google.com/api-client-library/python/guide/aaa_oauth
[Using OAuth2.0 for web application python]: https://developers.google.com/api-client-library/python/auth/web-app

[Select id with space]: http://stackoverflow.com/questions/596314/jquery-ids-with-spaces