---

comments: true
date: 2015-09-06 16:42:25
layout: post
title: AutoLayout之NSLayoutConstraint
categories:
-  IOS

---

 <kbd>Constraint</kbd>是<kbd>AutoLayout</kbd>中基石组件。它可以组织元素之间的关系：<kbd>left</kbd>、<kbd>right</kbd>、<kbd>top</kbd>、<kbd>bottom</kbd>、<kbd>width</kbd>、<kbd>height</kbd>等等。

初始化

{% highlight objc %}
+(instancetype)constraintWithItem:(id)view1
                        attribute:(NSLayoutAttribute)attr1
                        relatedBy:(NSLayoutRelation)relation
                           toItem:(id)view2
                        attribute:(NSLayoutAttribute)attr2
                       multiplier:(CGFloat)multiplier
                         constant:(CGFloat)c;
 {% endhighlight %} 

它有这个公式：

{% highlight objc %}
view1.attr1 = view2.attr2 * multiplier + c
{% endhighlight %}

***Note:用代码写Constraint需要把view的translatesAutoresizingMaskIntoConstraints设为NO。***


例子：
{% highlight objc %}
	UIView *view = [[UIView alloc] initWithFrame:CGRectMake(0, 0, 44, 44)];
    view.translatesAutoresizingMaskIntoConstraints = NO;
    view.backgroundColor = [UIColor redColor];
    [self.view addSubview:view];
    
    [self.view addConstraint:
     [NSLayoutConstraint constraintWithItem:view
                                  attribute:NSLayoutAttributeLeft
                                  relatedBy:NSLayoutRelationEqual
                                     toItem:self.view
                                  attribute:NSLayoutAttributeLeft
                                 multiplier:1
                                   constant:20]];
    
    [self.view addConstraint:
     [NSLayoutConstraint constraintWithItem:view
                                  attribute:NSLayoutAttributeTop
                                  relatedBy:NSLayoutRelationEqual
                                     toItem:self.view
                                  attribute:NSLayoutAttributeTop
                                 multiplier:1
                                   constant:30]];
    
    [self.view addConstraint:
     [NSLayoutConstraint constraintWithItem:view
                                  attribute:NSLayoutAttributeWidth
                                  relatedBy:NSLayoutRelationEqual
                                     toItem:self.view
                                  attribute:NSLayoutAttributeWidth
                                 multiplier:0
                                   constant:30]];
    
    [self.view addConstraint:
     [NSLayoutConstraint constraintWithItem:view
                                  attribute:NSLayoutAttributeHeight
                                  relatedBy:NSLayoutRelationEqual
                                     toItem:self.view
                                  attribute:NSLayoutAttributeHeight
                                 multiplier:0
                                   constant:30]];
    
    UIView *view1 = [[UIView alloc] init];
    view1.translatesAutoresizingMaskIntoConstraints = NO;
    view1.backgroundColor = [UIColor blueColor];
    [self.view addSubview:view1];
    
    
    [self.view addConstraint:
     [NSLayoutConstraint constraintWithItem:view1
                                  attribute:NSLayoutAttributeLeft
                                  relatedBy:NSLayoutRelationEqual
                                     toItem:view
                                  attribute:NSLayoutAttributeRight
                                 multiplier:1
                                   constant:20]];
    
    [self.view addConstraint:
     [NSLayoutConstraint constraintWithItem:view1
                                  attribute:NSLayoutAttributeTop
                                  relatedBy:NSLayoutRelationEqual
                                     toItem:view
                                  attribute:NSLayoutAttributeTop
                                 multiplier:1
                                   constant:0]];
    
    [self.view addConstraint:
     [NSLayoutConstraint constraintWithItem:view1
                                  attribute:NSLayoutAttributeWidth
                                  relatedBy:NSLayoutRelationEqual
                                     toItem:view
                                  attribute:NSLayoutAttributeWidth
                                 multiplier:1
                                   constant:0]];
    
    [self.view addConstraint:
     [NSLayoutConstraint constraintWithItem:view1
                                  attribute:NSLayoutAttributeHeight
                                  relatedBy:NSLayoutRelationEqual
                                     toItem:view
                                  attribute:NSLayoutAttributeHeight
                                 multiplier:1
                                   constant:0]];
{% endhighlight %} 

THE END!