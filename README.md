# How To Use The Twice Edition

The twice edition of the script contains all of the filtering options of the original script + fully automates checkout. This requires quite a bit of setup so I'll list the options available and how to get started.

# Available Settings
| Option      | Description |
| ----------- | ----------- |
| Filter On Load      | Whether or not to filter the product page by the filter criteria when the page loads. Defaults to false       |
| Deafult Filter Mode   | Which filter mode to use. Defaults to User Input.        |
| Default Filter Text      | What text to automatically fill in as search criteria when the page loads. If the filter mode is set to User Input, products will be filtered by this text. Defaults to an empty string     |
| Default Dropdown Value   | What dropdown option to select by default. If the filter mode is set to Dropdown Value, prdoucts will be filtered by this selection.  Defaults to (none)      |
| Price Range Start   | The minimum price for a product to be shown. Defaults to 0 if no number is entered         |
| Price Range End      | The maximum price for a product to be shown. Defaults to 9999 if no number is entered.       |
| Allow Unsaved Products  | Whether or not to automatically checkout if the script detects products that are in your cart but are NOT in your ATC Part Numbers list. For example, if your ATC Part Number list only contains GPUs, but during a drop you also added a power supply, if this option is false the script will not automatically check out. If this option is true, the script will checkout with both products. This is to prevent accidental purchases of unneeded products. Defaults to false.        |
| ATC Part Numbers   | A list of part numbers that should be searched for and automatically added to the cart if they are instock. Product numbers should be separated by a comma with no spaces. Default is an empty string.     |
| Auto Apply Coupon Code   | Whether or not to automatically apply the coupon (EVGA elite) code specified in the next option. Defaults to false.        |
| Auto Checkout   | Whether or not to automatically begin the checkout process. Only supports PayPal. Defaults to false         |
| Auto Open Billing Page   | Whether or not to automatically open the billing page regardless of the status of "Auto Checkout". Good for quickly getting to the billing page and then doing the rest of the checkout process manually.        |
| Checkout Mode   | Whether or not to go through the full checkout process. Full checkout will go from cart > shipping > billing > paypal (manual) > submit order. The hot cart trick (requries setup) will go cart > billing options > paypal (manual) > submit order.        |
| Coupon Code   | The coupon (EVGA Elite) code you wish to apply. Defaults to an empty string.        |
| Dummy Product Part Number      | The part number for the dummy product to be used for the cart trick. If this product exists in your cart when the cart is loaded, the script will automatically remove it to avoid missing a checkout because the dummy product was out of stock (also saves you money yay). Default is an empty string.       |
| Show product list   | Whether or not to show the list of products that are in your add to cart list. The script will check **once** on refresh, and products will turn red when out of stock, and green when in stock (which will break the loop and take you to your cart).         |
| Test Mode   | **IMPORTANT:** Whether or not to run the script in test mode. If this option is true, the script will run all the way until the final step, but will not actually confirm your order. This is great for testing your setup and making sure everything works. If Test mode is disabled, **the script will automatically purchase products according to your settings if you let it run its course.** Defaults to true.       |


# About the extension
The extension has a popup window that opens when you click the extension icon. This is where you will do all of the setup for background script, which is what automates the checkout process. You can also set up filtering options, but you probably won't need them if you're using auto checkout.
   
Also note that this script will only work for one product at a time. EVGA limits orders to one GPU per order anyway, so there's no plans for support for multiple SKUs at once. You *could* however, set this script up in multiple chrome profiles with multiple accounts.

# Important note about a checkout issue I discovered.
On one drop, there was an issue where PayPal would not open from the billing page, with or without the script. I recently discovered that there appears to be an expiry on your cart. If you set up a hot cart, it may expire before the next drop. If this happens, no matter what you do you will not be able to finish checkout.

To solve this, remove any items from your cart and add a completely different item. Go through the shipping page and the billing page and try to open PayPal. If it opens, you should be all good.

If that doesn't work, go to the *Cart Page* and try opening up the developer console, go to Application > Local Storage and clear the item "_boomr_akamaiXhrRetry". Then repeat the steps above. You can also try clearing cookies and logging out/back in again.

