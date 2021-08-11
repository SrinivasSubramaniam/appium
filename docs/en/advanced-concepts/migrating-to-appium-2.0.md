# Migrating to Appium 2.x from Appium 1.x

## Overview of Appium 2.0

## Breaking Changes

Have a look at the [Appium 2.0 release notes](#TODO) for a more comprehensive list of changes. Here we call out the breaking changes and what you need to do do account for them.

#### Installing drivers during setup

When you installed Appium 1.x, all available drivers would be installed at the same time as the main Appium server. This is no longer the case. Simply installing Appium 2.0 (e.g., by `npm install -g appium`), will install the Appium server only, but no drivers. To install drivers, you must instead use the new [Appium extension CLI](../drivers/driver-cli.md). For example, to install the latest versions of the XCUITest and UiAutomator2 drivers, after installing Appium you would run the following commands:

```
appium driver install xcuitest
appium driver install uiautomator2
```

At this point, your drivers are installed and ready. There's a lot more you can do with this CLI so be sure to check out the docs on it.
If you're running in a CI environment or want to install Appium along with some drivers all in one step, you can do so using some special flags during install, for example:

```
npm install -g appium --drivers=xcuitest,uiautomator2
```

This will install Appium and the two drivers for you in one go.

#### Driver updates

In the past, to get updates to your iOS or Android drivers, you'd simply wait for those updates to be rolled into a new release of Appium, and then update your Appium version. With Appium 2.x, the Appium server and the Appium drivers are versioned and released separately. This means that drivers can be on their own release cadence and that you can get driver updates as they happen, rather than waiting for a new Appium server release. The way to check for driver updates is with the CLI:

```
appium driver list --updates
```

If any updates are available, you can then run the `update` command for any given driver:

```
appium driver update xcuitest
```

To update the Appium server itself, you do the same thing as in the past: `npm install -g appium`. Now, installing new versions of the Appium server will leave your drivers intact, so the whole process will be much more quick.

#### Protocol changes

*Capabilities*

TODO

*Removed Commands*

Commands which were a part of the old JSON Wire Protocol and not a part of the W3C Protocol are no longer available:

* List TODO

If you use a modern Appium or Selenium client, you should no longer have access to these.

#### Image analysis features moved to plugin

TODO

#### Old drivers removed

The old iOS and Android (UiAutomator 1) drivers and related tools (e.g., `authorize-ios`) have been removed. They haven't been relevant for many years anyway.

#### Internal packages renamed

Some Appium-internal NPM packages have been renamed (for example, `appium-base-driver` is now `@appium/base-driver`). This is not a breaking change for Appium users, only for people who have built software that directly incorporates Appium's code.

#### "WD" JavaScript client library no longer supported

For many years, some of Appium's authors maintained the [WD](https://github.com/admc/wd) client library. This library has been deprecated and has not been updated for use with the W3C WebDriver protocol. As such, if you're using this library you'll need to move to a more modern one. We recommend [WebdriverIO](https://webdriver.io).

#### Appium Inspector split out from Appium Desktop

The inspecting portion of Appium Desktop has been moved to its own app, Appium Inspector: [github.com/appium/appium-inspector](https://github.com/appium/appium-inspector). It's fully compatible with Appium 2.0 servers. Simply download it and run it on its own. You no longer need the GUI Appium Desktop server to inspect apps. The Appium Desktop server will continue to be supported at its original site: [github.com/appium/appium-desktop](https://github.com/appium/appium-desktop). It will simply no longer bundle the Inspector with it.

You can also now use the Appium Inspector without downloading anything, by visiting the [web version of Appium Inspector](https://inspector.appiumpro.com). Note that to test against local servers, you'll need to start the server with `--allow-cors` so that the browser-based version of Appium Inspector can access your Appium server to start sessions.

## Major New Features

#### Plugins

*Server Plugins*

TODO

*Client Plugins*

TODO

#### Install drivers and plugins from anywhere

TODO

#### Driver and Plugin CLI args

TODO

