"# wordpress" 
最近在国外论坛 www.nulled.to 上看到这样一个破解 Wordfence 安全插件专业版的方法，试了一下，可行。下面附上教程。测试的是 7.1.* 的版本，修改后授权码时间会变成 17773 天。

教程：
第 1 步：登录您的 WordPress 网站，并安装 Wordfence 插件。

第 2 步：安装后会弹出一个添加邮箱，输入后接着出现一个专业版授权码的窗口，不激活

第 3 步：连接你的 FTP，并找到以下路径：wp-content/plugins/wordfence/lib

第 4 步：打开 wordfenceClass.php 文件，推荐使用 Notepad++等软件

第 5 步：搜索if (!WFWAF_SUBDIRECTORY_INSTALL && $waf = wfWAF::getInstance()) {
找到 $siteurl = wfUtils::wpSiteURL(); 这一行代码（大概在下两行的位置）



第 6 步：在找到的代码下添加
wfConfig::set('isPaid', 1);

wfConfig::set('keyType', wfAPI::KEY_TYPE_PAID_CURRENT);

!!wfConfig::set('isPaid', 1);

!!wfConfig::set('keyType', wfAPI::KEY_TYPE_PAID_CURRENT);
修改后的的完整代码为
// Sync the WAF data with the database.

if (!WFWAF_SUBDIRECTORY_INSTALL && $waf = wfWAF::getInstance()) {

$homeurl = wfUtils::wpHomeURL();

$siteurl = wfUtils::wpSiteURL();

wfConfig::set('isPaid', 1);

wfConfig::set('keyType', wfAPI::KEY_TYPE_PAID_CURRENT);

!!wfConfig::set('isPaid', 1);

!!wfConfig::set('keyType', wfAPI::KEY_TYPE_PAID_CURRENT);
第 7 步：保存然后上传覆盖源文件。

最后关闭授权码窗口，进入插件的仪表盘就 OK 了。

 
