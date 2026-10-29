# enso-x Maven repository

Static Maven repository served by GitHub Pages at <https://enso-x.github.io/maven/>.

```groovy
repositories {
    maven {
        url = 'https://enso-x.github.io/maven/'
        content { includeGroup 'io.ensox.exlua' }
    }
}

dependencies {
    implementation 'io.ensox.exlua:exluaj-jse:3.0.1-exlua.1'
}
```

| Artifact | Source |
|---|---|
| `io.ensox.exlua:exluaj-jse` | [enso-x/exluaj](https://github.com/enso-x/exluaj), branch `exlua` |

Artifacts are published from each library's own build (`gradlew publishPages`);
released versions are never overwritten.
