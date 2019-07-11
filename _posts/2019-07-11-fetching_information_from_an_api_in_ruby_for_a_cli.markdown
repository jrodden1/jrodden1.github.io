---
layout: post
title:      "Fetching Information from an API in Ruby for a CLI"
date:       2019-07-11 15:45:05 -0400
permalink:  fetching_information_from_an_api_in_ruby_for_a_cli
---


In the past I had used JavaScript to get information from an API but had never done it in Ruby before so when a school project came up to build a CLI (Command Line Interface) that needed to scrape info from the Web or use an API, I decided to try to pull information from an API.  But, what should my CLI app do?  After some deliberation and preliminary scouting for APIs, I decided to make a CLI weather *fetching* app that would get information from a weather API.  And so WeatherPup (because it plays fetch 😉) came into existence.  I wanted WeatherPup to fetch weather conditions based on a US Zip Code or a GPS Coordinate pair (a latitude and longitude pair).

The quest then began to:
1. Test and make sure the API I had found would give me the information I wanted
2. Figure out how to pull information in from that API using Ruby 
3. Build the CLI

I decided to use OpenWeatherMap.org's [Current Weather API](https://openweathermap.org/current).  After looking over the documentation I decided to fire up [Postman](https://www.getpostman.com/) to test it out to see what kind of information I would get back from the API after making a call.  I got something like this back.

```
{
    "coord": {
        "lon": -73.93,
        "lat": 40.76
    },
    "weather": [
        {
            "id": 500,
            "main": "Rain",
            "description": "light rain",
            "icon": "10d"
        }
    ],
    "base": "stations",
    "main": {
        "temp": 301.7,
        "pressure": 1012,
        "humidity": 69,
        "temp_min": 299.82,
        "temp_max": 303.15
    },
    "visibility": 16093,
    "wind": {
        "speed": 5.1,
        "deg": 130,
        "gust": 8.2
    },
    "clouds": {
        "all": 90
    },
    "dt": 1562867803,
    "sys": {
        "type": 1,
        "id": 4026,
        "message": 0.0102,
        "country": "US",
        "sunrise": 1562837633,
        "sunset": 1562891284
    },
    "timezone": -14400,
    "id": 0,
    "name": "Astoria",
    "cod": 200
}
```

Cool.  That looks to have the information I want in it for [WeatherPup](https://github.com/jrodden1/weatherpup).  Now, how to get that into something I can work with in Ruby.  Commense web search!  I happened upon [this handy instructional video from Edutechional](https://www.youtube.com/watch?v=mwtKQlu7a08) on how to call a JSON API in Ruby.  While I didn't follow the exact steps he had in the video, it gave me enough information to be dangerous and start tinkering on making the API call myself in WeatherPup.   I installed the [HTTParty gem](https://rubygems.org/gems/httparty) and was ready to give it a whirl.

Do you know what happened on my first attempt?  Failure!  I then tried various different things to get it to work.  Failure, failure, more failure.  It was getting late, but I wanted this to work before I hung up my hat for the day.  Then finally, I decided to just put in the full url (with some variable values interpolated into it) and directly called the HTTParty.get method.  Success! - HTTParty returned a hash with the API information I wanted.  Hooray!   

That moment after the successful API call in my CLI app was exhilarating.  It may not seem like a huge thing -- I just got some weather data -- but I felt like the world was now open to me.  There are thousands of APIs out there and now I know how to pull information from them using Ruby.  The possibilities to create feel endless.  

After this point, I spent the next few days coding up the rest of the CLI.  Feel free to checkout [WeatherPup on my GitHub](https://github.com/jrodden1/weatherpup).  It was such a joy to create WeatherPup from my own imagination and see it go from being a concept to being a functional CLI.  So, aspiring coder, keep at it!  It's worth all the learning, persevering, and hard work.

-Jeremiah



