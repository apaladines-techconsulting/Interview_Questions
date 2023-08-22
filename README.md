# Elev Speech:

- Hello, I'm an accomplished iOS developer with over 8 years of experience,
- Worked on 5 published mobile applications. My expertise spans Swift, Objective-C, and NodeJS, flutter and React-Native
- With in-depth knowledge of various design architectures like MVVM and VIPER.
- Well-versed in UI/UX development, utilizing both programmatic and storyboard approaches.
- Worked with data persistence like CoreData, Realm, UserDefaults, Keychain, 
- Focus on performance optimization using multithreading and GCD.
- Commonly worked RESTful APIs 
- CoreGraphics, CoreAnimation, and CoreLocation, MapKit.
- I'm committed to best practices, unit testing (TDD XCTest),
- Continuous integration (Jenkins and fastlane, 2. AzureCI, CircleCI, Bitrise, TravisCI, GitHub Actions, Bitbucket Pipelines).

# Exp:
- Northwest Bank, Warren, Pennsylvania - 02/2022 – Current (Remote).
    - Redesign from UIKit to swiftUI
    - MVVM  -> Async Await; Combine; prop wrappers;
    - SDLC end-to-end
    - LLDB statements, register read, po, bt, expr
    - Test coverage of the App from 60% to 70%
    - Worked with UX closelly

- Marriott International Inc., Bethesda, Maryland 06/2020 – 02/2022 (7750 Wisconsin Ave, Bethesta)
    - Same before
    - MapKit, CoreLocation, Keichain, Lottie.
    - CoreBluetooth
    - swiftLint
    - Agile Scrum
    - AES
    - GirHub
    - GDC

# Interview_Questions
Collection of possible questions for Senior iOS Devevelpers

## OOPS:
- Object-Oriented Programming
    - Encapsulation -> Hidding attributes;
    - Inheritance -> Creating sub classes from superclass
    - Polymorphism -> Subclasses can be treated as objects of a common superclass
    - Abstraction -> Interfaces.- protocols

## Dependency injections
- function injetion
- parameter injection
- constructor injection


## Protocols:
Protocols are a blueprint to implement methods, properties or requirements that a class, struct, or enum must adopt. They have no implementation of methods. The only case is for additional functionalities in an extension of the protocol.
Protocols can be composite like Codable that involves `Decodable & Encodable`.
Mostrly used in SwiftUI but also used in Swift, for NetworkManager to create fake and real managers for better testings. Dependency injections and indirectly used for test cases

```swift
protocol Vehicle {
    var numberOfWheels: Int { get }
    func start()
    func stop()
}

struct Car: Vehicle {
    var numberOfWheels: Int = 4

    func start() {
        print("Car started!")
    }

    func stop() {
        print("Car stopped!")
    }
}
```

## Extension:
As its word says, they are often used to extend the original functionality of an object.
Following the open close principle, open to extensions close for editing.
extensions in protocols -> to create optional functinoalities.


```swift
//Following the Vehicle's protocol:
extension Vehicle {
    func getWheelsPressure() -> String {
        "The PSI is right in every wheel."
    }
}
```

## Enums:
Enums are widely used for a finite set of values or states.
We have `Associative Enums` that can attach additional data to each case and `Raw Value Enums` 

```swift
enum Weather {
    case sunny(temperature: Double)
    case rainy(inchesOfRain: Double)
    case cloudy
}

let currentWeather = Weather.sunny(temperature: 78.4)

switch currentWeather {
case .sunny(let temperature):
    print("It's sunny with a temperature of \(temperature)°F.")
case .rainy(let inchesOfRain):
    print("It's rainy with \(inchesOfRain) inches of rain.")
case .cloudy:
    print("It's cloudy.")
}
```
## Closures:
Closures are blocks of code that can be passed around and used like variables. Capturing values from their context and and being used to perform actions. Closures are often used as arguments for functions and methods, making code more expressive.

