# PrettyGadle
工作中使用的gradle配置

# allprojects
返回该Project对象以及其所有子项目

# subprojects
返回所有子项目

# project(‘:sub-project-name’)
在父项目的build.gradle文件中通过project(‘:sub-project-name’)来设置对应的子项目的配置

# checkstyle
CheckStyle是SourceForge下的一个项目，提供了一个帮助JAVA开发人员遵守某些编码规范的工具
apply plugin: 'checkstyle'
checkstyle{
configFile = file('config/checkstyle/checkstyle-main.xml')
}

# FindBugs
FindBugs 是一个静态分析工具，它检查类或者 JAR 文件，将字节码与一组缺陷模式进行对比以发现可能的问题。
apply plugin: 'findbugs'

# JDepend
在开发Java项目时经常会遇到关于包混乱的问题， JDepend工具可以帮助你在开发过程中随时跟踪每个包的依赖性（引用/被引用），从而设计高维护性的架构，不论是在打包发布还是版本升级都会更加轻松。
apply plugin: 'jdepend'

# PMD
PMD是一种开源分析Java代码错误的工具。与其他分析工具不同的是，PMD通过静态分析获知代码错误，即在不运行Java程序的情况下报告错误。
apply plugin: 'pmd'

# 构建脚本的依赖
buildscript {
    repositories {
        mavenCentral()
    }
    dependencies {
        classpath "gradle-cucumber-plugin:gradle-cucumber-plugin:0.2"
    }
}
apply plugin: com.excella.gradle.cucumber.CucumberPlugin

# 使用Wrapper指定Gradle的版本
task wrapper(type: Wrapper) {
    gradleVersion = '1.0'
    archiveBase = 'PROJECT'
    archivePath = 'gradle/dists'
}

gradle wrapper