Worst case scenario, create an entirely new profile and set the extension and your cart up again.

# Stock Monitoring
The script checks for new messages in a stock alert channel, and automatically opens the B Stock page when new messages are detected. Log in to discord in your browser with the extension installed, and navigate to [evga-bstock](https://discord.com/channels/767566223729754122/869681156797390849)

# Setting up the script
1. Install the extension as an unpacked extension. To do this go to your extensions on Chrome, toggle Developer Mode on, and click "Load Unpacked". Then, select the folder you extracted from the zip I provided.
2. Click on the extension icon (you may need to pin it depending on how many extensions you have)
3. Fill in the ATC settings to your liking. I **highly** recommend leaving "Test Mode" enabled until you've tried the extension out. You can leave the "ATC Part Numbers" blank for now, as that will get auto filled by the "Product Select" tab when we get there. Refer to the "Available Settings" section if you're unclear on what any of the settings do.
4. Go to the Product Select tab. Toggle any products that you want the script to search for and checkout with. They will be prioritized in the order that you toggle them (remember, the script will only checkout one product at a time due to EVGA order limits). If you mess up the priority, you can reorder them from the "Product Priority" tab.
5. Return to the ATC Settings, and make sure that "ATC Part Numbers" is filled in. If it is, you're all set!
6. If you want to add a custom product to the list that wasn't available in the product picker, add it by using the "Part Number" listed on EVGA's website. Make sure you separate it with a **comma with no spaces**, just like the rest of the list. If you leave whitespace the script probably won't pick it up.
7. You can also set up filtering options in the filter tab. This will hide any elements on any product page that do not fit your filter criteria, which could make it easier to catch drops manually.

# Setting up your cart
You can skip this section if you know how to set up the cart trick.
1. Add your dummy product to your cart. Make sure that you have put your dummy product part number into your settings correctly. If you don't, the script will open a new tab automatically. If you have set up the cart before, the script might try to checkout with that product (you can just close the tab quickly to cancel it).
2. Click go to checkout. Fill in your shipping info, choose your shipping option, and continue to the next screen.
3. Your cart is now hot and ready to go for a drop! Open your settings pane and verify that your settings look the same as they did on the product pages.


# Doing a test run
## Pre Test Run Warning
PayPal WILL preauthorize the charge on your card, even if you don't finish checkout. These charges should drop off within a day or so. Mine dropped off within a few hours. Choose a cheap item as your dummy product!

## Test Run Instructions
1. **MAKE SURE THAT TEST MODE IS ON. IF IT'S NOT YOU'RE GOING TO END UP PURCHASING A PRODUCT YOU DON'T NEED.**
2. 
    * Make sure you have a product that is currently in stock in your ATC Part Numbers list. You'll probably have to add it manually.
    * Make sure you don't have anything else in your cart besides your dummy product.
    * If you did have something else in your cart, the script will remove your dummy product and begin checking out with whatever was in your cart. You can cancel any of the page loads/close tabs to cancel the checkout.
3. Go to the B Stock page and watch the magic happen. The script will:
    * Add the test product to the cart
    * Remove the dummy product from the cart
    * Open the shipping page or the billing options based on your settings.
    * Automatically apply your coupon code if you set those settings up
    * Select the paypal option and automatically click the the checkboxes and buttons needed to open PayPal.
    * Automatically click the buttons to finish submitting your order, however if test mode is **ON**, the order will not be submitted, and instead you'll get an alert that the test was successful. Hooray!
    * If test mode was OFF, enjoy your new (refurbished) power supply :KEKW:
4. Close the alert. Open the extension settings and remove the test product part number from the "ATC Part Numbers" list.
6. Go to your cart and remove the test product from it.
9. Go through the "Setting up your cart" section again. Your cart is probably still configured and hot, but it can't hurt to set it up again to be safe. Wouldn't want to miss out on a card because your cart wasn't configured.
10. If you don't want to do any more testing, open your settings pane and turn "Test Mode" to false. You will get a warning that your script is now hot, and if you let it run it will buy whatever is in your list. Click "OK" to confirm the switch, or cancel it to leave test mode on.
11. Congrats! You should be all set up, and ready to cop some GEE PEE YOUZ.
