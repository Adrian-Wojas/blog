---
layout: layout.njk
title: Updating normalize.css
---


>html {  
&ensp;&ensp;line-height: ~~1.15~~ **1.5**; [1]  
&ensp;&ensp;-webkit-text-size-adjust: 100%;  
}

[1] - Correct the line height for a more proper value

>body {  
&ensp;&ensp;margin: ~~0;~~  
}

That's opinionated, as every major browser has normalised `margin: 8px` on body, but I'll leave it because of the broad usage of this rule

>~~main {  
&ensp;&ensp;display: block;  
}~~  

Rule for IE, deleted

>h1 {  
&ensp;&ensp;font-size: 2em;  
&ensp;&ensp;margin: 0.67em 0;  
}  

That's opinionated, as every major browser behaves the same with nested h1 in `section` and `article`, but it creates confusion, so I'll leave it

>~~hr {~~  
&ensp;&ensp;~~box-sizing: content-box;~~ [1]  
&ensp;&ensp;~~height: 0;~~ [1]  
&ensp;&ensp;~~overflow: visible;~~ [2]  
~~}~~

[1] - Firefox has a proper box-sizing ąnd height see: [link to github](https://github.com/necolas/normalize.css/pull/817)  
[2] - Rule for IE, deleted

>~~pre {  
&ensp;&ensp;font-family: monospace, monospace;  
&ensp;&ensp;font-size: 1em;  
}~~  

This rule is merged with `code`, `samp` and `kbd` tags, see below.

>~~a {  
&ensp;&ensp;background-color: transparent;  
}~~  

Rule for IE, deleted

>abbr[title] {  
&ensp;&ensp;~~border-bottom: none;~~ [1]  
&ensp;&ensp;~~text-decoration: underline;  
&ensp;&ensp;text-decoration: underline dotted;~~  
&ensp;&ensp;**-webkit-text-decoration: underline dotted** [2]  
}

[1] - Rule for old Chrome (57-), deleted  
[2] - Only Safari doesn't underline `abbr` tag, fixed it (see [abbr tag browser compatibility](https://developer.mozilla.org/en-US/docs/Web/CSS/text-decoration))

>b,  
&ensp;&ensp;strong {  
&ensp;&ensp;font-weight: bolder;  
}  

No changes.

>**pre,** [1]  
code,  
kbd,  
samp {  
&ensp;&ensp;font-family: monospace, monospace;  
&ensp;&ensp;font-size: 1em;  
}

[1] - Merged `pre` with other tags with the same rules.

>~~small {  
&ensp;&ensp;font-size: 80%;  
}~~  

Every major browser has `font-size: smaller` on `small` tag, no reason to change it

>~~sub,  
sup {  
&ensp;&ensp;font-size: 75%;  
&ensp;&ensp;line-height: 0;  
&ensp;&ensp;position: relative;  
&ensp;&ensp;vertical-align: baseline;}  
sub {bottom: -0.25em;}  
sup {top: -0.5em;}~~  
**sub,  
sup {  
&ensp;&ensp;line-height: 0;  
}**  

It's opinionated as every browser has the same styling for sub and sup, but these are annoying. I'm yet to find problems with using only `line-height: 0;` for `sup` and `sub` tags.

>~~img {  
&ensp;&ensp;border-style: none;  
}~~  

Rule for IE, deleted


>button,  
input,  
optgroup,  
select,  
textarea {  
&ensp;&ensp;font-family: inherit;  
&ensp;&ensp;font-size: 100%;  
&ensp;&ensp;line-height: ~~1.15~~ **1.5**; [1] /* why not line-height: inherit instead? */
&ensp;&ensp;/* don't do font: inherit as we don't want to inherit for example font weight */  
&ensp;&ensp;margin: 0; /* correct margins on Safari and textarea margin on Firefox*/  
}

[1] - Change the line-height to be equal to the line-height of html with `line-height: inherit`.
These styles are not a part of normalisation because these elements have similar styles across major browsers, but because it's broad use of these rules I'll keep them

>~~button,  
input {  
&ensp;&ensp;overflow: visible;  
}~~  

Rule for IE and old Edge, deleted, see: [link to github](https://github.com/csstools/normalize.css/issues/14)

>~~button,  
select {  
&ensp;&ensp;text-transform: none;  
}~~

Firefox doesn't have inheritance of text transform anymore. see [link to github](https://github.com/necolas/normalize.css/pull/828) and [mozilla docs](https://dxr.mozilla.org/mozilla-central/source/layout/style/res/forms.css#152)

>~~button,~~  
[type="button"],  
[type="reset"],  
[type="submit"] {  
&ensp;&ensp;-webkit-appearance: button;  
}  

Button's default appearance is `button` already, deleted it. If you're curious why is there a rule that sets `-webkit-appearance: button;` see: [link](https://webkit.org/blog/28/buttons/)


>~~button::-moz-focus-inner,  
[type="button"]::-moz-focus-inner,  
[type="reset"]::-moz-focus-inner,  
[type="submit"]::-moz-focus-inner,~~  
**::-moz-focus-inner** {  
&ensp;&ensp;border-style: none;  
&ensp;&ensp;padding: 0;  
}  

Updated selector for clarity.

>~~button:-moz-focusring,  
[type="button"]:-moz-focusring,  
[type="reset"]:-moz-focusring,  
[type="submit"]:-moz-focusring,~~  
**:-moz-focusring** {  
&ensp;&ensp;outline: 1px dotted ButtonText;  
}

Same as above.

>~~fieldset {  
&ensp;&ensp;padding: 0.35em 0.75em 0.625em;  
}~~  

Firefox fixed the inconsistency, rule deleted.

>~~legend {~~  
&ensp;&ensp;~~box-sizing: border-box;~~ [1]  
&ensp;&ensp;~~color: inherit;~~ [1]  
&ensp;&ensp;~~display: table;~~ [1]  
&ensp;&ensp;~~max-width: 100%;~~ [1]  
&ensp;&ensp;~~padding: 0;~~ [2]  
&ensp;&ensp;~~white-space: normal;~~ [1]  
~~}~~

[1] - Rules for IE and old Edge, deleted.  
[2] - Every major browser has the same padding value of 2px, nothing to normalize here. ***OR IT CAN STAY, RESEARCH FURTHER***

>~~textarea {  
&ensp;&ensp;overflow: auto;  
}~~  

Rule of IE, deleted.

>~~[type="checkbox"],  
[type="radio"] {  
&ensp;&ensp;box-sizing: border-box;  
&ensp;&ensp;padding: 0;  
}~~  

Rule for IE, deleted.


>[type="number"]::-webkit-inner-spin-button ,  
[type="number"]::-webkit-outer-spin-button {  
&ensp;&ensp;height: auto;  
}  

No changes, spin button still behaves weird on Safari.


>[type="search"] {  
&ensp;&ensp;-webkit-appearance: textfield; [1]  
&ensp;&ensp;~~outline-offset: -2px;~~ [2]  
}

[1] - No changes, searchfield still behaves weird on SAFARI, CHROME IS FIXED  
[2] - I'm not sure what was the issue with outline on search inputs, but it works properly nowadays. 


>[type="search"]::-webkit-search-decoration {  
&ensp;&ensp;-webkit-appearance: none;  
}  

No changes, but inputs vary significantly anyways


>::-webkit-file-upload-button {  
&ensp;&ensp;-webkit-appearance: button; /* 1 */ ***IS IT NEEDED?***  
&ensp;&ensp;font: inherit; /* 2 */  
}

No changes.


>~~details {  
&ensp;&ensp;display: block;  
}~~  

Rule for IE and old Edge, Firefox fixed it, deleted.


>summary {  
&ensp;&ensp;display: list-item;  
}  

No changes.


>~~template {  
&ensp;&ensp;display: none;  
}~~  

Rule for IE, deleted.


>~~[hidden] {  
&ensp;&ensp;display: none;  
}~~  

Rule for IE, deleted.





### ADDED THESE: 

>::placeholder {  
&ensp;&ensp;color: #757575;  
&ensp;&ensp;opacity: 1;  
&ensp;&ensp;/* FOR SAFARI????? */  
&ensp;&ensp;line-height: normal/inherit; /* see: https://github.com/necolas/normalize.css/pull/775  */  
}

see: [this](https://github.com/whatwg/html/issues/2561#issuecomment-569920124)