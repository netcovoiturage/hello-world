# Hello world.
## Hello.
### Hi.

    function getCustomerByName(name){
        return find(name);
    }
    
### test highlighting
    
```javascript
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
``` 
    
## posts
<ul>
  {% for post in site.posts %}
    <li>{{ post.url }}</li> 
    <li>{{ site.url }}</li>
    <li>
      <a href="/hello-world{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

## Task Lists
- [x] @netcovoiturage, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
