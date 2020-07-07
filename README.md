# wsl--
wsl遇到的奇怪问题


#1.奇怪的配置文件#

之前碰到无法yarn跟npm,我以为是哪里出了问题,没想到是zsh上还需要再配置一遍~/.zshrc,把etc/profile的配置文件再复制到zsh上就好了.


#2.奇怪的权限问题#


碰到问题是无法chmod,老提示chmod: cannot read directory,后来搜的问题是wsl配置文件还要搞一下sudo vim /etc/wsl.conf,发现并不对,最后是终端sudo umount /mnt/e  然后sudo mount -t drvfs E: /mnt/e -o metadata,盘符写自己的就行,再把项目的node_modle删掉重新yarn就好了



#3.wsl安装flutter还有运行dart问题#


(1)直接在wsl里配置flutter会报错:
/mnt/c/Development/flutter/bin/flutter: line 5: $'\r': command not found
/mnt/c/Development/flutter/bin/flutter: line 6: $'\r': command not found
/mnt/c/Development/flutter/bin/flutter: line 14: $'\r': command not found
(2)要配置一下环境变量:
alias winpro='cd /mnt/<DIRECTORY IN WINDOWS YOU WANT>'

flutter() {
    command CMD.exe /c flutter $@
}
(3)如果有zsh,也要复制给zsh环境变量一份,就能运行flutter了
#dart#

(1)直接在windows的vscode里用wsl里的命令行时,一旦点击runcode,就会报路径错误,是因为zsh照着windows的路径运行的,肯定不对,只能重新开一个vscode窗口专门运行wsl才可以,那样路径是对的,现在暂时无解
