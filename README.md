The Code Computerlove team is no longer managing and supporting Photoswipe. But we’re passing it on to you.
===========================================================================================================
Thanks for making Photoswipe so successful and we hope that you, the community will continue to make use of it.


PhotoSwipe - The web image gallery for your mobile device
=========================================================

web: [www.photoswipe.com](http://www.photoswipe.com), [www.codecomputerlove.com](http://www.codecomputerlove.com)

twitter: [@photoswipe](http://twitter.com/#!/photoswipe)

Inspired by the iOS photo viewer and Google images for mobile, PhotoSwipe is a HTML/CSS/JavaScript based image gallery specifically targeting mobile devices.

The current version supports mobile handsets running WebKit based browsers, i.e. iOS, Android and Blackberry 6.

PhotoSwipe also runs on the desktop and has been tested on Chrome, Firefox, Safari and Internet Explorer 8 and above and in a limited capacity on Windows Phone 7 (Mango).

Have you used PhotoSwipe? It'd be great to hear from you!
---------------------------------------------------------

It'd be fantastic to see how you have implemented PhotoSwipe on your site! We're looking at showcasing some of the best on [photoswipe.com](http://www.photoswipe.com). Feel free to drop us a tweet at [@photoswipe](http://twitter.com/#!/photoswipe) and tell us all about it!



Latest Release v3.0.5
---------------------
[Download](http://github.com/downloads/codecomputerlove/PhotoSwipe/code.photoswipe-3.0.5.zip)

- Fixed user agent string issues with Firefox for Android
- Fixed iOS5 black screen issue when using pinch to zoom

**Changes for v3**

- You can now specify a target for PhotoSwipe. It doesn't have to run in full screen anymore! To do this, you specify a "target" as part of PhotoSwipe settings. The target MUST be a valid DOM element for it to work. See examples "12-custom-target.html", "13-custom-target-with-indicators.html" for more details.
- Multi-line captions when caption bar placed at the bottom should now be fixed.
- Fixed issue where toolbar and caption remained visible when zooming in and captionAndToolbarAutoHideDelay = 0.
- Upgraded to jQuery Mobile 1.0 RC2
- Upgraded Code.Util to 1.0.6
- Work around for issue #141 now officially added - when rotating an app with PhotoSwipe displayed in a UIWebView, PhotoSwipe does not rotate. This seems to be an issue with UIWebView not PhotoSwipe. To enable this work around, set "enableUIWebViewRepositionTimeout = true" when creating your PhotoSwipe instance. You can also specify the frequency of this timeout by setting "uiWebViewResetPositionDelay" (default 500ms) - **Please Note** This is not needed for PhoneGap apps, nor web apps added to your homescreen.

**Important notes about the examples and Internet Explorer**

The majority of the bundled examples supplied with PhotoSwipe are running the optimised non-jQuery version. These examples will error on Internet Explorer. This is by design. They will work if you use the jQuery version of PhotoSwipe. Please read the "Getting Started" section below for more information regarding the different implementations of PhotoSwipe.

Features
--------

- Optimised for mobile devices running a WebKit browser.
- Runs on modern desktop browsers, including Internet Explorer 8 and above.
- From v3 can be run within a div on your page as well as "full screen".
- Multiple input options including swipe gestures (both mouse and screen touches), keyboard control and an interactive on screen toolbar.
- Responsive to device orientation changes.
- Automatically scales images to maximise screen size and orientation.
- Zoom and pan around images
- Rotate image (iOS only)
- Works with your markup and semantic structure. Does not enforce any specific markup.
- Supports image captions.
- Slideshow feature to automatically play through images in the gallery.
- Uses hardware acceleration where possible for smoother transitions and effects.
- Can be integrated into jQuery Mobile.
- Comprehensive customisation options:
    - Presentation controlled via CSS
    - Set whether the gallery loops or not i.e. when you reach the end, is the next image the first image, or does the gallery show a bounce effect to indicate that you have reached the end.
    - Hide or show captions and toolbar
    - Change caption and toolbar positions
    - Provide your own toolbar HTML
    - Set the speeds of all animations used, from sliding in to fading.

Getting Started
---------------

PhotoSwipe comes with an example site to help you get started.

There are two distributions of the library:

- The default distribution optimised for WebKit and Mozilla based browsers. This distribution uses standard DOM querying and manipulation. It also uses CSS3 transformations for animations.

- The jQuery distribution that uses jQuery as it's engine.

It is recommended for WebKit based mobile devices to use the default distribution. This negates a lot of the overhead from using jQuery. It does not require jQuery (so one less library to download to your mobile device!). The default distribution will also work on desktop WebKit browsers (such as Chrome and Safari) as well as Firefox 4 and above.

Use the jQuery distibution if you need to support a wider range of browsers such as Internet Explorer etc.



Getting Started - Default Distribution
--------------------------------------

See "examples/01-default.html".

This example assumes no jQuery at all and is heavily optimised for WebKit and Mozilla browsers. PhotoSwipe.attach takes three parameters, an array of HTML elements, optional options and optional instance ID string.

```js
// Set up PhotoSwipe with all anchor tags in the Gallery container
document.addEventListener('DOMContentLoaded', function(){
  var myPhotoSwipe = Code.PhotoSwipe.attach(
    window.document.querySelectorAll('#Gallery a'),
    {
      enableMouseWheel: false ,
      enableKeyboard: false
    }
  );
}, false);
```

PhotoSwipe can be initiated without being attached to HTML elements. See "examples/09-exclusive-mode-no-thumbnails.html" for more information.

Getting Started - Default Distribution (with jQuery engine)
-----------------------------------------------------------

See "examples/02-jquery.html". The plugin takes two parameters both of which optional; an options objectand an instance ID string.

```js
// Set up PhotoSwipe with all anchor tags in the Gallery container
$(document).ready(function(){
  var myPhotoSwipe = $("#Gallery a").photoSwipe({
    enableMouseWheel: false,
    enableKeyboard: false
  });
});
```

Options
-------

<table>
  <tr>
    <th>Name</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
  	<td><code>allowUserZoom</code></td>
  	<td><code>true</code></td>
  	<td>Allow the user to zoom / pan around images.</td>
  </tr>
  <tr>
  	<td><code>autoStartSlideshow</code></td>
  	<td><code>false</code></td>
  	<td>Automatically starts the slideshow mode when PhotoSwipe is activated.</td>
  </tr>
  <tr>
  	<td><code>allowRotationOnUserZoom</code></td>
  	<td><code>false</code></td>
  	<td>iOS only - Allow the user to rotate images whilst zooming / panning.</td>
  </tr>
  <tr>
  	<td><code>backButtonHideEnabled</code></td>
  	<td><code>true</code></td>
  	<td>This will hide the gallery when the user hits the back button. Useful for Android  and Blackberry. Works in BB6, Android v2.1 and above and iOS 4 and above.</td>
  </tr>
  <tr>
  	<td><code>captionAndToolbarAutoHideDelay</code></td>
  	<td><code>5000</code></td>
  	<td>How long to wait before the caption and toolbar automatically disappear. Default = 5000. Set to 0 to prevent auto disappearing</td>
  </tr>
  <tr>
  	<td><code>captionAndToolbarFlipPosition</code></td>
  	<td><code>false</code></td>
  	<td>Place the caption at the bottom and the toolbar at the top.</td>
  </tr>
  <tr>
  	<td><code>captionAndToolbarHide</code></td>
  	<td><code>false</code></td>
  	<td>Hide the caption and toolbar.</td>
  </tr>
  <tr>
  	<td><code>captionAndToolbarOpacity</code></td>
  	<td><code>0.8</code></td>
  	<td>The opacity of the caption and toolbar.</td>
  </tr>
  <tr>
  	<td><code>captionAndToolbarShowEmptyCaptions</code></td>
  	<td><code>true</code></td>
  	<td>Shows a blank caption area even if a caption cannot be found for the current image.</td>
  </tr>
  <tr>
  	<td><code>cacheMode</code></td>
  	<td><code>Code.PhotoSwipe.Cache.Mode.normal</code></td>
  	<td><code>Code.PhotoSwipe.Cache.Mode.normal</code> (default) or <code>Code.PhotoSwipe.Cache.Mode.aggressive</code>. Changes how PhotoSwipe manages it's cache. Aggressive will purposely set images that are not either the current, next or previous to be an empty "spacer" type image. This helps on older iOS versions if you have excessively large images. In the main, normal should suffice</td>
  </tr>
  <tr>
  	<td><code>doubleTapSpeed</code></td>
  	<td><code>300</code></td>
  	<td>Double tap speed in milliseconds.</td>
  </tr>
  <tr>
  	<td><code>doubleTapZoomLevel</code></td>
  	<td><code>2.5</code></td>
  	<td>When the user double taps an image, the default "zoom-in" level.</td>
  </tr>
  <tr>
  	<td><code>enableDrag</code></td>
  	<td><code>true</code></td>
  	<td>Enables dragging the next / previous image into view.</td>
  </tr>
  <tr>
  	<td><code>enableKeyboard</code></td>
  	<td><code>true</code></td>
  	<td>Enables keyboard support.</td>
  </tr>
  <tr>
  	<td><code>enableMouseWheel</code></td>
  	<td><code>true</code></td>
  	<td>Enables mouse wheel support.</td>
  </tr>
  <tr>
  	<td><code>enableUIWebViewRepositionTimeout</code></td>
  	<td><code>false</code></td>
  	<td>If enabled, continually checks to see if the device orientation has changed. Required as a work around for issue #141.</td>
  </tr>
  <tr>
  	<td><code>fadeInSpeed</code></td>
  	<td><code>250</code></td>
  	<td>The speed of any fading-in elements in milliseconds.</td>
  </tr>
  <tr>
  	<td><code>fadeOutSpeed</code></td>
  	<td><code>250</code></td>
  	<td>The speed of any fading-out elements in milliseconds.</td>
  </tr>
  <tr>
  	<td><code>imageScaleMethod</code></td>
  	<td><code>fit</code></td>
  	<td>How images will fit onto the screen. Either <code>fit</code>, <code>fitNoUpscale</code> or <code>zoom</code>. <code>fit</code> ensures the image always fits the screen. <code>fitNoUpscale</code> works like <code>fit</code> but will never upscale the image. <code>zoom</code> the image will always fill the full screen, this may cause the image to be "zoomed" in and cropped.</td>
  </tr>
  <tr>
  	<td><code>invertMouseWheel</code></td>
  	<td><code>false</code></td>
  	<td>By default, moving the mouse wheel down will move to the next image, up to the previous. Setting this to true reverses this.</td>
  </tr>
  <tr>
  	<td><code>jQueryMobile</code></td>
  	<td></td>
  	<td>Whether PhotoSwipe is integrated into a jQuery Mobile project or not. By default, PhotoSwipe will try and work this out for you.</td>
  </tr>
  <tr>
  	<td><code>jQueryMobileDialogHash</code></td>
  	<td><code>&ui-state=dialog</code></td>
  	<td>The window hash tag used by jQuery Mobile and dialog pages.</td>
  </tr>
  <tr>
  	<td><code>loop</code></td>
  	<td><code>true</code></td>
  	<td>Whether the gallery auto-loops back to the beginning when you reach the end.</td>
  </tr>
  <tr>
  	<td><code>margin</code></td>
  	<td><code>20</code></td>
  	<td>The margin between each image in pixels.</td>
  </tr>
  <tr>
  	<td><code>maxUserZoom</code></td>
  	<td><code>5.0</code></td>
  	<td>The maximum a user can zoom into an image. (set to zero for this to be ignored)</td>
  </tr>
  <tr>
  	<td><code>minUserZoom</code></td>
  	<td><code>0.5</code></td>
  	<td>The minimum a user can zoom out of an image. (set to zero for this to be ignored)</td>
  </tr>
  <tr>
  	<td><code>mouseWheelSpeed</code></td>
  	<td><code>500</code></td>
  	<td>How responsive the mouse wheel is.</td>
  </tr>
  <tr>
  	<td><code>nextPreviousSlideSpeed</code></td>
  	<td><code>0</code> (immediately)</td>
  	<td>How fast images are displayed when the next/previous buttons are clicked in milliseconds.</td>
  </tr>
  <tr>
  	<td><code>preventHide</code></td>
  	<td><code>false</code></td>
  	<td>Prevents the user closing PhotoSwipe. Also hides the "close" button from the toolbar. Useful for "exclusive mode" (see examples/08-exclusive-mode.html).</td>
  </tr>
  <tr>
  	<td><code>preventSlideshow</code></td>
  	<td><code>false</code></td>
  	<td>Prevents the slideshow being activated. Also hides the "play" button from the toolbar.</td>
  </tr>
  <tr>
  	<td><code>preventDefaultTouchEvents</code></td>
  	<td><code>true</code></td>
  	<td>Prevents device default touch events (i.e. stops the user scrolling the screen upwards etc).</td>
  </tr>
  <tr>
  	<td><code>slideshowDelay</code></td>
  	<td><code>3000</code></td>
  	<td>The delay between showing the next image when in slideshow mode in milliseconds.</td>
  </tr>
  <tr>
  	<td><code>slideSpeed</code></td>
  	<td><code>250</code></td>
  	<td>How fast images slide into view in milliseconds.</td>
  </tr>
  <tr>
  	<td><code>swipeThreshold</code></td>
  	<td><code>50</code></td>
  	<td>How many pixels your finger has to move across the screen to register a swipe gesture.</td>
  </tr>
  <tr>
  	<td><code>swipeTimeThreshold</code></td>
  	<td><code>250</code></td>
  	<td>A swipe must take no longer than this value in milliseconds to be registered as a swipe gesture.</td>
  </tr>
  <tr>
  	<td><code>slideTimingFunction</code></td>
  	<td><code>ease-out</code></td>
  	<td>Easing function used when sliding.</td>
  </tr>
  <tr>
  	<td><code>target</code></td>
  	<td><code>window</code></td>
  	<td>DOM Target for PhotoSwipe. By default "window" which will mean PhotoSwipe runs "fullscreen". Value must be a valid DOM element.</td>
  </tr>
  <tr>
  	<td><code>uiWebViewResetPositionDelay</code></td>
  	<td><code>500</code></td>
  	<td>Related to <code>enableUIWebViewRepositionTimeout</code>.</td>
  </tr>
  <tr>
  	<td><code>zIndex</code></td>
  	<td><code>1000</code></td>
  	<td>The intial zIndex for PhotoSwipe</td>
  </tr>
</table>

Options - Custom Functions
--------------------------

You can provide your own functions to tell PhotoSwipe how to work with your mark up etc.

- `getToolbar`: Function that returns the HTML string to be used for the toolbar content
- `getImageSource`: Function to specify how the gallery obatins image sources. By default, the gallery assumes you send it a list of images with each image wrapped in an anchor tag. The anchor tag will contain the URL to the full size image. You can change this e.g. if you supply a list of images without an anchor tag, and supply the full size URL on the image's `rel` attribute:

```js
document.addEventListener('DOMContentLoaded', function(){
  var myPhotoSwipe = PhotoSwipe.attach(
    window.document.querySelectorAll('#Gallery a'),
    {
      getImageSource: function(el){
	    return el.getAttribute('rel');
      }
	}
  );
}, false);
```

- `getImageCaption`: Like `getImageSource`, function to specify how the gallery obatins image captions. By default, the gallery looks for an image's `alt` tag.
- `getImageMetaData`: Function to associated additional meta data against an image in the gallery. This meta data can then be used in your own code if you listen to the `onDisplayImage` event.

```js
getImageMetaData: function(el){
	return {
		longDescription: el.getAttribute(el, 'data-long-description')
	}
}
```

Keyboard controls for desktop browsers
--------------------------------------

- **Left cursor**: Previous image
- **Right cursor**: Next image
- **Escape**: Close gallery
- **Space bar**: Show toolbar / caption if they have faded from view. If both are hidden via the configuration, space bar will close the gallery
- **Enter**: Start slideshow
