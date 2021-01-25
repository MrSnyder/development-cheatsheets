# Javascript Basics

## Execution model (browser)

[What the heck is the event loop anyway?](https://www.youtube.com/watch?v=8aGhZQkoFbQ&t=710s)

* Event loop: JS is single-threaded: This thread executes the event loop and checks the task queue
* WebAPIs: Asynchronous calls use WebAPIs (Ajax, etc) to perform something as a background task
* Task queue: Finished background tasks add callback to the task queue

## JQuery

```js
$(function () {
    // execute on DOM ready: shorthand for $( document ).ready()
}


$('#mapcontext_tree')
$('#mapcontext_tree a[class=jstree-anchor]').each(function() {
    console.log(this);?
});
$('#mapcontext_tree a[class=jstree-anchor]').after('<button type="button" class="button btn-primary btn-sm">X</button>');
$('#mapcontext_tree button').click(function() {
   let nodeId = $(this).parent()[0].id;
   let inst = $('#mapcontext_tree').jstree(true);
   let node = inst.get_node(nodeId);
   inst.delete_node(node);
});
```
