# 创建 Library 项目

Library 项目跟常规的 Android 项目很相似，只是有部分不同。

既然构建 Library 跟构建应用不同，那肯定用不同的插件，但是两个插件内部其实共享大部分同样的代码，且由同一个 jar 包提供：`com.android.tools.build.gradle`

``` Groovy
buildscript {
    repositories {
        mavenCentral()
    }

    dependencies {
        classpath 'com.android.tools.build:gradle:0.5.6'
    }
}

apply plugin: 'android-library'

android {
    compileSdkVersion 15
}
```

这里创建了一个使用 API 15 编译的 Library 项目，并且 *SourceSet*、 dependencies（依赖关系）的配置方法与普通项目一样，且同样支持自定义配置。
