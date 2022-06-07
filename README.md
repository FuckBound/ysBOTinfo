<br><center><font size =5>原神机器人说明文档v2.0@220607</center></font>

<br>
目录

[toc]
# 6月7日更新内容:
1. 使用新的机器人
项目地址:
    > https://github.com/CMHopeSunshine/LittlePaimon

    命令列表
    > https://blog.cherishmoon.fun/posts/nonebot2funclist.html

2. 机器人可以接受不以`/`开头的命令

# 添加cookie方法(pc/安卓)
大部分机器人的命令,需要依赖自己的cookie

电脑通过各种浏览器,安卓手机通过via浏览器添加cookie
1. 打开浏览器,安卓手机可用via浏览器
   via浏览器地址 
>https://viayoo.com/zh-cn/
2. 访问米游社,先登录自己的账号
https://m.bbs.mihoyo.com/ys/
3. 复制以下内容,粘贴到地址栏，运行(安卓via浏览器直接粘贴,其他浏览器粘贴后可能需要补全前面的javascript: 电脑也可使用F12调试里的console运行)
> javascript:(function(){prompt(document.domain,document.cookie)})();
4. 出现弹窗,复制框内文本
5. 发送 ysb（空格）（复制的内容），添加cookie

# 部分命令列表

`[]`内是可选参数  `()`内是必选参数
|功能|对自己使用|扩展
|-|-|-|
实时便签| `ssbq`|`ssbq [uid]`
每月札记| `myzj [月份]`|`myzj [uid] [月份]`
米游社签到| `mys签到`|`mys签到 [uid]`
个人信息主页|`ys`|`ys [uid]`
查看全部角色|`ysa`|`ysa [uid]`
查看角色天赋等级|`ysc 角色名`| `ysc [uid] 角色名`
查看深渊具体阵容| `sy [层数]`|`sy [uid] [层数]`
自动签到 |`mys自动签到 (开启/关闭) uid`|
自动提醒 |`ssbq (开启关闭)提醒 树脂数` |

更多命令,详细参见
> https://blog.cherishmoon.fun/posts/nonebot2funclist.html

# 抽卡记录分析功能
命令: `获取抽卡记录 [uid] 抽卡记录链接`
必须依赖`抽卡记录链接`,获取它有很多方法
## pc上通过`powershell`获取抽卡链接的一种方法
来源:
>https://github.com/sunfkny/genshin-gacha-export-js
的geturl.ps1.txt文件

0. 确保近期打开过原神游戏内的抽卡历史记录
1. 打开powershell窗口(右键windows徽标-->powershell)
2. 复制以下内容至powershell窗口
``` powershell
# 拼接日志路径
# 外服需要把 原神 改成 Genshin Impact
$output_log_path = "$env:USERPROFILE\AppData\LocalLow\miHoYo\原神\output_log.txt"
# 读取文件
$log = Get-Content $output_log_path
# 提取链接，去除不需要的OnGetWebViewPageFinish:
$urls = $log -match "OnGetWebViewPageFinish:" -match "#/log" -replace "OnGetWebViewPageFinish:",""
# 取最后一个链接
$url = $urls[$urls.Length-1]
# 输出到控制台
Write-Host $url
# 浏览器打开
Start-Process -FilePath $url
# 如果运行ps1脚本
# write-host "按任意键退出..."
# [void][System.Console]::ReadKey($true)
```
