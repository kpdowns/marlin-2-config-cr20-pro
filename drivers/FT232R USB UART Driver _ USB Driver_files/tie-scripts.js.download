jQuery(document).ready(function() {
	$window 		  = jQuery(window),
	$the_post		  = jQuery('#the-post'),
	$wrapper 		  = jQuery("#wrapper");

if( tie.SmothScroll ){
	tie_SmothScroll();
}

//Responsive Videos
	$wrapper.fitVids();

//LightBox
	jQuery( "a.lightbox-enabled, a[rel='lightbox-enabled']" ).iLightBox({ skin: tie.lightbox_skin});

	if( tie.lightbox_all ){
	 	$the_post.find("div.entry a").not( "div.entry .gallery a, div.entry .flat-social a" ).each(function(i, el) {
			var href_value = el.href;
			if (/\.(jpg|jpeg|png|gif)$/.test(href_value)) {
				jQuery(this).iLightBox({ skin: tie.lightbox_skin});
			}
		});
	};

	if( tie.lightbox_gallery ){
		$the_post.find("div.entry .gallery a").each(function(i, el) {
			var href_value = el.href;
			if (/\.(jpg|jpeg|png|gif)$/.test(href_value)) {
				jQuery(this).addClass( 'ilightbox-gallery' );
			}
		});
		$the_post.find( '.ilightbox-gallery' ).iLightBox({
			skin: tie.lightbox_skin,
			path: tie.lightbox_thumb,
			controls: {
				arrows: tie.lightbox_arrows,
			}
		});
	};

	jQuery( 'section.videos-lightbox a.single-videolighbox, .lightbox-img' ).iLightBox({
		skin: tie.lightbox_skin,
		path: tie.lightbox_thumb,
		controls: {
			arrows: tie.lightbox_arrows,
		}
	});

	jQuery( ".woocommerce-product-gallery__trigger" ).iLightBox({
		skin: tie.lightbox_skin,
		path: tie.lightbox_thumb,
		controls: {
			arrows: tie.lightbox_arrows,
		}
	});

//Slide-out Sidebar
	jQuery("#slide-out-open").click(function() {
		if( jQuery( this ).hasClass( "slide-out-open" ) ) {
			$wrapper.css({overflow:"hidden"});
			jQuery("body").addClass( 'js-nav' );
			jQuery( this ).removeClass('slide-out-open').addClass('slide-out-close');
			return false;
		}
		else if( jQuery( this ).hasClass( "slide-out-close" ) ) {
			$wrapper.css({overflow:"auto"});
			jQuery("body").removeClass( 'js-nav' );
			jQuery( this ).removeClass('slide-out-close').addClass('slide-out-open');
			return false;
		}
	});

	if ( !Modernizr.csstransforms || !Modernizr.csstransitions || !Modernizr.csstransforms3d) {
		var TieSlideOpenIE = false ;
		jQuery('#slide-out').hide();
		jQuery("#slide-out-open").click(function() {
			jQuery('#mobile-menu').show();
			jQuery('#slide-out').show();
			jQuery(this).hide();
			jQuery('div.wrapper-outer').css({overflow:"hidden"});
			jQuery('#open-slide-overlay').remove();
			jQuery('body').append('<div id="open-slide-overlay"></div>');
			TieSlideOpenIE = true ;
		});

		jQuery(document).on("click", "#open-slide-overlay" , function(){
			if( TieSlideOpenIE ){
				jQuery('#slide-out').hide();
				jQuery('#mobile-menu').hide();
				jQuery('#slide-out-open').show();
				jQuery('div.wrapper-outer').css({overflow:"auto"});
				jQuery(this).remove();
				TieSlideOpenIE = false ;
			}
		});
	}

//Mobile Menus
	if( tie.mobile_menu_active ){
		var mobileItems = jQuery( '#main-nav div.main-menu' ).clone();
		mobileItems.find( 'div.mega-menu-content' ).remove();
		mobileItems.find( 'li.menu-item-has-children' ).append( '<i class="mobile-arrows fa fa-chevron-down"></i>' );
		jQuery( '#slide-out #mobile-menu' ).append( mobileItems );

		if( tie.mobile_menu_top ){
			var mobileItemsTop = jQuery( '#top-nav div.top-menu ul.menu' ).clone();
			mobileItemsTop.find( 'li.menu-item-has-children' ).append( '<i class="mobile-arrows fa fa-chevron-down"></i>' );
			jQuery( '#slide-out #mobile-menu' ).append( mobileItemsTop );
		}
	}

	jQuery("#mobile-menu li.menu-item-has-children i.mobile-arrows").click(function() {
		if( jQuery( this ).hasClass( "fa-chevron-down" ) )
			jQuery( this ).removeClass( "fa-chevron-down" ).addClass( "fa-chevron-up" );
		else
			jQuery( this ).removeClass( "fa-chevron-up" ).addClass( "fa-chevron-down" );

		jQuery( this ).parent().find('ul:first').toggle();
	});

//Scroll To top
	var $topcontrol = jQuery('#topcontrol');
	$window.scroll(function(){
		if (jQuery(this).scrollTop() > 100) {
			$topcontrol.css({bottom:"10px"});
		} else {
			$topcontrol.css({bottom:"-100px"});
		}
	});
	$topcontrol.click(function(){
		jQuery('html, body').animate({scrollTop: '0px'}, 800);
		return false;
	});

//Go to Post Content
	jQuery('a.go-to-the-post').click(function(){
		jQuery('html, body').animate({scrollTop: $the_post.offset().top}, 500);
		return false;
	});

//tooltip();
    jQuery('.tooltip-nw').tipsy({fade: true, gravity: 'nw'});
    jQuery('.tooltip-ne').tipsy({fade: true, gravity: 'ne'});
    jQuery('.tooltip-w' ).tipsy({fade: true, gravity: 'w' });
    jQuery('.tooltip-e' ).tipsy({fade: true, gravity: 'e' });
    jQuery('.tooltip-sw').tipsy({fade: true, gravity: 'w' });
    jQuery('.tooltip-se').tipsy({fade: true, gravity: 'e' });
    jQuery('.ttip, .tooltip-n'	  ).tipsy({fade: true, gravity: 's'});
    jQuery('.tooldown, .tooltip-s').tipsy({fade: true, gravity: 'n'});

// Toggle Shortcode
	jQuery("h3.toggle-head-open").click(function () {
		jQuery(this).parent().find("div.toggle-content").slideToggle("slow");
		jQuery(this).hide();
		jQuery(this).parent().find("h3.toggle-head-close").show();
    });
	jQuery("h3.toggle-head-close").click(function () {
		jQuery(this).parent().find("div.toggle-content").slideToggle("slow");
		jQuery(this).hide();
		jQuery(this).parent().find("h3.toggle-head-open").show();
    });

//Mega-Menus
	jQuery( "#main-nav li.mega-menu:not(#main-nav li li)" ).hover(function(){
		var menuWidth 			= jQuery( '#main-nav div.container' ).width();
		var menuPosition 		= jQuery( '#main-nav div.container' ).offset();
		var menuItemPosition 	= jQuery(this).offset();
		var PositionLeft 		= menuItemPosition.left-menuPosition.left+1;
		jQuery(this).find('div.mega-menu-block').css({ left: '-'+PositionLeft+'px', width: menuWidth });
	});

//Mega Menus Tabs
	jQuery("div.mega-cat-wrapper").each(function(){
		jQuery( this ).find("div.mega-cat-content-tab").hide();
		jQuery( this ).find("ul.mega-cat-sub-categories li:first").addClass("cat-active").show();
		jQuery( this ).find("div.mega-cat-content-tab:first").addClass("already-loaded").show();
		jQuery( this ).find("ul.mega-cat-sub-categories li").click(function( event ) {
			event.preventDefault();
			jQuery( this ).parent().find("li").removeClass("cat-active");
			jQuery( this ).addClass("cat-active");
			jQuery( this ).parent().parent().parent().find("div.mega-cat-content-tab").hide();
			var activeTab = jQuery(this).find("a").attr("href");

			if( jQuery(activeTab).hasClass( "already-loaded" ) ){
				jQuery(activeTab).fadeIn();
			}else{
				jQuery(activeTab).addClass("loading-items").fadeIn( 600 , function() {
					jQuery( this ).removeClass("loading-items").addClass("already-loaded");
				});
			}
			return false;
		});
	});

//iPad menu hover bug with Safari
	var userAgent = navigator.userAgent;
	if ( userAgent.match(/iPad/i) ) {
		if ( userAgent.search("Safari") >= 0 && userAgent.search("Chrome") < 0 ) {
			jQuery('#main-nav li.menu-item-has-children a, #main-nav li.mega-menu a, #top-nav li.menu-item-has-children a').attr("onclick","return true");
		}
	}

//tabbed Boxes
 	jQuery("div.cat-box-content").each(function(){
		jQuery( this ).find("div.cat-tabs-wrap").hide();
		jQuery( this ).find("div.cat-tabs-header ul li:first").addClass("active").show();
		jQuery( this ).find("div.cat-tabs-wrap:first").show();
		jQuery( this ).find("div.cat-tabs-header ul li").click(function( event ) {
			event.preventDefault();
			jQuery( this ).parent().find("li").removeClass("active");
			jQuery( this ).addClass("active");
			jQuery( this ).parent().parent().parent().find("div.cat-tabs-wrap").hide();
			var activeTab = jQuery(this).find("a").attr("href");
			jQuery(activeTab).fadeIn();
			return false;
		});
	});

	var $tabbed_Widget_tabs_wrap = jQuery("#tabbed-widget div.tabs-wrap");
	$tabbed_Widget_tabs_wrap.hide();
	jQuery("#tabbed-widget ul.posts-taps li:first").addClass("active").show();
	jQuery("#tabbed-widget div.tabs-wrap:first").show();
	jQuery("#tabbed-widget li.tabs").click(function() {
		jQuery("#tabbed-widget ul.posts-taps li").removeClass("active");
		jQuery(this).addClass("active");
		$tabbed_Widget_tabs_wrap.hide();
		var activeTab = jQuery(this).find("a").attr("href");
		jQuery(activeTab).slideDown();
		return false;
	});

//Scrolling Boxes height Fix
	$window.smartresize(function(){
		jQuery("div.group_items-box").each(function(i, el) {
			var groups_height = jQuery(this).find( 'div.group_items:first-child' ).height();
			jQuery(this).height( groups_height );
		});
	});

//Stick Navigation
	var stickySidebarTop = 0;
	var $fixed_enabled = jQuery("#main-nav.fixed-enabled");
	if( !tie_isMobile.any() && $fixed_enabled.length > 0 ){
		stickySidebarTop = 50;
		jQuery( '#theme-header' ).imagesLoaded(function() {
			jQuery(function(){
				var navScroll_1  = jQuery(document).scrollTop();
				var headerHeight = $fixed_enabled .offset().top;

				$window.scroll(function() {
					var navScroll_2 = jQuery(document).scrollTop();

					if (navScroll_2 > headerHeight){ $fixed_enabled.addClass('fixed-nav'); }
					else { $fixed_enabled.removeClass('fixed-nav');}

					if (navScroll_2 > navScroll_1){ $fixed_enabled.removeClass('fixed-nav-appear');}
					else { $fixed_enabled.addClass('fixed-nav-appear');}

					navScroll_1 = jQuery(document).scrollTop();
				});
			});
		});
	}

//Sticky Sidebar
	if( !tie_isMobile.any() && tie.sticky_sidebar ){
		jQuery( '#sidebar' ).theiaStickySidebar({"containerSelector":".content","additionalMarginTop": stickySidebarTop });
	}

//Check Also Box
	jQuery(function(){
		var $check_also_box = jQuery("#check-also-box");
		if( tie.is_singular && $check_also_box.length > 0 ){
			var articleHeight   =  $the_post.outerHeight();
			var checkAlsoClosed = false ;
			$window.scroll(function() {
				if( !checkAlsoClosed ) {
					var articleScroll = jQuery(document).scrollTop();
					if ( articleScroll > articleHeight ){ $check_also_box.addClass('show-check-also');}
					else { $check_also_box.removeClass('show-check-also');}
				}
			});
		}
		jQuery('#check-also-close').click(function() {
			$check_also_box.removeClass("show-check-also");
			checkAlsoClosed = true ;
			return false;
		});
	});

//Reading Position Indicator
	if( tie.is_singular && tie.reading_indicator ){
		var reading_content = $the_post.find( '.entry' );
		if( reading_content.length > 0 ){

			reading_content.imagesLoaded(function() {
				var content_height	= reading_content.height();
					window_height	= $window.height();

				$window.scroll(function() {
					var percent 		= 0,
						content_offset	= reading_content.offset().top;
						window_offest	= $window.scrollTop();

					if (window_offest > content_offset) {
						percent = 100 * (window_offest - content_offset) / (content_height - window_height);
					}
					jQuery('#reading-position-indicator').css('width', percent + '%');
				});
			});
		}
	}

//Comments Form
	if( tie.is_singular ){
		jQuery( "#reply-title" ).after( '<div class="stripe-line"></div>' );
	}

});

