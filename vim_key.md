### vim 个人习惯按键

+ 保存和退出
    + :q ,q退出
    + :q! 退出不保存
    + :w ,w保存
    + :sav filename 另保存

+ 复制和粘贴
    + y 复制内容
    + p 粘贴内容
    + d 剪切内容
    + dd 剪切当前行
    + yy 复制当前行
    + dd 剪切当前行

+ 插入 
    + i 光标左侧插入
    + a 光标右侧插入
    + o 光标添加下一行
    + O 光标添加上一行
    + I 光标所在行头插入
    + A 光标所在行尾插入

+ 移动
    + G 移动到文件末尾
    + gg 移动到文件开头
    + :n 移动到n行
    + m| 移动到m
    + ctrl f 前移一页
    + ctrl b 后移一页

+ 搜索
    + /word 全文搜索
    + ?word 倒序搜索
    + /\<the 以the开头
    + /the\> 以the结尾

+ 替换
    + :%s/old/new/g 全文old替换new
    + :%s/old/new/gi 全文old替换new,大小写不敏感

+ 插件功能
    + 跳转
        + ,,b/w 光标前后跳转
        + ,,[hjkl] 行列跳转
        + ,ss 搜索跳转
    + 选中
        + v/V 选中部分
        + ,sa 全部选中
    + 标签
        + m[a-zA-Z] 打标签
        + '[a-zA-Z] 跳到标签位置
        + '. 最后一次变更的位置
        + " 跳回来位置
        + m<space> 去除所有标签
    + 注释
        + ,cc 加注释
        + ,cu 解开注释
        + ,c<space>智能判断
    + 其他
        + kj  代替Esc
        + ,zz 代码折叠

更多参考https://github.com/wklken/k-vim
