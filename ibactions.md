#IBActions and IBOutlets

### Linking View Elements to Controllers
Within your view/storyboard, you may have buttons, images, etc that you want to perform actions for when they are pressed or have a reference to them to update/change through code.  This can be accomplished by connecting your view's elements to your view controller.  First, you want to open split view so that both your view and your view controller are viewable side-by-side. Next, to peform an action/function call when something in your view is pressed, you can hold CTRL and drag from the desired element to your view controller. You should get a popup that asks you to name the connection between the button and the view controller. In the field that says "Connection", select the arrow to access the drop down menu and then select "Action". What this does is it creates an IBAction for the view element you selected (typically a button), and so now within the IBAction's function you can write code for whatever event you would like to occur when that element is pressed upon. If you don't want to perform an action when an element is pressed, but would rather want a reference to the element so that you may change it later on i.e change the text of an UILabel, then you can choose to make the Connection as an  "Outlet". This way, the element will be connected to the view controller as an IBOutlet and you can manipulate the element using its reference in your code.

## Passing Data Between View Controllers
To pass data from one view controller to another, you can use the prepareForSegue method (more details here: https://developer.apple.com/documentation/uikit/uiviewcontroller/1621490-prepareforsegue). The preareForSegue method has an arguement called segue which refers to the segue between the initial view controller and the one we want to segue to. We can use the arguement segue's destination property, which is refers to the destination view controller, and cast its type to our desired view controller i.e "MyDestinationVC". So, we can do something like this within the prepareForSegue function:
``` swift
if let destinationVC = segue.destination as? MyDestinationVC {
	// Send some data here
}
```
Within the `if` block, we can set the values for the MyDestinationVC's IBOutlets. For example, if you have a UILabel in MyDestinationVC and you want it to match the UILabel in your initial view controller, you can do something like this:
``` swift
if let destinationVC = segue.destination as? MyDestinationVC {
	// Update UILabel's text in MyDestinationVC
	destinationVC.textLabel.text = initialVCTextLabel.text
}
```

You can learn more about passing data between VCs here: http://www.thomashanning.com/passing-data-between-view-controllers/
