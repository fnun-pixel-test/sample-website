# JoyMart E-Commerce Website

A fully responsive e-commerce website built with HTML, CSS, and JavaScript. With product listings, shopping cart functionality, and open for Facebook Pixel integration for event tracking.

## Table of Contents

- [Features](#features)
- [Setup Instructions](#setup-instructions)
- [Running Locally](#running-locally)
- [Website Components](#website-components)
- [Facebook Pixel Integration](#facebook-pixel-integration)
- [Monitoring Events in Facebook Events Manager](#monitoring-events-in-facebook-events-manager)
- [API Integration](#api-integration)
- [Screenshots](#screenshots)

## Features

- Integrated with Faker.js and mmockapi.io for dynamic data generation
- Responsive layout for all device sizes
- Shopping cart with add, remove, and quantity adjustment
- Product details page with ratings and description
- Order confirmation flow
- Need to implement - Facebook Pixel event tracking

## Setup Instructions

1. **Clone the repository**
   ```
   bash
   [git clone https://github.com/yourusername/E-CommerceWebsite.git](https://github.com/fnun-pixel-test/sample-website.git)
   cd E-CommerceWebsite
   ```

2. **Project Structure**
   The project has the following structure:
   ```
   E-CommerceWebsite/
   ├── index.html              # Main entry point
   ├── header.html             # Navigation header
   ├── footer.html             # Footer section
   ├── content.html            # Product listings page
   ├── contentDetails.html     # Product details page
   ├── cart.html               # Shopping cart page
   ├── orderPlaced.html        # Order confirmation page
   ├── css/                    # CSS stylesheets
   │   ├── header.css
   │   ├── footer.css
   │   ├── content.css
   │   ├── contentDetails.css
   │   ├── cart.css
   │   └── orderPlaced.css
   ├── js/                     # JavaScript libraries
   │   └── jQuery3.4.1.js
   ├── content.js              # Product listing functionality
   ├── contentDetails.js       # Product details functionality
   ├── cart.js                 # Shopping cart functionality
   └── orderPlaced.js          # Order confirmation functionality
   ```

3. **Facebook Pixel Setup**
   - The website is already configured with Facebook Pixel ID: 476140130512097
   - If you want to use your own Pixel:
     - Create a Facebook Pixel in your Facebook Business Manager
     - Replace the Pixel ID in the following files:
       - index.html
       - contentDetails.html
       - cart.html
       - orderPlaced.html

## Running Locally

Since the website uses XMLHttpRequest to load components, you need to serve it through a web server rather than opening the HTML files directly. Here are three ways to run it locally:

### 1. Using Python (Recommended)

Python comes with a built-in HTTP server that's perfect for local development:

**For Python 3:**
```bash
cd /path/to/E-CommerceWebsite
python -m http.server 8000
```

**For Python 2:**
```bash
cd /path/to/E-CommerceWebsite
python -m SimpleHTTPServer 8000
```

Then open your browser and navigate to: `http://localhost:8000`

### 2. Using VS Code Live Server

If you're using Visual Studio Code:
1. Install the "Live Server" extension
2. Right-click on index.html and select "Open with Live Server"

## Website Components

### 1. Header (header.html, header.css)
- Colorful JoyMart navigation bar
- Logo and search functionality
- Account and cart links
- Category navigation

### 2. Product Listing (content.html, content.js, content.css)
- Hero banner
- Category cards
- Product grid with:
  - Product images
  - Titles and descriptions
  - Ratings and reviews
  - Pricing with consistent 2-decimal formatting
  - Prime badges
  - "Add to Cart" buttons

### 3. Product Details (contentDetails.html, contentDetails.js)
- Product images
- Title, category, and description
- Price information
- Star ratings and review count
- "Add to Cart" and "Buy Now" buttons

### 4. Shopping Cart (cart.html, cart.js)
- List of added products
- Quantity adjustment controls
- Remove item functionality
- Total price calculation
- "Place Order" button

### 5. Order Confirmation (orderPlaced.html, orderPlaced.js)
- Order success message
- Order summary
- Total amount and item count

### 6. Footer (footer.html, footer.css)
- Multiple information sections
- Links to various site sections
- Copyright information
- "Back to top" button

## Facebook Pixel Integration

The website integrates Facebook Pixel for tracking user interactions and measuring conversion events.

### Events Tracked

1. **PageView**
   - Triggered on every page load
   - Helps track overall site traffic

2. **ViewContent**
   - Triggered when a user views a product detail page
   - Tracks which products users are interested in
   - Includes product information: title, category, price, ID

3. **AddToCart**
   - Triggered when a user adds a product to their cart
   - Helps measure intent to purchase
   - Includes product details and quantity

4. **Purchase**
   - Triggered when a user completes an order
   - Measures conversion success
   - Includes order value, products purchased, and quantities

### Pixel Implementation

The Facebook Pixel base code is included in the `<head>` section of each HTML file:

```html
<!-- Facebook Pixel Code -->
<script>
  !function(f,b,e,v,n,t,s)
  {if(f.fbq)return;n=f.fbq=function(){n.callMethod?
  n.callMethod.apply(n,arguments):n.queue.push(arguments)};
  if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
  n.queue=[];t=b.createElement(e);t.async=!0;
  t.src=v;s=b.getElementsByTagName(e)[0];
  s.parentNode.insertBefore(t,s)}(window, document,'script',
  'https://connect.facebook.net/en_US/fbevents.js');
  fbq('init', '476140130512097');
  fbq('track', 'PageView');
</script>
<noscript><img height="1" width="1" style="display:none"
  src="https://www.facebook.com/tr?id=476140130512097&ev=PageView&noscript=1"
/></noscript>
<!-- End Facebook Pixel Code -->
```

Event-specific tracking is implemented in the respective JavaScript files:

- **ViewContent**: In contentDetails.js
- **AddToCart**: In content.js and contentDetails.js
- **Purchase**: In orderPlaced.js

## Monitoring Events in Facebook Events Manager

To monitor the events tracked by Facebook Pixel:

1. **Access Events Manager**
   - Go to [Facebook Business Manager](https://business.facebook.com/)
   - Navigate to "Events Manager" in the left sidebar
   - Select your Pixel (ID: 476140130512097 or your custom Pixel)

2. **View Real-time Events**
   - Click on "Test Events" tab to see events as they happen
   - Use the Facebook Pixel Helper Chrome extension for debugging

3. **Analyze Event Data**
   - Use the "Overview" tab to see event trends
   - Check "Activity" for detailed event logs
   - View "Diagnostics" to identify any implementation issues

4. **Setting Up the Facebook Pixel Helper**
   - Install the [Facebook Pixel Helper](https://chrome.google.com/webstore/detail/facebook-pixel-helper/fdgfkebogiimcoedlicjlajpkdmockpc) Chrome extension
   - Navigate to your website
   - Click on the Pixel Helper icon to see detected events
   - Verify that events are firing correctly with the expected parameters

## API Integration

The website uses [FakeStore API](https://fakestoreapi.com/) to fetch product data:

- Product listings: https://fakestoreapi.com/products
- Product details: https://fakestoreapi.com/products/{id}

All prices from the API are consistently formatted to display with 2 decimal places using `Number(price).toFixed(2)`.

## Screenshots

### Home Page (JoyMart Design)
![Home Page](https://user-images.githubusercontent.com/17312616/65086776-b1beb080-d9d0-11e9-9983-143d61ed8fdc.png)

### Product Details Page
![Product Details](https://user-images.githubusercontent.com/17312616/65086777-b1beb080-d9d0-11e9-9e2b-af3b7210bdf3.png)

### Shopping Cart
![Shopping Cart](https://user-images.githubusercontent.com/17312616/65086778-b2574700-d9d0-11e9-9377-8e4886f582a8.png)

### Order Confirmation
![Order Confirmation](https://user-images.githubusercontent.com/17312616/65086779-b2efdd80-d9d0-11e9-95d5-4b1a48eafe04.png)

---

## License

This project is open source and available under the [MIT License](LICENSE).

## Acknowledgments

- Original design created for JoyMart
- Product data provided by [FakeStore API](https://fakestoreapi.com/)
- Facebook Pixel for event tracking
