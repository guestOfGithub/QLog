# QLog
Android Log Persistence Lightweight Framework 安卓日志持久化轻量级框架
<br/>
  * 短小精悍却五脏俱全,无任何依赖,简洁党的福音
  * 使用buff延迟写入,time+size两种条件触发
  * 支持打印调用方法栈
  * 支持自动清理过期日志
  * 非阻塞,线程安全,SimpleDateFormat优化
## DEMO
```
    QLog.init(getApplication());//默认路径->/Android/data/包名/files/DCIM/QLog
    Log.i("info日志"));//默认写入->/2020-10-20_QLog.txt
    Log.e("login", "error日志"));//写入->2020-10-20_login.txt
```
## 集成
可以直接下载[QLog.java](https://raw.githubusercontent.com/tohodog/QLog/master/app/src/main/java/com/qsinong/example/single/QLog.java)单文件使用,够轻量!
<br/>
### Gradle
```
allprojects {
    repositories {
        maven {
            url "https://jitpack.io"
        }
    }
}

dependencies {
    implementation 'com.github.tohodog:QLog:1.0'
}
```

## 高级
```
QLog.init(QLogConfig.Build(getApplication())
        .buffSize(128 * 1024)//buff大小
        .delay(10000)//延迟写入时间
        .day(30)//日志保留30天,默认无限制
        .methodCount(1)//打印调用方法名
        .debug(true)//true会输出控制台,上线可关掉
        .build());

QLog.flush();//如果要杀死App,需调用写入缓存
```

## Other
  * 有问题请Add [issues](https://github.com/tohodog/QLog/issues)
  * 如果项目对你有帮助的话欢迎[![star][starsvg]][star]

[starsvg]: https://img.shields.io/github/stars/tohodog/QLog.svg?style=social&label=Stars
[star]: https://github.com/tohodog/QLog
