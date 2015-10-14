# Arctic Scroll, A Read Me

An MIT licensed simple but useful internal link scroller with options

**[Demo](http://pauladamdavis.github.io/Arctic-Scroll/)**

---

## Initialization

```javascript
$(function(){
    $(".arctic_scroll").arctic_scroll({
        speed: 800
    });
});
```
---

## Usage

Simply add the class (with offset, if desired) and you're set.

A negative offset of `-100` means the page scrolls to a position 100px above the target.

Using a positive number like `+100` or simply `100` means the page scrolls an extra 100 pixels past the top of the target.

If you need to scroll to a set point, just use a `data-position` attribute instead.

```html
<a href="#example" class="arctic_scroll">Example</a>
<a href="#moreexample" class="arctic_scroll" data-offset="100">Example</a>
<a href="#last" class="arctic_scroll" data-position="1234">Example</a>
```