# VueHambMenu
A simple Vue.js sliding hamburger menu component

The component relies on the material design icon font, which can be included in the top of your index.html like this:

`<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">`

After including the component, use it in the template like any other vue.js component:

`<VueHambMenu />`

## Props

### iconColor

An optional prop, through which a custom hamburger icon color can be specified.

### linkColor

Custom color for the links in the slideout menu.

### menuColor

Custom background color for the slideout menu.

### position

The default value is 'right', meaning the menu will appear fixed on the upper right side. This can be changed to 'left', in which case the menu also slides out from the left.

### darken

A simple boolean prop, which if added, darkens the rest of the page when the menu slides out.

### horizontal

An optional prop that takes a Number, and defines horizontal positioning in pixels (distance from top of page).

### vertical

An optional prop that takes a Number, and defines vertical positioning in pixels (distance from edge of page).

### links

A prop that takes the links to be displayed as an array of objects, that each have a 'text' and a 'href' property. Example:

`<VueHambMenu :links="[{text: 'link1', href: '/link1.html'}, {text: 'link2', href: '/link2.html'}]" />`

### linkSize

A Number prop that defines custom link size in pixels.

### linkSpacing

An optional prop that takes a Number, and defines the spacing between links in pixels.

