# Interview_Questions
Collection of possible questions for Senior iOS Devevelpers

## Protocols:
Protocols are a blueprint to implement methods, properties or requirements that a class, struct, or enum must adopt. They have no implementation of methods. The only case is for additional functionalities in an extension of the protocol.
Protocols can be composite like Codable that involves `Decodable & Encodable`.

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
`Swift` is a modern and expressive language with strong typing `(variables can be explicitly declared)` and Type Inference where swift's compiler can infer the data type of a variable based on its initial value. Error handling and optionals to enhance code reliability. ARC (Automatic Reference Counting) meaning automatic memory management.
`Objective-C` is an established, dynamic language that integrates well with C. It offers powerful runtime features and is suitable for legacy projects. It can also be gradually adopted in Swift projects. 

## Struct vs Classes:
`Structs` are value type, meaning they can be copied and passed arround the code. Modifications in a copy don't affect the original. They do not support iheritance and are suitable for simple data models.
Trait safe one value can be acessed at time.
Structs are faster because they are put as stock in memory


`Classes` are reference type meaning multiple variables can point to the same object in memory, have inheritance, they are deallocable and often used for complex data models. 
Not trait, multiple values can be accessed at time.


## Multithreading options in iOS:
1. GCD -> Grand Central Dispatch
2. OperationQueue
3. Await Async
4. Actor
5. Thread
6. Semaphore
 
DispatchWorkItem
DispatchGroup


#### GCD:

It allows you to perform tasks concurrently by dividing them into smaller blocks and submitting them to queues that can be concurrent or serial.(main queue as maint thread).
- `main` -> Serial queue.
- `global` -> Concurrent queue.
- `custom` -> Serial or Concurrent depending on the requirement.

`GCD - QoS (1 for the most prioritary and 4 for less priority):`
1. `User Interactive` => For animations or any kind of user related job with direct UI interactions.
2. `User Initiated` => When user requires imediate results, scrolling tableview for pagination or pull to reload
* `Default` => Falls between UserInitiated and Utility.
3. `Utility` => tasks which are long running, like downloading files.
4. `Background` => Something which is not visible to user like creating backups, restoring from server/ syncing like retrieving data from google cloud, etc.
* `Unspecified` => This has the last priority.

Concurrent and Serial.

sync and async
sync -> Blocks everything after it is finalized. One thing at time
async -> Allows to continue with the application and run things in 
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

#### Generics:
Generics represent any tyoe of data you define to mqke reusable and modular the functionality of the code.
You can ad restrictions like T: Decodable to specify a particular behaviour to the function.


#### App Life cycle States:
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

#### Closure pattern:
Is just the same closures we use as parameters or variables.
It is used to send data back to the class that is implementing the closure. they can be scapping and nonScapping.


#### Declarative and imperative codibg


####  Combine:
 
 It is a native framework made by Apple for Reactive development programming introduced in iOS 13.0
 Before Combine, there were two frameworks, RXSwift and RXCocoaTouch.

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
    
#### Common higher methods to use in Combine:
- `.tryMap` -> To map data.
- `.decode` -> Parsinng.
- `.receive` -> Receiving actual output.
- `.sink` -> getting completion (data, error) (CORRECT THIS PART).
- `.store` -> to clear out memory references, to deinitialize a reference or to cancel any task.
- `.map` ->
- `.merge` -> To mix multiple streams
- `.debounce` -> to delay responses
- `.throttle` -> ??

#### RXSwift and RXCocoaTouch:
- Major components:
    1. Schedulers
    2. Observables
    3. Operators