```swift
// Custom closure type: (Int, Double) -> Double
typealias PriceCalc = (Int, Double) -> Double

// Custom closure implementation: Calculates the total price by multiplying itemCount and itemPrice
let totalPriceClosure: PriceCalc = { itemCount, itemPrice in
    return Double(itemCount) * itemPrice
}

// Function that uses the custom closure
func calcTotalPrice(itemCount: Int, itemPrice: Double, priceCalculator: PriceCalc) -> Double {
    return priceCalculator(itemCount, itemPrice)
}

// Using the custom closure
let itemCount = 5
let itemPrice = 10.0

let totalPrice = calcTotalPrice(itemCount: itemCount, itemPrice: itemPrice, PriceCalc: totalPriceClosure)
print("Total Price: $\(totalPrice)") // Output: Total Price: $50.0

```
`Non-escaping closures:`
A non-escaping closure is a closure that is guaranteed to be executed before the function it's passed to returns. In other words, the closure is not allowed to outlive the function that it's passed to. Non-escaping closures are the default behavior in Swift, and you don't need to explicitly mark them as non-escaping.


## Swift vs Objective-C:
Was developed from C and C++

`Swift` is a modern and expressive language with strong typing `(variables can be explicitly declared)` and Type Inference where swift's compiler can infer the data type of a variable based on its initial value. Error handling and optionals to enhance code reliability. ARC (Automatic Reference Counting) meaning automatic memory management.
typoe safety, type inference, generics, 
`Objective-C` is an established, dynamic language that integrates well with C. It offers powerful runtime features and is suitable for legacy projects. It can also be gradually adopted in Swift projects. 

Objg: Reference type, we need to manage the memory by ourselfs
Swift: Reference and 


OOPS on C and CPP

###### Objc:
- Everything is classes, theres no structs
- protocols
- category
- Enum -> But used with Int only

- Reference Type
    - NSString
    - NSArray
    - NSDictionary

NSNameSpace

Actor -> Only one trhead can change the value
weak -> 
strong ->
atomic -> Thread Safe: Only one trhead can change the value
nonatomic -> NONThread Safe: Multiple trheads can change the value

##### Swift:
* TypeSafety -> `var name = 10, true` We cannot assign different types to the same variable.

* TypeInference -> `var name = "ABC"`

- Optionals -> Internally it is an enum with two states (none and nil).
- Structs
- Generics
- Closures
- Higher Oreder Funcions (map, filter, sort)
- Extensions

- Value Types:
    - Array
    - String
    - Dictionary


- Objects can be null
- Objects can be nil


## Computed property and Lazy Property
//COMPLETE

## Struct vs Classes:
`Structs` are value type, meaning they can be copied and passed arround the code. Modifications in a copy don't affect the original. They do not support iheritance and are suitable for simple data models.
Trait safe one value can be acessed at time.
Structs are faster because they are put as stock in memory


`Classes` are reference type meaning multiple variables can point to the same object in memory, have inheritance, they are deallocable and often used for complex data models. 
Not trait, multiple values can be accessed at time.

## Value Type vs Reference Type:
`Value Type`:
    - Is a type of data that is copied when assigned to a new variable or passed as an argument to a function.
    - Each variable or instance of a value type has its own independent copy of the data, and changes made to one copy do not affect other copies.
    - Common examples of value types in Swift include basic types like integers, floating-point numbers, booleans, strings, arrays, and structs.
    
`Reference Type`: 
    - Is a type of data where variables or instances share a reference to the same underlying data in memory.
    - When a reference type is assigned to a new variable or passed as an argument, only the reference (memory address) is copied, not the actual data.
    - Changes made to one instance of a reference type will be reflected in all other instances that share the same reference.
    - Common examples of reference types in Swift include classes and closures.
    
## Multithreading or threading options in iOS:
1. GCD -> Grand Central Dispatch
2. OperationQueue
3. Await Async
4. Actor
5. Thread
6. Semaphore
7. Defer

DispatchWorkItem
DispatchGroup


#### GCD:
It allows you to perform tasks concurrently by dividing them into smaller blocks and submitting them to queues that can be concurrent or serial.(main queue as maint thread).
- `main` -> Serial queue.
- `global` -> Concurrent queue.
- `custom` -> Serial or Concurrent depending on the requirement.
    Threads can be:
    `Concurrent` -> 
    `Serial` -> 

