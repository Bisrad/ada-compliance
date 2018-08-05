# Screen Reader Compatibility 

###### Requirements

* [Document Language](#document-language)
* [Document Title](#document-title)
* [Content Navigation](#content-navigation)
* [Landmarks](#landmarks)
* ['Skip Navigation' Links](#skip-navigation-links)
* [Dynamic Content](#dynamic-content)
* [Keyboard Accessibility](#keyboard-accessibility)
* [UI Control Accessibility](#ui-control-accessibility)
* [Links & Buttons](#links--buttons)
* [Validation](#validation)

## Document Language

Specify document language with a lang attribute on the `<html>` tag.

 ```html
 <html lang=“en”>
 ```

## Document Title

Specify a document title with the `<title>` element.

```html
<title>Document Title</title>
```

## Content Navigation

* Links should make sense out of context.

* Content should be organised with headings, which should represent an accurate outline of the content.

* When possible, place the distinguishing information of a paragraph in the first sentence.

* Where appropriate, allow users to skip over repetitive navigation links.

* Define appropriate landmarks.

* Use proper HTML [semantic structure](https://webaim.org/techniques/semanticstructure/) with elements marked up appropriately.

## Landmarks

Landmarks provide a way to identify the organization and structure of a web page. The structural information conveyed visually to users should be represented programmatically in the markup using landmark roles. The use of landmarks roles support keyboard navigation to the structure of a web page for screen reader users, and can be used as targets for author supplied "[skip navigation](#skip-navigation-links)" links and browser extensions for enhanced keyboard navigation.

** NOTE: The 'article' role is mentioned on [webaim.org](https://webaim.org/techniques/aria/#landmarks) as being a landmark but according to [W3C Specfications](https://www.w3.org/TR/wai-aria/roles#article) it _*IS NOT*_ a landmark. Need to keep an eye on this as current standards seem to be in flux.

###### Landmarks

* [banner](#--banner)
* [navigation](#--navigation)
* [main](#--main)
* [search](#--search)
* [complementary](#--complementary)
* [contentinfo](#--contentinfo)
* [region](#--region)
* [form](#--form)

#### - banner

A banner landmark identifies site-oriented content at the beginning of each page within a website. Site-oriented content typically includes things such as the logo or identity of the site sponsor, and site-specific search tool. A banner usually appears at the top of the page and typically spans the full width.

###### ARIA

```html
<div role=“banner”>
```

###### HTML5

The HTML5 `<header>` element defines a banner landmark when its context is the body element.

The HTML5 `<header>` element is not considered a banner landmark when it is descendant of any of following elements:

* article
* aside
* main
* nav
* section

[W3C Specification](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/banner.html)

---

#### - navigation

Navigation landmarks provide a way to identify groups (e.g. lists) of links that are intended to be used for website or page content navigation.

###### ARIA

```html
<div role=“navigation”>
```

###### HTML5

One `<nav>` landmark on the page:

```html
<nav>
```

When there is more than one navigation landmark on a page, each should have a unique label:

```html
<nav aria-labelledby=“nav1”>
	<h2 id=“nav1”> ...

<nav aria-labelledby=“nav2”>
	<h2 id=“nav2”> ...
```

[W3C Specification](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/navigation.html)

---

#### - main

A main landmark identifies the primary content of the page.

###### ARIA

```html
<div role=“main”>
```

###### HTML5

One `<main>` landmark on the page:

```html
<main>
```

When there is more than one main landmark on a page, each should have a unique label:

```html
<main aria-labelledby=“title1”>
	<h1 id=“title1”> ...

<main aria-labelledby=“title2”>
	<h1 id=“title2> ...
```

[W3C Specification](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/main.html)

---

#### - search 

A search landmark contains a collection of items and objects that, as a whole, combine to create search functionality to content on the website.

###### ARIA

```html
<form role=“search”>
```

###### HTML5

There is no HTML5 element that defines a search landmark.

[W3C Specification](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/search.html)

---

#### - complementary
		
A complementary landmark is a supporting section of the document, designed to be complementary to the main content at a similar level in the DOM hierarchy, but remains meaningful when separated from the main content.

###### ARIA

```html
<div role=“complimentary>
```

###### HTML5

Use the HTML5 `<aside>` element to define a complementary landmark.

When there is more than one complementary landmark on a page, each should have a unique label:

```html
<aside aria-labelledby=“comp1”>
	<h2 id=“comp1”> ...

<aside aria-labelledby=“comp1”>
	<h2 id=“comp2”> ...
```

[W3C Specification](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/complementary.html)

---

#### - contentinfo

A contentinfo landmark is a way to identify common information at the bottom of each page within a website, typically called the "footer" of the page, including information such as copyrights and links to privacy and accessibility statements.

###### ARIA

```html
<div role=“contentinfo”>
```

###### HTML5

The HTML5 footer element defines a contentinfo landmark when its context is the body element.

The HTML5 footer element is not considered a contentinfo landmark when it is descendant of any of following elements:

* article 
* aside
* main
* nav
* section

```html
<footer>
	…
```

[W3C Specification](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/contentinfo.html)

---

#### - region
	
A region landmark is a perceivable section containing content that is relevant to a specific, author-specified purpose and sufficiently important that users will likely want to be able to navigate to the section easily and to have it listed in a summary of the page.

###### ARIA

```html
<div role=“region” aria-labelledby=“region1”>
	<h2 id=“region1”>Title for Region Area 1</h2> ...
```

###### HTML5

Use the HTML5 `<section>` element to define a region landmark.

Using existing content on the page:

```html
<section aria-labelledby=“region1”>
	<h2 id=“region1”>Title for Region Area 1</h2> ...

<section aria-labelledby=“region2”>
	<h2 id=“region2”>Title for Region Area 2</h2> ...
```

Using attribute value that is only visible to assistive technologies:

```html
<section aria-label=“Title for Region Area 1”>
	<h2 id=“region1”>Title for Region Area 1</h2> ...

<section aria-label=“Title for Region Area 2”>
	<h2 id=“region2”>Title for Region Area 2</h2> ...
```

[W3C Specification](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/region.html)

---

#### - form

A form landmark identifies a region that contains a collection of items and objects that, as a whole, combine to create a form when no other named landmark is appropriate (e.g. main or search).

###### ARIA

```html
<div role=“form” aria-labelledby=“contact”>
	<h2 id=“contact”>Add Contact</h2> ...

<div role=“form” aria-labelledby=“organization”>
	<h2 id=“organization”>Add Organization</h2> ...
```

###### HTML5

If a form element has an accessible name it is considered form landmark.

```html
<form aria-labelledby=“contact”>
	<h2 id=“contact”>Add Contact</h2> ...

<form aria-labelledby=“organization”>
	<h2 id=“organization”>Add Organization</h2> ...
```

[W3C Specification](https://www.w3.org/TR/wai-aria-practices/examples/landmarks/form.html)

---

## 'Skip Navigation' Links

An innvisible link can provide a link at the top of the page which jumps the user down to an anchor or target at the beginning of the main content. The link should be hidden visually by default, but it should become visible when it receives keyboard focus.

###### HTML

```html
<!-- Anchor -->
<div class="skip-navigation anchor">
      <a href="#skipNavigationTarget">Skip to Main Content</a>
 </div>

<!-- Target -->
<div id="skipNavigationTarget" class="skip-navigation target"></div>
```

###### SCSS

```scss
.skip-navigation {

	&.anchor {
		left: 0;
		position: absolute;
		top: 0;
		width: 100%;
		text-align: center;
		
		a {
			font-weight: bold;
			height: 1px; 
			left: -10000px; 
			overflow: hidden;
			position:absolute; 
			top: auto; 
			width: 1px; 

			&:focus {
				height:auto; 
				position:static; 
				width:auto; 
			}
		}	
	}

	&.target {
		height: 0;
	}
}
```

## Dynamic Content

[WAI-ARIA](https://www.w3.org/WAI/intro/aria) can be used to identify regions that dynamically change as a live region. A live region allows content updates in a way that a screen reader understands. It also allows you to add additional functionality to alert the user, provide controls for the live region, determine the amount of new content that would be read, and much more.

To create a live region, add the [aria-live](https://www.w3.org/TR/wai-aria-1.1/#aria-live) property to the element with a value of `off`, `polite`, or `assertive`. The value, or politeness level (or alternatively the intrusiveness level), specifies what a screen reader should do when the element is updated.

** NOTE: 'rude' is mentioned on [webaim.org](https://webaim.org/techniques/aria/#dynamic) as an aria-live property but according to the Accessible Rich Internet Applications Working Group's [changelog](https://www.w3.org/WAI/ARIA/track/actions/331) it has been _*removed*_ from the specification.

#### - off

A value of off tells the screen reader to not announce the update. If/when the screen reader user encounters the updated content, it will be read at that time. This would be used for non-important or irrelevant content updates.

###### HTML

```html
<div aria-live="off"> ...
```
---

#### - polite

A value of polite will notify the user of the content change as soon as he/she is done with the current task. This might take the form of a beep or an audio indication of the update. The user can then choose to directly jump to the updated content. This value would be the most common for content updates, especially for things like status notification, weather or stock updates, chat messages, etc.

###### HTML

```html
<div aria-live="polite"> ...
```
---

#### - assertive

A value of assertive will result in the user being alerted to the content change immediately or as soon as possible. Assertive would be used for important updates, such as error messages

###### HTML

```html
<div aria-live="assertive"> ...
```
---

## Keyboard Accessibility

In HTML, only links and form elements can receive keyboard focus. This means that as you 'tab' through a page, the browser stops or sets focus only on these types of elements. ARIA provides mechanisms for non-focusable elements to receive focus through the [tabindex](https://www.w3.org/TR/html5/editing.html#attr-tabindex) property. 

In theory, tabindex should only be used in cases where:

* The default tab order is not ideal, AND
* The tab order cannot be changed by rearranging items in the content and/or by altering the style sheet to reflect the best visual arrangement.

#### - tabindex="1"

A tabindex value of 1, or any number greater than 1, defines an explicit tab order. This is almost always a bad idea.

An element with any tabindex value of 1+ will receive keyboard focus before elements with no tabindex value (or tabindex="0"). This is unexpected behavior and can be especially confusing to screen reader user who are presented with one order when reading a page and with a different order when navigating with the `Tab` key. Because of this, the use of positive tabindex values is _*not recommended*_. Instead, fix the navigation order by restructuring the HTML.

###### HTML

```html
<div tabindex="1"> ...
```
---

#### - tabindex="0"

A tabindex value of 0 allows elements besides links and form elements to receive keyboard focus. It does not change the tab order, but places the element in the logical navigation flow, as if it were a link on the page. This allows elements that are not natively focusable (such as `<div>`, `<span>`, `<p>`, and `<a>` with no `href`) to receive keyboard focus. Links and form controls are best for almost all interactive elements, but tabindex="0" allows other elements to be focusable and able to trigger interaction.

If tabindex="0" is used to make elements focusable, the keyboard interaction must be correct for that element, as defined above. This means that elements that are presented as buttons, for example, must respond to both `Enter` and `Spacebar` key presses. In some browsers this may require keypress detection with scripting. ARIA `role="link"`, `role="button"`, aria-`expanded="true"`, etc. must often be used to inform screen reader users of the function of the navigable element.

###### HTML

```html
<div tabindex="0"> ...
```
---

#### - tabindex="-1"

A tabindex value of -1 allows things besides links and form elements to receive "programmatic" focus, meaning focus can be set to the element through scripting, links, etc.

A tabindex value of -1 allows things besides links and form elements to receive "programmatic" focus (focus can be set to it from a link, or with scripting) and removes the element from the default navigation flow. This may be useful for elements that should not be navigated to, but need to have focus set to them. A good example is a modal dialog window: when opened, focus should be set to the dialog so a screen reader will begin reading and the keyboard will be able to navigate within the dialog. Because the dialog (probably a `<div>` element) is not focusable by default, assigning it `tabindex="-1"` allows scripting to set focus to it when it is presented.
	
A value of -1 may also be useful in complex widgets and menus that utilize arrow keys, or other shortcut keys. This ensures that only one element within the widget is navigable with the Tab key, while still allowing focus to be set on other components within the widget.

Remember that `tabindex="-1"` removes the element from the default navigation flow. Do not assign `tabindex="-1"` to any element that must be keyboard navigable, such as a link or button that sighted users can click on with the mouse.

###### HTML

```html
<div tabindex="-1"> ...
```
---

## UI Control Accessibility

'UI control' is broad definition used to describe interactive elements that are created and controlled through scripting. It refers to controls that are not native to HTML or to HTML controls that are greatly enhanced with JavaScript. Examples of widgets would include sliders, drop-down and fly-out menus, tree systems, drag and drop controls, auto-completing text boxes, and tooltip windows, etc. Accessibility of UI controls does not happen natively or naturally and HTML has very limited markup for defining complex widgets. 

[ARIA](https://www.w3.org/WAI/PF/aria-practices/#aria_ex)'s set of roles, properties, and values addresses these accessibility issues.

#### - Form Validation

ARIA's aria-required="true" will inform a screen reader that the specified form element is required.

###### HTML

```html
<input name="name" id="name" aria-required="true">
```
---

#### - Non-Native UI Control

The following is a text element (not an actual HTML button) that can be clicked or activated with the keyboard (`Enter` or `Space`).

```html
<span role="button" tabindex="0" onkeydown="if(event.keyCode==13 || event.keyCode==32) alert('You activated me with the keyboard');" onclick="alert('You clicked me with the mouse');">Push Me</span>
```

In this example, the text is styled to visually appear like a button. The `role="button"` tells the browser that the text should behave as a button. `tabindex="0"` puts the element into the keyboard navigation flow so keyboard users can activate the button. The onkeydown event handler detects whether the user has pressed `Enter` or the `Space` while focused on the element. While this example is a bit contrived (why not just use an actual button?), it demonstrates the ability for ARIA to add semantics and accessible interactivity to any element.

---

## Links & Buttons

Links and buttons should contain text but in cases where they don't an `aria-label` attribute can be used to define a screen-readable string to label the link/button.

[W3C Specification](https://www.w3.org/TR/WCAG20-TECHS/ARIA14.html)

###### Link HTML

```html
<a href="#" arial-label="Read More">
	<img src="../image.jpg">
</a>
```
---

###### Button HTML

```html
<button aria-label="Close">x</button>
```
---

## Validation

The [aXe Accessibility Engine](https://www.axe-core.org/) can be used for validation.

## Resources

* [WebAIM - Designing for Screen Reader Compatibility](https://webaim.org/techniques/screenreader/)
* [WebAIM - Landmarks](https://webaim.org/techniques/aria/#landmarks)
* [W3C - article (role) specification](https://www.w3.org/TR/wai-aria/roles#article)
* [W3C - WAI-ARIA Overview ](https://www.w3.org/WAI/intro/aria)
* [W3C - WAI-ARIA Authoring Practices 1.1](https://www.w3.org/TR/wai-aria-practices/)
* [Foundation 6 Accessibility](https://foundation.zurb.com/sites/docs/accessibility.html)