// Breaking News
function createTicker(){
	var tickerLIs 	= jQuery("#breaking-news ul").children();
	tickerItems 	= new Array();
	tickerLIs.each(function(el) {
		tickerItems.push( jQuery(this).html() );
	});
	i = 0  ;
	rotateTicker();
}
var isInTag = false;
function typetext() {
	var $breaking_news = jQuery('#breaking-news ul');
	if( $breaking_news.length > 0 ){
		var thisChar = tickerText.substr(c, 1);
		if( thisChar == '<' ){ isInTag = true; }
		if( thisChar == '>' ){ isInTag = false; }
		$breaking_news.html(tickerText.substr(0, c++));
		if(c < tickerText.length+1)
			if( isInTag ){
				typetext();
			}else{
				setTimeout("typetext()", 35);
			}
		else {
			c = 1;
			tickerText = "";
		}
	}
}

//images Scroll
jQuery(function() {
  var win_height_padded = $window.height() * .9;

  $window.on('scroll', tieRevealOnScroll);

  function tieRevealOnScroll() {
    var scrolled = $window.scrollTop(),
        win_height_padded = $window.height() * .9;

	jQuery("body.lazy-enabled #theme-footer div.post-thumbnail, body.lazy-enabled #main-content div.post-thumbnail, body.lazy-enabled #main-content img:not(.ei-slider-thumbs img), body.lazy-enabled #featured-posts").each(function () {
      var $this     = jQuery(this),
          offsetTop = $this.offset().top;

      if (scrolled + win_height_padded > offsetTop) {
		   jQuery(this).addClass( 'tie-appear' );
      }
    });
  }

  tieRevealOnScroll();
});

