# Luci2

This is a complete rewrite of Luci, [OpenWrt’s](https://openwrt.org) web interface, with the goal of making it more modern looking, simpler to use and requiring less device’s resources.

LOGO
BADGES

## Demo

You can try it live at:
[Online OpenWrt]()
Using 

*user*: `guest`

*password*: `OpenWrt`

## Screenshots


## Design Principles

The main design principles are:
* Keep separation of view/model/business logic
- Minimal dependencies. No LUA. Only depend at on Ubus rpcd.
- Static web pages served, rendered on the client, interacting with the device with UBUS thru http calls 
- View definitions completely done in pure json. No code needed on any specific framework
- Modern look & feel
- Responsive and working well on mobile.
- Core Developed using Angular and modern web development tooling.
- Minimal API exposed from Luci2 to the views. All business logic should be in Ubus methods in the backend


## Current Status

Luci2 is currently under development. It is possible to install and run it, but it will offer limited functionality.

You are encouraged to contribute to it’s development!


## Installing

Currently there is no package feed with compiled packages to directly install on the device.
To use it you will need to compile it yourself. The easiest way is to use [OpenWrt SDK](https://openwrt.org/docs/guide-developer/using_the_sdk).

You’ll need to add this repo to `feeds.conf`

```
src-git Luci2 https://github.com/jow-/luci-ng;release
```

You need to install `luci2-app-base`, which will pull all needed dependencies.

https://openwrt.org/docs/guide-developer/feeds

## Developing Views

To completely define a view a number of files are needed, mostly json. Not all are necessary:
1. ACLs defining the permissions needed to run de view, if applicable 
2. UCI Schema, describing the corresponding UCI config. Required only if the view manages UCI options.
3. View definition. The description of the UI and it’s behavior. In some simple cases can be omitted and generated automatically from the UCI schema.
4. Menu/Route to access the view. 
5. UBUS plug-in/script with business logic, if needed. 
6. Helper client side plain js with helper functions to post process Ubus responses. This is discouraged as the logic should reside in the Ubus method.

Documentation coming soon.

## License

