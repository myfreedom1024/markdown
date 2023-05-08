<details>
<summary>
VMware虚拟机挂载宿主机共享目录
</summary>

* 在Linux中安装vm-tools：
yum install -y open-vm-tools open-vm-tools-desktop
* 查看共享的目录
vmware-hgfsclient
* 执行命令挂载目录
mount -t fuse.vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other,nonempty
* 修改数据令系统启动时自动挂载
vim /etc/fstab  
* 在末尾另起一行 添加:  
.host:/ /mnt/hgfs fuse.vmhgfs-fuse allow_other 0 0
* 再次挂载目录
vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other,nonempty
* 建立软连接
ln -s /mnt/hgfs /www/work

</details>