//isMobile
var tie_isMobile={Android:function(){return navigator.userAgent.match(/(?=.*\bAndroid\b)(?=.*\bMobile\b)/i)},BlackBerry:function(){return navigator.userAgent.match(/BlackBerry/i)},iOS:function(){return navigator.userAgent.match(/iPhone|iPod/i)},Opera:function(){return navigator.userAgent.match(/Opera Mini/i)},Windows:function(){return navigator.userAgent.match(/IEMobile/i)},any:function(){return tie_isMobile.Android()||tie_isMobile.BlackBerry()||tie_isMobile.iOS()||tie_isMobile.Opera()||tie_isMobile.Windows()}};
//debouncing
(function(e,t){var n=function(e,t,n){var r;return function(){function u(){if(!n)e.apply(s,o);r=null}var s=this,o=arguments;if(r)clearTimeout(r);else if(n)e.apply(s,o);r=setTimeout(u,t||100)}};jQuery.fn[t]=function(e){return e?this.bind("resize",n(e)):this.trigger(t)}})(jQuery,"smartresize")
//SmoothScroll for websites v1.2.1
function tie_SmothScroll(){function c(){var e=false;if(e){N("keydown",y)}if(t.keyboardSupport&&!e){T("keydown",y)}}function h(){if(!document.body)return;var e=document.body;var i=document.documentElement;var a=window.innerHeight;var f=e.scrollHeight;o=document.compatMode.indexOf("CSS")>=0?i:e;u=e;c();s=true;if(top!=self){r=true}else if(f>a&&(e.offsetHeight<=a||i.offsetHeight<=a)){var l=false;var h=function(){if(!l&&i.scrollHeight!=document.height){l=true;setTimeout(function(){i.style.height=document.height+"px";l=false},500)}};i.style.height="auto";setTimeout(h,10);if(o.offsetHeight<=a){var p=document.createElement("div");p.style.clear="both";e.appendChild(p)}}if(!t.fixedBackground&&!n){e.style.backgroundAttachment="scroll";i.style.backgroundAttachment="scroll"}}function m(e,n,r,i){i||(i=1e3);k(n,r);if(t.accelerationMax!=1){var s=+(new Date);var o=s-v;if(o<t.accelerationDelta){var u=(1+30/o)/2;if(u>1){u=Math.min(u,t.accelerationMax);n*=u;r*=u}}v=+(new Date)}p.push({x:n,y:r,lastX:n<0?.99:-.99,lastY:r<0?.99:-.99,start:+(new Date)});if(d){return}var a=e===document.body;var f=function(s){var o=+(new Date);var u=0;var l=0;for(var c=0;c<p.length;c++){var h=p[c];var v=o-h.start;var m=v>=t.animationTime;var g=m?1:v/t.animationTime;if(t.pulseAlgorithm){g=D(g)}var y=h.x*g-h.lastX>>0;var b=h.y*g-h.lastY>>0;u+=y;l+=b;h.lastX+=y;h.lastY+=b;if(m){p.splice(c,1);c--}}if(a){window.scrollBy(u,l)}else{if(u)e.scrollLeft+=u;if(l)e.scrollTop+=l}if(!n&&!r){p=[]}if(p.length){M(f,e,i/t.frameRate+1)}else{d=false}};M(f,e,0);d=true}function g(e){if(!s){h()}var n=e.target;var r=x(n);if(!r||e.defaultPrevented||C(u,"embed")||C(n,"embed")&&/\.pdf/i.test(n.src)){return true}var i=e.wheelDeltaX||0;var o=e.wheelDeltaY||0;if(!i&&!o){o=e.wheelDelta||0}if(!t.touchpadSupport&&A(o)){return true}if(Math.abs(i)>1.2){i*=t.stepSize/120}if(Math.abs(o)>1.2){o*=t.stepSize/120}m(r,-i,-o);e.preventDefault()}function y(e){var n=e.target;var r=e.ctrlKey||e.altKey||e.metaKey||e.shiftKey&&e.keyCode!==l.spacebar;if(/input|textarea|select|embed/i.test(n.nodeName)||n.isContentEditable||e.defaultPrevented||r){return true}if(C(n,"button")&&e.keyCode===l.spacebar){return true}var i,s=0,o=0;var a=x(u);var f=a.clientHeight;if(a==document.body){f=window.innerHeight}switch(e.keyCode){case l.up:o=-t.arrowScroll;break;case l.down:o=t.arrowScroll;break;case l.spacebar:i=e.shiftKey?1:-1;o=-i*f*.9;break;case l.pageup:o=-f*.9;break;case l.pagedown:o=f*.9;break;case l.home:o=-a.scrollTop;break;case l.end:var c=a.scrollHeight-a.scrollTop-f;o=c>0?c+10:0;break;case l.left:s=-t.arrowScroll;break;case l.right:s=t.arrowScroll;break;default:return true}m(a,s,o);e.preventDefault()}function b(e){u=e.target}function S(e,t){for(var n=e.length;n--;)w[E(e[n])]=t;return t}function x(e){var t=[];var n=o.scrollHeight;do{var i=w[E(e)];if(i){return S(t,i)}t.push(e);if(n===e.scrollHeight){if(!r||o.clientHeight+10<n){return S(t,document.body)}}else if(e.clientHeight+10<e.scrollHeight){overflow=getComputedStyle(e,"").getPropertyValue("overflow-y");if(overflow==="scroll"||overflow==="auto"){return S(t,e)}}}while(e=e.parentNode)}function T(e,t,n){window.addEventListener(e,t,n||false)}function N(e,t,n){window.removeEventListener(e,t,n||false)}function C(e,t){return(e.nodeName||"").toLowerCase()===t.toLowerCase()}function k(e,t){e=e>0?1:-1;t=t>0?1:-1;if(i.x!==e||i.y!==t){i.x=e;i.y=t;p=[];v=0}}function A(e){if(!e)return;e=Math.abs(e);f.push(e);f.shift();clearTimeout(L);var t=O(f[0],120)&&O(f[1],120)&&O(f[2],120);return!t}function O(e,t){return Math.floor(e/t)==e/t}function _(e){var n,r,i;e=e*t.pulseScale;if(e<1){n=e-(1-Math.exp(-e))}else{r=Math.exp(-1);e-=1;i=1-Math.exp(-e);n=r+i*(1-r)}return n*t.pulseNormalize}function D(e){if(e>=1)return 1;if(e<=0)return 0;if(t.pulseNormalize==1){t.pulseNormalize/=_(1)}return _(e)}var e={frameRate:150,animationTime:400,stepSize:120,pulseAlgorithm:true,pulseScale:8,pulseNormalize:1,accelerationDelta:20,accelerationMax:1,keyboardSupport:true,arrowScroll:50,touchpadSupport:true,fixedBackground:true,excluded:""};var t=e;var n=false;var r=false;var i={x:0,y:0};var s=false;var o=document.documentElement;var u;var a;var f=[120,120,120];var l={left:37,up:38,right:39,down:40,spacebar:32,pageup:33,pagedown:34,end:35,home:36};var t=e;var p=[];var d=false;var v=+(new Date);var w={};setInterval(function(){w={}},10*1e3);var E=function(){var e=0;return function(t){return t.uniqueID||(t.uniqueID=e++)}}();var L;var M=function(){return window.requestAnimationFrame||window.webkitRequestAnimationFrame||function(e,t,n){window.setTimeout(e,n||1e3/60)}}();var P=/chrome/i.test(window.navigator.userAgent);var H=null;if("onwheel"in document.createElement("div"))H="wheel";else if("onmousewheel"in document.createElement("div"))H="mousewheel";if(H&&P){T(H,g);T("mousedown",b);T("load",h)}}
//Modernizr 2.7.0
;window.Modernizr=function(a,b,c){function B(a){j.cssText=a}function C(a,b){return B(m.join(a+";")+(b||""))}function D(a,b){return typeof a===b}function E(a,b){return!!~(""+a).indexOf(b)}function F(a,b){for(var d in a){var e=a[d];if(!E(e,"-")&&j[e]!==c)return b=="pfx"?e:!0}return!1}function G(a,b,d){for(var e in a){var f=b[a[e]];if(f!==c)return d===!1?a[e]:D(f,"function")?f.bind(d||b):f}return!1}function H(a,b,c){var d=a.charAt(0).toUpperCase()+a.slice(1),e=(a+" "+o.join(d+" ")+d).split(" ");return D(b,"string")||D(b,"undefined")?F(e,b):(e=(a+" "+p.join(d+" ")+d).split(" "),G(e,b,c))}var d="2.7.0",e={},f=!0,g=b.documentElement,h="modernizr",i=b.createElement(h),j=i.style,k,l={}.toString,m=" -webkit- -moz- -o- -ms- ".split(" "),n="Webkit Moz O ms",o=n.split(" "),p=n.toLowerCase().split(" "),q={svg:"http://www.w3.org/2000/svg"},r={},s={},t={},u=[],v=u.slice,w,x=function(a,c,d,e){var f,i,j,k,l=b.createElement("div"),m=b.body,n=m||b.createElement("body");if(parseInt(d,10))while(d--)j=b.createElement("div"),j.id=e?e[d]:h+(d+1),l.appendChild(j);return f=["&#173;",'<style id="s',h,'">',a,"</style>"].join(""),l.id=h,(m?l:n).innerHTML+=f,n.appendChild(l),m||(n.style.background="",n.style.overflow="hidden",k=g.style.overflow,g.style.overflow="hidden",g.appendChild(n)),i=c(l,a),m?l.parentNode.removeChild(l):(n.parentNode.removeChild(n),g.style.overflow=k),!!i},y=function(b){var c=a.matchMedia||a.msMatchMedia;if(c)return c(b).matches;var d;return x("@media "+b+" { #"+h+" { position: absolute; } }",function(b){d=(a.getComputedStyle?getComputedStyle(b,null):b.currentStyle)["position"]=="absolute"}),d},z={}.hasOwnProperty,A;!D(z,"undefined")&&!D(z.call,"undefined")?A=function(a,b){return z.call(a,b)}:A=function(a,b){return b in a&&D(a.constructor.prototype[b],"undefined")},Function.prototype.bind||(Function.prototype.bind=function(b){var c=this;if(typeof c!="function")throw new TypeError;var d=v.call(arguments,1),e=function(){if(this instanceof e){var a=function(){};a.prototype=c.prototype;var f=new a,g=c.apply(f,d.concat(v.call(arguments)));return Object(g)===g?g:f}return c.apply(b,d.concat(v.call(arguments)))};return e}),r.touch=function(){var c;return"ontouchstart"in a||a.DocumentTouch&&b instanceof DocumentTouch?c=!0:x(["@media (",m.join("touch-enabled),("),h,")","{#modernizr{top:9px;position:absolute}}"].join(""),function(a){c=a.offsetTop===9}),c},r.csstransforms=function(){return!!H("transform")},r.csstransforms3d=function(){var a=!!H("perspective");return a&&"webkitPerspective"in g.style&&x("@media (transform-3d),(-webkit-transform-3d){#modernizr{left:9px;position:absolute;height:3px;}}",function(b,c){a=b.offsetLeft===9&&b.offsetHeight===3}),a},r.csstransitions=function(){return H("transition")},r.svg=function(){return!!b.createElementNS&&!!b.createElementNS(q.svg,"svg").createSVGRect};for(var I in r)A(r,I)&&(w=I.toLowerCase(),e[w]=r[I](),u.push((e[w]?"":"no-")+w));return e.addTest=function(a,b){if(typeof a=="object")for(var d in a)A(a,d)&&e.addTest(d,a[d]);else{a=a.toLowerCase();if(e[a]!==c)return e;b=typeof b=="function"?b():b,typeof f!="undefined"&&f&&(g.className+=" "+(b?"":"no-")+a),e[a]=b}return e},B(""),i=k=null,function(a,b){function l(a,b){var c=a.createElement("p"),d=a.getElementsByTagName("head")[0]||a.documentElement;return c.innerHTML="x<style>"+b+"</style>",d.insertBefore(c.lastChild,d.firstChild)}function m(){var a=s.elements;return typeof a=="string"?a.split(" "):a}function n(a){var b=j[a[h]];return b||(b={},i++,a[h]=i,j[i]=b),b}function o(a,c,d){c||(c=b);if(k)return c.createElement(a);d||(d=n(c));var g;return d.cache[a]?g=d.cache[a].cloneNode():f.test(a)?g=(d.cache[a]=d.createElem(a)).cloneNode():g=d.createElem(a),g.canHaveChildren&&!e.test(a)&&!g.tagUrn?d.frag.appendChild(g):g}function p(a,c){a||(a=b);if(k)return a.createDocumentFragment();c=c||n(a);var d=c.frag.cloneNode(),e=0,f=m(),g=f.length;for(;e<g;e++)d.createElement(f[e]);return d}function q(a,b){b.cache||(b.cache={},b.createElem=a.createElement,b.createFrag=a.createDocumentFragment,b.frag=b.createFrag()),a.createElement=function(c){return s.shivMethods?o(c,a,b):b.createElem(c)},a.createDocumentFragment=Function("h,f","return function(){var n=f.cloneNode(),c=n.createElement;h.shivMethods&&("+m().join().replace(/[\w\-]+/g,function(a){return b.createElem(a),b.frag.createElement(a),'c("'+a+'")'})+");return n}")(s,b.frag)}function r(a){a||(a=b);var c=n(a);return s.shivCSS&&!g&&!c.hasCSS&&(c.hasCSS=!!l(a,"article,aside,dialog,figcaption,figure,footer,header,hgroup,main,nav,section{display:block}mark{background:#FF0;color:#000}template{display:none}")),k||q(a,c),a}var c="3.7.0",d=a.html5||{},e=/^<|^(?:button|map|select|textarea|object|iframe|option|optgroup)$/i,f=/^(?:a|b|code|div|fieldset|h1|h2|h3|h4|h5|h6|i|label|li|ol|p|q|span|strong|style|table|tbody|td|th|tr|ul)$/i,g,h="_html5shiv",i=0,j={},k;(function(){try{var a=b.createElement("a");a.innerHTML="<xyz></xyz>",g="hidden"in a,k=a.childNodes.length==1||function(){b.createElement("a");var a=b.createDocumentFragment();return typeof a.cloneNode=="undefined"||typeof a.createDocumentFragment=="undefined"||typeof a.createElement=="undefined"}()}catch(c){g=!0,k=!0}})();var s={elements:d.elements||"abbr article aside audio bdi canvas data datalist details dialog figcaption figure footer header hgroup main mark meter nav output progress section summary template time video",version:c,shivCSS:d.shivCSS!==!1,supportsUnknownElements:k,shivMethods:d.shivMethods!==!1,type:"default",shivDocument:r,createElement:o,createDocumentFragment:p};a.html5=s,r(b)}(this,b),e._version=d,e._prefixes=m,e._domPrefixes=p,e._cssomPrefixes=o,e.mq=y,e.testProp=function(a){return F([a])},e.testAllProps=H,e.testStyles=x,e.prefixed=function(a,b,c){return b?H(a,b,c):H(a,"pfx")},g.className=g.className.replace(/(^|\s)no-js(\s|$)/,"$1$2")+(f?" js "+u.join(" "):""),e}(this,this.document),function(a,b,c){function d(a){return"[object Function]"==o.call(a)}function e(a){return"string"==typeof a}function f(){}function g(a){return!a||"loaded"==a||"complete"==a||"uninitialized"==a}function h(){var a=p.shift();q=1,a?a.t?m(function(){("c"==a.t?B.injectCss:B.injectJs)(a.s,0,a.a,a.x,a.e,1)},0):(a(),h()):q=0}function i(a,c,d,e,f,i,j){function k(b){if(!o&&g(l.readyState)&&(u.r=o=1,!q&&h(),l.onload=l.onreadystatechange=null,b)){"img"!=a&&m(function(){t.removeChild(l)},50);for(var d in y[c])y[c].hasOwnProperty(d)&&y[c][d].onload()}}var j=j||B.errorTimeout,l=b.createElement(a),o=0,r=0,u={t:d,s:c,e:f,a:i,x:j};1===y[c]&&(r=1,y[c]=[]),"object"==a?l.data=c:(l.src=c,l.type=a),l.width=l.height="0",l.onerror=l.onload=l.onreadystatechange=function(){k.call(this,r)},p.splice(e,0,u),"img"!=a&&(r||2===y[c]?(t.insertBefore(l,s?null:n),m(k,j)):y[c].push(l))}function j(a,b,c,d,f){return q=0,b=b||"j",e(a)?i("c"==b?v:u,a,b,this.i++,c,d,f):(p.splice(this.i++,0,a),1==p.length&&h()),this}function k(){var a=B;return a.loader={load:j,i:0},a}var l=b.documentElement,m=a.setTimeout,n=b.getElementsByTagName("script")[0],o={}.toString,p=[],q=0,r="MozAppearance"in l.style,s=r&&!!b.createRange().compareNode,t=s?l:n.parentNode,l=a.opera&&"[object Opera]"==o.call(a.opera),l=!!b.attachEvent&&!l,u=r?"object":l?"script":"img",v=l?"script":u,w=Array.isArray||function(a){return"[object Array]"==o.call(a)},x=[],y={},z={timeout:function(a,b){return b.length&&(a.timeout=b[0]),a}},A,B;B=function(a){function b(a){var a=a.split("!"),b=x.length,c=a.pop(),d=a.length,c={url:c,origUrl:c,prefixes:a},e,f,g;for(f=0;f<d;f++)g=a[f].split("="),(e=z[g.shift()])&&(c=e(c,g));for(f=0;f<b;f++)c=x[f](c);return c}function g(a,e,f,g,h){var i=b(a),j=i.autoCallback;i.url.split(".").pop().split("?").shift(),i.bypass||(e&&(e=d(e)?e:e[a]||e[g]||e[a.split("/").pop().split("?")[0]]),i.instead?i.instead(a,e,f,g,h):(y[i.url]?i.noexec=!0:y[i.url]=1,f.load(i.url,i.forceCSS||!i.forceJS&&"css"==i.url.split(".").pop().split("?").shift()?"c":c,i.noexec,i.attrs,i.timeout),(d(e)||d(j))&&f.load(function(){k(),e&&e(i.origUrl,h,g),j&&j(i.origUrl,h,g),y[i.url]=2})))}function h(a,b){function c(a,c){if(a){if(e(a))c||(j=function(){var a=[].slice.call(arguments);k.apply(this,a),l()}),g(a,j,b,0,h);else if(Object(a)===a)for(n in m=function(){var b=0,c;for(c in a)a.hasOwnProperty(c)&&b++;return b}(),a)a.hasOwnProperty(n)&&(!c&&!--m&&(d(j)?j=function(){var a=[].slice.call(arguments);k.apply(this,a),l()}:j[n]=function(a){return function(){var b=[].slice.call(arguments);a&&a.apply(this,b),l()}}(k[n])),g(a[n],j,b,n,h))}else!c&&l()}var h=!!a.test,i=a.load||a.both,j=a.callback||f,k=j,l=a.complete||f,m,n;c(h?a.yep:a.nope,!!i),i&&c(i)}var i,j,l=this.yepnope.loader;if(e(a))g(a,0,l,0);else if(w(a))for(i=0;i<a.length;i++)j=a[i],e(j)?g(j,0,l,0):w(j)?B(j):Object(j)===j&&h(j,l);else Object(a)===a&&h(a,l)},B.addPrefix=function(a,b){z[a]=b},B.addFilter=function(a){x.push(a)},B.errorTimeout=1e4,null==b.readyState&&b.addEventListener&&(b.readyState="loading",b.addEventListener("DOMContentLoaded",A=function(){b.removeEventListener("DOMContentLoaded",A,0),b.readyState="complete"},0)),a.yepnope=k(),a.yepnope.executeStack=h,a.yepnope.injectJs=function(a,c,d,e,i,j){var k=b.createElement("script"),l,o,e=e||B.errorTimeout;k.src=a;for(o in d)k.setAttribute(o,d[o]);c=j?h:c||f,k.onreadystatechange=k.onload=function(){!l&&g(k.readyState)&&(l=1,c(),k.onload=k.onreadystatechange=null)},m(function(){l||(l=1,c(1))},e),i?k.onload():n.parentNode.insertBefore(k,n)},a.yepnope.injectCss=function(a,c,d,e,g,i){var e=b.createElement("link"),j,c=i?h:c||f;e.href=a,e.rel="stylesheet",e.type="text/css";for(j in d)e.setAttribute(j,d[j]);g||(n.parentNode.insertBefore(e,n),m(c,0))}}(this,document),Modernizr.load=function(){yepnope.apply(window,[].slice.call(arguments,0))};
//jQuery Easing v1.4
!function(n){"function"==typeof define&&define.amd?define(["jquery"],function(e){return n(e)}):"object"==typeof module&&"object"==typeof module.exports?exports=n(require("jquery")):n(jQuery)}(function(n){function e(n){var e=7.5625,t=2.75;return n<1/t?e*n*n:n<2/t?e*(n-=1.5/t)*n+.75:n<2.5/t?e*(n-=2.25/t)*n+.9375:e*(n-=2.625/t)*n+.984375}void 0!==n.easing&&(n.easing.jswing=n.easing.swing);var t=Math.pow,u=Math.sqrt,r=Math.sin,i=Math.cos,a=Math.PI,c=1.70158,o=1.525*c,s=2*a/3,f=2*a/4.5;n.extend(n.easing,{def:"easeOutQuad",swing:function(e){return n.easing[n.easing.def](e)},easeInQuad:function(n){return n*n},easeOutQuad:function(n){return 1-(1-n)*(1-n)},easeInOutQuad:function(n){return n<.5?2*n*n:1-t(-2*n+2,2)/2},easeInCubic:function(n){return n*n*n},easeOutCubic:function(n){return 1-t(1-n,3)},easeInOutCubic:function(n){return n<.5?4*n*n*n:1-t(-2*n+2,3)/2},easeInQuart:function(n){return n*n*n*n},easeOutQuart:function(n){return 1-t(1-n,4)},easeInOutQuart:function(n){return n<.5?8*n*n*n*n:1-t(-2*n+2,4)/2},easeInQuint:function(n){return n*n*n*n*n},easeOutQuint:function(n){return 1-t(1-n,5)},easeInOutQuint:function(n){return n<.5?16*n*n*n*n*n:1-t(-2*n+2,5)/2},easeInSine:function(n){return 1-i(n*a/2)},easeOutSine:function(n){return r(n*a/2)},easeInOutSine:function(n){return-(i(a*n)-1)/2},easeInExpo:function(n){return 0===n?0:t(2,10*n-10)},easeOutExpo:function(n){return 1===n?1:1-t(2,-10*n)},easeInOutExpo:function(n){return 0===n?0:1===n?1:n<.5?t(2,20*n-10)/2:(2-t(2,-20*n+10))/2},easeInCirc:function(n){return 1-u(1-t(n,2))},easeOutCirc:function(n){return u(1-t(n-1,2))},easeInOutCirc:function(n){return n<.5?(1-u(1-t(2*n,2)))/2:(u(1-t(-2*n+2,2))+1)/2},easeInElastic:function(n){return 0===n?0:1===n?1:-t(2,10*n-10)*r((10*n-10.75)*s)},easeOutElastic:function(n){return 0===n?0:1===n?1:t(2,-10*n)*r((10*n-.75)*s)+1},easeInOutElastic:function(n){return 0===n?0:1===n?1:n<.5?-(t(2,20*n-10)*r((20*n-11.125)*f))/2:t(2,-20*n+10)*r((20*n-11.125)*f)/2+1},easeInBack:function(n){return(c+1)*n*n*n-c*n*n},easeOutBack:function(n){return 1+(c+1)*t(n-1,3)+c*t(n-1,2)},easeInOutBack:function(n){return n<.5?t(2*n,2)*(7.189819*n-o)/2:(t(2*n-2,2)*((o+1)*(2*n-2)+o)+2)/2},easeInBounce:function(n){return 1-e(1-n)},easeOutBounce:e,easeInOutBounce:function(n){return n<.5?(1-e(1-2*n))/2:(1+e(2*n-1))/2}})});
//ELASTIC IMAGE SLIDESHOW
(function(a,b,c){var d=b.event,e;d.special.smartresize={setup:function(){b(this).bind("resize",d.special.smartresize.handler)},teardown:function(){b(this).unbind("resize",d.special.smartresize.handler)},handler:function(a,b){var c=this,d=arguments;a.type="smartresize";if(e){clearTimeout(e)}e=setTimeout(function(){jQuery.event.handle.apply(c,d)},b==="execAsap"?0:100)}};b.fn.smartresize=function(a){return a?this.bind("smartresize",a):this.trigger("smartresize",["execAsap"])};b.Slideshow=function(a,c){this.$el=b(c);this.$list=this.$el.find("ul.ei-slider-large");this.$imgItems=this.$list.children("li");this.itemsCount=this.$imgItems.length;this.$images=this.$imgItems.find("img:first");this.$sliderthumbs=this.$el.find("ul.ei-slider-thumbs").hide();this.$sliderElems=this.$sliderthumbs.children("li");this.$sliderElem=this.$sliderthumbs.children("li.ei-slider-element");this.$thumbs=this.$sliderElems.not(".ei-slider-element");this._init(a)};b.Slideshow.defaults={animation:"sides",autoplay:false,slideshow_interval:3e3,speed:800,easing:"",titlesFactor:.6,titlespeed:800,titleeasing:"",thumbMaxWidth:150};b.Slideshow.prototype={_init:function(a){this.options=b.extend(true,{},b.Slideshow.defaults,a);this.$imgItems.css("opacity",0);this.$imgItems.find("div.ei-title > *").css("opacity",0);this.current=0;var c=this;this.$loading=b('<div class="ei-slider-loading"></div>').prependTo(c.$el);b.when(this._preloadImages()).done(function(){c.$loading.hide();c._setImagesSize();c._initThumbs();c.$imgItems.eq(c.current).css({opacity:1,"z-index":10}).show().find("div.ei-title > *").css("opacity",1);if(c.options.autoplay){c._startSlideshow()}c._initEvents()})},_preloadImages:function(){var a=this,c=0;return b.Deferred(function(d){a.$images.each(function(e){b("<img/>").load(function(){if(++c===a.itemsCount){d.resolve()}}).attr("src",b(this).attr("src"))})}).promise()},_setImagesSize:function(){this.elWidth=this.$el.width();var a=this;this.$images.each(function(c){var d=b(this);imgDim=a._getImageDim(d.attr("src"));d.css({width:imgDim.width,height:imgDim.height,marginLeft:imgDim.left,marginTop:imgDim.top})})},_getImageDim:function(a){var b=new Image;b.src=a;var c=this.elWidth,d=this.$el.height(),e=d/c,f=b.width,g=b.height,h=g/f,i,j,k,l;if(e>h){j=d;i=d/h}else{j=c*h;i=c}return{width:i,height:j,left:(c-i)/2,top:(d-j)/2}},_initThumbs:function(){this.$sliderElems.css({"max-width":this.options.thumbMaxWidth+"%",width:100/this.itemsCount+"%"});this.$sliderthumbs.css("max-width",this.options.thumbMaxWidth*this.itemsCount+"%").show()},_startSlideshow:function(){var a=this;this.slideshow=setTimeout(function(){var b;a.current===a.itemsCount-1?b=0:b=a.current+1;a._slideTo(b);if(a.options.autoplay){a._startSlideshow()}},this.options.slideshow_interval)},_slideTo:function(a){if(a===this.current||this.isAnimating)return false;this.isAnimating=true;var c=this.$imgItems.eq(this.current),d=this.$imgItems.eq(a),e=this,f={zIndex:10},g={opacity:1};if(this.options.animation==="sides"){f.left=a>this.current?-1*this.elWidth:this.elWidth;g.left=0}d.find("div.ei-title > h2").css("margin-right",50+"px").stop().delay(this.options.speed*this.options.titlesFactor).animate({marginRight:0+"px",opacity:1},this.options.titlespeed,this.options.titleeasing).end().find("div.ei-title > h3").css("margin-right",-50+"px").stop().delay(this.options.speed*this.options.titlesFactor).animate({marginRight:0+"px",opacity:1},this.options.titlespeed,this.options.titleeasing);b.when(c.css("z-index",1).find("div.ei-title > *").stop().fadeOut(this.options.speed/2,function(){b(this).show().css("opacity",0)}),d.css(f).stop().animate(g,this.options.speed,this.options.easing),this.$sliderElem.stop().animate({left:this.$thumbs.eq(a).position().left},this.options.speed)).done(function(){c.css("opacity",0).find("div.ei-title > *").css("opacity",0);e.current=a;e.isAnimating=false})},_initEvents:function(){var c=this;b(a).on("smartresize.eislideshow",function(a){c._setImagesSize();c.$sliderElem.css("left",c.$thumbs.eq(c.current).position().left)});this.$thumbs.on("click.eislideshow",function(a){if(c.options.autoplay){clearTimeout(c.slideshow);c.options.autoplay=false}var d=b(this),e=d.index()-1;c._slideTo(e);return false})}};var f=function(a){if(this.console){console.error(a)}};b.fn.eislideshow=function(a){if(typeof a==="string"){var c=Array.prototype.slice.call(arguments,1);this.each(function(){var d=b.data(this,"eislideshow");if(!d){f("cannot call methods on eislideshow prior to initialization; "+"attempted to call method '"+a+"'");return}if(!b.isFunction(d[a])||a.charAt(0)==="_"){f("no such method '"+a+"' for eislideshow instance");return}d[a].apply(d,c)})}else{this.each(function(){var c=b.data(this,"eislideshow");if(!c){b.data(this,"eislideshow",new b.Slideshow(a,this))}})}return this}})(window,jQuery);
//tipsy
(function(a){function b(a,b){return typeof a=="function"?a.call(b):a}function c(a){while(a=a.parentNode){if(a==document)return true}return false}function d(b,c){this.$element=a(b);this.options=c;this.enabled=true;this.fixTitle()}d.prototype={show:function(){var c=this.getTitle();if(c&&this.enabled){var d=this.tip();d.find(".tipsy-inner")[this.options.html?"html":"text"](c);d[0].className="tipsy";d.remove().css({top:0,left:0,visibility:"hidden",display:"block"}).prependTo(document.body);var e=a.extend({},this.$element.offset(),{width:this.$element[0].offsetWidth,height:this.$element[0].offsetHeight});var f=d[0].offsetWidth,g=d[0].offsetHeight,h=b(this.options.gravity,this.$element[0]);var i;switch(h.charAt(0)){case"n":i={top:e.top+e.height+this.options.offset,left:e.left+e.width/2-f/2};break;case"s":i={top:e.top-g-this.options.offset,left:e.left+e.width/2-f/2};break;case"e":i={top:e.top+e.height/2-g/2,left:e.left-f-this.options.offset};break;case"w":i={top:e.top+e.height/2-g/2,left:e.left+e.width+this.options.offset};break}if(h.length==2){if(h.charAt(1)=="w"){i.left=e.left+e.width/2-15}else{i.left=e.left+e.width/2-f+15}}d.css(i).addClass("tipsy-"+h);d.find(".tipsy-arrow")[0].className="tipsy-arrow tipsy-arrow-"+h.charAt(0);if(this.options.className){d.addClass(b(this.options.className,this.$element[0]))}if(this.options.fade){d.stop().css({opacity:0,display:"block",visibility:"visible"}).animate({opacity:this.options.opacity})}else{d.css({visibility:"visible",opacity:this.options.opacity})}}},hide:function(){if(this.options.fade){this.tip().stop().fadeOut(function(){a(this).remove()})}else{this.tip().remove()}},fixTitle:function(){var a=this.$element;if(a.attr("title")||typeof a.attr("original-title")!="string"){a.attr("original-title",a.attr("title")||"").removeAttr("title")}},getTitle:function(){var a,b=this.$element,c=this.options;this.fixTitle();var a,c=this.options;if(typeof c.title=="string"){a=b.attr(c.title=="title"?"original-title":c.title)}else if(typeof c.title=="function"){a=c.title.call(b[0])}a=(""+a).replace(/(^\s*|\s*$)/,"");return a||c.fallback},tip:function(){if(!this.$tip){this.$tip=a('<div class="tipsy"></div>').html('<div class="tipsy-arrow"></div><div class="tipsy-inner"></div>');this.$tip.data("tipsy-pointee",this.$element[0])}return this.$tip},validate:function(){if(!this.$element[0].parentNode){this.hide();this.$element=null;this.options=null}},enable:function(){this.enabled=true},disable:function(){this.enabled=false},toggleEnabled:function(){this.enabled=!this.enabled}};a.fn.tipsy=function(b){function e(c){var e=a.data(c,"tipsy");if(!e){e=new d(c,a.fn.tipsy.elementOptions(c,b));a.data(c,"tipsy",e)}return e}function f(){var a=e(this);a.hoverState="in";if(b.delayIn==0){a.show()}else{a.fixTitle();setTimeout(function(){if(a.hoverState=="in")a.show()},b.delayIn)}}function g(){var a=e(this);a.hoverState="out";if(b.delayOut==0){a.hide()}else{setTimeout(function(){if(a.hoverState=="out")a.hide()},b.delayOut)}}if(b===true){return this.data("tipsy")}else if(typeof b=="string"){var c=this.data("tipsy");if(c)c[b]();return this}b=a.extend({},a.fn.tipsy.defaults,b);if(!b.live)this.each(function(){e(this)});if(b.trigger!="manual"){var h=b.live?"live":"bind",i=b.trigger=="hover"?"mouseenter":"focus",j=b.trigger=="hover"?"mouseleave":"blur";this[h](i,f)[h](j,g)}return this};a.fn.tipsy.defaults={className:null,delayIn:0,delayOut:0,fade:false,fallback:"",gravity:"n",html:false,live:false,offset:0,opacity:.8,title:"title",trigger:"hover"};a.fn.tipsy.revalidate=function(){a(".tipsy").each(function(){var b=a.data(this,"tipsy-pointee");if(!b||!c(b)){a(this).remove()}})};a.fn.tipsy.elementOptions=function(b,c){return a.metadata?a.extend({},c,a(b).metadata()):c};a.fn.tipsy.autoNS=function(){return a(this).offset().top>a(document).scrollTop()+a(window).height()/2?"s":"n"};a.fn.tipsy.autoWE=function(){return a(this).offset().left>a(document).scrollLeft()+a(window).width()/2?"e":"w"};a.fn.tipsy.autoBounds=function(b,c){return function(){var d={ns:c[0],ew:c.length>1?c[1]:false},e=a(document).scrollTop()+b,f=a(document).scrollLeft()+b,g=a(this);if(g.offset().top<e)d.ns="n";if(g.offset().left<f)d.ew="w";if(a(window).width()+a(document).scrollLeft()-g.offset().left<b)d.ew="e";if(a(window).height()+a(document).scrollTop()-g.offset().top<b)d.ns="s";return d.ns+(d.ew?d.ew:"")}}})(jQuery);
//innerfade
(function($){var default_options={animationType:"fade",animate:true,first_slide:0,easing:"linear",speed:"normal",type:"sequence",timeout:2e3,startDelay:0,loop:true,containerHeight:"auto",runningClass:"innerFade",children:null,cancelLink:null,pauseLink:null,prevLink:null,nextLink:null,indexContainer:null,currentItemContainer:null,totalItemsContainer:null,callback_index_update:null};$(function(){window.isActive=true;$(window).focus(function(){this.isActive=true});$(window).blur(function(){this.isActive=false})});$.fn.innerFade=function(options){return this.each(function(){$fade_object=new Object;$fade_object.container=this;$fade_object.settings=$.extend({},default_options,options);$fade_object.elements=$fade_object.settings.children===null?$($fade_object.container).children():$($fade_object.container).children($fade_object.settings.children);$fade_object.count=0;$($fade_object.container).data("object",$fade_object);if($fade_object.elements.length>1){if($fade_object.settings.nextLink||$fade_object.settings.prevLink){$.bindControls($fade_object)}if($fade_object.settings.cancelLink){$.bindCancel($fade_object)}$($fade_object.container).css({position:"relative"}).addClass($fade_object.settings.runningClass);if($fade_object.settings.containerHeight=="auto"){height=$($fade_object.elements).filter(":first").height();$($fade_object.container).css({height:height+"px"})}else{$($fade_object.container).css({height:$fade_object.settings.containerHeight})}if($fade_object.settings.indexContainer){$.innerFadeIndex($fade_object)}for(var i=0;i<$fade_object.elements.length;i++){$($fade_object.elements[i]).hide(0).css("z-index",String($fade_object.elements.length-i)).css("position","absolute")}var toShow="";var toHide="";if($fade_object.settings.type=="random"){toShow=Math.floor(Math.random()*$fade_object.elements.length);do{toHide=Math.floor(Math.random()*$fade_object.elements.length)}while(toHide==toShow)}else if($fade_object.settings.type=="random_start"){$fade_object.settings.type="sequence";toHide=Math.floor(Math.random()*$fade_object.elements.length);toShow=(toHide+1)%$fade_object.elements.length}else{toShow=$fade_object.settings.first_slide;toHide=$fade_object.settings.first_slide==0?$fade_object.elements.length-1:$fade_object.settings.first_slide-1}if($fade_object.settings.animate){$.fadeTimeout($fade_object,toShow,toHide,true)}else{$($fade_object.elements[toShow]).show();$($fade_object.elements[toHide]).hide();$.updateIndexes($fade_object,toShow)}$.updateIndexes($fade_object,toShow);$($fade_object.elements[toShow]).show();if($fade_object.settings.currentItemContainer){$.currentItem($fade_object,toShow)}if($fade_object.settings.totalItemsContainer){$.totalItems($fade_object)}if($fade_object.settings.pauseLink){$.bind_pause($fade_object)}}})};$.fn.innerFadeTo=function(slide_number){return this.each(function(index){var $fade_object=$(this).data("object");var $currentVisibleItem=$($fade_object.elements).filter(":visible");var currentItemIndex=$($fade_object.elements).index($currentVisibleItem);$.stopSlideshow($fade_object);if(slide_number!=currentItemIndex){$.fadeToItem($fade_object,slide_number,currentItemIndex)}})};$.fadeToItem=function($fade_object,toShow,toHide){var speed=$fade_object.settings.speed;switch($fade_object.settings.animationType){case"slide":$($fade_object.elements[toHide]).slideUp(speed);$($fade_object.elements[toShow]).slideDown(speed);break;case"slideOver":var itemWidth=$($fade_object.elements[0]).width(),to_hide_css={},to_show_css={},to_hide_animation={},to_show_animation={};$($fade_object.container).css({overflow:"hidden"});to_hide_css={position:"absolute",top:"0px"};to_show_css=$.extend({},to_hide_css);if(toShow>toHide){to_hide_css.left="0px";to_hide_css.right="auto";to_show_css.left="auto";to_show_css.right="-"+itemWidth+"px";to_hide_animation.left="-"+itemWidth+"px";to_show_animation.right="0px";console.log(to_hide_css)}else{to_hide_css.left="auto";to_hide_css.right="0px";to_show_css.left="-"+itemWidth+"px";to_show_css.right="auto";to_hide_animation.right="-"+itemWidth+"px";to_show_animation.left="0px"};$($fade_object.elements[toHide]).css(to_hide_css);$($fade_object.elements[toShow]).css(to_show_css).show();$($fade_object.elements[toHide]).animate(to_hide_animation,speed,$fade_object.settings.easing,function(){$(this).hide()});$($fade_object.elements[toShow]).animate(to_show_animation,speed,$fade_object.settings.easing);break;case"fadeEmpty":$($fade_object.elements[toHide]).fadeOut(speed,function(){$($fade_object.elements[toShow]).fadeIn(speed)});break;case"slideEmpty":$($fade_object.elements[toHide]).slideUp(speed,function(){$($fade_object.elements[toShow]).slideDown(speed)});break;default:$($fade_object.elements[toHide]).fadeOut(speed);$($fade_object.elements[toShow]).fadeIn(speed);break}if($fade_object.settings.currentItemContainer){$.currentItem($fade_object,toShow)}if($fade_object.settings.indexContainer||$fade_object.settings.callback_index_update){$.updateIndexes($fade_object,toShow)}};$.fadeTimeout=function($fade_object,toShow,toHide,firstRun){if(window.isActive){if(firstRun!=true){$.fadeToItem($fade_object,toShow,toHide)}$fade_object.count++;if($fade_object.settings.loop==false&&$fade_object.count>=$fade_object.elements.length){$.stopSlideshow($fade_object);return}if($fade_object.settings.type=="random"){toHide=toShow;while(toShow==toHide){toShow=Math.floor(Math.random()*$fade_object.elements.length)}}else{toHide=toHide>toShow?0:toShow;toShow=toShow+1>=$fade_object.elements.length?0:toShow+1}}var timeout=firstRun&&$fade_object.settings.startDelay?$fade_object.settings.startDelay:$fade_object.settings.timeout;$($fade_object.container).data("current_timeout",setTimeout(function(){$.fadeTimeout($fade_object,toShow,toHide,false)},timeout))};$.fn.innerFadeUnbind=function(){return this.each(function(index){var $fade_object=$(this).data("object");$.stopSlideshow($fade_object)})};$.stopSlideshow=function($fade_object){clearTimeout($($fade_object.container).data("current_timeout"));$($fade_object.container).data("current_timeout",null)};$.bindControls=function($fade_object){$($fade_object.settings.nextLink).on("click",function(event){event.preventDefault();$.stopSlideshow($fade_object);var $currentElement=$($fade_object.elements).filter(":visible");var currentElementIndex=$($fade_object.elements).index($currentElement);var $nextElement=$currentElement.next().length>0?$currentElement.next():$($fade_object.elements).filter(":first");var nextElementIndex=$($fade_object.elements).index($nextElement);$.fadeToItem($fade_object,nextElementIndex,currentElementIndex)});$($fade_object.settings.prevLink).on("click",function(event){event.preventDefault();$.stopSlideshow($fade_object);var $currentElement=$($fade_object.elements).filter(":visible");var currentElementIndex=$($fade_object.elements).index($currentElement);var $previousElement=$currentElement.prev().length>0?$currentElement.prev():$($fade_object.elements).filter(":last");var previousElementIndex=$($fade_object.elements).index($previousElement);$.fadeToItem($fade_object,previousElementIndex,currentElementIndex)})};$.bind_pause=function($fade_object){$($fade_object.settings.pauseLink).unbind().click(function(event){event.preventDefault();if($($fade_object.container).data("current_timeout")!=null){$.stopSlideshow($fade_object)}else{var tag=$($fade_object.container).children(":first").prop("tagName").toLowerCase();var nextItem="";var previousItem="";if($fade_object.settings.type=="random"){previousItem=Math.floor(Math.random()*$fade_object.elements.length);do{nextItem=Math.floor(Math.random()*$fade_object.elements.length)}while(previousItem==nextItem)}else if($fade_object.settings.type=="random_start"){previousItem=Math.floor(Math.random()*$fade_object.elements.length);nextItem=(previousItem+1)%$fade_object.elements.length}else{previousItem=$(tag,$($fade_object.container)).index($(tag+":visible",$($fade_object.container)));nextItem=previousItem+1==$fade_object.elements.length?0:previousItem+1}$.fadeTimeout($fade_object,nextItem,previousItem,false)}})};$.bindCancel=function($fade_object){$($fade_object.settings.cancelLink).unbind().click(function(event){event.preventDefault();$.stopSlideshow($fade_object)})};$.updateIndexes=function($fade_object,toShow){$($fade_object.settings.indexContainer).children().removeClass("active");$("> :eq("+toShow+")",$($fade_object.settings.indexContainer)).addClass("active");if(typeof $fade_object.settings.callback_index_update=="function"){$fade_object.settings.callback_index_update.call(this,toShow)}};$.createIndexHandler=function($fade_object,count,link){$(link).click(function(event){event.preventDefault();var $currentVisibleItem=$($fade_object.elements).filter(":visible");var currentItemIndex=$($fade_object.elements).index($currentVisibleItem);$.stopSlideshow($fade_object);if($currentVisibleItem.size()<=1&&count!=currentItemIndex){$.fadeToItem($fade_object,count,currentItemIndex)}})};$.createIndexes=function($fade_object){var $indexContainer=$($fade_object.settings.indexContainer);for(var i=0;i<$fade_object.elements.length;i++){var $link=$('<li><a href="#">'+(i+1)+"</a></li>");$.createIndexHandler($fade_object,i,$link);$indexContainer.append($link)}};$.linkIndexes=function($fade_object){var $indexContainer=$($fade_object.settings.indexContainer);var $indexContainerChildren=$("> :visible",$indexContainer);if($indexContainerChildren.size()==$fade_object.elements.length){var count=$fade_object.elements.length;for(var i=0;i<count;i++){$("a",$indexContainer).click(function(event){event.preventDefault()});$.createIndexHandler($fade_object,i,$indexContainerChildren[i])}}else{alert("There is a different number of items in the menu and slides. There needs to be the same number in both.\nThere are "+$indexContainerChildren.size()+" in the indexContainer.\nThere are "+$fade_object.elements.length+" in the slides container.")}};$.innerFadeIndex=function($fade_object){var $indexContainer=$($fade_object.settings.indexContainer);if($(":visible",$indexContainer).size()<=0){$.createIndexes($fade_object)}else{$.linkIndexes($fade_object)}};$.currentItem=function($fade_object,current){var $container=$($fade_object.settings.currentItemContainer);$container.text(current+1)};$.totalItems=function($fade_object){var $container=$($fade_object.settings.totalItemsContainer);$container.text($fade_object.elements.length)}})(jQuery);
//jQuery FlexSlider v2.5.0  Copyright 2012 WooThemes Contributing Author: Tyler Smith
!function($){$.flexslider=function(e,t){var a=$(e);a.vars=$.extend({},$.flexslider.defaults,t);var n=a.vars.namespace,i=window.navigator&&window.navigator.msPointerEnabled&&window.MSGesture,s=("ontouchstart"in window||i||window.DocumentTouch&&document instanceof DocumentTouch)&&a.vars.touch,r="click touchend MSPointerUp keyup",o="",l,c="vertical"===a.vars.direction,d=a.vars.reverse,u=a.vars.itemWidth>0,v="fade"===a.vars.animation,p=""!==a.vars.asNavFor,m={},f=!0;$.data(e,"flexslider",a),m={init:function(){a.animating=!1,a.currentSlide=parseInt(a.vars.startAt?a.vars.startAt:0,10),isNaN(a.currentSlide)&&(a.currentSlide=0),a.animatingTo=a.currentSlide,a.atEnd=0===a.currentSlide||a.currentSlide===a.last,a.containerSelector=a.vars.selector.substr(0,a.vars.selector.search(" ")),a.slides=$(a.vars.selector,a),a.container=$(a.containerSelector,a),a.count=a.slides.length,a.syncExists=$(a.vars.sync).length>0,"slide"===a.vars.animation&&(a.vars.animation="swing"),a.prop=c?"top":"marginLeft",a.args={},a.manualPause=!1,a.stopped=!1,a.started=!1,a.startTimeout=null,a.transitions=!a.vars.video&&!v&&a.vars.useCSS&&function(){var e=document.createElement("div"),t=["perspectiveProperty","WebkitPerspective","MozPerspective","OPerspective","msPerspective"];for(var n in t)if(void 0!==e.style[t[n]])return a.pfx=t[n].replace("Perspective","").toLowerCase(),a.prop="-"+a.pfx+"-transform",!0;return!1}(),a.ensureAnimationEnd="",""!==a.vars.controlsContainer&&(a.controlsContainer=$(a.vars.controlsContainer).length>0&&$(a.vars.controlsContainer)),""!==a.vars.manualControls&&(a.manualControls=$(a.vars.manualControls).length>0&&$(a.vars.manualControls)),""!==a.vars.customDirectionNav&&(a.customDirectionNav=2===$(a.vars.customDirectionNav).length&&$(a.vars.customDirectionNav)),a.vars.randomize&&(a.slides.sort(function(){return Math.round(Math.random())-.5}),a.container.empty().append(a.slides)),a.doMath(),a.setup("init"),a.vars.controlNav&&m.controlNav.setup(),a.vars.directionNav&&m.directionNav.setup(),a.vars.keyboard&&(1===$(a.containerSelector).length||a.vars.multipleKeyboard)&&$(document).bind("keyup",function(e){var t=e.keyCode;if(!a.animating&&(39===t||37===t)){var n=39===t?a.getTarget("next"):37===t?a.getTarget("prev"):!1;a.flexAnimate(n,a.vars.pauseOnAction)}}),a.vars.mousewheel&&a.bind("mousewheel",function(e,t,n,i){e.preventDefault();var s=a.getTarget(0>t?"next":"prev");a.flexAnimate(s,a.vars.pauseOnAction)}),a.vars.pausePlay&&m.pausePlay.setup(),a.vars.slideshow&&a.vars.pauseInvisible&&m.pauseInvisible.init(),a.vars.slideshow&&(a.vars.pauseOnHover&&a.hover(function(){a.manualPlay||a.manualPause||a.pause()},function(){a.manualPause||a.manualPlay||a.stopped||a.play()}),a.vars.pauseInvisible&&m.pauseInvisible.isHidden()||(a.vars.initDelay>0?a.startTimeout=setTimeout(a.play,a.vars.initDelay):a.play())),p&&m.asNav.setup(),s&&a.vars.touch&&m.touch(),(!v||v&&a.vars.smoothHeight)&&$(window).bind("resize orientationchange focus",m.resize),a.find("img").attr("draggable","false"),setTimeout(function(){a.vars.start(a)},200)},asNav:{setup:function(){a.asNav=!0,a.animatingTo=Math.floor(a.currentSlide/a.move),a.currentItem=a.currentSlide,a.slides.removeClass(n+"active-slide").eq(a.currentItem).addClass(n+"active-slide"),i?(e._slider=a,a.slides.each(function(){var e=this;e._gesture=new MSGesture,e._gesture.target=e,e.addEventListener("MSPointerDown",function(e){e.preventDefault(),e.currentTarget._gesture&&e.currentTarget._gesture.addPointer(e.pointerId)},!1),e.addEventListener("MSGestureTap",function(e){e.preventDefault();var t=$(this),n=t.index();$(a.vars.asNavFor).data("flexslider").animating||t.hasClass("active")||(a.direction=a.currentItem<n?"next":"prev",a.flexAnimate(n,a.vars.pauseOnAction,!1,!0,!0))})})):a.slides.on(r,function(e){e.preventDefault();var t=$(this),i=t.index(),s=t.offset().left-$(a).scrollLeft();0>=s&&t.hasClass(n+"active-slide")?a.flexAnimate(a.getTarget("prev"),!0):$(a.vars.asNavFor).data("flexslider").animating||t.hasClass(n+"active-slide")||(a.direction=a.currentItem<i?"next":"prev",a.flexAnimate(i,a.vars.pauseOnAction,!1,!0,!0))})}},controlNav:{setup:function(){a.manualControls?m.controlNav.setupManual():m.controlNav.setupPaging()},setupPaging:function(){var e="thumbnails"===a.vars.controlNav?"control-thumbs":"control-paging",t=1,i,s;if(a.controlNavScaffold=$('<ol class="'+n+"control-nav "+n+e+'"></ol>'),a.pagingCount>1)for(var l=0;l<a.pagingCount;l++){if(s=a.slides.eq(l),i="thumbnails"===a.vars.controlNav?'<img src="'+s.attr("data-thumb")+'"/>':"<a>"+t+"</a>","thumbnails"===a.vars.controlNav&&!0===a.vars.thumbCaptions){var c=s.attr("data-thumbcaption");""!==c&&void 0!==c&&(i+='<span class="'+n+'caption">'+c+"</span>")}a.controlNavScaffold.append("<li>"+i+"</li>"),t++}a.controlsContainer?$(a.controlsContainer).append(a.controlNavScaffold):a.append(a.controlNavScaffold),m.controlNav.set(),m.controlNav.active(),a.controlNavScaffold.delegate("a, img",r,function(e){if(e.preventDefault(),""===o||o===e.type){var t=$(this),i=a.controlNav.index(t);t.hasClass(n+"active")||(a.direction=i>a.currentSlide?"next":"prev",a.flexAnimate(i,a.vars.pauseOnAction))}""===o&&(o=e.type),m.setToClearWatchedEvent()})},setupManual:function(){a.controlNav=a.manualControls,m.controlNav.active(),a.controlNav.bind(r,function(e){if(e.preventDefault(),""===o||o===e.type){var t=$(this),i=a.controlNav.index(t);t.hasClass(n+"active")||(a.direction=i>a.currentSlide?"next":"prev",a.flexAnimate(i,a.vars.pauseOnAction))}""===o&&(o=e.type),m.setToClearWatchedEvent()})},set:function(){var e="thumbnails"===a.vars.controlNav?"img":"a";a.controlNav=$("."+n+"control-nav li "+e,a.controlsContainer?a.controlsContainer:a)},active:function(){a.controlNav.removeClass(n+"active").eq(a.animatingTo).addClass(n+"active")},update:function(e,t){a.pagingCount>1&&"add"===e?a.controlNavScaffold.append($("<li><a>"+a.count+"</a></li>")):1===a.pagingCount?a.controlNavScaffold.find("li").remove():a.controlNav.eq(t).closest("li").remove(),m.controlNav.set(),a.pagingCount>1&&a.pagingCount!==a.controlNav.length?a.update(t,e):m.controlNav.active()}},directionNav:{setup:function(){var e=$('<ul class="'+n+'direction-nav"><li class="'+n+'nav-prev"><a class="'+n+'prev" href="#">'+a.vars.prevText+'</a></li><li class="'+n+'nav-next"><a class="'+n+'next" href="#">'+a.vars.nextText+"</a></li></ul>");a.customDirectionNav?a.directionNav=a.customDirectionNav:a.controlsContainer?($(a.controlsContainer).append(e),a.directionNav=$("."+n+"direction-nav li a",a.controlsContainer)):(a.append(e),a.directionNav=$("."+n+"direction-nav li a",a)),m.directionNav.update(),a.directionNav.bind(r,function(e){e.preventDefault();var t;(""===o||o===e.type)&&(t=a.getTarget($(this).hasClass(n+"next")?"next":"prev"),a.flexAnimate(t,a.vars.pauseOnAction)),""===o&&(o=e.type),m.setToClearWatchedEvent()})},update:function(){var e=n+"disabled";1===a.pagingCount?a.directionNav.addClass(e).attr("tabindex","-1"):a.vars.animationLoop?a.directionNav.removeClass(e).removeAttr("tabindex"):0===a.animatingTo?a.directionNav.removeClass(e).filter("."+n+"prev").addClass(e).attr("tabindex","-1"):a.animatingTo===a.last?a.directionNav.removeClass(e).filter("."+n+"next").addClass(e).attr("tabindex","-1"):a.directionNav.removeClass(e).removeAttr("tabindex")}},pausePlay:{setup:function(){var e=$('<div class="'+n+'pauseplay"><a></a></div>');a.controlsContainer?(a.controlsContainer.append(e),a.pausePlay=$("."+n+"pauseplay a",a.controlsContainer)):(a.append(e),a.pausePlay=$("."+n+"pauseplay a",a)),m.pausePlay.update(a.vars.slideshow?n+"pause":n+"play"),a.pausePlay.bind(r,function(e){e.preventDefault(),(""===o||o===e.type)&&($(this).hasClass(n+"pause")?(a.manualPause=!0,a.manualPlay=!1,a.pause()):(a.manualPause=!1,a.manualPlay=!0,a.play())),""===o&&(o=e.type),m.setToClearWatchedEvent()})},update:function(e){"play"===e?a.pausePlay.removeClass(n+"pause").addClass(n+"play").html(a.vars.playText):a.pausePlay.removeClass(n+"play").addClass(n+"pause").html(a.vars.pauseText)}},touch:function(){function t(t){t.stopPropagation(),a.animating?t.preventDefault():(a.pause(),e._gesture.addPointer(t.pointerId),w=0,p=c?a.h:a.w,f=Number(new Date),l=u&&d&&a.animatingTo===a.last?0:u&&d?a.limit-(a.itemW+a.vars.itemMargin)*a.move*a.animatingTo:u&&a.currentSlide===a.last?a.limit:u?(a.itemW+a.vars.itemMargin)*a.move*a.currentSlide:d?(a.last-a.currentSlide+a.cloneOffset)*p:(a.currentSlide+a.cloneOffset)*p)}function n(t){t.stopPropagation();var a=t.target._slider;if(a){var n=-t.translationX,i=-t.translationY;return w+=c?i:n,m=w,y=c?Math.abs(w)<Math.abs(-n):Math.abs(w)<Math.abs(-i),t.detail===t.MSGESTURE_FLAG_INERTIA?void setImmediate(function(){e._gesture.stop()}):void((!y||Number(new Date)-f>500)&&(t.preventDefault(),!v&&a.transitions&&(a.vars.animationLoop||(m=w/(0===a.currentSlide&&0>w||a.currentSlide===a.last&&w>0?Math.abs(w)/p+2:1)),a.setProps(l+m,"setTouch"))))}}function s(e){e.stopPropagation();var t=e.target._slider;if(t){if(t.animatingTo===t.currentSlide&&!y&&null!==m){var a=d?-m:m,n=t.getTarget(a>0?"next":"prev");t.canAdvance(n)&&(Number(new Date)-f<550&&Math.abs(a)>50||Math.abs(a)>p/2)?t.flexAnimate(n,t.vars.pauseOnAction):v||t.flexAnimate(t.currentSlide,t.vars.pauseOnAction,!0)}r=null,o=null,m=null,l=null,w=0}}var r,o,l,p,m,f,g,h,S,y=!1,x=0,b=0,w=0;i?(e.style.msTouchAction="none",e._gesture=new MSGesture,e._gesture.target=e,e.addEventListener("MSPointerDown",t,!1),e._slider=a,e.addEventListener("MSGestureChange",n,!1),e.addEventListener("MSGestureEnd",s,!1)):(g=function(t){a.animating?t.preventDefault():(window.navigator.msPointerEnabled||1===t.touches.length)&&(a.pause(),p=c?a.h:a.w,f=Number(new Date),x=t.touches[0].pageX,b=t.touches[0].pageY,l=u&&d&&a.animatingTo===a.last?0:u&&d?a.limit-(a.itemW+a.vars.itemMargin)*a.move*a.animatingTo:u&&a.currentSlide===a.last?a.limit:u?(a.itemW+a.vars.itemMargin)*a.move*a.currentSlide:d?(a.last-a.currentSlide+a.cloneOffset)*p:(a.currentSlide+a.cloneOffset)*p,r=c?b:x,o=c?x:b,e.addEventListener("touchmove",h,!1),e.addEventListener("touchend",S,!1))},h=function(e){x=e.touches[0].pageX,b=e.touches[0].pageY,m=c?r-b:r-x,y=c?Math.abs(m)<Math.abs(x-o):Math.abs(m)<Math.abs(b-o);var t=500;(!y||Number(new Date)-f>t)&&(e.preventDefault(),!v&&a.transitions&&(a.vars.animationLoop||(m/=0===a.currentSlide&&0>m||a.currentSlide===a.last&&m>0?Math.abs(m)/p+2:1),a.setProps(l+m,"setTouch")))},S=function(t){if(e.removeEventListener("touchmove",h,!1),a.animatingTo===a.currentSlide&&!y&&null!==m){var n=d?-m:m,i=a.getTarget(n>0?"next":"prev");a.canAdvance(i)&&(Number(new Date)-f<550&&Math.abs(n)>50||Math.abs(n)>p/2)?a.flexAnimate(i,a.vars.pauseOnAction):v||a.flexAnimate(a.currentSlide,a.vars.pauseOnAction,!0)}e.removeEventListener("touchend",S,!1),r=null,o=null,m=null,l=null},e.addEventListener("touchstart",g,!1))},resize:function(){!a.animating&&a.is(":visible")&&(u||a.doMath(),v?m.smoothHeight():u?(a.slides.width(a.computedW),a.update(a.pagingCount),a.setProps()):c?(a.viewport.height(a.h),a.setProps(a.h,"setTotal")):(a.vars.smoothHeight&&m.smoothHeight(),a.newSlides.width(a.computedW),a.setProps(a.computedW,"setTotal")))},smoothHeight:function(e){if(!c||v){var t=v?a:a.viewport;e?t.animate({height:a.slides.eq(a.animatingTo).height()},e):t.height(a.slides.eq(a.animatingTo).height())}},sync:function(e){var t=$(a.vars.sync).data("flexslider"),n=a.animatingTo;switch(e){case"animate":t.flexAnimate(n,a.vars.pauseOnAction,!1,!0);break;case"play":t.playing||t.asNav||t.play();break;case"pause":t.pause()}},uniqueID:function(e){return e.filter("[id]").add(e.find("[id]")).each(function(){var e=$(this);e.attr("id",e.attr("id")+"_clone")}),e},pauseInvisible:{visProp:null,init:function(){var e=m.pauseInvisible.getHiddenProp();if(e){var t=e.replace(/[H|h]idden/,"")+"visibilitychange";document.addEventListener(t,function(){m.pauseInvisible.isHidden()?a.startTimeout?clearTimeout(a.startTimeout):a.pause():a.started?a.play():a.vars.initDelay>0?setTimeout(a.play,a.vars.initDelay):a.play()})}},isHidden:function(){var e=m.pauseInvisible.getHiddenProp();return e?document[e]:!1},getHiddenProp:function(){var e=["webkit","moz","ms","o"];if("hidden"in document)return"hidden";for(var t=0;t<e.length;t++)if(e[t]+"Hidden"in document)return e[t]+"Hidden";return null}},setToClearWatchedEvent:function(){clearTimeout(l),l=setTimeout(function(){o=""},3e3)}},a.flexAnimate=function(e,t,i,r,o){if(a.vars.animationLoop||e===a.currentSlide||(a.direction=e>a.currentSlide?"next":"prev"),p&&1===a.pagingCount&&(a.direction=a.currentItem<e?"next":"prev"),!a.animating&&(a.canAdvance(e,o)||i)&&a.is(":visible")){if(p&&r){var l=$(a.vars.asNavFor).data("flexslider");if(a.atEnd=0===e||e===a.count-1,l.flexAnimate(e,!0,!1,!0,o),a.direction=a.currentItem<e?"next":"prev",l.direction=a.direction,Math.ceil((e+1)/a.visible)-1===a.currentSlide||0===e)return a.currentItem=e,a.slides.removeClass(n+"active-slide").eq(e).addClass(n+"active-slide"),!1;a.currentItem=e,a.slides.removeClass(n+"active-slide").eq(e).addClass(n+"active-slide"),e=Math.floor(e/a.visible)}if(a.animating=!0,a.animatingTo=e,t&&a.pause(),a.vars.before(a),a.syncExists&&!o&&m.sync("animate"),a.vars.controlNav&&m.controlNav.active(),u||a.slides.removeClass(n+"active-slide").eq(e).addClass(n+"active-slide"),a.atEnd=0===e||e===a.last,a.vars.directionNav&&m.directionNav.update(),e===a.last&&(a.vars.end(a),a.vars.animationLoop||a.pause()),v)s?(a.slides.eq(a.currentSlide).css({opacity:0,zIndex:1}),a.slides.eq(e).css({opacity:1,zIndex:2}),a.wrapup(f)):(a.slides.eq(a.currentSlide).css({zIndex:1}).animate({opacity:0},a.vars.animationSpeed,a.vars.easing),a.slides.eq(e).css({zIndex:2}).animate({opacity:1},a.vars.animationSpeed,a.vars.easing,a.wrapup));else{var f=c?a.slides.filter(":first").height():a.computedW,g,h,S;u?(g=a.vars.itemMargin,S=(a.itemW+g)*a.move*a.animatingTo,h=S>a.limit&&1!==a.visible?a.limit:S):h=0===a.currentSlide&&e===a.count-1&&a.vars.animationLoop&&"next"!==a.direction?d?(a.count+a.cloneOffset)*f:0:a.currentSlide===a.last&&0===e&&a.vars.animationLoop&&"prev"!==a.direction?d?0:(a.count+1)*f:d?(a.count-1-e+a.cloneOffset)*f:(e+a.cloneOffset)*f,a.setProps(h,"",a.vars.animationSpeed),a.transitions?(a.vars.animationLoop&&a.atEnd||(a.animating=!1,a.currentSlide=a.animatingTo),a.container.unbind("webkitTransitionEnd transitionend"),a.container.bind("webkitTransitionEnd transitionend",function(){clearTimeout(a.ensureAnimationEnd),a.wrapup(f)}),clearTimeout(a.ensureAnimationEnd),a.ensureAnimationEnd=setTimeout(function(){a.wrapup(f)},a.vars.animationSpeed+100)):a.container.animate(a.args,a.vars.animationSpeed,a.vars.easing,function(){a.wrapup(f)})}a.vars.smoothHeight&&m.smoothHeight(a.vars.animationSpeed)}},a.wrapup=function(e){v||u||(0===a.currentSlide&&a.animatingTo===a.last&&a.vars.animationLoop?a.setProps(e,"jumpEnd"):a.currentSlide===a.last&&0===a.animatingTo&&a.vars.animationLoop&&a.setProps(e,"jumpStart")),a.animating=!1,a.currentSlide=a.animatingTo,a.vars.after(a)},a.animateSlides=function(){!a.animating&&f&&a.flexAnimate(a.getTarget("next"))},a.pause=function(){clearInterval(a.animatedSlides),a.animatedSlides=null,a.playing=!1,a.vars.pausePlay&&m.pausePlay.update("play"),a.syncExists&&m.sync("pause")},a.play=function(){a.playing&&clearInterval(a.animatedSlides),a.animatedSlides=a.animatedSlides||setInterval(a.animateSlides,a.vars.slideshowSpeed),a.started=a.playing=!0,a.vars.pausePlay&&m.pausePlay.update("pause"),a.syncExists&&m.sync("play")},a.stop=function(){a.pause(),a.stopped=!0},a.canAdvance=function(e,t){var n=p?a.pagingCount-1:a.last;return t?!0:p&&a.currentItem===a.count-1&&0===e&&"prev"===a.direction?!0:p&&0===a.currentItem&&e===a.pagingCount-1&&"next"!==a.direction?!1:e!==a.currentSlide||p?a.vars.animationLoop?!0:a.atEnd&&0===a.currentSlide&&e===n&&"next"!==a.direction?!1:a.atEnd&&a.currentSlide===n&&0===e&&"next"===a.direction?!1:!0:!1},a.getTarget=function(e){return a.direction=e,"next"===e?a.currentSlide===a.last?0:a.currentSlide+1:0===a.currentSlide?a.last:a.currentSlide-1},a.setProps=function(e,t,n){var i=function(){var n=e?e:(a.itemW+a.vars.itemMargin)*a.move*a.animatingTo,i=function(){if(u)return"setTouch"===t?e:d&&a.animatingTo===a.last?0:d?a.limit-(a.itemW+a.vars.itemMargin)*a.move*a.animatingTo:a.animatingTo===a.last?a.limit:n;switch(t){case"setTotal":return d?(a.count-1-a.currentSlide+a.cloneOffset)*e:(a.currentSlide+a.cloneOffset)*e;case"setTouch":return d?e:e;case"jumpEnd":return d?e:a.count*e;case"jumpStart":return d?a.count*e:e;default:return e}}();return-1*i+"px"}();a.transitions&&(i=c?"translate3d(0,"+i+",0)":"translate3d("+i+",0,0)",n=void 0!==n?n/1e3+"s":"0s",a.container.css("-"+a.pfx+"-transition-duration",n),a.container.css("transition-duration",n)),a.args[a.prop]=i,(a.transitions||void 0===n)&&a.container.css(a.args),a.container.css("transform",i)},a.setup=function(e){if(v)a.slides.css({width:"100%","float":"left",marginRight:"-100%",position:"relative"}),"init"===e&&(s?a.slides.css({opacity:0,display:"block",webkitTransition:"opacity "+a.vars.animationSpeed/1e3+"s ease",zIndex:1}).eq(a.currentSlide).css({opacity:1,zIndex:2}):0==a.vars.fadeFirstSlide?a.slides.css({opacity:0,display:"block",zIndex:1}).eq(a.currentSlide).css({zIndex:2}).css({opacity:1}):a.slides.css({opacity:0,display:"block",zIndex:1}).eq(a.currentSlide).css({zIndex:2}).animate({opacity:1},a.vars.animationSpeed,a.vars.easing)),a.vars.smoothHeight&&m.smoothHeight();else{var t,i;"init"===e&&(a.viewport=$('<div class="'+n+'viewport"></div>').css({overflow:"hidden",position:"relative"}).appendTo(a).append(a.container),a.cloneCount=0,a.cloneOffset=0,d&&(i=$.makeArray(a.slides).reverse(),a.slides=$(i),a.container.empty().append(a.slides))),a.vars.animationLoop&&!u&&(a.cloneCount=2,a.cloneOffset=1,"init"!==e&&a.container.find(".clone").remove(),a.container.append(m.uniqueID(a.slides.first().clone().addClass("clone")).attr("aria-hidden","true")).prepend(m.uniqueID(a.slides.last().clone().addClass("clone")).attr("aria-hidden","true"))),a.newSlides=$(a.vars.selector,a),t=d?a.count-1-a.currentSlide+a.cloneOffset:a.currentSlide+a.cloneOffset,c&&!u?(a.container.height(200*(a.count+a.cloneCount)+"%").css("position","absolute").width("100%"),setTimeout(function(){a.newSlides.css({display:"block"}),a.doMath(),a.viewport.height(a.h),a.setProps(t*a.h,"init")},"init"===e?100:0)):(a.container.width(200*(a.count+a.cloneCount)+"%"),a.setProps(t*a.computedW,"init"),setTimeout(function(){a.doMath(),a.newSlides.css({width:a.computedW,"float":"left",display:"block"}),a.vars.smoothHeight&&m.smoothHeight()},"init"===e?100:0))}u||a.slides.removeClass(n+"active-slide").eq(a.currentSlide).addClass(n+"active-slide"),a.vars.init(a)},a.doMath=function(){var e=a.slides.first(),t=a.vars.itemMargin,n=a.vars.minItems,i=a.vars.maxItems;a.w=void 0===a.viewport?a.width():a.viewport.width(),a.h=e.height(),a.boxPadding=e.outerWidth()-e.width(),u?(a.itemT=a.vars.itemWidth+t,a.minW=n?n*a.itemT:a.w,a.maxW=i?i*a.itemT-t:a.w,a.itemW=a.minW>a.w?(a.w-t*(n-1))/n:a.maxW<a.w?(a.w-t*(i-1))/i:a.vars.itemWidth>a.w?a.w:a.vars.itemWidth,a.visible=Math.floor(a.w/a.itemW),a.move=a.vars.move>0&&a.vars.move<a.visible?a.vars.move:a.visible,a.pagingCount=Math.ceil((a.count-a.visible)/a.move+1),a.last=a.pagingCount-1,a.limit=1===a.pagingCount?0:a.vars.itemWidth>a.w?a.itemW*(a.count-1)+t*(a.count-1):(a.itemW+t)*a.count-a.w-t):(a.itemW=a.w,a.pagingCount=a.count,a.last=a.count-1),a.computedW=a.itemW-a.boxPadding},a.update=function(e,t){a.doMath(),u||(e<a.currentSlide?a.currentSlide+=1:e<=a.currentSlide&&0!==e&&(a.currentSlide-=1),a.animatingTo=a.currentSlide),a.vars.controlNav&&!a.manualControls&&("add"===t&&!u||a.pagingCount>a.controlNav.length?m.controlNav.update("add"):("remove"===t&&!u||a.pagingCount<a.controlNav.length)&&(u&&a.currentSlide>a.last&&(a.currentSlide-=1,a.animatingTo-=1),m.controlNav.update("remove",a.last))),a.vars.directionNav&&m.directionNav.update()},a.addSlide=function(e,t){var n=$(e);a.count+=1,a.last=a.count-1,c&&d?void 0!==t?a.slides.eq(a.count-t).after(n):a.container.prepend(n):void 0!==t?a.slides.eq(t).before(n):a.container.append(n),a.update(t,"add"),a.slides=$(a.vars.selector+":not(.clone)",a),a.setup(),a.vars.added(a)},a.removeSlide=function(e){var t=isNaN(e)?a.slides.index($(e)):e;a.count-=1,a.last=a.count-1,isNaN(e)?$(e,a.slides).remove():c&&d?a.slides.eq(a.last).remove():a.slides.eq(e).remove(),a.doMath(),a.update(t,"remove"),a.slides=$(a.vars.selector+":not(.clone)",a),a.setup(),a.vars.removed(a)},m.init()},$(window).blur(function(e){focused=!1}).focus(function(e){focused=!0}),$.flexslider.defaults={namespace:"flex-",selector:".slides > li",animation:"fade",easing:"swing",direction:"horizontal",reverse:!1,animationLoop:!0,smoothHeight:!1,startAt:0,slideshow:!0,slideshowSpeed:7e3,animationSpeed:600,initDelay:0,randomize:!1,fadeFirstSlide:!0,thumbCaptions:!1,pauseOnAction:!0,pauseOnHover:!1,pauseInvisible:!0,useCSS:!0,touch:!0,video:!1,controlNav:!0,directionNav:!0,prevText:"Previous",nextText:"Next",keyboard:!0,multipleKeyboard:!1,mousewheel:!1,pausePlay:!1,pauseText:"Pause",playText:"Play",controlsContainer:"",manualControls:"",customDirectionNav:"",sync:"",asNavFor:"",itemWidth:0,itemMargin:0,minItems:1,maxItems:0,move:0,allowOneSlide:!0,start:function(){},before:function(){},after:function(){},end:function(){},added:function(){},removed:function(){},init:function(){}},$.fn.flexslider=function(e){if(void 0===e&&(e={}),"object"==typeof e)return this.each(function(){var t=$(this),a=e.selector?e.selector:".slides > li",n=t.find(a);1===n.length&&e.allowOneSlide===!0||0===n.length?(n.fadeIn(400),e.start&&e.start(t)):void 0===t.data("flexslider")&&new $.flexslider(this,e)});var t=$(this).data("flexslider");switch(e){case"play":t.play();break;case"pause":t.pause();break;case"stop":t.stop();break;case"next":t.flexAnimate(t.getTarget("next"),!0);break;case"prev":case"previous":t.flexAnimate(t.getTarget("prev"),!0);break;default:"number"==typeof e&&t.flexAnimate(e,!0)}}}(jQuery);
//FitVids
!function(t){"use strict";t.fn.fitVids=function(e){var i={customSelector:null,ignore:null};if(!document.getElementById("fit-vids-style")){var r=document.head||document.getElementsByTagName("head")[0],a=".fluid-width-video-wrapper{width:100%;position:relative;padding:0;}.fluid-width-video-wrapper iframe,.fluid-width-video-wrapper object,.fluid-width-video-wrapper embed {position:absolute;top:0;left:0;width:100%;height:100%;}",o=document.createElement("div");o.innerHTML='<p>x</p><style id="fit-vids-style">'+a+"</style>",r.appendChild(o.childNodes[1])}return e&&t.extend(i,e),this.each(function(){var e=['iframe[src*="player.vimeo.com"]','iframe[src*="youtube.com"]','iframe[src*="youtube-nocookie.com"]','iframe[src*="kickstarter.com"][src*="video.html"]',"iframe[src*='dailymotion.com']","object","embed"];i.customSelector&&e.push(i.customSelector);var r=".fitvidsignore";i.ignore&&(r=r+", "+i.ignore);var a=t(this).find(e.join(","));a=a.not("object object"),a=a.not(r),a.each(function(){var e=t(this);if(!(e.parents(r).length>0||"embed"===this.tagName.toLowerCase()&&e.parent("object").length||e.parent(".fluid-width-video-wrapper").length)){e.css("height")||e.css("width")||!isNaN(e.attr("height"))&&!isNaN(e.attr("width"))||(e.attr("height",9),e.attr("width",16));var i="object"===this.tagName.toLowerCase()||e.attr("height")&&!isNaN(parseInt(e.attr("height"),10))?parseInt(e.attr("height"),10):e.height(),a=isNaN(parseInt(e.attr("width"),10))?e.width():parseInt(e.attr("width"),10),o=i/a;if(!e.attr("name")){var d="fitvid"+t.fn.fitVids._count;e.attr("name",d),t.fn.fitVids._count++}e.wrap('<div class="fluid-width-video-wrapper"></div>').parent(".fluid-width-video-wrapper").css("padding-top",100*o+"%"),e.removeAttr("height").removeAttr("width")}})})},t.fn.fitVids._count=0}(window.jQuery||window.Zepto);
//Images Loaded
(function(c,n){var l="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///ywAAAAAAQABAAACAUwAOw==";c.fn.imagesLoaded=function(f){function m(){var b=c(i),a=c(h);d&&(h.length?d.reject(e,b,a):d.resolve(e));c.isFunction(f)&&f.call(g,e,b,a)}function j(b,a){b.src===l||-1!==c.inArray(b,k)||(k.push(b),a?h.push(b):i.push(b),c.data(b,"imagesLoaded",{isBroken:a,src:b.src}),o&&d.notifyWith(c(b),[a,e,c(i),c(h)]),e.length===k.length&&(setTimeout(m),e.unbind(".imagesLoaded")))}var g=this,d=c.isFunction(c.Deferred)?c.Deferred():0,o=c.isFunction(d.notify),e=g.find("img").add(g.filter("img")),k=[],i=[],h=[];c.isPlainObject(f)&&c.each(f,function(b,a){if("callback"===b)f=a;else if(d)d[b](a)});e.length?e.bind("load.imagesLoaded error.imagesLoaded",function(b){j(b.target,"error"===b.type)}).each(function(b,a){var d=a.src,e=c.data(a,"imagesLoaded");if(e&&e.src===d)j(a,e.isBroken);else if(a.complete&&a.naturalWidth!==n)j(a,0===a.naturalWidth||0===a.naturalHeight);else if(a.readyState||a.complete)a.src=l,a.src=d}):m();return d?d.promise(g):g}})(jQuery);
//Sticky Sidebars
!function(i){i.fn.theiaStickySidebar=function(t){var o={containerSelector:"",additionalMarginTop:0,additionalMarginBottom:0,updateSidebarHeight:!0,minWidth:0};t=i.extend(o,t),t.additionalMarginTop=parseInt(t.additionalMarginTop)||0,t.additionalMarginBottom=parseInt(t.additionalMarginBottom)||0,this.each(function(){function o(){e.fixedScrollTop=0,e.sidebar.css({"min-height":"1px"}),e.stickySidebar.css({position:"static",width:""})}function a(t){var o=t.height();return t.children().each(function(){o=Math.max(o,i(this).height())}),o}var e={};e.sidebar=i(this),e.options=t||{},e.container=i(e.options.containerSelector),0==e.container.size()&&(e.container=e.sidebar.parent()),e.sidebar.css({position:"relative",overflow:"visible","-webkit-box-sizing":"border-box","-moz-box-sizing":"border-box","box-sizing":"border-box"}),e.stickySidebar=e.sidebar.find(".theiaStickySidebar"),0==e.stickySidebar.length&&(e.sidebar.find("script").remove(),e.stickySidebar=i("<div>").addClass("theiaStickySidebar").append(e.sidebar.children()),e.sidebar.append(e.stickySidebar)),e.marginTop=parseInt(e.sidebar.css("margin-top")),e.marginBottom=parseInt(e.sidebar.css("margin-bottom")),e.paddingTop=parseInt(e.sidebar.css("padding-top")),e.paddingBottom=parseInt(e.sidebar.css("padding-bottom"));var d=e.stickySidebar.offset().top,r=e.stickySidebar.outerHeight();e.stickySidebar.css("padding-top",1),e.stickySidebar.css("padding-bottom",1),d-=e.stickySidebar.offset().top,r=e.stickySidebar.outerHeight()-r-d,0==d?(e.stickySidebar.css("padding-top",0),e.stickySidebarPaddingTop=0):e.stickySidebarPaddingTop=1,0==r?(e.stickySidebar.css("padding-bottom",0),e.stickySidebarPaddingBottom=0):e.stickySidebarPaddingBottom=1,e.previousScrollTop=null,e.fixedScrollTop=0,o(),e.onScroll=function(e){if(e.stickySidebar.is(":visible")){if(i("body").width()<e.options.minWidth)return void o();if(e.sidebar.outerWidth(!0)+50>e.container.width())return void o();var d=i(document).scrollTop(),r="static";if(d>=e.container.offset().top+(e.paddingTop+e.marginTop-e.options.additionalMarginTop)){var n,s=e.paddingTop+e.marginTop+t.additionalMarginTop,c=e.paddingBottom+e.marginBottom+t.additionalMarginBottom,p=e.container.offset().top,b=e.container.offset().top+a(e.container),g=0+t.additionalMarginTop,l=e.stickySidebar.outerHeight()+s+c<i(window).height();n=l?g+e.stickySidebar.outerHeight():i(window).height()-e.marginBottom-e.paddingBottom-t.additionalMarginBottom;var f=p-d+e.paddingTop+e.marginTop,S=b-d-e.paddingBottom-e.marginBottom,h=e.stickySidebar.offset().top-d,m=e.previousScrollTop-d;"fixed"==e.stickySidebar.css("position")&&(h+=m),h=m>0?Math.min(h,g):Math.max(h,n-e.stickySidebar.outerHeight()),h=Math.max(h,f),h=Math.min(h,S-e.stickySidebar.outerHeight());var u=e.container.height()==e.stickySidebar.outerHeight();r=(u||h!=g)&&(u||h!=n-e.stickySidebar.outerHeight())?d+h-e.sidebar.offset().top-e.paddingTop<=t.additionalMarginTop?"static":"absolute":"fixed"}if("fixed"==r)e.stickySidebar.css({position:"fixed",width:e.sidebar.width(),top:h,left:e.sidebar.offset().left+parseInt(e.sidebar.css("padding-left"))});else if("absolute"==r){var y={};"absolute"!=e.stickySidebar.css("position")&&(y.position="absolute",y.top=d+h-e.sidebar.offset().top-e.stickySidebarPaddingTop-e.stickySidebarPaddingBottom),y.width=e.sidebar.width(),y.left="",e.stickySidebar.css(y)}else"static"==r&&o();"static"!=r&&1==e.options.updateSidebarHeight&&e.sidebar.css({"min-height":e.stickySidebar.outerHeight()+e.stickySidebar.offset().top-e.sidebar.offset().top+e.paddingBottom}),e.previousScrollTop=d}},e.onScroll(e),i(document).scroll(function(i){return function(){i.onScroll(i)}}(e)),i(window).resize(function(i){return function(){i.stickySidebar.css({position:"static"}),i.onScroll(i)}}(e))})}}(jQuery);
