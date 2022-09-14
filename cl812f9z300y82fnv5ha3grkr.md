## Lets design a custom context menu

### Introduction
A context menu is a pop-up menu that provides shortcuts for actions the software developer anticipates the user might want to take. User interaction with context menus depends upon the computing device, its operating system (OS) and it input mechanisms. If the user does not have a mouse, for example, he may access context menus by pressing a keyboard combination, pressing and holding a trackball, holding a tap on a touch screen or placing two fingers on a touch pad. Context menus can be closed by selecting an action or clicking outside the menu area in open space.


### Context menu in different OS

#### Windows

![windows context menu](https://cdn.hashnode.com/res/hashnode/image/upload/v1662632240345/4NNN15JCD.png align="left")

### Mac


![mac context menu](https://cdn.hashnode.com/res/hashnode/image/upload/v1662632252030/jBEffM5nA.png align="left")

### Ubuntu

![ubuntu context menu](https://cdn.hashnode.com/res/hashnode/image/upload/v1662632381669/2oCCcSn8Z.png align="left")


### Pen designing

Let's plot an outline of the requirements, 

1. Need an event listener on right click. 
2. On right click, i need to show a div with list of options(button).
3. On clicking outside, context menu should disappear. 
4. By default, the context menu should pop to the right side of the pointer. 
5. But while clicking on the edges we need to reposition it so that its within Viewport Height (VH) and Viewport Width (VW).


### Edgecase: Positioning box when clicked on edges/corners.

On clicking, we will have the co-ordinate of that point (i.e,) pageX and pageY. We can get the width and height of the screen using window object; ```window.innerWidth``` and ```window.innerHeight``` .

We can find whether the screen is oveflowing using the below code, 

```javascript
const widthOverflow = e.pageX  + ctxWidth > window.innerWidth;
const heightOverflow = e.pageY + ctxHeight > window.innerHeight;

```

We will get a boolean values, based on the boolean values we can further place the context menu. 

```javascript
const ctxHeight = contextmenu.offsetHeight;
const ctxWidth = contextmenu.offsetWidth + 5;

const widthOverflow = e.pageX  + ctxWidth > window.innerWidth;
const heightOverflow = e.pageY + ctxHeight > window.innerHeight;

ctxPosition = {
	pageX: widthOverflow ? e.pageX - ctxWidth - 5 : e.pageX,
	pageY: heightOverflow ? e.pageY - ctxHeight : e.pageY
};

```

### Code Base.

#### HTML 

%[https://gist.github.com/syedjafer/2e43d8f5f7ae6b86ecba171d4ba3bbbc#file-context_menu_index-html]

#### CSS

%[https://gist.github.com/syedjafer/8dc79442e68b52e715b90d9da927f1f1#file-context_menu_index-css]

### JS

%[https://gist.github.com/syedjafer/1394689429c72c974daa9b12e3d07872#file-context_menu_index-js]

### Live Tryout

Please right click inside the box.

<iframe src="https://syedjafer.github.io/custom-context-menu/index.html" style="border:1px solid; height: 400px; width: 100%">
</iframe>

- **External Link**: https://syedjafer.github.io/custom-context-menu/index.html
- **Github:** https://github.com/syedjafer/custom-context-menu/

