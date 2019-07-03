
# What 
An asynchrounous value whose computation will be completed sometime in the future.  It is a mechanism to encapsulate concurrent operations used by a framework (Finagle)<sup>[[2]](#concurrent-programming-with-futures)</sup>.  It is a utility from the Twitter Util library<sup>[[4]](#source-code)</sup>.            

# Why


# Creation

# States
A future can be in one of three states<sup>[[1]](#twitter-futures-scaladoc)</sup>:
* Pending
* Succeeded
* Failed 

# Obtaining The Value / Creation
There are different ways to obtain the value of a Future depending on whether you want to block or not.  

## Future.value
Blocks

## Future()
Uses the Future.apply function
Blocks

## Future.exception
Blocks current thread

## Await.result
If you want to block the current thread, there is a helper function in Twitter Util that accepts a Future as an argument:
```scala
import com.twitter.conversions.DurationOps._
import com.twitter.util.{Future}

val futureInt: Future[Int] = Future.value(1)
val futureOperation: Future[Int] = futureInt.map {value => value + 1}
Await.result(futureOperation, 1.second)
```

It's better to avoid blocking to receive the value of a Future like in the example above.

If you must block, use [FuturePool][#Future Pools]

Blocking can prevent the overarching framework from doing the work they need to do



## onSuccess
```scala
import com.twitter.conversions.DurationOps._
import com.twitter.util.{Future}

val futureInt: Future[Int] = Future.value(1)
val futureOperation: Future[Int] = futureInt.map {value => value + 1}
futureOperation.onSuccess {
	value => println(value)
}
```

## onFailure

## Composition of Values
### map
### flatMap
### for comprehensions

### join
Accepts a seq of futures or 2...22 futures returning a tuple

### collect
Accepts a seq of futures

### select 
selects the first completed future from a seq of futures

### Sequentially
Future.traverseSequentially
Future.batched



### handle
### rescue


## ensure
runs regardless of success or failure


# Future Pools

# Timeout
within

# Promise



# Interrupts
https://github.com/twitter/util#future-interrupts


# Resources
[<a name="twitter-futures-scaladoc">1</a>] [Twitter Futures Scala Documentation][twitter-futures-scaladoc]

[<a name="concurrent-programming-with-futures">2</a>] [Concurrent Programming with Futures][concurrent-programming-with-futures]

[<a name="futures-and-concurrency">3</a>] [“Chapter 32: Futures and Concurrency.”][futures-and-concurrency] Programming in Scala, by Martin Odersky et al., 3rd ed., Artima, 2017.

[<a name="source-code">4</a>] [Twitter-Util][source-code]

[<a name="source-code-examples">5</a>] [Twitter-Util Futures Examples][source-code-examples]

[<a name="twitter-futures-finagle">2</a>] [Twitter Futures][twitter-futures-finagle]

[twitter-futures-scaladoc]: https://twitter.github.io/util/docs/com/twitter/util/Future.html "Twitter Futures Scala Documentation"
[concurrent-programming-with-futures]: https://twitter.github.io/finagle/guide/Futures.html "Concurrent Programming with Futures"
[futures-and-concurrency]: https://learning.oreilly.com/library/view/programming-in-scala/9780981531687/futures-and-concurrency.html "Chapter 32: Futures and Concurrency"
[source-code]: https://github.com/twitter/util "Twitter Util"
[source-code-examples]: https://github.com/twitter/util#futures
[twitter-futures-finagle]: https://twitter.github.io/finagle/guide/developers/Futures.html