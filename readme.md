# Arctic Scroll, A Read Me

A simple but more useful internal link scroller with options. Code by [@pauladamdavis](http://twitter.com/pauladamdavis)

---

## Code

	(function ($) {
	    $.fn.arctic_scroll = function (options) {

	        var defaults = {
	            elem: $(this),
	            speed: 500
	        };
	        var options = $.extend(defaults, options);

	        options.elem.click(function(event){     
	            event.preventDefault();
	            var offset = ($(this).attr('data-offset')) ? $(this).attr('data-offset') : false,
	                position = ($(this).attr('data-position')) ? $(this).attr('data-position') : false;         
	            if (offset) {
	                var toMove = parseInt(offset);
	                $('html,body').stop(true, false).animate({scrollTop: ($(this.hash).offset().top + toMove) }, options.speed);
	            } else if (position) {
	                var toMove = parseInt(position);
	                $('html,body').stop(true, false).animate({scrollTop: toMove }, options.speed);
	            } else {
	                $('html,body').stop(true, false).animate({scrollTop: ($(this.hash).offset().top) }, options.speed);
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

	<a href="#example" class="arctic_scroll">Example</a>
	<a href="#moreexample" class="arctic_scroll" data-offset="100">Example</a>

---

## Todo

* Add easing
* Check & test horizontal scrolling
* Allow constant speed of scrolling, so further element take longer to get to but doesn't kill performance.