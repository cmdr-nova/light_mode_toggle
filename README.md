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

Now, with all this code, and both scripts, you should have no problems customizing this to your liking! Enjoy!
