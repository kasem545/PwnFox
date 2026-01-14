# <img src="/firefox/icons/icon.svg" width=30> PwnFox

PwnFox is a Firefox/Burp extension that provides useful tools for your security audit.

## Features

![popup](/screenshots/popup.png)

### Single click BurpProxy

Connect to Burp with a simple click, this will probably remove the need for other addons like foxyProxy. However if you need the extra features provided by foxyProxy you can leave this unchecked.

Supports both HTTP and SOCKS5 proxy protocols. Configure the protocol in the extension settings.

###  Containers Profiles

PwnFox give you fast access to the Firefox containers. This allow you to have multiple identities in the same browser. 
When PwnFox and the `Add container header` option are enabled, PwnFox will automatically add a `X-PwnFox-Color` header to highlight the query in Burp.

PwnFoxBurp will automatically highlight and strip the header, but you can also specify your own behavior with addons like logger++.

![tabs](/screenshots/tabs.png)
![burp](/screenshots/burp.png)



### PostMessage Logger

PwnFox add a new message tab in you devtool. This allow you to quickly visualize all postMessage between frames.

![](/screenshots/post-single.png)

You can also provide your own function to parse/filter the messages.
You get access to 3 arguments:
 * data -> the message data
 * origin -> the window object representing the origin
 * destination -> the window object representing the destination

You can return a string or a JSON serializable object.

![](/screenshots/post-dual.png)


### Toolbox

Inject you own javascript code on page load. The code will be loaded as soon as possible. This can used to add dangerous behavior detection, or just to add extra function to your js console.

**Be careful, the injected toolbox will run in the window context. Do not inject secrets in untrusted domains.**


![settings](/screenshots/settings.png)


### Security header remover

Sometime it's easier to work with security header disabled. You can now do it with a single button press. Don't forget to reenable them before testing your final payload.

Headers stripped:
* Content-Security-Policy
* X-XSS-Protection
* X-Frame-Options
* X-Content-Type-Options

## Installation


You can find the latest build here:
* [https://github.com/kasem545/PwnFox/releases](https://github.com/kasem545/PwnFox/releases)


### Burp
- Go to extender and add `PwnFox-Burp.jar` as a java extension.

## Build

### Firefox

```shell
cd firefox
web-ext build
# the zip file is available in /firefox/web-ext-artifacts/pwnfox-${version}.zip
# Optional. If you want to sign you own build
web-ext sign --api-key="$KEY" --api-secret="$SECRET"
# the xpi file is available in /firefox/web-ext-artifacts/pwnfox-${version}.xpi

```

## Changelog
* v1.2.0
  * Added SOCKS5 proxy protocol support
  * UI improvements - modern dark theme with better UX