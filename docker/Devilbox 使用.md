# [Devilbox] [1] 使用

## 安装devilbox

```bash
# 下载
git clone https://github.com/cytopia/devilbox.git
# 创建.env文件
cp env-example .env
# 参照下边一个小节修改.env文件,
# 当然如果需要改软件版本的自己用#注释掉原来的版本,
# 去掉要用的版本前边的#即可

# 启动所有服务,-d参数用于后台运行
sudo docker-compose up -d

# 停止所有服务
sudo docker-compose stop

# 停止并移除
sudo docker-compose down
```

## .env配置

1. TLD_SUFFIX:配置项目扩展名

```.env
TLD_SUFFIX:loc #default config
#我自己的配置,tw比较短,而且浏览器不会当成搜索关键词搜索,tw后缀网站也不常用
TLD_SUFFIX:tw 
```

2. DEVILBOX_UI_SSL_CN:默认使用SSL的域名或者后缀

```.env
# 默认配置
DEVILBOX_UI_SSL_CN=localhost,*.localhost,devilbox,*.devilbox
# 我自己的配置
DEVILBOX_UI_SSL_CN=*.tw #自己定义的后缀
```

3. HOST_PATH_HTTPD_DATADIR:所有项目根目录

```.env
# 默认配置
HOST_PATH_HTTPD_DATADIR=./data/www
# 我自己的配置
HOST_PATH_HTTPD_DATADIR=/home/lm/www
```

4. HOST_PORT_BIND:为DNS服务开放的端口,默认是1053,如果要使用auto-DNS,则需要修改为53

```.env
HOST_PORT_BIND=1053
```

5. HTTPD_DOCROOT_DIR:项目的root目录,像laravel这些框架一般为public

```.env
# 默认配置
HTTPD_DOCROOT_DIR=htdocs
# 我的配置
HTTPD_DOCROOT_DIR=public
```

6. HTTPD_TEMPLATE_DIR: 项目的虚拟主机配置(暂时不会用,待补充)

```.env
# 默认配置
HTTPD_TEMPLATE_DIR=.devilbox
```

## 配置Auto-DNS

## 配置SSL证书

启动devilbox的时候会自动在当前[devilbox git][2]目录下生成一个ca文件夹
找到其中的crt扩展名的文件导入到浏览器即可

## 配置Nginx

## 定制虚拟主机（vhost-gen)

### 文件复制
1. 进入[devilbox git][2]目录(以tp5为例:/home/lm/www/tp5/public)

`cd /home/lm/docker/devilbox`

2. 创建`.devilbox`文件夹

`mkdir /home/lm/www/tp5/public/.devilbox`

3. 复制模板文件

`cp templates/vhostgen/* /home/lm/www/tp5/public/.devilbox`

4. 重启devilbox使之生效

### 模板解释

nginx 两个版本共享统一模板,Apache两个版本有差异,所以需要不同的配置文件

1. 验证yaml文件的有效性

yaml文件中不能使用`\t`形式的`TAB`缩进,所以需要验证

```bash
cd /home/lm/docker/devilbox
./shell.sh
cd /shared/httpd/tp5/public/.devilbox
yamllint apache22.yml
```



[1]: http://devilbox.org/	"官网"
[2]: https://github.com/cytopia/devilbox	"GitHub"