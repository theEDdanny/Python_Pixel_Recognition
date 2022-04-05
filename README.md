# Pixel_Image_Recognition

   This is some software I wrote to get past security features on weblights that deny requests for HTML. In this repository I will give a brief introduction to the 
   program, describe how it works, and go over some varieous uses for the software.   
 
# Brief Intro

   Some websights such 'BestBuy.com', 'OfferUp.com' and 'Creigslist.com' have mitigation strategies to prevent Robots from using their web pages. One of these strategies denies any trafic using the requests module in python. 
   
   This picture below is the WAF response from bestbuy.com

![WAF_Response](https://user-images.githubusercontent.com/92893340/161455165-81078a35-0a41-4527-917c-6ec8acf05918.PNG)

   After reciving this message from the websight I realized scraping these websights with the reequests module wasnt going to be an option. I hod no clue how I was going to build  my Bot. But after much contemplation a light bulb lit up over my head. I rushed back to my computer and turned to google for its wisdom. I found two modlues that would soon make my idea a reality. These modules were pynput and pyautogui. Pynput is used simulate computer input like moving the curser or clicking the mouse. Pyautogui us used to take screenshots of specifyed portions of the screen. 
   
  I fugured if I can train a bot to know what things look like on the screen, and also get the location of where that thing is on the screen. Then thoeretically, the      bot could operate the entire computer. 

# How It Works

I belive the best way to describe how this software works without writing a book is to describe each script briefly, and describe how the pic_in_pic function finds images basid on their pixel order. 

Movement.py

The first script to be dissected is the Movement script. This is my main.py script that I renamed for simplicity. In this script all the instructions are given to the program. Any function that is built in any other script is executed here. It also handles all the user input functions like moving the mouse and clicking. 

Screenshotstuff.py

the screenshotstuff script contains all the functions that gather and filter data on images. A good example of a usfull function in this script is the seperation_selected_area function. Which returns the RGB values of each pixel in a picture inputed as an argument. This script is also home to the fuction pic_in_pic. pic_in_pic is the function that makes this program work. It will get its own explanation after all the scripts have been explained. 

sc_control.py

This script is full of functions that intalize and prepare data for the pic_in_pic function. Each function in this script contains the data for the picture that is being looked for in pic_in_pic. Although sc_control.py is simple its what makes this program versatile.\

keypressed.py

In this script there are a few simple functions that are run when typing is necessary. 

scroll.py

Scroll.py is another simple script that is used to scroll down or up a page. 
