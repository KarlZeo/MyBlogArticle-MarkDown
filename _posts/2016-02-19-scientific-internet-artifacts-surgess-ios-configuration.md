---
id: 86
title: iOS科学上网神器 Surge+SS配置
date: 2016-02-19T22:23:24+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=86
permalink: /2016/02/19/scientific-internet-artifacts-surgess-ios-configuration/
dsq_thread_id:
  - 4603522281
views:
  - 57
categories:
  - 黑科技
---
<!--wp-compress-html-->

<!--wp-compress-html no compression--><section class=" section--body section--first"> 

<div class="section-content">
  <div class="section-inner layoutSingleColumn">
    <p id="81d1" class="graf--p graf-after--h3">
      Surge 是基于 iOS 9 的新特性 Network Extension 开发的一款网络调试工具，工作原理是使用 Packet Tunnel Provider 给系统套上一个代理，Surge 有两个主要组件：Surge 代理服务器和 Surge TUN 接口。程序运行之后，Surge 会将自身设置为默认的 HTTP/HTTPS 代理服务器来处理所有的 HTTP/HTTPS 流量。针对一些不服从系统代理设置（如 Mail.app ）的应用程序 ，将由 Surge 的 TUN 接口来进行处理。
    </p>
    
    <p id="51bd" class="graf--p graf-after--p">
      Surge 会接管全局的（几乎）所有通信，所以所有网络方面的电量消耗都会被算在 Surge 头上，实际上 Surge 的运行功耗很少，使用中也不会感到 Surge 对电量有明显影响。
    </p>
    
    <h4 id="3301" class="graf--h4 graf-after--p">
      添加配置文件
    </h4>
    
    <p id="9475" class="graf--p graf-after--h4">
      打开 Surge，默认包含有一个 Default 的配置文件，点击右上角的编辑（Edit）可以打开了解配置文件的基本结构：日志模式（Log Level）的设定、代理服务器（Proxy）的设置以及规则（Rules）的设置。
    </p>
    
    <p id="972a" class="graf--p graf-after--p">
      一条一条添加内容是困难的，而且对刚接触这一块的用户来说也不明所以，所以简单的方法是从网上复制一份现成配置内容下来，保存成后缀为.conf 的文本（Uncode UTF-8）文件，最后连接数据线通过 iTunes 导入到 Surge中。
    </p><figure id="8b00" class="graf--figure graf-after--p"> 
    
    <div class="aspectRatioPlaceholder">
      <img class="graf-image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/425f7925fa04614bf71afe5982e68e9d.png" alt="iOS科学上网神器 Surge+SS配置" title="iOS科学上网神器 Surge+SS配置" alt="" data-image-id="1*A_-U4l3Yphphj10cq1_ikA.png" />
    </div></figure> 
    
    <p id="709a" class="graf--p graf-after--figure">
      配置文件中服务器的部分需要填写，如果不知道服务器的地址和端口是多少，不妨打开 GoagentX 停止服务后选择不同的服务器并查看具体地址，你既可以直接在 Surge 中填写，也可以直接编辑 .conf 配置文件最后再导入到 Surge。
    </p><figure id="8787" class="graf--figure graf-after--p"> 
    
    <div class="aspectRatioPlaceholder">
      <img class="graf-image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/926de82c25e9a57adb5fe16f5d977788.png" alt="iOS科学上网神器 Surge+SS配置" title="iOS科学上网神器 Surge+SS配置" alt="" data-image-id="1*mmILx7hYNXghMt76M3EZAA.png" />
    </div></figure> 
    
    <p id="4d79" class="graf--p graf-after--figure">
      对于大多数人来说，基于范例文件编辑加上自己的服务器（Proxy）地址 Surge 就可以开始工作了。规则部分可以借鉴范例文件进行补充，规则并不是越多越好，除了利用 DNS 缓存对经常访问的网站进行加速外，仅需要补充本地 DNS 无法正常解析的域名到规则中。
    </p>
    
    <blockquote id="4919" class="graf--blockquote graf-after--p">
      <p>
        如果您使用的是 HTTPS 代理，Surge 会校验服务器证书名称，请使用域名进行配置，不要直接使用 IP。
      </p>
    </blockquote>
    
    <h4 id="9d85" class="graf--h4 graf-after--blockquote">
      多个服务器配置（服务器覆盖文件）
    </h4>
    
    <p id="875f" class="graf--p graf-after--h4">
      配置文件的 Proxy 部分可以写入多个服务器地址，Surge 会将当前命名为「Proxy」的地址作为当前使用地址，这种方式每次想切换代理服务器时比较麻烦，例如我想使用香港代理服务器，需要找到 HK 条目，并将现有「 Proxy = 」中的 Proxy 改成别的名字，然后将「 HK = 」中的 HK 改成 Proxy，说起来都比较绕。
    </p>
    
    <p id="0033" class="graf--p graf-after--p">
      多个服务器切换更简单的方式是单独写「服务器配置覆盖文件」，在这种覆盖文件中只需要指向自定义配置的主文件（如图示中HK(HKG3).conf 第一行），然后写上服务器地址的部分（Proxy 定义部分）即可。
    </p><figure id="3de1" class="graf--figure graf-after--p"> 
    
    <div class="aspectRatioPlaceholder is-locked">
      <div class="aspectRatioPlaceholder-fill">
      </div>
      
      <div class="progressiveMedia js-progressiveMedia graf-image is-canvasLoaded is-imageLoaded" data-image-id="1*unvgROde9sdKy3_gCpHlpw.png" data-width="1512" data-height="1002" data-action="zoom" data-action-value="1*unvgROde9sdKy3_gCpHlpw.png" data-scroll="native">
        <canvas class="progressiveMedia-canvas js-progressiveMedia-canvas" width="75" height="47"></canvas><img class="progressiveMedia-image js-progressiveMedia-image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/6de75c9ff5d883c041221f9049f392dd.png" alt="iOS科学上网神器 Surge+SS配置" title="iOS科学上网神器 Surge+SS配置" alt="" data-src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/6de75c9ff5d883c041221f9049f392dd.png" />
      </div>
    </div></figure> 
    
    <blockquote id="15bf" class="graf--blockquote graf-after--figure">
      <p>
        服务器覆盖文件不同于完整的 Main.conf 文件，需要在电脑上编辑并导入 Surge，不支持在 iPhone 里进行编辑。
      </p>
    </blockquote>
    
    <p id="711d" class="graf--p graf-after--blockquote">
      主文件（如，Main.conf）是个独立的标准文件，所以其中 Proxy 部分是必须的，服务器覆盖配置文件（如，HK.conf、TYO.conf）中只写一个服务器地址，并且这个地址不需要和 Main.conf 的中 Proxy 部分形成对应关系，如果你打算使用 5 个服务器切换，Main.conf 的 Proxy 部分可以写 1 ，然后其他覆盖配置文件里分别写 2、3、4、5 的地址，在 Surge 主界面中选中哪个使用哪一个。
    </p>
    
    <p id="44fc" class="graf--p graf-after--p">
      多个服务器配置的方式使用起来更灵活，切换服务器时只需要选择不同的服务器覆盖文件即可。这种方式也能实现所谓的规则和服务器配置分离的作用，Main.conf 中服务器地址的部分（Proxy 部分）写的都是假地址，使用时服务器地址读取的是 HK.conf 这样的服务器覆盖文件。这样每次你可以通过网络或者 iCloud、iTunes 的方式直接更新覆盖旧的 Main.conf 即可，对于更新配置来说很方便。
    </p>
    
    <p id="f85f" class="graf--p graf-after--p">
      通过 <a class="markup--anchor markup--p-anchor" href="https://gist.githubusercontent.com/raw/b0c6129840272c136a82/Main.conf" rel="nofollow" data-href="https://gist.githubusercontent.com/raw/b0c6129840272c136a82/Main.conf">URL 更新配置</a>文件时需要注意，Surge「Edit-Download Conf from URL」下载地址要复制完整地址而不是短链方式，否则名称会被识别为短链而不是 Main.conf。
    </p>
    
    <blockquote id="e5ae" class="graf--blockquote graf-after--p">
      <p>
        Main.conf (for SSLEdge)
      </p>
    </blockquote>
    
    <pre name="f73b" id="f73b" class="graf--pre graf-after--blockquote">[General]
