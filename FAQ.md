#*flow* FAQ

###Can I use double data-binding? How do I bind the model in a *flow* controller? 

Yes. When you set the model in a *flow* controller which is a subclass of `BindingController` you'll have available that model in the template and do things like `{ model. name }` to make the template be rendered with the model's properties. Check the `RivetsJSTestsController` class for more examples.

###How do I compose *flow* controllers?

Controllers can have controllers. See the `StuffController` for an example on how it's done.

###How does *flow* routes? How URL changes map to controllers?
By reacting to the `onhashchange` event and reflecting about its new value. It will ask the `RouteableController` hierarchy to detect who answers `true` to the `isValidFor: anURI` message. If you follow *flow*'s convention, you create a `YourNamedController` subclass of `RouteableController` and it will be rendered when the URI matches `http://flow.dev/YourNamed` (tip: you can manipulate that arbitrarily by changing  `isValidFor: anURI`)

###Can I use the html canvas or I need to use templates?

Whatever you like it better. You can use the 'traditional' canvas or you can use the also 'traditional' templates. 

###How do I change the CSS style in a controller?

Editing the `.css` files found in `frontend/css/`

###How does *flow* persists models in the localStorage?

Using MiniMapless.

###How does flow compare with the other Smalltalk web frameworks already out there like [Seaside](http://seaside.st/) and [Aida](http://www.aidaweb.si/)?
Seaside and Aida are great *full server stack* frameworks. They work with the notion of *pre-render everything from the server* and use the browser to display. 

*flow*, in the other hand, is opinionated on the [separation of concerns](http://en.wikipedia.org/wiki/Separation_of_concerns) regarding front and back ends. That makes it a good fit for [Single Page Applications](http://en.wikipedia.org/wiki/Single-page_application) where the rendering process happens in the web browser itself and generated by the [frontend](http://en.wikipedia.org/wiki/Front_and_back_ends). That's the main difference you'll find with *flow* and **any** *full server stack*. Secondarily, the backend is [RESTful](http://en.wikipedia.org/wiki/Representational_state_transfer) and depending on how you use it, it can be [stateless](http://en.wikipedia.org/wiki/Stateless_protocol).


### Does flow support application localization for languages (e.g., English, Spanish, Russian, Hebrew) as well as language dialects (e.g., American English vs British English)?

### Can *flow* be used for building a CMS (Content Management System)?

Yes. Anything you can think in doing as a [Single Page Applications](http://en.wikipedia.org/wiki/Single-page_application) is a great fit for *flow*.

### Seaside can use [Magritte](https://code.google.com/p/magritte-metamodel/) for modeling. What about *flow*?
The only meta-generation of views available in *flow* is scaffolding. 

*flow* intentionally favours the use of custom microtemplates to leverage designers collaboration. 

###What is scaffolding?

...

###How do a *flow*-based app gets deployed?

In *flow* we have a `grunt watch` task that rebuilds the `public/` directory every time you change any of the frontend's source files. It takes care of `css/`, `img/` and `src` where Amber stores its `.js` and `.st`. 

The `grunt watch` tasks output about Amber sources is to make one ball of js that you'll find in `public/js/the.js` and use in production.

###Is the framework SEO friendly?
Currently, probably not. For now, the advice is to make SEO things with already SEO friendly arctifacts and let *flow* for the app itself. If the app itself needs SEO really bad (like ecommerce or things like that) then that would be a wall to climb. Good news is Google (and friends) eventually will solve that for us but if you need that in a project now, you can use your favorite tool from [any of the listed here](https://www.google.com/search?q=angular+seo&oq=angular+seo&aqs=chrome..69i57j0l5.2531j0j7&sourceid=chrome&es_sm=91&ie=UTF-8#q=angular+seo). Many of them prerender for the bots and are probably adaptable for *flow*.