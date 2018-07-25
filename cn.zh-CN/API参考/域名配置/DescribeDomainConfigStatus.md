# DescribeDomainConfigStatus {#reference_ebj_lkv_42b .reference}

查询指定域名的转发配置是否生效。

## 请求参数 {#section_ybx_zfv_42b .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是| 要执行的操作。 取值：

 DescribeDomainConfigStatus

 |
|Domain|String|是|已添加的域名名称。|

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|Status|Integer|请求执行状态：-   0：表示该请求等待执行。
-   1：表示该请求正在执行中。
-   2：表示该请求已执行完成。

|
|WafTaskId|String|WAF的请求ID。|
|ConfigStatus|Integer|域名转发配置生效状态：-   0：表示未生效。
-   1：表示已生效。
-   2：表示尚未检测完成。

|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#createVPCpub}
https://wafopenapi.cn-hangzhou.aliyuncs.com/?Action=DescribeDomainConfig
&Domain=www.aliyun.com
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DescribeDomainConfigStatusResponse>
        <RequestId>D7861F61-5B61-46CE-A47C-6B19160D5EB0</RequestId>
        <Status>2</Status>
        <WafTaskId>aliyun.waf.20180712214032277.qmxI9a</WafTaskId>
        <ConfigStatus>2</ConfigStatus>
    </DescribeDomainConfigStatusResponse>
    ```

-   JSON格式

    ```
    {
        "RequestId":"D7861F61-5B61-46CE-A47C-6B19160D5EB0", 
        "Status":2,
        "ConfigStatus":2,
        "WafTaskId":"aliyun.waf.20180712214032277.qmxI9a" 
    }
    ```


