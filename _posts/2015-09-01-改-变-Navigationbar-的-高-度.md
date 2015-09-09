---

comments: true
date: 2015-09-01 16:42:25
layout: post
title: 改变Navigationbar的高度
categories:
-  IOS

---

重写- (CGSize)sizeThatFits:(CGSize)size方法：
{% highlight objc %}
 #import "CustomNavigationbar.h"

@implementation CustomNavigationbar

-(instancetype)initWithFrame:(CGRect)frame {
    self = [super initWithFrame:frame];
    if (self) {
        self.barTintColor = [UIColor blueColor];
    }
    return self;
}

-(CGSize)sizeThatFits:(CGSize)size {
    CGSize navigationSize = [super sizeThatFits:size];
    navigationSize = CGSizeMake(navigationSize.width, navigationSize.height + 20);
    return navigationSize;
}
{% endhighlight %}

使用：
{% highlight objc %}
TableViewController *controller = [[TableViewController alloc] init];
UINavigationController *nav = [[UINavigationController alloc] 
		initWithNavigationBarClass:[CustomNavigationbar class] toolbarClass:nil ];
nav.viewControllers = @[controller];
[self presentViewController:nav animated:YES completion:nil];
 {% endhighlight %}

THE END