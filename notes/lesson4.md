Lesson 4

Full Responsiveness

Content 1: Responding to Screen Capability & View

Before you start implementing responsive images, consider doing an image audit of your site:

What is the production workflow for images?
Do you use hero images, thumbnails, icons, decorations?
http://blog.cloudfour.com/responsive-hero-images/

Type-based guidelines for responsive hero images
When we had completed our research, we had a simple set of guidelines that we could give 
to the designers responsible for the hero images.

Image	Breakpoints
Name	Width	Height	Max Width	Min Width
Large	1080	360	    n/a	        781
Medium	780	    320	    780	        541
Small	540	    270	    540	        n/a
So long as the designers didn’t use anything smaller than 18pt and continued to only use the 
typeface that the brand specified, then the three sizes of hero images that we specified would work.

What image formats are used on your site?
Should some images be inlined or delivered as SVGs?

For more information, see Jason Grigsby's article Responsive Image Audits.
http://blog.cloudfour.com/responsive-images-audits

Pro tip: to get the maximum bang-for-your-buck when optimizing your site, focus on very large 
images. Pick the ten largest!

In particular, resizing images in CSS or HTML can be a huge problem for big images. For example: 
you need a 1000x1000px image file to display in a 500x500px img element on a 2x screen. If you 
use a 1100x1100px image, that's 100 x 100 = 10,000 wasted pixels!



Content 2: srcset
Spot the deliberate mistake!

At around 2:30 you'll see that Firefox chooses wallaby_1x.jpg even with srcset turned on. That's because we did the screencast on a 1x display :^).

Examples:

srcset with w values
http://udacity.github.io/responsive-images/examples/3-03/srcsetWValues

srcset with w values, 50vw
http://udacity.github.io/responsive-images/examples/3-03/srcsetWValues50vw


A fun article on srcset (Warning: A little bit of NSFW language)
http://ericportis.com/posts/2014/srcset-sizes/

large.jpg (1024 x 768)
medium.jpg (640 x 480)
small.jpg (320 x 240)

Device pixel density list
http://pixensity.com/list/phone

More information about working with pixel density
http://www.html5rocks.com/en/mobile/high-dpi/

Working with h units
https://github.com/ResponsiveImagesCG/picture-element/issues/86

Wikipedia wallabies
https://en.wikipedia.org/wiki/Wallaby

    <img src="wallaby_1x.jpg" srcset="wallaby_1x.jpg 1x,
        wallaby_2x.jpg 2x" alt="Wallaby">
        
    browser console
    
    get device pixel ratio
    
    window.devicePixelRation
    
    <img src="small.jpg" srcset="small.jpg 500w, medium.jpg 100w,
            large.jpg 1500w" alt="Wallaby">


Content 3. Sizes Attribute

Examples:

srcset with w values
http://udacity.github.io/responsive-images/examples/3-03/srcsetWValues

srcset with w values, 50vw
http://udacity.github.io/responsive-images/examples/3-03/srcsetWValues50vw

In JavaScript you can get the source of an img element with currentSrc.

The sizes attribute gives the browser information about the display size 
of an image element – it does not actually cause the image to be resized. 
That's done in CSS!
    
    <img src="small.jpg" srcset="small.jpg 500w, medium.jpg 1000w,
         large.jpg 1500w" sizes="50vw" alt="Wallaby"/>

    img {
        transition: width 0.5s;
        width: 50vw;
    }
    @media screen and (max-width: 250px)
    {
        img {
            width: 100vw;
        }
    }
    
    <img src="small.jpg" srcset="small.jpg 500w, medium.jpg 1000w,
         large.jpg 1500w" sizes="(max-width:250px) 100vw, 50vw" alt="Wallaby"/>
         
         
    browser console
    get the current responsive image source file
    
    $0.currentSrc
    
