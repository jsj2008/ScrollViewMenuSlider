ScrollViewMenuSlider v1.0.1 for iOS
===================
by Alexander Langstrand
What this is
------------

ScrollViewMenuSlider is a similar control to the slide down menu control featured in the iOS app created by Facebook.

![Alt text](http://i50.tinypic.com/352fz8i.jpg "ScrollViewMenuSlider")

What it does
------------
It makes it easy for the user to access the top menu from anywhere in the list.

To show the slide in menu, the user simply has to scroll upwards fast enough for the list to scroll a little further by itself. 

Getting started
------------

### Modify your interface file

  Add the scrollViewDelegate:

    @interface YourViewController : UIYourViewController<UIScrollViewDelegate...>

### Modify your implementation file

  Import ScrollViewMenuSlider:

    #import "ScrollViewMenuSliderController.h"

  Declare the ScrollViewMenuSlider:

    @implementation YourController {
      ScrollViewMenuSlider *scrollViewMenuSliderController;
    }

  Add the scrollViewDelegate methods:

    - (void)scrollViewDidScroll:(UIScrollView *)scrollView {
      [_scrollViewMenuSliderController scrollViewDidScroll:scrollView];
    }

    -(void)scrollViewWillBeginDecelerating:(UIScrollView *)scrollView {
      [_scrollViewMenuSliderController scrollViewWillBeginDecelerating:scrollView];
    }

    -(void)scrollViewWillBeginDragging:(UIScrollView *)scrollView {
      [_scrollViewMenuSliderController scrollViewWillBeginDragging:scrollView];
    }

    -(void)scrollViewDidEndDragging:(UIScrollView *)scrollView willDecelerate:(BOOL)decelerate {
      [_scrollViewMenuSliderController scrollViewDidEndDragging:scrollView willDecelerate:decelerate];
    }
    
  And finally, add these lines in your viewDidLoad:
  
    if (_scrollViewMenuSliderController == nil) {

        _scrollViewMenuSliderController = [[ScrollViewMenuSliderController alloc] initWithMenuView:_yourMenuView];
        
        [self.YourView addSubview:_scrollViewMenuSliderController.view];
        [self.YourView setContentInset:UIEdgeInsetsMake(_menuView.frame.size.height, 0, 0, 0)];
        [self.YourView setScrollIndicatorInsets:UIEdgeInsetsMake(_yourMenuView.frame.size.height, 0, 0, 0)];
    }

Branching
------------
All development work is done on the dev branch. When it's considered stable, it's merged to master with a new version tag.

License
------------

Copyright (c) 2013 FINN.no AS

MIT License

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
