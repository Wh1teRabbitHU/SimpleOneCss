# SimpleOneCss
Its a lightweight design framework, used only css3 elements!

## Documentation in progress, please be patient!

For now, you can check the test page for this framework:

[Test page](www.thewhiterabbit.hu/simple_one_css)

## Feature list:

- Buttons
- Inputs
- Tables
- Navtabs
- Navbars
- Lists
- Responsive utils
- Source code format
- Toggle boxes
- Modal window
- Breadcrumbs
- Navigations
- Badges
- Containers
- Alerts
- Progress bars

# Documentation

I try to make every function clear in this part. If something is missing, you can always check the html code and try it in the used way (at the test page). But i try to not left anything out! ;) Oh and sorry for my english... :P

## Buttons

Its a simple one, you should give to the button tag a 'btn' class in general. It format it and give some transition effect.

```
<button type="button" class="btn">I am a default button</button>
```

The next thing is the color palette used for buttons. They named after some functional state. The following colors/states are available:
- warning
- error
- info
- success
- primary

```
<button type="button" class="btn success">I am a success button with a fancy green color</button>
```

If a button is disabled, its color is less vivid and the hover cursor is changing

```
<button type="button" class="btn success" disabled="disabled">I am disabled :(</button>
```

You can easily give some toolbar to the buttons, only needed to fulfill the title attribute:

```
<button type="button" class="btn success" title="This is a toolbox">I have toolbox</button>
```

## Inputs

Inputs gets some visual improvements. Fading placeholder and color schemes, similar to the buttons. The default input looks like this:

```
<input type="text" name="test" class="input" placeholder="Default input" />
```

The placeholder not required, and only need an 'input' class for your input.
The color schemes are the same as the buttons, but get different state names:
- invalid
- valid
- optional
- required
- warning

```
<input type="text" name="test" class="input valid" placeholder="I am a valid input" />
```

Inputs has classes for changing their sizes. 5 different sizes are available, the middle one is the default, it doesnt require a plus class:
- xs-sized
- s-sized
- (without class)
- l-sized
- xl-sized

```
<input type="text" name="test" class="input l-sized" placeholder="I am a big boy now" />
```

If you would like to use labels for the inputs, you should put them into a 'form-container'. Labels has their own classes (in general, every label has a 'label' one), witch are similar to those what inputs has.
You dont need to put the same class to both input and label, if you use in the form-container. Its your call how to use it

```
<div class="form-container invalid">
	<label class="label" for="invalid">For invalid</label>
	<input type="text" id="invalid" name="test" class="input" placeholder="Invalid" />
</div>
```

and

```
<div class="form-container">
	<label class="label invalid" for="invalid">For invalid</label>
	<input type="text" id="invalid" name="test" class="input invalid" placeholder="Invalid" />
</div>
```

are the same.

Also you can make inline form elements too. You only need an extra 'inline' class to your form-container

```
<div class="form-container inline">
	<label class="label" for="default_inline">Inline label</label>
	<input type="text" id="default_inline" name="test" class="input" placeholder="Inline input" />
</div>
```

With the 'input' class, not only text type inputs can be formatted. The following types also supported: (but nothing special)
- number
- password
- date
- file
- input
- checkbox
- radio

## Tables

Tables with 'table' class has a pretty simple design with a few options. The default one is looking like this:

```
<table class="table">
	<thead>
		<tr>
			<th>Alpha</th>
			<th>Beta</th>
			<th>Gamma</th>
			<th>Delta</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>London</td>
			<td>Medium</td>
			<td>2.11</td>
			<td>A</td>
		</tr>
	</tbody>
</table>
```

Using with the 'stripped' class, the table will get some stripped design, witch is very handy for big tables:

```
<table class="table stripped">
	...
</table>
```

The 'hover' class add mouse hover effect to the rows:

```
<table class="table hover">
	...
</table>
```

With the 'bordered' class you get the good old all-over-the-rows-n-columns bordered table:

```
<table class="table bordered">
	...
</table>
```

As the buttons and inputs, table rows have status colors too! Put one of the following class to a row:
- active
- info
- warning
- danger
- success

like this:

```
<tr class="active">
	<td>London</td>
	<td>Medium</td>
	<td>2.11</td>
	<td>A</td>
</tr>
```

Table hover supported also.

## Navtabs

