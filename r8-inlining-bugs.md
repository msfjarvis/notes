---
date: 2020-10-24T23:46
---

# Potential bugs with R8's full mode

It appears that some code in the latest revision of Google's R8 optimizer is causing it to try and inline things it shouldn't, and thus fail.

Exhibit 1 from [compose-lobsters](https://msfjarvis.dev/g/compose-lobsters)

```
R8: com.android.tools.r8.errors.e: FORCE inlining on non-inlinable: void dev.msfjarvis.lobsters.data.source.PostsDatabase.constructor$androidx$room$RoomDatabase()
```

Speciment 2 from [wireguard-android](https://git.zx2c4.com/wireguard-android)

```
R8: FORCE inlining on non-inlinable: void androidx.fragment.app.FragmentManagerImpl.constructor$androidx$fragment$app$FragmentManager()
```

~~This can be fixed by turning off R8's full mode by setting `android.enableR8.fullMode=false` in `gradle.properties`.~~

This has been fixed in AGP `4.2.0-alpha15`, and the corresponding fixed R8 versions are `2.0.102`, `2.1.75` and `2.2.31`. If you can't use the alpha AGP, forcing R8 to a specific version is easy and can be done like this:

```groovy
buildscript {
    repositories {
        maven {
            url 'https://storage.googleapis.com/r8-releases/raw'
        }
    }
    dependencies {
        classpath 'com.android.tools:r8:2.1.75'          // Must be before the Gradle Plugin for Android.
        classpath 'com.android.tools.build:gradle:X.Y.Z' // Your current AGP version.
     }
}
```

Details on the fix can be found at Google's issue tracker [here](https://issuetracker.google.com/issues/170677722).