---
 license: Licensed to the Apache Software Foundation (ASF) under one
         or more contributor license agreements.  See the NOTICE file
         distributed with this work for additional information
         regarding copyright ownership.  The ASF licenses this file
         to you under the Apache License, Version 2.0 (the
         "License"); you may not use this file except in compliance
         with the License.  You may obtain a copy of the License at

           http://www.apache.org/licenses/LICENSE-2.0

         Unless required by applicable law or agreed to in writing,
         software distributed under the License is distributed on an
         "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
         KIND, either express or implied.  See the License for the
         specific language governing permissions and limitations
         under the License.
---

# Contacts

> The `contacts` object provides access to the device contacts database.

__WARNING__: Collection and use of contact data raises
important privacy issues.  Your app's privacy policy should discuss
how the app uses contact data and whether it is shared with any other
parties.  Contact information is considered sensitive because it
reveals the people with whom a person communicates.  Therefore, in
addition to the app's privacy policy, you should strongly consider
providing a just-in-time notice before the app accesses or uses
contact data, if the device operating system doesn't do so
already. That notice should provide the same information noted above,
as well as obtaining the user's permission (e.g., by presenting
choices for __OK__ and __No Thanks__).  Note that some app
marketplaces may require the app to provide a just-in-time notice and
obtain the user's permission before accessing contact data.  A
clear and easy-to-understand user experience surrounding the use of
contact data helps avoid user confusion and perceived misuse of
contact data.  For more information, please see the Privacy Guide.

## Methods

- contacts.create
- contacts.find

## Arguments

- contactFields
- contactSuccess
- contactError
- contactFindOptions

## Objects

- Contact
- ContactName
- ContactField
- ContactAddress
- ContactOrganization
- ContactFindOptions
- ContactError

## Accessing the Feature

As of version 3.0, Cordova implements device-level APIs as _plugins_.
Use the CLI's `plugin` command, described in The Command-Line
Interface, to add or remove this feature for a project:

        $ cordova plugin add org.apache.cordova.contacts
        $ cordova plugin ls
        [ 'org.apache.cordova.contacts' ]
        $ cordova plugin rm org.apache.cordova.contacts

These commands apply to all targeted platforms, but modify the
platform-specific configuration settings described below:

* Amazon Fire OS

        (in app/res/xml/config.xml)
        <feature name="Contacts">
            <param name="android-package" value="org.apache.cordova.contacts.ContactManager" />
        </feature>

        (in app/AndroidManifest.xml)      
        <uses-permission android:name="android.permission.READ_CONTACTS" />
        <uses-permission android:name="android.permission.WRITE_CONTACTS" />
        <uses-permission android:name="android.permission.GET_ACCOUNTS" />

* Android

        (in app/res/xml/config.xml)
        <feature name="Contacts">
            <param name="android-package" value="org.apache.cordova.contacts.ContactManager" />
        </feature>

        (in app/AndroidManifest.xml)      
        <uses-permission android:name="android.permission.READ_CONTACTS" />
        <uses-permission android:name="android.permission.WRITE_CONTACTS" />
        <uses-permission android:name="android.permission.GET_ACCOUNTS" />

* BlackBerry WebWorks

        (in www/plugins.xml)
        <feature name="Contact">
            <param name="blackberry-package" value="org.apache.cordova.pim.Contact" />
        </feature>

        (in www/config.xml)
        <feature id="blackberry.find"        required="true" version="1.0.0.0" />
        <feature id="blackberry.identity"    required="true" version="1.0.0.0" />
        <feature id="blackberry.pim.Address" required="true" version="1.0.0.0" />
        <feature id="blackberry.pim.Contact" required="true" version="1.0.0.0" />

* iOS (in the named application directory's `config.xml`)

        <feature name="Contacts">
            <param name="ios-package" value="CDVContacts" />
        </feature>

* FirefoxOS
       
		Enable access to the API by changing [app permissions](https://developer.mozilla.org/en-US/Apps/Developing/App_permissions)

        (in platforms/firefoxos/www/manifest.webapp)
        "type": "privileged",
        "permissions": {
			"contacts": {
				"access": (choose from "readonly", "readwrite", "readcreate", or "createonly"),
				"description": "Describe why you need access to contacts API"
			}
        }

		All privileged apps enforce [Content Security Policy](https://developer.mozilla.org/en-US/Apps/CSP) 
		which forbids inline scripts. Initialize your application in another way.

* Windows Phone (in `Properties/WPAppManifest.xml`)

        <Capabilities>
            <Capability Name="ID_CAP_CONTACTS" />
        </Capabilities>

  Reference: [Application Manifest for Windows Phone](http://msdn.microsoft.com/en-us/library/ff769509%28v=vs.92%29.aspx)

Some platforms may support this feature without requiring any special
configuration.  See Platform Support for an overview.
