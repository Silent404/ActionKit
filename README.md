![Banner](actionKitBanner.png)
[![Version](https://img.shields.io/cocoapods/v/ActionKit.svg?style=flat)](http://cocoadocs.org/docsets/ActionKit)
[![Carthage](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
[![License](https://img.shields.io/cocoapods/l/ActionKit.svg?style=flat)](http://cocoadocs.org/docsets/ActionKit)
[![Platform](https://img.shields.io/cocoapods/p/ActionKit.svg?style=flat)](http://cocoadocs.org/docsets/ActionKit)
![Swift](https://img.shields.io/badge/%20in-swift%204.0-orange.svg)

# ActionKit

ActionKit is a light-weight, easy to use framework that wraps the target-action design paradigm into a less verbose, cleaner format. It shortens target-action method calls by removing the target and replacing the selector with a closure.

### Example of target-action *without* ActionKit
```swift
button.addTarget(self, action: #selector(MyViewController.buttonWasTapped(_:)), forControlEvents: .TouchUpInside)
```

#### and somewhere else...
```
func buttonWasTapped(sender: Any) {
  if let button = sender as? UIButton {
    button.setTitle("Button was tapped!", forState: .Normal)
  } 
}
```

### Or *with* ActionKit, all in one place
```swift
button.addControlEvent(.touchUpInside) { (control: UIControl) in
  guard let button = control as? UIButton else {
    return
  }
  button.setTitle("Button was tapped!", forState: .Normal)

}
```

## Installation

### CocoaPods
 ActionKit is available through [CocoaPods](http://cocoapods.org). To install
 it, simply add the following line to your Podfile:
 
    pod 'ActionKit', '~> 2.3.0'

### Carthage

- 1. Add the following to your *Cartfile*:

```
    github "ActionKit/ActionKit" == 2.3.0
``` 
   
- 2. Run `carthage update`
- 3. Add the framework as described in [Carthage Readme](https://github.com/Carthage/Carthage#adding-frameworks-to-an-application)

## How it works

ActionKit extends target-action functionality by providing easy to use methods that take closures instead of a selector. ActionKit uses a singleton which stores the closures and acts as the target. Closures capture and store references to any constants and variables from their context, so the user is free to use variables from the context in which the closure was defined in.

## Features

* Add an action based closure to any `UIGestureRecognizer` subclass (eg. `UITapGestureRecognizer`, `UIPanGestureRecognizer`...) instead of needing to use the target-action mechanism
* Remove actions added to `UIGestureRecognizer` subclasses
* Add an action based closure to any `UIControl` subclass (eg: `UIButton`, `UIView`, `UISwitch`...) instead of needing to use the target-action mechanism
* Remove actions added to `UIControl` subclasses
* Add an action based closure to any `UIBarButtonItem`, instead of needing target-action
* Remove actions added to `UIBarButtonItem`s

## Examples

See the [examples wiki](EXAMPLES.md)

## FAQ

#### Does ActionKit work with Xcode 9's new build system?

Yes, but you need to do 1 extra step. Thank you @phucnm for the help, he said he only removed Info.plist from Compile Sources in Build Phases settings, and that allowed ActionKit to function on the new build system.


## License

Licensed under the terms of the MIT license. See [LICENSE](LICENSE) file
