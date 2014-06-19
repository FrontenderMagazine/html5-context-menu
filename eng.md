![Firefox Context Menu][1]
One of the hidden gems within the [HTML5 spec is context menus][2]. The HTML5
context menu spec allows developers to create custom context menus for given 
blocks within simple menu and menuitem elements. The menu information lives 
right within the page so there's no need to[create a custom plugin][3]. Let me
show you how you can create your own custom context menus from basic HTML!

## The HTML

Let's first start by defining a block of HTML and assigning the ID of the menu
nodes to be used:

    <section contextmenu="mymenu">
    	<!-- 
    		For the purpose of cleanliness, 
    		I'll put my menu inside the element that will use it 
    	-->
    </section>
    

With the block defined, now it's time to create the additional context menu
items for the given block:

    <menu type="context" id="mymenu">
    	<menuitem label="Refresh Post" onclick="window.location.reload();" icon="/images/refresh-icon.png"></menuitem>
    	<menuitem label="Skip to Comments" onclick="window.location='#comments';" icon="/images/comment_icon.gif"></menuitem>
    	<menu label="Share on..." icon="/images/share_icon.gif">
    		<menuitem label="Twitter" icon="/images/twitter_icon.gif" onclick="goTo('//twitter.com/intent/tweet?text=' + document.title + ':  ' + window.location.href);"></menuitem>
    		<menuitem label="Facebook" icon="/images/facebook_icon16x16.gif" onclick="goTo('//facebook.com/sharer/sharer.php?u=' + window.location.href);"></menuitem>
    	</menu>
    </menu>
    

With a base menu tag with the type of context and id to match the `context`
attribute for the blog it's to be used for, menu items or submenus may be 
created. Menu items may have`label`, `icon`, and `onclick` attributes to
represent design and actions. Actions can have predefined functions or inline 
javascript code, just as any element can. Multiple parents can use the same menu,
so no need to repeat the same menus.

*This is where I'd insert more detail, but this is so damn easy that there's no
point in boring you.
..*

Mozilla Firefox is currently the only browser to support this API. I wouldn't
consider adding context menus a critical necessity but the ability to do so is 
quite nice, and I plan to add them to my blog soon. This API is the epitome of "
used for enhancement and wont harm". My "share" example is fairly basic and 
supplemental; have an scenario which the contextmenu API may be more useful? 
Share!

 [1]: img/firefox-contextmenu.png

 [2]: http://www.whatwg.org/specs/web-apps/current-work/multipage/interactive-elements.html#context-menus
 [3]: http://davidwalsh.name/firefox-toolbar