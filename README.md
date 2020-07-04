# wsl--
wsl遇到的奇怪问题


#1.奇怪的配置文件

之前碰到无法yarn跟npm,我以为是哪里出了问题,没想到是zsh上还需要再配置一遍~/.zshrc,把etc/profile的配置文件再复制到zsh上就好了.


#2.奇怪的权限问题


碰到问题是无法chmod,老提示chmod: cannot read directory,后来搜的问题是wsl配置文件还要搞一下sudo vim /etc/wsl.conf,发现并不对,最后是终端sudo umount /mnt/e  然后sudo mount -t drvfs E:/mnt/e -o metadata,盘符写自己的就行
