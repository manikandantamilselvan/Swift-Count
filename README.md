# Swift count(where:)

As of **Swift 6.0**, the `count(where:)` method remains an efficient way to count elements in a collection that satisfy a condition. The syntax and functionality are consistent with **Swift 5.7 **and later versions.

Here's a quick overview of its use in **Swift 6.0:**

## Example Scenarios in Swift 6.0

#### 1.Counting numbers greater than 10:

``` 
let numbers = [5, 12, 18, 7, 9]
let countGreaterThanTen = numbers.count(where: { $0 > 10 })
print(countGreaterThanTen) // Output: 2
 ```
#### 2.Checking the presence of specific patterns in a collection:

```
let phrases = ["Swift is great", "I love coding", "Swift 6.0"]
let swiftMentions = phrases.count(where: { $0.contains("Swift") })
print(swiftMentions) // Output: 2
```

#### 3.Using with custom types:

```
struct Task {
    let title: String
    let isComplete: Bool
}

let tasks = [
    Task(title: "Buy groceries", isComplete: false),
    Task(title: "Finish project", isComplete: true),
    Task(title: "Call mom", isComplete: true)
]

let completedTasks = tasks.count(where: { $0.isComplete })
print(completedTasks) // Output: 2

```

## Advantages in Swift 6.0

**1.Conciseness**: Avoids the need for `filter` followed by `count`, reducing verbosity.

```
let count = collection.filter { condition }.count // Old way
let count = collection.count(where: { condition }) // New way
```
**2.Performance:** Directly counts matching elements without creating an intermediate array, making it more memory-efficient.

## Alternative for Older Swift Versions

If for some reason you're working with a version earlier than **Swift 5.7**, you can replicate `count(where:)` with a simple extension:

```
extension Collection {
    func count(where predicate: (Element) -> Bool) -> Int {
        return self.reduce(0) { $0 + (predicate($1) ? 1 : 0) }
    }
}
```

With this extension, you can use `count(where:)` in the same way as in later Swift versions.
**Swift 6.0** retains backward compatibility with this approach while enhancing language features for clarity and efficiency.

