# light_mode_toggle
A light mode toggle for your website!

This is a simple piece of JavaScript that will enable you to easily setup a light mode toggle for your website. I'm putting this here on Github, because, like with most things related to development and web development, documentation and how-tos are few and far between, scattered, random, and hard to find in-general. All you have to do is copy the provided files into your JavaScript path, and then start setting up the elements (which I can't do for you, unfortunately).

What these scripts do, is, the initial state script helps the main toggle script determine what position the user has the slider in, so that it can be consistent across all pages. This *may* cause some flicker, but you can put a transition on the body in order to make it look smoother.

Example:
```
body {
    transition: background-color 0.3s, color 0.3s;
}
```
This will effectively ensure that, even if there's a little bit of a transition with light mode toggled on, it'll smooth out when navigating between pages. I am, unfortunately, *still* trying to figure out how to make the saved light state be 100% consistent in that it doesn't need to transition between page loads on separate navigation.

Your script setup should be like this:

```
<head>
<!-- head content, like meta tags and title, and what-not -->
<script src="/assets/js/initial-state.js"></script> <!-- load this script first -->
<!-- the rest of your scripts -->
<script src="/assets/js/light-mode.js"></script>
</head>
```
Albeit, you don't *need* to put the script into /assets/js, that's just *my* website structure.

Anyway, in order to get this working, do what's described above, and then this ...

In every element in your CSS that depicts a color, be it for your background, or your links, you're going to want to make a sister element that says, "Hey, so, this is going to be the light mode version."

For example:

```
body {
  background-color: #000;
}
```
This (obviously), says that your background on the website is black. Without changing that, you'll want to put this right beneath it:

```
.light-mode {
  background-color: #FFF;
}
```
But for other elements, you'll want to do something like this:

Default state
```
a { 
  color: #00d9ff; 
  text-decoration: none; 
}
```
This says that your links are, by default, a neon blue, with no decoration.
```
.light-mode a {
  color: #000;
  text-decoration: underline;
}
```
But, in light mode, your links are now black, and underlined.

Now, let's set us up the toggle switch so that you can turn this one. Take this piece of code, and put it wherever you want on your website, be it in a sidebar, or right above the main content. It's up to you!
```
        <p class="symbols">
          <i class="ph ph-moon"></i> / <i class="ph ph-sun"></i>
        </p>
          <label class="switch">
            <input type="checkbox" id="light-mode-toggle">
            <span class="slider round"></span>
          </label>
```
Notice, I'm using Phosphor icons to show a moon and a sun, so that it's more apparent what each toggle position does. You'll want to go to <a href="https://phosphoricons.com" target="_blank">this website</a> to get yourself these icons for your own site. I do not recommend using font-awesome, since they've gone full-greed mode.

If you want a switch that *only* shows for mobile users, just-in-case you have elements of your site that are hidden when on smaller screens (therefore, possibly hiding your toggle switch), you can do this to give mobile users a toggle of their own.

```
    <!-- Mobile Light Mode Toggle -->
      <div id="mobile-light-mode-toggle" class="mobile-only center">
        <p class="symbols">
          <i class="ph ph-moon"></i> / <i class="ph ph-sun"></i>
        </p>
        <label class="switch">
          <input type="checkbox" id="mobile-light-mode-checkbox">
          <span class="slider round"></span>
        </label>
      </div>
```
Ignore the "center", and "symbols" classes, these are just elements I use for divs and styling on my own site. But, now, here's the associated CSS styling to make this work, *specifically*.

```
/* Show the desktop-only content on desktop devices */
@media (min-width: 481px) {
  .desktop-only {
    display: block;
  }
}

/* Hide the mobile toggle on desktop */
.mobile-only {
  display: none;
}

/* Show the mobile toggle on mobile devices */
@media (max-width: 480px) {
  .mobile-only {
    display: block;
  }

  #sidebar .switch {
    display: none;
  }
}
```
On your desktop version of the toggle, include "desktop-only" as a class, and in the mobile version of the switch, include "mobile-online." In this way, the switch will move positions depending on whether you're viewing the site on desktop, or on mobile. I'm using anything greater than 481 pixels for desktop, and anything 480 pixels or below for mobile. I've tested this on the <a href="https://vivaldi.com" target="_blank">Vivaldi</a> browser responsive settings in the developer mode, and this seems to work best. You can, *of course*, completely change this, if you like.

There are settings within the light mode script that ensure having *two* toggles on your site will stay synchronized, instead of breaking.

Now, with all this code, and both scripts, you should have no problems customizing this to your liking! Enjoy!
