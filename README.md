# AnkoExt
这个库作为官方的[Anko](https://github.com/Kotlin/anko)的一个扩展，提供官方**Anko**没有提供的一些实用方法，建
议和官方Anko一起导入到你的项目中。

# 使用方法：
1) 增加以下脚本到你的工程根目录的build.gradle文件中
<pre>
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
</pre>

2）在你的app工程中，增加如下依赖:
<pre>
dependencies {
	        compile 'com.github.yuanhoujun:AnkoExt:0.1.0'
}
</pre>

以下是目前AnkoExt提供的一些实用方法，以及和Java语言的简单对比：

在Activity中获取常用的服务管理类
### Java
<pre>
NotificationManager notificationManager = (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE)
</pre>

### Kotlin
<pre>
val notificationManager = notificationManager()
</pre>

**AnkoExt** 也提供了其它服务的获取接口：
<pre>
val windowManager = windowManager()
val alarmManager = alarmManager()
val wifiManager = wifiManager()
val pref = defaultSharedPreferences()
</pre>

更多服务获取接口，欢迎你Fork这个仓库，推送Pull Request。

针对字符串处理，**AnkoExt**也提供了如下接口：
### Java
<pre>
// 将指定格式字符串转换为Date
 SimpleDateFormat formatter = SimpleDateFormat(pattern , Locale.CHINA)
 try {
    Date result = formatter.parse(this)
 } catch (e: Exception) {
 }
</pre>

### Kotlin
<pre>
// 将指定格式字符串转换为Date
val date = "2017-10-1 12:12:12".toDate("yy-MM-dd HH:mm")
</pre>

当然，**AnkoExt**也提供了将Date转换为字符串的接口:
<pre>
val dateString = date.toDateString("yy-MM-dd HH:mm")
</pre>

针对SharePreferences，**AnkoExt**也提供了一些简化处理的接口：
### Java
<pre>
SharedPreferences pref = ...
SharedPreferences.Editor editor = pref.editor();
editor.putString("name" , "Scott Smith");
editor.apply();
</pre>

### Kotlin
<pre>
val pref = ...
pref.edit {
    putString("name" , "Scott Smith")
}
</pre>

针对Android常用数据格式转换，**AnkoExt**也提供了一些相应的接口，这个其实官方**Anko**也有，不过解决方案不太一样：
### Kotlin
<pre>
val dp = 12.toDp(this)
val px = 12.toPx(this)
val dateString = 12L.toDateString("yy-MM-dd HH:mm")
</pre>

### 针对字符串格式的判断，**AnkoExt**提供了如下接口：
<pre>
val str = ...
// 判断该字符串是否是一个有效的手机号
str.isPhoneNumber()
// 判断该字符串是否是一个有效的IP地址
str.isIP()
// 判断该字符串是否是一个有效的身份证号
str.isIdNumber()
// 判断该字符串是否是一个有效的邮箱地址
str.isEmail()
// 判断该字符串是否全是中文
str.isChinese()
// 字符串安全转换到整型
str.safeConvertToInt()
// 字符串安全转换到整型
str.safeConvertToInt()
// 字符串安全转换到长整型
str.safeConvertToLong()
// 字符串安全转换到浮点类型
str.safeConvertToFloat()
// 字符串安全转换到双精度类型
str.safeConvertToDouble()
// 字符串安全转换到短整型类型
str.safeConvertToShort()


</pre>

### Android常用数据获取
在Contex的子类，例如：Activity，Application等，可以直接使用如下api获取如下数据:
<pre>
// 获取整型版本号
val versionCode = versionCode()
// 获取版本名称
val versionName = versionName()
// 获取Density
val density = density()
// 获取清单文件元数据 (这里可能会导致获取失败)
val meta = metaData("channel")
// 获取导航栏高度
val navigationBarHeight = navigationBarHeight()
// 获取状态栏高度
val statusBarHeight = statusBarHeight()
</pre>