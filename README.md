# Online Shop Gorgeous

## Table of Contents
- [Overview and goals](#overview-and-goals)
- [Pages](#pages)
- [Design](#design)
- [Functionality](#functionality)
- [Validation and Testing](#validation-and-testing)
- [Deployment](#deployment)

## Overview and goals

This is Code Institute Stream Three Project as part of the Full Stack Development course. The project is focused on
both Front End and Back End Development skills. It is a brand new Django project composed of
multiple apps.

Gorgeous is a fictitious online clothing shop for women. All products are of high quality and newest fashion with
elegant and feminine style to them. The target audience is young and middle age women, who follow fashion, want to look
good and shop online.  

The goal was to create a website for existing and potential customers in order to sell products and manage shop online
and to promote the brand. The following requirements were set and met:
- the website is user and mobile friendly
- the website design helps to create a good brand image
- the homepage calls for action to make customers shop
- shop managers can manage products, stock and orders online
- customers can view and sort, filter products on the website, register, add products to the shopping bag, edit
shopping bag, buy products and view orders on their account, as also update their delivery address or other account
details and get customer support contact information.

The project was made keeping in mind possible future functionality updates.

## Pages

The website has the following pages:
- Homepage
- Products page with all products
- Products page for each category (dresses, tops, trousers, coats, shoes)
- Individual product page
- Shopping bag page
- Checkout page
- Login/ Register page
- Account page
- Account delivery address edit page
- Account details edit page
- Account password change page
- Account password change complete page
- Orders page
- Individual order page
- Contact page

## Design

The wireframes were created during the initial planning stage before starting the project development.

UX and UI design ideas were taken by looking at other online shop examples, like Shopify themes, ASOS, New Look,
Missguided, PrettyLittleThing, River Island, Forever 21 etc.

Shop logo was created using Adobe Illustrator.

The following colors used for the design - gold, black, white, grey. Gold color is used for logo, buttons and slider
arrows, grey color is used as a background color for footer and shopping bag, checkout containers, as also for borders.
Font is either in black or white, black color is used for copyright and promotion block background, as also for icons.
[Colour Contrast Check](http://leaverou.github.io/contrast-ratio/) was used to check color contrast and choose the
right color shades.

The website is made as responsive as possible using media queries and jQuery.

Bootstrap library was used for the website grid, as also for accordion, tabs and dropdown menu functionality.

[Font Awesome Icons](http://fontawesome.io/icons/) were used for different icons on the website (account, shopping bag,
burger menu, social media, arrow icons etc.).

The shop logo sits at the top middle of the page to make it stand out. On desktop site the size of the logo decreases
when you scroll down the page so the header does not take too much space.

As for the navigation the menu is just below the logo on the desktop site with links to the account dropdown menu and
shopping bag on the right side. And on the mobile site there is a burger icon on the left of the logo for the menu. On
click the menu slides in from the left and can be closed by sliding it left using a finger or by clicking on the burger
icon. It is achieved using [SlideOut.js library](https://slideout.js.org/).

In order to avoid dropdown menu from closing when clicking outside it on mobile
[Mike Kane solution](https://stackoverflow.com/questions/19740121/keep-bootstrap-dropdown-open-when-clicked-off)
was followed.

The header with logo and the menu is fixed both on desktop and mobile site so it can be easily accessible at any time.

The homepage uses full screen slider at the top of the page as also a parallax image on the page with a call for action
to attract customers. [Renan Breno example](https://codepen.io/RenanB/pen/GZeBNg) was followed to create parallax
effect. All website pages are kept as clean as possible using white space to avoid distractions and improve readability.

[Slick.js slider](http://kenwheeler.github.io/slick/) is used to create all sliders on the website as it is easily
customizable and works perfectly on all browsers.

One page (Login/register page) is used as for both logging in and for registration. The page has two tabs. One tab with
login form and one tab with registration form. So users can switch to the tab they need. loginRegisterTabs jQuery
function is used to show selected tab on page refresh.

All accounts pages have the same layout with account navigation on the left which has two sections: My details and
My orders. The page the customer is on is underlined (either My details or My orders link). 

On the products page the navigation for filtering products is displayed on the left as usually on shopping websites.
Customers can expand or close filters. On the mobile site there is a button at the top of the products list to open
filters in a pop up screen which overlays all the page (except header). It gives enough space for customers to view and
select filters. There is a button to either reset filters or to close them. Select menu is used to sort products, It is
positioned at the top right of the products list on desktop site and next to filters button on the mobile site.
[noUiSlider.js library](https://refreshless.com/nouislider/) is used to filter products by price. And
[wNumb.js](https://refreshless.com/wnumb/) library is used to format numbers for noUiSlider.

On the individual product page the product image thumbnails are displayed on the left of the main product image so the
users do not have to scroll down to click on thumbnails. Users can click on thumbnails or on slider arrows to view
different product images. Users can also click on the main image to zoom it in. [jQuery Zoom library by Jack
Moore](http://www.jacklmoore.com/zoom/) is used for that purpose. Magnifying glass cursor is used on product image
hover. But for Internet Explorer the crosshair cursor is used instead as a fallback. On the mobile site the image
thumbnails are not displayed to save space but they are still displayed on tablet size screen.

On the Shopping bag and Checkout page there are different sections with grey background to separate content for
readability. On the Checkout page, for example, order form is on the left and product list is on the right. Product list
can be closed or expanded (it is closed on mobile by default to save space). Each product also has a borderline to
separate it from other products.

## Functionality

Django project has the following apps:
- [gorgeous](#gorgeous-app)
- [home](#home-app)
- [accounts](#accounts-app)
- [products](#products-app)
- [cart](#cart-app)
- [orders](#orders)

In the templates folder there is a folder for each app templates.

### Gorgeous app
The main app gorgeous has urls file where urls from all other apps are imported, as also admin.site, tinymce and
django.contrib.auth urls (for updating password). Gorgeous app has one view to render
contact page.

### Home app
Home app has one view to render homepage. Popular products data is passed to the template to display bestsellers in the
"Popular this week" slider. At the moment bestsellers are filtered from all products sold (as there won't be orders
made every week). But the logic for filtering the most sold products this week is in place and commented out in the
view.

### Accounts app
Accounts app has customized user model. It accepts email as a username and has fields first_name and last_name.
Superuser must be created in the back-end using "python manage.py createsuperuser" command. And first_name and last_name
fields are also required when creating a superuser. Superusers can be shop managers. However they are not supposed to
shop on the website. It can be changed in the future though if necessary. Accounts app also has customized authenticate
and get_user function for user.
[Vitor Freitas guide](https://simpleisbetterthancomplex.com/tutorial/2016/07/22/how-to-extend-django-user-model.html#abstractbaseuser)
was followed to create customized users.

Address model is used to save customer's delivery address.

Accounts app has UserRegistrationForm, UserLoginForm, UserDetailsForm and AddressForm. UserRegistrationForm and
AddressForm is used for registration. AddressForm is also used to edit customer's address. UserLoginForm is used for
logging in to the account. UserDetailsForm is used to edit user's details. 

Login and registration form data is submitted using ajax to avoid page refresh. On success the user is redirected to
their account page and if form validation failed the error message is displayed for the user.

In order to check which form has been submitted (as they are on the same page) submit button value is used.

Account page displays user details and their address. There is a link to edit user details, user password or to edit
user address. When user clicks on any of the links they are redirected to another page for editing the necessary
details. They can click cancel to return to account page and if the click save, form validation will take place. In
case of success they will be redirected to account page. UserDetailsForm data is submitted using ajax in order to
display a message to the user if an email address has been taken already.

When user clicks on logout they are redirected to homepage.

### Products app

Products app has several models:
- Category model to sort products by category.
- Size model to apply different sizes for each product.
- Color model to apply different colors for each product.
- Image model to upload several images for each product. It has product field as a foreign key.
- Product model to create products. Product model has category as a foreign key and size and color fields as
ManyToManyFields, meaning that each product can have several sizes, colors and each size, color can belong to different
products. Product model also has fields name, description, price and created.
- Stock model saves amount available for each product with specific size and color. Amount is PositiveIntegerField and
product, size and color are foreign keys.

Category, Image, Product, Size, Color, Stock models are included on admin site so they can edit them or add new.

Products app has three views. One view is to render products list. It has two urls, one for viewing all products and
one for viewing specific category products. The view checks if category_name argument is passed in url. If it is passed
in url the page renders only specific category products and also it does not show a filter to filter products by
category. It also changes the title of the page accordingly.

Only products which are in stock are displayed on the page.

Ajax is used to filter products by category, size, color and price as also to sort them by new in, low to high or high
to low. Every time a user selects a filter checkbox, updates price range slider or uses sort menu ajax makes get
request to the view with selected data and products are filtered or sorted in the view using the selected data. The view
renders a separate html file with new products data and returns a response with products html to ajax. This html is then
placed in a specific container on the page.

Django paginator is used to show products on different pages.

Individual product page displays information about specific product. It shows product images on the left side and
product description on the right side. The page displays all sizes in a select menu. If size is not in stock the option
is greyed out and it says next to size name that it is out of stock. So users can only add items to bag which are in
stock. 

Product description is entered on admin site using tinymce text editor. And then it is displayed in the template using 
autoescape tag to escape HTML. 

### Cart app

Cart app was created following Antonio Mele guide in the book Django By Example.

The app has file cart.py which has different functions for the cart class. The cart is stored in the session. When the
cart is initialized in the view the init function checks if the cart is already stored in the session, and if not, it
creates an empty cart in the session.

CartForm is used to add products to the cart or update them in the cart. It has a field quantity with select options
from 1 to 10 and it has hidden field update. Its value is false by default but if form is used in the shopping cart to
update items in the bag the update field value is changed to true in this case.

The function add in the cart.py file is used for changing items in the cart. It has several conditions. If the cart is
empty, the function adds new product to the cart. If the cart is not empty, the function checks if this product is
already in the cart and which size is in the cart. And then the function either updates size or quantity accordingly.
It also checks if the quantity requested is available in stock. When changes are made the function save is called to
save the cart.

CartForm is used on the product page to add product item to the shopping bag. The quantity field is hidden to add one
item by default to the cart. When user clicks on "add to bag" button the post request is made to the cart app view 
using ajax to add product item to the shopping bag. In case of success ajax shows the message that product was added to
the bag mentioning product name and size. If product size is not available anymore (number of items for this size in
shopping bag exceeds the amount in stock) ajax displays a message that this product in selected size is not available
anymore.

On shopping bag page the user can see items in the cart - product image, name, price, selected size and quantity. There
are select menus for size and quantity so users can update values. If size is out of stock the option will be disabled
so users won't be able to choose size which is not in stock. Ajax is used to update the shopping bag. When user selects
a new size or new quantity, a button "update" and also link "cancel" appears. If user clicks on "cancel" the buttons
will disappear and the size and quantity values will change to initial ones. If user clicks on "save" the buttons will
disappear, new values will be selected and prices will be updated in the cart.

Class cart in cart.py has also functions to calculate subtotal, delivery and total price for the cart, as also to
iterate through cart items. Delivery price is £0 if user has £75 or more worth items in the cart. Iteration function
adds additional information for each item in the cart which is used in the template. Cart also has function remove to
remove item from the cart and clear function to empty the cart.

To remove the item from the cart, another url is used to call remove function. After the item is removed from the cart
the page refreshes. If the cart is empty the shopping bag page displays a message informing that shopping bag is empty
and a button "shop now".

Context processor is created for the cart so the total cart price would be available on each page. It is displayed in
the header next to shopping bag icon.

And session is set to expire on closing browser in settings. So the user will be logged out and shopping bag empty after
user closes their browser.

### Orders app

Orders app models were created following Antonio Mele guide in the book Django By Example.

Order model is used to create orders. Each order stores address as a string so it would not change. Order also has
status field which by default is processing. Shop managers can change order status on the admin site either to
dispatched or to delivered. Order has field created (date and time of order creation), updated (date and time of last
order update) and stripe_id field to store Stripe charge id. It is empty by default. Order also has foreign key to the
user to find specific user orders. Order model has functions to calculate subtotal, delivery and total cost similarly
as the cart has.

OrderItem model has foreign key to the order, product and size. It has field price and quantity as well. OrderItem has
also function to calculate its cost (price multiplied by quantity).

Order app has PaymentForm for registering order. It has fields for billing address and card details as also stripe_id
field.

Checkout view gets information from the cart about the product items added to the cart. It renders a template which
displays delivery address on the left with a payment form below and products list with prices on the right. User is able
to tick "use delivery address" in billing address section and the form will be filled in with delivery address
information.

Stripe id is generated on form submission using functions in stripe.js file. This stripe id is then used
to create a stripe charge. If form is not valid or payment was unsuccessful page refreshes and shows error messages for
the user. If form is valid, stripe charge is created and if payment is successful order and order items are created as
well. Stock is updated at the end as well and shopping bag cleared. User is redirected to their order page which
displays information about the order.

There is also a view to display all orders on the customer's page. The table is used to display orders information:
columns with order date, order number, items number, total price, order status, each row has button "view order" on the
right. On mobile screen the table shows only two columns - order date and order status, each row with a button "view"
on the right.


