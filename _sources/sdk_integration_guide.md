# 导入SDK

SDK支持 JDK 1.6 和 Android SDK version 18 以上系统

​       

## 1.1 导入SDK


```java

        implementation 'com.eling:imlibrary:1.0.0'
        
```






## 1.2 SDK中已导入的第三方依赖

```java

    implementation 'com.android.support:appcompat-v7:25.2.0'
    //alyun oss
    implementation('com.aliyun.dpa:oss-android-sdk:+') {
        exclude module: 'okhttp'
    }
    implementation 'com.zhy:okhttputils:2.6.2'
    implementation 'com.google.code.gson:gson:2.6.2'
        
```
>使用SDK时避免与上诉包冲突
