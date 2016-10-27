# [转] iOS 9 默认禁用 HTTP 的解决办法
升级了 Apple 推出了 iOS 9.1 beta ，并且配合推出了 Xcode 7.1 beta，在 iOS 9 中默认是不支持 HTTP 的。
  
运行 http 连接程序会提示

```
Transport security has blocked a cleartext HTTP (http://) resource load since it is insecure. Temporary exceptions can be configured via your app's Info.plist file.
```


本来这是好事儿，但是鉴于特殊国情，还是得支持HTTP啊。
  
按照提示其实只要在 Info.plist 添加

```
<key>NSAppTransportSecurity</key>
<dict>
  <!--Include to allow all connections (DANGER)-->
  <key>NSAllowsArbitraryLoads</key>
      <true/>
</dict>
```

即可，还可以指定域名。

```
<key>NSAppTransportSecurity</key>
<dict>
  <key>NSExceptionDomains</key>
  <dict>
    <key>yourserver.com</key>
    <dict>
      <!--Include to allow subdomains-->
      <key>NSIncludesSubdomains</key>
      <true/>
      <!--Include to allow HTTP requests-->
      <key>NSTemporaryExceptionAllowsInsecureHTTPLoads</key>
      <true/>
      <!--Include to specify minimum TLS version-->
      <key>NSTemporaryExceptionMinimumTLSVersion</key>
      <string>TLSv1.1</string>
    </dict>
  </dict>
</dict>
```



