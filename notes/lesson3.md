Images with Markup

Content 1. Performance

Why is latency the new bottleneck? Check out what Ilya has to say in High Performance Browser Networking. 
Notice how reducing latency continues to improve page load times, whereas for bandwidth the graph flattens out:
http://chimera.labs.oreilly.com/books/1230000000545/ch10.html#MORE_BANDWIDTH_DOESNT_MATTER_MUCH

To reduce the number of image downloads, you can also use CSS image sprites (or responsive sprites). 
A sprite sheet image combines lots of images, which can be displayed individually by setting the sprite 
sheet as the background to an element, then adjusting background position with CSS. This technique can be 
particularly useful for icons and other repeated graphics.

https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/CSS_Image_Sprites
http://blog.brianjohnsondesign.com/responsive-background-image-sprites-css-tutorial/
https://www.google.co.uk/images/nav_logo195.png


Whatever techniques you use to avoid latency, be aware of the changes that are coming with HTTP/2.

In a nutshell, HTTP/2 will mean that requesting multiple files will be less costly: prepare to stop using 
spriting, concatenating and other HTTP/1 hacks!

To find out more, check out HTTP2 for front-end web devs.


Content 2. Text Problems

Text as image
http://udacity.github.io/responsive-images/examples/2-02/textAsImage

Text as image over photo
http://udacity.github.io/responsive-images/examples/2-02/textAsImageOverPhoto

Text using Web Font
http://udacity.github.io/responsive-images/examples/2-02/textAsText

Text as text, over photo
http://udacity.github.io/responsive-images/examples/2-02/textAsTextOverPhoto


Content 3. CSS Techniques
CSS effects
http://udacity.github.io/responsive-images/examples/2-04/divWithCssEffects

How CSS affects load time
http://smashingmagazine.com/2013/04/03/build-fast-loading-mobile-website

Amazon’s separate mobile product pages use a responsive-images technique 
that assigns a particular background image to a div according to media-query matches.
http://smashingmagazine.com/2013/04/03/build-fast-loading-mobile-website 


Content 4. CSS background Images

Div with background image
http://udacity.github.io/responsive-images/examples/2-06/divWithBackgroundImage

    body {
      align-items: center;
      display: flex;
      height: 100vh;
      justify-content: center;
      margin: 0;
    }
    div#background {
      align-items: center;
      background: url(backgroundPattern.png);
      display: flex;
      height: 50vw;
      justify-content: center;
      width: 50vw;
    }
    div#background div {
      align-items: center;
      background: white;
      display: flex;
      font-family: Courier;
      font-size: 5vmin;
      height: 20vw;
      justify-content: center;
      margin: 5vw;
      padding: 2vw;
      text-align: center;
      width: 20vw;
    }

CSS background-size: cover
http://udacity.github.io/responsive-images/examples/2-06/backgroundSizeCover

    body {
      align-items: center;
      background-image: url(albino_kookaburra.jpg);
      background-repeat: no-repeat;
      background-size: cover;
      display: flex;
      font-size: 10vw;
      font-family: "Roboto Condensed";
      text-shadow: 5px 5px 15px #333;
      height: 100vh;
      justify-content: center;
      margin: 0;
    }

Body with background image
http://udacity.github.io/responsive-images/examples/2-06/bodyWithBackgroundImage

    body {
      background-image: url(html5.svg);
      background-repeat: no-repeat;
      background-position: 97% 95%;
      background-size: 5%;
      margin: 0;
    }
    html {
      height: 100vh;
    }

