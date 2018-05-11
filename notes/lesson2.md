Lesson 7

width: calc((100% - 10px)/2);

Examples:

Fixed size image
http://udacity.github.io/responsive-images/examples/1-07/singleImage640x360/

width: 100%
http://udacity.github.io/responsive-images/examples/1-07/singleImageNotBigEnough100pc/

max width: 100%
http://udacity.github.io/responsive-images/examples/1-07/singleImageMaxWidth100pc/

Two images, 50% width
http://udacity.github.io/responsive-images/examples/1-07/twoImages50pc

Two images, 50% width with margin
http://udacity.github.io/responsive-images/examples/1-07/twoImages50pcWithMargin

You can find out more about calc() from Mozilla Developer Network.

The horse and giraffe are from lorempixel.com, which provides URLs for random placeholder images. For example, check this out.

https://developer.mozilla.org/en-US/docs/Web/CSS/calc

http://lorempixel.com/

http://lorempixel.com/400/200/animals/

# no margin on last image
img:last-of-type { margin-right:0;}

# even though margin 10px is just on the right side
# we still remove 20px from the width of the image
margin-right:10px;
width:calc((100% - 20px) / 3);

Dachsund Image
http://udacity.github.io/responsive-images/examples/1-09/landscapeImageTooWideForPhonePortrait/

vh = view port height

for full width or full height of screen (this will scale)
width: 100vmin;
height: 100vmin;

for full width or full height of screen (no scaleing)
width: 100vmax;
height: 100vmax;

Did you notice how setting both the height and the width to 100vmax or 
100vmin changes the image's aspect ratio? It'll compress your images to squares, 
so be careful if you want to maintain a different aspect ratio!

Open the SVG v PNG example in a large display – you'll see a massive difference in quality!
http://udacity.github.io/responsive-images/examples/1-11/svgVersusPng/

quiz
chrome logo, kittens
http://udacity.github.io/responsive-images/examples/1-14/differentImages/index.html

Section 12
Examples:

Photo with logo as JPEG
http://udacity.github.io/responsive-images/examples/1-15/kittensPlusHtml5Logo

Photo as JPEG, logo overlaid as SVG
http://udacity.github.io/responsive-images/examples/1-15/kittensPlusHtml5LogoSvg

SVG v PNG v JPG
http://udacity.github.io/responsive-images/examples/1-15/svgPngJpg

Image formats
https://litmus.com/blog/png-gif-or-jpeg-which-ones-should-you-use-in-email

Image optimization
https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization

More about WebP
https://developers.google.com/speed/webp/?csw=1

Browser support for WebP
http://caniuse.com/#feat=webp