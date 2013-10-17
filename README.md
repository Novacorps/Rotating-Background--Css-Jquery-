Rotating Background (Css/Jquery)
================================

Full page background images on web sites has become more popular than ever.
Its a good way to utilize the remaining real estate of the browser, without having to sacrifice content.
But what about rotating these images? Wouldn’t that even be better?

This tutorial will walk you through how to create full page background images that rotate like a slideshow.
We will be using CSS and jQuery – particularly the nifty cycle plugin.
On a side note – if you want to learn more about jQuery, check out this video series from Udemy!
Ready to get started? Let’s begin:

The HTML Markup:

First we create the background images. Place them in your root folder, in a directory called “images”.
We wrap them around a special DIV which houses all the images.
We need this DIV so we can target it from our script later:


<div id="slideshow">
<img src="/images/b1.jpg" class="bgM"/>
<img src="/images/b2.jpg" class="bgM"/>
<img src="/images/b3.jpg" class="bgM"/>
<img src="/images/b4.jpg" class="bgM"/>
<img src="/images/b5.jpg" class="bgM"/>
<img src="/images/b6.jpg" class="bgM"/>
<img src="/images/b7.jpg" class="bgM"/>
</div>
<div id="wrap">
...your content here
</div>


Make sure your image is a good sized horizontal shot. For almost all screen resolutions have wider width vs height. Our images will scale to the width of the screen. The DIV id=”wrap” is the container for your content. This is directly underneath our slideshow container. Save your HTML and view it in the browser. You should see a series of images on top of each other.
The CSS

Add this code to your page. This will set the images width to span the entire page.


#slideshow, img.bgM {
        min-height: 100%;
        min-width: 1024px;
        width: 100%;
        height: auto;
        position: fixed;
        top: 0;
        left: 0;
        z-index:-9999;
}


View Refresh your page. You should see only the first image.
The rest of the images are tucked away underneath the first one.
This is what “z-index” and “position” properties in our code did.
Now for the slideshow effect, we use some jQuery magic.


The jQuery

Download the jQuery Cycle plugin from here, and place it inside a directory called “scripts” in your root folder.
Add the jQuery library and a reference to the plugin inside the head section of your HTML:


<script type="text/javascript" src="http://code.jquery.com/jquery-1.6.3.min.js"></script>
<script type="text/javascript" src="scripts/jquery.cycle.all.2.74.js"></script>

Then add this code that will pickup our slideshow DIV, and apply the cycle functionality from our plugin:


$(document).ready(function() {
				$('#slideshow').cycle({
				fx: 'fade',
				pager: '#smallnav', 
				pause:   1, 
				speed: 1800,
				timeout:  3500 
			});			
		});
		

You can choose to edit the plugin options by tweaking the above code.
For the list of available options such as transition effects, timing and callbacks – refer to the jQuery Cycle docs.

Conclusion:

Now refresh your browser and you should see your background fade into the next image and to another.
Like I said, this style can be quite refreshing – to vary your page from a million other websites out there
with large image backgrounds. The only problem with this is when browser is resized, the image stays in
the original size and doesn’t resize on the fly. Maybe one of you guys can improve the image handling with
javascript or something.

Bonus Tip: for added functionality, you can add individual links to the background images by wrapping each image into an anchor tag:
	

<div id="slideshow">
<a href="http://yahoo.com"><img src="images/b1.jpg" </a>
<img src="images/b3.jpg" class="bgM"/>
class="bgM"/></a>


This is especially useful if you’re using your background as advertising space of some sort (hint hint).

So go on and try it out for yourself. Don’t forget the jQuery series from Udemy! 
