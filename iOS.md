Print to log

	NSLog(@“Log message”);

AppDelete.m

	# get mainscreen bounds
	CGRect viewRect = [[UIScreen mainScreen] bounds];
	
	# print screen height and width to NSLog
	NSLog(@"Screen is %f tall and %f wide",
                 viewRect.size.height, viewRect.size.width); 
                 
	# Allocate memory for a UI Window and initialize object with 
	# frame size to the bounds of the main screen
	UIWindow *window = [[UIWindow alloc] initWithFrame:viewRect];
	
	# or
	self.window = [[UIWindow alloc] initWithFrame:viewRect];
	
	# Application windows are expected to have a root view controller 
	# at the end of application launch	UIViewController *colorTouchVC = [[UIViewController alloc] init];
	# Create a view the size of the whole screen	UIView *colorView = [[UIView alloc] initWithFrame:viewRect];
	# setup view background color	colorView.backgroundColor = [UIColor yellowColor];	colorTouchVC.view = colorView;
	self.window.rootViewController = colorTouchVC;
	[self.window makeKeyAndVisible]; # should receive all keyboard & non-touch events

AppDelete.h

	@property (strong, nonatomic) UIWindow *window;	@class ViewController;	@property (strong, nonatomic) ViewController *viewController;
ViewController.h
	- (void)buttonPressed:(UIButton *)sender;ViewController.m
	- (void)viewDidLoad	{
		UIButton *firstButton = [UIButton buttonWithType:UIButtonTypeRoundedRect];
		# Located at x = 100pts, y = 100pts, 100pts width, 44pts height
		firstButton.frame = CGRectMake(100, 100, 100, 44);
		
		# Sets the title when pressed >> forState:UIControlStateHighlighted
		[firstButton setTitle:@"Click me!" forState:UIControlStateNormal];
		
		[self.view addSubview:firstButton];
		
		UILabel *firstLabel = [[UILabel alloc] initWithFrame:CGRectMake(50, 30, 200, 44)];
		firstLabel.backgroundColor = [UIColor clearColor];
		firstLabel.text = @"Hello, welcome to my app!";
		[self.view addSubview:firstLabel];
		
		# addTarget:self >> # ViewController
		[firstButton addTarget:self                     action:@selector(buttonPressed:)          forControlEvents:UIControlEventTouchUpInside];	}
	- (void)buttonPressed:(UIButton *)sender	{	    NSLog(@"Button pressed, sender: %@", sender);	    if ([sender.titleLabel.text isEqualToString:@"Make 50%"]) {	    # or [sender isEqual:self.firstButton]	        self.view.alpha = .5;	    } else {	        self.view.alpha = 1;	    }
	    # removing a view	    [sender removeFromSuperview];	}
	- (void)touchesBegan:(NSSet *)touches withEvent:(UIEvent *)event	{	    NSLog(@"Started touching the screen");	}