# warning, notify, info, verbose
skip-proxy = 192.168.0.0/16,10.0.0.0/8,172.16.0.0/12,localhost,*.local
bypass-tun = 192.168.0.0/16,10.0.0.0/8,172.16.0.0/12
dns-server = 119.29.29.29,223.5.5.5,114.114.114.114
loglevel = notify

[Proxy]
# SSLEdge,自行修改 Proxy 中的服务器地址、端口、用户名、密码
Proxy = https,1.2.3.4,443,username,password

[Rule]
# 规则部分请参照范例补充完善，此处只列出几条示意
DOMAIN-KEYWORD,umeng.co,REJECT
DOMAIN-KEYWORD,google,Proxy,force-remote-dns

GEOIP,CN,DIRECT
FINAL,Proxy</pre>
    
    <blockquote id="8006" class="graf--blockquote graf-after--pre">
      <p>
        Main.conf (for ShadowSocks)
      </p>
    </blockquote>
    
    <pre name="a2be" id="a2be" class="graf--pre graf-after--blockquote">[General]
# warning, notify, info, verbose
skip-proxy = 192.168.0.0/16,10.0.0.0/8,172.16.0.0/12,localhost,*.local
bypass-tun = 192.168.0.0/16,10.0.0.0/8,172.16.0.0/12
dns-server = 119.29.29.29,223.5.5.5,114.114.114.114
loglevel = notify</pre>
    
    <pre name="0bfb" id="0bfb" class="graf--pre graf-after--pre">[Proxy]
