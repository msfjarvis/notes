---
date: 2020-11-13T18:22
---

# Java's Comparator is stupid

I have a hard time remembering what value means what and their Javadoc does not even try to make this quick to understand:

```
* Compares its two arguments for order.  Returns a negative integer,
* zero, or a positive integer as the first argument is less than, equal
* to, or greater than the second.<p>
```

So I'm writing the same thing here, but tabulated, so I can quickly access and understand it.

Condition | Value
----------|-------
First item is greater than second | Positive integer
Second item is greater than first | Negative integer
Both items are equal | 0