Content 4. Quiz: srcset Quiz
    Syntax
    There are two flavors of srcset, one using x to differentiate between device 
    pixel ratios (DPR), and the other using w to describe the image's width.
    
    Reacting to Device Pixel Ratio
    
    <img src="image_2x.jpg" srcset="image_2x.jpg 2x, image_1x.jpg 1x" alt="a cool image">
    
    Set srcset equal to a comma separated string of filename multiplier pairs, where 
    each multiplier must be an integer followed by an x.
    
    For example, 1x represents 1x displays and 2x represents displays with twice the 
    pixel density, like Apple's Retina displays.
    
    The browser will download the image that best corresponds to its DPR .
    
    Also, note that there's a src attribute as a fallback.
    
    High DPI Images for Variable Pixel Densities explains Device Pixel Ratio in detail: 
    device-pixels-per-CSS-pixel is not quite the whole story!
    http://html5rocks.com/en/mobile/high-dpi
    
        It is recommended that the reference pixel be the visual angle of one pixel on 
        a device with a pixel density of 96dpi and a distance from the reader of an 
        arm's length. For a nominal arm's length of 28 inches, the visual angle is 
        therefore about 0.0213 degrees.
        
        physicalPixels = window.devicePixelRatio * idealPixels
        
        Overview of HiDPI image techniques
        There are many techniques for solving the problem of showing the best quality 
        images as fast as possible, broadly falling into two categories:
        
        Optimizing single images, and
        Optimizing selection between multiple images.
        Single image approaches: use one image, but do something clever with it. These 
        approaches have the drawback that you will inevitably sacrifice performance, 
        since you will be downloading HiDPI images even on older devices with lower DPI. 
        Here are some approaches for the single image case:
        
        Heavily compressed HiDPI image
        Totally awesome image format
        Progressive image format
        Multiple image approaches: use multiple images, but do something clever to pick 
        which to load. These approaches have inherent overhead for the developer to 
        create multiple versions of the same asset and then figure out a decision strategy. 
        
        Here are the options:
        
        JavaScript
        Server side delivery
        CSS media queries
        Built-in browser features (image-set(), <img srcset>)
        
        Modernizr ships with such a feature detection script, which is available via Modernizr.webp.
        
        # WebP image and JPEG fallback image
        #pic {
          background: image("foo.webp", "foo.jpg");
        }
        
        #  If you want to load high DPI images and the device pixel ratio exceeds a threshold, 
        # here's what you might do
        
        #my-image { background: (low.png); }

        @media only screen and (min-device-pixel-ratio: 1.5) {
          #my-image { background: (high.png); }
        }
        
        #It gets a little more complicated with all of the vendor prefixes mixed in, especially 
        # because of insane differences in placement of "min" and "max" prefixes:
        
        @media only screen and (min--moz-device-pixel-ratio: 1.5),
            (-o-min-device-pixel-ratio: 3/2),
            (-webkit-min-device-pixel-ratio: 1.5),
            (min-device-pixel-ratio: 1.5) {
        
          #my-image {
            background:url(high.png);
          }
        }
        
        Browser features for high DPI support
        
        Best practices for image-set
        
        background-image:  -webkit-image-set(
          url(icon1x.jpg) 1x,
          url(icon2x.jpg) 2x
        );
        
        ## fallback
        background-image: url(icon1x.jpg);
        background-image: -webkit-image-set(
          url(icon1x.jpg) 1x,
          url(icon2x.jpg) 2x
        );
        /* This will be useful if image-set gets into the platform, unprefixed.
           Also include other prefixed versions of this */
        background-image: image-set(
          url(icon1x.jpg) 1x,
          url(icon2x.jpg) 2x
        );
        
        
        #Image srcset
        
        <img alt="my awesome image"
          src="banner.jpeg"
          srcset="banner-HD.jpeg 2x, banner-phone.jpeg 640w, banner-phone-HD.jpeg 640w 2x">
          
        # not recommended div example
        <div id="my-content-image"
          style="content: -webkit-image-set(
            url(icon1x.jpg) 1x,
            url(icon2x.jpg) 2x);">
        </div>
        
        To summarize, my recommendations are as follows:
        
        For background images, use image-set with the appropriate fallbacks for browsers that 
        don't support it.
        
        For content images, use a srcset polyfill, or fallback to using image-set (see above).
        
        For situations where you're willing to sacrifice image quality, consider using heavily 
        compressed 2x images.
    
    Reacting to Image Width
    
    <img src="image_200.jpg" srcset="image_200.jpg 200w, image_100.jpg 100w" alt="a cool image">
    Set srcset equal to a comma separated string of filename widthDescriptor pairs, where each 
    widthDescriptor is measured in pixels and must be an integer followed by a w. Here, 
    the widthDescriptor gives the natural width of each image file, which enables the browser 
    to choose the most appropriate image to request, depending on viewport size and DPR. 
    (Without the widthDescriptor, the browser cannot know the width of an image without downloading it!)
    
    Also, note that there's a src attribute as a fallback.
    
    Quiz
    
    <img class="dpi" src="images/Den_Haag_2x.jpg" alt="Den Haag Skyline" 
        srcset="images/Den_Haag_1x.jpg 1x, images/Den_Haag_2x.jpg 2x">
        
    <img class="w" src="images/Australia_1280w.jpg" alt="Australia from Space" 
        srcset="images/Australia_1280w.jpg 1280w, images/Australia_640w.jpg 640w">
        
        
    DPR (Den Haag)
    <img  class="dpi"
          src="images/Den_Haag_2x.jpg"
          srcset="images/Den_Haag_2x.jpg 2x, images/Den_Haag_1x.jpg 1x"
          alt="Den Haag Skyline">
    Notice how I've got a src as a backup. The order of the sources in srcset doesn't matter. 
    Also, if you omit the multiplier, it will default to 1x, meaning that
    
    srcset="images/Den_Haag_2x.jpg 2x, images/Den_Haag_1x.jpg 1x"
    is the same as
    
    srcset="images/Den_Haag_2x.jpg 2x, images/Den_Haag_1x.jpg"
    
    Image Width (Australia)
    
    <img  class="w"
          src="images/Australia_1280w.jpg"
          srcset="images/Australia_1280w.jpg 1280w, images/Australia_640w.jpg 640w"
          alt="Australia from Space">
    
    Once again, there's a src backup and you can switch the order of the images in srcset.
    
    
    
