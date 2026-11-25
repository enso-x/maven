# enso-x Maven repository

Static Maven repository served by GitHub Pages at <https://enso-x.github.io/maven/>.

```groovy
repositories {
    maven {
        url = 'https://enso-x.github.io/maven/'
        content {
            includeGroup 'io.ensox.exlua'
            includeGroup 'com.ensox.ui'
        }
    }
}

dependencies {
    implementation 'io.ensox.exlua:exluaj-jse:3.0.1-exlua.1'
    // Ensox UI (Minecraft mod library): -common, -fabric, -neoforge
    implementation 'com.ensox.ui:ensox-ui-fabric:1.0.0+26.3'
}
```

| Artifact | Source |
|---|---|
| `io.ensox.exlua:exluaj-jse` | [enso-x/exluaj](https://github.com/enso-x/exluaj), branch `exlua` |
| `com.ensox.ui:ensox-ui-common`, `-fabric`, `-neoforge` | Ensox UI, one branch per Minecraft line (`release/26.3`); MIT |

Artifacts are published from each library's own build (`gradlew publishPages`;
Ensox UI: `gradlew publishLibrary -PmavenDir=<this checkout>`);
released versions are never overwritten.
