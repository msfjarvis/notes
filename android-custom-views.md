---
date: 2020-11-20T12:00
---

# Custom views in Android

This is going to be a collection of things I'm learning while building a new UI for the chatbot SDK at Navana Tech entirely in code.

## LayoutParams

Don't try to _update_ `LayoutParams`, _set_ them. So, rather than doing this:

```kotlin
  updateLayoutParams<ViewGroup.LayoutParams> {
    width = ViewGroup.LayoutParams.MATCH_PARENT
    height = ViewGroup.LayoutParams.WRAP_CONTENT
  }
```

do this:


```kotlin
  layoutParams = ViewGroup.LayoutParams(
    ViewGroup.LayoutParams.MATCH_PARENT,
    ViewGroup.LayoutParams.WRAP_CONTENT,
  )
```
