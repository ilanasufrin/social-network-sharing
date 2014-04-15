social-network-sharing
======================

Sharing to social networks should be straight forward - Use this library for Huffpost Labs Projects

Use this Library
---

- Download ```social-network-sharing.js```
- If you want specialized Facebook sharing, edit it with the instructions below
- Publicly host ```social-network-sharing.js``` and include a reference to it before calling any of its functions
- You're good to go!


Sharing to Twitter
===

In your code, call ```HuffpostLabsShareTwitter(text, url, callback)``` where:
- ```text``` is the content of the tweet
- ```url``` is the url of the link back
	- if no url or ```null``` is provided, url will default to the page where shared from, ie ```window.location.href```
- ```callback``` (optional) is the function that will be fired upon tweeting

All shares will include ```via @HuffpostLabs```

Sharing to Facebook
===
This will share to someone's 'feed'

In your code, call ```HuffpostLabsShareFB(shareData, onSuccess, onError)```, where

- ```onSuccess``` callback that will be fired upon successful share
- ```onError``` (optional) callback that will be fired upon error
- ```shareData``` - a dictionary with the following fields:
	- ```name``` (required) - the main header text that is also a link
	- ```picture``` (optional) - absolute URL of the picture that will be shared on the left side with the text
		- defaults to Huffpost's favicon: http://www.huffingtonpost.com/favicon.ico
	- ```link``` (optional) - link back that user will go to when clicking on the ```name``` in the share.
		- Defaults to wherever shared from, ie, ```window.location.href```
	- ```caption``` (reuired) - sub header shown in facebook post under ```name```
	- ```description``` (optional) - sub sub heading shown under ```caption```.
		- If not provided, Facebook will try to be smart and pull content from the page

Example
---

```
<img class=".fb-share-btn" src="/fb-button-icon.png" onclick="fbShare()">
<script>
	function successCallback() {
		console.log('YAY SOMEONE SHARED');
	}
	function errorCallback() {
		console.log('uh oh.... but at least someone tried to share...')
	}
	var shareData = {
		'name': 'Awesome Widget',
		'picture': 'http://www.huffingtonpost.com/contributors/brandon-diamond/headshot.jpg',
		'link': 'http://LINK-TO-MY-AWESOME-STUFF.com',
		'caption': 'This is so cool',
		'description': 'Let me tell you more: blah blah blah...'
	}
	HuffpostLabsShareFB(shareData, onSuccess, onError)
</script>
```



Sharing to Facebook from other domains
---

Facebook is very picky about where users can share from.  Users can only share with our facebook app from our registered domains/subdomains:

- http://code.huffingtonpost.com
- http://www.huffingtonpost.com
- http://p.huffingtonpost.com
- http://huffingtonpost.com
and our mobile domain
- http://m.huffpost.com

if there is a Huffpost subdomain that isn't supported above:

- get added as an 'administrator' or 'developer' to the HuffpostLabs FB app
- Add the subdomain
- Edit this README - add the subdomain above
- Edit ```social-network-sharing.js```: 
	- ```"http://NEW-SUBDOMAIN.huffingtonpost.com": 	  '1427100424195799',```
- PLEASE make pull request so that everyone else can use it too

###
- If you want your facebook share button to hide when domain not supported, put a ```.fb-share-btn``` class or a ```#fb-share-btn``` id on it
	- If style still overridden, edit the ```disableFBsharing``` function










