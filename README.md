sprite.less
===========

LESS image sprite mixin for maintaining sprite definitions in a single location.
Experimental, for my personal use...

Import
------

	@import 'sprite.less';

Create your sprite
------------------

Example is based on a 16 px wide, vertical sprite.

### 2.1 By name
    .mySprite(@item) {
        /* Define name and position in sprite */
        @items: '{"twitter": 1, "facebook": 2, "google": 3, "skype": 4 }';
        .sprite('../images/mySprite.png', 16px, @item, @items);
    }

### 2.2 By number

    .mySprite(@item) {
        .sprite('../images/mySprite.png', 16px, @item);
    }

Use your sprite
---------------

### By name

    #socialNetwork li#twitter a { .mySprite('twitter') }
    #socialNetwork li#facebook a { .mySprite('facebook') }
    ...

### By number

    #socialNetwork li#twitter a { .mySprite(1) }
    #socialNetwork li#facebook a { .mySprite(2) }
    ...

Output
------

    #socialNetwork li#twitter a{background:url("../images/mySprite.png") 0px 0px no-repeat;background-position:0 0px;}
    #socialNetwork li#facebook a{background:url("../images/mySprite.png") 0px 0px no-repeat;background-position:0 -16px;}
