---
layout: layout.njk
title: Updating normalize.css
---

>html {
    line-height: ~~1.15~~ 1.5; [1]
    -webkit-text-size-adjust: 100%;
    }
    
[1] - Correct the line height for a more proper value

>body {
margin: 0;
}

That's opinionated, as every major browser has normalised `margin: 8px` on body, but I'll leave it because of the broad usage of this rule

>~~main {
display: block;
}~~

Rule for IE, deleted

>h1 {
font-size: 2em;
margin: 0.67em 0;
}

That's opinionated, as every major browser behaves the same with nested h1 in `section` and `article`, but it creates confusion, so I'll leave it

>~~hr {~~
~~box-sizing: content-box;~~ [1]
~~height: 0;~~ [1]
~~overflow: visible;~~ [2]
~~}~~

[1] - Firefox has a proper box-sizing ąnd height see: [link to github](https://github.com/necolas/normalize.css/pull/817)
[2] - Rule for IE, deleted

>~~pre {
font-family: monospace, monospace;
font-size: 1em;
}~~

This rule is merged with `code`, `samp` and `kbd` tags, see below.

>~~a {
background-color: transparent;
}~~

Rule for IE, deleted

>abbr[title] {
~~border-bottom: none;~~ [1]
~~text-decoration: underline;
text-decoration: underline dotted;~~
**-webkit-text-decoration: underline dotted** [2]
}

[1] - Rule for old Chrome (57-), deleted
[2] - Only Safari doesn't underline `abbr` tag, fixed it (see [abbr tag browser compatibility](https://developer.mozilla.org/en-US/docs/Web/CSS/text-decoration))

>b,
strong {
font-weight: bolder;
}

No changes.

>**pre,** [1]
code,
kbd,
samp {
font-family: monospace, monospace;
font-size: 1em;
}

[1] - Merged `pre` with other tags with the same rules.

>~~small {
font-size: 80%;
}~~

Every major browser has `font-size: smaller` on `small` tag, no reason to change it

>~~sub,
sup {
font-size: 75%;
line-height: 0;
position: relative;
vertical-align: baseline;}
sub {bottom: -0.25em;}
sup {top: -0.5em;}~~
**sub,
sup {
line-height: 0;
}**

It's opinionated as every browser has the same styling for sub and sup, but these are annoying. I'm yet to find problems with using only `line-height: 0;` for `sup` and `sub` tags.

>~~img {
border-style: none;
}~~

Rule for IE, deleted


>button,
input,
optgroup,
select,
textarea {
  font-family: inherit;
  font-size: 100%;
  line-height: ~~1.15~~ **1.5**; [1] /* why not line-height: inherit insead? */
  /* don't do font: inherit as we don't want to inherit for example font weight */
  margin: 0; /* correct margins on Safari and textarea margin on Firefox*/
}

[1] - Change the line-height to be equal to the line-height of html with `line-height: inherit`.
These styles are not a part of normalisation because these elements have similar styles across major browsers, but because it's broad use of these rules I'll keep them

>~~button,
input {
overflow: visible;
}~~

Rule for IE and old Edge, deleted, see: [link to github](https://github.com/csstools/normalize.css/issues/14)

>~~button,
select {
  text-transform: none;
}~~

Firefox doesn't have inheritance of text transform anymore. see [link to github](https://github.com/necolas/normalize.css/pull/828) and [mozilla docs](https://dxr.mozilla.org/mozilla-central/source/layout/style/res/forms.css#152)

>~~button,~~
[type="button"],
[type="reset"],
[type="submit"] {
  -webkit-appearance: button;
}

Button's default appearance is `button` already, deleted it. If you're curious why is there a rule that sets `-webkit-appearance: button;` see: [link](https://webkit.org/blog/28/buttons/)


>~~button::-moz-focus-inner,
[type="button"]::-moz-focus-inner,
[type="reset"]::-moz-focus-inner,
[type="submit"]::-moz-focus-inner,~~
**::-moz-focus-inner** {
border-style: none;
padding: 0;
}

Updated selector for clarity.

>~~button:-moz-focusring,
[type="button"]:-moz-focusring,
[type="reset"]:-moz-focusring,
[type="submit"]:-moz-focusring,~~
**:-moz-focusring** {
outline: 1px dotted ButtonText;
}

Same as above.

>~~fieldset {
padding: 0.35em 0.75em 0.625em;
}~~

Firefox fixed the inconsistency, rule deleted.

>~~legend {~~
~~box-sizing: border-box;~~ [1]
~~color: inherit;~~ [1]
~~display: table;~~ [1]
~~max-width: 100%;~~ [1]
~~padding: 0;~~ [2]
~~white-space: normal;~~ [1]
~~}~~

[1] - Rules for IE and old Edge, deleted.
[2] - Every major browser has the same padding value of 2px, nothing to normalize here. ***OR IT CAN STAY, RESEARCH FURTHER***

>~~textarea {
overflow: auto;
}~~

Rule of IE, deleted.

>~~[type="checkbox"],
[type="radio"] {
box-sizing: border-box;
padding: 0;
}~~

Rule for IE, deleted.


>[type="number"]::-webkit-inner-spin-button,
[type="number"]::-webkit-outer-spin-button {
  height: auto;
}

No changes, spin button still behaves weird on Safari.



>[type="search"] {
  -webkit-appearance: textfield; [1]
  ~~outline-offset: -2px;~~ [2]
}

[1] - No changes, searchfield still behaves weird on SAFARI, CHROME IS FIXED
[2] - I'm not sure what was the issue with outline on search inputs, but it works properly nowadays. 


>[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}

No changes, but inputs vary significantly anyways


>::-webkit-file-upload-button {
  -webkit-appearance: button; /* 1 */ ***IS IT NEEDED?***
  font: inherit; /* 2 */
}

No changes.


>~~details {
display: block;
}~~

Rule for IE and old Edge, Firefox fixed it, deleted.


>summary {
  display: list-item;
}

No changes.


>~~template {
display: none;
}~~

Rule for IE, deleted.


>~~[hidden] {
display: none;
}~~

Rule for IE, deleted.





## ADDED THESE: 

>::placeholder {
  color: #757575;
  opacity: 1;
  /* FOR SAFARI????? */
  line-height: normal/inherit; /* see: https://github.com/necolas/normalize.css/pull/775  */
}

see: https://github.com/whatwg/html/issues/2561#issuecomment-569920124