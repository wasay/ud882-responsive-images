Lesson 1-5 = ud893
Lesson 6-9 = ud882



1 device independent pixel may not be same as 1 hardware pixel

<meta name="viewport" content="width=device-width, initial-scale=1.0">


**************************

for best touch experience, have the object width and height set to 48 pixels

48x48 will be a good click option

at least have 40 pixel tap target to avoid tap issues


<style>
a, button, input[type=button], input[type=submit]
{
	min-width:48px;
	min-height:48px;
}

/* OR */

a, button, input[type=button], input[type=submit]
{
	padding: 1.5em;
}
</style>
**************************

start from small form factor to large form factors

mobile first, tablet, and laptops and desktops

it's better to go from small to large as it helps in prioritize the content

header and nav, set width to 100%

make sure of full viewport by using 100% width


320 pixels, could be the smallest device width

**************************
<img id="owl">
#owl {
    width: 640px;
    max-width: 100%;
}

<img class="logo">
.logo {
    width: 125px;
}

<div class="city"></div>
.city{
    width: 100%;
}
**************************

<link rel="stylesheet" href="styles.css">

// stay with SCREEN OR PRINT
// ALL OTHER MEDIA QUERIES ARE NOT MUCH IN USE

<link rel="stylesheet" media="screen and (min-width: 500px)"
    href="over500.css" >

OR

<style>
    @media screen and (min-width: 500px) {
        /* */
    }
</style>

OR

// IMPORT TAGS are not good for performace
<style>
    @import url("over500.css" only screen and (min-width: 500px);
</style>

**************************
Media Queries
**************************

                    scan

mm-aspect-ratio     aspect          max-aspect-ratio
min-color           color           max-color
min-height          height          max-height
min-width           width           max-width
min-resolution      resolution      max-resolution

                    grid


// AVOID
min-device-width    max-device-width
**************************


// style
.container {
    display: flex;
    flex-wrap: wrap;
}
.box {
    height: 100px;
    text-align: center;
    width: 100%;
}


/*
force table to act like div

<table>
    <thead>
        <tr>
            <th>Team</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td data-th="Team">Tiger</td>
        </tr>
    </tbody>
</table>

@media screen and (max-width: 500px)
{
    table, thead, tbody, tfoot, tr, th, td
    {
        display: block;
    }
    thead tr{
        position: absolute;
        top: -9999px;
        left: -9999px;
    }
    td {
        position: relative;
        padding-left: 50%;
    }
    td:before {
        position: absolute;
        left: 6px;
        content: attr(data-th);
        font-weight: bold;
    }
}

// https://css-tricks.com/responsive-data-table-roundup/

// https://codepen.io/JohnMav/pen/Mazrwm

// contained table
div.contained_table {
    width:100%;
    overflow-x: auto;
}

<div class="contained_table">
    <table></table>
</div>

// ideal measure
45 charactors per line to 90 characters per line

// consensus for web
65 charactors

// good font size
font-size: 16 px;
line-height: 1.2em;

*/

.truncate {
  width: 250px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

Page breakpoints

Common breakpoints are at around 
480, 667, 768, 800, 900, 1024 and 1280 pixels.
This all depends on your page layout, though. There probably 
aren't any "fixed" criteria for breakpoints. 
If things get too "wide" it's probably time for a breakpoint.
 
 Accessible & Responsive Web Apps