Body with background image and gradient
http://udacity.github.io/responsive-images/examples/2-06/bodyWithBackgroundImageAndGradient

    body {
      background: url(html5.svg) no-repeat;
      background-position: 97% 95%;
      background-size: 5%;
      height: 100vh;
      margin: 0;
    }
    html {
      background: linear-gradient(#000, white) no-repeat;
      height: 100vh;
    }

Body with elaborate background using only CSS
http://udacity.github.io/responsive-images/examples/2-06/bodyWithElaboratePatternPureCSS

    body {
      background:
      linear-gradient(27deg, #151515 5px, transparent 5px) 0 5px,
      linear-gradient(207deg, #151515 5px, transparent 5px) 10px 0px,
      linear-gradient(27deg, #222 5px, transparent 5px) 0px 10px,
      linear-gradient(207deg, #222 5px, transparent 5px) 10px 5px,
      linear-gradient(90deg, #1b1b1b 10px, transparent 10px),
      linear-gradient(#1d1d1d 25%, #1a1a1a 25%, #1a1a1a 50%, transparent 50%, transparent 75%, #242424 75%, #242424);
      background-color: #131313;
      background-size: 20px 20px;
    }

Using CSS background images for conditional image display
http://udacity.github.io/responsive-images/examples/2-06/backgroundImageConditional

    body {
      font-family: 'Roboto Condensed';
      font-weight: 200;
      margin: 5vw;
    }
    div.koala {
      background-image: url(koala.jpg);
    }
    div.photo {
      background-size: cover;
      float: left;
      margin: 0 2vw 1vw 0;
      height: 50vw;
      position: relative;
      top: 3px;
      transition: all 0.5s;
      width: 50vw;

    }
    @media screen and (max-width: 500px) {
      div.photo {
        background-image: none;
        height: 0;
        margin: 0;
        width: 0;
      }
    }

Using CSS background images for alternative images
http://udacity.github.io/responsive-images/examples/2-06/backgroundImageAlternative

    body {
      align-items: center;
      display: flex;
      height: 100vh;
      justify-content: center;
      margin: 0;
    }
    div {
      background-image: url(koala.jpg);
      background-size: cover;
      height: 50vw;
      transition: background-image 2s;
      width: 50vw;
    }
    @media screen and (max-width: 500px) {
      div {
        background-image: url(koala_crop.jpg);
      }
    }

image-set()
http://udacity.github.io/responsive-images/examples/2-06/imageSet

    body {
      align-items: center;
      display: flex;
      height: 100vh;
      justify-content: center;
    }

    div {
      background-image: url(icon1x.png);
      background-image: -webkit-image-set(url(icon1x.png) 1x, url(icon2x.png) 2x);
      background-image: image-set(url(icon1x.png) 1x, url(icon2x.png) 2x);
      height: 128px;
      width: 128px;
    }
    
Content 5: Quiz: CSS background image techniques

    background-size: cover (small as possible still filling it's container)
    
    background-size: contain (large as possible still visible in container)
    
    
Content 6: Symbol characters
    Example: Unicode instead of an image
    http://udacity.github.io/responsive-images/examples/2-08/unicodeStar

    Unicode character sets
    http://unicode-table.com/en/sets/
    
    List of Unicode characters
    http://en.wikipedia.org/wiki/List_of_Unicode_characters



Content 7: Quiz: Unicode Treble Clef
    Here's a big list of unicode characters.
    http://unicode-table.com/
    
    More on meta tag charsets
    https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta
    
    Having trouble seeing unicode characters? Unfortunately, not all browsers include the fonts needed 
    to see all unicode characters by default. This site will help you determine what characters your 
    browser can render and here's some advice for enabling unicode with Chrome on Windows.
    http://www.alanwood.net/unicode/#links
    http://gschoppe.com/uncategorized/fixing-unicode-support-in-google-chrome/
    
    Still having trouble with unicode? Help us out by letting us know what OS and browser you're using in the forums.
    
    
    
Content 8: Icon Fonts
    Zocial
    http://zocial.smcllns.com/
    
    Font Awesome
    http://fortawesome.github.io/Font-Awesome/
    
    We Love Icon Fonts!
    http://weloveiconfonts.com/
    
    Icon fonts on CSS-Tricks
    https://css-tricks.com/examples/IconFont/
    
    ARIA
    https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA
    
    How Zocial works:
    @import url(http://weloveiconfonts.com/api/?family=zocial);

    /* zocial */
    [class*="zocial-"]:before {
      font-family: 'zocial', sans-serif;
    }
    
    <!-- Single Element -->
    <span class="zocial-dribbble"></span>
    
    <!-- Group of Elements -->
    <ul>
      <li class="zocial-twitter"></li>
      <li class="zocial-flickr"></li>
      <li class="zocial-lastfm"></li>
      <li class="zocial-reddit"></li>
    </ul>
    
    
    
Content 9: Inlining images with SVG and data URIs
    Examples:
    
    SVG Data URI in HTML
    http://udacity.github.io/responsive-images/examples/2-11/svgDataUri
    
    SVG Data URI in CSS
    http://udacity.github.io/responsive-images/examples/2-11/svgDataUriCss
    
    SVG text on a path
    http://udacity.github.io/responsive-images/examples/2-11/svgTextOnAPath
    
    SVG optimized and unoptimized
    http://udacity.github.io/responsive-images/examples/2-11/svgUnoptimisedAndOptimised
    
    Browser support for inline SVG
    http://caniuse.com/#feat=svg-html5
    
    Browser support for Data URIs
    http://caniuse.com/datauri
    
    SVG Optimiser
    http://petercollingridge.appspot.com/svg-optimiser
    
    Trajan's Column SVG example
    http://upload.wikimedia.org/wikipedia/commons/6/6c/Trajans-Column-lower-animated.svg
    
    20 examples of SVG that will make your jaw drop
    http://www.creativebloq.com/design/examples-svg-7112785
    
    SVG animation examples
    http://codepen.io/chrisgannon/
    
Content 10: Quiz: Strategy Quiz 1
    
    <img src="file.png">
    
    vs
    
    <img src="data:image/png;base64,..."/>
    
    raster image vs material design icon