# Swift Resume

[![License](http://img.shields.io/badge/license-MIT-green.svg?style=flat)](https://github.com/jimmyaat10/SwiftResume/blob/master/LICENSE)

## Disclaimer

This repository will try to collect links to different useful things&topics in swift (libraries, frameworks, utils, pro tips, patterns, links to conferences, books ...). 

For the Code Snippets I add a script addSnippet.sh. Run the script in the current folder of the script to add the snippet to Xcode. To use it, search for AAT.

If you think something is wrong or missing, feel free to send a PR :)

For an extended list of libraries, check [Awesome Swift List Resources](https://github.com/matteocrippa/awesome-swift) or [Another Awesome Swift List](https://github.com/Wolg/awesome-swift). This repository doesn't pretend to copy it, it's just my personal resume :)

## Resume

Ordered Alphabetically

- [3D Touch](#3DTouch)
- [Analytics](#Analytics)
- [Animations](#Animations)
- [Apple Pay](#ApplePay&Wallet)
- [Architecture](#Architecture)
- [Audio](#Audio)
- [AutoLayout](#AutoLayout)
- [CI](#CI)
- [Concurrency](#Concurrency)
- [CoreData](#CoreData)
- [Extensions](#Extensions)
- [Game](#Game)
- [Git](#Git)
- [Inspiration](#Inspiration)
- [IOS 11](#IOS11)
- [MapKit](#MapKit)
- [Networking](#Networking)
- [Notifications](#Notifications)
- [Patterns](#Patterns)
- [Realm](#Realm)
- [RxSwift](#RxSwift)
- [Social](#Social)
- [Search](#Search)
- [Swift4](#Swift4)
- [Testing](#Testing)
- [UserDefaults](#UserDefaults)
- [Video](#Video)
- [Xcode Tips](#Xcode)

## 3DTouch

- Libraries
	- [QuickActions](https://github.com/ricardopereira/QuickActions) 
	- [3D Touch in Simulator](https://github.com/AndreasVerhoeven/AveSimulator3DTouch)
- Conferences
	- [RWDevCon 2016 - Part 14: 206: 3D Touch](https://videos.raywenderlich.com/courses/59-rwdevcon-2016-vault/lessons/14)
	- [NSMeetup Video - Ryan Nystrom - Lessons Learned with 3D Touch at Instagram](https://www.youtube.com/watch?v=GCpwAuv_Avw)
- Keywords
	- QuickActions (Static, Dynamic), UIApplicationShortcutItem, [Peek&Pop](https://krakendev.io/peek-pop/) (UIViewControllerPreviewingDelegate)  
	- `view.traitCollection.forceTouchCapability== .available`  

## Analytics

- Libraries
	- [ARAnalytics](https://github.com/orta/ARAnalytics). Abstraction for different services. [Code Example](https://github.com/artsy/eidolon/blob/master/Kiosk/App/AppDelegate.swift)
	- [Google Reporter](https://github.com/ksmandersen/GoogleReporter). Use Google Analytics without download Google SDK! 

## Animations

- Libraries
	- [Spring](https://github.com/MengTo/Spring)
	- [EasyAnimation](https://github.com/icanzilb/EasyAnimation)
	- [Lottie](https://github.com/airbnb/lottie-ios) . Library that natively render After Effects vector animations
- Good lectures
	- [WWDC 2017 - Session 235 - Building Visually Rich User Experiences](https://developer.apple.com/videos/play/wwdc2017/235/)
		- 23m30s CoreAnimation Best Practices
			- If animation happens and come back, the problem is the model
			- Dont' do -> `animation.removedOnCompletion = false; animation.fillMode = kCAFillModeForwards`
			- Set the models property after the animation, so apply final state when adding animations
				- 	`let animation = CABasicAnimation(keyPath: "opacity"); animation.duration = 0.5; animation.fromValue = 1; animation.toValue = 0 //important ; layer.add(animation, forKey: nil); layer.opacity = 0 //important`   
			- Transforms and Frames
				- Frame is affected by transform
				- Set bounds/position directly instead  
			- Multiple Masks affect to performance, use shortcuts
			- Layer Shadows affect performance, use shadow paths 
	- [Clear Animation Code](http://ronnqvi.st/clear-animation-code/)
	- [Multiple Animations](http://ronnqvi.st/multiple-animations/)
	- [Youtube Channel Big Mountain - Transitions](https://www.youtube.com/watch?v=Psp0pzbwAWY)
		- Transitions happen in the superview
		- option showHideTransitionViews to not remove the view from superview 
	- [Youtube Channel Brian Advent - Lottie](https://www.youtube.com/watch?v=ESjFEaZx7UI&list=PLY1P2_piiWEaaeO49ria36p6lQ1uk0q_F&index=2) 
- Notes
	- ios10 Property Animator. Control the animations when happening (reverse, pause) 
	
## ApplePay&Wallet

- Tutorials
	- [RW Tutorial 2014](https://www.raywenderlich.com/87300/apple-pay-tutorial)
- Libraries
	- [Stripe](https://github.com/stripe/stripe-ios) 
- Keywords
	- PassKit, PKPaymentRequest, PKPaymentAuthorizationViewController, PKPaymentAuthorizationViewControllerDelegate, PKShippingMethod, PKPaymentSummaryItem 

## Architecture

- Conferences
	- [RWDevCon 2016 - Part23 - 307 - Architecting-for-Multiple-Platforms](https://videos.raywenderlich.com/courses/59-rwdevcon-2016-vault/lessons/23)
		- Create Frameworks/Targets to share code (DRY) between platforms (iOS, App Extension, tvOS, watchOS) and import depends platform with preprocessor macros like `#if os(tvOS) import MyAppKitTv #else import MyAPpKit #endif`
		- Compatibility
			- Models/Network shared everywhere
			- UIKit not in tvOS
				- touchUpInside / primaryActionTriggered 
			- Controls
				- touchesBegan, pressesBegan (tvOS) 
			- Particular StoryBoard for every platform 
		- Protocol & Protocol Extension to decorate a target with specific behavior
	- [RWDevCon 2016 - PART 22: 306: MVVM in Practice](https://videos.raywenderlich.com/courses/59-rwdevcon-2016-vault/lessons/22)
		- [Boxing](https://github.com/jimmyaat10/SwiftResume/blob/master/Resources/Codes/Architecture/Box.swift) for [bindings](https://github.com/jimmyaat10/SwiftResume/blob/master/Resources/Codes/Architecture/Box_Binding.png)  
	- [RWDevCon 2017 - PART 7: Building Reusable Frameworks](https://videos.raywenderlich.com/courses/81-rwdevcon-2017-vault-tutorials/lessons/7)  
- iOS Good lectures
	- [Flow Controllers for Navigation](http://merowing.info/2016/01/improve-your-ios-architecture-with-flowcontrollers/) 
	- [MV(x)](https://techblog.badoo.com/blog/2016/03/21/ios-architecture-patterns/)
	- [Objc.io - MVVM at KickStarter](https://talk.objc.io/episodes/S01E47-view-models-at-kickstarter)
- General Good lectures
	- [Clean Architecture - Uncle Bob](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html)
	- Book - Working Effectively with Legacy Code (Michael C. Feathers)
	-  Book - Clean Code Robert C. Martin
	-  Book - Refactoring Martin Fowler

## Audio

- Libraries
	- [AudioKit](https://github.com/audiokit/AudioKit)
	- [SwiftySound](https://github.com/adamcichy/SwiftySound)
	- [More in CocoaControls](https://www.cocoacontrols.com/search?q=audio) 
- Snippet 
	- [AVFoundation - AVAudioPlayer Snippet Code - AAT AVAudioPlayer](https://github.com/jimmyaat10/SwiftResume/blob/master/Resources/CodeSnippets/Audio/AVFoundation_AVAudioPlayer.codesnippet)
- Code Examples 
	- [Audio Player with Lock screen controls](https://github.com/lukagabric/LGAudioPlayerLockScreen)
		- [AudioPlayer](https://github.com/jimmyaat10/SwiftResume/blob/master/Resources/Images/Audio/AudioPlayer.png)
		- [AudioPlayer Device Locked](https://github.com/jimmyaat10/SwiftResume/blob/master/Resources/Images/Audio/AudioPlayer_DeviceLocked.png)	 
	- [Radio APP Example](https://github.com/swiftcodex/Swift-Radio-Pro)
	- [Record Audio](https://github.com/twostraws/HackingWithSwift/blob/master/project33/Project33/RecordWhistleViewController.swift) - Hacking with Swift - Project 33
- SpriteKit
	- Example in Hacking with Swift - Project 17: Swifty Ninja. [Code](https://github.com/twostraws/HackingWithSwift/blob/master/project17/Project17/GameScene.swift)
	- `run(SKAction.playSoundFileNamed("nameFile.extension", waitForCompletion: false))`
- Keywords
	- Capability for Audio Background Mode
	- AVFoundation
		- AVAudioSession, AVAudioSessionInterruptionOptions  
	- MediaPlayer
		- MPRemoteCommandCenter, MPNowPlayingInfoCenter, MPMediaItemProperty (Metadata), MPMediaItemArtwork, MPNowPlayingInfoProperty
- Speech ios10
	- [RayWenderlich ScreenCast Live Speech Recognition](https://videos.raywenderlich.com/screencasts/456-ios-10-live-speech-recognition)
	- [RayWenderlich ScreenCast File Speech Transcription](https://videos.raywenderlich.com/screencasts/430-ios-10-audio-file-speech-transcription)
- [RayWenderlich Course](https://videos.raywenderlich.com/courses/14-beginning-audio-with-avfoundation/) - Recording & Playback, Controlling Audio, Audio Effects, Speech Synthesis
	
## AutoLayout

- Libraries
	- [Cartography](https://github.com/robb/Cartography)
	- [SnapKit](https://github.com/SnapKit/SnapKit)
- Books
- Conferences
- Good to see
	- [Youtube Channel Lets Build that APP](https://www.youtube.com/channel/UCuP2vJ6kRutQBfRmdcI92mA)
		- Autolayout by code with App Examples  
- Tutorials

## CI

- Conferences
	- [AltConf - Continuous Delivery](https://news.realm.io/news/altconf-thomas-dohmke-continuous-delivery/) 
- [Blog Post - Xcode Server, Jenkins, Travis and fastlane](http://thebugcode.github.io/ios-continous-integration-choosing-a-build-server-and-tooling/) 
- [Fastlane](https://fastlane.tools/)
	- [Plugins](https://docs.fastlane.tools/actions/#plugins)
	- Tutorials
		- [Xcode 8.2, Swift 3 and Fastlane 2.6.0](http://getsharey.com/share/587ecddd4bae66.08736349)
		- [RWDevCon 2017 - PART 10: Fastlane](https://videos.raywenderlich.com/courses/81-rwdevcon-2017-vault-tutorials/lessons/10)
- Self Hosted
	- [Jenkins](https://jenkins.io/)
		- [Setup Jenkins](https://livetyping.com/en/blog/ios-ci)
		- [Blog Post in Spanish](http://mmorejon.github.io/blog/integracion-continua-jenkins-ios9-xcode/)
		- [Plugins](https://plugins.jenkins.io/) 
- Cloud
	- [BuddyBuild](https://www.buddybuild.com/)
		- [Udacity Free Course](http://blog.udacity.com/2017/01/continuous-integration-deployment-buddybuild.html)
	- [Travis CI](https://travis-ci.org/)
	- [Circle CI](https://circleci.com/) 

## Concurrency

- Good lectures
	- [GCD by John Sundell](https://www.swiftbysundell.com/posts/a-deep-dive-into-grand-central-dispatch-in-swift)
- Conferences
	- [RWDevCon 2017 - PART 4: iOS Concurrency](https://videos.raywenderlich.com/courses/81-rwdevcon-2017-vault-tutorials/lessons/4)
- Tutorials
	- [RayWenderlich Course - iOS Concurrency with GCD and Operations](https://videos.raywenderlich.com/courses/55-ios-concurrency-with-gcd-and-operations/lessons/1)  
		- Tasks, Operation, OperationQueue, AsyncOperation, Dependencies, Canceling Tasks, Operations In Practice, Concurrency Solutions 
- Notes 
	- Dispatch barrier lets finish the tasks in the queue and when the barrier task finished, lets enter more tasks in the queue. Good options is to wrapper with an isolationQueue
	- Found race conditions with Scheme - Run - Thread Sanitizer
	- Operations queue is like dispatch but you can create dependencies and change the order they run
	- In Xcode9, there's a default main thread checker

## CoreData

- [Today Extension with CoreData](https://videos.raywenderlich.com/courses/16-ios-app-extensions/lessons/8)


## Extension

- Libraries
	- [EZSwiftExtensions](https://github.com/goktugyil/EZSwiftExtensions) 


## Game



## Git

- Good to see
	- [RWDevCon 2017 - PART 6: Mastering Git](https://videos.raywenderlich.com/courses/81-rwdevcon-2017-vault-tutorials/lessons/6)
	- [Git Flow](https://danielkummer.github.io/git-flow-cheatsheet/)
	- [Practical Git(Hub) - by Xavier Jurado](https://speakerdeck.com/xavierjurado/practical-git-hub)

## IOS11

- [WWDC 2017 - Videos](https://developer.apple.com/videos/wwdc2017/)

## MapKit



## Networking



## Notifications



## Patterns

- Conferences
	- [RWDevCon 2016 - 201-Design-Patterns-in-Swift](https://videos.raywenderlich.com/courses/59-rwdevcon-2016-vault/lessons/9)
	- [RWDevCon 2017 - 20-Advanced-iOS-Design-Patterns](https://videos.raywenderlich.com/courses/81-rwdevcon-2017-vault-tutorials/lessons/20) 
- Good lectures
 	-  Book - Patterns of Enterprise Application Architecture - Martin Fowler
	- [Design Patterns in Swift](https://github.com/ochococo/Design-Patterns-In-Swift) with examples
	- [Composition - Mixins over Inheritance](http://alisoftware.github.io/swift/protocol/2015/11/08/mixins-over-inheritance/)
	- [8 Patterns to avoid Massive View Controller](http://khanlou.com/2014/09/8-patterns-to-help-you-destroy-massive-view-controller/)
	-  [Generic Delegates in Swift](https://152percent.com/blog/2017/4/11/delegates-in-swift)

Personally I like Composition with Dependency Injection, which implicitly uses some other patterns (Façade, Strategy). 

Good lecture to leverage protocol composition to make our maintenance cost lower and even increase readability -> [Protocol Composition for DI](http://merowing.info/2017/04/using-protocol-compositon-for-dependency-injection/)

For example:

`init(apiService: ApiServiceType, persistence: PersistenceType)`

Here we are injecting dependencies with the protocols for Api and Persistence.

The protocols (Façades) declares some methods.

We can provide different implementations for the Types depends of the target for the App or Test (Strategy).

Typically the ApiService implementation will use [networking](#Networking) to call the WS and the ApiServiceMock implementation in the [test](#Testing) will use local json to simulate the WS call.

Another example is the [Persistence](https://github.com/jimmyaat10/MarvelSwift/blob/master/Marvel/Persistence/PersistenceManager.swift), the implementation for the App will use [Realm](#Realm) or [CoreData](#CoreData) with a database and for the test target we can instiantate the PersistenceMock with the test [configuration](https://github.com/jimmyaat10/MarvelSwift/blob/master/Marvel/Persistence/RealmConfig.swift) which use inMemoryIdentifier to avoid conflicts.

## Realm



## RxSwift



## Search



## Security

- Good Lectures
	- [WWDC 2017 - Session 701 - Your Apps and Evolving Network Security Standards](https://developer.apple.com/videos/play/wwdc2017/701/) 
	- [Collection of the most common vulnerabilities found in iOS applications](https://github.com/felixgr/secure-ios-app-dev) 
	- [iOS Security basic](https://swifting.io/blog/2016/08/09/21-ios-security-101/)
	- [iOS Security 101](https://engineers.sg/video/ios-security-101-ios-dev-scout--1356)
	- [WWDC 2016 session - How iOS Security Really Works](https://developer.apple.com/videos/play/wwdc2016/705/)
	- [How to strictly secure sensitive data on 3rd party applications and implement your own encryption schema](https://swifting.io/blog/2017/01/16/33-security-implement-your-own-encryption-schema/)
	- [Vixentael Conference Slides](https://speakerdeck.com/vixentael)
	- [IOS Application Security Testing Cheat Sheet](https://www.owasp.org/index.php/IOS_Application_Security_Testing_Cheat_Sheet) 
- Libraries
	- [KeychainSwift](https://github.com/marketplacer/keychain-swift) . Helper functions for Keychain
	- [CryptoSwift](https://github.com/krzyzanowskim/CryptoSwift) . Collection of secure cryptographic algorithms
	- [App Transport Security](https://useyourloaf.com/blog/app-transport-security/)
		- nscurl --ats-diagnostics https://url 

## Social

- Good to see
	- [Objc.io - DeepLink at KickStarter](https://talk.objc.io/episodes/S01E49-deep-linking-at-kickstarter)
- Pro Tips
	- Testing out custom URL schemes or universal links `xcrun simctl openurl booted myApp:url` where booted is the current opened simulator. You can replace booted for the Device UDID. To see the list `xcrun simctl list`

## Swift4

- [What's new in Swift - by WWDC 2017](https://developer.apple.com/videos/play/wwdc2017/402/)
- [What's new in Swift4 - by Oleb](https://github.com/ole/whats-new-in-swift-4)
- [What's new in Swift4 - by RayWenderlich](https://www.raywenderlich.com/163857/whats-new-swift-4)

## Testing

- Conferences
	- [WWDC 2017 - Session 414 Engineering for Testability](https://developer.apple.com/videos/play/wwdc2017/414/) 
	- [RWDevCon 2016 - PART 15: 207: Xcode UI Testing](https://videos.raywenderlich.com/courses/59-rwdevcon-2016-vault/lessons/15) 
		- accessibilityIdentifer (testing only, distinguish views) vs accessibilityLabel (testing & impaired users + Localized + find views)
- Good Lectures
	- [UI Test - John Sundell](https://www.swiftbysundell.com/posts/getting-started-with-xcode-ui-testing-in-swift)
		- `app.launchArguments.append("--uitesting")`
		- Reset state in didFinishLaunchingWithOptions `if CommandLine.arguments.contains("--uitesting") {
        resetState()
    }`  
- Pro Tips
	- A strategy to speed up tests is to speed up animations when running UITests `UIApplication.shared.keyWindow?.layer.speed = 100`	
	- [Abolish Retain Cycles in Swift with a Single Unit Test](https://www.jarroo.com/blog/2017/3/3/abolish-retain-cycles-in-swift-with-a-single-unit-test) 

## UserDefaults

- Libraries
	- [SwiftyUserDefaults](https://github.com/radex/SwiftyUserDefaults) 
		- Shared UserDefaults: `var Defaults = UserDefaults(suiteName: "com.my.app")!` 
- Testing
	- `userDefaults = UserDefaults(suiteName: #file)`
	- `userDefaults.removePersistentDomain(forName: #file)`

## Video



## Xcode

- Conferences
	- [RWDevCon 2016 - PART 16: 208: Xcode Tips & Tricks](https://videos.raywenderlich.com/courses/59-rwdevcon-2016-vault/lessons/16) 
		- Add Preference - Custom Behaviors with show/hide elements. For example when coding Hide Debugger & Utilities 
		- Alt+Shift and click a file to chose how to open it in the editor
		- Cmd + Shift + J: Jump to current file in Navigator 		- Cmd + Shift + Y: Finished debugging		- Alt in IB: Show distances between views 
		- Cmd + 1~8: Toggle between navigators
		- Cmd + [ or Cmd + ] to tabulate code
		- Alt + Cmd + / to add Documentation
- Pro Tips
	- Remove unavailable Xcode Simulators `xcrun simctl delete unavailable` 
	- Add actions to breakpoints (Double click in the breakpoint)
	- Drag the execution program counter when the app is running (Green arrow in the breakpoint)

## Inspiration

Inspirations from (ordered alphabetically):

- [AliSoftware](http://alisoftware.github.io/)
- [Arsty Blog](http://artsy.github.io/blog/archives/)
- [Awesome iOS](https://ios.libhunt.com/)
- [Awesome iOS Open Source Projects](https://github.com/dkhamsing/open-source-ios-apps)
- [Awesome Swift Resources List](https://github.com/matteocrippa/awesome-swift)
- [Awesome Swift List](https://github.com/Wolg/awesome-swift)
- [Cocoa Controls](https://www.cocoacontrols.com/controls?language=2-swift)
- [Cocoa with love](http://www.cocoawithlove.com/archive/)
- Conferences
	- [360iDev Videos](https://360idev.com/session-videos/) 
	- [AppBuilders 2016 Slides+Videos](https://github.com/swissmobidevs/appbuilders16) 
	- [AppBuilders 2017 Slides+Videos](https://github.com/swissmobidevs/appbuilders17)
	- [Cocoa Heads Fr Slides](http://cocoaheads.fr/slides/)
	- [DotConf Videos](https://www.dotconferences.com/talks)
	- [FrenchKit](http://frenchkit.fr/)
	- [NSSpain Summaries](https://github.com/NSSpain/NSSpain-Summaries) 	
	- [PragmaConf Videos](https://www.youtube.com/user/pragmamark/videos)
	- [RWDevCon](https://www.rwdevcon.com/)
	- [Swift Aveiro Videos](https://www.youtube.com/channel/UChcHSofZmxcG23iu_8muZqw)
	- [Try Swift](https://news.realm.io/news/try-swift/)
	- [UIKonf Videos](http://www.uikonf.com/videos/)
	- [WWDC Videos](https://developer.apple.com/videos/)
- [Erica Sadun Blog](http://ericasadun.com/)
- [Essential Developer](https://www.essentialdeveloper.com/articles/)
- [Greg Heo Blog](https://gregheo.com/)
- [Hacking with Swift](https://www.hackingwithswift.com/)
- [iOS Dev Weekly](https://iosdevweekly.com/)
- [Lets build that app](https://www.letsbuildthatapp.com/)
- [Little bites of cocoa](https://littlebitesofcocoa.com/)
- [Merowing Blog](http://merowing.info/post/)
- [Mike Ash Blog](https://www.mikeash.com/pyblog/)
- [Natasha the robot](https://www.natashatherobot.com/)
- [NSHipster](http://nshipster.com/)
- [Objc.io](https://www.objc.io/)
- [Quality coding](http://qualitycoding.org/blog/)
- [RayWenderlich](https://www.raywenderlich.com/)
- [Realm News](https://news.realm.io/news/tags/apple/)
- [Rx-Marin](http://rx-marin.com/)
- [Swift by Sundell](https://www.swiftbysundell.com/)
- [Swiftly Brief](https://swiftweekly.github.io/)
- [Swiftly Digest](http://digest.swiftweekly.com/)
- [Swift News](https://swiftnews.curated.co/)
- [Swift Unwrapped](https://spec.fm/podcasts/swift-unwrapped)
- [Xebia Blog](http://blog.xebia.com/?s=swift)
- [Youtube Functional Swift](https://www.youtube.com/channel/UCNFUO_7gsLBk4YTmZoSTk5g/videos)


##License

This project is released under the [MIT license](https://github.com/jimmyaat10/SwiftResume/blob/master/LICENSE).