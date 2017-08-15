danted安装部署
1.	环境要求
经过测试和修改安装脚本，当前danted支持如下系统版本：
系统类型	版本


Centos 6系列	6.0
	6.2
	6.3
	6.4 (推荐)
	6.5
	6.6
	6.7
	6.8
Centos 7系列	7.1
	7.2



ubuntu系列	12.04
	14.04.2
	14.04.3
	14.04.5
	15.10
	16.04

Oracle linux系列	6.5
	7.1
	7.2
2.	安装选项
选项	描述
--port=	socks5 端口号码
--ip=;;	配置的IP地址，默认全部开启，使用;分格
--user=	pam认证用户名
--passwd=	pam认证用户密码
--master=	免认证地址，例如 github.com 或者 8.8.8.8/32
使用实例：
bash danted_install.sh --port="1000" --ip="192.168.199.206" --user="zk" --passwd="123456"
3.	功能特点
•	1. 采用dante稳定版本 1.3.2 编译安装。
•	2. 自动识别系统IP（默认排除192.168.0.*， 10.0.0.*,127.0.0.*）,根据安装命令选择部分Ip或者全部IP安装(多IP环境)。
•	3. 采用PAM 用户认证，认证不需要添加系统用户（默认添加进程用户sock），删除、添加用户方便，安全。
•	4. sock5 运行状态查看,系统启动后自动加载。
•	5. 完美支持多访问进出口（多IP的环境，支持 使用IP-1，访问网站IP查询为IP-1）。
•	6. 认证方式可选： 无用户名密码，系统用户名密码，Pam用户名密码
•	7. 完美支持Centos/Ubuntu/Debian,自动识别系统进行安装配置。[注意，经反馈，Centos 5 无法使用。]
•	8. 自定义对连接客户端认证方式，支持白名单即支持某些IP/IP段无需认证即可连接。
4.	 安装步骤
•	1. 下载 danted_install.sh脚本
•	2. [可选] 修改 默认参数，DEFAULT_PORT 为默认端口，DEFAULT_USER PAM用户名，DEFAULT_PAWD PAM用户对应密码 MASTER_IP 为免认证白名单（域名，IP可选： 如默认的buyvm.info 或者具体Ip 8.8.8.8/32 ）
•	3. 修改后，执行 bash danted_install.sh （指使用默认参数）
•	4. 若运行结束后显示 Dante Server Install Successfuly! 则表明成功。
o	显示 Dante Server Install Failed! 则表明安装失败。

注意：也可动态知道配置参数， 执行命令如下:
	bash danted_install.sh --port="1000" --ip="192.168.199.206" --user="zk" --passwd="123456"
5.	安装后使用说明
•	1. 命令参数 /etc/init.d/danted {start|stop|restart|status|add|del}
•	2. 重启sock5 /etc/init.d/danted restart 或者 service danted restart
•	3. 关闭sock5 /etc/init.d/danted stop 或者 service danted stop
•	4. 开启sock5 /etc/init.d/danted start 或者 service danted start
•	5. 查看sock5状态 /etc/init.d/danted status 或者 service danted status
•	6. 添加SOCK5 PAM用户/修改密码 /etc/init.d/danted add 用户名 密码
•	7. 删除SOCK5 PAM用户 /etc/init.d/danted del 用户名
•	8. 配置文件路径/etc/danted/sockd.conf
•	9. 日志记录路径 /var/log/danted.log
•	10. danted 帮助命令 danted --help
6.	使用注意事项
•	1. 绝大部分浏览器（除了Opera）都不支持带密码认证的Socks5，所以使用电脑需要安装proxifier/proxycap 等软件做验证处理。
•	2. 如果是固定IP/Ip 段 可以修改配置文件，设置白名单访问。
o	进入 /etc/danted/ 找到配置文件
o	修改 第一个pass {} 模块下的 from: Master_IP/32 to: 0.0.0.0/0 . 把 Master_IP/32 修改为需要使用代理的Ip段/IP地址 如 114.114.114.0/24 或者 5.5.5.5/32 . 多个访问源，请复制多个 client pass {} 模块
o	重启Danted 进程 service danted restart
•	3. 如需删除danted，请参考以下命令删除程序文件
o	service danted stop
o	rm -rf /etc/danted/
o	rm -f /etc/init.d/danted
7.	遗留问题
1. 分析log对连接sock5的用户进行统计。

