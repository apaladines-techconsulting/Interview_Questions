# Posible Questions for an iOS developer (it doesn't mean this is all you have to know).

# My experience.

# Elevator Speech:

Hello, I'm Andres, an accomplished iOS Developer with over 8 years of experience crafting refined mobile applications. My track record includes 5 published and successful apps, showcasing my experience in Objective-C, UIKit and SwiftUI. 

My contribution on 'Northwest Mobile Banking' app was redesigning UI components and implementing MVVM architecture. At Marriott, I played a key role enhancing the 'Marriott Bonvoy' app implementing Apple accessibility APIs and migrating code from UIKit to SwiftUI. I also have experience with the Agile approach and have managed end-to-end development at companies like Cardinal Health and Floor & Décor.

I specialize in frameworks like UIKit, SwiftUI, Combine, CoreData, MapKit, CoreLocation and 3rd-party frameworks like AlamoFire and Firebase. I also excel at architecting solutions using design patterns like MVVM-C, VIPER and Clean Architecture. With a deep understanding of multithreading, I ensure seamless performance using GCD, Operation Queue, Actors and Await Async. While collaborating with cross-functional teams, I integrated CI/CD tools like Jenkins and Fastlane as part of my daily routine. Another part of my routine was managing version control with GIT. This included helping developers to deal with merge conflits and approving pull requests of previously reviewed code.

With my technical depth and more than 12 years in IT, I am ready to bring substantial value to your technical endeavours.

#### Jobs:
- Splendid Spoon, Minneapolis, Minnesota, U.S.- 02/2010 – 12/2014
- Hooters of America, LLC, Atlanta, GA - 01/2015 – 03/2017
- Floor & Décor, Atlanta, GA 03/2017 – 05/2019
- Cardinal Health, Dublin, Ohio - 05/2019 – 06/2020
- Marriott International Inc., Bethesda, Maryland 06/2020 – 02/2022
- Northwest Bank, Warren, PA - 02/2022 – Current

# Exp:
- Northwest Bank, Warren, Pennsylvania - 02/2022 – Current (Remote).
    - Redesign from UIKit to swiftUI
    -   -> Async Await; Combine; prop wrappers;
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

## Difference between: as, as? and as!:
- as:
    `let object: Subclass = Subclass()`  
    `let superclassObject = object as Superclass // Upcasting`
- as?:
    `let anyValue: Any = 42`  
    `let intValue = anyValue as? Int // Conditional type casting, returns an optional`
- as!:
    `let anyValue: Any = 42`  Difference between: as, as? and as
    `let intValue = anyValue as? Int // Conditional type casting, returns an optional`


## Dependency injections (3 types)
- 1. Method Injection: When sending dependencies as parameters in a function that only will be used there.
- 2. Constructor Injection: When sending dependencies as init parameters to ensure we will have them for any task inside the initialized object.
- 3. Property Injection: Dependencies are set through public properties of the class.

## Protocols:
Protocols are a set of methods, properties or requirements that a class, struct, or enum must adopt. They have no implementation of methods. The only case is for additional functionalities in an extension of the protocol.
Protocols can be composite like Codable that involves `Decodable & Encodable`.
Mostrly used in SwiftUI but also used in Swift, for NetworkManager to create fake and real managers for better testings. Dependency injections and indirectly used for test cases

## Protocol Oriented Programing
Is a coding approach that emphatizes the usage of (contracts) protocols facilitating code composition and reuse, including the usage of multiple protocols in one object.

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

## Protocols in Swift vs Objective-c
- `Syntax`: **Swift** = protool; **Objc** = @protocol.
- `Optional methods`: **Swift** = in extension; **Objc** = no extensions, declared as @optional.
- `Inheritance`: **Swift** = Can inherit from other protocols; **Objc** = Cannot inherit from other protocols.

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

`Escaping closures:`
Is a closure that is passed as an argument to a function but is allowed to outlive the function's execution.

## ANY
#### Any:
- Any is a type that represents values of any type, including instances of classes, structs, enums, and other types.
- It is a powerful and flexible way to work with values of unknown types or to create functions or data structures that can work with a variety of types.
- For example, you can use Any to store values of different types in a collection like an array or a dictionary.

