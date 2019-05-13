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
    
Try to handle GH flow.
Start to study hot to work with git.
Do some tutorials.

As Kanye West said:
> We're living the future so
> the present is our past.

## Task Lists
- [x] @netcovoiturage, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item


<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
