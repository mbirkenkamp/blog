---
title: "Vue Focus Handling"
date: 2022-04-12T19:02:22+02:00
tags: ["vuejs", "vue", "focus", "elements", "refs", "learning"]
---

# Storytime

i was working on a POC for multi factor authentication using time-based one time passwords (TOTP) and wanted to create a nice input UI for this, so i thought this would be a great way to practice my vue knowledge and create another showcase of vue for the team. 

What i wanted was a UI like the one iOS uses, so 6 separate input boxes that are more or less handled like a normal input field but pretty 😊. I found a easy solution that was based solely on css styling of an input field, the look was approx. like this:

`_ _ _ _ _ _` 

which would have been an ok solution (and quick) but i really wanted the UI to shine and be the best i could do (remark: normally this would be out of scope for a POC, but i already implemented the backend in a way that could placed in the product as is, so i wanted the UI to also be "production ready").

# The Problem

i did a quick prototype in codepen with 6 input fields and quickly got to the point where i wanted to jump to the next field on input, which i could do with document.getElementById(...) etc. in a vanillajs sort of way, but this seemed a little tedious and since a lot of things have elegant solutions in vue, i tried to find out if this was really the way to do it in vue.

# Analysis

my suspicion was right, according to [Focus management with Vue refs - Learn web development | MDN](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/Vue_refs_focus_management#virtual_dom_and_refs) the use of direct Element access like "document.getElementById()" is discouraged.

# The right way™

instead of using the id of the element to select it from the DOM, vue uses the "ref" attribute in the markup and the this.$refs object to access the virtual DOM elements in the javascript code, which lead me to a solution where the single inputs were mapped to an array of refs i.e.:

```html
<input type="text" ... ref="otp[1]" />
```

and accessing the element in javascript like:

```javascript
this.$refs.otp[1]
```

Using this technique, i could handle the focus through the array index and concat the OTP using Array.join():

```javascript
this.otp.join("");
```

 this seemed to be an easy and clean solution, so i went with this.

# Problems encountered

## Backspace handling

when the user mistypes the otp, they would input in the following sequence: 

> 1235[Backspace]45

the backspace key should go back to the last field, select the value and delete it, leading to 12345, which meant that is needed to implement a special handling of this key (and the uglier code that comes with these sort of implementation details).

## Cursor handling

just like the backspace key, cursor left and cursor right should also navigate the input fields, so here i needed additional handling for these special cases as well.

# Result

![](vue-focus-handling-1.gif)
