# Oximeter Monitor
Project made for my Microcontrollers class, the goal of this project is to collect the heartrate and oxygen saturation data using the ESP32 microcontroller
and the MAX30100 sensor. The whole project is divided into 3 parts/repositories: the [microcontroller firmware](https://github.com/LaBatata101/oximeter-esp32-firmware), the [REST Api](https://github.com/LaBatata101/oximeter-rest-api) for the data management and the [Telegram bot](https://github.com/LaBatata101/oximeter-telegram-bot) for real time data visualization.

An overview of how all the parts works together. When the user puts the finger in the MAX30100 sensor the ESP32 starts reading the data coming from the
sensor every second and then sends the data to the REST Api, for later consumption by clients of the Api. There is two ways to visualize this data in real time, 
the first one, the ESP32 hosts a web page that can be accessed with the `http://oximetro.local` URL (the mDNS protocol which is used here for the `oximetro.local` domain name doesn't work on android devices). The second way is through the Telegram Bot, after starting a conversation with the bot
you can type the command `/monitorar` to start monitoring the data from the sensor every second or so (the ESP32 can take up to 5 seconds to send the data to REST Api so some of the data shown by the bot may be repeated), this data is fetched from the REST Api by the bot, to stop monitoring just type the command `/parar`.

The REST Api is a basic CRUD, offering 5 routes to manipulate the data, more information can be found in the REST Api repository.

The installation and running instructions can be found on the repositories mentioned above.
