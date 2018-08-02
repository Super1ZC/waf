# 步骤4：修改DNS解析 {#concept_afg_dy1_p2b .concept}

通过修改域名的DNS解析记录将网站域名解析到WAF，完成业务正式接入。推荐您使用CNAME方式接入WAF，成功添加域名到WAF控制台后，WAF会为域名分配一个CNAME值，您只需添加/修改域名的CNAME解析记录为分配的CNAME值，即可完成接入。

参照[步骤1：添加网站配置](intl.zh-CN/快速入门/步骤1：添加网站配置.md#)中**查看Web应用防火墙为该网站分配的CNAME**，记录下WAF分配给域名的CNAME值，如`xxxxxxxx7wmqvixt8vedyneaepztpuqu.alicloudwaf.com`。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15549/15331809247586_zh-CN.png)

## CNAME接入说明 {#section_ug3_g5b_p2b .section}

WAF通常采用CNAME解析的方式将网站接入进行防护，也支持A记录解析的方式接入。

**说明：** 强烈建议您采用CNAME解析的方式。因为在某些极端情况下（如节点故障、机房故障等），通过CNAME解析方式接入WAF，可以实现自动切换节点IP甚至将直接解析切回源站，从而最大程度保证业务的稳定运行，提供高可用性和灾备能力。

如果必须使用A记录解析的方式接入（例如，@记录与MX记录冲突等情况），您可以通过Ping WAF分配的CNAME值获取所分配的WAF IP（该IP地址一般不会频繁变更），然后将网站域名通过A记录解析的方式接入WAF进行防护。

**域名主机记录**

关于域名的主机记录，以域名`abc.com`为例：

-   www： 用于精确匹配www开头的域名，如`www.abc.com`，但无法匹配`abc.com`
-   @： 用于匹配直接访问`abc.com`的情况
-   \*： 用于匹配泛域名，即匹配任意域名，如`blog.abc.com`、`www.abc.com`、`abc.com`等

**修改DNS解析记录的注意事项**

-   对于同一个主机记录，CNAME解析记录值只能填写一个，您可以将该记录值修改为WAF的CNAME值，从而将网站域名接入WAF进行防护。
-   由于不同DNS解析记录类型存在冲突，对于同一个主机记录，CNAME记录与A记录、MX记录、TXT记录等其他记录互相冲突。您需要删除原其它记录后再添加CNAME记录解析记录，或者将原记录类型修改为CNAME类型。

    关于DNS解析记录互斥的详细说明，请参考[解析记录冲突的规则](https://www.alibabacloud.com/help/doc-detail/58456.htm)。

    **说明：** 删除其它解析记录并新增CNAME解析记录的过程应尽可能在短时间内完成。如果删除A记录后长时间没有添加CNAME解析记录，可能导致域名无法正常解析。

-   如果必须保留MX记录（邮件服务器记录），您可以使用A记录解析的方式将域名解析到WAF的IP。通过Ping CNAME获取所分配的WAF IP（该IP地址一般不会频繁变更）后，将网站域名A解析记录类型的记录值修改为该WAF IP。

    **说明：** 使用A记录解析的方式进行接入，WAF将无法支持自动故障集群调度和故障bypass操作。


## 操作步骤 {#section_yg3_g5b_p2b .section}

本文以阿里云云解析DNS和花生壳为例，介绍DNS配置方式，其它DNS提供商可以参考本文档进行类似配置。

**阿里云云解析配置示例**

**说明：** 如果您使用**阿里云云解析DNS**行域名解析，并且在执行[步骤1：添加网站配置](intl.zh-CN/快速入门/步骤1：添加网站配置.md#)前已经为域名设置并启用了A记录（且如果是中国大域名，已完成备案），则您在添加网站配置时，可以一键添加网站并自动更新解析记录。以下操作步骤适用于您的域名已经添加到WAF域名列表，但DNS解析状态为异常的情况。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15549/15331809247587_zh-CN.jpg)

参照以下步骤，在阿里云云解析修改CNAME记录来接入WAF：

1.  登录[阿里云云解析控制台](https://dns.console.aliyun.com/#/dns/domainList)。
2.  选择要操作的域名，单击其操作列的**解析设置**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15549/15331809247588_zh-CN.jpg)

3.  选择要操作的主机记录，单击其操作列下的**修改**。

    **说明：** 您也可以删除已有的A记录，然后单击**添加记录**，添加一条新的CNAME记录。删除原解析记录后，请尽快添加CNAME解析记录，否则可能导致网站域名解析失败。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15549/15331809247589_zh-CN.jpg)

4.  将记录类型修改为**CNAME**，记录值修改为WAF所分配的CNAME值。

    **说明：** TTL值一般建议设置为600秒（即10分钟）。TTL值越大，则DNS记录的同步和更新越慢。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15549/15331809247590_zh-CN.jpg)


**花生壳配置示例**

部分域名提供商（如花生壳）可能不支持直接修改已有解析记录的记录类型和主机记录，您需要删除原有的A记录后，再添加新的CNAME解析记录。

**说明：** 删除原解析记录后，请尽快完成添加CNAME解析记录，否则可能导致网站域名解析失败。

参照下图设置来修改您的域名在花生壳上的DNS解析信息。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15549/15331809247591_zh-CN.jpg)

## 验证DNS配置 {#section_hh3_g5b_p2b .section}

将网站域名的DNS解析切换至WAF后，您的网站域名即接入WAF进行防护。解析记录配置完成后，您可以通过Ping网站域名的方式或[DNS Check](https://mxtoolbox.com/dnscheck.aspx)等其他工具验证DNS解析生效情况。

**说明：** 由于DNS解析记录生效需要一定时间，如果本地测试域名无法访问，您可以等待10分钟后重新检查。