danted安装部署
1.	环境要求
经过测试和修改安装脚本，当前danted支持如下系统版本：
系统类型	版本


Centos 6系列	6.0
	6.2
	6.3
	6.4 (推荐)
	6.5
	6.6
	6.7
	6.8
Centos 7系列	7.1
	7.2



ubuntu系列	12.04
	14.04.2
	14.04.3
	14.04.5
	15.10
	16.04

Oracle linux系列	6.5
	7.1
	7.2
2.	安装选项
选项	描述
--port=	socks5 端口号码
--ip=;;	配置的IP地址，默认全部开启，使用;分格
--user=	pam认证用户名
--passwd=	pam认证用户密码
--master=	免认证地址，例如 github.com 或者 8.8.8.8/32
使用实例：
bash danted_install.sh --port="1000" --ip="192.168.199.206" --user="zk" --passwd="123456"
3.	功能特点
•	1. 采用dante稳定版本 1.3.2 编译安装。
•	2. 自动识别系统IP（默认排除192.168.0.*， 10.0.0.*,127.0.0.*）,根据安装命令选择部分Ip或者全部IP安装(多IP环境)。
•	3. 采用PAM 用户认证，认证不需要添加系统用户（默认添加进程用户sock），删除、添加用户方便，安全。
•	4. sock5 运行状态查看,系统启动后自动加载。
•	5. 完美支持多访问进出口（多IP的环境，支持 使用IP-1，访问网站IP查询为IP-1）。
•	6. 认证方式可选： 无用户名密码，系统用户名密码，Pam用户名密码
•	7. 完美支持Centos/Ubuntu/Debian,自动识别系统进行安装配置。[注意，经反馈，Centos 5 无法使用。]
•	8. 自定义对连接客户端认证方式，支持白名单即支持某些IP/IP段无需认证即可连接。
4.	 安装步骤
•	1. 下载 danted_install.sh脚本
•	2. [可选] 修改 默认参数，DEFAULT_PORT 为默认端口，DEFAULT_USER PAM用户名，DEFAULT_PAWD PAM用户对应密码 MASTER_IP 为免认证白名单（域名，IP可选： 如默认的buyvm.info 或者具体Ip 8.8.8.8/32 ）
•	3. 修改后，执行 bash danted_install.sh （指使用默认参数）
•	4. 若运行结束后显示 Dante Server Install Successfuly! 则表明成功。
o	显示 Dante Server Install Failed! 则表明安装失败。

注意：也可动态知道配置参数， 执行命令如下:
	bash danted_install.sh --port="1000" --ip="192.168.199.206" --user="zk" --passwd="123456"
5.	安装后使用说明
•	1. 命令参数 /etc/init.d/danted {start|stop|restart|status|add|del}
•	2. 重启sock5 /etc/init.d/danted restart 或者 service danted restart
•	3. 关闭sock5 /etc/init.d/danted stop 或者 service danted stop
•	4. 开启sock5 /etc/init.d/danted start 或者 service danted start
•	5. 查看sock5状态 /etc/init.d/danted status 或者 service danted status
•	6. 添加SOCK5 PAM用户/修改密码 /etc/init.d/danted add 用户名 密码
•	7. 删除SOCK5 PAM用户 /etc/init.d/danted del 用户名
•	8. 配置文件路径/etc/danted/sockd.conf
•	9. 日志记录路径 /var/log/danted.log
•	10. danted 帮助命令 danted --help
6.	使用注意事项
•	1. 绝大部分浏览器（除了Opera）都不支持带密码认证的Socks5，所以使用电脑需要安装proxifier/proxycap 等软件做验证处理。
•	2. 如果是固定IP/Ip 段 可以修改配置文件，设置白名单访问。
o	进入 /etc/danted/ 找到配置文件
o	修改 第一个pass {} 模块下的 from: Master_IP/32 to: 0.0.0.0/0 . 把 Master_IP/32 修改为需要使用代理的Ip段/IP地址 如 114.114.114.0/24 或者 5.5.5.5/32 . 多个访问源，请复制多个 client pass {} 模块
o	重启Danted 进程 service danted restart
•	3. 如需删除danted，请参考以下命令删除程序文件
o	service danted stop
o	rm -rf /etc/danted/
o	rm -f /etc/init.d/danted
7.	遗留问题
1. 分析log对连接sock5的用户进行统计。

