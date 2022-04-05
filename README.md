# Pixel_Image_Recognition

   This is some software I wrote to get past security features on WAF's that deny requests for source HTML. At the time of creaton I was trying to create a bot that could watch bestbuy for new gpu's, and also watch webistes like offerup for good used deals of stuff. These scripts that I wrote performed for both projects perfectly. In this repository I will give a brief introduction to my program, describe how it works, and go over some varieous uses for the software.   
 
# Brief Intro

   Some websights such 'BestBuy.com', 'OfferUp.com' and 'Creigslist.com' have mitigation strategies to prevent Robots from using their web pages. One of these strategies denies any trafic coming from the requests module in python. 
   
   This picture below is the WAF response from bestbuy.com

![WAF_Response](https://user-images.githubusercontent.com/92893340/161455165-81078a35-0a41-4527-917c-6ec8acf05918.PNG)

   After reciving this message from the websight I realized scraping these websights with the reequests module wasnt going to be an option. The request and BS4 modules at this time were the only way knew how to crawl websites. Whit this being said, I hod no clue how I was going to build my Bot. But after much contemplation a light bulb lit up over my head. I rushed back to my computer and turned to google for its wisdom. I found two modlues that would soon make my idea a reality. These modules were pynput and pyautogui. Pynput is used to simulate user input like moving the curser or clicking the mouse. Pyautogui us used to take screenshots of specifyed portions of the screen. 
   
  I fugured if I can train a bot to know what objects look like on the screen, and also get the location of where that object is on the screen. Then I could have the mouse click on that object. At that point this computer could Thoeretically maneuver around anything on a computer and not get caught by most current anti robot security(not including captchas yet, but maybe soon). To this day that statment remains true. 

# How It Works

I belive the best way to describe how this software works is to describe each script briefly, then walk through the functions. After that I will describe how the pic_in_pic function finds images within other images basid on their pixel order. 

# Scripts

Movement.py
The first script to be dissected is the Movement script. This is my main.py script that I renamed for simplicity. In this script all the instructions are given to the program. Any function that is built in any other script is executed here. It also handles all the user input functions like moving the mouse and clicking. 

Screenshotstuff.py
the screenshotstuff script contains all the functions that gather and filter data on images. A good example of a usfull function in this script is the seperation_selected_area function. Which returns the RGB values of each pixel in a picture inputed as an argument. This script is also home to the fuction pic_in_pic. pic_in_pic is the function that makes this program work. It will get its own explanation after all the scripts have been explained. 

sc_control.py
This script is full of functions that intalize and prepare data for the pic_in_pic function. Each function in this script contains the data for the picture that is being looked for in pic_in_pic. Although sc_control.py is simple its what makes this program versatile.

keypressed.py
In this script there are a few simple functions that are run when typing is necessary. 

scroll.py
Scroll.py is another simple script that is used to scroll down or up a page. 

# Functions
