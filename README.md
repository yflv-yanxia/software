# software
## ffmpeg
    ffmpeg -ss 00:00:00 -i input.mp4 -c copy -t 00:01:00 output.mp4
    ffprobe -i video_path -show_entries format-duration -v quiet -of csv="p=0"

## linux
    find $directory -type f -name "*" -exec mv {} $directory2/. \;
### install
    touch ~/.bashrc<br>
    echo -e "export LD_LIBRARY_PATH=$LD_LIBRAARY_PATH:"
    source ~/.bashrc
    if [ ! -f -d -e  "" ]; then<br>
        cd
        echo
        exit
    fi

## sourceInsigtht

## wall
    psiphon3
    ShadowSocks

## vim
    set number
    set mouse=a

## abench
## anaconda
    url errors： modify ./.condarc
    https://mirror.tuna.tsinghua.edu.cn/help/anaconda/
    add channels
## tmux
    tmux new-session -s name
    tmux attach-session -t name
    tmux list-session
    
    1）进入tmux面板后，一定要先按ctrl+b，然后松开，再按其他的组合键才生效。 
    2）常用到的几个组合键：
    ctrl+b ?            显示快捷键帮助
    ctrl+b 空格键       采用下一个内置布局，这个很有意思，在多屏时，用这个就会将多有屏幕竖着展示
    ctrl+b !            把当前窗口变为新窗口
    ctrl+b  "           模向分隔窗口
    ctrl+b %            纵向分隔窗口
    ctrl+b q            显示分隔窗口的编号
    ctrl+b o            跳到下一个分隔窗口。多屏之间的切换
    ctrl+b 上下键      上一个及下一个分隔窗口
    ctrl+b C-方向键    调整分隔窗口大小
    ctrl+b &           确认后退出当前tmux
    ctrl+b [           复制模式，即将当前屏幕移到上一个的位置上，其他所有窗口都向前移动一个。
    ctrl+b c           创建新窗口
    ctrl+b n           选择下一个窗口
    ctrl+b l           最后使用的窗口
    ctrl+b p           选择前一个窗口
    ctrl+b w           以菜单方式显示及选择窗口
    ctrl+b s           以菜单方式显示和选择会话。这个常用到，可以选择进入哪个tmux
    ctrl+b t           显示时钟。然后按enter键后就会恢复到shell终端状态
    ctrl+b d           脱离当前会话；这样可以暂时返回Shell界面，输入tmux attach能够重新进入之前的会话
