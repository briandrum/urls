# Interaction patterns

Six years after Kyle Neath wrote about [URL Design](http://warpspire.com/posts/url-design) it still seems common for teams to struggle with this fundamental aspect of the web. The popularity of JavaScript and single-page applications has compounded the issue by making URLs entirely optional in some cases. Yet I believe URLs – and the proper markup to make use of them – is more important than ever. [Ed: evidence?] This article is an attempt to articulate my thought process when designing and implementing URLs schemes. The same principles hold true whether you are building a static web site or a single-page application.

## Linking to pages
The most common use case and one of the defining characteristics of the web. Link to a web page or application view using a URL and `a` tag. Creates a new entry in the browser history and can be revisited using the browser’s “Back” button.

#### Examples
* [Primary navigation](//briandrum.github.io/urls/examples/navigation)
* [Tabbed content requiring a trip to the server](//briandrum.github.io/urls/examples/tabs-1)

## Linking to content within the current page
Link to a sub-state of a view in the application using a URL and `a`tag  with a fragment identifier `#settings`. Creates a new entry in the browser history (unless overridden with `onReplaceState`) and can be revisited using the browser’s “Back” button.

#### Examples
* [Links to anchors](//briandrum.github.io/urls/examples/anchors)
* [Tabbed content already in page source](//briandrum.github.io/urls/examples/tabs-2)

## Modifying page state
Use optional query strings. The page should still render without them. Use `onReplaceState` to udpate without creating a new entry in the browser history.

#### Examples
* sorting and filtering
* table or chart view

## Submitting a form
Use `form` and `button` tags. Make sure the result of your `GET` or `POST` operation is a URL that can be revisited to see the outcome of that submission.

#### Examples
* 
* 

## Interacting with page elements
No entry in browser history. If a fallback URL exists, use an anchor tag `a` and override the default behavior with JavaScript. If no fallback URL exists, use a `button` tag.

#### Examples
* Dropdowns

# Why bother

Article started after requests for `cursor:pointer` on all interactive elements. Doing this encourages anti-patterns like:

1. using the wrong tag (`li` with click handlers for navigation)
2. not providing the proper affordance signifiers (like `:hover` and `:focus` states) on interactive elements like `button`

By not giving your views distinct URLs, you’re robbing users of expected functionality (afforandances) like sharing and bookmarking, browser Back button, open link in new tab, etc. 
By not using the most appropriate markup (`a` or `button`) you're missing out on built-in signifiers like `:hover`, `:focus`, and `cursor` states, some of which are critical for those dependant on assistive technology.

Using a band-aid like `cursor: pointer` just confuses the issue.

## Further reading
* [Kyle Neath: URL Design](http://warpspire.com/posts/url-design)
* [Wikipedia: Semantic URL](https://en.wikipedia.org/wiki/Semantic_URL)
* [24 Ways: How Tabs Should Work](https://24ways.org/2015/how-tabs-should-work)
* [Adam Silver: Buttons shouldn’t have a hand cursor
](https://medium.com/simple-human/buttons-shouldnt-have-a-hand-cursor-b11e99ca374b)

**See that little green heart down on the left?** It's a `button` element with no `:focus` or `:hover` states, opting instead for `cursor: pointer`. Don't do that. But do give it a tap if you enjoyed this article.
