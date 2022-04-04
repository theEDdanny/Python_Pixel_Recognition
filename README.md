# Pixel_Image_Recognition

   This is some software I wrote to get past security features on weblights that deny requests for HTML. In this repository I will give a brief introduction to the 
   program, describe how it works, and go over some varieous uses for the software.   
 
# Brief Intro

   Some websights such 'BestBuy.com', 'OfferUp.com' and 'Creigslist.com' have mitigation strategies to prevent Robots from using their web pages. One of these strategies
   denies any trafic using the requests module in python. 
   
   This picture below is the WAF response from bestbuy.com

![WAF_Response](https://user-images.githubusercontent.com/92893340/161455165-81078a35-0a41-4527-917c-6ec8acf05918.PNG)

   After reciving this message from the websight I realized scraping these websights with the reequests module wasnt going to be an option. I hod no clue how I was going to build  my Bot. But after much contemplation a light bulb lit up over my head. I rushed back to my computer and turned to google for its wisdom. I found two modlues that would soon make my idea a reality. These modules were pynput and pyautogui. Pynput is used simulate computer input like moving the curser or clicking the mouse. Pyautogui us used to take screenshots of specifyed portions of the screen. 
   
  I fugured if I can train a bot to know what things look like on the screen, and also get the location of where that thing is on the screen. Then thoeretically, the      bot could operate the entire computer. 
