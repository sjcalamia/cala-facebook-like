# &lt;facebook-like&gt; Button Webcomponent
#### Uses HTML-LIT (or maybe full out Polymer? is that necessary?) ...
## to hoist the iframe ...
# into the _shadowDOM_

A Polymer Facebook Like component, so as to reduce blocking script loading... with the power of webcomponents and ansync loading!

#### ! Disclaimer !
I just starting writing this, to-day... super Alpha.

## How to use, in 3 easy steps
#### clone the repo (maybe if it gets cool I'll push to NPM)
You might even be able to add it to your npm via the github link... I think?
I don't usually get crazy with my cheezewhiz.

#### include or require the script
#### use the new custom element in your HTML

## But Why??
Wouldn't it be nice if we could just use some logical HTML in our HTML? Semantic Web something or other?
Doesn't it just feel right to just write `<facebook-like></facebook-like>`?

And, added bonus, this sandboxes the Like button pretty nicely by encapsulating the execution environment. Like a nice, well-made tupperware container, it can only get the data we give it, and it's sealed (mostly) airtight. Just because you want to let people like you, doesn't mean you have to give facebook undying access to your scripting environment. Sandbox the Book!

## Attributes & Parameters
#### _They are practically the same thing anyhow_

AppID [string]  
FBConnectVersion [string]  
href [string] 
  This should be set by the page, really. Trying to simplify here.
width [string]  
layout [string]  
action [string]  
size [string]  
show-faces [string]  
share [string]  
Size [string]  
    Possible values:  
      "small"  
      "medium"  
      "large"  

This was made to be able to recognize that it's pulling the page it's living on currently. 

Do we need a have another mode for the main sites' FB URL?

## Styling ... yeahhhhhh it's an iFrame, dude.
But you do have some degree of freedom, like, how big is it? What type of preconcieved FB Like Button you get. Eh. It's something. Hopefully this is just sliiiiightly easier to implement for people. (and you can hold onto the code)

.

<pre>
<div id="fb-root"></div>
<script>(function(d, s, id) {
  var js, fjs = d.getElementsByTagName(s)[0];
  if (d.getElementById(id)) return;
  js = d.createElement(s); js.id = id;
  let appId = "";
  let connectVer = "2.11";
  js.src = `https://connect.facebook.net/en_US/sdk.js#xfbml=1&version=v${connectVer}&appId=${appId}&autoLogAppEvents=1`;
  // It would be really cool if we could prefetch this ^^^^
  fjs.parentNode.insertBefore(js, fjs);
}(document, 'script', 'facebook-jssdk'));</script>
</pre>

```

    html`<div 
      class="fb-like" 
      data-href="${location.href}" 
      data-width="${this.width || 50px}" 
      data-layout="button" 
      data-action="like" 
      data-size="large" 
      data-show-faces="true" 
      data-share="true"
      ></div>`

```
