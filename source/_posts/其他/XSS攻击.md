---
title: XSS攻击
category: other
---

## XSS



[前端安全系列（一）：如何防止XSS攻击？ - 美团技术团队 (meituan.com)](https://tech.meituan.com/2018/09/27/fe-security.html)

> Cross-Site Scripting（跨站脚本攻击）简称 XSS，是一种代码注入攻击。攻击者通过在目标网站上注入**恶意脚本**，使之在**用户的浏览器上运行**。利用这些恶意脚本，攻击者可获取用户的敏感信息如 Cookie、SessionID 等，进而危害数据安全。
>
> 为了和 CSS 区分，这里把攻击的第一个字母改成了 X，于是叫做 XSS。

#### 可能出现的地方:

> 不仅仅是业务上的“用户的产生的内容”可以进行注入，包括 URL 上的参数等都可以是攻击的来源。在处理输入时，以下内容都不可信：
>
> - 来自用户的 UGC 信息(user-generated content)
> - 来自第三方的链接
> - URL 参数
> - POST 参数
> - Referer （可能来自不可信的来源）
> - Cookie （可能来自其他子域注入）

#### 例子

```html
<input value="" /><button>搜索</button>
<!--
搜索时输入["<script>alert(XSS脚本!)</script>],就会执行XSS
-->
```

```html
<p>
    这里是用户的评论内容
</p>
<textarea value="请输入"></textarea><button>提交评论</button>
<!--
这里面可能没有对用户的输入进行判断,可输入脚本.比如输入:
<img src=1 onerror="alert(1)"/>
-->
```

