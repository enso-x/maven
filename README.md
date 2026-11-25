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
    // EnsoX UI (Minecraft mod library): -common, -fabric, -neoforge
    implementation 'com.ensox.ui:ensox-ui-fabric:1.0.1+26.3'
}
```

| Artifact | Source |
|---|---|
| `io.ensox.exlua:exluaj-jse` | [enso-x/exluaj](https://github.com/enso-x/exluaj), branch `exlua` |
| `com.ensox.ui:ensox-ui-common`, `-fabric`, `-neoforge` | [enso-x/ensox-ui](https://github.com/enso-x/ensox-ui), one branch per Minecraft line (`release/26.3`); MIT |

Artifacts are published from each library's own build (`gradlew publishPages`;
EnsoX UI: `gradlew publishLibrary -PmavenDir=<this checkout>`);
released versions are never overwritten.

Text files (`.pom`, `maven-metadata.xml`, `.module`) are stored with LF line endings and
their checksums are computed over the LF bytes. `.gitattributes` keeps git from converting
anything, so the served bytes are exactly the committed ones. EnsoX UI normalizes its files
in `publishLibrary`; other builds (ExLuaJ `publishPages`) must do the same before committing.
