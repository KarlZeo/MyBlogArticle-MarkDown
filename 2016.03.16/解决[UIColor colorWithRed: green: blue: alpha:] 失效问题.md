# 解决[UIColor colorWithRed: green: blue: alpha:] 失效问题

在设置颜色是用[UIColor colorWithRed: green: blue: alpha:] 有时会遇到颜色不显示的问题，，，刚开始以为是设置的颜色值太过浅的原因，后来试了其他的颜色值发觉并不是这样的，网上搜索了一下，发现了问题的所在：RGB的颜色值范围都是在**0.0~1.0**之间的，并不是我们误认为的0~255。

错误用法：

```
cell.temperature.backgroundColor = [UIColor colorWithRed:226 green:229 blue:229 alpha:1];
```


正确用法：

```
cell.temperature.backgroundColor = [UIColor colorWithRed:226.0/255 green:229.0/255 blue:229.0/255 alpha:1];

```




