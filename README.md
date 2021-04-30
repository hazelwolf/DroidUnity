# Unity AR Core Integration with Native Android App

## Steps to Recreate
1. Export Unity as Gradle project, under build settings > Other settings change from Mono to IL2CPP and select ARMv7 and ARMv64.

![configuration unity](./images/configurationunity.png)

2. Create a new project in android studio and update settings.gradle with <br>`include ':unityLibrary'`
`project(':unityLibrary').projectDir = new File("unityLibrary")`

![Gradle settings](./images/settings_gradle.png)

where project dir is path to the unityLibrary folder.

3. In project level build.gradle under all projects include <br>
`flatDir {
            dirs "${project(':unityLibrary').projectDir}/libs"
        }`

![Project build gradle](./images/build_gradle_project.png)
:exclamation: Failing to do so will not compile Unity Package libraries such as AR Core Unity etc.

4. In app level gradle under depedencies add 
`implementation project(':unityLibrary')`

![App build gradle](./images/build_gradle_app.png)
5. In strings.xml add string value 
`<string name="game_view_content_description">Game view</string>`

![App build gradle](./images/strings_xml.png)
:exclamation: Failing to do so will throuw error on launching unity activity such as Res.layout not found.

