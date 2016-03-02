[![Travis](https://img.shields.io/travis/nabble/unveil2.svg)](https://travis-ci.org/nabble/unveil2)
[![Code Climate](https://img.shields.io/codeclimate/github/nabble/unveil2.svg)](https://codeclimate.com/github/nabble/unveil2)
[![npm](https://img.shields.io/npm/v/unveil2.svg)](https://www.npmjs.com/package/unveil2)

# unveil2.js

> __A very lightweight plugin to lazy load images for jQuery or Zepto.js__  
> Based on [luis-almeida/unveil](https://github.com/luis-almeida/unveil).

## Getting started

Install unveil2.js by downloading a copy of [`jquery.unveil2.min.js`](https://raw.githubusercontent.com/nabble/unveil2/develop/dist/jquery.unveil2.min.js) and add it to your page after [jQuery](http://jquery.com) or [Zepto](http://zeptojs.com):

```html
<script src="//code.jquery.com/jquery-2.1.4.min.js"></script>
<script src="jquery.unveil2.min.js"></script>
```

And call the unveil plugin on the images you want to be lazily loaded:

```js
$('img').unveil();
```

__Note:__ If you load scripts at the bottom of the page, [you don't have to wait for `$.ready`](http://stackoverflow.com/a/9558601/938297).

[That's all folks](https://www.youtube.com/watch?v=gBzJGckMYO4)!

## Examples

[See our online examples](http://nabble.github.io/unveil2/docs/index.html)

## More options

For a complete list of options, see [API section](http://nabble.github.io/unveil2/docs/api.html).

### Retina images

Unveil2 can replace images with a retina variant if it detects a high DPI screen. Define a retina image as follows:

```html
<img src="image.png" data-src="image.png|image@2x.png" />
```

### Placeholder images

To replace images with a placeholder once they're not yet loaded, use the `data-src-placeholder` attribute:

```html
<img src="image.png" data-src-placeholder="placeholder.png" />
```

__Note:__ Don't replace the original image in the `src` attribute with a placeholder image, since this will potentially mess with bots, scrapers and JavaScript disabled browsers. Unveil2 will tell the browser to stop loading the original image so it won't slow down the loading of the page.

### CSS background images

Unveil2 can lazy laod CSS background images:

```html
<header data-src="bg.png|bg@2x.png" />
<script>
$('header').unveil();
</script>
```

### Breakpoints

Specify larger images to be used on larger screen-widths by adding attributes and passing an array of breakpoints when invoking unveil2, for a true mobile-first experience :)

```html
<img src="small.png" data-src-md="medium.png" />
<script>
$('img').unveil({
    breakpoints: [{
        minWidth: 768,
        attribute: 'data-src-md'
    }]
});
</script>
```

### Advanced example

```html
<img src="http://loremflickr.com/450/300"
    data-src="http://loremflickr.com/450/300|http://loremflickr.com/900/600"
    data-src-md="http://loremflickr.com/750/500|http://loremflickr.com/1500/1000"
    data-src-lg="http://loremflickr.com/1050/700|http://loremflickr.com/2100/1400"
    />
<script src="//code.jquery.com/jquery-2.1.4.min.js"></script>
<script src="jquery.unveil2.min.js"></script>
<script>
$('img').unveil({
    offset: 100,
    throttle: 200,
    placeholder: 'http://placehold.it/500x300'
    loaded: function () {
        console.log('Unveiled', this);
    },
    breakpoints: [
        {
            minWidth: 768,
            attribute: 'data-src-md'
        },
        {
            minWidth: 1200,
            attribute: 'data-src-lg'
        }
    ],
    debug: true
});
</script>
```

## API

See [API documentation](http://nabble.github.io/unveil2/docs/api.html)

## License

[MIT](http://opensource.org/licenses/MIT)