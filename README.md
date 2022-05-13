# Pixel_Image_Recognition

   This is some software I wrote to get past security features on WAF's that deny requests for source HTML. At the time of creaton I was trying to create a bot that could watch bestbuy for new gpu's, and also watch webistes like offerup for good used deals of stuff. These scripts that I wrote performed for both projects perfectly. In this repository I will give a brief introduction to my program, describe how it works, and go over some varieous uses for the software.   
 
# Brief Intro

   Some websights such 'BestBuy.com', 'OfferUp.com' and 'Creigslist.com' have mitigation strategies to prevent Robots from using their web pages. One of these strategies denies any trafic coming from the requests module in python. 
   
   This picture below is the WAF response from bestbuy.com

![WAF_Response](https://user-images.githubusercontent.com/92893340/161455165-81078a35-0a41-4527-917c-6ec8acf05918.PNG)

   After reciving this message from the websight I realized scraping these websights with the reequests module wasnt going to be an option. The request and BS4 modules at this time were the only way knew how to crawl websites. Whit this being said, I hod no clue how I was going to build my Bot. But after much contemplation a light bulb lit up over my head. I rushed back to my computer and turned to google for its wisdom. I found two modlues that would soon make my idea a reality. These modules were pynput and pyautogui. Pynput is used to simulate user input like moving the curser or clicking the mouse. Pyautogui us used to take screenshots of specifyed portions of the screen. 
   
  I fugured if I can train a bot to know what objects look like on the screen, and also get the location of where that object is on the screen. Then I could have the mouse click on that object. At that point this computer could Thoeretically maneuver around anything on a computer and not get caught by most current anti robot security(not including captchas yet, but maybe soon). To this day that statment remains true. 

# How It Works

Here I’m giving a brief description of how my program works. I built a simple script named demonstartion.py that opens chrome and maximizes the window regardless of where the maximize button is on the screen. 

I have chrome pinned on my taskbar. So it will always have the same coordinates on the screen. This being said we can tell the computer to click those coordinates and it will be reliable every time. In this case these coordinates are (760, 1038).

Soon after the click chrome will open. Our goal is to maximize the window, but the maximize button won’t always be in the same place. Because of this we need to run the pic_in_pic function to find the maximize button on the screen and return its coordinates. To do this we need two things. First, we need to know what the maximize button looks like. Second, we will need a screenshot of the screen to sift through and find the maximize button. Image of the maximize button needs to be noted before the program is run (this is done my cropping a screenshot). The screenshot however needs to be retaken every time the program is run. The screenshot and the maximize button are shown below.


![shot](https://user-images.githubusercontent.com/92893340/168201851-14c283a7-30df-4fe4-9615-6a103d2e096d.png)
![max_button](https://user-images.githubusercontent.com/92893340/168203000-694aec79-e041-4ca9-8507-4c0bb1fefbf0.PNG)

Now that we have this data, the pic_in_pic function can go to work to find the maximize button and click on it. This is where the fun begins! 

Now, pip_in_pic works by using the first pixel in the target picture and comparing it to every pixel in the main picture (the picture the program in looking through). Every time the RGB value of the first pixel in the target pic matches a pixel in the main pic an event is triggered. This event takes the length of the first row in the target pic and looks ahead that many pixels in the main pic. If every pixel in the first row of the target pic matches the results from this test, 1920 is added to every pixel number. By adding 1920 to these pixels in the first row, the second row is found. From here the function can continue to compare RGB values. This last process is repeated for every horizontal row that the target pic has(the height of the target picture).
If all goes well and every RGB value matches, then all that needs to be done is to return the location of the target pic. There is a process to find this location. To find the location of the first pixel in coordinates we need to divide the value returned by 1920, if there is a remainder a value of one will be added to result. This result will represent the vertical value of the coordinates. The horizontal value is the remainder of the division problem that was just performed.



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
