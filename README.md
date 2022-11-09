搭建v2ray开启Debian自带BBR加速

把下面代码一起复制并粘贴到VPS命令行中执行，有回显  tcp_bbr   20480  即为开启！
```bash
   echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
   echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
   sysctl -p
   lsmod | grep bbr
   ```

搭建Xray

更新系统

* 		yum update -y #CentOS系统命令
* 		apt update -y #Debian系统命令

安装工具组件

* 		yum install -y wget #CentOS系统命令
* 		apt install -y wget #Debian系统命令

执行Xray一键安装脚本

```bash
   wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/mack-a/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh
   ```

该脚本运行一次以后，以后想调出该脚本使用，只需要在 VPS 命令行输入 vasma 即可。
若是忘记了各项配置参数，可以在 VPS 里面输入上述 vasma ，然后输入数字 3 ——查看账号，即可翻看原先搭建的各项协议参数。
部署成功以后，在浏览器中输入搭建时绑定的域名，https://xxx.xxx.xxx，即可到达该脚本自动部署的伪装网站。如下图所示：

Cloudflare优选IP MacOS运行代码：

```bash
   curl https://raw.githubusercontent.com/badafans/better-cloudflare-ip/master/shell/cf.sh -o cf.sh && chmod +x cf.sh && ./cf.sh
   ```

打开Cloudflare 小云朵

打开 Cloudflare 小云朵，也就是开启CDN。
找到 SSL/TLS 一栏，把里面的 加密模式 改为 完全

添加Qv2ray节点

查看刚才搭建成功的 Xray 的节点信息，找到这个协议 ：VLESS + WS + TLS + CDN     
