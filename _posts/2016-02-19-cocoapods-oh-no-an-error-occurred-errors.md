---
id: 231
title: 'CocoaPods [!] Oh no, an error occurred.错误'
date: 2016-02-19T23:01:06+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=231
permalink: /2016/02/19/cocoapods-oh-no-an-error-occurred-errors/
views:
  - 13
dsq_thread_id:
  - 4723594098
categories:
  - Mac
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

错误日志

<pre class="prettyprint" ><code>CocoaPods 0.29.0 is available. 2014-02-17 00:25:35.875 ruby[65690:507] CFPropertyListCreateFromXMLData(): Old-style plist parser: missing semicolon in dictionary on line 908. Parsing will be abandoned. Break on _CFPropertyListMissingSemicolon to debug. ――― MARKDOWN TEMPLATE ――――――――――――――――――――――――――――――――――――――――――――――――――――――――――― ### Report * What did you do? * What did you expect to happen? * What happened instead? ### Stack ``` CocoaPods : 0.27.1 Ruby : ruby 2.0.0p247 (2013-06-27 revision 41674) [universal.x86_64-darwin13] RubyGems : 2.1.10 Host : Mac OS X 10.9.1 (13B42) Xcode : 5.0.1 (5A2053) Ruby lib dir : /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib Repositories : master - https://github.com/CocoaPods/Specs.git @ 8e7e6d8f6da821576f7b42fc513532790c8e1bc8 ``` ### Podfile ```ruby platform :ios, '7.0' pod 'SWRevealViewController' pod 'MagicalRecord' pod 'AFNetworking', '1.3.3' ``` ### Error ``` ArgumentError - Unable to read plist data from `"/Users/mac/Documents/Projects/StatsTrack/StatsTrack.xcodeproj/project.pbxproj"': Unexpected character / at line 1 /Library/Ruby/Gems/2.0.0/gems/xcodeproj-0.14.1/lib/xcodeproj/project.rb:172:in `read_plist' /Library/Ruby/Gems/2.0.0/gems/xcodeproj-0.14.1/lib/xcodeproj/project.rb:172:in `initialize_from_file' /Library/Ruby/Gems/2.0.0/gems/xcodeproj-0.14.1/lib/xcodeproj/project.rb:93:in `open' /Library/Ruby/Gems/2.0.0/gems/cocoapods-0.27.1/lib/cocoapods/installer/analyzer.rb:488:in `block in compute_target_platforms' /Library/Ruby/Gems/2.0.0/gems/cocoapods-0.27.1/lib/cocoapods/installer/analyzer.rb:485:in `each' /Library/Ruby/Gems/2.0.0/gems/cocoapods-0.27.1/lib/cocoapods/installer/analyzer.rb:485:in `compute_target_platforms' /Library/Ruby/Gems/2.0.0/gems/cocoapods-0.27.1/lib/cocoapods/installer/analyzer.rb:55:in `analyze' /Library/Ruby/Gems/2.0.0/gems/cocoapods-0.27.1/lib/cocoapods/installer.rb:171:in `analyze' /Library/Ruby/Gems/2.0.0/gems/cocoapods-0.27.1/lib/cocoapods/installer.rb:94:in `block in resolve_dependencies' /Library/Ruby/Gems/2.0.0/gems/cocoapods-0.27.1/lib/cocoapods/user_interface.rb:52:in `section' /Library/Ruby/Gems/2.0.0/gems/cocoapods-0.27.1/lib/cocoapods/installer.rb:93:in `resolve_dependencies' /Library/Ruby/Gems/2.0.0/gems/cocoapods-0.27.1/lib/cocoapods/installer.rb:86:in `install!' /Library/Ruby/Gems/2.0.0/gems/cocoapods-0.27.1/lib/cocoapods/command/project.rb:38:in `run_install_with_update' /Library/Ruby/Gems/2.0.0/gems/cocoapods-0.27.1/lib/cocoapods/command/project.rb:68:in `run' /Library/Ruby/Gems/2.0.0/gems/claide-0.3.2/lib/claide/command.rb:206:in `run' /Library/Ruby/Gems/2.0.0/gems/cocoapods-0.27.1/lib/cocoapods/command.rb:51:in `run' /Library/Ruby/Gems/2.0.0/gems/cocoapods-0.27.1/bin/pod:19:in `' /usr/bin/pod:23:in `load' /usr/bin/pod:23:in `' ``` ――― TEMPLATE END ―――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――― [!] Oh no, an error occurred. Search for existing github issues similar to yours: https://github.com/CocoaPods/CocoaPods/search?q=Unable+to+read+plist+data+from+%60%22%2FUsers%2Fmac%2FDocuments%2FProjects%2FStatsTrack%2FStatsTrack.xcodeproj%2Fproject.pbxproj%22%27%3A+Unexpected+character+%2F+at+line+1&amp;type=Issues If none exists, create a ticket, with the template displayed above, on: https://github.com/CocoaPods/CocoaPods/issues/new
</code></pre>

解决办法

删除 ruby 2.3 ,使用系统自带的 ruby, 重装 cocoapods. 解决.

complete!now!

&nbsp;

<!--wp-compress-html no compression-->

<!--wp-compress-html-->