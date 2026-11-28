# enso-x Maven repository

Static Maven repository served by GitHub Pages at <https://enso-x.github.io/maven/>.

```groovy
repositories {
    maven {
        url = 'https://enso-x.github.io/maven/'
        content {
            includeGroup 'io.ensox.exlua'
            includeGroup 'com.ensox.ui'
            includeGroup 'com.ensox'
        }
    }
}

dependencies {
    implementation 'io.ensox.exlua:exluaj-jse:3.0.1-exlua.1'
    // EnsoX UI (Minecraft mod library): -common, -fabric, -neoforge
    implementation 'com.ensox.ui:ensox-ui-fabric:1.1.0+26.3'
    implementation 'com.ensox:dynamic-config:1.1.0'
    // LootBeamsUp addon API (JDK types only; compileOnly, LootBeamsUp ships the classes)
    compileOnly 'com.ensox:lootbeamsup-api:3.0.0'
}
```

| Artifact | Source |
|---|---|
| `io.ensox.exlua:exluaj-jse` | [enso-x/exluaj](https://github.com/enso-x/exluaj), branch `exlua` |
| `com.ensox.ui:ensox-ui-common`, `-fabric`, `-neoforge` | [enso-x/ensox-ui](https://github.com/enso-x/ensox-ui), one branch per Minecraft line (`release/26.3`); MIT |
| `com.ensox:dynamic-config` | [enso-x/ensox-dynamic-config](https://github.com/enso-x/ensox-dynamic-config), plain Java 21; MIT |
| `com.ensox:lootbeamsup-api` | LootBeamsUp mod, package `com.ensox.lootbeamsup.api`, plain Java 21; see the [Addon API](https://github.com/enso-x/lootbeamsup-docs/wiki/Addon-API) wiki page |

Artifacts are published from each library's own build (`gradlew publishPages`;
EnsoX UI and dynamic-config: `gradlew publishLibrary -PmavenDir=<this checkout>`);
released versions are never overwritten.

Text files (`.pom`, `maven-metadata.xml`, `.module`) are stored with LF line endings and
their checksums are computed over the LF bytes. `.gitattributes` keeps git from converting
anything, so the served bytes are exactly the committed ones. Every build normalizes its files
when it publishes (`publishLibrary`, ExLuaJ `publishPages`).
