# IBAnimatable
Design and prototype UI, interaction, navigation, transition and animation for App Store ready Apps in Interface Builder with IBAnimatable.

![](https://github.com/JakeLin/IBAnimatable/blob/master/Screenshots/IBAnimatable.gif)

**The app is made in Interface Builder with `IBAnimatable` without single line of code**. Due to the size of [the GIF file on Dribbble](https://dribbble.com/shots/2453933-IBAnimatable-Design-App-Store-ready-Apps-in-Interface-Builder), it only demonstrates a subset of features. We can also find the full HD version on [YouTube](https://www.youtube.com/watch?v=dvD8X6J1YLM) or [MP4 on Github](https://github.com/JakeLin/IBAnimatable-Misc/blob/master/Videos/IBAnimatable.mp4?raw=true)

![](https://github.com/JakeLin/IBAnimatable/blob/master/Screenshots/Storyboard.png)

Here is the design in Interface Builder (Storyboard).

With `IBAnimatable`, we can design UI in Interface Builder like Sketch, and prototype animations in Swift playground like Framer Studio. Also we can use the output of the design directly in the production ready App.

As a designer, we love Sketch, which is a simple but yet super powerful tool to design UI. However, Sketch can't design interaction, navigation, transition and animation, we may need another tool like Framer Studio to design some of them. Moreover, to make an App Store ready App, we need to use Xcode and Interface Builder to implement the UI and animations. To speed up the process and minimise the waste, we create `IBAnimatable` to make Interface Builder designable and animatable.   

## Languages
[中文](https://github.com/JakeLin/IBAnimatable/blob/master/Documentation/README.zh.md)

## Features
* From prototype to shippable App Store ready App - What you design in Interface Builder is what the App exactly looks like. 
* Designer friendly - Sketch style setting panel on Attributes Inspector to lower the learning curve for using Interface Builder.   
* Animation desigin support in Swift playground - Similar to Framer Studio, we can prototype animations in Swift playground to save time for runing on simulator or actual iOS devices. 
* Built-in Auto Layout support - We can use Auto Layout and Size Classes with `IBAnimatable` to support orientations and multiple iOS devices. 
* Navigation and transition support - We can use default navigation pattern in the App and `IBAnimatable` also adds unwind segues to navigate back or dismiss scene without any code. More transitions will be added soon.
* Protocol oriented programming - `IBAnimatable` used protocol oriented programming paradigm. With Swift protocol extension, it is easy to support more designable or animatable features. We can even use these protocol extensions to create other custom UI elements instead of using the default ones from `IBAnimatable`.  

## Use cases
* Prototyping - Create interactive proptotype to validate the idea quickly.
* Redesigning in Interface Builder - Redesign UI from Sketch and animation from Framer Studio without writing any code.
* Making custom UI elements - Use `IBAnimatable` protocols to make custom UI elements. eg. Buttons with default color palette.

## How to run example App
The easy way to learn and understand how powerful of `IBAnimatable`is to run the example App and play around the settings in Interface Builder. Just few steps we can run the App as below:

1) Clone the repository

```
$ git clone https://github.com/JakeLin/IBAnimatable.git
```

2) Open the workspace in Xcode

```
$ cd IBAnimatable
$ open "IBAnimatable.xcworkspace"
```

3) Compile and run the app in your simulator or iOS device

## How to design in Interface Builder
![](https://raw.githubusercontent.com/JakeLin/IBAnimatable/master/Screenshots/DesignInInterfaceBuilder.png)

To use `IBAnimatable` to design the UI and animations in Interface Builder, just follow few steps as below:

1. Open a storyboard or Xib file.
2. Drag and drop a UIKit element eg. UIView to a ViewController.
3. In Identity Inspector, connect the UI element to `Animatable` custom UI class eg. `AnimatableView`, you can find all `Animatable` classes in [APIs section](https://github.com/JakeLin/IBAnimatable#apis).
4. Configure the UI and animations in Attribute Inspector.


## How to animate in Swift playground
![](https://github.com/JakeLin/IBAnimatable/blob/master/Screenshots/AnimateInSwiftPlayground.gif)

We can configure the animation settings in Attribute Inspector. However, Interface Builder doesn't support previewing Animations, but we can still prototype animations in Swift playgournd. There are three sample pages to demostrate how to design animation in Swift playground. You can find them in [IBAnimatable.playground](https://github.com/JakeLin/IBAnimatable/tree/master/IBAnimatable.playground). Firstly, select one page in Swift playground, then click on "Assistant editor" button to split the playground. After that, select "Timeline" on the top of right-hand side to preview the animation. We can use Xcode menu "Editor" -> "Execute" to re-run the playground.

## How to animate programmatically
As you saw above, we can prototype an App fully in Interface Builder withouth single line of code, but `IBAnimatable` also provides APIs to let us fully control the UI and animations. `IBAnimatable` provides simple APIs like `pop()`. We can simplly call them in one line.

```
view.pop() // pop animation for the view
view.squeezeFadeInLeft() // squeeze and fade in from left animation
```  

You can play around all these predefined animations in [Swift playgournd Page - Predefined Animations](https://github.com/JakeLin/IBAnimatable/tree/master/IBAnimatable.playground/Pages/Predefined%20Animations.xcplaygroundpage)

### Animation properties
There are some properties we can change to customise the animation. What we need to do is to set the properties and call `animate()` method to start the animation.

```
// Setup the animation
view.animationType = "SqueezeInLeft"
view.delay = 0.5
view.damping = 0.5
view.velocity = 2
view.force = 1

// Start the animation
view.animate()
```

You can play around all animations with different properties in [Swift playgournd Page - Animation Properties](https://github.com/JakeLin/IBAnimatable/tree/master/IBAnimatable.playground/Pages/Animation%20Properties.xcplaygroundpage)

### Chaining animations
Sometimes, we need to run another animation after the previous one. With `IBAnimatble`, we can easily chain animations together to provide sleek user experience.

```
// Simplly put the next animation within `{}` closure as below. It is an example to pop the view after squeeze in from the top.
view.squeezeInDown{ view.pop() }

// Heaps of animations have been chained togehter, it is the source code of animated Gif in "Animate in Swift playground" section
view.squeezeInDown{ view.pop { view.shake{ view.squeeze{ view.wobble{ view.flipX { view.flash{ view.flipY { view.fadeOutDown() } } } } } } } }
```

## How to install
### Manually install
Copy and paste `IBAnimatable` folder in your Xcode project.

### Git submodule
TBD, more details on [Issue #22 - Swift package manager support](https://github.com/JakeLin/IBAnimatable/issues/22)

### Swift package manager
TBD, more details on [Issue #5 - Swift package manager support](https://github.com/JakeLin/IBAnimatable/issues/5)

### CocoaPods
TBD, more details on [Issue #7 - CocoaPods support](https://github.com/JakeLin/IBAnimatable/issues/7)

### Carthage 
TBD, more details on [Issue #6 - Carthage support ](https://github.com/JakeLin/IBAnimatable/issues/6)

## APIs

### Animatable UI elements 
The easiest way to use `IBAnimatable` is to drag and drop UIKit elements and connect with `Animatable` UI elements in Identity Inspector. Here are the supported `Animatable` UI elements to map UIKit elements.

| UIKit elements | Animatable UI elements | Remark |
| ------------- |:-------------:| ----- |
| UIView | AnimatableView | |
| UIBarButtonItem | AnimatableBarButtonItem | |
| UIButton | AnimatableButton | |
| UIButton | AnimatableCheckBox | Connect UIButton as AnimatableCheckBox to make CheckBox control |
| UIImageView | AnimatableImageView | |
| UILabel | AnimatableLabel | To style the text in Label, we can use Interface Builder built-in Attributed Text |
| UIStackView | AnimatableStackView | |
| UITableView | AnimatableTableView | |
| UITableViewCell | AnimatableTableViewCell | |
| UITextField | AnimatableTextField | |
| UITextView | AnimatableTextView | |
| UIView | DesignableGradientView | |
| UINavigationBar | DesignableNavigationBar | |
| UIViewController | DesignableViewController | |

### Designable protocols
`IBAnimatable` provides a set of Designable protocols as below. Because of the power of protocol oriented programming in Swift, we don't even have to use Animatable default UI elements eg. `AnimatableView` to unlocked the power of `IBAnimatable`. We can conform to `IBAnimatable` protocols to use the default implementation in protocol extension to create other custom UI elements.

#### `BarButtonItemDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| roundedImage | Optional&lt;UIImage> | By default, Interface Builder can only support outline images for Bar Button Item. With `roundedImage`, we can display a rounded image. The image can not be previewed in Interface Builder. |


#### `BlurDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| blurEffectStyle | Optional&lt;String> | Support three different blur effects: `ExtraLight`, `Light` and `Dark`. They ard defined in `BlurEffectStyle` enum. The look of blur effect in Interface Builder is different from Simulator or device. |
| blurOpacity | CGFloat | Opacity of the blur effect specified above. Default value is `CGFloat.NaN`, the value is from 0.0 to 1.0. |


#### `BorderDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| borderColor | Optional&lt;UIColor> | border color |
| borderWidth | CGFloat | border width. Default value is `CGFloat.NaN`, the value is greater than 0. |
| borderSide | Optional&lt;String> | border side, `Top`, `Right`, `Bottom` or `Left`. If not specify, then display four sides. |


#### `CheckBoxDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| checked | Bool | Default value is `false` |
| checkedImage | Optional&lt;UIImage> | The image to display when CheckBox is checked. |
| uncheckedImage | Optional&lt;UIImage> | The image to display when CheckBox is unchecked. |

#### `CornerDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| cornerRadius | CGFloat | rounded corner radius. Default value is `CGFloat.NaN`, the value is greater than 0. |

#### `FillDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| fillColor | Optional&lt;UIColor> | fill color of the UI Element |
| opacity | CGFloat | opacity, alpha of the UI Element, Dafault value is `CGFloat.NaN`, the value is from 0.0 to 1.0. |

#### `GradientDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| startColor | Optional&lt;UIColor> | start gradient color |
| endColor | Optional&lt;UIColor> | end gradient color |
| startPoint | Optional&lt;String> | start direction point, can find in `GradientStartPoint`. |

#### `NavigationBarDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| solidColor | Bool | whether to display solid color only. Default value is `false`. Need to manually untick translucent in Interface Builder, otherwise, it will have constrait issue in IB although it is correct in run time. |

#### `MaskDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| maskType | Optional&lt;String> | maks type, eg. `Circle`. |

#### `PaddingDesignable`
It is used in `AnimatableTextField` to add padding on either or both sides.

| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| paddingLeft | CGFloat | padding on left-hand side. Default value is `CGFloat.NaN`. |
| paddingRight | CGFloat | padding on right-hand side. Default value is `CGFloat.NaN`. |
| paddingSide | CGFloat | padding on both sides. Default value is `CGFloat.NaN`. |

#### `PlaceholderDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| placeholderColor | Optional&lt;UIColor> | placeholder text color in `AnimatableTextField`. |

#### `RootWindowDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| rootWindowBackgroundColor | Optional&lt;UIColor> | root window background color. Can be seen when we use flip transition. |

#### `RotationDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| rotate | CGFloat | rotation of the UI element in degrees. Default value is `CGFloat.NaN`, value is from 0 to 360. |

#### `ShadowDesignable`
Drop shadow of the UI element, it is popular in Material Design. These properties are not able to render in IB correctly, it maybe an Interface Builder's bug.

| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| shadowColor | Optional&lt;UIColor> | shadow color |
| shadowRadius | CGFloat | shadow corner radius. Default value is `CGFloat.NaN`, the value is greater than 0. |
| shadowOpacity | CGFloat | shadow opacity. Default value is `CGFloat.NaN`, the value is from 0.0 to 1.0. |
| shadowOffset | CGPoint | `x` is horizontal offset and `y` is vertical offset. |

#### `SideImageDesignable`
Display a side hint image in `AnimatableTextField`

| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| leftImage | Optional&lt;UIImage> | the image to display on the left-hand side. |
| leftImageLeftPadding | CGFloat | left padding of hint image. Default value is `CGFloat.NaN`. |
| leftImageRightPadding | CGFloat | right padding of hint image. Default value is `CGFloat.NaN`. |
| leftImageTopPadding | CGFloat | top padding of hint image. Default value is `CGFloat.NaN`. If not specified, the image will center vertically. |

#### `StatusBarDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| lightStatusBar | Bool | to display white or black text status bar. Default value is `false` to display black text. |

#### `TableViewCellDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| removeSeparatorMargins | Bool | whether to remove separator margins in `AnimatableTableViewCell`. Default value is `false`. There maybe a bug of Interface Builder when setting "Separator Insert" to 0 doesn't work. |

#### `TintDesignable`
Easily add color layer on top of the UI element especially `AnimatableImageView`.

| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| tintOpacity | CGFloat | opacity of tint color (white color). Default value is `CGFloat.NaN`. |
| shadeOpacity | CGFloat | opacity of shade color (black color). Default value is `CGFloat.NaN`. |
| toneColor | Optional&lt;UIColor> | tone color|
| toneOpacity | CGFloat | opacity of tone color. Default value is `CGFloat.NaN`. |

#### `ViewControllerDesignable`
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| hideNavigationBar | Bool | whether to hide navigation bar. Default value is `false`. |

### Animatable protocol
#### Properties
| Property name | Data type | Remark |
| ------------- |:-------------:| ----- |
| animationType | Optional&lt;String> | Supported animations. All supported predefined animations are in enum `AnimationType` |
| autoRun | Bool | Whether to automatically start the animation. Default value is `true`. if it is true, the animation will automatically run when the view is loaded. If want to manually start the animation should set it to `false`. |
| duration | CGFloat | Animation duration in seconds. Default value is 0.7. |
| delay | Double | Delay to start the animation in seconds. Default value is 0. |
| damping | CGFloat | Used in UIView Spring animation (0 ~ 1 seconds). To smoothly decelerate the animation without oscillation, use a value of 1. Employ a damping ratio closer to zero to increase oscillation. Default value is 0.7. Notice: FadeOutIn, FadeInOut, Shake, Pop, Morph, Squeeze, Flash, Wobble and Swing animations do not use damping. |
| velocity | CGFloat | used in UIView Spring animation. A value of 1 corresponds to the total animation distance traversed in one second. For example, if the total animation distance is 200 points and you want the start of the animation to match a view velocity of 100 pt/s, use a value of 0.5. Default is 0.7. Notice: FadeOutIn, FadeInOut, Shake, Pop, Morph, Squeeze, Flash, Wobble and Swing animations do not use damping. |
| force | CGFloat | used to apply force to the animation. The number is higher, the animation property has more changes. eg. for Pop animation, higher force causes the view poping bigger. Default value is 1. |
| repeatCount | Float | Used to sepecify the count to repeat the animation. Can noly used in Shake, Pop, Morph, Squeeze, Flash, Wobble and Swing animations. Default value is 1.  |

### Extension
#### UIViewController
With these methods, we can navigate back or dismiss current ViewController with any code in Interface Builder.

| Method name | Remark |
| ------------- | ----- |
| func unwindToViewController(sender: UIStoryboardSegue) | Used in Interface Builder to uswind from Naviagation Controller |
| func dismissCurrentViewController(sender: UIStoryboardSegue) | Used in Interface Builder to dismiss current ViewController |


## How to contribute
All of us can contribute to this project. Fewer overheads mean less time to build quality Apps and more time to enjoy coffee ☕️.

* If you are a designer, you can design in Interface Builder with `IBAnimatable` without designing tool like Sketch, or implement your existing design from Sketch or Photoshop in Interface Builder rapidly. With `IBAnimatable`, you should be able to do <del>all</del> most of design work in Interface Builder. If you have any feature request, please [create a GitHub Issue](https://github.com/JakeLin/IBAnimatable/issues/new) and we will put it in the backlog. If you have done any design with `IBAnimatable`, please let us know via creating Pull Request or GitHub Issue. We will add it to Readme file.

* If you are a developer, you can work on features or fix bugs, please check out [GitHub Issues](https://github.com/JakeLin/IBAnimatable/issues) to find out the backlog. If you have used `IBAnimatable` in your App, please let us know via creating Pull Request or GitHub Issue. We will add it to Readme file.

* If you are good at English, please correct my English 😁. If you are good at other languages, please create a Readme file in those languages.

* If you like the project, please share it with the other designers and developers, and star 🌟 the project. 🤗


## Inspirations
* `IBDesignable` and `IBInspectable` - The entire project is based on that.
* Sketch -  Interface Builder should be as easy as Sketch to use.
* Framer Studio - Design and preview animations in one place.
* [Spring by Meng To](https://github.com/MengTo/Spring) - steal a lot of animation parameters from this project.
* [Invision ToDo App UI Kit](http://www.invisionapp.com/do), The demo App's original design is from this UI Kit and redone in Interface Builder. We also added interaction, navigation and animations.

## License
`IBAnimatable` is released under the MIT license. See [LICENSE](https://github.com/JakeLin/IBAnimatable/blob/master/LICENSE) for details.

