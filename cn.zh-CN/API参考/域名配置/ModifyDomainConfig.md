# ModifyDomainConfig {#reference_ig1_5f1_p2b .reference}

修改指定域名配置信息。

## 请求参数 {#section_ybx_zfv_42b .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是| 要执行的操作。 取值：

 ModifyDomainConfig

 |
|Domain|String|是|域名名称。|
|SourceIps|Array|是|源站IP，支持指定多个IP。|
|Protocols|Array|是| 该域名所支持的访问协议，取值：

-   http：表示支持HTTP协议。
-   https：表示支持HTTPS协议。
-   http,https：同时支持HTTP、HTTPS协议。

 |
|HttpPort|Array|否|HTTP协议配置的端口。指定多个HTTP端口时，使用“,”进行分隔。**说明：** 配置协议为HTTP时，该参数为必填项。默认值为80。HttpPort与HttpsPort两个请求参数至少需要填一个。

|
|HttpsPort|Array|否|HTTPS协议配置的端口。指定多个HTTPS端口时，使用“,”进行分隔。**说明：** 配置协议为HTTPS时，该参数为必填项。默认值为443。HttpPort与HttpsPort两个请求参数至少需要填一个。

|
|IsAccessProduct|Integer|是|该域名在WAF前是否配置有七层代理（例如，高防、CDN等），取值：-   0：表示无。
-   1：表示有。

|

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|Status|Integer|请求执行状态：-   0：表示该请求等待执行。
-   1：表示该请求正在执行中。
-   2：表示该请求已执行完成。

|
|WafTaskId|String|WAF的请求ID。|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#createVPCpub}
https://wafopenapi.cn-hangzhou.aliyuncs.com/?Action=ModifyDomainConfig
&Domain=www.aliyun.com
&SourceIps=["x.x.x.x","x.x.x.x"]
&Protocols=["http","https"]
&HttpPort=[80]
&HttpsPort=[443]
&IsAccessProduct=0
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <ModifyDomainConfigResponse>
        <RequestId>D7861F61-5B61-46CE-A47C-6B19160D5EB0</RequestId>
        <Status>2</Status>
        <WafTaskId>aliyun.waf.20180712214032277.qmxI9a</WafTaskId>
    </ModifyDomainConfigResponse>
    ```

-   JSON格式

    ```
    {
        "RequestId":"D7861F61-5B61-46CE-A47C-6B19160D5EB0", 
        "Status":2,
        "WafTaskId":"aliyun.waf.20180712214032277.qmxI9a" 
    }
    ```


