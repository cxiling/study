浏览器提供了一些安全相关的响应头，使用这些响应头一般只需要修改服务器配置即可，不需要修改程序代码。

###1. Strict-Transport-Security

它允许一个HTTPS网站，要求浏览器总是通过HTTPS来访问它。
>strict-transport-security: max-age=16070400; includeSubDomains

###2. X-Frame-Options
减少点击劫持。
>x-frame-options: SAMEORIGIN

- DENY：不允许被任何页面嵌入；
- SAMEORIGIN：不允许被本域以外的页面嵌入；
- ALLOW-FROM uri：不允许被指定的域名以外的页面嵌入（Chrome现阶段不支持）；

###3. X-XSS-Protection

防范XSS。
浏览器提供的XSS保护机制并不完美，但是开启后仍然可以提升攻击难度，总之没有特别的理由，不要关闭它。
>x-xss-protection: 1; mode=block

- 0：禁用XSS保护；
- 1：启用XSS保护；
- 1; mode=block：启用XSS保护，并在检查到XSS攻击时，停止渲染页面（例如IE8中，检查到攻击时，整个页面会被一个#替换）；

###4. X-Content-Type-Options
这个响应头可以禁用浏览器的类型猜测行为。

想象这样一个攻击场景：某网站允许用户在评论里上传图片，攻击者在上传图片的时候，看似提交的是个图片文件，实则是个含有JavaScript的脚本文件。该文件逃过了文件类型校验（这涉及到了恶意文件上传这个常见安全问题，但是由于和前端相关度不高因此暂不详细介绍），在服务器里存储了下来。接下来，受害者在访问这段评论的时候，浏览器会去请求这个伪装成图片的JavaScript脚本，而此时如果浏览器错误的推断了这个响应的内容类型（MIME types），那么就会把这个图片文件当做JavaScript脚本执行，于是攻击也就成功了。
>X-Content-Type-Options: nosniff

###5. X-Content-Security-Policy
>Content-Security-Policy: default-src 'self'

```default-src``` 是 CSP 指令，多个指令之间用英文分号分割；```'self'``` 是指令值，多个指令值用英文空格分割。
https://imququ.com/post/content-security-policy-reference.html