Content 5: Quiz: srcset and sizes

    srcset with sizes Syntax
    Here's an example:
    
    <img  src="images/great_pic_800.jpg"
          sizes="(max-width: 400px) 100vw, (min-width: 401px) 50vw"
          srcset="images/great_pic_400.jpg 400w, images/great_pic_800.jpg 800w"
          alt="great picture">
          
    sizes consists of comma separated mediaQuery width pairs. sizes tells the browser early in 
    the load process that the image will be displayed at some width when the mediaQuery is hit.
    
    In fact, if sizes is missing, the browser defaults sizes to 100vw, meaning that it expects 
    the image will display at the full viewport width.
    
    sizes gives the browser one more piece of information to ensure that it downloads the right 
    image file based on the eventual display width of the image. Just to be clear, it does not 
    actually resize the image - that's what CSS does.
    
    
    If the DPR is a value between the densities of two adjacent candidates, the browser 
    calculates  the candidates' geometric mean. If DPR is higher than the geo mean, the candidate 
    with the larger density value "wins". Otherwise, it's the smaller one.
    
    For your example, the geo mean of 500w and 1000w is 707, which explains why only above that 
    value, the larger resource gets picked.
    
Content 6: The Picture Element
    Example:
    
    Picture element: alternative image formats
    http://udacity.github.io/responsive-images/examples/3-06/pictureAlternativeFormats
    
    More information about WebP
    https://developers.google.com/speed/webp/?csw=1
    