Its a realy tricky element. In css3 there is no clicked state and wont be in the near future, so i needed to do some trick to handle the click event. For this (and for some other elements too) i used the following trick:
Instead of using buttons, i put hidden checkboxes or radio buttons to the elements with a customizable label (I gave the 'btn' class to them, but feel free to use any design element instead of that) So when you click on the label, it trigger the checkbox/radio and changing the :checked status, which is an existing css selector. One thing is important: the controller input and the modifier element has to be siblings! Thats all you need to do, other things are changeable. So, introduting the navtabs here is an example:

```
<ul class="navtab">
	<li>
		<input type="radio" id="tab1" name="navbar1" class="toggle"></input>
		<label for="tab1" class="tab-label">Select A</label>
		<div class="tab-content">CONTENT</div>
	</li>
	<li>
		<input type="radio" id="tab2" name="navbar1" class="toggle"></input>
		<label for="tab2" class="tab-label">Select B</label>
		<div class="tab-content">CONTENT</div>
	</li>
</ul>
```

A few more thing:
- The name parameters has to be the same, otherwise it wont work. (but use uniqe for each element in a single page!)
- Always give id to the hidden input, it will need for the label's 'for' attribute. Otherwise it won't know which input is belonging to that label.
- Its very basic, but also important: checkboxes are multiple selects, radios dont. So when you need toogle, use radio, when you dont mind if multiple selection occured inside an element, use checkboxes (for navtabs, you must choose the radio type!)

Navtabs has 2 more design variant: pills and tabs:

```
<ul class="navtab pills">
	...
</ul>
```

and

```
<ul class="navtab tabs">
	...
</ul>
```

## Navbars

Used for menus. There are several items can be used in navbars:
- Title: Just add some 'title' class to it
- Lists: Add 'menu' to the root ul. Under this list, you can put normal links, toggle submenu and hover menu. The mechanism is prety the same as navtabs for toggle.
- If you use hover, only need is a link with 'hover' class and next to it a 'submenu' list (toggle menu needs a submenu too)
- You can add 'active' class for the currently selected menu item
- If you add 'fixed-top' or 'fixed-bottom', your navbar will be fixed at the page while you scrolling

```
<nav class="navbar">
	<div class="title">Title</div>
	<ul class="menu">
		<li><a href="#">Normal</a></li>
		<li class="active"><a href="#">Active</a></li>
		<li>
			<input type="checkbox" id="dropdown" class="toggle"></input>
			<label class="dropdown" for="dropdown">Toggle submenu</label>
			<ul class="submenu">
				<li><a href="#">A Sublink</a></li>
				<li class="active"><a href="#">B Sublink</a></li>
				<li><a href="#">C Sublink</a></li>
				<li><a href="#">D Sublink</a></li>
				<li><a href="#">E Sublink</a></li>
			</ul>
		</li>
		<li>
			<a href="#" class="hover">Hover submenu</a>
			<ul class="submenu">
				<li><a href="#">A Sublink</a></li>
				<li><a href="#">B Sublink</a></li>
				<li><a href="#">C Sublink</a></li>
				<li class="active"><a href="#">D Sublink</a></li>
				<li><a href="#">E Sublink</a></li>
			</ul>
		</li>
	</ul>
</nav>
```

## Lists

Lists are very simple elements. Add 'list' to the ul element for a basic one.

```
<ul class="list">
	<li>Alpha element</li>
	<li>Beta item</li>
	...
</ul>
```

Bordered lists need 'border' class:

```
<ul class="list border">
	...
</ul>
```

List with an outer box need 'box' class:

```
<ul class="list box">
	...
</ul>
```
Last, but not least if you want some hover effect, put some extra 'hover' class to your list:

```
<ul class="list box hover">
	...
</ul>
```

## Responsive utilities

These classes can be used on nearly all container and on their child elements. All of them has 2 part: The outer class, which has to be added to the container itself. It define the inner elements width:
The formula is simple, if you have for example 'outer-5' class in your container, the elements inside has 100%/5 width multipled by their 'inner-x' class number (x for a number between 1 and 5). Using a more specified example, if you have 'outer-4' the container separated into 4 equal parts and inside it an 'inner-2' element has 100% / 4 (4 'in outer-4') * 2 (2 in 'inner-2') = 50% width. Of course the inner elements class numbers must be equal or less than the outer number. Some example code:

