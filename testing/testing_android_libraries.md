# 测试 Android Library 项目

测试 Android Library 项目类似于测试应用项目。

唯一的不同点在于整个库（包括它的依赖）都是自动作为依赖库被添加到测试应用中。  
结果就是测试 APK 不单只包含它的代码，还包含了 Library 项目以及它的所有依赖的代码。  
Library 的 manifest 被组合到测试应用的 manifest 中（引用这个 Library 的其他项目作为容器）。

**<font color='green'>androidTest</font>** task 变为只执行安装（或者卸载）测试 APK（因为没有其它 APK 被安装）。

其它的部分都是相同的。