# ShadowSocks,<em class="markup--em markup--pre-em">custom不要变，</em>修改服务器地址、端口、加密方式、密码、Shadowsocks 模块URL
Proxy = <em class="markup--em markup--pre-em">custom,</em>$IP,$PORT,$METHOD,$PASSWORD,$MODULE_URL</pre>
    
    <pre name="0641" id="0641" class="graf--pre graf-after--pre">[Rule]
# 规则部分请参照范例补充完善，此处只列出几条示意
DOMAIN-KEYWORD,umeng.co,REJECT
DOMAIN-KEYWORD,google,Proxy,force-remote-dns</pre>
    
    <pre name="1c6a" id="1c6a" class="graf--pre graf-after--pre">GEOIP,CN,DIRECT
FINAL,Proxy</pre>
    
    <blockquote id="3db4" class="graf--blockquote graf-after--pre">
      <p>
        🇭🇰HK(HKG3).CONF
      </p>
    </blockquote>
    
    <pre name="4a25" id="4a25" class="graf--pre graf-after--blockquote">#!PROXY-OVERRIDE:Main.conf

[Proxy]
Proxy = https,2.2.3.5,6556,username,password</pre>
    
    <blockquote id="0308" class="graf--blockquote graf-after--pre">
      <p>
        🇯🇵JP(TYO2).CONF
      </p>
    </blockquote>
    
    <pre name="d409" id="d409" class="graf--pre graf-after--blockquote">#!PROXY-OVERRIDE:Main.conf

