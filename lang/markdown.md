# Markdown Cheat Sheet  
Note: found this once online and adapted it slightly...



## Headings

Headings from `h1` through `h6` are constructed with a `#` for each level:

``` markdown
# h1 Heading
## h2 Heading
### h3 Heading
#### h4 Heading
##### h5 Heading
###### h6 Heading
```



## Horizontal Boundaries

boundary element:

* `___`: three underscores, or
* `---`: three dashes, or
* `***`: three sterisks




## Emphasis

### Bold

``` markdown
**rendered as bold text**
```

### Italics

``` markdown
_rendered as italicized text_
```

### strikethrough

``` markdown
~~Strike through this text.~~
```

## Blockquotes



``` markdown
Add `>` before any text you want to quote. 
```

Example:  

> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.

Note: Use several `>` for nesting


## Lists

### Unordered

```markdown
* valid bullet
- valid bullet
+ valid bullet
```

Example with sublists: 

``` markdown
+ Lorem ipsum dolor sit amet
+ Consectetur adipiscing elit
+ Integer molestie lorem at massa
+ Facilisis in pretium nisl aliquet
+ Nulla volutpat aliquam velit
  - Phasellus iaculis neque
  - Purus sodales ultricies
  - Vestibulum laoreet porttitor sem
  - Ac tristique libero volutpat at
+ Faucibus porta lacus fringilla vel
+ Aenean sit amet erat nunc
+ Eget porttitor lorem
```

### Ordered


``` markdown
1. Lorem ipsum dolor sit amet
2. Consectetur adipiscing elit
3. Integer molestie lorem at massa
4. Facilisis in pretium nisl aliquet
5. Nulla volutpat aliquam velit
6. Faucibus porta lacus fringilla vel
7. Aenean sit amet erat nunc
8. Eget porttitor lorem
```

**Pro Tip**: Also possible to use `1.` for each item, as Github will enumerate automatically.  

## Code

### Inline code
Wrap inline snippets of code with `` ` ``.


### Indented code

Or indent several lines of code by at least four spaces, as in:

``` js
    // Some comments
    line 1 of code
    line 2 of code
    line 3 of code
```

### Block code "fences"

Use "fences"  ```` ``` ```` to block in multiple lines of code. 


### Syntax highlighting

Github Flavoured Markdown supportes syntax highlighting. Just add the name of the language behind the fence of your code block

## Tables

Use Pipes for cells and Dashes for headers. Need not be vertically aligned (even though code looks much nicer then..)

``` markdown
| Option | Description |
| ------ | ----------- |
| pizza  | A programmer's delight |
| burger | cardiac arrest, here I come |
| banana | a healthy option for the educated |
```



## Links

### Basic link

``` markdown
[google](http://www.google.com)
```


### Hover Tooltip Link

``` markdown
[google](http://www.google.com "Search for Something")
```


### Table of Contents

```markdown
# Table of Contents
  * [Chapter 1](#chapter-1)
  * [Chapter 2](#chapter-2)
  * [Chapter 3](#chapter-3)
```
will be linked to 

```markdown
## Chapter 1 <a id="chapter-1"></a>
Content for chapter one.

## Chapter 2 <a id="chapter-2"></a>
Content for chapter one.

## Chapter 3 <a id="chapter-3"></a>
Content for chapter one.
```


## Images
same as links but with exclamation mark.

``` markdown
![myimage](urltoimagegoeshere)
```

