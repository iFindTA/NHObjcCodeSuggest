# Developer's Tips：
**--description:开发中的一些建议点**

1，原则、规范上一个文件的注释量不少于20%代码量

2，原则上一些重要敏感逻辑需要单元测试

3，原则上不允许前端因后台数据而崩溃（类型、null）

4，原则上类名前缀使用公司字母缩写不超过三个字母

5，原则上非UI操作均放在其他线程操作，譬如background queue

6，过滤换行与空格在可输入性文字在使用前

7，字典、数组取值前保证类型匹配（安全取值），构造时注意去除nil对象

8，日期、数字等格式化器使用单例模式写法

9，网络请求前判断必输项及格式eg电话号码、邮箱、昵称、密码等长度格式，如没有填写需给出相对应的HUD提示

10，下拉刷新上拉更多，如内容不超过一屏则隐藏上拉更多

11，基本类型声明、运算时注意32bits、64bits适配

12，在heightForRow中不推荐直接调用cellForRow，可以尝试使用[UITableView-FDTemplateLayoutCell](https://github.com/forkingdog/UITableView-FDTemplateLayoutCell)类库（与Masonry无关）或Masonry autoLayout布局。

13，如无特殊需求不推荐直接使用delegate‘s window

14，触发网络请求的控件在网络请求中需要控制再次触发时机

15，针对变化不频繁的数据推荐使用缓存刷新可由用户触发

16，数据持久化时注意去重和时间覆盖

17，数据库使用时注意open、close等对应操作，时间存储采取标准数据库格式

18，自动增加build脚本(丹霞提供)：
```
#!/bin/bash
buildNumber=$(/usr/libexec/PlistBuddy -c "Print CFBundleVersion" "$INFOPLIST_FILE")
buildNumber=$(($buildNumber + 1))
/usr/libexec/PlistBuddy -c "Set :CFBundleVersion $buildNumber" "$INFOPLIST_FILE"
```

19，Release前去除无用的第三方库，eg. reveal etc.

20，Release后一定记得**++在Git上Release一个版本Tag++** eg：V2.1.1 etc

21，