[Proxy]
Proxy = https,3.2.3.6,15560,username,password</pre>
    
    <blockquote id="7024" class="graf--blockquote graf-after--pre">
      <p>
        SSLEdge 和 ShadowSocks 的差别只是 Proxy 代理服务器那一行，服务器覆盖配置中同理，SSEncrypt.module 模块的下载链接请自行 Google。
      </p>
    </blockquote>
    
    <blockquote id="e13a" class="graf--blockquote graf-after--blockquote">
      <p>
        为了显示上的直观，图示服务器覆盖文件的文件名加入了表情符号（原生拼音输入法输入香港🇭🇰）。 Dropbox 目前还不支持同步文件名包含表情符号的文件，所以如果要传到 Surge 里请使用 iTunes 或 iCloud Drive 方式。
      </p>
    </blockquote>
    
    <h4 id="4050" class="graf--h4 graf-after--blockquote">
      具体配置和规则
    </h4><figure id="f40f" class="graf--figure graf-after--h4"> 
    
    <div class="aspectRatioPlaceholder">
      <img class="graf-image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/7f390c24e9ae3e14421b771d653ebbbb.png" alt="iOS科学上网神器 Surge+SS配置" title="iOS科学上网神器 Surge+SS配置" alt="" data-image-id="1*TZAxQESxxBCtV8h9Pp3zmA.png" />
    </div></figure> 
    
    <pre name="bdf8" id="bdf8" class="graf--pre graf-after--figure"># 通用设置
loglevel = notify
bypass-system = true
skip-proxy = 192.168.0.0/16, 10.0.0.0/8, 172.16.0.0/12, localhost, *.local
bypass-tun = 192.168.0.0/16, 10.0.0.0/8, 172.16.0.0/12
dns-server = 8.8.8.8, 8.8.4.4</pre>
    
    <ul class="postList">
      <li id="7c49" class="graf--li graf-after--pre">
        记录日志的几种方式: verbose、info、notify、warning。默认是 notify，分析（Analytics）模块中可以查看具体的 Logs，日志对分析 Surge 的使用状况很有帮助，打开具体日志能看到 Surge 的行为和动作，如果遇到异常情况可以打开具体日志并通过右上角的分享将日志通过邮件发送给作者
      </li>
      <li id="33f1" class="graf--li graf-after--li">
        除非是在调试 Bug 的时候，平时请不要启动 verbose 级别的日志，因为日志需要保证完整写入，使用的是同步式地写入，性能上会有严重问题
      </li>
    </ul>
    
    <pre name="0f6c" id="0f6c" class="graf--pre graf-after--li"># 代理设置
[Proxy] 
Proxy = https,127.0.0.1,3120,username,password
ProxyA = socks5,127.0.0.1,3129
ProxyC = http,127.0.0.1,3120</pre>
    
    <ul class="postList">
      <li id="40f5" class="graf--li graf-after--pre">
        可以创建多个代理服务器条目，规则中可以指定某条规则走哪个代理
      </li>
      <li id="9af7" class="graf--li graf-after--li">
        SSLedge 使用 HTTPS，老式 APNp 用 HTTP
      </li>
      <li id="066d" class="graf--li graf-after--li">
        Surge 支持 HTTP, HTTPS 和 SOCKS5 的代理服务器，当前仅 HTTP/HTTPS 代理支持验证（用户名、密码）
      </li>
    </ul>
    
    <pre name="d64e" id="d64e" class="graf--pre graf-after--li"># 规则设置
[Rule] 
# 基于<strong class="markup--strong markup--pre-strong">域名</strong>判断并屏蔽（REJECT）请求
DOMAIN,pingma.qq.com,REJECT

# 基于<strong class="markup--strong markup--pre-strong">域名后缀</strong>判断屏蔽（REJECT）请求
DOMAIN-SUFFIX,flurry.com,REJECT

# 基于<strong class="markup--strong markup--pre-strong">关键词</strong>后缀判断走代理（Proxy），强制不尊重系统代理的请求走 Packet-Tunnel-Provider
DOMAIN-KEYWORD,google,Proxy,force-remote-dns

# 基于<strong class="markup--strong markup--pre-strong">域名后缀</strong>判断请求走直连（DIRECT）
DOMAIN-SUFFIX,126.net,DIRECT

# Telegram.app 指定“no-resolve”Surge 忽略这个规则与域的请求。 
IP-CIDR,91.108.56.0/22,Proxy,no-resolve</pre>
    
    <pre name="bee7" id="bee7" class="graf--pre graf-after--pre"># 判断是否是<strong class="markup--strong markup--pre-strong">局域网</strong>，如果是，走直连
