# SDK方案简介 {#concept_kvh_khq_p2b .concept}

SDK方案专门针对原生App端，提供可信通信、防机器脚本滥刷等安全防护，可以有效识别高风险手机、猫池、牧场等特征。

## SDK方案解决什么问题 {#section_q2p_khq_p2b .section}

SDK方案集成了阿里巴巴集团和阿里云多年来对抗黑灰产、羊毛党的经验和技术积累。接入SDK后，您的App将获得与天猫、淘宝、支付宝等客户端相同的可信通信技术，并共享阿里巴巴集团对抗黑灰产、羊毛党的恶意设备指纹库，从根本上解决App端的安全问题。

SDK方案帮助您解决以下**原生App**端的问题：

-   恶意注册、撞库、暴力破解
-   针对App的大流量CC攻击
-   短信/验证码接口被刷
-   薅羊毛、抢红包
-   秒杀限时限购商品
-   恶意查票、刷票（如机票酒店等）
-   价值咨询爬取（如价格、征信、融资、小说）
-   机器批量投票
-   灌水、恶意评论

## SDK方案如何接入 {#section_s2p_khq_p2b .section}

参照以下步骤，将您的App接入SDK：

**说明：** 集成SDK，您无需在服务器端进行任何改动。配置完成后，WAF将自动过滤恶意流量，将合法的请求转发给源站服务器。恶意请求产生的压力将全部由WAF承担，保障您的服务器端稳定运行。

1.  登录[云盾Web应用防火墙控制台](https://yundun.console.aliyun.com/?p=waf)。
2.  前往**管理** \> **网站配置**页面，将App使用的域名添加进来，为其开启WAF防护。具体步骤请参考[添加网站配置](../../../../intl.zh-CN/快速入门/步骤1：添加网站配置.md#)。
3.  在App域名解析服务商处，添加CNAME记录，将App域名解析指向WAF。具体步骤请参考[修改DNS解析](../../../../intl.zh-CN/快速入门/步骤4：修改DNS解析.md#)。
4.  在App中集成WAF提供的SDK组件（[单击下载SDK](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/62847/cn_zh/1527666392401/WAF-SDK-20180525.zip)）。

    **说明：** 集成SDK工作可能需要您投入1-2天时间的工作量。

    关于SDK的详细接入操作，请参考：

    -   [iOS接入文档](intl.zh-CN/用户指南/SDK方案/iOS接入文档.md#)
    -   [Android接入文档](intl.zh-CN/用户指南/SDK方案/Android接入文档.md#)
5.  联系WAF技术支持人员测试集成好的App。您可以扫描文末的二维码，通过钉钉联系WAF技术支持人员。
6.  打包发布新的App版本，享受SDK防护。

如果您对方案/接入有任何问题，请扫描下方的钉钉二维码联系我们（进群时请说明咨询SDK方案）。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15578/15350126747821_zh-CN.png)

