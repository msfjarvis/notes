---
date: 2020-10-27T11:47
---

# Android SearchView and custom Toolbar

I was struggling to find why [pairing SearchView with MaterialToolbar](https://twitter.com/MSF_Jarvis/status/1320862481741303809) was so complicated and it turns out that I wasn't too stupid, it *is* really hard. Solution is to either [write a custom widget](https://twitter.com/saketme/status/1320866731729035266) or [wrap a good old `EditText` in a `FrameLayout`](https://twitter.com/its_sasikanth/status/1320875341758353408). I will probably go with the latter and update this note once I'm done.
