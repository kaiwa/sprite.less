sprite.less
===========

LESS image sprite mixin for maintaining sprite definitions in a single location.


Basically, it works this way: You define a custom sprite pseudo-class which takes either the _sprite item position_ or the _sprite item name_ as argument for every sprite. The argument will be passed to the .sprite mixin together with some custom sprite "configuration"-stuff. Then the mixin is doing it's job and calculates the offsets and applies some CSS styles.

What's the benefit? You don't have to copy & paste nearly the same code (usually only the offsets do change) for every usage of your sprite. Instead you can do an easy-readable .myIconSprite('fancyInfoIcon').. for example.

!!! !!!

Experimental, it's just an idea for my personal use. But feel free to clone, do-what-ever-you-like-to-do-license.

!!! !!!

Import
------

	@import 'sprite.less';

Create your sprite
------------------

Example is based on a 16 px wide, vertical sprite.

### 2.1 By name

This way you will create a sprite with named items which has two advantages:
  1. When addressing the items with their names your CSS might be easier to understand
  2. If (can't imagine such case.. but..) the position of an item changes within the sprite, you need to adjust that only in the sprite definition, not everywhere across your code
```
     .socialNetworkSprite(@item) {
         /* Define name and position in sprite */
         @items: '{"twitter": 1, "facebook": 2, "google": 3, "skype": 4 }';
         .sprite('../images/mySprite.png', 16px, @item, @items);
     }
```
### 2.2 By number

If it is too much work for you to name every single sprite item, simply omit the names. In this case you will address the sprite items by their positions in the sprite.

    .socialNetworkSprite(@item) {
        .sprite('../images/mySprite.png', 16px, @item);
    }

Use your sprite
---------------

### By name

Addressing the sprite items by their names:

    #socialNetwork li#twitter a { .socialNetworkSprite('twitter') }
    #socialNetwork li#facebook a { .socialNetworkSprite('facebook') }
    ...

### By number

Addressing the sprite items by their position:

    #socialNetwork li#twitter a { .socialNetworkSprite(1) }
    #socialNetwork li#facebook a { .socialNetworkSprite(2) }
    ...

Output
------

    #socialNetwork li#twitter a{background:url("../images/mySprite.png") 0px 0px no-repeat;background-position:0 0px;}
    #socialNetwork li#facebook a{background:url("../images/mySprite.png") 0px 0px no-repeat;background-position:0 -16px;}
