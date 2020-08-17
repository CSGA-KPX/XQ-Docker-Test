# 先驱机器人Docker化测试

# 一、Docker容器化（成功）

1. 替换环境

    * 新装wine-coolq容器：run之前解压先驱机器人程序到挂载目录内。
    
      然后用``docker run --name=coolq -d -p 8080:9000 -p 8081:10000 -v G:\docker-desktop\coolq:/home/user/coolq -e VNC_PASSWD=12345678 coolq/wine-coolq``安装
      
      其中8080/9000是VNC端口，8081/10000是cqhttp端口。

    * 已有wine-coolq容器：停止容器，备份插件配置文件，然后删除过改名挂载目录内酷Q相关文件，然后解压放置先驱机器人程序，恢复配置文件。

2. 启动容器，VNC连接，应当正常出现先驱机器人主界面，然后报ntdll.dll错误（正常现象）。
   
3. ``docker exec -it coolq bash`` 进入容器shell，运行apt-get update和apt-get upgrade更新wine全家桶。
   * 如有需要，用``sed -i "s/archive.ubuntu.com/mirrors.aliyun.com/g" /etc/apt/sources.list``和``export https_proxy=http://xxx.yyy.zzz.aaa:1081/``加速更新。

4. 重启容器，VNC连接，现在应能正常运行先驱机器人。


# 二、CQXQ插件安装（成功）

1. 去``https://github.com/w4123/CQXQ``下载插件按教程安装。
2. VNC内关闭先驱机器人，等待自动重启。
3. 检查日志中插件状态。

# 三、CQHttp安装（基本成功）

* 备注：发送消息需要XQ 0817+，0805无法发送原因不明
* base64:///图片无效，XQ好像不支持base64发送，[可能需要CQXQ转化base64](https://github.com/w4123/CQXQ/issues/18)

1. 取``https://github.com/richardchien/coolq-http-api``下载插件dll和json，按照CQXQ指示安装。

2. 拷贝ucrtbased.dll, msvcp140d.dll, libiconv.dll, sqlite3.dll等到挂载目录（不拷的话可能报LoadLibrary 126错误）。

3. VNC内关闭先驱机器人，等待自动重启。

4. 检查日志中插件状态。
