# 先驱机器人Docker化测试

# 一、Docker容器化（成功）

1. 替换环境

    * 新装：解压先驱机器人程序到挂载目录内

    * 已有：停止容器，删除过改名挂载目录内酷Q相关文件，然后解压放置先驱机器人程序

2. docker run ...启动容器，VNC连接，应当正常出现先驱机器人主界面，然后报ntdll.dll错误（正常现象）。

3. docker进入容器shell，运行apt-get update和apt-get upgrade更新wine全家桶。

4. 重启容器，VNC连接，现在应能正常运行先驱机器人。



# 二、CQXQ插件安装（成功）

1. 去``https://github.com/w4123/CQXQ``下载插件按教程安装。
2. 关闭先驱机器人，等待自动重启。
3. 检查日志中插件状态。



# 三、CQHttp安装（成功，等待功能测试）

1. 取``https://github.com/richardchien/coolq-http-api``下载插件dll和json，按照CQXQ指示安装。

2. 拷贝ucrtbased.dll, msvcp140d.dll, libiconv.dll, sqlite3.dll等到挂载目录。

3. 关闭先驱机器人，等待自动重启。

4. 检查日志中插件状态。