IP-CIDR,192.168.0.0/16,DIRECT</pre>
    
    <pre name="b14a" id="b14a" class="graf--pre graf-after--pre"># 判断<strong class="markup--strong markup--pre-strong">服务器所在地</strong>，如果是国内，走直连
GEOIP,CN,DIRECT

# 其他的走代理
FINAL,Proxy</pre>
    
    <blockquote id="50fc" class="graf--blockquote graf-after--pre">
      <p>
        规则配置的高级选项中，「Force Remote DNS」的作用主要是用来解决本地 DNS 解析受到污染的问题，在添加针对 Google、Twitter 的规则时可以开启。
      </p>
    </blockquote>
    
    <blockquote id="4f1f" class="graf--blockquote graf-after--blockquote">
      <p>
        规则按照顺序执行，注意不要出现先后矛盾的地方，同一个域名或后缀的规则定义不要重复，使用文本编辑器编辑时注意每条规则间的分隔逗号是英文标点。
      </p>
    </blockquote>
    
    <h4 id="a359" class="graf--h4 graf-after--blockquote">
      高级设置中的选项
    </h4><figure id="8294" class="graf--figure graf-after--h4"> 
    
    <div class="aspectRatioPlaceholder is-locked">
      <div class="aspectRatioPlaceholder-fill">
      </div>
      
      <div class="progressiveMedia js-progressiveMedia graf-image is-canvasLoaded is-imageLoaded" data-image-id="1*cMFU5bgNGo0dkYBwT2H0gQ.png" data-width="1512" data-height="1002" data-action="zoom" data-action-value="1*cMFU5bgNGo0dkYBwT2H0gQ.png" data-scroll="native">
        <canvas class="progressiveMedia-canvas js-progressiveMedia-canvas" width="75" height="47"></canvas><img class="progressiveMedia-image js-progressiveMedia-image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/8942b8922175c390e59f67cbc71ddca2.png" alt="iOS科学上网神器 Surge+SS配置" title="iOS科学上网神器 Surge+SS配置" alt="" data-src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/8942b8922175c390e59f67cbc71ddca2.png" />
      </div>
    </div></figure> 
    
    <blockquote id="ffab" class="graf--blockquote graf-after--figure">
      <p>
        最右侧的图是分析模块中的统计（Statistics）数据，可以直观的看到当前连接（Surge 断开后统计重置）的时长以及Wi-Fi 和蜂窝移动网络的流量使用情况。
      </p>
    </blockquote>
    
    <p id="1a2d" class="graf--p graf-after--blockquote">
      主配置文件设置高级选项中的「Bypass System Related」不要关闭，Surge 通过这个开关和内置规则放行系统层面的通讯请求。如果禁用此选项，它可能会导致一些系统问题，如推送通知的延迟。
    </p>
    
    <p id="f3ff" class="graf--p graf-after--p">
      高级选项中的其他两项设置「SKIP PROXY」和「BYPASS TUN」是为了解决一些应用的兼容性问题，通过指定具体域名（apple.com或者*apple.com）或者 IP（192.168.2.* 或 192.168.2.0/24）让这类请求绕过 Surge 代理服务器和 TUN 接口。
    </p><figure id="1e5a" class="graf--figure graf-after--p"> 
    
    <div class="aspectRatioPlaceholder is-locked">
      <div class="aspectRatioPlaceholder-fill">
      </div>
      
      <div class="progressiveMedia js-progressiveMedia graf-image is-canvasLoaded is-imageLoaded" data-image-id="1*NruyQFzvj32cL2vDBMJqqw.png" data-width="1024" data-height="469" data-action="zoom" data-action-value="1*NruyQFzvj32cL2vDBMJqqw.png" data-scroll="native">
        <canvas class="progressiveMedia-canvas js-progressiveMedia-canvas" width="75" height="32"></canvas><img class="progressiveMedia-image js-progressiveMedia-image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/b75082c8fc41ad5172d18de6dd859384.png" alt="iOS科学上网神器 Surge+SS配置" title="iOS科学上网神器 Surge+SS配置" alt="" data-src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/b75082c8fc41ad5172d18de6dd859384.png" />
      </div>
    </div><figcaption class="imageCaption">Skip Proxy 和 Bypass TUN 的功能与原理(By 
    
    <a class="markup--anchor markup--figure-anchor" href="https://medium.com/@Blankwonder/surge-%E5%8E%9F%E7%90%86%E4%B8%8E%E5%AE%9E%E7%8E%B0-8aa3304fb3bb#.pwkuqyh7o" data-href="https://medium.com/@Blankwonder/surge-原理与实现-8aa3304fb3bb#.pwkuqyh7o">@Blankwonder</a> )</figcaption> </figure> 
    
    <p id="d0cd" class="graf--p graf-after--figure">
      Surge 能作为 DNS Client 使用，「DNS OVERRIDE」中填写的 DNS 地址将覆盖缺省的 DNS，针对较差的网络环境 Surge 能进行更高频率地重发，并同样适用于蜂窝数据网络，支持设置中（如：119.29.29.29,223.5.5.5,114.114.114.114）的多服务器并发查询。
    </p>
    
    <blockquote id="5440" class="graf--blockquote graf-after--p">
      <p>
        对于一般用户，不建议开启 DNS Override 选项 (dns-server)。第三方 DNS 不一定比 ISP 的要好，还容易造成 CDN 缓慢。
      </p>
    </blockquote>
    
    <h4 id="b458" class="graf--h4 graf-after--blockquote">
      分析网络活动
    </h4>
    
    <p id="8f51" class="graf--p graf-after--h4">
      Surge 分析模块中能直观看到 Surge 启动后最近地访问请求（Recent Requests）。
    </p><figure id="66cc" class="graf--figure graf-after--p"> 
    
    <div class="aspectRatioPlaceholder is-locked">
      <div class="aspectRatioPlaceholder-fill">
      </div>
      
      <div class="progressiveMedia js-progressiveMedia graf-image is-canvasLoaded is-imageLoaded" data-image-id="1*xSgkKYIAUkvNpnESeO3GKQ.png" data-width="1512" data-height="1002" data-action="zoom" data-action-value="1*xSgkKYIAUkvNpnESeO3GKQ.png" data-scroll="native">
        <canvas class="progressiveMedia-canvas js-progressiveMedia-canvas" width="75" height="47"></canvas><img class="progressiveMedia-image js-progressiveMedia-image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/60c35699c0f633611edaa05ed2a9f4de.png" alt="iOS科学上网神器 Surge+SS配置" title="iOS科学上网神器 Surge+SS配置" alt="" data-src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/60c35699c0f633611edaa05ed2a9f4de.png" />
      </div>
    </div></figure> 
    
    <p id="de8d" class="graf--p graf-after--figure">
      还可以通过规则结果测试（Rule Test Results）<strong class="markup--strong markup--p-strong">临时</strong>调整规则（点击某条记录），REJECT、DIRECT 或者指定它走某个代理。
    </p><figure id="1c10" class="graf--figure graf-after--p"> 
    
    <div class="aspectRatioPlaceholder">
      <img class="graf-image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/25e226268d0c9f607bb83ee0eb1c2f4f.png" alt="iOS科学上网神器 Surge+SS配置" title="iOS科学上网神器 Surge+SS配置" alt="" data-image-id="1*XO0-FDpH4Vs3GFOouxkUXA.png" />
    </div></figure> 
    
    <p id="d5af" class="graf--p graf-after--figure">
      通过规则结果测试（Rule Test Results）可以方便地跟踪当前 App 的网络访问，临时改变规则后可以观察 App 的实际运行情况，如果有效随后就能补充到主配置文件中。
    </p>
    
    <p id="9847" class="graf--p graf-after--p">
      在 iPad 分屏模式的使用场景中，我经常干的一件事就是打开某个国产应用，然后分屏查看 Surge 里 Test Results 的网络访问情况，侦查那些和应用功能无关的隐私或广告请求，然后记录下来添加到自己的规则列表中。更多规则设置的内容可以阅读《<a class="markup--anchor markup--p-anchor" href="https://medium.com/@scomper/surge-%E5%AE%9A%E5%88%B6%E8%87%AA%E5%B7%B1%E7%9A%84%E8%A7%84%E5%88%99%E9%85%8D%E7%BD%AE-34a6d74b0434#.yx9ddamxx" data-href="https://medium.com/@scomper/surge-%E5%AE%9A%E5%88%B6%E8%87%AA%E5%B7%B1%E7%9A%84%E8%A7%84%E5%88%99%E9%85%8D%E7%BD%AE-34a6d74b0434#.yx9ddamxx">Surge -定制自己的规则配置</a>》
    </p>
    
    <p id="373b" class="graf--p graf-after--p">
      如果说 Surge 最吸引人的地方在哪里，估计就是这种透明的网络访问方式，在轻松访问各种网络服务以外还是一个强有力地调试工具。<strong class="markup--strong markup--p-strong">安全和隐私已经变成只有少数人才能掌控的东西</strong>，学习掌握一款这样的工具还是很重要的。
    </p>
    
    <h4 id="9cc5" class="graf--h4 graf-after--p">
      常见问答
    </h4>
    
    <p id="b4a2" class="graf--p graf-after--h4">
      <strong class="markup--strong markup--p-strong">Q：为什么 Surge 一直显示是下载状态没有安装成功？</strong>
    </p>
    
    <p id="7107" class="graf--p graf-after--p">
      A：不能开启 Surge 的同时更新它自己，需要先停用 Surge，等更新完成后再打开 Surge。
    </p>
    
    <p id="c8e3" class="graf--p graf-after--p">
      <strong class="markup--strong markup--p-strong">Q：修改配置文件中的规则后会立即生效吗？</strong>
    </p>
    
    <p id="b223" class="graf--p graf-after--p">
      A：不会，需要到 Surge 中停止（Stop）后重新开始（Start）。
    </p>
    
    <p id="7eea" class="graf--p graf-after--p">
      <strong class="markup--strong markup--p-strong">Q：编辑服务器覆盖文件的时候提示「不能解析Final」是什么原因？</strong>
    </p>
    
    <p id="2a5c" class="graf--p graf-after--p">
      A：服务器覆盖配置文件不同于完整的 Main.conf 文件，需要在 Mac 上编辑好以后导入到 Surge 中才可以，目前还不支持直接在 iPhone 里进行编辑。
    </p>
    
    <p id="3f2b" class="graf--p graf-after--p">
      <strong class="markup--strong markup--p-strong">Q：Surge 的配置文件中的服务器该如何填写？</strong>
    </p>
    
    <p id="5c5e" class="graf--p graf-after--p">
      A：Surge 是一个网络调试工具，并不提供代理服务器，需要另行购买或自行搭建服务器，具体的服务器地址和端口可以咨询服务器提供商。
    </p>
    
    <p id="c2df" class="graf--p graf-after--p">
      <strong class="markup--strong markup--p-strong">Q：如何快速启动或关闭 Surge ？</strong>
    </p>
    
    <p id="bd8c" class="graf--p graf-after--p">
      A：Surge 提供了通知中心扩展 Widget，加载后由通知中心就能快速切换 Surge 状态。如果使用 Launcher 这类软件，可以通过 URL Scheme 命令`surge:///toggle`来控制 Surge 的切换，更多命令参见 <a class="markup--anchor markup--p-anchor" href="http://surge.run/manual/" rel="nofollow" data-href="http://surge.run/manual/">surge.run</a>。
    </p>
    
    <blockquote id="1db6" class="graf--pullquote pullquote graf-after--p graf--last">
      <p>
        <a class="markup--anchor markup--pullquote-anchor" href="https://itunes.apple.com/cn/app/surge-web-developer-tool-proxy/id1040100637?ls=1&mt=8" rel="nofollow" data-href="https://itunes.apple.com/cn/app/surge-web-developer-tool-proxy/id1040100637?ls=1&mt=8">Surge — Web Developer Tool and Proxy Utility</a> 是一款开发者调试和流量跟踪工具，需要一定的专业背景知识才可使用，购买前推荐先阅读作者写的《<a class="markup--anchor markup--pullquote-anchor" href="https://medium.com/@Blankwonder/surge-appstore-%E8%B4%AD%E4%B9%B0%E5%89%8D%E8%AF%B4%E6%98%8E-4bf1feb58c44#.sk5378nnq" data-href="https://medium.com/@Blankwonder/surge-appstore-购买前说明-4bf1feb58c44#.sk5378nnq">Surge App Store 购买前说明</a>》。
      </p>
    </blockquote>
  </div>
