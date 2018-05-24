在 Ubuntu、Kali linux、Debian 下测试通过

准备部分，不一定非得用搜狗拼音输入法，只要有你喜欢的中文输入法就好了，这部分完成的可以直接跳过看下一部分

## Sublime Text 3安装方法:

从 http://www.sublimetext.com/3 下载对应版本的 Sublime Text 3 后
```
sudo dpkg -i sublime-text*.deb
```


## 正文部分:

1. 保存下面的代码到文件 `sublime_imfix.c `(放到一个自己可以找的到的位置)

```c
#include <gtk/gtkimcontext.h>

void gtk_im_context_set_client_window (GtkIMContext * context, GdkWindow * window)
{
    GtkIMContextClass *klass;
    g_return_if_fail (GTK_IS_IM_CONTEXT (context));
    klass = GTK_IM_CONTEXT_GET_CLASS (context);
    if (klass->set_client_window)
        klass->set_client_window (context, window);
    g_object_set_data (G_OBJECT (context), "window", window);
    if (!GDK_IS_WINDOW (window))
        return;
    int width = gdk_window_get_width (window);
    int height = gdk_window_get_height (window);

    if (width != 0 && height != 0)
        gtk_im_context_focus_in (context);
}
```

2. 将上面的代码编译成共享库 libsublime-imfix.so，命令

```bash
gcc -shared -o libsublime-imfix.so sublime_imfix.c  `pkg-config --libs --cflags gtk+-2.0` -fPIC

 # 注意：如果提示 'gtk/gtkimcontext.h：没有那个文件或目录'，那就是没有相关的依赖软件，安装命令：

sudo apt-get install build-essential libgtk2.0-dev
```

3. 然后将libsublime-imfix.so拷贝到sublime_text所在文件夹

```bash
sudo mv libsublime-imfix.so /opt/sublime_text/
```

4. 修改文件/usr/bin/subl的内容

```bash
sudo gedit /usr/bin/subl
```

将原来的

```text
#!/bin/sh
exec /opt/sublime_text/sublime_text "$@"
```

修改为

```text
#!/bin/sh
LD_PRELOAD=/opt/sublime_text/libsublime-imfix.so exec     /opt/sublime_text/sublime_text "$@"
```

此时，在命令中执行 subl 将可以使用中文输入法

5. 为了使用鼠标右键打开文件时能够使用中文输入，还需要修改文件sublime_text.desktop 的内容。

命令

```bash
sudo gedit /usr/share/applications/sublime_text.desktop
```

- 将 [Desktop Entry] 中的字符串
  `Exec=/opt/sublime_text/sublime_text %F`
  修改为`Exec=bash -c "LD_PRELOAD=/opt/sublime_text/libsublime-imfix.so exec /opt/sublime_text/sublime_text %F"`

  或者修改为`Exec=subl %F`

- 将[Desktop Action Window]中的字符串
  `Exec=/opt/sublime_text/sublime_text -n`
  修改为`Exec=bash -c "LD_PRELOAD=/opt/sublime_text/libsublime-imfix.so exec /opt/sublime_text/sublime_text -n"`

- 将[Desktop Action Document]中的字符串`Exec=/opt/sublime_text/sublime_text --command new_file`修改为`Exec=bash -c "LD_PRELOAD=/opt/sublime_text/libsublime-imfix.so exec /opt/sublime_text/sublime_text --command new_file"`

Notice：

修改时请注意双引号"",否则会导致不能打开带有空格文件名的文件。
此处仅修改了 /usr/share/applications/sublime-text.desktop，但可以正常使用了。
/opt/sublime_text/ 目录下的 sublime-text.desktop 可以修改，也可不修改 (这句是原作者有特殊说明的，我在 kali 中没有这个文件，正常使用)
