# 基本知识和配置

正如前面所提到的，紧邻 **<font color='green'>main</font>** *sourceSet* 的就是 **<font color='green'>androidTest</font>** *sourceSet*，默认路径在 `src/androidTest/` 下。

在这个测试 *sourceSet* 中会构建一个使用 Android 测试框架，并且可以部署到设备上的测试 apk 来测试应用程序。这里面包含单元测试，集成测试，和后续 UI 自动化测试。

`<instrumentation>` 节点会包含在测试构建过程中自动生成的测试 AndroidManifest.xml，但是你也可以自己创建一个 `src/androidTest/AndroidManifest.xml` 文件并添加其他组件。

下面的值可以用来配置测试应用，相当于配置 `<instrumentation>` 节点：

* `testPackageName`
* `testInstrumentationRunner`
* `testHandleProfiling`
* `testfunctionalTest`

正如前面所看到的，这些配置在 **<font color='green'>defaultConfig</font>** 对象中配置：

``` Groovy
android {
    defaultConfig {
        testPackageName "com.test.foo"
        testInstrumentationRunner "android.test.InstrumentationTestRunner"
        testHandleProfiling true
        testFunctionalTest true
    }
}
```

在测试应用程序的 manifest 文件中，`instrumentation` 节点的 `targetPackage` 属性值会自动使用测试应用的包名设置，即使这个名称是通过 **<font color='green'>defaultConfig</font>** 或者 *Build Type* 对象自定义的。这也是 manifest 文件需要自动生成的一个原因。

另外，这个测试 *sourceSet* 也可以拥有自己的依赖。  
默认情况下，应用程序和他的依赖会自动添加到测试应用的 classpath 中，但是也可以通过以下来扩展：

``` Groovy
dependencies {
    androidTestCompile 'com.google.guava:guava:11.0.2'
}
```

**<font color='green'>assembleTest</font>** 不依赖于主要的 **<font color='green'>assemble</font>** task，所以要手动运行测试。
当测试运行时，**<font color='green'>assembleTest</font>** task 会自动运行，并生成测试应用。

目前只有一个 *Build Type* 会被测试。默认情况下是 **<font color='green'>debug</font>** *Build Type*，可以通过以下代码进行自定义配置：

``` Groovy
android {
    ...
    testBuildType "staging"
}
```