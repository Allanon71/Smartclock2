## SMARTCLOCK
> Author  : Fabio Falcucci (Allanon)  
> Contact : info@a-mc.biz  
> License : Freeware  

### What is smartclock?
Smartclock is an evolution of a project I started some time ago. It is an application that can display a clock, weather data and news.
I developed this program for my personal use since I had a rpi4 laying around on my desk, I also needed a nice, nerdish and cute clock able to display animated Gifs, still images, clock in several layouts, current date, current weather and forecasts, I also needed an rss viewer for the latest news.
Have a look at the `screenshot` folder to see what you can get with this program.
[![sc2-anim.gif](https://i.postimg.cc/3JS62TTt/sc2-anim.gif)](https://postimg.cc/zVh0143h)

### Warning for Linux users
If you are going to run this program on Linux, you may encounter an error related to libSSL, to resolve the problem you have to install the SSL lib version 1.0.0.  
Here is the link for the **Raspberry Pi** that I used to resolve the problem on my little machine: https://packages.debian.org/jessie/armhf/libssl1.0.0/download
And here is how to install it: `sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u12_armhf.deb`

### Features  
* Available source code
* Free
* Support for images (most common formats are supported)
* Support for animGifs as background or as objects
* Support for clock: digital, analog and graphicals views
* Support for OpenWeather to retrive current weather and forecast (you need a free api key)
* Support for news ticker using an RSS feed url
* Multiple layouts: click (or touch) the screen to switch the another layout
* Compatible with any system supported by Hollywood-MAL

### Programming language
This program has been coded using Hollywood-MAL v9  
https://www.hollywood-mal.com

### How does it work?
You need to configure the master configuration file `sc2conf.txt` where you can setup the main options which are:   
* Translations : you can assign your own translations for your language
* Text colors : define your preferred colors for the text elements
* Weather data : set the interval between each update, which data you want to display for the current weather and for the forecast, the units to use, the language for the api, your apikey, your location's coordinates, and how many forecast days you want to display.
* News data : the rss feed url, the update frequency and a title
* Actions : set if you want to switch layout clicking on the screen or not
The default behaviour is:  
* Left mouse click (or touch) to switch layout
* Right mouse click to quit

### Using OpenWeather
OpenWeather provide a free key for standard users that do not exceed a fixed amount of calls in the given frame time. This is perfect for our use so you have to go the <a href="https://openweathermap.org/api" target="_blank">OpenWeather</a> website, create a free account and create a free api key, then put the key into the `sc2conf.txt` file and you are done.

### Clock definition files  
As said you can define how many layouts you want, there is no limit since they are loaded dynamically.
You have to place your layouts into the `/data/layouts` folder, when you run the program this folder will be analyzed.

#### Supported clock objects
Here is a brief description of supported objects that you can place in your layouts, please have a look at the provided examples for more details.
##### Screen Section
Here you can define the screen properties, the native buffer size and if the window should have borders, gadgets, etc...
```plaintext
native_width            : Native buffer horizontal resolution
native_height           : Native buffer vertical resolution
scaled_width            : Screen horizontal resolution
scaled_height           : Screen vertical resolution
borderless              : 1:Borderless window, 0:Borders enabled
sizeable                : 1:Window can be resized, 0:Window cannot be resized
fixed                   : 1:Window can be moved, 0:Window cannot be moved
nomodeswitch            : 1:Alt-Enter disabled, 0:Alt-Enter enabled (for fullscreen)
noclose                 : 1:Close gadger disabled, 0:Close gadget enabled
hidepointer             : 1:Hide mouse pointer, 0:Show mouse pointer
smoothscale             : 1:Smooth graphics on resized graphics, 0:Do not smooth graphics
```
##### Layout Section
In this section you can define the items you want to put into the layout, remember that the objects will be rendered in the same exact order you define them.
Each item is defined into a numbered sub-section like in the following sample:
```plaintext
{ layout
  { #0
    // Animated Background
    [SST]type = background
    [SST]name = bganim
    { geometry
      [SIN]x = 0
      [SIN]y = 0
      [SIN]w = 800
      [SIN]h = 480
      }
    { params
      [SST]file   = data/ANM_AnimBG_01.gif
      [SIN]fps    = 10
      [SBL]smooth = 0
      }
    }
  { #1
    // Digital Clock
    ...
```
Here is a brief list of all supported items, remember that everything related to pixels can be expressed in absolute values or relative to the screen buffer size, in the latter case you have to provide the optional tag `[SBL]relative = 1` :
* `geometry`
    * `x` : horizontal position
    * `y` : vertical position
    * `w` : item width
    * `h` : item height
    * `sw` : optional, scaled item width
    * `sh` : optional, scaled item height
* `type` : The object type which is one of the following: `background`, `text`, `scroller`, `special-clock`
* `name` : A unique name to assign to the object
* `params` : A section with further parameters depending on the object `type` please have a look at the provided examples.

### Executables
Executables are provided for several platforms

### Disclaimer
**This program is free** and is provided with some example layouts, these examples make use of some graphic art I found on Internet, mostly animGifs created by other people from old games: **I do not own this content. All credits go to its rightful owners**.
The inclusion of such art is intended as "fair use".  
No copyright infrangement intended.  
  
All code in this repository is released under the terms of the MIT license.

### Media
if you are curious to see what it looks like take a look at the screenshots

### Support me
If you like my work and you want to buy me a coffee you can support me on Patreon https://www.patreon.com/Allanon71  or using PayPal to mailto:hijoe@tin.it     
The program is FREE :D
