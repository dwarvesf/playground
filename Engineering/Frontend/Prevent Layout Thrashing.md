---
tags: engineering/frontend,web-performance
author: Le Minh Thanh
date: 2022-09-11
---
### What is Layout thrashing
![[layout-thrashing.png]]

Layout thrashing means Forcing the browser to calculate a layout that is never rendered to the screen, and it hurt your performance so bad

### Why
Layout Thrashing happens, when you request layout information of an element or the document, while layout is in an **invalidated state**.

```js
// any DOM or CSSOM change flags the layout as invalid
document.body.classList.add('foo');

// reads layout == forces layout calculation
const box = element.getBoundingClientRect();

// write/mutate
document.body.appendChild(someBox);

//read/measure
const color = getComputedStyle(someOtherBox).color;
```

Mixing Layout Read & Layout Mutation needs to wait for browser to recalculate layout & reflow to return you Layout value

![[dont-touch-me.png]]

### How to fix
SEPARATE YOUR READS FROM YOUR WRITES AND THE PROBLEM IS SOLVED

- Batch Read Layout first
- Then Mutate Layout later

```js
// reads layout
const box = element.getBoundingClientRect();
const color = getComputedStyle(someOtherBox).color;

// write
document.body.classList.add('foo');
document.body.appendChild(someBox);
```

or use library
```js
import fastdom from 'fastdom';

function resizeAllParagraphsToMatchBoxWidth(paragraphs, box) {

    fastdom.measure(() => {
        const width = box.offsetWidth;

        fastdom.mutate(() => {
            for (let i = 0; i < paragraphs.length; i++) {
                paragraphs[i].style.width = width + 'px';
            }
        });
    });
}
```

### How to debug
Open `Performance Tab` on Dev tool, slow down your CPU and click `Start Profiling`
![[layout-thrashing-debug.png]]

Look for puple task and get info in detail
<video src="https://afarkas.github.io/layout-thrashing/material/layout-thrashing-debug.mp4" controls></video>


### List of commands cause Layout Thrashing we need to be careful when using it

Generally, all APIs that synchronously provide layout metrics will trigger forced reflow / layout. Read on for additional cases and details.

https://gist.github.com/paulirish/5d52fb081b3570c81e3a


#### Reference

- https://gist.github.com/paulirish/5d52fb081b3570c81e3a
- https://afarkas.github.io/layout-thrashing/#/
