YQ-Library-Objective-C
======================

My library come here. (in Objective-C)


Add Cutomized Fonts
======================

1. You need your font in .otf or .ttf copied to your project. For example in Supporting Files.
2. You need to edit .plist file. Add "Fonts provided by application" key into your plist and in Item 0 copy the exact filename of the font you copied to your Supporting files WITH extension. For example: "JosefinSansStd-Light_0.otf"
3. Make sure that the font you imported to your app is being packed into app itself. Do that by selecting your Target, then Build Phases, then Copy Bundle Resources. If you don't see your font in there, drag it from Supporting Files.


NSDictionary-JSONString
======================

NSString category to make the transition between NSDictionary and JSONString.


YQLabel
======================

YQLabel is to generate programmably UILabel, including size fits with width. It's used in dynamically height table cell.
<br>
Example (WebScraper)
```Objective-C
float tempOriginY = 72.0;
CGRect tempFrame = CGRectMake(20.0, tempOriginY, CGRectGetWidth(self.view.frame)-40.0, 1024.0);
NSDictionary *tempHead = [self.kimonoResultsHeader objectAtIndex:0];

NSString *tempTitle = [tempHead objectForKey:@"Title"];
self.articleTitle = [[YQLabelWithFixedWidth alloc] initWithFrame:tempFrame
                                                            font:[UIFont fontWithName:@"Georgia" size:20]
                                                            text:tempTitle
                                                   textAlignment:NSTextAlignmentLeft];


NSString *tempAuthor = [[tempHead objectForKey:@"Author"] objectForKey:@"text"];
self.articleAuthor = [[YQLabelWithFixedWidth alloc] initWithText:tempAuthor
                                                   textAlignment:NSTextAlignmentLeft
                                                        fontSize:17
                                             labelEstimatedWidth:CGRectGetWidth(self.view.frame) afterUILabel:self.articleTitle];

NSString *tempDate = [tempHead objectForKey:@"Date"];
self.publishDate = [[YQLabelWithFixedWidth alloc] initWithText:tempDate
                                                 textAlignment:NSTextAlignmentLeft
                                                      fontSize:17
                                           labelEstimatedWidth:CGRectGetWidth(self.view.frame)
                                                  afterUILabel:self.articleAuthor];

[self.view addSubview:self.articleTitle];
[self.view addSubview:self.articleAuthor];
[self.view addSubview:self.publishDate];
```

YQButton
======================
I primarily use YQButton to create a click-able image.

<br>
```Objective-C
@interface YQButtonWithImage : YQButton

// mutable subclass(NString, NSDictionary)
@property (strong, nonatomic) NSString* regularImage;
@property (strong, nonatomic) NSString* selectedImage;
@property (nonatomic) BOOL isBackgroundTransparent;
@property (nonatomic) BOOL hasAnimation;

- (instancetype)initWithFrame:(CGRect)frame image:(NSString*)image selectedImage:(NSString*)selectedImage;
- (instancetype)initWithCenterPoin:(CGPoint)centerPoint imageSize:(CGSize)imageSize image:(NSString*)image selectedImage:(NSString*)selectedImage;

@end

```

```Objective-C
// Long press on the screen, and a button is generated at the point you pressed.
YQButtonWithImage *tempButton = [[YQButtonWithImage alloc] initWithCenterPoin:locationInView imageSize:CGSizeMake(45, 45) image:tempImageName selectedImage:tempImageName];
tempButton.hasAnimation = YES;

[self.backgroundView addSubview:tempButton];
```
