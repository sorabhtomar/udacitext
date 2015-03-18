<h1><u>Web Components Overview</u></h1>

<img src="/images/web-components-1.png" width="260" height="194">

Web Components are at the bleeding edge of web development, they provide
modular, shareable, and customizable HTML elements that users can define. Web
Components incorporate a set of polyfills (in this case the code that provides
the technology you will be utilizing for creating web components). These
polyfills will eventually become natively supported in browsers as web
components become the norm but until then you will need to utilize the
webcomponent.js file that is provided to use web components. <i>(Note Chrome
36+ has fully implemented these polyfills!).</i>

<h2><u>So What are Web Components Exactly?</u></h2>

Web components is a broader term for a set of specifications that allow you,
the developer, to create custom elements, utilize html imports, utilize
templates without a templating engine, and make use of the shadow DOM.

<h2><u>Custom Elements</u></h2>

The first noticeable thing that anyone will tell you about web components is
how awesome it is to be able to define and reuse custom DOM elements. This
means that you will be able to bundle up styling, script, and structure into an
HTML tag and reuse that tag in your project. For example if we take a look at
[this sample project provided][1] by Polymer’s development team and explore the
source code in our developer tools.

<img src="/images/web-components-2.png" width="675" height="500">

We notice several DOM elements that are not standard to HTML5. In this case we
see `<topeka-app>`, `<topeka-categories>`, `<core-animated-pages>`, and many
more! You also may notice several attributes that are not common to HTML5 being
used throughout the page. Each of these elements are written and defined in
their own .html files that are then, through the use of web component
specifications, capable of being used anywhere in your app.

Even better, you’ll be able to share your custom elements with others and they
will be able to use your custom built elements in their own projects. There are
already hundreds of custom elements that you can explore at [Custom Elements
IO][2], [Component Kitchen][3], and [Built with Polymer][4].

<h2><u>HTML Imports</u></h2>

HTML imports let you reuse HTML documents in other HTML documents. Similar to
how `<script>` tags let you include external javascript you can include
external HTML by saying `<link rel="import" href="my-custom-element.html">`.
This specifically is how we are able to utilize our custom elements so easily.

<h2><u>Templates</u></h2>

Along with being able to import HTML you can utilize templating to declare
inert DOM subtrees that can be manipulated throughout the document and provide
identical content throughout your page. In the past templating required the use
of an engine like AngularJS, Mustache.js, Handlebars.js, etc.. Now with the new
`<template>` tag included in HTML5, web components make full use of this new
element and improves on the templating that is provided by the aforementioned
frameworks. If your interested in learning more about the `<template>` tag be
sure to read [this article about the template element][5].

<h2><u>Shadow DOM</u></h2>

The Shadow DOM is simply a method of establishing and maintaining boundaries
between DOM trees as well as defining rules for how these trees interact with
each other. The shadow DOM lets an element get a new node associated with them,
i.e. the shadow root. An element with a shadow root is called a shadow host.
The content in the shadow host isn’t rendered, instead the content in the
shadow root is rendered.

For example with the following code:
```html
<button>Hello, World!</button>
<script>
    var host = document.querySelector('button');
    var root = host.createShadowRoot();
    root.textContent = "I'm a robot";
</script>
```
Will result in the following DOM structure
```html
<html>
    <head></head>
    <body>
        <button>
            #shadow-root
                "I'm a robot"
            "Hello, World!"
        </button>
        <script>
            var host = document.querySelector('button');
            var root = host.createShadowRoot();
            root.textContent = "I'm a robot";
        </script>
    </body>
</html>
```

This would render as “I’m a robot” and not as “Hello, World!”. Additionally if
you use JavaScript to get the buttons textContent you’d get “Hello, World!”
because the DOM subtree under the shadow root is encapsulated.

If you’re interested in learning more about the Shadow DOM I highly suggest
reading [this blog post by Dominic Cooney][6]. It sheds some great detail on
what the shadow DOM is doing and how you can utilize it in your web
development.

<h2><u>Libraries for using Web Component Standards</u></h2>

A lot of libraries of predefined web components exist already, some of the most
popular and widely supported ones include [Polymer][7], [Bosonic][8], and
[X-Tag][9]. Each of these make use of the 4 common themes of web components
listed above. However, just like the differences between JavaScript frameworks,
each solves each problem just a little bit differently and approaches web
components in their own fashion.

If you're really interested in learning more about Web Components be sure to
check our [WebComponents.org][10]. They have a lot of great articles and
information about where web components are and where they will be. Also, be
sure to check the discussion boards next week when I'll be sharing a demo on
Polymer and how to make use of Polymer in your own projects!

Talk about this on the forums [here][11]!

[1]: https://polymer-topeka.appspot.com/
[2]: http://customelements.io/
[3]: http://component.kitchen/components
[4]: http://builtwithpolymer.org/elements/
[5]: http://webcomponents.org/articles/introduction-to-template-element/
[6]: http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom/
[7]: https://www.polymer-project.org/
[8]: http://bosonic.github.io/
[9]: http://x-tags.org/
[10]: http://webcomponents.org/
[11]: http://discussions.udacity.com/t/web-components-the-bleeding-edge-of-web-development-mar-15/13734
