原插件存在bug, 刷新页面才能生效。需要将事件绑定的page.change事件上。对plugin.js做了修改:

```javascript
require(["gitbook", "jQuery"], function(gitbook, $) {
  gitbook.events.bind("page.change", function() {
    [].slice.call(document.querySelectorAll('table')).forEach(function(el){
        var wrapper = document.createElement('div');
        wrapper.className = 'table-area';
        el.parentNode.insertBefore(wrapper, el);
        el.parentNode.removeChild(el);
        wrapper.appendChild(el);
    });
  });
});
```

## 使用方法

修改book.json的plugins，增加数组项："auto-scroll-table@git+https://github.com/ideamean/gitbook-plugin-auto-scroll-table.git"


