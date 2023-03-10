# Home Assistant HTML Weather card
Just a place to put a copy of the weather card I use in Home Assistant.

Notes:
  - This is meant to be used with https://github.com/PiotrMachowski/Home-Assistant-Lovelace-HTML-Jinja2-Template-card, inside a card.
  - You will need to change all the sensor names to your own stuff
    - `sensor.weather_update_time` is my own template sensor, the template being `{{int(as_timestamp(states.sensor.toronto_observation_time.last_updated)) | as_datetime}}`. I needed the sensor for other stuff and just reused it here, but you can probably write something better and cleaner which doesn't need another sensor.
  - This relies on locally hosted icons for the current weather condition being located within your Home Assistant config folder; `/config/www/weather`
    - The icons were extracted from the files of [the WeatherCAN Android app](https://play.google.com/store/apps/details?id=ca.gc.ec.weather_app_android.ops&hl=en_US). The icons are found inside the `config.xxxhdpi.apk` file, inside the path `res/drawable-xxxhdpi-v4/`.
    - You can also find the icons hosted on Environment Canada's server; you can use `<td style="width:60px;height:51px;"><img src="https://weather.gc.ca/weathericons/{{ states('sensor.icon_code') }}.gif"></td>` to use those instead of self-hosting. Their icons are lower resolution and a slightly different aspect ratio, which may change things (that's why the style is defining 60x51px). I just copied and pasted an old line of code from before I updated to use local images, so it may not work perfectly if you use it.
  - All integrated links are set up to open in a new tab, because I hate it when links open in the same tab. That's what `target="_blank" rel="noopener noreferrer"` does.
  - This is literally the first thing in html i've ever written from scratch so it's probably terrible, but the final product does look good (to me, at least).
  
IMPORTANT:

If you want to go and play around with this, I recommend that you edit the file **outside** of the card editor in Home Assistant. Saving the changes on the HTML Jinja2 template card will screw up the code formatting something fierce inside the card editor. The final output should still be the same, however. I usually just edit inside a file and then copy and paste the entire thing into home assistant and overwrite everything each time, which is why the card header stuff is still there in this file.

Have fun! If anything breaks, send your complaints to `/dev/null`.
