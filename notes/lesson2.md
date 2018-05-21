Lesson 2
Units, Formats and Environment

Example - Horses differing images
"browser disable caches"
http://udacity.github.io/responsive-images/examples/1-05/identicalImagesDifferentCompressionAndSize/index.html

HTTP Archive: on average, web pages make 56 requests for images.
http://httparchive.org/trends.php#bytesImg&reqImg

Every 100ms of latency costs Amazon 1% of profit
https://news.ycombinator.com/item?id=273900

The impact of site performance
http://www.lesniakswann.com/news/the-need-for-website-speed.html



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
https://developer.mozilla.org/en-US/docs/Web/CSS/calc

The horse and giraffe are from lorempixel.com, which provides URLs for random placeholder
images. For example, check this out.

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

quiz: raster or vector banner?

chrome logo, kittens
http://udacity.github.io/responsive-images/examples/1-14/differentImages/index.html

File formats:
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

Quiz: Spot the difference
http://udacity.github.io/responsive-images/examples/1-17/sameImage/index.html

Image Issues?
Does the image data look the same for both images? The images have probably been cached! 
Make sure to check the Disable cache checkbox in DevTools. 

Quiz: Spot the difference 2
http://udacity.github.io/responsive-images/examples/1-19/sameImage/index.html

Note about PageSpeed Insights and Developer Tools
PageSpeed Insights is no longer part of Developer Tools. It has been deprecated. 
https://developers.google.com/speed/pagespeed/insights_extensions
The online version is still available.
https://developers.google.com/speed/pagespeed/insights/

PageSpeed Insights example
https://developers.google.com/speed/pagespeed/insights/?url=simpl.info%2Fcssfilters
Grunt PageSpeed plugin
https://www.npmjs.com/package/grunt-pagespeed
PageSpeed Node module
https://github.com/addyosmani/psi/
cURL examples
http://www.thegeekstuff.com/2012/04/curl-examples/
PageSpeed Insights Node module
https://github.com/addyosmani/psi/




Quiz: Project Part 1
Download the project files here.*
Make sure to run your project through localhost. For Mac/Linux cd to your work directory and set up a simple HTTP server. For Windows, see below.
http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python

Make sure you are running the Udacity Feedback Chrome Extension to get feedback.

Open the console to see the total size of all of your images!

Learn more about the figure tag!
https://developer.mozilla.org/en-US/docs/Web/HTML/Element/figure

Setting up Build Process
Before you start automating your build process with tools like ImageMagick or ImageOptim, 
you will first need to install Node.js. Node.js is a JavaScript runtime built on 
Chrome's V8 JavaScript engine. It also comes with a package manager, npm, that gives 
you access to thousands of code packages, like Grunt, that you can use in your projects. 
Make sure you've installed Node.js and updated npm. Then, use the links below to finish 
setting up your build process.

https://nodejs.org/en/download/
https://nodejs.org/en
https://developers.google.com/v8/
https://www.npmjs.com/
https://docs.npmjs.com/getting-started/installing-node

ImageMagick:
ImageMagick
http://www.imagemagick.org/

Simple ImageMagick installer for Mac
http://cactuslab.com/imagemagick/

GraphicsMagick (a fork of ImageMagick)
http://www.graphicsmagick.org/


Grunt:
Getting started with Grunt
http://gruntjs.com/getting-started

$ grunt

Grunt for People Who Think Things Like Grunt are Weird and Hard
http://24ways.org/2013/grunt-is-not-weird-and-hard/
Generate multi-resolution images with Grunt
http://addyosmani.com/blog/generate-multi-resolution-images-for-srcset-with-grunt/

Grunt plugin for generating multiple images
https://github.com/andismith/grunt-responsive-images


Files used in scripting examples:
convert.sh (includes instructions)
http://udacity.github.io/responsive-images/convert.sh

Gruntfile.js (remove line 7, engine: 'im', on Windows)
http://udacity.github.io/responsive-images/Gruntfile.js

Imager.js: responsive image loading developed for BBC News
https://github.com/BBC-News/Imager.js/

Image processing tools:

ImageOptim (Mac only)
http://imageoptim.com/

Trimage - Similar to ImageOptim (Windows, Mac, Linux)
http://trimage.org/

ImageAlpha
https://github.com/pornel/ImageAlpha


Feel Free to follow this article to learn more about running localhost on windows. 
If the article is unhelpful please follow the advice below

Student ("James") suggested instructions for running localhost on windows:

First you must turn on IIS:

Start>Control Panel>Programs>Turn Windows features on or off

The Windows Features box will appear. It may take a while for it to load

Scroll down and find Internet Information Services and ensure the box is clicked. 
Underneath that is Internet Information Services Hostable Web Core. Click that box as well.

Second you must open the Internet Information Services (IIS) Manager and configure IIS

Click the Start button and type IIS in the search bar

Click on Internet Information Services (IIS) Manager to open

In the left Connections pane click the little arrowhead to open the tree and right click 
on the Sites folder

Click Add Web Site

Give the site a name, and add the path to the folder where your website is located.

Go to the IP address and click the drop down. Find the IP address (ex. 192.168.0.92). 
(write this down somewhere. I put it as comments in my html and css files)

Pick a port. I don't recommend using port 80 but any other should do. I used 90

click ok.

Third, set read permissions on the website folder

Right-click on the folder your website is kept on and click on properties

Go to the security tab and scroll through Group or user names and look for the following:

IUSR and IIS_IUSRS

If they are there, be sure that "read & execute" and "read" are checked. If they are there 
and not checked click on on of them and then click edit. check the box for read & execute 
and read. Click apply then click ok.

If they are not there then click edit and then Add. This brings up the Select Users or 
Groups box.

Click the Advanced Button and then the Find Now button. Scroll down until you find IIS_IUSRS. 
Click on it and press OK 2 times. Click apply.

Repeat for IUSR

To bring up website on local host

Open Chrome and type in the IP address and port like this:

192.168.0.142:90 (or whatever your port number is)

I hope this helps. Good luck

Student ("Alexander") also recommends this video for Windows Setup:

https://www.youtube.com/watch?v=A_0SqnOPSng

Changing security/permissions for IIS* files/folders

*Microsoft Internet Information Services (IIS)

Feel Free to follow this article to learn more about running localhost on windows. 
If the article is unhelpful you are welcome to try Fenix to quickly host your project 
or you can give the advice below a try.
http://www.aspdotnet-suresh.com/2015/02/empty-missing-binding-type-in-iis-8-in-windows8.html
http://fenixwebserver.com/

Download the project here instead!
http://udacity.github.io/responsive-images/downloads/RI-Project-Part-1-Solution.zip

For the Project Part 1 Tests, 3rd item "Page bytes are under 1.5MB (refresh to update)" 
will work properly if you run your own webserver. From your terminal (mac/linux):

change directories to where your index.html file is
run a web server, such as python -m SimpleHTTPServer 8080
view the page, going to this URL http://localhost:8080/
