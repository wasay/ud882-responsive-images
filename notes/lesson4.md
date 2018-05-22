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
        
        webP image example 
        #pic {
          background: image("foo.webp", "foo.jpg");
        }
    
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
    