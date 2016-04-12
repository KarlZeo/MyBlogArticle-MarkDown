---
id: 48
title: iOS 9 默认禁用 HTTP 的解决办法
date: 2016-02-19T21:39:59+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=48
permalink: /2016/02/19/ios-solution-9-http-is-disabled-by-default/
dsq_thread_id:
  - 4679555453
views:
  - 5
categories:
  - iOS 编程
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

升级了 Apple 推出了 iOS 9.1 beta ，并且配合推出了 Xcode 7.1 beta，在 iOS 9 中默认是不支持 HTTP 的。
  
运行 http 连接程序会提示

<pre class="prettyprint" ><code>Transport security has blocked a cleartext HTTP (http://) resource load since it is insecure. Temporary exceptions can be configured via your app's Info.plist file.
</code></pre>

本来这是好事儿，但是鉴于特殊国情，还是得支持HTTP啊。
  
按照提示其实只要在 Info.plist 添加

<pre class="lang:xhtml decode:true">&lt;key&gt;NSAppTransportSecurity&lt;/key&gt;
&lt;dict&gt;
  &lt;!--Include to allow all connections (DANGER)--&gt;
  &lt;key&gt;NSAllowsArbitraryLoads&lt;/key&gt;
      &lt;true/&gt;
&lt;/dict&gt;</pre>

即可，还可以指定域名。

<pre class="lang:xhtml decode:true ">&lt;key&gt;NSAppTransportSecurity&lt;/key&gt;
&lt;dict&gt;
  &lt;key&gt;NSExceptionDomains&lt;/key&gt;
  &lt;dict&gt;
    &lt;key&gt;yourserver.com&lt;/key&gt;
    &lt;dict&gt;
      &lt;!--Include to allow subdomains--&gt;
      &lt;key&gt;NSIncludesSubdomains&lt;/key&gt;
      &lt;true/&gt;
      &lt;!--Include to allow HTTP requests--&gt;
      &lt;key&gt;NSTemporaryExceptionAllowsInsecureHTTPLoads&lt;/key&gt;
      &lt;true/&gt;
      &lt;!--Include to specify minimum TLS version--&gt;
      &lt;key&gt;NSTemporaryExceptionMinimumTLSVersion&lt;/key&gt;
      &lt;string&gt;TLSv1.1&lt;/string&gt;
    &lt;/dict&gt;
  &lt;/dict&gt;
&lt;/dict&gt;</pre>

&nbsp;

<!--wp-compress-html no compression-->

<!--wp-compress-html-->