---
title: 学堂在线-生活英语听说(自主模式)-视频地址抓取
tags: [PHP,爬虫]
date: 2017-12-25 16:14:23
---
## 使用语言:

PHP

## 开发工具:

VSCode

## PHP版本

PHP7.1.3

## 框架:

QueryList 4.0([访问官网](https://querylist.cc/))

## 功能:

获取该课程的所有视频以及字幕的下载地址

## 分析:

1. 获取课程目录页面
2. 分析课程目录页面中包含的课程以及对应的播放页面地址
3. 获取某节课的播放页面
4. 分析播放页面中的视频连接以及字幕下载地址
    a. 发现视频请求的是其他页面,当前页面只能拿到获取视频地址用到的id
    b. 用上一步拿到的id拼接视频播放地址获取接口
    c. 用上一步得到的视频地址数据得到高清和标清的视频地址
    d. 在播放页面找到字幕下载地址
5. 将4的步骤循环,获取全部课程目录中的视频的高清地址
6. 按不同章节存放在不同目录中.

## 代码

```php
# PasePath.php
require './vendor/autoload.php';

use QL\QueryList;

class PasePath
{
    public function paseUrl($headers,$url,$domain){
        $rule = [
            'chapter' => ['div.chapter','html']
        ];

        $rule2 = [
            'dirname' => ['h3','text']
        ];

        $rule3 = [
            'filename' => ['ul>li','text','-p.subtitle'],
            'fileurl' => ['ul>li>a','href']
        ];


        $arr = QueryList::get($url,[],['headers' => $headers])->rules($rule)->query()->getData()->all();

        $dir_arr=[];
        foreach ($arr as $k=>$v){
            $str = $v['chapter'];

            $dir = QueryList::html($str)->rules($rule2)->query()->getData()->all();
            $dirname = trim($dir[0]['dirname']);

            $file = QueryList::html($str)->rules($rule3)->query()->getData()->all();
            $list = [];
            foreach($file as $k2=>$v2){
                $filename = strtr(trim($v2['filename'],"? \n ' '"),':',"_");
                $fullurl = $domain.$v2['fileurl'];
                $list += [$filename=>$fullurl];
            }
            $dir_arr += [$dirname => $list];
        
        }
        return $dir_arr;
    }

    public function getVideoUrlList($pageUrl,$headers,$realVideoPath,$domain){
        # 采集规则1,匹配视频播放器的位置
        $rule = [
            'video' => ['#seq_contents_0','text']
        ];

        # 获得播放器所在位置的隐藏HTML
        $ql = QueryList::get($pageUrl,[],['headers'=>$headers])->rules($rule)->query();

        #转换隐藏的HTML代码部分
        $html = htmlspecialchars_decode($ql->getData()->all()[0]['video']);

        # 采集规则2,获取视频的data-ccsource信息
        $rule2 = [
            'videoId' => ['div.closed','data-ccsource'],
            'srtUrl' =>['ul.wrapper-downloads>li>a','href']
        ];
        
        # 执行采集方法采集data-ccsource
        $data = QueryList::html($html)->rules($rule2)->query()->getData()->all();
        
        if(!empty($data[0])){
        # 拿到data-ccsource设为视频id

        $videoId = $data[0]['videoId'];
        $srtUrl = $domain.$data[0]['srtUrl'];
        # 组装完整的视频获取地址
        $realUrl = $realVideoPath.$videoId;

        # 采集视频清晰度列表
        $videourl = QueryList::get($realUrl)->getHtml();
        # 返回视频下载地址列表

        $source =[
            'videoDownUrl'=>(json_decode($videourl)->sources)->quality20[0],
            'srtUrl' => $srtUrl
        ];
   
        return $source;
        }else{
            return Null;
        }
    }

    public function getSrt($srtUrl){
        
    }

}


$domain = 'https://www.xuetangx.com';
// 完整视频获取地址前缀
$realVideoPath = 'http://www.xuetangx.com/videoid2source/';
$url = "https://www.xuetangx.com/courses/course-v1:TsinghuaX+30640014X+2017_T2/courseware/d0ab249c93a3461a957a7523c7bb51d8/";
// 登录状态
$headers = [
    'Cookie' => 'aliyungf_tc=AQAAAKJg5S+S0wIAwJXnc/3hQ9JZEeZT; sessionid=92890beb06427e5fe6a894b29f4ac564; '
];
set_time_limit(500000);
$pasepath = new PasePath();
$tree = $pasepath->paseUrl($headers,$url,$domain);

$j = 0;
foreach($tree as $k=>$v){
    $i=0;
    if(!file_exists('down/'.$k)){
        mkdir('down/'.$k,0777,true);
        echo '文件夹',$k,'创建成功<hr>';
    }
    foreach($v as $k2=>$v2){

        $b = $pasepath->getVideoUrlList($v2,$headers,$realVideoPath,$domain);
        if(!empty($b)){
            $wfile = fopen("down/{$k}/{$k2}.txt",'w') or die('文件不存在');
            fwrite($wfile,$b["videoDownUrl"]);
            fclose($wfile);
        }

        $i+1==2? die: 1 ;
        $i++;
    }
    $j+1==2? die: 1 ;
    $j++;
}

```

## 不足:

1. 没有做模拟登录,需要在浏览器先登录自己的账号,复制cookie信息
2. 下载速度太慢
3. 暂时只获取到了mp4地址,并没有写下载程序(直接下载的速度太慢了)
4. 字幕所在地址找到了,但是下载字幕存在问题

## 改进方向

1. 增加模拟登录
2. 采用多进程进行采集
3. 使用多线程进程采集
4. 找到字幕的下载方法
