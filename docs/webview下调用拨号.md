框架 f7 + vue

```html
<a :href="'tel:12321'" class="external">12321</a>
```

> https://github.com/framework7io/Framework7/issues/48
f7对```a```标签下的uri做了封装，需加上```class="external"```用来区分

> https://stackoverflow.com/questions/31913895/phone-link-in-html-for-ios-and-android
在ios下及安卓浏览器下可以正常调起拨号
在安卓webview下是跳页面，所以需要webview封装一个ShouldOverrideUrlLoading的方法
