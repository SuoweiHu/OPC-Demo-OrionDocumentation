---
sidebar_position: 3
---

# Drupal Module : API





## **Controllers (API End-Points)**
- `JsonApi_getCompanyIdentifier_fromUserField.php`: api of getting the company id of current user (field machine name `company_identifier`, see screenshot: [https://share.cleanshot.com/h61DBNlgS9bGZ8t8sJ2L](https://share.cleanshot.com/h61DBNlgS9bGZ8t8sJ2L))
- `JsonApi_Company.php`: api for getting the company details such as address, phone number, main contact, etc; with given company ID (by utilising the proxy to connectwise offical api).
- `JsonApi_Tickets.php`: api for getting the tickets given company id (a typical ticket field used in this case will include its name, ID, overall , and link to the time entries table)
- `JsonApi_TimeEntries_currentMonth.php`: given the company id, find the sum of time spenditure for this company at the current month (method 1)
- `JsonApi_TimeEntries_withCalc.php`: given the company id, find the sum of time spenditure for this company at the current month (method 2)
- `JsonApi_TimeEntries.php`: given company id, return a list of time spenditure of this company

:::danger Take care

Make sure you update the corresponding page (Drupal custom module: ConnectWise-Module-Page) when you change these endpoints

:::

## **File Hierarchies**

```
	\ConnectWise_Module_API
	|
	|______ConnectWise_Module_api.info.yml
	|
	|______ConnectWise_Module_api.routing.yml
	|
	|______\src
	        |
	        |_______\Controller
						  |_______JsonApi_Company.php
						  |_______JsonApi_RequestProxy.php
						  |_______JsonApi_Tickets.php
						  |_______JsonApi_TimeEntries_currentMonth.php
						  |_______JsonApi_TimeEntries_withCalc.php
						  |_______JsonApi_TimeEntries.php
						  |_______JsonApi_getCompanyIdentifier_
	                                         \fromUserField.php
```

For the above file/directories
- `\ ConnectWise_Module_API ` :
	- Directory containing the custom module.
- `ConnectWise_Module_api.info.yml`:
	- The file of which lets drupal know of this custom module, the drupal PHP will get the fields "machine name", "description", "package", "compatible drupal version"  from this file.
	- [More information. ](https://www.drupal.org/docs/develop/creating-modules/let-drupal-know-about-your-module-with-an-infoyml-file)
- `ConnectWise_Module_api.routing.yml`:
	- The router of the drupal module, mapping a path like "/page/hello\_world" to some callback of controller say "/Drupal/example/ControllerExample::page\_hello\_world\_controller"; This file also defines the type of output (json/html), the permission, and library to load (e.g. javascript, CSS) for this page.
	- [ More information. ](https://www.drupal.org/docs/develop/creating-modules/create-a-custom-page-using-a-controller)
- `\src\Controller`
	- The handler / callback for the router, it is the processing logic of the page; This file takes the parameter from the router, adds a header and returns the page body.
	- [ More information. ](https://www.drupal.org/docs/develop/creating-modules/create-a-custom-page-using-a-controller)

