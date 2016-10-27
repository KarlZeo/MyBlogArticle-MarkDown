# [转] IOS学习笔记——iOS组件之UIScrollView详解
引言
  
UIScrollView的是几个UIKit类包括的UITableView和UITextView中的超类。

一个UIScrollView对象（或者，简单地说，一个滚动视图）的核心概念是，它是一个视图，其起源是可调过的内容视图。它剪辑的内容，它的框架，这通常（但不一定）恰逢该应用程序的主窗口。滚动视图跟踪手指的变动，并相应调整原点。这正显示出它的内容“，通过”滚动视图的视图绘制的基础上，新的原点，它被固定在内容视图的偏移部分本身。滚动视图本身没有绘制，除了显示垂直和水平滚动的指标。滚动视图必须知道的内容视图的大小，所以它知道何时停止滚动，默认情况下，它“反弹”回来时，滚动超出了内容的范围。

用于管理内容的绘制有关的对象显示在一个滚动视图应该瓦片的内容的子视图，以便没有视图超过屏幕的大小。当用户在滚动滚动视图，这个对象应该添加和删除子视图是必要的。

由于滚动视图没有滚动条，它必须知道是否触摸信号的意图与滚动意图在内容跟踪一个子视图。做出此决定，它暂时拦截触摸按下事件通过启动一个定时器，并在定时器触发之前，看是否触摸手指做任何运动。如果定时器触发无位置显著的变化，滚动视图将跟踪事件的内容视图的感动子视图。然后，如果用户在定时器期满前拉着自己的手指远远不够，滚动视图将取消任何跟踪的子视图，并进行滚动本身。子类可以重写touchesShouldBegin ： withEvent：方法inContentView ：,pagingEnabled和touchesShouldCancelInContentView ：方法（这是由滚动视图调用）来影响滚动视图如何处理滚动手势。

滚动视图还处理缩放和平移的内容。当用户使一个夹在或向外挤压手势，滚动视图调整偏移量和内容的标度。当手势结束，管理内容视图中的对象应该要更新的内容为必要的子视图。 （请注意，手势可以结束和手指仍可能下跌。 ）虽然手势正在进行中，滚动视图不发送任何跟踪调用子视图。

该UIScrollView的类可以有必须采取UIScrollViewDelegate协议的委托。对于缩放和平移工作，委托必须实现viewForZoomingInScrollView ：和scrollViewDidEndZooming ： withView ： atScale ： ，此外，最大（ maximumZoomScale ）和最小（ minimumZoomScale ）变焦倍数必须是不同的。

方法&&属性:

