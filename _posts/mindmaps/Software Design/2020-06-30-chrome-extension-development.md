
# chrome extension development  

## context where extension lives   

### popup   

* html, js in html   

* tooltip   

* debugged from it's own page   

### background   

* debugged from extension page   

* "background": {    "scripts": ["background.js"],    "persistent": false  },   

#### event   

* onInstallation event   

##### onSuspend   

* last minute cleanups   

* sometimes not fired during crash   

* OnMessage   

* Subtopic 4   

#### effective background script is dormant until an event they are listening for fires   

##### is unloaded when   

* no visible view   

* no open message port i.e no listening of onmessage event   

### content scriptsthis script is also run in context of page   

* debugged from website page   

#### three ways   

* loading from manifest json   

* programmatically loading   

* can access chrome api by exchanging messages   

* can also access ifnormation by making cross site requests   

#### on these chrome apis can be accessed   

* i18nstorageruntime:connectgetManifestgetURLidonConnectonMessagesendMessage   

#### regarding messages   

##### how web page to content script   

###### sends   

* windows.postmessage   

###### receives   

* windows.addlistener('message')   

##### how bacground script to content script   

###### sends   

* chrome.tab.message   

###### receives   

* chrome.tab.onmessage   

##### content script to others   

###### webpage   
send to web   

* windows.postmessage   
receive from web   

* windows.addlistener   

###### background   
send to background   

* chrome.runtime.port().postmessage   
receives from background   

* windows.addlistnern   

##### browser action popup   

###### to background script   

* chrome.runtime.sendMessage   

###### from background script   

* chrome.runtime.onMessage.addListener   

##### background script with browser action popup   

###### send   

* chrome.runtime.sendMessage   

###### receive   

* chrome.runtime.onMessage.addListener   

### scripts inside page   

* debugged from website page   

## UI   

### toolbar   

#### page_action   

##### icons   

* "page_action": {      "default_icon": {        "16": "extension_toolbar_icon16.png",        "32": "extension_toolbar_icon32.png"      }    }   

* popup   

#### brwoser_action   

* icons   

##### popup   

* "browser_action": {      "default_popup": "popup.html"    }   

### icons   

#### directly in manifest   

* {    "name": "My Awesome Extension",    ...    "icons": {      "16": "extension_icon16.png",      "32": "extension_icon32.png",      "48": "extension_icon48.png",      "128": "extension_icon128.png"    }    ...  }   

* 16x16	favicon on the extension's pages32x32	Windows computers often require this size. Providing this option will prevent size distortion from shrinking the 48x48 option.48x48	displays on the extensions management page128x128	displays on installation and in the Chrome Webstore   

## interaction with extension   

* omnibox   

* context menu   

* popup   

* commands   
