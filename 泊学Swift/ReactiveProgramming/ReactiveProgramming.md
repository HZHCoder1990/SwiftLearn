#### 理解Reactive编程思想

函数式编程思想

```swift
// 函数式编程
let stringArray = ["1", "2", "3", "4", "5", "6", "7", "8", "9"]
let evenArray = stringArray.map { Int($0)! }.filter { $0 % 2 == 0 }
print(evenArray)
```

#### Hello world in RxSwift

```swift
// map这种高级operation,如果只有一行代码,可以省略 return
 rxTextInput.rx.text.orEmpty.map { input in
    let char =  input.suffix(1)
    if let res = Int(char) {
        return res
     }
        return -1
 }.filter{
    $0 % 2 == 0
 }.subscribe(onNext: {
    print($0)
 }).disposed(by: bag)
```

**Closure的一些用法**

```swift
typealias OnNext = (Int) -> Void
    
private func closure(_ name: String, on: (Int) -> Void) {
    on(30)
}
    
private func closure2(_ on: @escaping (OnNext) -> Void) {
        
     /*
     let onNext = { (age: Int) -> Void in
         print(age)
     }*/
        
     let onNext = { (age: Int) in  // 省略了 -> Void
         print(age)
     }
    // 这里不能是 onNext(xx) 因为需要传递一个closure，而不是closure的结果!
    on(onNext)
}
    
private func closure3(_ on: OnNext) {
    on(36)
}

// 使用
closure("黄先生") { age in
    print(age)
}
        
closure2 { (age: (Int) -> Void) in
    age(35)
}
        
closure3 { (age: Int) -> Void in
    print(age)
}
```

#### 理解Observables and Observer

```swift
// Observable
let emptySequence = Observable<Int>.empty()
_ = emptySequence.subscribe {
  (event: RxSwift.Event<Int>) -> Void in // -> Void 可以省略
  print(event)
}


```