`GCD - QoS (1 for the most prioritary and 4 for less priority)`:
1. `User Interactive` => For animations or any kind of user related job with direct UI interactions.
2. `User Initiated` => When user requires imediate results, scrolling tableview for pagination or pull to reload
3. `Default` => Falls between UserInitiated and Utility.
4. `Utility` => tasks which are long running, like downloading files.
5. `Background` => Something which is not visible to user like creating backups, restoring from server/ syncing like retrieving data from google cloud, etc.
* `Unspecified` => This has the last priority.

#### OperationQueue:
Manages the execution of tasks as individual Operation objects.
Tasks as Operations.
Concurrency Control.
Dependency Management.
Prioritization.
Cancellation.
Completion Block.

#### Await Async:
Commonly used in api calls, get data from a file, getting data from keychain.
`Sync` -> Blocks everything after it is finalized. One thing at time.
`Async` -> Allows to continue with the application and run things in.

#### OperationQueue:
Are nothing but tasks. They have the ability to add dependency, pause, stop and resume.
OperationQueue is a high-level iOS mechanism that manages the execution of tasks (operations) concurrently. It provides control over task order, cancellation, and prioritization, making it easier to handle complex and structured operations compared to using GCD directly.
you can priorityze the sequences
you can add operation dependency 
you can add, resume, notify, cancel threash.

```swift
//Generating simple tasks:
let prepareLettuces = BlockOperation { print("Preparing lettuce 🥬") }
let prepareOnion = BlockOperation { print("Preparing Onion 🧅") }
let prepareTomatoes = BlockOperation { print("Preparing Tomatoes 🍅") }

//Adding dependency:
prepareTomatoes.addDependency(prepareOnion)
prepareLettuces.addDependency(prepareOnion)

//Creating control:
let opQueue = OperationQueue()
opQueue.maxConcurrentOperationCount = 1
opQueue.addOperations([
    prepareLettuces,
    prepareOnion,
    prepareTomatoes
], waitUntilFinished: false)

//Output: Preparing Onion 🧅
//Output: Preparing lettuce 🥬
//Output: Preparing Tomatoes 🍅
```

#### Await Async:
A simplified approach for asynchronous programming such as network requests, file operations, or database queries. Instead of using callback closures, delegates, or completion handlers.

#### Actor:
Actors encapsule mutable state within a protected boundary, ensuring that only one task (actor) can access that state at a time, eliminatiing potential data races and synchronization issues.

#### Thread:
They are the old way to use concurrency in app to handle networking, background processing, and UI updates. using them directly can be complex increasing the probability for data races and deadlocks.

#### Semaphore:
Semaphore is used in concurrent programming. Acts as a gatekeeper, regulating the number of threads or processes allowed to access a particular resource at any given time.
`Binary Semaphore`: Also known as a mutex (short for mutual exclusion), this type of semaphore has a maximum count of 1. It means only one thread or process can access the resource at a time. Binary semaphores are typically used to protect critical sections of code, where only one thread should be executing at any given time.
`Counting Semaphore`: This type of semaphore has a specified maximum count greater than 1. It allows multiple threads or processes to access the resource simultaneously, up to the maximum count. Counting semaphores are often used to control access to resources that can handle a limited number of concurrent users, like limiting the number of connections to a database or controlling access to a pool of shared objects.

## Generics:
Generics represent any tyoe of data you define to mqke reusable and modular the functionality of the code.
You can ad restrictions like T: Decodable to specify a particular behaviour to the function.

## local storage options in iOS:
1. UserDefaults => @AppStorage -  It is used to store small information in app like bool, string, int, double, etc. Just simple values.
2. KeyChain => To store critical sensitive user data like password, certificates, cryptographyc keys and so on.
3. CoreData => Coretada by default runs in main thread.
    * Migrations:
        1. Ligh weighth migration -> automatic migration, when you create a version n from the first database with Editor -> Add New Model Version.
        2. Heavy weight migration -> manual migration -> We write the migration login in appDelegate.
 
     * CoreData Concurrency: CoreData provides 2 ways of concurency for managed object models:
        1. NSMainQueueConcurancyType -> All operations happens on main thread by default.
        2. NSPrivateQueueConcurancyType -> Everything related to coredata will be done in background thread. This is for larger projects when we are managing large amounts of information.

4. Bundle and some files => json, text,
5. `.plist` => stored property lists inside the project
6. Realm - 3rd party option to save data locally in our app.