#### AnyObject:
- AnyObject is a protocol that represents instances of classes (reference types).
- It can be used to work with class instances when you need to interact with objects of unknown classes.
- AnyObject is often used in Objective-C interoperability scenarios.

#### AnyClass:
- AnyClass is an older Swift construct that represents a class type, specifically a metatype (the type of a class itself).
- It is typically used in Objective-C interoperability to work with class types.
- In modern Swift, you can often use Type.Type instead of AnyClass.

#### AnyHashable:
    AnyHashable is a type-erased wrapper around a hashable value.
    It allows you to store values of different types in a collection (e.g., a dictionary) where the keys need to conform to the Hashable protocol.
    AnyHashable can be used when you want to store values of different types in a dictionary without knowing their specific types in advance.
        
## Swift vs Objective-C:
Was developed from C and C++

`Swift`:
- Is a modern and expressive language with strong typing `(variables can be explicitly declared)` and Type Inference where swift's compiler can infer the data type of a variable based on its initial value.
- Error handling and optionals to enhance code reliability.
- ARC (Automatic Reference Counting) meaning automatic memory management.
- Type safety, type inference, generics.
- Managers reference and Value types.
- `Characteristics:`
  - Type Safety -> `var name = 10, true` We cannot assign different types to the same variable.
  - Type Inference -> `var name = "ABC"`
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
   

`Objective-C`
- Is an established, dynamic language that integrates well with C.
- It offers powerful runtime features and is suitable for legacy projects.
- It can also be gradually adopted in Swift projects.
- Managers reference type, we need to manage the memory by ourselfs.
- `Characteristics:`
    - Everything is classes, theres no structs
    - protocols
    - category
    - Enum -> But used with Int only
        - Reference Type:
            - NSString
            - NSArray
            - NSDictionary
    - NSNameSpace

## Difference between ObjC and Swift in compiler execution?
In terms of performance, Objective-C can have some performance overhead compared to Swift.

- **Objective-C:** Uses a two-step compilation process.
    - First, the code is compiled into intermediate code (LLVM IR or Objective-C bytecode) by the Clang compiler.
        - (LLVM IR → Low-Level Virtual Machine Intermediate Representation)
    - Then, the runtime system (Objective-C runtime) handles dynamic method dispatch and other runtime features.
- **Swift:** Uses a single-step compilation process. The Swift compiler (also part of Clang/LLVM) directly produces machine code or bytecode, depending on the target platform.

## Use of dynamic keyword in swift?
We use `dynamic` keywords in swift for:
**Interoperability with Objective-C**:
functions and properties because swift is uses static dispatch instead of Objective-C that is dynamic runtime system.

**Key-Value Coding (KVC) and Key-Value Observing (KVO):**
- KVC allows you to access properties by string names
- KVO enables observing changes to properties.
  
```swift
import Foundation

// Define a class that we want to observe
class Person: NSObject {
    @objc dynamic var name: String
    @objc dynamic var age: Int
    
    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }
}

// Create an instance of the Person class
let person = Person(name: "John", age: 30)

// Add an observer to watch changes in the 'age' property
let ageObservation = person.observe(\.age, options: [.new, .old]) { person, change in
    if let newValue = change.newValue as? Int, let oldValue = change.oldValue as? Int {
        print("Age changed from \(oldValue) to \(newValue)")
    }
}

// Using Key-Value Coding to access and modify properties
person.setValue("Alice", forKey: "name")
person.setValue(35, forKey: "age")

// Remove the observer when it's no longer needed
ageObservation.invalidate()

```

## Content Compression and Content Hugging.
`Content hugging`: a priority that indicates how much a view wants to hug its content to prevent it from expanding.
`Content compression`: resistance - is a priority that indicates how much a view resists being compressed.

## What is Static dispatch or language(Swift)?
Means that the compiler determines at compile time which implementation of the method should be called based on the declared type of the object. This approach is efficient and safe, as it allows the compiler to catch many errors at compile time.

## What is Dynamic dispatch or language(Objective-C)?

