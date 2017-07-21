# In Stock Notifier plugin for Craft CMS

Sends an email to users who have requested to be notified when a product is restocked

![Screenshot](resources/screenshots/plugin_logo.png)

## Installation

To install In Stock Notifier, follow these steps:

1. Download & unzip the file and place the `instocknotifier` directory into your `craft/plugins` directory
2.  -OR- do a `git clone https://github.com/n-dW/instocknotifier.git` directly into your `craft/plugins` folder.  You can then update it with `git pull`
3.  -OR- install with Composer via `composer require n-dW/instocknotifier`
4. Install plugin in the Craft Control Panel under Settings > Plugins
5. The plugin folder should be named `instocknotifier` for Craft to see it.  GitHub recently started appending `-master` (the branch name) to the name of the folder for zip file downloads.

In Stock Notifier works on Craft 2.4.x and Craft 2.5.x.

## In Stock Notifier Overview

Allows users to request to be notified when a product is restocked via email.

## Configuring In Stock Notifier

None nessesary ATM just install


## Using In Stock Notifier

### Customer Request

Send a POST request to inStockNotifier/notification/requestRestockNotification with the fields

- customerEmail - the email address of the person who wants to be notified when product is restocked
- productId - the id of the product

```HTML
<input type="hidden" name="action" value="inStockNotifier/notification/requestRestockNotification">
<input type="hidden" name="productId" value="{{product.id}}">
<input type="hidden" name="customerEmail" value="{{ currentUser.email }}">
```

This will create a record in the db.

### Send Emails
The emails are sent when a product is saved and its stock increased to greater than zero. We use the event commerce_products.onBeforeSaveProduct and check if the product is about to be saved from the cp and that its stock was 0 and will be increased upon save.

If you don't want it to send onBeforeSaveProduct or to send with a task or cron job use:

```PHP
craft()->inStockNotifier_notification->processNotifications();
```
This will go through ever request that has not been sent yet and return all the requests that have product in stock and attempt to send emails to the user.

Additionally you can add 

```PHP
craft()->inStockNotifier_notification->processNotifications($productId = false, $isReStock = false);
```
- $productId will get all notification requests for that product
- $isReStock if this is true it means we checked that the product is in stock already and we dont need to do it twice, use this with $productId.

## In Stock Notifier Roadmap

Add a widget to show latest request, and latest emails sent and failed send.
Add a trigger in cp to send emails
Make email customizable
Add archive flag to db table to archive send ones.

* Release it

Brought to you by [NdW](natedewaard.com)
