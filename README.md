***  
#### GIT
1. git pull origin master/分支名字 --rebase(作用：拉取分支并且与原有的分支合并)  
2. git push origin master/分支名字  
3. git add .  
4. git reset 文件名(作用：将add的文件移除add仓库)  
5. git commit -s(作用：自定义编辑文本提交)  
6. git log/reflog(作用：查看git记录)  
7. git stash(作用：保存未add的文件,并不参与commit,之后可以通过git stash pop来移出)  
8. git stash pop(作用：移出通过git stash的文件)  
9. git stash list(作用：查看所有的缓存)
10. git remote add origin (作用：与远程仓库关联)  
11. git clone(作用：克隆远程仓库)  
12. git checkout 文件名/. (作用：还原修该过的未被add的文件)  
13. git checkout -b 分支名(作用：创建一个分支并且切换到这个分支)  
14. git blame 文件名(作用：查看这个文件没一行修改者是谁，之前版本的也会显示)
15. git reset HEAD~/log (作用：回退版本)
16. git status(作用：查看当前的git状态)
17. git diff 文件名 (作用：查看文件的变化)  
18. git diff --cache(作用：查看已经add但是没有commit的文件)
19. git diff HEAD(作用：查看上面两个内容的合并)
20. git cherry-pick (作用:当你需要在分支上提交代码到另一个分支上的时候可以使用)


***  
#### ADB  
1. adb kill-server  
2. adb start-server  
4. adb devices(获取是设备列表以及设备状态)
5. adb get-state(获取设备状态，有device——设备正常连接、offline——连接出现异常，设备无响应、unkonow——没有设备连接三种)
6. adb install (-r) xx.apk (安装apk -r使用来覆盖安装)
7. adb uninstall (-k) 包名 (卸载apk -k卸载时保留数据)
8. adb reboot (重启手机)

###### pm——PackageManager
1. adb shell pm list package (-s/-3/-f/-i) 过滤字 (列出手机装的所有应用的包名 `-s`:列出系统应用 `-3`:列出第三方应用  
  `-f`:列出应用包名以及对应apk存放的位置 `-i`:列出应用包名及其安装来源)
2. adb shell pm path 包名 (列出对应包名的.apk位置)(基本可而已使用adb shell pm list package -f 来取代)
3. adb shell pm list instrumentation (-f) (列出含有单元测试case的应用，-f显示具体地址)
4. adb shell pm dump 包名 (列出指定应用的dump的信息)
5. adb shell pm install xxx.apk (用来安装在手机中存在的apk)
6. adb shell pm uninstall 包名 (同理adb unstall 包名)
7. adb shell pm clear 包名 (清除数据)
8. adb shell pm get-install-location 包名 (获取应用安装的位置 0——默认自动 1——默认安装在手机内部 2——默认安装在外部存储)

###### am——ActivityManager
1. adb shell am start (-n/-S/-W/-a) 包名/包名.activity名称 (-d tel:/http:) (启动一个activity -n:直接启动 -S:先停止后启动 -W:先等待后启动 -a和-d组合用)
2. adb shell am monitor (监控crash与ANR和activity的启动)
3. adb shell am force-stop 包名 (结束应用)

###### input——向android设备发送按键事件
1. adb shell input text xxx (发送xxx文本内容，不能发送中文 必须某个输入框有焦点才可以)
2. adb shell input ketevent (KEYCODE_HOME/3)(5——通话记录)(6——锁屏)(7——0 8——1 ... 16——9 17——* 18——#)(24——调大音量 25——调小音量) (点击home键)
3. adb shell input tap xx xx (向屏幕坐标(xx,xx)发送一个触摸事件)
4. adb shell input swipe xx xx zz zz (time) (从坐标(xx,xx)滑动到(zz,zz) 经过time时间)

###### 其他
1. adb shell screencap -p 存储地址 (截屏)
2. adb shell screenrecord 存储地址 (录屏)
3. adb shell ime list -s (列出设备上的输入法)
4. adb shell ime set xx (对设备设置输入法)
5. adb shell wm size (显示设备的分辨率)

###### 开发用到的
1. adb shell dumpsys activity|grep "mFocusedActivity" (作用：显示当前栈顶的Activity)——linux  
adb shell dumpsys activity|findstr "mFocusedActivity" ——windows
2. adb shell uiautomator dump [存储地址] (获取当前界面的控件信息)

***  
#### gradle  