In Objective-C, method calls are resolved at runtime and the method to be executed is determined based on the actual class of the object at runtime. This nature allows flexible runtime behaviors.



## Explain SwiftUI?
 - Declarative Language
 - Built using Swift
 - Is Apple cross platform
 - Manages basic animations by default
 - State management with Wrappers

## Struct vs Classes (class vs struct):
`Structs`: 
- value type, meaning they can be copied and passed arround the code.
- Modifications in a copy don't affect the original.
- They do not support iheritance and are suitable for simple data models.
- Thread safe one value can be acessed at time.
- Structs are faster because they are put as stock in memory
- Doesn't have inheritance

![image](https://github.com/apaladines-techconsulting/Interview_Questions/assets/138136886/97f2b4cb-71d6-4e8d-9454-beaafb3634ed)


`Classes`:
- Reference type meaning multiple variables can point to the same object in memory.
- Have inheritance.
- They are deallocable and often used for complex data models.
- Not Thread safe, multiple threads can accesess to the object at the same time.

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

## Multithreading or threading options in iOS (6 ways):
1. GCD -> 
2. OperationQueue
3. Await Async
4. Actor
5. Thread
6. Semaphore


DispatchWorkItem
DispatchGroup

### Grand Central Dispatch VS -> NSOperation
-  n njhuy76presice and easy to use, lots of threads vs NSOperation more control over the multithreading stop, continue, cancel.

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
6. `Unspecified` => This has the last priority.

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

Advantages:
- Reusability: Write code that works with different types.
- Type Safety: Avoid runtime errors by enforcing type constraints.
- Cleaner Code: Reduce code duplication and improve code readability.
- Performance: Generics can be more efficient than using protocols and casting.
    
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
- Managed Object Model: The blueprint that defines how your data looks, including its structure, attributes, and relationships. It's like designing the layout of your data.
- Managed Object Context: The workspace where you create, modify, and interact with your data objects. Think of it as a place to perform actions on your data.
- Persistent Store Coordinator: The bridge that connects your data objects in the context to where they're actually stored. It manages the translation between your app's objects and their storage format.
- Persistent Store: The place where your data is saved, like a file or database. It's where your app's data lives on disk, even when the app is closed.
  
By default CoreData run in main thread, a better practice is to run it in privateContext that means background.

![image](https://github.com/apaladines-techconsulting/Interview_Questions/assets/138136886/de399225-5933-4f5b-afd2-0cc90ac5c10b)

#### CoreData Concurrency:

![image](https://github.com/apaladines-techconsulting/Interview_Questions/assets/138136886/6e4c2f3a-4a80-4d40-b0fe-50053a40ee79)

#### Deletion Rules in CoreData
- No Action: We have a category that contains several notes. If the category is deleted, the notes are not notified of this event. The notes on the other end of the relationship believe that they are still associated with the deleted category.
- Nullify: If a category has several notes and the category is deleted, the relationships pointing from the notes to the category are nullified. This is the default delete rule.
- Cascade: If a note should always have a category, the deletion of a category should automatically delete the notes associated with that category.
- Deny: If a note is tied to a category, the category cannot be deleted until it is not tied no any note.

## Can I use 2 Managed Object Models?

Yes. Usually done when you want to maintain separate topics inside the same application like a Bank app with clients and enterprises features that works separately inside the same app.

```swift
// Create a persistent container for the first model
let container1 = NSPersistentContainer(name: "Model1")
container1.loadPersistentStores { description, error in
    if let error = error {
        fatalError("Failed to load store: \(error)")
    }
}

// Create a persistent container for the second model
let container2 = NSPersistentContainer(name: "Model2")
container2.loadPersistentStores { description, error in
    if let error = error {
        fatalError("Failed to load store: \(error)")
    }
}
```

## Can I use 2 Managed Object Contexts?

First of all, we cannot start a CoreData task and finish it in other thread context.

- **Main Queue and Background Queue Contexts**: In many applications, you have a main queue context (`viewContext`) and one or more background queue contexts. The main queue context is typically used for interacting with the user interface, while background
 contexts are used for performing tasks that might be time-consuming and
 should not block the main queue.
    - Example: `let backgroundContext = persistentContainer.newBackgroundContext()`
- **Child Contexts:** Child contexts are created as children of a parent context. They allow you to perform changes in a separate context and then merge those changes into the parent context. This is often used to isolate changes made in a temporary context before saving to the main context or persistent store.
    
    ```swift
    let childContext = NSManagedObjectContext(concurrencyType: .privateQueueConcurrencyType)
    childContext.parent = parentContext
    ```
    
- **Multiple Contexts for Isolation:** In some cases, you might use multiple contexts to isolate different parts of your application's data. For example, you could have one context dedicated to user authentication and another for managing application settings.
- **Concurrency Control**: Multiple contexts can help you manage concurrency. For example, if you have a long-running background task that updates data, it can use its own context and then merge the changes into the main context when the task is complete.
- **Temporary or Scratch Contexts**: You can create temporary contexts for specific tasks, such as importing data, performing batch updates, or calculating values without affecting your main data.

```swift
// Create the main queue context (viewContext)
let mainContext = persistentContainer.viewContext

// Create a background queue context
let backgroundContext = persistentContainer.newBackgroundContext()

// Perform operations on the main context (viewContext)
let entity = MyEntity(context: mainContext)
entity.name = "Example"

// Perform operations on the background context
backgroundContext.perform {
    let backgroundEntity = MyEntity(context: backgroundContext)
    backgroundEntity.name = "Background Example"

    do {
        try backgroundContext.save() // Save changes in the background context
    } catch {
        print("Error saving background context: \(error)")
    }

    // Merge changes into the main context
    mainContext.perform {
        do {
            try mainContext.save() // Save changes in the main context
        } catch {
            print("Error saving main context: \(error)")
        }
    }
}
```

## What is the background queue technique?

This technique is essential for improving the responsiveness and performance of your app, especially when dealing with time-consuming or potentially blocking operations. It's often used in conjunction with technologies like Grand Central Dispatch (GCD) or Operation Queues. Here's how it works.

```swift
// Dispatch a task to a background queue
DispatchQueue.global().async {
    // Perform time-consuming task
    let result = performSomeTask()

    // Update UI on the main queue
    DispatchQueue.main.async {
        updateUIWithResult(result)
    }
}
```

```swift
import Foundation

// Create an OperationQueue for background tasks
let backgroundQueue = OperationQueue()
backgroundQueue.name = "BackgroundQueue"

// Create a custom operation for the time-consuming task
class MyOperation: Operation {
    override func main() {
        if isCancelled {
            return
        }
        
        // Perform time-consuming task
        let result = performSomeTask()
        
        // Update UI on the main queue
        DispatchQueue.main.async {
            updateUIWithResult(result)
        }
    }
}

// Create an instance of the custom operation
let myOperation = MyOperation()

// Add the operation to the background queue
backgroundQueue.addOperation(myOperation)
```


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

## ViewController life cycle:
- Initialization (init(coder:) or init(nibName:bundle:)): When a view controller is first created, its initialization method is called. You can customize this process by overriding the appropriate init method based on your needs.

- loadView: The view controller's loadView method is called. If you're not using Interface Builder or Storyboards, you can create and assign the view for your view controller in this method.

- viewDidLoad: This method is called after the view has been loaded into memory and is typically used for additional setup, such as configuring UI components and setting initial values.

- viewWillAppear: Before the view appears on the screen, the viewWillAppear method is called. This is a good place to prepare your view for display and perform tasks that need to happen each time the view appears.

- viewDidAppear: After the view has appeared on the screen, the viewDidAppear method is called. It's a suitable place for starting animations or fetching data that should occur after the view is visible.

- viewWillDisappear: When the view is about to disappear from the screen (e.g., due to a navigation action or dismissal), the viewWillDisappear method is called. You can use this method to perform cleanup or save state before the view disappears.

- viewDidDisappear: After the view has disappeared from the screen, the viewDidDisappear method is called. You can use this method for stopping animations or releasing resources associated with the view.

- viewWillLayoutSubviews: Before the view's layout is updated, the viewWillLayoutSubviews method is called. This can be used to prepare for layout changes.

- viewDidLayoutSubviews: After the view's layout has been updated, the viewDidLayoutSubviews method is called. It's an appropriate place to make additional layout adjustments.

- Memory Warnings: If the system encounters a memory warning, the view controller may receive didReceiveMemoryWarning method calls. This is an opportunity to release non-essential resources to free up memory.

- Rotation and Size Changes: When the device's orientation or size changes, the view controller can respond by overriding methods such as viewWillTransition(to:size:).

- Deallocation (deinit): When the view controller is no longer needed and is removed from memory, its deinit method is called. This is where you can perform final cleanup, remove observers, and release any remaining resources.

## AppDelegate lifeCycle: 
- application(_:willFinishLaunchingWithOptions:): This method is called when the app is about to finish launching but before it's visible on the screen. It's an opportunity to perform some initialization tasks, set up global configurations, and prepare for app setup.

- application(_:didFinishLaunchingWithOptions:): After the app has launched and its initial setup is complete, this method is called. It's the last method called during app launch and is commonly used for post-launch tasks and additional configuration.

- applicationDidBecomeActive(_:): This method is called when the app becomes active, either at startup or when returning from the background. It's an appropriate place to start or resume tasks, like animations, audio playback, or network requests.

- applicationWillResignActive(_:): When the app is about to move from the active to the inactive state, this method is called. You can use it to pause ongoing tasks and save user data.

- applicationDidEnterBackground(_:): This method is called when the app enters the background state. It's a good place to perform any tasks that are necessary to save app data, stop timers, or release resources.

- applicationWillEnterForeground(_:): Just before the app transitions from the background to the active state, this method is called. It's a suitable place for tasks like resuming any paused operations or updating the user interface.

- applicationWillTerminate(_:): This method is called when the app is about to be terminated. You can use it to save any critical data or perform cleanup operations, but keep in mind that you have limited time to execute code in this method.

- applicationDidReceiveMemoryWarning(_:): When the system experiences memory pressure, it may call this method on the AppDelegate. It's an opportunity to release memory and resources to prevent the app from being terminated.

- application(_:open:options:): This method is called when the app is launched from another app or when it's asked to open a file. You can handle custom URL schemes and file open requests here.

- application(_:handleEventsForBackgroundURLSession:completionHandler:): If your app performs background downloads using URLSession, this method is called to handle the completion of background downloads.

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

 We can also chain multiple **`operators`** on a Publisher.
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
  5. @Environment
  6. @EnvironmentObject
  7. @FocusState
  8. @Published
  9. @FetchRequest
  10. @AppStorage
  11. @ViewBuilder
  12. @FetchedObject
  13. @MainActor
  14. @Namespace

 Difference between
     @StateObject -> Only recreates a part of the view
     @ObservedObject -> recreates everything
     
#### Common higher methods (OPERATORS) to use in Combine:
- `.tryMap` -> To map data.
- `.decode` -> Parsinng.
- `.receive` -> Receiving actual output.
- `.sink` -> getting completion (data, error) (CORRECT THIS PART).
- `.store` -> to clear out memory references, to deinitialize a reference or to cancel any task.
- `.map` -> transforms the emitted values from one type to another using a transformation closure.
- `.merge` -> To mix multiple streams.
- `.debounce` -> to delay responses.
- `.throttle` -> limits the rate of values emitted by a publisher.
- `.zip` -> Used to combine different responses in one.
- `.removeDuplicates` -> Removes any duplicated elements in publisher.
- `.reduce` -> Returns the result of combining the elements of the sequence using the given closure.

## ArchitecturePatterns -> One Single for whole project:
1. MVC -> Model ViewController
2. MVVM -> Model View ViewModel
3. MVVM-C -> Model View ViewModel Coordinator (Coordinator Pattern)
4. MVP -> Model View Presenter (this is an old arq not much used now)
5. TCA -> Clean Architecture
6. VIPER -> View Interactor Presenter Entity Router
 
### MVVM:
MVVM is a design pattern used in iOS development to separate the concerns of your application into three distinct components:
- Model: Represents the data and business logic.
- View: Represents the user interface.
- ViewModel: Acts as an intermediary between the Model and the View. It transforms the data from the Model into a format that the View can display and also handles user interactions.

#### Advantages of MVVM:
- Separation of Concerns: MVVM cleanly separates the concerns of an application. The Model handles the data and business logic, the ViewModel handles the presentation logic, and the View is responsible for displaying the data. This separation makes the codebase more organized and maintainable.
- Testability: MVVM makes it easier to write unit tests for your application. The ViewModel can be tested independently of the View, as it doesn't have any direct references to UI elements. This improves test coverage and helps catch bugs early in the development process.
- Reusability: ViewModels can be reused across multiple views or view controllers. This is especially useful in scenarios where different parts of the app need to display the same data differently.
- Flexibility and Adaptability: MVVM allows for easy adaptation to changes in the UI or business logic. As UI requirements change, you can update the ViewModel without affecting the Model or the View. This flexibility is essential for handling evolving app requirements.
- Binding: MVVM often leverages data binding frameworks like Combine or RxSwift, which allow automatic synchronization of the ViewModel and View. This reduces boilerplate code for updating UI elements in response to changes in the underlying data.
- Improved Collaboration: MVVM promotes collaboration between designers and developers. Designers can work on the layout and appearance of the View independently of the ViewModel and Model, allowing for parallel development.

#### Disadvantages of MVVM:
- Complexity: MVVM can introduce some complexity to the codebase, especially in larger applications. It requires creating and managing ViewModel objects for each View, which may increase code size and complexity.
- Learning Curve: Developers new to MVVM may face a learning curve when understanding how to structure and maintain ViewModel code.
- Overhead: In simpler apps or when used incorrectly, MVVM can introduce unnecessary overhead. Not every app requires the level of separation that MVVM provides, and using it inappropriately can lead to code bloat.
- Potential for Boilerplate: Depending on the platform and libraries used, there can be some boilerplate code involved in setting up data binding or communication between the ViewModel and View.
- Performance Considerations: MVVM relies on data binding, which can have performance implications if not used carefully. Excessive updates to the View can impact performance, so it's important to monitor and optimize as needed.
    
### Design Patterns:
Group of smaller related classes, modules or sub functionalities inside one project. In one project can be multiple Design Patterns used:

 1. `Creational Design Patterns` -> Anything related to Object creation of class, comes under this category (one to one comunication, one to many, etc).
 2. `Behavieour Design Patterns` -> How your projects are going to comunicate or pass data around or bahave.
 3. `Structural Design Patterns` -> How you assemble objects and classes into a larger group.

 - Creational Design:
     1. Singleton
     2. Factory Design Pattern / Factory Method
     3. Builder
     4. Prototype

 - Behavioural Design Pattern
     1. Observer Pattern
     2. Chain of responsibility
     3. Memento
     4. Iterator

 - Structural Design Pattern
    1. Adaptor pattern (Protocol delegate)
    2. Decorator
    3. Facade Design Pattern

### Singleton Pattern:
 It ensures that only one object of class will be there thoroutghout our app
 It provides global access to that instance.
- Examples:
    - DataManager
    - AuthenticationManager
    - FileDownloaderManager
    - AnalyticsManager

- Advantages:
    - Make it easy.
    - Gives global access.
      
- Disadvantages:
    - Creates hidden dependencies.
    - Creates Global states because of that it difficult to write unit tests.
    - Will be alive throughout your app life cycle so it might create memory issues in app.

- AntiDesign Pattern
    - Cannot have injeritance.
    - Needs to be used carefully.
    - Cannot write test cases.

### Closure pattern:
- Is just the same closures we use as parameters or variables.
- It is used to send data back to the class that is implementing the closure. they can be scapping and nonScapping.

#### RXSwift and RXCocoaTouch:
- Major components:
    1. Schedulers
    2. Observables
    3. Operators

## Repository Pattern: 
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

## Memory Management ARC - Automatic Reference Counting:
_**How iOS Does Memory Management?**_
 
 Objective and swift it works automatically.

 Initially the **Automatic Reference Counting** will be zero.
```swift
 var gretings = "Hello World"
 Reference count = Reference count +1
 Reference count = 1

 gretings = nil
 //Reference count = Reference count -1
 //Reference count = 0
 //Thats when OS free that block of memory
```
 It keeps the track of references to objects and releases them when they are no longer needed.

### ARC (Automatic Reference Counting):
Is a memory management mechanism used in Swift to automatically manage memory by keeping track of references to objects. 
When there are no more strong references to an object, it gets deallocated.

**Strong, Weak, Unowned References:**
- _**Strong:**_ Keeps a strong reference to an object, preventing it from being deallocated. ARC +1
- _**Weak:**_ Maintains a weak reference to an object, allowing it to be deallocated when no strong references exist. ARC +0
- _**Unowned:**_ Similar to weak but assumes the reference won't be nil, and it doesn't keep the reference count. ARC +0
    
### Type of reference variables:
- strong -> This is the default attribute. It keeps those objects alive in memory.
- weak -> When we don't want to have ownership of that object. To avoid cycle issues as well.
- unowned -> Similar to weak but complusionb is that it should always have data. otherwise it can cause crashes in app.

### Retain Cycle:
A retain cycle occurs when two or more objects reference each other strongly, preventing them from being deallocated by the memory management system. In Swift, this often happens when using closures or delegate patterns.
How to Resolve Retain Cycles and Memory Leaks:
To resolve retain cycles and memory leaks:
- Use weak or unowned references in closures to prevent strong reference cycles.
- Use Instruments in Xcode to identify memory leaks.
- Be mindful of strong references within closures, especially when capturing self.

## Declarative and imperative codibg:
- `Imperative`: Swift -> Is an approach where you describe the sequence of actions and changes that need to occur to create and update the user interface.
- `Declarative`: SwiftUI -> Is an approach where you describe what you want the user interface to look like based on its current state, without specifying the step-by-step instructions for achieving that state.
- 
## Computed property and Lazy Property:
- `Lazy property`: Is a property that is not calculated or initialized until the first time it is accessed. It's value is cached for the next uses meaning that it wont be computed again.
- `Computed property`: Is a property that does not store a value directly but provides a getter and an optional setter through which you can compute or derive its value on-the-fly.

# iOS Security:
    1. Data Storage Security
    2. Network layer Security
    3. Jailbroken Detection
    4. Development techniques or best practices

## 1. Data Storage Security:
    a. UserDefaults -> Don't store sensitive data here
    b. Keychain -> To store small sensitive data
    c. CoreData -> We can use `SQLCipher` or sqlite file we can set a value for key `NSPersistenStoreFilePRotectionKey` to store data in a secure way.
        - completeUntilFirstUserAuthentication
        - completeUnlessOpen
        - complete
        - none
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
    - Create server trust
    - Certificate
    - SSL Prolicy for domain name check
    - evaluate server Certificate
    - local Certificate
    - Comparing data of local an remote server certificates

 2. The public key pinning:
    - a. priate key
    - b. multiple public key

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


## TTD & BDD - Tests
- TDD = write test first then functionality
- BDD = write functionality and then test cases

TDD Test Driven Development:
XCTest
    Stubbing, bocking, Faking.
    For api calls we use `XCTestExpectation` and `wait(for: [expectation], timeout: waitDuration)`
    Defining what will be test, expectation, fulfill assertions and wait if necessary.

BDD: Behavioural Driven Development:
    Quick and Nimble -> Start with given (setting up) when () and then ()
    More for Testers than developers. It's a higher level Testing.

## SwiftUI vs Swift
- Everything made with structs Tsack memory (faster) instead of classes Heat memory
- More updated
- We use code instead of UIKit (storyboards)
- Protocol oriented programming instead of Swift that is oop
- We dont have constraints nor autolayout in swiftUI

## Limitations of swiftUI
- Platform Availability:
        SwiftUI is primarily designed for Apple platforms, including iOS, macOS, watchOS, and tvOS. It does not provide cross-platform support for non-Apple platforms like Android or web.

- iOS Version Support:
        SwiftUI is only available on iOS 13.0 and later, macOS 10.15 and later, watchOS 6.0 and later, and tvOS 13.0 and later. This means that apps targeting older iOS versions cannot fully utilize SwiftUI.

- Learning Curve:
        While SwiftUI simplifies many aspects of UI development, it also introduces a learning curve, especially for developers who are familiar with UIKit or AppKit. SwiftUI's declarative syntax and architecture may take some time to grasp.

- Limited Third-Party Library Support:
        SwiftUI does not have the extensive ecosystem of third-party libraries and components that UIKit has. Developers may need to build custom UI components or work with UIKit in conjunction with SwiftUI for certain scenarios.

- Missing Features:
        As of my last knowledge update, SwiftUI lacked some features and components that were available in UIKit. For example, complex collection view layouts, custom camera views, or highly customized gesture recognizers might require UIKit integration.

- Incomplete macOS Support:
        While SwiftUI is available for macOS, it does not cover all macOS-specific UI elements and features. Developers may need to fall back to AppKit for some desktop-specific UI needs.

- Backward Compatibility:
        SwiftUI does not provide backward compatibility with older iOS versions, which means developers may need to maintain separate code paths for SwiftUI and UIKit/AppKit when targeting a wide range of iOS/macOS versions.

- Performance:
        While SwiftUI is designed to be performant, it may not always offer the same level of fine-grained control over performance optimization as UIKit, especially in scenarios where performance is critical.

- Debugging and Tooling:
        Debugging SwiftUI-based applications, especially complex ones, may be more challenging compared to traditional UIKit apps. At the time of my last update, the tooling and debugging support for SwiftUI were evolving.

- Limited Cross-Platform Support:
        Although SwiftUI supports multiple Apple platforms, achieving full cross-platform development (e.g., iOS and macOS) with shared code and UI can still be challenging due to platform-specific differences.


# Solving problems interview :

## I have a login page, 7 concurrent api calls, first 4 are independent(parallel), 5 output is the input of 6, 6 output is the input of 7

- **OperationQueue:**

```swift
let operationQueue = OperationQueue()
operationQueue.maxConcurrentOperationCount = 4

let operation1 = BlockOperation { }
let operation2 = BlockOperation { }
let operation3 = BlockOperation { }
let operation4 = BlockOperation { }

let operation5 = BlockOperation { }
let operation6 = BlockOperation { }
let operation7 = BlockOperation { }

operation5.addDependency(operation4)
operation6.addDependency(operation5)
operation7.addDependency(operation6)

operationQueue.addOperations([operation1, operation2, operation3, operation4, operation5, operation6, operation7], waitUntilFinished: false)
```

- **DispatchWorkItem:**

```swift
import Foundation

// Create a DispatchQueue for the tasks
let queue = DispatchQueue(label: "com.example.taskQueue", attributes: .concurrent)

// Create a DispatchGroup to coordinate the tasks
let group = DispatchGroup()

// Create DispatchWorkItems for tasks A, B, C, and D
let workItemA = DispatchWorkItem { }
let workItemB = DispatchWorkItem { }
let workItemC = DispatchWorkItem { }
let workItemD = DispatchWorkItem { }

// Add tasks A, B, C, and D to the queue and group
queue.async(group: group, execute: workItemA)
queue.async(group: group, execute: workItemB)
queue.async(group: group, execute: workItemC)
queue.async(group: group, execute: workItemD)

// Wait for tasks A, B, C, and D to complete
group.wait()

// Create DispatchWorkItems for tasks E, F, and G
let workItemE = DispatchWorkItem { }
let workItemF = DispatchWorkItem { }
let workItemG = DispatchWorkItem { }

// Set dependencies using notify
workItemE.notify(queue: queue) {
    // Execute task F after task E
    queue.async(execute: workItemF)
}

workItemF.notify(queue: queue) {
    // Execute task G after task F
    queue.async(execute: workItemG)
}

// Add task E to the queue
queue.async(execute: workItemE)

// Wait for task G to complete (or you can use a group if needed)
workItemG.wait()

// Perform any final cleanup or actions
print("All tasks are complete")
```


