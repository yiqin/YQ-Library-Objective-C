YQ-Library-Objective-C
======================

My library come here. (in Objective-C)


NSDictionary-JSONString
======================

NSString category to make the transition between NSDictionary and JSONString.


YQLabel
======================

YQLabel is to generate programmably UILabel, including size fits with width. It's used in dynamically height table cell.
<br>Example (WebScraper)

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
