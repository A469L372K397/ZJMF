### 魔方业务系统V10使用方法

1. 首先需要安装php扩展。根据网站要使用的php版本，下载扩展文件（[php7.2](https://raw.githubusercontent.com/A469L372K397/ZJMF/main/ext/finance/php7.2/idcsmart.so)、[php7.3](https://raw.githubusercontent.com/A469L372K397/ZJMF/main/ext/finance/php7.3/idcsmart.so)、[php7.4](https://raw.githubusercontent.com/A469L372K397/ZJMF/main/ext/finance/php7.4/idcsmart.so)），上传到php安装目录 /lib/php/extensions/no-debug-non-zts-xxxx（xxxx为一串数字）文件夹里面。

2. 修改php配置文件（php.ini），加入以下内容，然后重启php进程。

   ```
   extension=idcsmart.so
   ```

3. 后台系统设置->系统信息，随便填写一个授权码即可授权成功。

4. 在[此页面](https://github.com/A469L372K397/ZJMF-CBAP-plugins)下载应用并安装。


### 魔方财务系统使用方法

*魔方财务系统支持版本：**<=3.7.5***

1. 首先需要安装php扩展。根据网站要使用的php版本，下载扩展文件（[php7.2](https://raw.githubusercontent.com/A469L372K397/ZJMF/main/ext/finance/php7.2/idcsmart.so)、[php7.3](https://raw.githubusercontent.com/A469L372K397/ZJMF/main/ext/finance/php7.3/idcsmart.so)、[php7.4](https://raw.githubusercontent.com/A469L372K397/ZJMF/main/ext/finance/php7.4/idcsmart.so)），上传到php安装目录 /lib/php/extensions/no-debug-non-zts-xxxx（xxxx为一串数字）文件夹里面。

2. 修改php配置文件（php.ini），加入以下内容，然后重启php进程。

   ```
   extension=idcsmart.so
   ```

3. 使用[官方安装包](https://raw.githubusercontent.com/A469L372K397/ZJMF/main/zjmfmangerbetaV3.7.5.zip)进行安装。填写授权码的时候，随便填写一个的32位大写的MD5字符串，例如可以[在这里生成](https://md5jiami.bmcx.com/)。（之前用过官方安装包的，还需要解压此安装包单独覆盖vendor目录）
   该官方安装包已经集成部分常用插件，无需再去商店购买。

4. 安装完之后默认就是专业版，所有专业版的功能均可使用。

5. 如果上传了第三方付费插件或模板，使用过程中提示插件未购买，需要在php配置文件（php.ini）加入idcsmart.app这个配置项，配置第三方插件标识，多个插件标识用英文逗号隔开，例如：

   ```
   idcsmart.app=AliPayDmf,Smsbao,Subemail
   ```

   重启php进程，在后台系统升级页面，已授权模块处，点击“拉取授权”。即可使用付费的第三方插件或模板。

### 魔方云系统使用方法

*魔方云系统支持版本：**3.9.14***

1. 使用以下命令安装魔方云系统（之前已经安装过免费版的，直接跳到第3步）：

   ```shell
   wget https://raw.githubusercontent.com/A469L372K397/ZJMF/main/install-zjmf-cloud_new -O install-zjmf-cloud_new && chmod +x install-zjmf-cloud_new && ./install-zjmf-cloud_new
   ```

   国内服务器可以用以下命令：

   ```shell
   wget https://ghfast.top/https://raw.githubusercontent.com/A469L372K397/ZJMF/main/install-zjmf-cloud_new -O install-zjmf-cloud_new && chmod +x install-zjmf-cloud_new && ./install-zjmf-cloud_new
   ```

   TencentOS Server3.1安装命令：

   ```shell
   wget https://raw.githubusercontent.com/A469L372K397/ZJMF/main/install-zjmf-cloud_new_TencentOS -O install-zjmf-cloud_new_TencentOS && chmod +x install-zjmf-cloud_new_TencentOS && ./install-zjmf-cloud_new_TencentOS
   ```
   Rocky-linux-8.10安装命令：

   ```shell
   wget https://raw.githubusercontent.com/A469L372K397/ZJMF/main/install-zjmf-cloud_R8 -O install-zjmf-cloud_R8 && chmod +x install-zjmf-cloud_R8 && ./install-zjmf-cloud_R8
   ```

   HK区域安装命令：

   ```shell
   wget https://raw.githubusercontent.com/A469L372K397/ZJMF/main/install-zjmf-cloud_new_hk -O install-zjmf-cloud_new && chmod +x install-zjmf-cloud_new && ./install-zjmf-cloud_new
   ```
   以上命令是access模式安装脚本，如果要Trunk模式，是在最后加 -t，轻量版是在最后加 -l

2. 填写授权码的时候，随便填写一个的32位大写的MD5字符串。

3. 输入以下命令完成授权：

   ```
   echo -n "echo \"success\"" > /home/zjmf/dashboard/www/extend/other/extension
   wget https://raw.githubusercontent.com/A469L372K397/ZJMF/main/other/check_main -O /home/zjmf/dashboard/www/extend/other/check_main
   chmod +x /home/zjmf/dashboard/www/extend/other/extension
   chmod +x /home/zjmf/dashboard/www/extend/other/check_main
   wget https://raw.githubusercontent.com/A469L372K397/ZJMF/main/ext/cloud/3.9.0/idcsmart.so -O /usr/lib64/php/modules/idcsmart.so
   echo "extension=idcsmart.so" > /etc/php.d/40-idcsmart.ini
   wget https://raw.githubusercontent.com/A469L372K397/ZJMF/main/other/helper.php -O /home/zjmf/dashboard/www/vendor/topthink/think-helper/src/helper.php
   systemctl restart php-fpm
   ```
   
   国内服务器可以用以下命令：
   
   ```
   echo -n "echo \"success\"" > /home/zjmf/dashboard/www/extend/other/extension
   wget https://ghfast.top/https://raw.githubusercontent.com/A469L372K397/ZJMF/main/other/check_main -O /home/zjmf/dashboard/www/extend/other/check_main
   chmod +x /home/zjmf/dashboard/www/extend/other/extension
   chmod +x /home/zjmf/dashboard/www/extend/other/check_main
   wget https://ghfast.top/https://raw.githubusercontent.com/A469L372K397/ZJMF/main/ext/cloud/3.9.0/idcsmart.so -O /usr/lib64/php/modules/idcsmart.so
   echo "extension=idcsmart.so" > /etc/php.d/40-idcsmart.ini
   wget https://ghfast.top/https://raw.githubusercontent.com/A469L372K397/ZJMF/main/other/helper.php -O /home/zjmf/dashboard/www/vendor/topthink/think-helper/src/helper.php
   systemctl restart php-fpm
   ```

后续每次更新都要重新执行上述命令。

[魔方云安装完毕后几点优化操作 以及常见问题处理](https://raw.githubusercontent.com/A469L372K397/ZJMF/main/Common-problem-handling.md)

### 自建授权接口站点（可选）

这部分是可选的，如果内置授权接口出现连接不稳定等情况，可以选择自建。

1. 新建一个网站，上传[授权接口源码](https://raw.githubusercontent.com/A469L372K397/ZJMF/main/zjmf_auth_api.zip)，并配置好伪静态。

2. 在php配置文件（php.ini）加入idcsmart.url这个配置项，填写授权接口地址，例如：

   ```
   idcsmart.url=http://www.example.com/
   ```

   注意一定要以/结尾。然后重启php进程生效。

### 魔方云HyperV使用方法

1. 需自建授权接口站点，绑定license7.idcsmart.com域名，并开启SSL（随便一个域名证书即可）
2. 在Windows系统内配置hosts，将license7.idcsmart.com域名指向刚才的服务器IP
3. 使用官方安装程序安装，填写授权码的时候，随便填写一个的32位大写的MD5字符串。

   （一）环境要求
      1、系统：使用Windows-2019(已测试)，确保是干净的操作系统；Hyper-V操作系统镜像目前支持Windows-2019(推荐)、Windows-2008R2、Windows-2012R2、Windows-2016
   
      2、服务器自行安装微软Hyper-V组件，将外网网卡名称修改为external，并建议将安装文件和安装目录添加到Windows病毒防护白名单，详情参考[Hyper-V环境配置](https://www.idcsmart.com/wiki_list/893.html)
   
      3、创建实例所需[镜像](https://www.idcsmart.com/wiki_list/903.html)请自行下载并放置在计算节点服务器D:\images 目录下
   

   （二）注意事项
      1、请先部署主控后部署计算节点
   
      2、安装之前，请获取授权码
   
      3、Hyper-V节点只支持本地存储
   

   （三）操作步骤
      1、准备需要部署Hyper-v的服务器（注意环境要求）
   
      2、下载[Hyper-V安装包](https://raw.githubusercontent.com/A469L372K397/ZJMF/main/hv_install-2.0.6.zip)，放入服务器中（建议将安装文件和安装目录添加到Windows病毒防护白名单）
   
      3、解压安装包，运行“安装包.exe”
   
      4、输入的授权码校验成功后，指定程序安装位置，等待程序自动安装脚本
   
      5、在D盘创建images文件夹，将创建实例所需系统镜像（[Hyper-v镜像下载地址](https://www.idcsmart.com/wiki_list/903.html)）放入文件夹中
   
      6、进入魔方云web控制面板-->节点管理页面，进行添加节点操作，节点类型选择Hyper-V
   
      7、如需重新安装Hyper-V安装包，请先卸载之前的Hyper-V安装包
   

### 智简魔方用户指南

[《魔方DCIM使用文档 / 用户指南》](https://www.idcsmart.com/wiki_list/)
