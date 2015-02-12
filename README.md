
# Gotchas

 - Animations are run sequentially (only runs after previous animation has completed)
 - You don't have to use the chaining syntax for the animations to be queued properly.
 - "display: none" or "visibility: hidden" always gets applied after animation completes, while "display: block" or "visibility: visible" applies before animation begins
 - Set "queue" to false in the options start immediately regardless of current animations in queued
 - An easier way to think about "loops" in options, is a setting defining how many times to return back to it's old css styles. Setting 'true', makes the animation infinite. Use the 'stop' command to stop animation (ex: $('div').velocity("stop"))
 - using "delay" and "loop" together means a delay for each loop
 - If a unit is left out, it defaults to the natural unit (ex: "200" becomes "200px" for divs, "deg" for "rotateX")
 - Don't use shorthand attributes (ex: use "paddingLeft" not "padding")
 - Velocity does vendor prefixes (ex: just use "transform," not "-webkit-transform")
 - Want to weave in some asynchrony Velocity's animations? Use their "utility" pattern which exposes a promised interface: 
```
jQuery.Velocity.animate($ele, { opacity: 0.5 })
  .then(function($ele) {console.log("Resolved."); })
  .catch(function(error) { console.log("Rejected."); });
```