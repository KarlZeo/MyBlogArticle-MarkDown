---
id: 257
title: 解决 debian 系统升级卡在 reading changelogs
date: 2016-02-19T23:07:13+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=257
permalink: /2016/02/19/the-debian-system-upgrade-cards-reading-changelogs/
flavour_num_words:
  - 283
views:
  - 9
categories:
  - Linux
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

在 debian 系统下执行`apt-get update &amp;&amp; apt-get upgrade`屏幕输出如下:

<pre class="prettyprint" ><code>ca-certificates (20141019+deb8u1) stable; urgency=medium

* mozilla/{certdata.txt,nssckbi.h}:
Update Mozilla certificate authority bundle to version 2.6.
Closes: #806239
The following certificate authorities were added (+):
+ "CA WoSign ECC Root"
+ "Certification Authority of WoSign G2"
+ "Certinomis - Root CA"
+ "CFCA EV ROOT"
+ "COMODO RSA Certification Authority"
+ "Entrust Root Certification Authority - EC1"
+ "Entrust Root Certification Authority - G2"
+ "GlobalSign ECC Root CA - R4"
+ "GlobalSign ECC Root CA - R5"
+ "IdenTrust Commercial Root CA 1"
+ "IdenTrust Public Sector Root CA 1"
+ "OISTE WISeKey Global Root GB CA"
+ "S-TRUST Universal Root CA"
+ "Staat der Nederlanden EV Root CA"
+ "Staat der Nederlanden Root CA - G3"
+ "TÜRKTRUST Elektronik Sertifika Hizmet Sağlayıcısı H5"
+ "TÜRKTRUST Elektronik Sertifika Hizmet Sağlayıcısı H6"
+ "USERTrust ECC Certification Authority"
+ "USERTrust RSA Certification Authority"
The following certificate authorities were removed (-):
- "A-Trust-nQual-03"
- "America Online Root Certification Authority 1"
- "America Online Root Certification Authority 2"
- "Buypass Class 3 CA 1"
- "ComSign Secured CA"
- "Digital Signature Trust Co. Global CA 1"
- "Digital Signature Trust Co. Global CA 3"
- "E-Guven Kok Elektronik Sertifika Hizmet Saglayicisi"
- "GTE CyberTrust Global Root"
- "SG TRUST SERVICES RACINE"
- "TC TrustCenter Class 2 CA II"
- "TC TrustCenter Universal CA I"
- "Thawte Premium Server CA"
- "Thawte Server CA"
- "TURKTRUST Certificate Services Provider Root 1"
- "TURKTRUST Certificate Services Provider Root 2"
- "UTN DATACorp SGC Root CA"
- "Verisign Class 4 Public Primary Certification Authority - G3"

-- Michael Shuler &lt;email address hidden&gt; Mon, 14 Dec 2015 20:46:50 -0600
</code></pre>

回车键啥的按半天是没啥反应了.真相只有一个,那就是!!!<br>
  
**按一下 q 键&#8230;&#8230;**<br>
  
**Oh Shit , NMB &#8230;**

<!--wp-compress-html no compression-->

<!--wp-compress-html-->