```
<div class="outer-5">
	<div class="inner-2">40%</div>
</div>
<div class="outer-4">
	<div class="inner-1">25%</div>
</div>
<div class="outer-2">
	<div class="inner-1">50%</div><div class="inner-1">50%</div>
</div>
```

There is one extra thing worth to mention it: I used inline-blocks, not float, so if you put some elements (and their summed widths are 100%) inside a container you must put them without line breaks between them, otherwise they wont fit in one line. If this solution is bothering you, you can add float to your elements.

If you want some empty places inside a container, put 'offset-x' to the element after the desired place: (Its the same formula as 'inner-x' has)

```
<div class="outer-5">
	<div class="inner-1 offset-3">60% offset and 20% width</div>
</div>
```

## Source code

If you put some example code in your page, this is the element what you are looking for. Put 'sources' class to a container and every row wrapped with a "span" or "pre" inside it will be formatted as a source code. (the "pre" tag is important if you put html code inside)

The basic code:

```
<div class="sources">
	<span>console.log("Hello World!");</span>
</div>
```

You can add row numbers to lines if you add 'rownumbers' class:

```
<div class="sources rownumbers">
	<span>console.log("Hello World!");</span>
</div>
```

The 'code-container' class add a box style to your source code:

```
<div class="sources code-container">
	<span>console.log("Hello World!");</span>
</div>
```

(Of course, you can use both modifier class in one container)

## Toggle boxes

The mechanism is the same as we used in navtabs or navbars. To catch click event, you cannot use buttons, instead radio inputs will do the job. (Its important to not use checkboxes here, otherwise more than one container will be visible at the same time)
You must put these contents into double container (Outer has 'toggle-box' class, inners has 'wrapper'. Every 'wrapper' has only one content, so each radio selector (:checked) will trigger only one content)


```
<div class="toggle-box">
	<div class="wrapper">
		<input type="radio" id="box-label1" name="box-label" class="toggle" checked></input>
		<label for="box-label1" class="box-label">A</label>
		<div class="box-content">A CONTENT</div>
	</div>
	<div class="wrapper">
		<input type="radio" id="box-label2" name="box-label" class="toggle"></input>
		<label for="box-label2" class="box-label">B</label>
		<div class="box-content">B CONTENT</div>
	</div>
</div>
```

Also you should add an exact height to the 'toggle-box', otherwise the content's overflow may remain hidden. (Or change the overflow attribute)

## Modal window

Its a bit tricky element. It has 3 major parts:
- Open button (has 'opener' class)

```
<input type="radio" name="modal-toggle" id="open-modal" class="toggle opener"/>
<label for="open-modal" class="btn">Open modal</label>
```

- Modal content ( has 'window' class)

```
<div class="window">
	<div class="modal-header"><h3>Modal header</h3></div>
	<div class="modal-body">
		<h4>Modal body</h4>
		<p>CONTENT</p>
	</div>
	<div class="modal-footer">
		<input type="radio" name="modal-toggle" id="close-modal-1" class="toggle">
		<label for="close-modal-1" class="btn s-sized close-modal">Close modal</label>
	</div>
</div>
```

- And a background layer (has 'shadow' class)

```
<input type="radio" name="modal-toggle" id="close-modal-2" class="toggle" />
<label for="close-modal-2" class="shadow"></label>
```

All inputs need the same name, but with separate targets. Inside the modal body you can put an extra close button, but clicking at the background layer is just fine to close the modal. The modal 'window' should have 3 container :
- 'modal-header'
- 'modal-body'
- 'modal-footer'

but you can skip any of it.
One example for a working modal:

```
<div class="modal">
	<input type="radio" name="modal-toggle" id="open-modal" class="toggle opener" />
	<label for="open-modal" class="btn">Open modal</label>
	<div class="window">
		<div class="modal-header"><h3>Modal header</h3></div>
		<div class="modal-body">
			<h4>Modal body</h4>
			<p>CONTENT</p>
		</div>
		<div class="modal-footer">
			<input type="radio" name="modal-toggle" id="close-modal-1" class="toggle">
			<label for="close-modal-1" class="btn s-sized close-modal">Close modal</label>
		</div>
	</div>
	<input type="radio" name="modal-toggle" id="close-modal-2" class="toggle">
	<label for="close-modal-2" class="shadow"></label>
</div>
```

## Breadcrumb

