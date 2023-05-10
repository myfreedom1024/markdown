<details>
<summary>
<span style="color: red;font-size: 20px;"><b>
git设置忽略文件权限更改
</b></span>
</summary>

```
vi .git/conf
```
[core]->filemode:改成false

</details>

<details>
<summary>
<span style="color: red;font-size: 20px;"><b>
查看Linux系统信息
</b></span>
</summary>

* 查看当前系统的内核信息
```
cat /proc/version
```
```
uname -a
```
* 查看发型版本信息
```
cat /etc/os-release
```
</details>

<details>
<summary>
<span style="color: red;font-size: 20px;"><b>
开启mysql的root用户外网访问
</b></span>
</summary>

```
update user set host='%' where user ='root';
```
```
FLUSH PRIVILEGES;
```
</details>

<details>
<summary>
<span style="color: red;font-size: 20px;"><b>
linux增加编译速度
</b></span>
</summary>

```
sudo make -j $(nproc)
```
```
sudo cmake --build . --target all -- -j $(nproc)
```
</details>

<details>
<summary>
<span style="color: red;font-size: 20px;"><b>
VMware虚拟机挂载宿主机共享目录
</b></span>
</summary>

* 在Linux中安装vm-tools
```
suduo yum install -y open-vm-tools open-vm-tools-desktop
```
* 查看共享的目录
```
vmware-hgfsclient
```
* 执行命令挂载目录
```
mount -t fuse.vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other,nonempty
```
* 修改数据令系统启动时自动挂载
```
vim /etc/fstab
```
* 在末尾另起一行 添加:
```
.host:/ /mnt/hgfs fuse.vmhgfs-fuse allow_other 0 0
```
* 再次挂载目录
```
vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other,nonempty
```
* 建立软连接
```
ln -s /mnt/hgfs /www/work
```
</details>

<details>
<summary>
<span style="color: red;font-size: 20px;"><b>
设置网络-vmware-centos
</b></span>
</summary>

* 打开网卡
```
vi /etc/sysconfig/network-scripts/ifcfg-eth33
```
* 填入配置项(固定IP)
```
TYPE="Ethernet"
BOOTPROTO="static"
DEFROUTE="yes"
NAME="ens33"
DEVICE="ens33"
ONBOOT="yes"
IPADDR=1.1.1.5
PREFIX=24
GATEWAY=1.1.1.2
DNS1=8.8.8.8
DNS2=8.8.4.4
```
* 编辑->虚拟网络编辑器
![avatar](https://github.com/xiaofancomputer/image/blob/main/%E8%99%9A%E6%8B%9F%E6%9C%BA%E8%AE%BE%E7%BD%AE.png)
</details>