#### CoreData Stack:
    Managed object context -> Is the workhorse of the Core Data stack. It is the object of the Core Data stack you, the developer, interact with most
    Persistent store coordinator -> It keeps a reference to the managed object model and the managed object context. And, as the name implies, the persistent store coordinator is in charge of the persistent store of the application.
    Managed object model -> An instance of the NSManagedObjectModel class, loads the data model and exposes it to the Core Data stack.

By default CoreData run in main thread, a better practice is to run it in privateContext that means background.

![image](https://github.com/apaladines-techconsulting/Interview_Questions/assets/138136886/de399225-5933-4f5b-afd2-0cc90ac5c10b)

#### CoreData Concurrency:

![image](https://github.com/apaladines-techconsulting/Interview_Questions/assets/138136886/6e4c2f3a-4a80-4d40-b0fe-50053a40ee79)


## App Life cycle States:
- `Not Running:`
    The app is not launched or is terminated by the system or the user.
    No processes or code are running for the app.

- `Inactive:`
    The app is in the foreground but not receiving events (e.g., during a phone call or when the system interrupts it).
    Transitioning to Active or Background state.

- `Active:`
    The app is in the foreground and actively responding to user interactions.
    It is in the front and is the currently active app.

- `Background:`
    The app is in the background, either after the user switches to another app or when the system starts it in the background.
    Limited time for background execution (e.g., for tasks like audio playback or location updates).
    May be moved to Suspended state if resources are needed by other apps.

- `Suspended:`
When we receive a call, the application is get suspended, stoping all inside the app, after the call is finalized, 
    The app is in the background but is not executing code.
    In this state, the app is in memory but not actively running.
    It can be terminated by the system if resources are needed.

- `Terminated:`
    The app is not running at all, not in memory, and not receiving any events.
    Only a terminated app can be in this state.

## Declarative and imperative codibg

## Initializers or Inits
memberwise (structs)
default initializers
failable required
required initializers

## Combine:
 
 It is a native framework made by Apple for Reactive development programming introduced in iOS 13.0
 Before Combine, there were two frameworks, RXSwift and RXCocoaTouch.
 You can use combine to make the code simpler and reusable.

 - Publisher Subscriber Pattern
 - Observer Pattern
 if X things happen Y things will get triggered and happen.

 Three mayor components
 1. Publisher
 2. Subscriber
 3. Operator

 1. Publisher -> It is a protocol, it publishes the data.
  - It will be someone who will emit series of values over time.

 2. Subscriber -> It is a protocol, who will receive data sent by publisher

 Publisher and subscriber should have same or matching output and receive type.

 3. Operator -> This are methods that are called by Publisher they process the data in format in which subscriber needs

 We can also chain multiple operators on a Publisher.
 - Advantages of using Combine Framework:
    1. Your Async code is more simplified.
    2. Declarative syntax.
    3. Multithreading -> it handles concurancy by itself.
    4. Cancelation support.
    5. Built in memory management 

- Property Wrappers:
  1. @State
  2. @ObservedObject
  3. @StateObject
  4. @Binding
  5. @EnvironmentObject
  6. ObservableObject -> This is the protocol to create

 Difference between
     @StateObject -> Only recreates a part of the view
     @ObservedObject -> recreates everything
     
#### Common higher methods to use in Combine:
- `.tryMap` -> To map data.
- `.decode` -> Parsinng.
- `.receive` -> Receiving actual output.
- `.sink` -> getting completion (data, error) (CORRECT THIS PART).
- `.store` -> to clear out memory references, to deinitialize a reference or to cancel any task.
- `.map` -> transforms the emitted values from one type to another using a transformation closure.
- `.merge` -> To mix multiple streams.
- `.debounce` -> to delay responses.
- `.throttle` -> limits the rate of values emitted by a publisher.

## ArchitecturePatterns -> One Single for whole project:
1. MVC
2. MVVM -> Model View ViewModel
3. MVVM-C -> Model View ViewModel Coordinator (Coordinator Pattern)
4. MVP -> Model View Presenter (this is an old arq not much used now)
5. TCA -> Clean Architecture
6. VIPER -> View Interactor Presenter Entity Router

### Design Patterns:
Group of smaller related classes, modules or sub functionalities inside one project. In one project can be multiple Design Patterns used:

 1. `Creational Design Patterns` -> Anything related to Object creation of class, comes under this category (one to one comunication, one to many, etc).
 2. `Behavieour Design Patterns` -> How your projects are going to comunicate or pass data around or bahave.
 3. `Structural Design Patterns` -> How you assemble objects and classes into a larger group.

 A. Creational Design
    1. Singleton
    2. Factory Design Pattern / Factory Method
    3. Builder
    4. Prototype

 B. Behavioural Design Pattern
    1. Observer Pattern
    2. Chain of responsibility
    3. Memento
    4. Iterator

 C. Structural Design Pattern
    1. Adaptor pattern (Protocol delegate)
    2. Decorator
    3. Facade Design Pattern



 Singleton Pattern
 It ensures that only one object of class will be there thoroutghout our app
 It provides global access to that instance

 DataManager
 AuthenticationManager
 FileDownloaderManager
 AnalyticsManager

 Advantages:
    make it easy
    gives global access

 AntiDesign Pattern
    cannot have
    needs to be used carefully
    cannot write test cases



## Closure pattern:
Is just the same closures we use as parameters or variables.
It is used to send data back to the class that is implementing the closure. they can be scapping and nonScapping.

#### RXSwift and RXCocoaTouch:
- Major components:
    1. Schedulers
    2. Observables
    3. Operators

## Memory Management:
Whow iOS Does Memory Management
 ARC - Automatic Reference Counting

 Objective and swift it works automatically

 Initially the Reference count will mbe zero

 var gretings = "Hello World"
 Reference count = Reference count +1
 Reference count = 1

 gretings = nil
 Reference count = Reference count -1

 Reference count = 0
 Thats when OS free that block of memory

 It keeps the track of references to objects and releases them when they are no longer needed.

### Type of reference variables:
- strong -> This is the default attribute. It keeps those objects alive in memory.
- weak -> When we don't want to have ownership of that object. To avoid cycle issues as well.
- unowned -> Similar to weak but complusionb is that it should always have data. otherwise it can cause crashes in app.

 Retain cycle -> When one strong object retains another strong object, then, it creates retain cycle issues of memory leaks.

##  Repository Pattern: 
This provides an abstraction layer between the data storage (API / CoreData) and rest of aplication
 
## Clean Architecture:
Its like Onion (multiple layers) or Layer Archiqtecture.
All Business logic will be the center of your core
 
- Entities -> This is our business logic and are at core of clean arch
- Uses Cases -> (interactor / Repository) -> Will contain the rules or flow of data between entities.
- Interface Adapter -> (Presenters, Controllers and ViewModels) 
- Frameworks and Drivers -> UI, Database, Webservice, Analytics and all external third party frameworks.

MVVM vs Clean Architecture
We can go with mvvm and create a Clean Architecture.
 
 
 
## SOLID

S -> `Single Responsibility`: It states that, any function or class should only do one task.

O -> `Open Close Principle1`: Open for extension but closed for modification.

L -> `Liskov Substitution Principle`: Parent class objects should be easily replasable with child or derived object.

I -> `Interface Segregation`: Clients should not be forced to depend upon interfaces they don't requiere. Instead of having one big protocol, divide multiple small protocol.

D -> `Dependency Inversion`:  Different parts of your code should not depend on concrete classes.

 - Liskov
 ```swift
class Parent{
    var data: Data? 
}
class Child: Parent {

}
let data = dataFromService()
let parent = Parent(data: data)
let child = Child(data:data)
 ```
 
- Interface Segregation

Instead of:
 ```swift
protocol A {
    func a()
    func b()
    func c()
    func d()
    func e()
}
```

do this:
```swift

protocol A {
    func a()
    func b()
    func c()
}
protocol A {
    func d()
    func e()
}
 ```
 Because we wont need every function in every class that consforms the protocols.
 If there is a case, we can use `class Parent: A,B { ... }` or `public typealias Codable = Decodable & Encodable` for `class A: Codable`
 
 - Dependency Inversion
 Send object from outside, not defining objects inside the function, like the networkManager (protocols) that is sent in the init and not instanciated in function.

* Too much abstractions could make the code more complicated instad of facilitating the coding time to developers.


# iOS Security:
    1. Data Storage Security
    2. Network layer Security
    3. Jailbroken Detection
    4. Development techniques or best practices

## 1. Data Storage Security:
    a. UserDefaults -> Don't store sensitive data here
    b. Keychain -> To store small sensitive data
    c. CoreData -> We can use `SQLCipher` or sqlite file we can set a value for key `NSPersistenStoreFilePRotectionKey` to store data in a secure way.
    d. plist -> Save tokens and API keys in plist not in code directly (like google plist file).
    e. bundle -> Use `completeFileProtection` flag for writing files in your app.
        - Complete 
        bundle:
        ```swift
            func saveFileWithProtection() {
                do {
                    let bundle = Bundle(for: NetworkManager.self)
                    let fileURL = URL(string: "xyz")!
                    let data = "someData".data(using: .utf8)
                    try data?.write(to: fileURL, options: .completeFileProtection)
                } catch {
                    print(error.localizedDescription)
                }
            }
        ```

## 2. Network Layer Security - SSL/Certificate Pinning:

SSL Pinning is a mechanism used in ios to ensure the authenticity and integritty of server certificate durint api calls

we are adding an extra layer of security to our app's network communications by ensuring that the servers certificate is trusted and has not been tampered

### Certificate Pinning
1. Certificate Pinning
2. Public Key Pinning

 1. Certificate Pinning:
    Create server trust
    Certificate
    SSL Prolicy for domain name check
    evaluate server Certificate
    local Certificate
    Comparing data of local an remote server certificates

 2. The public key pinning:
    a. priate jey
    b. multiple public key

#### 2. ATS -> App Transport Security: By default requires https request.
- It doesn't allow any http connections happen in your app.
    
#### 3. Authentication Frameworks
    a. OAuth - Oauth2.0 -> Most common Industry standard:
        - Access Token
        - Refresh Token
    b. OKTA (SSO): Single Signing ???
    c. Apple Sign In:
    d. Firebase Authentication:
    
You can use your own Authentication Frameworks build by your backend team.

Third Party Frameworks:
Alamofire
TrustKit

### CryptoKit // -> 2019 (iOS 13)
 This will be helpfull to encryp and decrypt data (ecample in `NetworkManager.swift`)
- AES
- SHA

```swift
func encryptDataUsingCryptoKit() {
    let dataTOEncrypt = "Test Data".data(using: .utf8)!
    let sha256Hash = SHA256.hash(data: dataTOEncrypt)
    let sha384Hash = SHA384.hash(data: dataTOEncrypt)
    let sha512Hash = SHA512.hash(data: dataTOEncrypt)
}
```
SwiftUI vs Swift
- Everything made with structs Tsack memory (faster) instead of classes Heat memory
- More updated
- We use code instead of UIKit (storyboards)
- Protocol oriented programming instead of Swift that is oop
- We dont have constraints nor autolayout in swiftUI


## 3. Jailbroken Detection:
There is a preatty standard file that helps us with this task `JailbrokenCheck.swift`
SwiftUI:
```swift
    var body: some Scene {
        WindowGroup {
            if UIDevice.current.isJailBroken {
                EmptyView()
            }else {
                MainPageView()
                    .environmentObject(Coordinator())
            }
        }
    }
```

## 4. Development techniques or best practices:
Taking in cosideration all the past mentioned practices.
- Development Techniques:
    Deleting all prints and replacing it with a log file if necessary.
    Using `#if DEBUG` if prints are necessary in development mode.
    Following guidelines in [auth0.com](https://auth0.com/blog/security-best-practices-in-ios/)
    Synopsys.com -> Black Duck Software Comsposition Analysis.


# CI/CD

Everything  like building the app, running test cases, creating archive for app, and submiting build to testFlight, etc. will be automatically.

1. Jenkins and Fastlane
2. AzureCI
3. CircleCI
4. Bitrise
5. TravisCI
6. GitHub Actions

- Jenkins and Fastlane.
Jenkins -> 3rd party server tool for continuous integration.
Fastlane -> 3rd party tool for continuous delivery.
        Gemfile file with its own dependencies.
        fastlane/Fastlane directory and file.


## Test Testing TDD (test driven)BDD
TDD Test Driven Development:
XCTest
    Stubbing, bocking, Faking

BDD: Behavioural Driven Development:
    Quick and Nimble -> Start with given (setting up) when () and then ()

