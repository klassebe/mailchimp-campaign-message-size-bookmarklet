# Mailchimp Campaign Message Size Bookmarklet
This bookmarklet calculates and shows the message size of a Mailchimp campaign while it's being built.

## Background
At Klasse, we noticed Gmail clipping most of our newsletters sent out using Mailchimp. Mailchimp's Guides and Tutorials taught us [Gmail clips emails with a message size larger than 102KB](https://mailchimp.com/help/gmail-is-clipping-my-email/), but does not mention or offer any way to know the message size of a campaign before it is sent out to subscribers.

We sent in a feature request to Mailchimp, but since there is no way to tell if and when a feature like this would become available, we decided to build a bookmarklet that offers this functionality.

*Note: As mentioned in the bookmarklet, the calculated message size is purely an indication. The actual message size can deviate because of conditionals, for example.*

## Installation
There are 2 ways to add this bookmarklet to your browser:
1. Select and drag the code below to your bookmarks toolbar
2. Open your bookmarks, add a new bookmark and use the code below as the destination/location of the bookmark
```
javascript:(function(){var e,n,t,a,i=/(\r?\n|\r)/g,r=0===navigator.platform.indexOf("Win");function s(e,n){(n=n||{}).line_breaks=n.line_breaks||1;var t=e.length,a=t-e.replace(/[\u0100-\uFFFF]/g,"").length,r=t-e.replace(i,"").length;return t+a+Math.max(0,n.line_breaks*(r-1))}function l(e){for(var n=0;e>1024;)e/=1024,n++;return e=Math.round(100*e)/100,n=["","K","M","G","T"][n],Math.ceil(e)+" "+n+"B"}e=document.getElementsByClassName("preview-frame")[0],n=(e.contentDocument?e.contentDocument:e.contentWindow.document).documentElement.outerHTML,t=l(s(n="<!doctype html>"+n)),a=l(s(n,{line_breaks:2})),result=t,r&&(result=a),text="This campaign is "+result+" in size.\nWarning: This message size is purely an indication. The actual message size can deviate, for example because of conditionals.\n\nNote: Gmail clips emails with a message size larger than 102 KB.",alert(text)})();
```

## Usage
1. Navigate to the draft of the campaign you wish to know the message size of
2. Click 'Preview and Test'
3. Select 'Enter preview mode (1)'
4. Wait until your campaign is visible
5. Click the bookmarklet
6. An alert box now appears with the message size and other useful information

## Authors
* **Sander Teirlynck** - [Klasse](https://www.klasse.be/)

## Acknowledgements
* Lea Verou's [ByteSizeMatters](http://bytesizematters.com/)
