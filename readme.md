# Arctic Scroll, A Read Me

A simple but more useful internal link scroller with options. Code by [@pauladamdavis](http://twitter.com/pauladamdavis)

---

## Code

	(function ($) {
	    $.fn.arctic_scroll = function (options) {
	
	        var defaults = {
	            elem: $(this),
	            speed: 500,
	            scroll_selector: 'html,body'
	        };
	        
	        var options = $.extend(defaults, options),
	            to_scroll = options.scroll_selector,
	            ua = $.browser;
	        
	        if ( ua.msie && ua.version.slice(0,1) == "8" ) {
	            to_scroll = window;
	        } else if ( ua.msie && ua.version.slice(0,1) == "7" ) {
	            to_scroll = window;
	        }
	
	        options.elem.click(function(event){     
	            event.preventDefault();
	            var offset = ($(this).attr('data-offset')) ? $(this).attr('data-offset') : false,
	                position = ($(this).attr('data-position')) ? $(this).attr('data-position') : false;         
	            if (offset) {
	                var toMove = parseInt(offset);
	                $(options.scroll_selector).stop(true, false).animate({scrollTop: ($(this.hash).offset().top + toMove) }, options.speed);
	            } else if (position) {
	                var toMove = parseInt(position);
	                $(options.scroll_selector).stop(true, false).animate({scrollTop: toMove }, options.speed);
	            } else {
	                $(options.scroll_selector).stop(true, false).animate({scrollTop: ($(this.hash).offset().top) }, options.speed);
	            }
	        });
	
	    };
	})(jQuery);

---

## Initialization

	$(function(){
	    $(".arctic_scroll").arctic_scroll({
	        speed: 800
	    });
	});

---

## Usage

Simply add the class and offset if desired and you're set.

An offset of `-100` means the scroller takes 100 pixels off the amount to be scrolled, leaving a gap.

Using a positive number like `+100` or simply `100` means the page scrolls an extra 100 pixels past the top left of the desired element target with the ID in the href attribute.

If you need to scroll to a set point, just use a `data-position` attribute instead.

	<a href="#example" class="arctic_scroll">Example</a>
	<a href="#moreexample" class="arctic_scroll" data-offset="100">Example</a>
	<a href="#last" class="arctic_scroll" data-position="1234">Example</a>

---

## Working Example

For now, the example is on JSBin ([http://jsbin.com/izocuz](http://jsbin.com/izocuz)) just for convience. When I luanch my new website, a labs section will exist where a proper example will sit.

---

## Sites using Arctic Scroll

* [G'Nosh](http://gnosh.co.uk)

---

## Todo

* Add easing
* Check & test for horizontal scrolling
* Allow constant speed of scrolling, so further elements take longer to get to but doesn't kill performance.