</div></section> <section class=" section--body section--last"> 

<div class="section-divider layoutSingleColumn">
  <hr class="section-divider" />
</div>

<div class="section-content">
  <div class="section-inner layoutSingleColumn">
    <p id="abc0" class="graf--p graf--first">
      问题反馈请将日志（verbose 级别）发送到 surge-support@surge.run，并在邮件中注明使用的版本和配置文件地址。Edit 主配置文件，在 「General — Log Level」 中可以调整 Log 级别。Analytics 模块中点击具体 Log 日志文件，通过右上角分享按钮可将日志分享到邮件或者 AirDrop 到 Mac 上。
    </p>
    
    <p id="e153" class="graf--p graf-after--p">
      <strong class="markup--strong markup--p-strong">请注意不要把服务器地址泄露到网上，服务提供商可能会因此禁用你的账号。发送截图、log 请务必隐去服务器地址和用户密码。</strong>
    </p>
    
    <p id="c188" class="graf--p graf-after--p">
      参考文章：
    </p>
    
    <ul class="postList">
      <li id="f298" class="graf--li graf-after--p">
        @<a class="markup--user markup--li-user" href="https://medium.com/u/bbc0f2920e7" data-href="https://medium.com/u/bbc0f2920e7" data-anchor-type="2" data-user-id="bbc0f2920e7" data-action="show-user-card" data-action-type="hover">scavin</a>：<a class="markup--anchor markup--li-anchor" href="http://www.appinn.com/surge-for-ios/" rel="nofollow" data-href="http://www.appinn.com/surge-for-ios/">Surge — 牛逼的网络开发与调试工具</a>
      </li>
      <li id="fd41" class="graf--li graf-after--li">
        <a class="markup--anchor markup--li-anchor" href="https://twitter.com/paveo" rel="nofollow" data-href="https://twitter.com/paveo">@Paveo</a>：<a class="markup--anchor markup--li-anchor" href="https://g.owind.com/surge-the-missing-tool-for-ios/" rel="nofollow" data-href="https://g.owind.com/surge-the-missing-tool-for-ios/">Surge, the missing tool for iOS</a>
      </li>
      <li id="6c60" class="graf--li graf-after--li">
        <a class="markup--anchor markup--li-anchor" href="https://twitter.com/soolby" rel="nofollow" data-href="https://twitter.com/soolby">@soolby</a>：<a class="markup--anchor markup--li-anchor" href="http://laob.me/1888/" rel="nofollow" data-href="http://laob.me/1888/">Surge 「人话版」功能介绍</a>
      </li>
      <li id="14f8" class="graf--li graf-after--li">
        <a class="markup--anchor markup--li-anchor" title="Twitter profile for @SurgeDebugger" href="http://twitter.com/SurgeDebugger" rel="nofollow" data-href="http://twitter.com/SurgeDebugger">@Surge</a>：<a class="markup--anchor markup--li-anchor" href="http://surge.run/manual/" rel="nofollow" data-href="http://surge.run/manual/">官方使用手册</a>
      </li>
    </ul>
  </div>
</div></section> 

<!--wp-compress-html no compression-->

<!--wp-compress-html-->