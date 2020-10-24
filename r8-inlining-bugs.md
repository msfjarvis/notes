---
date: 2020-10-24T23:46
---

It appears that some code in the latest revision of Google's R8 optimizer is causing it to try and inline things it shouldn't, and thus fail.

Exhibit 1 from [compose-lobsters](https://msfjarvis.dev/g/compose-lobsters)

```
R8: com.android.tools.r8.errors.e: FORCE inlining on non-inlinable: void dev.msfjarvis.lobsters.data.source.PostsDatabase.constructor$androidx$room$RoomDatabase()
```

Speciment 2 from wireguard-android

```
R8: FORCE inlining on non-inlinable: void androidx.fragment.app.FragmentManagerImpl.constructor$androidx$fragment$app$FragmentManager()
```

This can be fixed by turning off R8's full mode by setting `android.enableR8.fullMode=false` in `gradle.properties`.
