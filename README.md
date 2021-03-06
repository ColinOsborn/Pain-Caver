## PAINCAVER

[LIVE ON HEROKU](https://paincaver-app.herokuapp.com/) || [GITHUB](https://github.com/stevepentler/Pain-Caver) 

#####[See a gif of the production site!](http://g.recordit.co/NSp5fiAbG8.gif)

#### A personal effort from: 
[Steve Pentler](https://github.com/stevepentler) 

####Pitch

The most concerning aspect of running can be testing your limits, especially when taking the leap from 26.2 miles to the trail ultra-marathon circuit. Wouldn't it be great if you could compare workouts/races that you have already completed to the races you want to register for?

####Solution

*PAINCAVER* is a tool that consumes runners' GPS data and calculates how each specific workout/race compares to famous races, like the Boston Marathon or the Leadville 100. The weighted calculations are based on distance, elevation gain, max elevation, and average heart rate. 

In addition to the difficulty comparison, this application also maps the exact path of a logged workout on Google Maps, and provides local trail recommendations complete with maps and directions. 

####Integrations

This app consumes four API's. The [Strava API](https://strava.github.io/api/) with the strava-api-3 gem as well as handrolled Faraday endpoints, [TrailAPI](https://market.mashape.com/trailapi/trailapi) with handrolled Faraday endpoints, as well as the [Google Maps JavaScript API](https://developers.google.com/maps/documentation/javascript/) and the [Google Maps Embed API](https://developers.google.com/maps/documentation/embed/). 


####Skills Utilized:

Rails 4.0, OmniAuth2, Caching, Skylight Performance Metrics, Mechanize/Nokogiri Scraping, Heroku Deployment, VCR/Webmock testing, Faraday, Materialize, CSS, HTML

####Challenges:

- Caching: proved to be the greatest challenge, as this was the first application where performance has been a priority. Caching can present some unexpected behaviors. At one point I cached a partial that included a form, which caused issues, but only on the second time a view was visited. It took a while to trace back this error, and taugh met the importance of dynamically named fingerprinting.

- Presenters: Upon switching to presenters to organize my controllers/views, I forgot to memo-ize a couple instance variables, which destroyed my loading times. Each instance was hitting an API, and caused loading times to jump to 17 seconds!

- Scraping: I received a crash course in scraping with mechanize/nokogiri. I was able to scrape plain html, but the content I wanted was nested under hidden JavaScript tags. I'll get back to scraping once I polish up my JavaScript debugging skills. 

####Testing:
- 99.71% at 90.99 hits/line from SimpleCov
![](http://i.imgur.com/DXjLuFo.png)

####To Run this Application Locally: 

If you wish to download the project and set it up locally, run the following commands:

```
$ git clone https://github.com/stevepentler/Pain-Caver.git
```
```
$ bundle
```
```
$ bundle exec figaro install
``` 
- This sets up figaro, a gem that organizes environment variables, on your local machine. You will need to obtain API keys from Strava, Google Maps, and TrailAPI, then save them in your `application.yml` file.
```
$ rake db:reset
```
- This application utilizes a Postgres database. Ensure that Postgres is running. The `rake db:reset` command is equivalent to `rake db:create`, `rake db:migrate`, and `rake db:seed`.

```
$ rails s
``` 

- Run this command in a seperate terminal pane to start the actual Rails server
- Visit `http://localhost:3000` to see the application on your local server

```
$ rake test
```
- API keys must be properly installed to run test suite.