Content 7: The Full Monty
    Examples:
    
        Picture element: art direction
        http://udacity.github.io/responsive-images/examples/3-08/pictureArtDirection
        
        Picture element: with srcset and media queries
        http://udacity.github.io/responsive-images/examples/3-08/pictureFullMonty
        
        Picturefill polyfill
        http://udacity.github.io/responsive-images/examples/3-08/picturefill
    
    Images are by Jon Q from Pearl Chen's HTML5 Rocks article Built-in Browser Support
    for Responsive Images.
    https://twitter.com/itsjonq
    http://www.html5rocks.com/tutorials/responsive/picture-element/
    
    The <picture> syntax
    <style>
      img {display: block; margin: 0 auto;}
    </style>
    
    <picture>
      <source 
        media="(min-width: 650px)"
        srcset="images/kitten-stretching.png">
      <source 
        media="(min-width: 465px)"
        srcset="images/kitten-sitting.png">
      <img 
        src="images/kitten-curled.png" 
        alt="a cute kitten">
    </picture>
    
    The example below supports 1x, 1.5x, and 2x resolution screens:    
    <picture>
      <source 
        media="(min-width: 650px)" 
        srcset="images/kitten-stretching.png,
                images/kitten-stretching@1.5x.png 1.5x,  
                images/kitten-stretching@2x.png 2x">
      <source 
        media="(min-width: 465px)" 
        srcset="images/kitten-sitting.png,
                images/kitten-sitting@1.5x.png 1.5x
                images/kitten-sitting@2x.png 2x">
      <img 
        src="images/kitten-curled.png" 
        srcset="images/kitten-curled@1.5x.png 1.5x,
                images/kitten-curled@2x.png 2x"
        alt="a cute kitten">
    </picture>
    
    Here's an example of using the sizes attribute to set the proportion of an image to 
    always fill 80% of the viewport. It is combined with the srcset attribute to supply 
    four versions of the same lighthouse photo in widths of 160px, 320px, 640px, and 1280px wide:
    
    <img src="lighthouse-160.jpg" alt="lighthouse"
         sizes="80vw"
         srcset="lighthouse-160.jpg 160w, 
                 lighthouse-320.jpg 320w,        
                 lighthouse-640.jpg 640w,
                 lighthouse-1280.jpg 1280w">
                 
                 
        With the addition of <picture>, the sizes attribute can be applied to both 
        <img> and <source> elements:
        
        <picture>
          <source media="(min-width: 800px)"
                  sizes="80vw"
                  srcset="lighthouse-landscape-640.jpg 640w,
                          lighthouse-landscape-1280.jpg 1280w,
                          lighthouse-landscape-2560.jpg 2560w">
          <img src="lighthouse-160.jpg" alt="lighthouse"
               sizes="80vw"
               srcset="lighthouse-160.jpg 160w,
                       lighthouse-320.jpg 320w,
                       lighthouse-640.jpg 640w,
                       lighthouse-1280.jpg 1280w">
        </picture>
        
        Building on the previous example, when the viewport is at 800px and above, 
        the browser will serve up a landscape version of the lighthouse version instead
        
        Load alternative image file formats
        The type attribute of <source> can be used to load alternative image file formats 
        that might not be supported in all browsers. For example, you can serve an image 
        in WebP format to browsers that support it, while falling back to a JPEG on other
        browsers:
        
        <picture>
          <source type="image/webp" srcset="images/butterfly.webp">
          <img src="images/butterfly.jpg" alt="a butterfly">
        </picture>
    
    You can download Picturefill here.
    http://scottjehl.github.io/picturefill/
    
        Usage:
        <head>
          <script>
            // Picture element HTML5 shiv
            document.createElement( "picture" );
          </script>
          <script src="picturefill.js" async></script>
        </head>
        
        SUPPORTING PICTURE IN INTERNET EXPLORER 9
        <picture>
          <!--[if IE 9]><video style="display: none;"><![endif]-->
          <source srcset="examples/images/extralarge.jpg" media="(min-width: 1000px)">
          <source srcset="examples/images/large.jpg" media="(min-width: 800px)">
          <!--[if IE 9]></video><![endif]-->
          <img srcset="examples/images/medium.jpg" alt="…">
        </picture>
        
        PREVENTING THE FLASH OF WRONG IMAGE™ ON SAFARI
        <picture>
          <!--[if IE 9]><video style="display: none;"><![endif]-->
          <source srcset="examples/images/extralarge.jpg" media="(min-width: 1000px)">
          <source srcset="examples/images/large.jpg" media="(min-width: 800px)">
          <!--[if IE 9]></video><![endif]-->
          <img alt="…">
        </picture>
        
        `MEDIA` AND `SRCSET` SYNTAX:
        <picture>
          <source srcset="examples/images/large.jpg, examples/images/extralarge.jpg 2x" 
            media="(min-width: 800px)">
          <img srcset="examples/images/small.jpg, examples/images/medium.jpg 2x" alt="…">
        </picture>
        
        
        The `type` attribute in `picture`
        Picturefill supports SVG and WebP as part of its core, but the following MIME 
        types can be used via the “typesupport” plugin:
        
            image/bmp
            image/xbmp
            image/jp2
            image/vnd.ms-photo
            video/vnd.mozilla.apng
            
            <picture>
              <source srcset="examples/images/large.webp" type="image/webp">
              <img srcset="examples/images/large.jpg" alt="…">
            </picture>
        
        Picturefill JavaScript API
            
            picturefill();
            
            picturefill({
              reevaluate: true,
              elements: [ document.getElementById( "myImg" ) ]
            });
            
            SOURCE SELECTION ALGORITHM OPTION
            
            //generating the config array
            window.picturefillCFG = window.picturefillCFG || [];
            picturefillCFG.push([ "algorithm", "saveData" ]);
            
        SUPPORT CAVEATS
            Picturefill 3 includes a small shim that polyfills common media conditions for IE9
            and earlier (min-width, max-width, min-height, and max-height). If you need old IE 
            support for other media conditions, such as orientation or aspect-ratio, please 
            additionally include the matchMedia polyfill.
            https://github.com/paulirish/matchMedia.js/
            
            
            
    
    Element Queries will work like Media Queries, but with reference to the size of an 
    element's parent container rather than viewport size. Browser implementation is in 
    progress and in the meantime there's a polyfill here.
    
    https://responsiveimagescg.github.io/cq-usecases/
    http://marcj.github.io/css-element-queries/
    https://github.com/marcj/css-element-queries
        
        Examples: Element Query
        
        .widget-name h2 {
            font-size: 12px;
        }
        
        .widget-name[min-width~="400px"] h2 {
            font-size: 18px;
        }
        
        .widget-name[min-width~="600px"] h2 {
            padding: 55px;
            text-align: center;
            font-size: 24px;
        }
        
        .widget-name[min-width~="700px"] h2 {
            font-size: 34px;
            color: red;
        }
        
        <div class="widget-name">
           <h2>Element responsiveness FTW!</h2>
        </div>
        Responsive image
            <div data-responsive-image>
                <img data-src="http://placehold.it/350x150"/>
                <img min-width="350" data-src="http://placehold.it/700x300"/>
                <img min-width="700" data-src="http://placehold.it/1400x600"/>
            </div>
        Include the javascript files at the bottom and you're good to go. No custom 
        javascript calls needed.
        
        <script src="src/ResizeSensor.js"></script>
        <script src="src/ElementQueries.js"></script>
        
        
        Module Loader
        If you're using a module loader you need to trigger the event listening or 
        initialization yourself:
        
        var ElementQueries = require('css-element-queries/src/ElementQueries');
        
         //attaches to DOMLoadContent
        ElementQueries.listen();
        
        //or if you want to trigger it yourself.
        // Parse all available CSS and attach ResizeSensor to those elements which have 
        // rules attached
        // (make sure this is called after 'load' event, because CSS files are not ready 
        // when domReady is fired.
        ElementQueries.init();
    
    Lots of other <picture> use cases, examples and code snippets are available here.
    
    https://dev.opera.com/articles/responsive-images/
        <picture>
            <source
                media="(min-width: 1280px)"
                sizes="50vw"
                srcset="opera-fullshot-200.webp 200w,
                        opera-fullshot-400.webp 400w,
                        opera-fullshot-800.webp 800w,
                        opera-fullshot-1200.webp 1200w,
                        opera-fullshot-1600.webp 1600w,
                        opera-fullshot-2000.webp 2000w"
                type="image/webp">
            <source
                sizes="(min-width: 640px) 60vw, 100vw"
                srcset="opera-closeup-200.webp 200w,
                        opera-closeup-400.webp 400w,
                        opera-closeup-800.webp 800w,
                        opera-closeup-1200.webp 1200w,
                        opera-closeup-1600.webp 1600w,
                        opera-closeup-2000.webp 2000w"
                type="image/webp">
            <source
                media="(min-width: 1280px)"
                sizes="50vw"
                srcset="opera-fullshot-200.jpg 200w,
                        opera-fullshot-400.jpg 400w,
                        opera-fullshot-800.jpg 800w,
                        opera-fullshot-1200.jpg 1200w,
                        opera-fullshot-1600.jpg 1800w,
                        opera-fullshot-2000.jpg 2000w">
            <img
                src="opera-closeup-400.jpg" alt="The Oslo Opera House"
                sizes="(min-width: 640px) 60vw, 100vw"
                srcset="opera-closeup-200.jpg 200w,
                        opera-closeup-400.jpg 400w,
                        opera-closeup-800.jpg 800w,
                        opera-closeup-1200.jpg 1200w,
                        opera-closeup-1600.jpg 1600w,
                        opera-closeup-2000.jpg 2000w">
        </picture>
    
    Find out more about responsive images from the Responsive Images Community Group.
    http://responsiveimages.org/
    
Content 8: 
    Enable ChromeVox from Chrome browser Extensions