Used for showing page hiearchy, like route to a subpage (a/b/c) The syntax is simple, add 'breadcrumb' to a list. To mark the active element, use 'active' class:

```
<ul class="breadcrumb">
	<li class="active">Active</li>
	<li><a href="#">Default separator</a></li>
	<li><a href="#">Default separator</a></li>
	<li><a href="#">Default separator</a></li>
</ul>
```

You can also choose between a few more separator types: (add next to the 'breadcrumb class')
- 'dots'
- 'lines'
- 'pipes'

```
<ul class="breadcrumb pipes">
	...
</ul>
```

If you need, you should add 'border' class for some fancy border to your breadcrumb:

```
<ul class="breadcrumb border">
	...
</ul>
```

## Navigation

Its a common pagination element, helps the visitors to navigate throught a list. Add 'pagination' class to your nav tag and 'active' to the current page number:

```
<nav class="pagination">
	<ul>
		<li><a href="#"><<</a></li>
		<li><a href="#"><</a></li>
		<li><a href="#">1</a></li>
		<li><a href="#">2</a></li>
		<li><a href="#">3</a></li>
		<li class="disabled"><a href="#">...</a></li>
		<li><a href="#">10</a></li>
		<li class="active"><a href="#">11</a></li>
		<li><a href="#">12</a></li>
		<li class="disabled"><a href="#">...</a></li>
		<li><a href="#">42</a></li>
		<li><a href="#">43</a></li>
		<li><a href="#">44</a></li>
		<li><a href="#">></a></li>
		<li><a href="#">>></a></li>
	</ul>
</nav>
```

If you dont like rectangles, use the 'rounded' class:

```
<nav class="pagination">
	<ul>
		...
	</ul>
</nav>
```

## Badges

Prety simple elements, with many color themes. An example for the default one:

```
<span class="badge">Default badge</span>
```

Available color themes:
- 'primary'
- 'info'
- 'warning'
- 'error'
- 'success'

```
<span class="badge success">Default badge</span>
```

## Containers

I made some basic container classes. To make one, you just add a 'container' class to your tag:

```
<div class="container">
	<h3>Normal sized container</h3>
	<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
</div>
```

Gives some margin, background color and different font size (based on the default size). If the default container is too big or small, you can add size classes to your container, too. Available size classes:
- 'xs-sized'
- 's-sized'
- (default, no need for extra class)
- 'l-sized'
- 'xl-sized'

```
<div class="container xs-sized">
	...
</div>
```

## Alerts

Add some animated boxes, with different visual design, based on the class you are using:

```
<div class="alert">
	Default alert!
</div>
```

And the list of the colors: ( Same as we using at buttons or badges for example )
- 'primary'
- 'info'
- 'warning'
- 'error'
- 'success'

```
<div class="alert info">
	...
</div>
```

## Progress bar

Progress bars used for indicate status. If you want to dinamicaly change the indicator size, you need to change the width's of the inner div (the one with 'bar' class) I recommend to use percentage instead of exact amount when you change the width value via javascript.
The default progress bar looks like this: (you should remove the style attribute when you animate the bar!)

```
<div class="progress">
	<div class="bar" style="width: 20%"><span class="indicator">20%</span></div>
</div>
```

All progress bar has 6 different color theme (familiar with the other themed elements listed above):
- 'primary'
- 'info'
- 'warning'
- 'error'
- 'success'

```
<div class="progress">
	<div class="bar primary" style="width: 20%"><span class="indicator">20%</span></div>
</div>
```

If you prefer stripped bars, you should add 'stripped' class:

```
<div class="progress">
	<div class="bar stripped" style="width: 20%"><span class="indicator">20%</span></div>
</div>
```

After you created some stripped bars, the next step should be to animate them. Just add 'animated' right after your classes:

```
<div class="progress">
	<div class="bar stripped animated" style="width: 20%"><span class="indicator">20%</span></div>
</div>
```

And the best of all, you can add more than one bar to a progress container. Beware: add them without space or line break between them, or when you reach 100%, the last bar will be in the next line. Or just float the bars, its up to you, how you handle this problem! A mixed example:

```
<div class="progress">
	<div class="bar primary" style="width: 40%">
		<span class="indicator">40%</span></div><div class="bar" style="width: 20%">
		<span class="indicator">20%</span></div><div class="bar info" style="width: 40%">
		<span class="indicator">40%</span></div>
</div>
```