---
: Kotlin
date: 2020-11-08T04:24
---

# Understanding Kotlin's experimental APIs support

Kotlin allows developers to mark APIs as experimental, requiring opting into being able to use them. The semantics around this were changed in Kotlin 1.3.70 to rename the compiler option and annotations for the purpose, but we'll be sticking with how things are in Kotlin 1.4.10.

To begin marking APIs as experimental, you'll first need to create an annotation. Here's how you create a fictional experimental API marker called `ExperimentalResultApi`

```kotlin
@RequiresOptIn(message = "This API is experimental. It may be changed in the future without notice.")
@Retention(AnnotationRetention.BINARY)
@Target(AnnotationTarget.CLASS, AnnotationTarget.FUNCTION)
annotation class ExperimentalResultApi
```

To mark a specific API as experimental, simply annotate it with this annotation. As you can check in the value of `@Target` above, this annotation can be applied to either classes or functions. Let's try that.

```kotlin
@ExperimentalResultApi
public class FancyResult(value: String) {
  fun doSomething() { 
    /** method body is irrelevant for this **/
  }
}

public object ResultUtils {
  @OptIn(ExperimentalResultApi::class)
  fun convertToFancyResult(value: String): FancyResult {
    return FancyResult(value)
  }
}
```

Now that we have our experimental APIs, let's try to use them.


```kotlin
fun main() {
  val r1 = ResultUtils.convertToFancyResult("random string")
  val r2 = FancyResult("random string")
  println("$r1 $r2")
}
```

Both `r1` and `r2` are generated using experimental APIs, but only the declaration of `r2` will cause the compiler to emit a warning/an error.

![The call to FancyResult results in a compiler error](/static/experimental-api-no-opt-in.webp)

The secret sauce to it is how we annotated the `ResultUtils.convertToFancyResult` method. Using the `OptIn` annotation as opposed to directly adding the `ExperimentalResultApi` annotation causes the compiler to **not propagate** the experimental nature of the API to callers.

To summarize:

Given a set of APIs marked experimental using `@ExperimentalResultApi`,

- Mark your wrapping methods with `@ExperimentalResultApi` if you want users of your code to manually opt into using experimental APIs
- Mark your wrapping methods with `@OptIn(ExperimentalResultApi::class)` if you assume the risk of these APIs' experimental nature and don't need your users to know that your code is built on said experimental APIs.
