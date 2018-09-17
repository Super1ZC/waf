# CDN结合WAF {#concept_ig2_xfj_p2b .concept}

云盾Web应用防火墙（WAF）可以与网宿、加速乐、七牛、又拍、阿里云等CDN结合使用，对使用了CDN的域名进行Web攻击防御。您可以参照以下架构为源站同时部署CDN和WAF：**CDN（内容加速）**\>**Web应用防火墙（中间，实现应用层防护）**\> **源站**。

**说明：** 大部分CDN服务商不防御CC攻击，有CC攻击的域名会在CDN层截断访问。建议有CC攻击的域名单独使用WAF。

## 使用阿里云CDN {#section_qnf_dhj_p2b .section}

1.  配置CDN，将域名接入CDN。
2.  配置Web应用防火墙，域名必须和CDN配置的域名保持一致（可以配置泛域名）。源站填写SLB公网IP、ECS公网IP、或云外机房服务器的IP，并在**是否接入CDN或高防IP等产品**选项处选择**是**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15558/15371769497705_zh-CN.jpg)

3.  配置成功后，Web应用防火墙会生成一个CNAME地址。

    **说明：** 关于如何查看WAF生成的CNAME地址，请参考[添加网站配置](../../../../cn.zh-CN/快速入门/步骤1：添加网站配置.md#)中**查看Web应用防火墙为该网站分配的CNAME**部分。

4.  将CDN中原本配置的源站修改为Web应用防火墙分配的CNAME地址，操作步骤如下：
    1.  登录[阿里云CDN控制台](https://cdn.console.aliyun.com/#/DomainList/list)。
    2.  在域名管理页面，选择要操作的域名，单击**配置**。
    3.  在**源站设置**下，单击**修改配置**。
    4.  修改源站信息。

        -   **类型**：选择**源站域名**。
        -   **源站地址 域名**：填写WAF生成的CNAME地址。
        -   **协议跟随回源**：开启。
        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15558/15371769497706_zh-CN.jpg)

    5.  在**回源设置**下，确认**回源host**未开启。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15558/15371769497707_zh-CN.jpg)

5.  完成上述配置后，流量经过CDN，其中动态内容将继续通过Web应用防火墙进行安全检测防护。

## 使用非阿里云CDN {#section_jv2_ghj_p2b .section}

1.  配置CDN，将域名接入CDN。
2.  配置Web应用防火墙，域名必须和CDN配置的域名保持一致（可以配置泛域名）。源站填写SLB公网IP、ECS公网IP、或云外机房服务器的IP，并在**是否接入CDN或高防IP等产品**选项处选择**是**。![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15558/15371769497705_zh-CN.jpg)
3.  配置成功后，Web应用防火墙会生成一个CNAME地址。

    **说明：** 关于如何查看WAF生成的CNAME地址，请参考[添加网站配置](../../../../cn.zh-CN/快速入门/步骤1：添加网站配置.md#)中**查看Web应用防火墙为该网站分配的CNAME**部分。

4.  将CDN中原本配置的源站改为Web应用防火墙分配的CNAME地址。

