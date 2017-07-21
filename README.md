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

Send a POST request to inStockNotifier/notification/requestRestockNotification with the fields

customerEmail - the email address of the person who wants to be notified when product is restocked
productId - the id of the product

This will create a record in the db.

When a product is saved in the admin cp and its stock has increased from zero therefore that means its been restocked we send out emails for that product if there are any requested.

If you don't want it to send onBeforeSaveProduct or to send with a task or cron job use craft()->inStockNotifier_notification->processNotifications().



## Using In Stock Notifier

-Insert text here-

## In Stock Notifier Roadmap

Some things to do, and ideas for potential features:

* Release it

Brought to you by [NdW](natedewaard.com)
