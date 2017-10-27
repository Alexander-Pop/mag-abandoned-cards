# DigitalPianism_Abandonedcarts

Abandoned Carts Notification module for Magento

# Documentation

Everything you need to know can be found here: http://www.digital-pianism.com/en/magento-modules/abandoned-carts-notification.html

# Magento Connect

http://www.magentocommerce.com/magento-connect/abandoned-carts-notifications.html

# Release Notes

## 1.0.7
Thanks to Septoctobre for all the bug reports and pull requests

- Fix a bug where the delay would not be taken into consideration when the cron ran: https://github.com/digitalpianism/abandonedcarts/issues/17
- Fix a bug where the area would not be properly loaded: https://github.com/digitalpianism/abandonedcarts/issues/8 and https://github.com/digitalpianism/abandonedcarts/issues/7
- Fix a bug where the count of total would be wrong because of the quantity : https://github.com/digitalpianism/abandonedcarts/issues/13
- Implement prices columns with currencies : https://github.com/digitalpianism/abandonedcarts/issues/13
- Fix a bug where the sale abandoned carts report would display nothing when flat catalog is enabled : https://github.com/digitalpianism/abandonedcarts/issues/15

## 1.0.6
- Fix a bug where an error would be triggered when filtering the grid by one date (from OR to) : https://github.com/digitalpianism/abandonedcarts/issues/9
- Fix a bug where the count in the grid would be wrong: https://github.com/digitalpianism/abandonedcarts/issues/11

## 1.0.5
- Fix a bug where the small image would not be picked: https://github.com/digitalpianism/abandonedcarts/issues/3

## 1.0.4
- Fix a bug where the default email template would not be picked: https://github.com/digitalpianism/abandonedcarts/issues/4

## 1.0.3
- Fix a bug where it was impossible to preview the email templates in the backend

## 1.0.2
- Fix a bug where the admin URL would be used when notifying from the backend
- Fix a bug where admin users store would not remain on a multistore install

## 1.0.1
- Fix a bug where the data script would never run

## 1.0.0
- Full refactor of the module
- Add two grids to the backend to see the abandoned carts
- Add a log database table to easily see what's going on
- Implement an autologin link system
- Implement Google Campaign tags
- Improve the templates to list all items
- Change the way dryrun and test email behaves
- Add notification flags columns to the native abandoned carts report

## 0.3.6
- Fix a bug where an error would be logged if the product image was missing

## 0.3.5
- Fix a bug where the product image would not be retrieved in the email.

## 0.3.4
- Fix a bug where the email would not be reflect the right store when sharing customers account globally.

# Overview
This module includes two functionalities:

The first one is an automatic email notification for customers who abandoned their carts after a customizable number of days
The second one is an automatic email notification when products which are in an abandoned cart go on sale
With this extension, you can increase your sales with follow-up emails in order to bring back customers who did not checkout the first time they added products to their bag.

Here is an example of the first functionality's email:
Dear John,
You have abandoned a Apple iPad 8GB and 2 more products in your cart.
Follow this link and log in to finalize your purchase: http://www.mystore.com/
Here is an example of the second functionality's email:
Dear John,
You have abandoned a Apple iPad 8GB in your cart.
It was 200€ and now is 150€.
Purchase the 2 other sale products in your cart and save 85€ on your order.
Follow this link and log in to finalize your purchase with the new special price: http://www.mystore.com/
## Configuration
Emails Design
In the backend, access System > Transactional Emails
Click on the "Add New Template" button
Under the "Load Default Template" section, choose "Abandoned Cart Template" for Template and "English (United States)" for Locale
Click the "Load Template" button and design your "Abandoned Cart" email to match with your store emails.
Repeat step 1 - 4 choosing "Abandoned Cart Sale Template" in step 3 to design the "Abandoned Cart Sale" email.
## Module Configuration
Access the module configuration under System > Configuration > Digital Pianism > Abandoned Carts Emails.

Global Configuration>
Enable Abandoned Carts Notification: setting this option to Yes will enabled the email notification for customers who abandoned their carts.
Enable Sale Abandoned Carts Notification: setting this option to Yes will enabled the email notification for customers who have abandoned carts with sale products.
Cron Schedule: for experimented cron users only, here you can change the cron schedule. By default it is set to run every night at 1AM. Use this setting carefully
Delay / Send Abandoned Cart Email After: in days, this is the delay before the email is sent. For example, if you provide 7 in this field, the abandoned cart notification email will be sent 7 days after the customer abandoned its cart.
Customer Groups: you can select specific customer groups to be notified here.
Email Configuration

Sender Name: here you can provide the sender name of the notification email
Sender Email: here you can provide the sender email of the notification email
Email Template for Unaltered Abandoned Carts: here you have to choose the email template you created previously for the "Abandoned Carts" email.
Email Template for Abandoned Carts Sale: here you have to choose the email template you created previously for the "Abandoned Carts Sale" email.
Enable Automatic login link in the email: disabled by default, if you enable that option the link in the email will automatically log the customer in. Links are one use only and expire after 48 hours for security reasons.
Test and debug

Dry Run: Setting this parameter to Yes will not send the real email notification.
Test email: With dry run set to yes, this email is used as a recipient email replacement so the real customer don't receive the email.
Enable Log: Setting this parameter to Yes will log abandoned cart actions so it can be viewed in Digital Pianism > Abandoned Carts > Logs
Google Campaign Tracker

Enable: set to Yes if you want to enable Google Campaign Tracker in the email link
Campaign Name: here you need to provide the Google Campaign Name which corresponds to the "utm_campaign" parameter. "utm_source" and "utm_email" are hardcoded to "abandonedcarts" and "email"
Save the configuration.

N.B. : Please note that abandoning carts without being logged in will result in no email being sent for this abandoned cart because there is no way we can retrieve not logged in customer's email.

## Emails Variables
The following variables are being used in the email templates that come with the extension.

For the abandoned carts email:

{{var firstname}} : first name of the customer
{{var productname}}: array of product names in the abandoned cart
{{var productimage}}: array of URLs of product images in the abandoned cart
{{var link}}: link to your store (automatic login link if enabled)
For the abandoned carts for sale products email:

{{var firstname}} : first name of the customer
{{var productname}}: array of product names in the abandoned cart
{{var productimage}}: array of URLs of product images in the abandoned cart
{{var cartprice}}: array of original products prices in the abandoned cart.
{{var specialprice}}: array of product sale prices in the abandoned cart.
{{var discount}}: possible discount if the whole abandoned cart is purchased.
{{var link}}: link to your store (automatic login link if enabled)
## Grids
The new version of the module provides three grids:

Digital Pianism > Abandoned Carts > Logs: to see the logs if you enabled the option
Digital Pianism > Abandoned Carts > Abandoned Carts List: to see the abandoned carts that'll be notified based on the delay provided
Digital Pianism > Abandoned Carts > Sale Abandoned Carts List: to see the sale abandoned carts
From the last two grids, you can manually send notifications without having to wait for the cron to run. You can use the Send notifications button to notify every customer in the list or use the massaction item to cherry pick the customers you want to notify
