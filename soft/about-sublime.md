---
title: 关于Sublime
tags: []
date: 2018-03-29 20:05:37
---
Sublime激活及其使用相关
<!--more-->
## Sublime TEXT3 激活码
sublime激活

```bash
—– BEGIN LICENSE —–
TwitterInc
200 User License
EA7E-890007
1D77F72E 390CDD93 4DCBA022 FAF60790
61AA12C0 A37081C5 D0316412 4584D136
94D7F7D4 95BC8C1C 527DA828 560BB037
D1EDDD8C AE7B379F 50C9D69D B35179EF
2FE898C4 8E4277A8 555CE714 E1FB0E43
D5D52613 C3D12E98 BC49967F 7652EED2
9D2D2E61 67610860 6D338B72 5CF95C69
E36B85CC 84991F19 7575D828 470A92AB
—— END LICENSE ——
```

[来源网站](https://9iphp.com/web/html/sublime-text-3-license-key.html)

## Sublime text3配置ctrl+鼠标左键进行函数跳转
点击Preferences->Browse Packages进入Packages目录，然后打开User目录，查看User目录里面有没有Default (Windows).sublime-mousemap文件，如果没有则创建一个。这个文件是用来配置sublime的鼠标操作的。在文件中输入如下内容：

```json
[
    {
        "button": "button2",
        "count": 1,
        "modifiers": ["ctrl"],
        "command": "jump_back"
    },


    {
        "button": "button1",
        "count": 1,
        "modifiers": ["ctrl"],
        "press_command": "drag_select",
        "command": "goto_definition"
    }
]
```

点击保存即可。

ctrl+鼠标左键跳转到函数定义处；

ctrl+鼠标右键跳回来。
[来源网站](https://blog.csdn.net/shangdibaozi/article/details/77503426)