```
  
// 监控目前滚动的位置(默认CGPointZero)

CGPoint contentOffset;
  
&#8211; (void)setContentOffset:(CGPoint)contentOffset animated:(BOOL)animated;
  
// 滚动范围的大小(默认CGSizeZero)

CGSize contentSize;
  
// 视图在scrollView中的位置(UIEdgeInsetsZero)

UIEdgeInsets contentInset;
  
// 设置协议

id<UIScrollViewDelegate> delegate;
  
// 指定控件是否只能在一个方向上滚动(默认为NO)

BOOL directionalLockEnabled;
  
// 控制控件遇到边框是否反弹(默认为YES)

BOOL bounces;
  
// 控制垂直方向遇到边框是否反弹(默认为NO,如果为YES，bounces也是YES)

BOOL alwaysBounceVertical;
  
// 控制水平方向遇到边框是否反弹(默认为NO,如果为YES，bounces也是YES)

BOOL alwaysBounceHorizontal;
  
// 控制控件是否整页翻动(默认为NO)

BOOL pagingEnabled;
  
// 控制控件是否能滚动

BOOL scrollEnabled;
  
// 控制是否显示水平方向的滚动条

BOOL showsHorizontalScrollIndicator;
  
// 控制是否显示垂直方向的滚动条

BOOL showsVerticalScrollIndicator;
  
// 指定滚动条在scrollerView中的位置

UIEdgeInsets scrollIndicatorInsets;
  
// 设定滚动条的样式

UIScrollViewIndicatorStyle indicatorStyle;
  
UIScrollViewDelegate详解
  
//scrollView滚动时，就调用该方法。任何offset值改变都调用该方法。即滚动过程中，调用多次
  
&#8211; (void)scrollViewDidScroll:(UIScrollView *)scrollView{

NSLog(@&#8221;scrollViewDidScroll&#8221;);
  
CGPoint point=scrollView.contentOffset;
  
NSLog(@&#8221;%f,%f&#8221;,point.x,point.y);
  
// 从中可以读取contentOffset属性以确定其滚动到的位置。

// 注意：当ContentSize属性小于Frame时，将不会出发滚动
  
}
  
// 当scrollView缩放时，调用该方法。在缩放过程中，回多次调用
  
&#8211; (void)scrollViewDidZoom:(UIScrollView *)scrollView{

NSLog(@&#8221;scrollViewDidScroll&#8221;);
  
float value=scrollView.zoomScale;
  
NSLog(@&#8221;%f&#8221;,value);
  
}
  
// 当开始滚动视图时，执行该方法。一次有效滑动（开始滑动，滑动一小段距离，只要手指不松开，只算一次滑动），只执行一次。
  
&#8211; (void)scrollViewWillBeginDragging:(UIScrollView *)scrollView{

NSLog(@&#8221;scrollViewWillBeginDragging&#8221;);

}
  
// 滑动scrollView，并且手指离开时执行。一次有效滑动，只执行一次。
  
// 当pagingEnabled属性为YES时，不调用，该方法
  
&#8211; (void)scrollViewWillEndDragging:(UIScrollView \*)scrollView withVelocity:(CGPoint)velocity targetContentOffset:(inout CGPoint \*)targetContentOffset{

NSLog(@&#8221;scrollViewWillEndDragging&#8221;);

}
  
// 滑动视图，当手指离开屏幕那一霎那，调用该方法。一次有效滑动，只执行一次。
  
// decelerate,指代，当我们手指离开那一瞬后，视图是否还将继续向前滚动（一段距离），经过测试，decelerate=YES
  
&#8211; (void)scrollViewDidEndDragging:(UIScrollView *)scrollView willDecelerate:(BOOL)decelerate{

NSLog(@&#8221;scrollViewDidEndDragging&#8221;);
  
if (decelerate) {
  
NSLog(@&#8221;decelerate&#8221;);
  
}else{
  
NSLog(@&#8221;no decelerate&#8221;);

}

CGPoint point=scrollView.contentOffset;
  
NSLog(@&#8221;%f,%f&#8221;,point.x,point.y);

}
  
// 滑动减速时调用该方法。
  
&#8211; (void)scrollViewWillBeginDecelerating:(UIScrollView *)scrollView{

NSLog(@&#8221;scrollViewWillBeginDecelerating&#8221;);
  
// 该方法在scrollViewDidEndDragging方法之后。
  
}
  
// 滚动视图减速完成，滚动将停止时，调用该方法。一次有效滑动，只执行一次。
  
&#8211; (void)scrollViewDidEndDecelerating:(UIScrollView *)scrollView{

NSLog(@&#8221;scrollViewDidEndDecelerating&#8221;);

[_scrollView setContentOffset:CGPointMake(0, 500) animated:YES];

}
  
// 当滚动视图动画完成后，调用该方法，如果没有动画，那么该方法将不被调用
  
&#8211; (void)scrollViewDidEndScrollingAnimation:(UIScrollView *)scrollView{

NSLog(@&#8221;scrollViewDidEndScrollingAnimation&#8221;);
  
// 有效的动画方法为：
  
// &#8211; (void)setContentOffset:(CGPoint)contentOffset animated:(BOOL)animated 方法
  
// &#8211; (void)scrollRectToVisible:(CGRect)rect animated:(BOOL)animated 方法
  
}
  
// 返回将要缩放的UIView对象。要执行多次
  
&#8211; (UIView \*)viewForZoomingInScrollView:(UIScrollView \*)scrollView{

NSLog(@&#8221;viewForZoomingInScrollView&#8221;);
  
return self.imgView;

}
  
// 当将要开始缩放时，执行该方法。一次有效缩放，就只执行一次。
  
&#8211; (void)scrollViewWillBeginZooming:(UIScrollView \*)scrollView withView:(UIView \*)view{

NSLog(@&#8221;scrollViewWillBeginZooming&#8221;);

}
  
// 当缩放结束后，并且缩放大小回到minimumZoomScale与maximumZoomScale之间后（我们也许会超出缩放范围），调用该方法。
  
&#8211; (void)scrollViewDidEndZooming:(UIScrollView \*)scrollView withView:(UIView \*)view atScale:(float)scale{

NSLog(@&#8221;scrollViewDidEndZooming&#8221;);

}
  
// 指示当用户点击状态栏后，滚动视图是否能够滚动到顶部。需要设置滚动视图的属性：_scrollView.scrollsToTop=YES;
  
&#8211; (BOOL)scrollViewShouldScrollToTop:(UIScrollView *)scrollView{

return YES;
  
}
  
// 当滚动视图滚动到最顶端后，执行该方法
  
&#8211; (void)scrollViewDidScrollToTop:(UIScrollView *)scrollView{

NSLog(@&#8221;scrollViewDidScrollToTop&#8221;);
  
}
  
Tip:判断uiscrollview是向上滚动还是向下滚动
  
int _lastPosition; //A variable define in headfile

  * (void)scrollViewDidScroll:(UIScrollView *)scrollView{
  
    int currentPostion = scrollView.contentOffset.y;
  
    if (currentPostion &#8211; _lastPosition > 25) {
  
    _lastPosition = currentPostion;
  
    NSLog(@&#8221;ScrollUp now&#8221;);
  
    }
  
    else if (_lastPosition &#8211; currentPostion > 25)
  
    {
  
    _lastPosition = currentPostion;
  
    NSLog(@&#8221;ScrollDown now&#8221;);
  
    }
  
    }
  
    // 25 可以是任意数字，可根据自己的需要来设定。
  
    // 升级版：到达顶部或底部时不会反弹
  * (void)scrollViewDidScroll:(UIScrollView *)scrollView
  
    {
  
    int currentPostion = scrollView.contentOffset.y;

if (currentPostion &#8211; _lastPosition > 20 && currentPostion > 0) { //这个地方加上 currentPostion > 0 即可）
  
_lastPosition = currentPostion;

NSLog(@&#8221;ScrollUp now&#8221;);
  
}
  
else if ((_lastPosition &#8211; currentPostion > 20) && (currentPostion <= scrollView.contentSize.height-scrollView.bounds.size.height-20) ){
  
_lastPosition = currentPostion;

NSLog(@&#8221;ScrollDown now&#8221;);
  
}
  
}

```

